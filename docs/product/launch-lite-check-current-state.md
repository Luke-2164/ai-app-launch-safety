# Launch Lite Check current public product state

Last updated: 2026-05-17

This document records the public-facing product state of Launch Lite Check without exposing private scanner implementation code, customer data, secrets, or paid backend internals.

## Product purpose

Launch Lite Check helps builders run a quick public-facing pre-launch check for AI-built web apps before sharing them publicly.

The tool is designed for builders using AI app builders and coding assistants such as Lovable, Replit, Bolt, Base44, Cursor, and similar tools.

It is not a full security audit, penetration test, compliance certification, or legal privacy review.

## Current offer ladder

| Tier | State | Purpose |
| --- | --- | --- |
| Free Launch Lite Check | Built and deployed | No-save URL check for limited public-facing risk signals |
| $19 Saved Lite Report | Built as MVP flow | Creates a saved report URL with more detail, evidence, app context, and AI-ready fix prompts |
| $49 Advanced Automated Report | Built as MVP flow | Adds advanced automated triage, launch-blocker style prioritization, and app-context-specific recommendations |

## Current free check behavior

The free check:

- Requires the user to confirm that they own the app or have explicit permission to test it.
- Does not require an email address.
- Does not save the report.
- Does not write to the database.
- Runs a limited public-facing scan against the submitted URL.
- Shows overall risk, score, checked areas, not-checked areas, and top findings.

## Current public-facing checks

The current scanner checks these categories at a high level:

- HTTP status and redirect behavior.
- Public response security headers.
- HTML and JavaScript bundle secret-like patterns.
- A small set of common admin, debug, test, dashboard, and settings routes.
- A small set of common exposed files such as `.env`, `.git/config`, and backups.
- Technology hints for common stacks such as Next.js, Supabase, Firebase, Stripe, OpenAI, and Vercel.

## Current result design

Findings are separated into two groups:

1. **Potential launch risks**
   - High, medium, and low severity findings.
   - These are shown as possible issues that may need attention before launch.

2. **Technology hints**
   - Informational findings.
   - These are not vulnerabilities by themselves.
   - They help the builder remember stack-specific checks, such as Supabase RLS, Stripe webhook verification, and `NEXT_PUBLIC_` environment variable boundaries.

When only informational technology hints are found, the free page positions the $19 report as a saved launch record rather than as fear-based risk escalation.

## Current safety posture

The current product includes several safety-oriented controls:

- Permission confirmation before a scan can run.
- Hosted scanner rejects `localhost` and private, loopback, and link-local IP address inputs.
- URL length is capped.
- Only `http://` and `https://` URLs are supported.
- Hash fragments are removed from scanned URLs.
- Request timeout is capped.
- HTML and script byte reads are capped.
- Script fetch count is capped.
- Common route and exposed-file checks are capped.
- Scanner uses a clear product user agent.
- Scanner is designed to avoid destructive or high-volume testing.
- The product uses baseline response security headers on its own deployed app.

## Current limitations

The current product does not yet include all abuse controls needed for broader distribution.

Known gaps:

- No app-level rate limiting yet.
- No CAPTCHA, Turnstile, or human verification yet.
- No persistent abuse log yet.
- No IP/user-agent based throttling yet.
- No blocklist or allowlist management UI yet.
- URL validation does not yet re-check the final resolved/redirected destination against private network ranges.
- Hostname DNS resolution and DNS rebinding protections are not yet complete.
- Manual payment reference fallback should be tightened before wider launch.

## Recommended next hardening work

Before broader public launch, prioritize:

1. Add app-level rate limiting to free and paid scan APIs.
2. Add stronger SSRF protection, including redirect/final URL validation and private-network checks after redirects.
3. Add abuse logging for scan requests, including normalized host, timestamp, result, and coarse request metadata.
4. Add Turnstile or an equivalent human-verification step when rate thresholds are exceeded.
5. Tighten paid report access so manual payment references are removed or restricted before real public sales.
6. Add monitoring for scan volume, error rate, timeout rate, and repeated scans against third-party domains.

## Public/private repository rule

This public repository may document:

- Product positioning.
- Public checklists.
- Sample reports.
- High-level architecture.
- Public safety rules.
- Non-sensitive operational notes.

This public repository must not include:

- Private scanner source code.
- Paid backend implementation details.
- Real customer scan data.
- Secret values.
- Exploit payloads.
- Instructions for destructive testing.
- Internal abuse-detection bypass details.
