---
title: Contributing
parent: Developers
nav_order: 4
description: "Help build GoRunRun Local AI: test it on more Macs, bring it to Windows and Linux, add features, improve the docs."
---

# Contributing
{: .no_toc }

GoRunRun Local AI is open source under the Apache License 2.0, and help is welcome, whether that's an afternoon of testing or a new platform. Read [CONTRIBUTING.md](https://github.com/gorunrunai/local-ai/blob/main/CONTRIBUTING.md) and the [Code of Conduct](https://github.com/gorunrunai/local-ai/blob/main/CODE_OF_CONDUCT.md) first. For anything big, open an issue before you start, so we can agree on the approach.
{: .fs-5 .fw-300 }

1. TOC
{:toc}

## Test it on your Mac

It's built and tested on one Mac: an M5 Max with 64 GB. Every other chip and memory size is untested. [Which Mac?](../macs/#help-us-test) lists them.

- Preview what the installer would do on your Mac, or any other, without installing anything: `install.sh --dry-run`, or add `--machine=M4Max-48GB` to simulate a different one.
- Install it, use it for a day, and file a [test report](https://github.com/gorunrunai/local-ai/issues/new?template=config_test.yml). Reports that everything works are just as useful as problems.
- Timings help most: how quickly replies start, how long a video takes, and whether voice mode keeps up.

## Bring it to Windows and Linux

This is the biggest open project. Today these parts are tied to Apple silicon and macOS:

| Part | On the Mac today | What another platform needs |
|---|---|---|
| Chat models | MLX (`mlx-vlm`) behind `llama-swap` | A backend for NVIDIA, AMD or CPU, such as llama.cpp, with the same model list in `config/models.yaml` |
| Speech and voice | MLX builds of the speech-to-text and text-to-speech models | Versions of the same models that run on CUDA, ROCm or the CPU |
| Video creation | `ltx-2-mlx` and an MLX build of Wan 2.2 | The original PyTorch versions on a GPU with enough video memory |
| Installer | `install.sh` (Homebrew, macOS checks) | A Linux script and a Windows installer, with memory tiers based on GPU video memory as well as system memory |
| Background service | A `launchd` agent | systemd on Linux, a service or scheduled task on Windows |
| Desktop app | A Swift window around the web app | A cross-platform window, or just the browser |

The web app, the orchestrator, the tools and the tests are ordinary Python and TypeScript, so most of the code carries over. A good first step is a Linux build that runs the chat model through llama.cpp on an NVIDIA GPU, with an entry in the memory table for it.

## Add features

Some ideas, if you're looking for one:

- Editing photos with a prompt, alongside animating them.
- More voices and languages for voice mode.
- New built-in tools, or ready-made MCP server setups (see [Extending it](extending)).
- Translating the app's interface.

Check the [open issues](https://github.com/gorunrunai/local-ai/issues) and [feature requests](https://github.com/gorunrunai/local-ai/issues/new?template=feature_request.yml) first.

## Docs and bug reports

Clearer instructions, a missing FAQ answer, or a [bug report](https://github.com/gorunrunai/local-ai/issues/new?template=bug_report.yml) with the last lines of the log (**Help → Show Logs**) all help. Questions: [amit@gorunrun.ai](mailto:amit@gorunrun.ai).

## Before you open a pull request

- Follow [Build from source](build) to set up, then run `make test` (and `make test-e2e` for interface changes).
- Keep each pull request focused, and add or update tests for what you change.
- By contributing, you agree that your contribution is licensed under the Apache License 2.0.
