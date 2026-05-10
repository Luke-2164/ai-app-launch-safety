# Sample Launch Risk Report

This is a sample structure for a human-reviewed Launch Risk Report.

## Executive summary

The app appears close to launch, but several pre-launch risks should be reviewed before accepting real users, payments, or sensitive data.

## Risk overview

| Severity | Count |
|---|---:|
| High | 1 |
| Medium | 3 |
| Low | 2 |
| Info | 4 |

## Recommended launch decision

```text
Hold launch until High findings are resolved.
Launch may proceed after Medium findings are accepted or mitigated.
```

## Priority fixes

1. Remove exposed private keys from public JavaScript.
2. Confirm Supabase RLS on user-owned tables.
3. Protect admin and dashboard routes server-side.
4. Add basic security headers.
5. Add rate limits for AI API actions.

## Data handled

- Email addresses
- User-generated text
- Uploaded images
- Payment checkout metadata

## Human review notes

This report combines automated public-facing checks with a manual review of app behavior and provided context.

## Re-check plan

After fixes are applied, run the Lite Check again and manually confirm:

- Exposed key is no longer present
- Admin route requires authorization
- RLS or equivalent access control is enabled
- Security headers are present
- AI API route has rate limiting

## Disclaimer

This report is not a full penetration test, source-code audit, compliance certification, or legal privacy review. It does not guarantee that the app is secure.
