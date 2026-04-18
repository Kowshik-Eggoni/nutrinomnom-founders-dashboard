# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A single-page brand & experience assessment dashboard for NutriNomNom Foods LLP (two brands: NutriNomNom meal subscriptions, and 20g shelf-stable protein products). The dashboard is consumed by the founder (Kowshik) and his co-founder/wife to track findings, a prioritized action plan, and open decisions across `nutrinomnom.com`, `20g.nutrinomnom.com`, and the 20g Design Guidelines.

Live URL: https://kowshik-eggoni.github.io/nutrinomnom-founders-dashboard/

## Architecture

**One file does everything.** `index.html` is a self-contained ~56KB page with inline `<style>` and inline `<script>` — no build step, no bundler, no dependencies, no package.json. Edit `index.html` directly; there is nothing to compile.

### Three-tab structure

The page has three tab panels (`#tab-findings`, `#tab-actions`, `#tab-questions`) switched by `showTab()`. The Action Plan tab contains N task items with IDs `t1`..`tN`, each clickable via `toggleTask('tN')`. The `TOTAL` constant in the `<script>` block must match the number of tasks rendered — update both together when adding/removing tasks.

### Task persistence (important — this is the non-obvious part)

Task completion state has a deliberate two-layer persistence model, so the co-founder on a different device sees the same progress:

1. **URL hash is the source of truth for sharing.** `saveTasks()` writes done tasks as `#t=1,3,7` on the URL. `loadTasks()` reads the hash first. The "Copy link" button in the header lets the user share current progress across devices.
2. **localStorage (`nutrinomnom_tasks_v1`) is the fallback** for same-device persistence when no hash is present.

If you change task IDs or the `STORAGE_KEY`, you will silently invalidate everyone's saved progress. Bump the key suffix (`_v2`, …) intentionally when you do.

## Common tasks

- **Edit the dashboard:** modify `index.html` directly.
- **Preview locally:** open `index.html` in a browser — no server needed. For live-reload, any static server works (`python -m http.server`, `npx serve`, etc.).
- **Deploy:** `git push` to `main`. GitHub Pages rebuilds from `main` / root in ~45 seconds. There is no CI, no tests, no lint step.
- **Add a new action-plan task:** add a `<div class="task-item" id="tN" onclick="toggleTask('tN')">…</div>` block inside the appropriate priority section, and increment `TOTAL` in the `<script>` block and the count shown in the tab button (`#actions-count` and the hard-coded `20` in the tab label).

## Business context that should shape suggestions

- Revenue is ~₹2–3.5L/month from NNN meal subscriptions and ~₹25k/month from 20g (new). Goal: double both.
- **WordPress on nutrinomnom.com is expiring** — a migration decision is pending (GCP/AWS free credits being evaluated). Don't suggest WordPress-dependent fixes.
- The founder is self-taught and vibe-codes; prefer concrete, minimal edits to this single file over introducing tooling, frameworks, or build steps.
