# Lido Public

Public hosted solo Bitcoin mining pool for people who do not run a home Umbrel/node.

| Site | Role |
| --- | --- |
| **https://lido.wtf** | Live pool (this repo) |
| **https://try.lido.wtf** | Live Umbrel demo / mock (not this stack) |

## vs Umbrel Lido

| | Umbrel (`lido-app`) | Public (`lido-public`) |
| --- | --- | --- |
| Who runs Bitcoin | Your Umbrel | Our server |
| Images | `ghcr.io/kevinguest/lido` + `lido-ui` | `ghcr.io/kevinguest/lido-public` + `lido-public-ui` |
| Versions | Umbrel track (`0.1.x` app store) | Independent (starts at `0.1.0`) |
| Miners table | Per-worker rows | Device groups → workers → detail |
| Charts | Total / weekly / per-miner | Total + weekly only |
| Settings | Full | Removed |
| Login | n/a | Bitcoin address → personal workers |

**Do not** point this compose at the Umbrel GHCR packages. Shared tags would couple releases and risk breaking home installs.

## Quick start

```bash
cp .env.example .env
# Set BITCOIN_RPC_* to a fully synced Bitcoin Core
mkdir -p data/database
docker compose pull
docker compose up -d
```

Miners: see [docs/connect.md](docs/connect.md).

Put TLS in front of port 80 (Cloudflare, Caddy, etc.) for production HTTPS on `lido.wtf`.

## Images

- Pool: `ghcr.io/kevinguest/lido-public`
- UI: `ghcr.io/kevinguest/lido-public-ui`

Published by [`.github/workflows/publish.yml`](.github/workflows/publish.yml) from this repo (builds sibling `lido` / `lido-ui` sources, tags as public packages only).

Bump [`VERSION`](VERSION), push to `main`, or run **Publish to GHCR** via workflow_dispatch.

## Local build without GHCR

From this directory (sibling checkouts of `lido` and `lido-ui` required):

```bash
docker build -t ghcr.io/kevinguest/lido-public:dev ../lido
docker build -t ghcr.io/kevinguest/lido-public-ui:dev ../lido-ui
LIDO_PUBLIC_TAG=dev LIDO_PUBLIC_UI_TAG=dev docker compose up -d
```
