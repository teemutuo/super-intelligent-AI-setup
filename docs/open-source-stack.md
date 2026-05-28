# The open-source stack I run alongside

This repo is not the whole setup. It is the part I wrote. The rest is open-source software that other people maintain, that I use every day, and that makes the skills in this repo actually sing.

## Memory layer

Every skill assumes Claude remembers what it learned about you. Without persistent memory across sessions your bootstrap reloads as an attachment every conversation. Pick one.

- **Mempalace** · file-based, self-hosted, fast. The one I run.
- **Mem0** · hosted long-term memory layer with an API. Lower friction than Mempalace, your memory lives on someone else's server.
- **Letta** · memory-aware agent framework. More architecturally complete, more dev-heavy.

Pick one. Do not run three.

## Prompt patterns library

When you build a new skill from scratch, start by checking if someone has already written something adjacent.

- **fabric**, by Daniel Miessler. The best curated library of patterns on the internet. Use as inspiration when building a new SKILL.md. Strip down, rewrite in your voice using your memory bootstrap.

## Multi-model routing

Once you have three or more LLMs you want to switch between (Claude, GPT, Gemini, Mistral, local models):

- **LiteLLM** · one API, every major model. Useful for A/B testing the same skill across providers. Open source.

## Self-hosted chat UI

If your company forbids external LLM use but lets you run inference internally:

- **Open WebUI** · the cleanest self-hosted frontend on top of a private model. Open source.

## Scheduler for agents

Native options first:

- **Claude Cowork scheduled tasks** · built in. Use this if you are on Cowork.
- **ChatGPT Tasks** · built in. Use this if you are on ChatGPT.
- **Microsoft Power Automate** · built in for Copilot for Microsoft 365.

External options if you need them:

- **n8n** · self-hosted workflow automation. Open source.
- **Make** or **Zapier** · hosted alternatives. Not open source. Fine for personal use, less great in regulated environments.

## My personal stack as of May 2026

| Layer | What I use | Why |
|-------|------------|-----|
| LLM | Claude (Max tier) | Long context, signed enterprise DPA, the Skills format I depend on. |
| Environment | Claude Cowork | Native scheduled tasks, native plugin install, MCP servers. |
| Memory | Mempalace | File-based, private, fast. |
| Skill library | This repo plus fabric for cold-start | This repo for my voice, fabric for inspiration when building new skills. |
| Connectors | Microsoft 365 plus Slack via Claude OAuth | Five-minute setup, scope read-only. |
| Agents | Claude Cowork native scheduler | No glue infrastructure. |
| Coding (rare) | Claude Code | For the moments a skill needs actual code, not prompt. |

## What you do not need

A vector database. A custom RAG pipeline. An "AI agent platform" that wraps an LLM with a marketing layer and a 2,000 euro per month invoice. If a vendor is pitching you those for a personal setup, they are solving a problem you do not have.

## How I picked these

I picked open-source because the value is in the architecture, not the prompts. The prompts you can rewrite in your voice in an afternoon. The architecture, once you trust it, is what makes the whole thing compound.

If you find a memory tool or a prompt library that is sharper than what I run, open a PR. The repo gets sharper from real use.
