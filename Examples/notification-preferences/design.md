# Notification Preferences — Design

## Architecture

This feature adds a preferences layer between the notification generation system and the delivery system. The existing `NotificationService` will check preferences before dispatching.

```
User → Preferences UI → Preferences API → preferences table
                                               ↓
Notification triggered → NotificationService → check preferences → deliver (or skip)
```

## Components

### PreferencesAPI

**Responsibility:** CRUD operations for user notification preferences
**Endpoints:**
- `GET /api/users/:id/notification-preferences` → returns all preferences
- `PUT /api/users/:id/notification-preferences` → updates preferences (partial update)
- `POST /api/users/:id/notification-preferences/mute-all` → toggles mute
**Errors:** 401 (not authenticated), 403 (not own preferences), 422 (invalid category/channel)

### PreferencesStore

**Responsibility:** Database access for notification preferences
**Location:** `src/features/notifications/preferences-store.ts`
**Uses:** Existing `db` utility from `src/lib/database.ts`

### NotificationPreferencesUI

**Responsibility:** Settings page component for managing preferences
**Location:** `src/features/notifications/components/NotificationPreferences.tsx`
**Uses:** Existing `ToggleSwitch` component from `src/components/ui/`

## Data Model

New table: `notification_preferences`

| Column | Type | Notes |
|--------|------|-------|
| id | UUID | Primary key |
| user_id | UUID | FK to users, unique per user+category+channel |
| category | VARCHAR(50) | e.g., "marketing", "product_updates", "security" |
| channel | VARCHAR(20) | "email", "in_app", "push" |
| enabled | BOOLEAN | Default: true |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

Index on `(user_id, category, channel)` — unique constraint.

New column on `notification_categories` table: `mandatory BOOLEAN DEFAULT false`

## Integration Points

- `NotificationService.send()` — Add preference check before dispatch. Use existing service at `src/services/notification-service.ts`.
- `src/lib/email.ts` — No changes; preferences are checked before email is triggered.

## Error Handling

- If preferences table is unreachable, **deliver the notification** (fail-open for user experience).
- If an invalid category is submitted, return 422 with the list of valid categories.

## Testing Strategy

- Unit tests: PreferencesStore CRUD, mute-all logic, mandatory override
- Integration tests: API endpoints with auth
- E2E test: Toggle a preference, trigger a notification, verify delivery/non-delivery
