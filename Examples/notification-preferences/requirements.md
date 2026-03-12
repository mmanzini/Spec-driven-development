# Notification Preferences — Requirements

## Objective

Allow users to control which notifications they receive and through which channels, reducing complaints and unsubscribes while preserving delivery of critical communications.

## Requirements

### R1: Preference Access

As a logged-in user, I want to access my notification preferences from account settings, so that I can control what notifications I receive.

**Acceptance criteria:**
- Given a logged-in user, when they navigate to account settings, then they see a "Notification Preferences" section
- Given a logged-in user on mobile, when they access notification preferences, then the UI is fully functional on screen widths from 320px

### R2: Per-Category Toggle

WHEN a user views notification preferences
THE SYSTEM SHALL display all notification categories with independent on/off toggles for each channel (email, in-app, push).

**Acceptance criteria:**
- [ ] Each category shows toggles for: email, in-app, push
- [ ] Toggles reflect the user's current saved preferences
- [ ] Default state for new users: all channels enabled for all categories

### R3: Mute All

As a user overwhelmed by notifications, I want a single "Mute All" toggle so that I can quickly silence everything non-critical.

**Acceptance criteria:**
- Given a user who enables "Mute All", then all non-mandatory notification toggles are set to off
- Given a user who disables "Mute All", then preferences return to their state before muting
- Mandatory notifications (security alerts) remain enabled regardless of "Mute All"

### R4: Immediate Effect

WHEN a user changes a notification preference
THE SYSTEM SHALL apply the change immediately to all subsequent notifications without requiring page refresh or re-authentication.

**Acceptance criteria:**
- [ ] Changes are persisted within 1 second
- [ ] Next notification respects the updated preference
- [ ] No page refresh or re-login required

### R5: Mandatory Notifications

IF a notification is categorized as mandatory (security alerts, account actions)
THEN THE SYSTEM SHALL always deliver it regardless of user preferences, and the corresponding toggles SHALL be disabled with an explanatory tooltip.

**Acceptance criteria:**
- [ ] Mandatory category toggles are visually disabled
- [ ] Hovering/tapping a disabled toggle shows "This notification cannot be disabled for your security"
- [ ] Mandatory notifications are always delivered even when "Mute All" is active

## Boundaries

### Always
- Preserve the user's pre-mute preferences when "Mute All" is toggled off
- Show mandatory notifications as disabled with explanation (never hide them)

### Ask
- Before adding a new notification category to the system

### Never
- Never allow mandatory notifications to be disabled
- Never require re-authentication to change preferences
