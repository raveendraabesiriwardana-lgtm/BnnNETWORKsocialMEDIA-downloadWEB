# Bee Downloader

A static, single-page video/audio downloader UI (YouTube, TikTok, Facebook, Instagram, X, Reddit, SoundCloud, and more), styled dark with a red/blue gradient. Built to be hosted for free on GitHub Pages.

## ⚠️ Important — read this first

GitHub Pages only serves static files (HTML/CSS/JS). It **cannot run a server**, so it cannot itself extract video links from YouTube/TikTok/etc.

This site works by:
1. Fetching a **live list** of community-run [cobalt](https://github.com/imputnet/cobalt) instances from `cobalt.directory`, filtered to whichever ones currently report working support for the platform you pasted a link from.
2. Trying each candidate instance in turn (POST request) until one returns a working download link.

Note: `api.cobalt.tools` (the *official* public instance) deliberately blocks requests from other websites as bot protection, so this site can't use it directly — that's why it goes through the community instance directory instead.

**Realistic expectations:**
- This is the most reliable *free, no-backend* setup available, but it is still **not guaranteed to work 100% of the time**. Community instances are run by volunteers and can go offline, get rate-limited, or lose YouTube access when platforms tighten anti-scraping measures — this happens periodically to the whole cobalt ecosystem, not just this site.
- **"25+ platforms"** reflects what's realistically supported — YouTube, TikTok, Instagram, Facebook, X/Twitter, Reddit, SoundCloud, Twitch clips, Vimeo, Pinterest, Tumblr, VK, Bilibili, and others. No free option genuinely covers "100+" sites reliably.
- For **guaranteed uptime**, self-host your own cobalt instance (free, open-source, deployable on Render/Fly.io/Railway/a VPS) and set it as the first candidate the app tries. Instructions: https://github.com/imputnet/cobalt/blob/main/docs/run-an-instance.md

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
