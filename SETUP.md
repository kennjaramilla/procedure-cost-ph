# Setup & Deploy — Gastimate

Everything to take this live. ~10 minutes total.

## 1. Deploy to Vercel (free) → `gastimate.vercel.app`
1. **vercel.com → Add New → Project → Import** → pick `kennjaramilla/procedure-cost-ph`
   (the repo name can stay; the URL comes from the project name below).
2. **Set the Project Name to `gastimate`** → URL becomes `gastimate.vercel.app`.
   (If taken: `gastimate-ph`, `gogastimate`, `gastimateph`.)
3. Framework Preset: **Other**. No build command. Output dir: default (root).
4. **Deploy.** After this, every push to `main` auto-redeploys.

## 2. Connect the "Share a price" form (Formspree, free)
The crowdsource form is built; it just needs somewhere to send submissions.
1. Sign up at **formspree.io** (free = 50 submissions/month).
2. Create a form → copy its endpoint, e.g. `https://formspree.io/f/abcdwxyz`.
3. In `index.html`, set the constant near the top of the `<script>`:
   ```js
   const CROWDSOURCE_ENDPOINT = "https://formspree.io/f/abcdwxyz";
   ```
4. Commit & push → submissions land in your Formspree inbox.
   (Until set, the form shows a friendly "not connected yet" message.)

## 3. (Optional) Real one-word domain → `gastimate.ph`
1. Buy `gastimate.ph` at **dot.ph** (~₱2,500–3,000/yr). `gastimate.com` (~$12/yr) also works.
2. Vercel project → **Settings → Domains → Add** `gastimate.ph`.
3. At the registrar, set the DNS Vercel shows (root → A `76.76.21.21`; `www` → CNAME
   `cname.vercel-dns.com`), or switch nameservers to Vercel's.
4. Wait a few minutes; Vercel auto-issues HTTPS.

## 4. Keeping data fresh (manual — there is no API)
All figures live in `index.html`:
- `PROCEDURES` — cost ranges + PhilHealth case rates (update when a new PhilHealth
  circular is issued, ~a few times/year; bump `REVIEWED`).
- `AID` — financial-assistance programs.
- `HOSPITALS` — directory (names + phones only).
- ₱↔€ rate auto-updates from `open.er-api.com` on load.

## Notes
- No personal data is collected/stored (besides what users type into the Formspree form).
- `vercel.json` sets `Cache-Control: no-store` so updates always show immediately.
