# Edge Kuri — Chitti Draw

Gamified monthly Kuri (chitti) draw for Edge Trading Academy.

- Login gate (username + password)
- Spinning wheel with tick sounds, 3-2-1 suspense countdown, confetti and winner card
- Winners leave the wheel automatically; one winner per round until everyone has received the Kuri
- Winners history with date/time (GST), Undo, Copy results, New cycle
- Member photos on the wheel, chips, history and the winner card (`assets/photos/<name>.jpg`, lowercase)
- Festival winner moment: crown, light garland, fireworks, confetti and a random song (no repeats until all have played) from `assets/music/`
- Funny Manglish suspense lines while spinning, plus a fun line and an inspiration quote for every winner
- Edit members from the **Members** button
- Fair draw: uses `crypto.getRandomValues` (unbiased)
- Results are saved in the browser on the device used for the draw

## Publish on GitHub Pages

1. Create a new repository on github.com (e.g. `edge-kuri`). Private repos need a paid plan for Pages; public works on free.
2. **Add file → Upload files**, drag in `index.html`, `README.md` and the `assets` folder, then **Commit**.
3. **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*, Branch = `main`, folder `/ (root)` → **Save**.
4. After ~1 minute the site is live at `https://<your-username>.github.io/edge-kuri/`.

## Changing the login

The page stores only a SHA-256 hash of `username:password`. To change it, run in any browser console:

```js
crypto.subtle.digest("SHA-256", new TextEncoder().encode("NewUser:NewPass"))
  .then(b => console.log([...new Uint8Array(b)].map(x => x.toString(16).padStart(2, "0")).join("")))
```

and replace the `HASH` value near the top of the `<script>` in `index.html`.

> Note: GitHub Pages is static hosting, so this login is a privacy gate that keeps casual visitors out — not bank-grade security. Don't put sensitive data on the page.
