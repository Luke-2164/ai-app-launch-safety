# Supabase RLS Review Notes

Supabase is common in AI-built apps. The most important launch-safety topic is whether user-owned data is protected with Row Level Security.

## Key concepts

- `anon` key can be public, but policies must be correct.
- `service_role` key must stay server-side.
- RLS should be enabled on tables that store user-owned or tenant-owned data.
- Policies should usually compare row ownership to `auth.uid()`.

## Common policy pattern

```sql
CREATE POLICY "Users can read own rows"
ON documents
FOR SELECT
TO authenticated
USING (user_id = auth.uid());
```

## Review checklist

- [ ] `service_role` key is not exposed in client-side code.
- [ ] RLS is enabled on user-owned tables.
- [ ] SELECT policies check owner/user/tenant.
- [ ] INSERT policies ensure new rows belong to the current user.
- [ ] UPDATE policies prevent editing another user's rows.
- [ ] DELETE policies prevent deleting another user's rows.
- [ ] Storage buckets are public only when intentionally public.

## Safe report wording

```text
Supabase usage was detected. This is not a risk by itself, but RLS and storage policies should be reviewed before launch, especially if the app stores user-owned or business data.
```
