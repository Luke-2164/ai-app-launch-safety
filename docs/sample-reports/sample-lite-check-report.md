# Sample Lite Check Report

This is a sample format for a lightweight pre-launch risk report.

## Summary

| Field | Value |
|---|---|
| App | Demo AI-built app |
| URL | `https://example-ai-app.test` |
| Report type | Lite Check |
| Review date | 2026-05-10 |
| Overall risk | Medium |

## Scope

This Lite Check reviewed common public-facing risk signals based on the provided URL.

## What was checked

- HTTP status and redirect behavior
- Public response security headers
- HTML and JavaScript bundle secret-like patterns
- Common admin, debug, test, and dashboard routes
- Common exposed files such as `.env`, `.git/config`, and backups
- Public-facing technology hints

## What was not checked

- Full penetration testing
- Source-code audit
- Authenticated user-to-user authorization testing
- Database policy correctness
- Compliance certification
- Destructive or high-volume testing
- Guarantee that the app is secure

## Findings

### Finding 1: Content-Security-Policy header was not detected

Severity: Medium  
Confidence: High  
Category: Headers

Description:

Content-Security-Policy was not present in the public HTTP response. This does not prove the app is exploitable, but CSP can reduce the impact of XSS and unwanted script loading.

Suggested fix:

Add a basic Content-Security-Policy and tighten it over time.

AI-ready fix prompt:

```text
Add a basic Content-Security-Policy header to this web app. Start with a conservative policy that supports the current scripts and styles, and explain any domains that must be allowed.
```

---

### Finding 2: Common route returned HTTP 200: `/admin`

Severity: Medium  
Confidence: Medium  
Category: Routes

Description:

A common admin route returned HTTP 200 without an obvious login redirect. This does not prove a vulnerability, but it should be reviewed before launch.

Suggested fix:

Confirm this route is intended to be public. If not, protect it with server-side authorization.

AI-ready fix prompt:

```text
Review the /admin route. If it should be private, add server-side authentication and authorization checks. Redirect unauthenticated users to login and block non-admin users with a 403 response.
```

## Disclaimer

This sample report is not a full security audit or penetration test. It does not guarantee that an app is secure.
