# Duplicate Emails on Order Confirmation — Fix Tasks

**Spec:** [[Business/Documentation & Research/Spec driven development/Examples/duplicate-order-emails/bugfix]]
**Status:** Not started

### 1. Reproduce the bug

- [ ] **Status:** Not started
- **Description:** Create a test that demonstrates the duplicate email behavior. Simulate both the webhook and UI callback firing for the same order and verify two emails are sent. This test should fail before the fix and pass after.
- **Files:** `tests/orders/duplicate-email.test.ts`
- **Depends on:** None
- **Validates:** Current Behavior section (confirms the bug exists)

### 2. Add idempotency check to order completion handler

- [ ] **Status:** Not started
- **Description:** Add an `email_sent_at` nullable timestamp column to the `orders` table. In the order completion handler, check this column before sending the confirmation email. If already set, skip email dispatch. Use a database transaction to prevent race conditions between concurrent handlers.
- **Files:** `src/db/migrations/xxx-add-email-sent-at.ts`, `src/services/order-service.ts`
- **Depends on:** Task 1
- **Validates:** Expected Behavior (exactly one email per order)

### 3. Disable Place Order button after first click

- [ ] **Status:** Not started
- **Description:** Add loading/disabled state to the "Place Order" button. After first click: disable the button, show a loading indicator. Re-enable only if the request fails. This is defense-in-depth — the backend fix is the primary safeguard.
- **Files:** `src/features/checkout/components/PlaceOrderButton.tsx`
- **Depends on:** None (independent of backend fix)
- **Validates:** Expected Behavior (UI prevents rapid double-click)

### 4. Verify regression prevention

- [ ] **Status:** Not started
- **Description:** Run existing order and email test suites. Add specific tests verifying: (1) single confirmation email is still sent, (2) email content is unchanged, (3) API-placed orders still receive confirmation, (4) shipping and refund emails are unaffected.
- **Files:** `tests/orders/duplicate-email.test.ts` (extend), `tests/orders/order-flow.test.ts` (verify passes)
- **Depends on:** Task 2, Task 3
- **Validates:** Unchanged Behavior section (no regressions)

## Progress

- Total tasks: 4
- Completed: 0
- Remaining: 4
