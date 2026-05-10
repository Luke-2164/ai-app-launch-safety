# Exposed Secrets in AI-built Apps

Exposed secrets are one of the fastest ways for a small app to become risky after launch.

## Common examples

- OpenAI API keys
- Stripe secret keys
- Supabase service_role keys
- GitHub tokens
- AWS access keys
- Private webhook signing secrets

## Public vs private keys

Some keys are designed to be public, but still need restrictions.

| Key type | Browser exposure | Notes |
|---|---|---|
| Stripe publishable key | Usually okay | Must not be confused with secret key |
| Stripe secret key | Not okay | Server-side only |
| Supabase anon key | Usually okay | RLS and policies must be correct |
| Supabase service_role key | Not okay | Server-side only |
| OpenAI API key | Not okay | Server-side only |
| Firebase client config | Usually okay | Rules must be correct |

## Review checklist

- [ ] Search public HTML for secret-like values.
- [ ] Search public JavaScript bundles for secret-like values.
- [ ] Confirm private keys are only used server-side.
- [ ] Confirm public keys have restrictions where possible.
- [ ] Rotate any key that may have been exposed.

## Safe report wording

```text
A secret-like value was detected in public-facing code. This should be verified by the app owner. If this is a private secret, remove it from client-side code and rotate it before launch.
```
