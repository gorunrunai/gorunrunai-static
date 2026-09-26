---
title: Extending it
parent: Developers
nav_order: 3
description: Add models, tools, MCP servers, prompts and styles.
---

# Extending GoRunRun Local AI
{: .no_toc }

1. TOC
{:toc}

## Connect an MCP server (no code)

Any [Model Context Protocol](https://modelcontextprotocol.io) server can give the assistant new tools. Add it in **Settings → Tools & MCP**, or in `config/mcp.json`:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/Users/YOU/Documents"],
      "policy": "confirm"
    }
  }
}
```

`policy` can be `allow`, `confirm` (ask the user each time) or `deny`. Tools that change things default to `confirm`.

## Add a built-in tool

A tool is one Python class. Create `orchestrator/tools/weather.py`:

```python
from orchestrator.tools.base import Tool, ToolContext, ToolResult


class Weather(Tool):
    name = "weather"
    description = "Current weather for a city."
    parameters = {"type": "object", "properties": {"city": {"type": "string"}}, "required": ["city"]}
    network = True          # uses the internet: labelled "internet" in Settings → Tools

    async def run(self, args: dict, ctx: ToolContext) -> ToolResult:
        report = await fetch_weather(args["city"])   # your code
        return ToolResult(f"{args['city']}: {report}", data={"city": args["city"]})
```

Register it in `ToolRegistry` (`orchestrator/policy.py`) and give it a default policy in `config/tools.yaml`. The model sees the name, description and JSON schema. Arguments are validated before `run`, and whatever `run` returns is shown to the model as untrusted data. `ctx.emit` can stream progress to the UI; `generate_video` does this.

## Add or swap a model

Models are listed in `config/models.yaml`. To try another MLX chat model:

```yaml
llms:
  my-model:
    display_name: My Model 8B
    backend: mlx-vlm
    repo: mlx-community/My-Model-8B-4bit
    est_memory_gb: 6
    capabilities: { image: true, tools: true }
```

Then run `uv run python scripts/download_models.py --only my-model` and pick it in the model menu, or make it the default under `defaults.llm`. GGUF models can run through llama.cpp with `backend: llama-server`. Speech, embedding, reranker and video models are configured in the same file.

## Change behavior with prompts and styles

- `config/prompts/system.md` is the base system prompt.
- `config/styles/*.md` are the writing styles (add a file to add a style).
- `config/tools.yaml` sets which tools are on and their default policies.

## Build on the API

The web app uses a plain HTTP API on `http://127.0.0.1:8000/api`. Replies stream as Server-Sent Events. For example:

```sh
make chat MSG="Summarize the plot of Hamlet in two sentences"
```

See `scripts/chat_cli.py` for a minimal client, and `orchestrator/api.py` for every endpoint.
