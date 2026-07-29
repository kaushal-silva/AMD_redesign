# AMD Platform — Prototype Portal

A single deployable folder containing a **landing page** plus **six role-specific site mocks**. Deploy the whole `amd-portal` folder to Netlify; the landing page (`index.html`) links to each site.

> All sites are **clickable front-end mocks with sample data** — no login, no backend, no real records. They exist to run per-site feedback sessions before handing specs to engineers.

## Structure

```
amd-portal/
  index.html          ← landing page (links to all sites)
  patient-app/        ← Patient PWA (mobile, installable)   [MVP]
  doctor-site/        ← AMD + ATC clinical tool             [MVP]
  hq-site/            ← AMD Taiwan HQ: IP upload, STA, KPIs  [MVP core]
  md-pt-site/         ← Referred specialists (least-access) [Phase 2]
  felix-site/         ← Dr. Liao, de-identified (US)        [Phase 2]
  lab-site/           ← STA production tracking             [Phase 2]
  README.md
```

**Each site is its own folder** so you can edit / redesign one after a feedback session without touching the others. Each `index.html` is self-contained (its own CSS/JS inline).

## Deploy to Netlify

1. Put the **contents of `amd-portal/`** at the root of a GitHub repo (so the landing `index.html` is at the top level).
2. Netlify → Add new site → Import from GitHub → pick the repo.
3. Build command: **empty**. Publish directory: **`.`**
4. Open the URL — the landing page appears; click into any site.
   (Or drag the `amd-portal` folder onto Netlify's manual-deploy drop zone to test instantly.)

The patient app is a PWA: open its URL on a phone → **Add to Home Screen** to install.

## What each mock demonstrates

- **Patient app** — Home task card (STA reminder + daily tasks + goals), journey timeline, before/after comparison, learn, chat, achievements, 中文/EN toggle.
- **Doctor site** — patient dashboard (difficulty color-coded), add-patient flow, patient record with the full **follow-up-record form** (A–J incl. STA gear adjustment, in-clinic questionnaire, hidden internal note), daily-task assignment, **referral creation**, chat, finish/graduate.
- **HQ site** — upload the IP (S+, Schwarz, diagnosis & plan), set case difficulty, **STA dispatch tracking**, and a **KPI analytics** dashboard (clinical / doctor / marketing).
- **MD/PT site** — referred patients only; add follow-up records + chat; **least-access** (full airway history is locked).
- **Felix site** — **de-identified** cases (patient code, age range, masked faces, view-only) for cross-border privacy compliance.
- **Lab site** — STA order queue and production/shipping status that feeds back to HQ + Doctor site.

## Reflects feedback from the 23 Jul 2026 session
Equal task points, gamification is opt-out, questionnaire done in-clinic on iPad, referrals originate on the Doctor side with least-access sharing, de-identification for cross-border, STA photos uploaded by AMD/ATC. See `../Feedback_Actions_2026-07-23.md` for the full list.

## Known simplifications
Sample data only; before/after and imaging are placeholders; no auth or real permissions (the least-access / de-identification is shown in the UI but must be enforced at the API layer in the real build). The patient app still uses its earlier nav (Home/Journey/Progress/Learn/Me) — the feedback nav changes (separate Appointment Records, merged Journey+Progress, gamification settings) are queued as the next patch.
