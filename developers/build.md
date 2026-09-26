---
title: Build from source
parent: Developers
nav_order: 1
description: Clone, set up, run and test GoRunRun Local AI.
---

# Build from source

**Requirements:** an Apple Silicon Mac with 32 GB+ of memory, macOS 15+ (developed on macOS 26), [Homebrew](https://brew.sh), Xcode command line tools, and about 40 GB of free disk.

```sh
git clone https://github.com/gorunrunai/local-ai.git
cd local-ai
make setup      # Homebrew deps, Python env (uv), llama-swap, models, web search, test fixtures, web app
make backend    # API + web app + models on http://127.0.0.1:8000
```

For frontend work with hot reload, use `make dev` and open http://127.0.0.1:5173.

## Useful targets

| Command | What it does |
|---|---|
| `make desktop-install` | Build the Swift Mac app and install it with its LaunchAgent |
| `make models-video` | Optional video generation engines and weights (~52 GB) |
| `make menubar-install` | Menu-bar helper with global screenshot hotkeys |
| `make remote` / `make remote-off` | Phone access over Tailscale (same as the switch in Settings → Phone access) |
| `make test` | Python and frontend unit tests (no models needed) |
| `make test-integration` | Tests against the real local models |
| `make test-e2e` | Playwright browser tests, including accessibility audits |
| `make bench` / `make bench-voice` | Speed, memory and voice-latency benchmarks |

## Repository layout

```
inference/      model manager, llama-swap config, providers, speech/embedding services, video
media/          file-type detection and processors for images, OCR, audio, video, documents
orchestrator/   FastAPI app: prompt pipeline, agent loop, tools, policy, MCP, RAG, memory, voice
frontend/       React web app, artifact runtime, Capacitor iOS/Android projects, Playwright tests
desktop/        Swift Mac app (WKWebView) that starts and stops the backend
menubar/        Swift menu-bar helper (screenshot hotkeys)
videogen/       separate environment for the video engines (LTX-2.3, Wan 2.2)
config/         models.yaml, tools.yaml, mcp.json, searxng.yml, prompts/, styles/
scripts/        setup, downloads, benchmarks, backend launcher
tests/          unit, integration and fixtures
install.sh      the one-line installer
```
