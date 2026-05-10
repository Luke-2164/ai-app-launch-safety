# Firebase Rules Review Notes

Firebase client configuration can be public, but Firestore, Realtime Database, and Storage Rules must match the app's privacy expectations.

## Common risks

- Public read access to private user data
- Public write access to database collections
- Storage files accessible without intended restrictions
- Rules that trust user-provided IDs without checking ownership

## Review checklist

- [ ] Public read is intentional.
- [ ] Public write is not allowed for private collections.
- [ ] Authenticated users can only read their own records where required.
- [ ] Authenticated users can only write their own records where required.
- [ ] Storage rules restrict private uploads.
- [ ] Rules are tested before launch.

## Safe report wording

```text
Firebase usage was detected. Firebase client configuration can be public, but database and storage rules should be reviewed before launch.
```
