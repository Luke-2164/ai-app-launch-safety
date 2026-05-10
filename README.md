# AI App Launch Safety

Public checklists and sample reports for pre-launch safety reviews of AI-built web apps.

AI App Launch Safety is a public resource hub for builders shipping web apps with AI app builders such as Lovable, Replit, Bolt, Base44, Cursor, and similar tools.

It provides practical checklists, sample reports, and templates for spotting common public-facing risks before sharing or launching an AI-built app.

## What this repository is for

- Public launch-safety checklists
- Sample Lite Check and Launch Risk Report formats
- Plain-English guides for common AI-built app risks
- Report and fix-prompt templates
- Public positioning and education content

## What this repository does not include

- Private scanning engine code
- Paid detection logic
- Customer data
- Real scan results
- Real secret values
- Exploit payloads or destructive testing instructions
- Billing, admin, or report-generation backend code

## Recommended starting points

- [Pre-launch Lite Check checklist](docs/checklists/pre-launch-lite-check.md)
- [Sample Lite Check report](docs/sample-reports/sample-lite-check-report.md)
- [Report template](docs/templates/report-template.md)
- [AI-ready fix prompt template](docs/templates/fix-prompt-template.md)

## Disclaimer

This repository is for educational and pre-launch risk-review purposes only.

It is not a full security audit, penetration test, compliance certification, or legal privacy review. It does not guarantee that an app is secure.

Only review apps you own or have explicit permission to test.

## Private product repository

The private implementation repository is intentionally separate from this public resource hub.

Public repo:

```text
ai-app-launch-safety
```

Private repo:

```text
launch-lite-check
```

The public repository builds trust and distribution. The private repository contains the actual scanner, report generation, customer workflow, and paid product code.
