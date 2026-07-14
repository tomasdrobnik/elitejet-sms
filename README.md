# Elite Jet SMS Forms — GitHub Pages Deployment

## Files in this folder
```
index.html                    ← Home screen launcher
wb_verification_report.html   ← W&B Verification Report
perf_verification_report.html ← Performance Verification Report
manifest.json                 ← PWA manifest
sw.js                         ← Service Worker (offline cache)
create-icons.html             ← Run once in browser to generate icons
icon-192.png                  ← App icon (generate with create-icons.html)
icon-512.png                  ← App icon (generate with create-icons.html)
```

---

## Step-by-step deployment (one time, ~10 minutes)

### 1 — Create a GitHub account (if you don't have one)
Go to https://github.com and sign up. Free account is sufficient.

### 2 — Create a new repository
- Click **New repository**
- Name it: `elitejet-sms` (or any name)
- Set to **Private** (recommended for internal tools)
- Click **Create repository**

### 3 — Generate the app icons
- Open `create-icons.html` in any desktop browser
- Click the two download links that appear
- Save `icon-192.png` and `icon-512.png` into this folder

### 4 — Upload all files to GitHub
In your new repository, click **Add file → Upload files** and upload:
- `index.html`
- `wb_verification_report.html`
- `perf_verification_report.html`
- `manifest.json`
- `sw.js`
- `icon-192.png`
- `icon-512.png`

Click **Commit changes**.

### 5 — Enable GitHub Pages
- Go to repository **Settings → Pages**
- Under "Source", select **Deploy from a branch**
- Branch: **main**, folder: **/ (root)**
- Click **Save**
- Wait ~60 seconds — GitHub will show your URL:
  `https://YOUR-USERNAME.github.io/elitejet-sms/`

### 6 — First load on iPad (must be online once)
- Open Safari on iPad
- Navigate to `https://YOUR-USERNAME.github.io/elitejet-sms/`
- The service worker downloads and caches everything (~2 MB)

### 7 — Install to iPad Home Screen
- Tap the **Share button** (box with arrow) in Safari
- Tap **Add to Home Screen**
- Name it **ELJ SMS** → tap **Add**
- The app icon appears on your home screen

### 8 — Use offline
- Open from home screen icon (launches in full-screen, no browser chrome)
- Works with **no Wi-Fi or cellular connection**
- Fill in the form, use Print/PDF to save, use Email when back online

---

## Updating the forms
When you update the HTML files:
1. Upload the new version to GitHub (drag and drop over the existing file)
2. GitHub Pages redeploys automatically in ~60 seconds
3. On the iPad, open the app once while online — the service worker fetches the update
4. The next launch uses the updated version

## Forcing a cache refresh on iPad
If an update isn't appearing:
- Open Safari → Settings → Clear History and Website Data
- Or: long-press the home screen icon → Edit → remove and re-add

---

## Security note
GitHub Pages with a private repository still requires authentication to view the source code. However, the **published Pages site is public by default** unless you have GitHub Pro/Teams with private Pages enabled.

**Options for restricted access:**
- GitHub Pro ($4/month) — enables private GitHub Pages
- Cloudflare Pages (free) with Access rules — adds password/email auth
- Self-hosted on company server/NAS — ideal if you have internal infrastructure

For internal airline use with no sensitive passenger data in the forms themselves, public GitHub Pages is generally acceptable — the forms contain no pre-filled personal data.

