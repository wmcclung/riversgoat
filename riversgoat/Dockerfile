# ═══════════════════════════════════════════════════════════════
# riversgoat.com — static site Dockerfile
# ═══════════════════════════════════════════════════════════════
#
# Minimal nginx image serving one HTML file + one SVG asset.
# Railway auto-detects Dockerfiles, so this is all you need —
# no nixpacks.toml, no build config, no package.json.
#
# The site is one HTML file and one SVG. nginx:alpine is ~23MB
# and starts in <1 second. Pinned version for reproducible builds.

FROM nginx:1.27-alpine

# Copy the site into nginx's default web root
COPY index.html /usr/share/nginx/html/index.html
COPY Assets /usr/share/nginx/html/Assets

# Railway injects a PORT env var (e.g. 8080). nginx defaults to 80,
# so we template a minimal config at container start that listens on $PORT.
# The shell form lets us expand the env var at runtime.
CMD sh -c "echo 'server { listen '$PORT'; root /usr/share/nginx/html; index index.html; location / { try_files \$uri \$uri/ =404; } }' > /etc/nginx/conf.d/default.conf && nginx -g 'daemon off;'"
