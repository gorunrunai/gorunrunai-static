---
title: Developers
nav_order: 7
has_children: true
permalink: /developers/
description: GoRunRun Local AI is open source. Build it, understand it, extend it.
---

# For developers

GoRunRun Local AI is open source under the [Apache License 2.0](https://github.com/gorunrunai/local-ai/blob/main/LICENSE). The code lives at **[github.com/gorunrunai/local-ai](https://github.com/gorunrunai/local-ai)**.

It's a small, readable codebase:
- **Python** (FastAPI) for the backend, orchestration and media handling
- **MLX** for running models on Apple silicon
- **React** for the web app
- **Swift** for the Mac app

Most extensions need only a configuration change or a single file.

- [Build from source](build): clone, set up, run and test.
- [Architecture](architecture): how a message travels from the box to the answer.
- [Extending it](extending): add models, tools, MCP servers, prompts and styles.
- [Contributing](contributing): test on more Macs, bring it to Windows and Linux, add features.

## Principles

- **Local first.** No telemetry and no hosted AI APIs. The network is used only to download models and by tools the user turns on.
- **Loopback by default.** Servers listen on `127.0.0.1`. Remote access is opt-in and token-protected.
- **Untrusted data stays data.** File contents, web pages and tool output are clearly marked as data, never followed as instructions. Risky tools ask first.
- **Measured.** Latency and memory claims come from benchmarks in the repo (`make bench`, `make bench-voice`).

Contributions are welcome: see [Contributing](contributing), and read [CONTRIBUTING.md](https://github.com/gorunrunai/local-ai/blob/main/CONTRIBUTING.md) and the [Code of Conduct](https://github.com/gorunrunai/local-ai/blob/main/CODE_OF_CONDUCT.md), and report security issues privately as described in [SECURITY.md](https://github.com/gorunrunai/local-ai/blob/main/SECURITY.md).
