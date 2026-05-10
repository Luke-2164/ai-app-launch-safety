# Pre-launch Lite Check Checklist

A lightweight checklist for AI-built web apps before they are shared publicly, submitted to Product Hunt, handed off to a client, or used with real users.

## Scope

This checklist focuses on public-facing risks that can often be spotted before launch.

It is not a full penetration test or security audit.

## 1. Ownership and permission

- [ ] I own this app or have explicit permission to review it.
- [ ] I will not perform destructive or high-volume testing.
- [ ] I will not attempt to bypass login, brute-force accounts, or extract private data.

## 2. Exposed secrets

Check public HTML and JavaScript bundles for secret-like values.

- [ ] OpenAI API keys are not exposed in the browser.
- [ ] Stripe secret keys are not exposed in the browser.
- [ ] Supabase service_role keys are not exposed in the browser.
- [ ] GitHub tokens are not exposed in the browser.
- [ ] AWS access keys are not exposed in the browser.
- [ ] Public keys, if present, are restricted by domain, API, and quota where possible.

## 3. Security headers

- [ ] Content-Security-Policy is present or intentionally deferred.
- [ ] Strict-Transport-Security is present for HTTPS production apps.
- [ ] X-Content-Type-Options is present.
- [ ] Referrer-Policy is present.
- [ ] X-Frame-Options or CSP frame-ancestors is present when embedding should be blocked.

## 4. Public admin and debug routes

Review common routes and make sure sensitive ones are protected.

- [ ] `/admin` is not publicly accessible unless intended.
- [ ] `/dashboard` is protected if it contains user or business data.
- [ ] `/settings` is protected.
- [ ] `/account` is protected.
- [ ] `/debug`, `/test`, and `/dev` are not public in production.
- [ ] `/api/admin`, `/api/users`, and `/api/debug` are not exposed without authorization.

## 5. Exposed files

- [ ] `.env` files are not publicly reachable.
- [ ] `.git/config` is not publicly reachable.
- [ ] SQL dumps are not publicly reachable.
- [ ] Backup archives are not publicly reachable.
- [ ] Build artifacts do not expose sensitive configuration.

## 6. Supabase / Firebase basics

- [ ] Supabase service_role key is server-side only.
- [ ] Supabase RLS is enabled on user-owned tables.
- [ ] Supabase storage buckets are public only when intentionally public.
- [ ] Firebase Security Rules do not allow unintended public read/write access.
- [ ] Firebase Storage Rules match the app's privacy expectations.

## 7. Abuse and cost control

- [ ] AI API actions are rate limited.
- [ ] Email-sending actions are rate limited.
- [ ] File uploads have size and type limits.
- [ ] Public forms have spam protection or abuse limits.

## 8. Report wording

Use cautious wording.

Prefer:

```text
Potential risk detected.
Manual review recommended before launch.
```

Avoid:

```text
Your app is secure.
Your app is vulnerable.
```
