# Deploying Idea Log to GitHub Pages

You have two options. **Option A** (recommended) adds it as a page inside your existing `science-vocab` site. **Option B** gives it a completely separate URL and repo. Both use the same files.

## Files in this package

- `idea-log.html` — the app itself
- `favicon.ico`, `icon-16.png`, `icon-32.png`, `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` — the icon set
- `site.webmanifest` — tells phones how to treat it as an "app" when saved to the home screen

All six icon/manifest files must sit in the **same folder** as `idea-log.html` — the HTML already links to them by relative filename (`favicon.ico`, `icon-192.png`, etc.), so don't rename them or nest them in a subfolder unless you also update those links.

---

## Option A: Add it inside science-vocab (recommended)

This publishes it at:
`https://jbrand454-crypto.github.io/science-vocab/idea-log/`

### Using the GitHub website (no git required)

1. Go to your repo: `https://github.com/jbrand454-crypto/science-vocab`
2. Click **Add file → Create new file**
3. In the filename box, type `idea-log/idea-log.html` — typing the `/` automatically creates the `idea-log` folder
4. Paste the full contents of `idea-log.html` into the editor
5. Click **Commit changes**
6. Repeat steps 2–5 for each of the 7 remaining files, each time typing the filename as `idea-log/favicon.ico`, `idea-log/icon-16.png`, etc.
   - **Note:** GitHub's web editor only accepts text paste for text files. For the `.ico` and `.png` files (binary), instead use **Add file → Upload files**, drag all 6 image/manifest files in at once, and make sure you're inside the `idea-log` folder first (open the folder, then click Upload files) — or upload them to the repo root and then move them into `idea-log/` afterward using the file browser's rename/move option.
7. Wait 1–2 minutes for GitHub Pages to rebuild, then visit the URL above.

### Using git on your computer

```bash
cd science-vocab
mkdir idea-log
# copy all 8 files from this package into the new idea-log folder
cp ~/Downloads/idea-log.html ~/Downloads/favicon.ico ~/Downloads/icon-16.png \
   ~/Downloads/icon-32.png ~/Downloads/icon-192.png ~/Downloads/icon-512.png \
   ~/Downloads/apple-touch-icon.png ~/Downloads/site.webmanifest idea-log/

git add idea-log
git commit -m "Add Idea Log app"
git push
```

Then visit `https://jbrand454-crypto.github.io/science-vocab/idea-log/` after a minute or two.

---

## Option B: Give it its own repo and landing page

This publishes it at its own address, e.g.:
`https://jbrand454-crypto.github.io/idea-log/`

### Using the GitHub website

1. Go to [github.com/new](https://github.com/new)
2. Repository name: `idea-log`
3. Set it to **Public** (required for free GitHub Pages), check **Add a README file**, then **Create repository**
4. In the new repo, click **Add file → Upload files**
5. Drag in all 8 files from this package (`idea-log.html` and the 7 icon/manifest files)
6. Commit
7. **Rename `idea-log.html` to `index.html`** so it loads automatically at the root URL — click into the file, click the pencil (edit) icon, then use the filename field at the top to rename it, and commit
8. Go to the repo's **Settings → Pages**
9. Under **Source**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then **Save**
10. Wait 1–2 minutes, then visit `https://jbrand454-crypto.github.io/idea-log/`

### Using git on your computer

```bash
mkdir idea-log && cd idea-log
git init
cp ~/Downloads/idea-log.html index.html
cp ~/Downloads/favicon.ico ~/Downloads/icon-16.png ~/Downloads/icon-32.png \
   ~/Downloads/icon-192.png ~/Downloads/icon-512.png ~/Downloads/apple-touch-icon.png \
   ~/Downloads/site.webmanifest .

git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/jbrand454-crypto/idea-log.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Source: Deploy from a branch → main → / (root) → Save**.

---

## Adding it to your phone's home screen

Once the page is live at whichever URL you chose:

**iPhone (Safari):** Open the link → tap the **Share** icon → **Add to Home Screen**. You'll see the kraft-brown star icon and the name "Idea Log."

**Android (Chrome):** Open the link → tap the **⋮** menu → **Add to Home screen** (or **Install app** if it appears).

It'll open full-screen without browser chrome, like a real app.

---

## One thing to know about the AI features

**Generate Prompt** and **Generate Summary** call Claude directly. Inside a Claude conversation, that's handled automatically. Once this is hosted standalone on GitHub Pages, there's no backend to hold an API key securely, so the app will ask you (via a small 🔑 button that appears next to Generate Prompt) to paste in your own Anthropic API key the first time you use either feature. That key is stored only in your phone/browser's local storage — it's never sent anywhere except directly to Anthropic when you generate something. You can get a key at [console.anthropic.com](https://console.anthropic.com).

Everything else — capturing, folders, tags, platforms, drag-to-reorder, Working On It / Up Next / In The Hole, search, trash, summaries you've already generated — works fully offline-first, no key needed, since your data saves to the browser's local storage on that device.

**Heads up:** local storage is per-browser, per-device. If you use this on your phone and your laptop, they'll each have their own separate set of ideas — there's no syncing between devices in this standalone version.
