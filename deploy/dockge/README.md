# Deploying flowerboi.se on the NAS

1. In dockge, create a stack named `flowerboi-web` and paste `compose.yml` from this folder. Deploy it.
   The page is then served on host port **18085**.
2. In Nginx Proxy Manager, add a proxy host:
   - Domain names: `flowerboi.se`, `www.flowerboi.se`
   - Forward to `http://<NAS IP>:18085`
   - SSL: request a certificate for both names (or use your existing setup for the apex), force SSL.
3. Watchtower (label-gated, already running) pulls `ghcr.io/toribash67/flowerboi-web:latest`
   after each push to `main`, so updates go live within a minute or two.

Health check: `curl http://<NAS IP>:18085/healthz` returns `ok`.
