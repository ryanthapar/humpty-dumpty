# Humpty Dumpty — Landing Page

Static landing page for the **Humpty Dumpty** coaching program: a weekly, in-person
scripts/objections/skills mastery program for seasoned real estate agents.

## Stack

Single-file static site. `index.html` with Tailwind via CDN — no build step, no
dependencies. Open the file in a browser to preview, or serve it locally:

```
python3 -m http.server 8000
```

## Deployment

Deploys to GitHub Pages via `.github/workflows/pages.yml` on every push to `main`.

One-time setup: **Settings → Pages → Build and deployment → Source: GitHub Actions**.

## Placeholders still to fill

The page ships with the copy that is settled and visible `[BRACKETED]` placeholders
for the decisions that are not. Search `index.html` for `TODO:` to find each one.

| Placeholder | Where | Decision needed |
| --- | --- | --- |
| `$[PRICE]` | Pricing section | Monthly price |
| `[PAYMENT TERMS]` | Pricing section | Month-to-month vs. 3-month minimum |
| `$[INCOME THRESHOLD]` | Who It's For | $150K or $200K guideline |
| Launch special | Pricing sidebar | Whether there is an intro offer, and what |
| Form `action` | Apply section | Form handler endpoint (Formspree / Google Form / CRM) |
| `og:image`, `og:url` | `<head>` | Social share image and live domain |
| Footer attribution | Footer | Brand/brokerage line and contact details |

Instructor, cohort start date, and venue are not yet on the page — add them once confirmed.
