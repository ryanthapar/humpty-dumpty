# Humpty Dumpty — Landing Page

Static landing page for the **Humpty Dumpty** coaching program: the continuing education
track for **Fast Track Farming 101** graduates — a biweekly, in-person
scripts/objections/skills mastery program.

Every Fast Track Farming 101 grad is automatically eligible. There is no application —
the page links straight to registration.

## Stack

Single-file static site. `index.html` with Tailwind via CDN — no build step, no
dependencies. Open the file in a browser to preview, or serve it locally:

```
python3 -m http.server 8000
```

## Branding

Colours and component patterns come from the sibling landing page,
[`ryanthapar/farming-fast-track`](https://github.com/ryanthapar/farming-fast-track)
("Let's Farm with Monica Thapar"). The tokens are duplicated in two places in
`index.html` and **must be kept in sync with each other and with the sibling repo**:

1. `:root` custom properties — copied verbatim from the sibling, source of truth
   for the hand-written component CSS (`.display`, `.eyebrow`, `.btn`, …).
2. The `tailwind.config` colour map — the same hex values, so Tailwind utilities
   (`bg-surface`, `text-slate-deep`, `border-line`) resolve to the brand palette.

| Token | Value | Role |
| --- | --- | --- |
| `--ground` | `#ffffff` | Page background |
| `--surface` / `--surface-2` | `#f5f8fa` / `#eaf0f3` | Alternating section fills, cards |
| `--slate` / `--slate-deep` | `#37576b` / `#294452` | Headings; `--slate` also backs the dark bands |
| `--body` / `--muted` | `#4a5257` / `#7b868d` | Body copy, secondary text |
| `--red` | `#e02d24` | Action only — primary CTA, price anchor |
| `--green` | `#4f9c3a` | Affirmative — ticks, accent rules, FAQ markers |
| `--blue` | `#97ccde` | Fills, bars and accents only (1.75:1 on white — never body text) |
| `--blue-ink` | `#2a7a96` | The same hue darkened for legible text (4.86:1 on white) |
| `--line` | `#e3e9ec` | Hairlines and card borders |

Two brand rules carried over from the sibling site:

- **Red is reserved for asking.** Primary CTAs and the price anchor only; the red
  eyebrow appears once, on the registration section.
- **`--blue` never carries text on white.** Use `--blue-ink` for anything readable;
  `--blue` is for fills, top rules and eyebrows on the dark slate bands.

Typography matches the sibling too: the system font stack, with headings at weight
900, uppercase and tight tracking. There are no webfont downloads.

## Deployment

Deploys to GitHub Pages via `.github/workflows/pages.yml` on every push to `main`.

One-time setup: **Settings → Pages → Build and deployment → Source: GitHub Actions**.

## Source material

The curriculum (the "Here's What Humpty Dumpty Includes" cards), the cadence, the
price, the payment terms and the December launch offer all come from an official
promotional flyer ("Humpty Dumpty — Real Estate Agent Mastermind"), which superseded
an earlier, rougher 12-topic list drawn from internal meeting notes. If the flyer and
this page ever diverge, treat the flyer (or whatever replaces it) as the source of
truth and update `index.html` to match.

The "for driven agents" framing in the Who It's For section and its matching FAQ entry
also come from that flyer — it describes the audience as "motivated and serious about
success" with no income figure, so the page does not state an income threshold.

## Placeholders still to fill

The page ships with the copy that is settled and visible `[BRACKETED]` placeholders
for the decisions that are not. Search `index.html` for `TODO:` to find each one.

| Placeholder | Where | Decision needed |
| --- | --- | --- |
| `og:image`, `og:url` | `<head>` | Social share image and live domain |
| Footer attribution | Footer | Brand/brokerage line and contact details |

Price, payment terms and the launch offer are resolved: **$599 + HST / month, minimum
three-month commitment**, with **"Join today, get December free"** on the pricing card
and in a site-wide announcement bar above the nav.

## Registration

The registration section (`#apply`) links straight to a Square-hosted checkout page —
there is no intake form on the site itself, so registering **is** paying. Every other
"Register" CTA on the page (nav, hero, pricing card, sticky mobile bar) scrolls to this
one section rather than linking to Square directly, so it stays the single place that
sends money off-site.

The Square link was supplied directly and has not been test-clicked from this
environment — this sandbox's egress policy blocks `checkout.square.site`, the same way
it blocks the Tailwind CDN (see below). Click it once yourself before pointing real
traffic at the page.

Instructor, cohort start date, and venue are not yet on the page — add them once confirmed.
