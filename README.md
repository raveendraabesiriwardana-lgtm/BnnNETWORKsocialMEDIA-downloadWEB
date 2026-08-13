# Bee Downloader

A static, single-page video/audio downloader UI (YouTube, TikTok, Facebook, Instagram, X, Reddit, SoundCloud, and more), styled dark with a red/blue gradient. Built to be hosted for free on GitHub Pages.

## ⚠️ Important — read this first

GitHub Pages only serves static files (HTML/CSS/JS). It **cannot run a server**, so it cannot itself extract video links from YouTube/TikTok/etc. The page in this repo calls a **public third-party extraction API** (`api.cobalt.tools`, an open-source project) to do that work.

This means:
- **It will only work as long as that public API is up and allows requests from your domain.** Public instances often rate-limit or block browser (CORS) requests from random sites — if that happens, downloads will fail with an error message on the page (this is handled gracefully, not a crash).
- **"25+ platforms"** reflects what a cobalt-style API realistically supports today — YouTube, TikTok, Instagram, Facebook, X/Twitter, Reddit, SoundCloud, Twitch clips, Vimeo, Pinterest, Tumblr, VK, Bilibili, and others. No free API genuinely covers "100+" sites reliably.
- For a **reliable** version, self-host your own cobalt API instance (it's free, open-source, deploy on Render/Fly.io/a VPS) and point `API_BASE` in `index.html` at your own URL. Instructions: https://github.com/imputnet/cobalt

## Deploy to GitHub Pages (free)

1. Create a new GitHub repository (e.g. `bee-downloader`).
2. Upload `index.html` (and this `README.md`) to the repo — either drag-and-drop in the GitHub web UI, or:
   ```bash
   git init
   git add index.html README.md
   git commit -m "Bee Downloader"
   git branch -M main
   git remote add origin https://github.com/<your-username>/bee-downloader.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source: Deploy from a branch**, branch: `main`, folder: `/ (root)`.
5. Save. Your site will be live in a minute or two at:
   `https://<your-username>.github.io/bee-downloader/`

## Customizing

- Colors/fonts: edit the `:root` variables and font links at the top of `index.html`.
- Platform list: edit the `PLATFORMS` array in the `<script>` section.
- API endpoint: edit `API_BASE` in the `<script>` section.
- Footer credit is already set to "Created by bee".

## Legal note

Only use this to download content you own or have permission to download, and follow each platform's terms of service. This tool is for personal use.
