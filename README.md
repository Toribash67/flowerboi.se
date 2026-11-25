# flowerboi.se

The landing page for [flowerboi.se](https://flowerboi.se): one static `index.html`, served by nginx in a container on the NAS (see `deploy/dockge/README.md`).

- **Sites** are plain `<li class="row">` entries in `index.html`. Each row's `data-host` is its subdomain, `data-repo` (optional) a public repo under Toribash67, and `data-private` marks a tailnet-only host. Each row gets one flower in the meadow.
- **Status** is checked from the visitor's browser on load (a `no-cors` request to each host). Private (tailnet) hosts are only checked in browsers that opened `flowerboi.se/#tailnet` once, because browsers ask before a site contacts a 100.x address.
- **Repo details** come from the GitHub API, one request, cached for an hour in the browser.
- **Themes** are the `THEMES` table in the `<head>` script.

Every push to `main` publishes `ghcr.io/toribash67/flowerboi-web` and watchtower picks it up.

Preview locally with `python3 -m http.server` and open http://localhost:8000.
