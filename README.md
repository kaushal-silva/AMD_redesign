# AMD · Patient App (PWA mock — v1 draft)

A mobile-first **Progressive Web App** mock of the AMD patient journey app. Pure static files (HTML/CSS/JS) — no build step, no backend. Designed to be dropped into GitHub and deployed on Netlify in minutes, and installable to a phone home screen.

> This is a **clickable prototype with sample data** to align with Nancy and show a dev partner — not the production app. All data is hard-coded in `index.html`.

## What's included

| File | Purpose |
|------|---------|
| `index.html` | The whole app: 5 tabs (Home, Journey, Progress, Learn, Me) + chat sub-screen |
| `manifest.json` | PWA metadata (name, icons, theme) so it installs like an app |
| `service-worker.js` | Offline caching so it opens without a connection |
| `icons/` | App icons (192 & 512px) |
| `netlify.toml` | Netlify config (static publish + no-cache on SW/manifest) |

## What the mock shows (MVP screens)

- **Home – "Today's card":** three health goals, the **STA turn reminder** (hero, with a done animation), a **daily-task checklist** with XP + streak + progress ring, and a next-visit countdown.
- **Journey:** the treatment **timeline** (Consultation → … → Graduation) with the current stage highlighted, plus the plan summary.
- **Progress:** a **drag-to-compare before/after** slider and a list of images/reports.
- **Learn:** shareable education articles + a shop link-out.
- **Me:** **health achievements**, reward-points progress, chat with the ATC, and a **中文 / English** toggle (tap the language button top-right).

## Deploy to Netlify via GitHub

1. Create a new GitHub repo (e.g. `amd-patient-app`).
2. Upload the **contents of this `patient-app` folder** to the repo root (so `index.html` is at the top level). Either drag-drop in GitHub's web uploader, or:
   ```bash
   git init && git add . && git commit -m "AMD patient app v1"
   git branch -M main
   git remote add origin https://github.com/<you>/amd-patient-app.git
   git push -u origin main
   ```
3. Go to **netlify.com → Add new site → Import an existing project → GitHub** and pick the repo.
4. Leave build command **empty** and publish directory as **`.`** (the `netlify.toml` already sets this). Click **Deploy**.
5. Open the Netlify URL **on your phone** → browser menu → **Add to Home Screen**. It now launches full-screen like a native app.

*(Fastest test without GitHub: drag this folder straight onto the Netlify "deploy manually" drop zone.)*

## Assumptions made (change freely)

- Sample patient **"Wang Xiaoming"**, mid-treatment (stage 6/9), with placeholder photos drawn as SVG silhouettes so no external images are needed.
- Bilingual EN/中文 throughout; English default.
- 5 daily tasks, sample XP/streak/points values.
- Colours: teal/green health palette, AMD "A" icon (placeholder — swap for your real logo in `icons/`).
- No login screen yet (this is the in-app experience). Auth comes with the real backend.

## What this mock deliberately does NOT do

No real data, login, notifications, payments, or connection to the Doctor/HQ sites. Those need the shared backend from the platform plan. This is the front-end feel only — enough to react to, refine, and hand to a developer.

## Easy next tweaks

- Replace `icons/icon-*.png` with your real logo.
- Edit sample content in the `TASKS`, `STEPS`, and `I18N` blocks near the bottom of `index.html`.
- Add real before/after images by dropping files in and pointing the `.ph` backgrounds at them.
