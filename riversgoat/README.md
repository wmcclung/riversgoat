# riversgoat.com

When someone dares vote Brady on [tb12notgoat.com](https://tb12notgoat.com), they're teleported here. Full-screen Phillip Rivers, procedural canvas lightning, Thor-god typography, and a quiet "Vote Again" escape hatch back to the main site.

## What's in here

- `index.html` — the whole page (HTML + CSS + JS, no dependencies)
- `Assets/phillip-rivers.svg` — the hero image
- `Dockerfile` — nginx:alpine container for Railway deploy

That's it. No build step, no framework, no package manager.

## Deploy to Railway

1. Create a new GitHub repo and push this folder to it (`riversgoat/` contents at repo root, not in a subfolder)
2. In Railway: **New Project → Deploy from GitHub repo → pick this repo**
3. Railway detects the Dockerfile, builds, and deploys automatically (~30s)
4. In the service **Settings → Networking → Custom Domain**, add `riversgoat.com`
5. Railway shows you a CNAME target — add it at your registrar's DNS panel
6. Wait 5–30 min for DNS propagation and TLS provisioning
7. Done — riversgoat.com is live

## Deploy to Vercel / Netlify / Cloudflare Pages (alternative)

Skip the Dockerfile entirely. All three host static HTML for free with zero config — just drag-drop the folder or connect the GitHub repo.

## Local preview

```sh
# Any static server — e.g.
python3 -m http.server 8000
# then open http://localhost:8000
```

## Syncing with tb12notgoat.com

The "Vote Again" link hard-codes `https://tb12notgoat.com#vote-section`. If the main site's domain changes, update that line in `index.html`.

The page also accepts a `?from=<host>` query param to dynamically override the return link — useful if you deploy this HTML to multiple destinations from one codebase.
