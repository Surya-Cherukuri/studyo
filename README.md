# Studyo website

The public Studyo landing page: free one-minute lessons that play in the page, how they're made, and the engine waitlist.
Plain HTML, no build step. Every lesson plays from YouTube by its video id (the `yt:` values in `LESSONS` and the `id:` values in `LONG` inside `index.html`),
so thumbnail and video changes made on YouTube show up here by themselves; the titles on the page are written in `index.html`.
`videos/` and `posters/` hold local copies: the hero plays `videos/cs-5-bfs.mp4`, and a lesson without a YouTube id plays its local file.

## Kept up to date by itself

`videos.js` holds the YouTube id of each lesson on the page. Your Mac rewrites it from the Studio's uploader records (tools/site_sync.py, run every minute by
fetch_reports.sh) whenever a lesson's video is replaced or goes private, then commits and pushes this repo. Only the lessons already on the page are
kept in sync (the list is tools/site/lessons.json in physics-videos); new YouTube uploads are not added by themselves. Don't edit videos.js by hand.

## Put it online (GitHub Pages, free)

1. On github.com, create a new **public** repository named `studyo` (no README, no licence).
2. In Terminal:

   ```
   cd ~/.n8n-files/physics-videos/"Claude outputs"/studyo-site
   git init -b main
   git add .
   git commit -m "Studyo website"
   git remote add origin https://github.com/Surya-Cherukuri/studyo.git
   git push -u origin main
   ```

3. In the repository: Settings, Pages, Source "Deploy from a branch", branch `main`, folder `/ (root)`, Save.
   A minute later the site is at https://surya-cherukuri.github.io/studyo/

## Waitlist

The button opens the Google Form https://forms.gle/WhERdtvAMhBDuGf37 (the `WAITLIST_URL` line in `index.html`). Sign-ups land in the form's responses sheet.

## Add a new video

Add a line to `LESSONS` (a short) or `LONG` (a longer video) in `index.html` with its YouTube id, commit and push.

## Later

A custom domain goes in Settings, Pages, Custom domain.
