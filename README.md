# NutriNomNom Founders Dashboard

**Live URL:** https://kowshik-eggoni.github.io/nutrinomnom-founders-dashboard/

---

## What this is

A CXO-level brand & experience assessment dashboard built by Claude (April 2026). Covers nutrinomnom.com, 20g.nutrinomnom.com, and the 20g Design Guidelines. Three tabs: What We Found / Action Plan (checkable tasks) / Decisions to Make.

The action plan tasks are checkable and persist in the browser (localStorage). Your cofounder can check things off and track progress.

---

## Business context (for Claude in future sessions)

- **NutriNomNom Foods LLP** — two brands: NutriNomNom (meal subscriptions) and 20g by NutriNomNom (shelf-stable protein products, 20g protein per serving)
- **Revenue:** ₹2–3.5L/month from NNN meal subs, ~₹25k/month from 20g (new)
- **Goal:** Double both revenue streams as fast as possible
- **Founder:** Kowshik Eggoni — self-taught, vibe-codes his way through requirements, not a CS background
- **Co-founder/wife:** also involved, uses this dashboard

### Key open items (as of April 2026)
1. **WordPress expiring this month** — nutrinomnom.com needs to migrate off WordPress (Business Plan tier). Decision pending on where to redeploy (GCP/AWS free credits being explored).
2. **20g brand** — strong visual identity but online presence is thin. Core fix: beef up 20g.nutrinomnom.com with product content, pricing, and a buy flow.
3. **NNN brand** — nutrinomnom.com has trust signals and good copy but no clear subscription CTA above the fold.

---

## How to update the dashboard

Ask Claude: *"Update the founders dashboard with [whatever changed]."*

Claude will edit `index.html` directly in this repo. GitHub Pages auto-redeploys in ~45 seconds. No manual steps needed.

---

## Repo structure

```
index.html   ← the dashboard (single self-contained file, ~55KB)
README.md    ← this file (context for Claude in future sessions)
```

---

## GitHub Pages setup

- Source: `main` branch, `/ (root)` folder
- Auto-deploys on every push to main
- Custom domain: not set (using default kowshik-eggoni.github.io subdomain)
