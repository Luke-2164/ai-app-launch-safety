# Authentication and Authorization

Authentication and authorization are different.

```text
Authentication = Who are you?
Authorization = Are you allowed to access this resource?
```

AI-built apps often appear to have login, but still miss object-level authorization.

## Common examples

- A logged-in user can access another user's `/projects/123` page.
- A dashboard API returns records without checking `user_id` or `tenant_id`.
- Admin pages only hide buttons in the UI but do not enforce server-side authorization.
- API routes trust IDs from the browser without checking ownership.

## Review checklist

- [ ] Protected pages redirect unauthenticated users.
- [ ] API routes verify the current user server-side.
- [ ] User-owned records check `owner_id`, `user_id`, or `tenant_id`.
- [ ] Admin routes check admin permission server-side.
- [ ] UI-only hiding is not used as the only protection.
- [ ] Test users A and B cannot access each other's data.

## Safe report wording

```text
A route or API appears to expose user-specific data by ID. Manual review is recommended to confirm server-side authorization checks are present.
```
