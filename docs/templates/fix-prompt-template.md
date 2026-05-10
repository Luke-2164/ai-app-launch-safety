# AI-ready Fix Prompt Template

Use this template to turn a finding into a paste-ready prompt for Cursor, Lovable, Replit Agent, Bolt, or another AI builder.

## Template

```text
I found a pre-launch risk in my web app.

Finding:
[Describe the finding]

Risk:
[Explain why it matters]

Evidence:
[Include safe, non-sensitive evidence]

Please help me fix this by:
1. Explaining the likely cause.
2. Showing the safest implementation approach.
3. Updating the relevant code or configuration.
4. Avoiding changes that expose secrets in the browser.
5. Adding a short verification checklist.

Important constraints:
- Do not remove authentication or authorization checks.
- Do not move private secrets to client-side code.
- Do not weaken existing security settings.
- Explain any trade-offs.
```

## Example: Missing CSP

```text
I found a pre-launch risk in my web app.

Finding:
Content-Security-Policy header was not detected.

Risk:
This does not prove the app is vulnerable, but CSP can reduce the impact of XSS and unwanted script loading.

Please help me add a basic CSP for a Next.js app. Start with a practical policy, explain each directive, and show me where to configure it.
```

## Example: Public admin route

```text
I found a pre-launch risk in my web app.

Finding:
/admin returned HTTP 200 without an obvious login redirect.

Risk:
If this route contains private or admin-only features, it should be protected server-side.

Please review the route protection pattern and help me add authentication and authorization checks. Unauthenticated users should be redirected to login, and non-admin users should receive a 403 response.
```
