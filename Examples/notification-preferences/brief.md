# Notification Preferences — Product Brief

## Problem Statement

Users receive all notification types (email, in-app, push) by default and have no way to control which notifications they receive. This generates complaints (~50/month) and contributes to email unsubscribes (12% monthly unsubscribe rate).

## User Need

Users need to choose which types of notifications they receive and through which channels. Power users want granular control; casual users want a simple on/off.

## Success Metrics

- Reduce notification-related complaints by 70%
- Reduce email unsubscribe rate from 12% to under 5%
- 60% of active users customize their preferences within 3 months

## Scope

### In Scope

- Notification preferences UI in account settings
- Per-category and per-channel toggles
- A "mute all" quick action
- Persisting preferences and applying them to notification delivery

### Out of Scope

- Notification history / log viewing
- Notification scheduling (e.g., "send only between 9am-5pm")
- SMS as a notification channel (future consideration)

## Constraints

- Must work on mobile and desktop
- Must not require re-authentication to change preferences
- Changes must take effect immediately (no batch processing delay)

## Open Questions

- [ ] How many notification categories do we currently have? (Need inventory)
- [ ] Are there any notifications that must always be sent regardless of preferences (e.g., security alerts)?
