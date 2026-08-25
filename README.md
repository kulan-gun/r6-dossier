# r6-dossier

Single-page repository. Intended to host an unlisted GitHub Pages page at an unguessable path.

Planned public page (replace with your full HTML file):
- /s/f9a3b7c2d6e4f1a0b3c7d9e2/index.html
- After enabling Pages: https://kulan-gun.github.io/r6-dossier/s/f9a3b7c2d6e4f1a0b3c7d9e2/

Privacy notes:
- This repo is public so Pages can be published for free.
- The page includes a `<meta name="robots" content="noindex, nofollow">` to request search engines not to index it.
- Do NOT block the path in robots.txt — crawlers need to be able to fetch the page to see the meta noindex tag.
- Do not link the published URL publicly; anyone with the URL can access the page.

How to replace the placeholder with your full index.html (via git):
1. Clone the repo:
   git clone git@github.com:kulan-gun/r6-dossier.git
   cd r6-dossier

2. Create the folder and copy your file:
   mkdir -p s/f9a3b7c2d6e4f1a0b3c7d9e2
   cp /path/to/your/full-index.html s/f9a3b7c2d6e4f1a0b3c7d9e2/index.html

3. Commit & push:
   git add s/f9a3b7c2d6e4f1a0b3c7d9e2/index.html
   git commit -m "Add full R6 dossier page"
   git push origin main

Or via the GitHub web UI:
- Upload your file into the folder path: s/f9a3b7c2d6e4f1a0b3c7d9e2/index.html

Enable GitHub Pages
1. On GitHub go to: Settings → Pages (or Settings → Code and automation → Pages)
2. Source: Branch: main, Folder: / (root). Save.
3. Wait ~1 minute and visit the published URL: https://kulan-gun.github.io/r6-dossier/s/f9a3b7c2d6e4f1a0b3c7d9e2/

If your page was already indexed and you want it removed
- Use Google Search Console (URL Removal) and Bing Webmaster Tools to request removal; after adding meta noindex, request re-crawl.

If you want me to add these placeholder files and enable Pages now
- Reply: “Please add files and enable Pages” — I will push the placeholder files and enable Pages for you.
