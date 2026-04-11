# Notification Preferences — Tasks

**Spec:** [[Business/Documentation & Research/Spec driven development/Examples/notification-preferences/requirements]] | [[Business/Documentation & Research/Spec driven development/Examples/notification-preferences/design]]
**Status:** Not started

### 1. Create notification preferences database migration

- [ ] **Status:** Not started
- **Description:** Create `notification_preferences` table with columns defined in design. Add `mandatory` boolean column to existing `notification_categories` table. Set `mandatory = true` for "security" and "account_actions" categories.
- **Files:** `src/db/migrations/xxx-notification-preferences.ts`
- **Depends on:** None
- **Validates:** R2 (data model for per-category toggles)

### 2. Implement PreferencesStore

- [ ] **Status:** Not started
- **Description:** Create data access layer with methods: `getByUserId(userId)`, `upsert(userId, category, channel, enabled)`, `muteAll(userId)`, `unmuteAll(userId)`. Use existing `db` utility from `src/lib/database.ts`.
- **Files:** `src/features/notifications/preferences-store.ts`
- **Depends on:** Task 1
- **Validates:** R2, R3, R4

### 3. Implement PreferencesAPI endpoints

- [ ] **Status:** Not started
- **Description:** Create GET, PUT, and POST (mute-all) endpoints as defined in design. Include auth middleware. Return 401/403/422 for error cases. PUT supports partial updates.
- **Files:** `src/features/notifications/preferences-api.ts`, `src/routes/api.ts` (register routes)
- **Depends on:** Task 2
- **Validates:** R1, R2, R3, R4

### 4. Add preference check to NotificationService

- [ ] **Status:** Not started
- **Description:** Before dispatching a notification, check user preferences. Skip delivery if the category+channel is disabled. Always deliver if `mandatory = true` on the category. Fail-open if preferences table is unreachable.
- **Files:** `src/services/notification-service.ts`
- **Depends on:** Task 2
- **Validates:** R4, R5

### 5. Build NotificationPreferencesUI component

- [ ] **Status:** Not started
- **Description:** Create settings page component showing all categories with per-channel toggles. Disable toggles for mandatory categories with tooltip. Include "Mute All" toggle at top. Use existing `ToggleSwitch` from `src/components/ui/`. Responsive from 320px.
- **Files:** `src/features/notifications/components/NotificationPreferences.tsx`
- **Depends on:** Task 3
- **Validates:** R1, R2, R3, R5

### 6. Implement Mute All with preference preservation

- [ ] **Status:** Not started
- **Description:** When "Mute All" is activated, store current preferences snapshot, then set all non-mandatory to disabled. When deactivated, restore from snapshot. Ensure mandatory categories are never affected.
- **Files:** `src/features/notifications/preferences-store.ts`, `src/features/notifications/components/NotificationPreferences.tsx`
- **Depends on:** Task 5
- **Validates:** R3, R5

### 7. Write tests

- [ ] **Status:** Not started
- **Description:** Unit tests for PreferencesStore (CRUD, mute/unmute, mandatory override). Integration tests for API endpoints (auth, validation, partial update). E2E test for toggle → notification delivery flow.
- **Files:** `tests/features/notifications/preferences-store.test.ts`, `tests/features/notifications/preferences-api.test.ts`, `tests/e2e/notification-preferences.test.ts`
- **Depends on:** Task 6
- **Validates:** All requirements

## Progress

- Total tasks: 7
- Completed: 0
- Remaining: 7
