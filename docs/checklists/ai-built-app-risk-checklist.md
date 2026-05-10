# AI-built App Risk Checklist

This checklist summarizes common risks that appear in fast-built web apps created with AI app builders, coding agents, and low-code tools.

## Common risk categories

| Category | Risk | Why it matters |
|---|---|---|
| Exposed secrets | Private keys appear in public HTML or JavaScript | Attackers may spend API credits, access services, or compromise accounts |
| Broken access control | Users can view records they do not own | Customer or business data may leak |
| Public storage | Uploaded files are publicly reachable | Private documents, screenshots, or customer files may leak |
| Weak production settings | Debug or test pages remain public | Internal behavior and data may be exposed |
| Missing hardening headers | Browser protections are missing | XSS, clickjacking, and data leakage impact may increase |
| No abuse controls | Expensive AI/email actions can be triggered repeatedly | Costs can spike or forms can be abused |
| No logging or recovery | Incidents are hard to detect or investigate | Operators may not know what happened or how to recover |

## Priority order for a first review

1. Check for exposed secrets.
2. Check protected pages and admin/debug routes.
3. Check public storage and exposed files.
4. Check basic Supabase / Firebase configuration assumptions.
5. Check security headers.
6. Check expensive actions such as AI calls and email sending.
7. Summarize what data the app stores and what would be harmful if leaked.

## Recommended positioning

This checklist should support a pre-launch risk review.

It should not be positioned as a complete security audit or penetration test.
