# Duplicate Emails on Order Confirmation — Bugfix Analysis

## Bug Summary

Some customers receive duplicate order confirmation emails after completing a purchase. The issue affects approximately 8% of orders and has generated 45 support complaints in the last 2 weeks. Duplicates are exact copies sent 1-3 seconds apart.

## Current Behavior (Defective)

1. User completes checkout and clicks "Place Order"
2. System processes the payment successfully
3. System sends an order confirmation email
4. **System sends a second identical confirmation email 1-3 seconds later**
5. User receives two identical emails

Reproduction: Occurs intermittently. More frequent during high-traffic periods. Reliable reproduction by clicking "Place Order" rapidly twice.

## Expected Behavior (Correct)

1. User completes checkout and clicks "Place Order"
2. System processes the payment successfully
3. System sends exactly one order confirmation email
4. Subsequent clicks on "Place Order" for the same order are ignored

## Unchanged Behavior (Regression Prevention)

- Order confirmation email content and formatting must remain identical
- Email delivery timing must remain within current SLA (under 60 seconds)
- Other transactional emails (shipping, refund) must not be affected
- The checkout flow and payment processing must work identically
- Orders placed through the API (not the web UI) must continue to work

## Root Cause Analysis

The order completion handler is called by both the payment webhook and the UI success callback. During normal flow, the payment webhook fires first and sends the email. When the UI callback arrives shortly after, it triggers the email again because there is no idempotency check on email dispatch.

The race condition is amplified by:
1. No debounce on the "Place Order" button
2. No idempotency key on the order completion handler
3. No deduplication check in the email queue

## Proposed Fix

Two-layer fix:
1. **UI layer:** Disable the "Place Order" button after first click to prevent duplicate submissions
2. **Backend layer:** Add an idempotency check to the order completion handler using the order ID. If the confirmation email has already been queued/sent for this order, skip the duplicate.

The backend fix is the primary fix (handles all entry points). The UI fix is defense-in-depth.

## Boundaries

### Always
- Preserve all existing email content and formatting
- Maintain the current email delivery SLA

### Never
- Never modify the payment processing flow
- Never change the webhook handler's response format (external integrations depend on it)
