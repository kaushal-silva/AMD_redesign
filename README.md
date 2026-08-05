# AMD Platform — Prototype Portal (v2)

A single deployable folder: a **landing page** plus **seven role-specific site mocks**. Deploy the whole `amd-portal` folder to Netlify; the landing page (`index.html`) links to each site.

> All sites are **clickable front-end mocks with sample data** — no login, no backend, no real records. They exist to run feedback sessions and brief the dev partner. One shared patient record will sit behind all surfaces in the real build.

## Structure

```
amd-portal/
  index.html          ← landing page (links to all sites)
  netlify.toml        ← deploy config (static, no build)
  patient-app/        ← Patient PWA (mobile, installable)      [MVP]
  doctor-site/        ← AMD + ATC clinical tool                [MVP]
  hq-site/            ← AMD Taiwan HQ: IP upload, STA, KPIs     [MVP core]
  md-pt-site/         ← Referred specialists (least-access)    [Phase 2]
  felix-site/         ← Dr. Liao: authors diagnosis/plan/STA   [Phase 2]
  fmd-site/           ← Functional Medicine (Premium add-on)   [Premium]
  lab-site/           ← STA + retainer production, QC gate     [Phase 2]
  README.md
```

Each site is its own folder (self-contained HTML/CSS/JS) so you can edit one after feedback without touching the others.

## What's new in v2 (from the 31 Jul / 2 Aug updates)
- **Whole-person / Premium tier** across the patient app — "a healthy body helps your STA work" framing, a **Health Score** (Premium, 0–100 composite vs baseline), a 6-month report entry, and a **Retainer** journey stage.
- **FMD site** (new) — Premium add-on, own site: reviews blood/sleep, uploads diet & supplement suggestions, takes referrals; least-access data view.
- **Lab** — separate **Retainer orders** section + a **fit-check / payment-hold gate** (don't pay the lab until the AMD/ATC confirms the STA fits; return/redo if not).
- **HQ** — **AI-assisted formal report** draft (from Felix's plan + first-visit data + FMD suggestion).
- **Doctor site** — satisfaction scores on the patient card; AI voice-dictate affordance on the follow-up record.

## Deploy to Netlify (drop-in)
1. Put the **contents of `amd-portal/`** at the root of a GitHub repo (so this `index.html` is at the top level).
   ```bash
   git init && git add . && git commit -m "AMD platform portal v2"
   git branch -M main
   git remote add origin https://github.com/<you>/amd-portal.git
   git push -u origin main
   ```
2. Netlify → Add new site → Import from GitHub → pick the repo.
3. Build command **empty**, publish directory **`.`** (the `netlify.toml` already sets this). Deploy.
4. The landing page loads first; click into any site. Open the patient app on a phone → **Add to Home Screen** to install (it's a PWA).

*(Fastest test without GitHub: drag the `amd-portal` folder onto Netlify's manual-deploy drop zone.)*

## Known simplifications
Sample data only; images are stylised placeholders; permissions (least-access, de-identification) are shown in the UI but must be enforced at the API layer in the real build. The patient app no longer registers a service worker (removed to avoid stale-cache issues during prototyping; re-add a versioned one for production offline + push).
