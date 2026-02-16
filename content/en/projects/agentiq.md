---
title: "agentiq"
description: "A portable, Rust-native AI agent orchestration framework with OS-level sandboxing and YAML-driven configuration."
weight: 1
---

## What is agentiq?

agentiq is an AI agent orchestration framework written in Rust. It lets you define, configure, and run multi-agent LLM-powered workflows through a declarative YAML configuration system and a command-line interface.

Where most agent frameworks are Python-based and tightly coupled to a specific UI, agentiq is designed to be portable, fast, and embeddable — a single static binary that can run anywhere, with the orchestration engine fully decoupled from any interface.

## The Problem

Running LLM-powered agents that collaborate, use tools, and safely modify a filesystem is complex. Most existing frameworks lack OS-level isolation, are tied to a single LLM provider, or require writing code to define agent behavior.

agentiq addresses this with three design choices: kernel-level sandboxing for safe tool execution, a provider-agnostic LLM interface, and fully declarative agent definitions — no Rust or Python needed to customize the workflow.

{{< spacer >}}

{{< cards count=3 >}}
{{< card >}}
### Multi-Agent Orchestration
Agents dispatch sub-agents with automatic verification chains. A project manager delegates to specialists, a tester validates results, and a verifier ensures quality before closing.
{{< /card >}}
{{< card >}}
### OS-Level Sandboxing
Agents run inside macOS Seatbelt or Linux bubblewrap sandboxes, restricting filesystem access to the project directory. No trust-the-LLM-to-behave-itself approach.
{{< /card >}}
{{< card >}}
### Provider Agnostic
Works with OpenAI, Azure OpenAI, Ollama, vLLM, DeepSeek, LM Studio, or any OpenAI-compatible API through a unified interface. Switch providers by changing one line in config.
{{< /card >}}
{{< /cards >}}

{{< spacer >}}

## Key Features

- **21+ built-in tools** — File operations, shell command execution, web search and scraping, PDF extraction, persistent memory, RAG-based knowledge base, and agent dispatch.
- **Self-correcting loops** — Developer-tester and manager-verifier feedback cycles let agents detect and fix their own mistakes before reporting back.
- **Hierarchical configuration** — Four-tier precedence: environment variables, local project config, global user config, and bundled presets. All values in YAML, nothing hardcoded.
- **Streaming responses** — Real-time streaming with support for reasoning/thinking content from models like DeepSeek.
- **Custom script tools** — Extend the framework with your own shell scripts defined in a tools YAML file.
- **Persistent memory** — Agents store and recall facts across sessions for continuity.

{{< spacer >}}

## The Agent Team

agentiq ships with six bundled agents that form a complete development workflow:

| Agent | Role |
|-------|------|
| **Project Manager** | Analyzes tasks, creates plans, delegates to specialists |
| **Researcher** | Deep codebase analysis, external research, produces structured findings |
| **Developer** | Code implementation with a self-correcting test loop |
| **Tester** | Runs tests, verifies correctness, dispatches developer for fixes |
| **Documenter** | Technical writing — READMEs, API docs, code comments |
| **Verifier** | Post-hook quality gate that validates work against requirements |

All agents are defined in YAML and can be customized or replaced without touching Rust code.

{{< spacer >}}

## Architecture

The project is structured as two Rust crates:

**agentiq-core** — The orchestration library. Handles agent lifecycle, tool execution, LLM provider abstraction, sandboxing, session management, and a callback system for UI-agnostic communication.

**agentiq-cli** — The command-line interface. Interactive chat, config validation, tool and agent inspection, themed terminal output. Built on top of core's callback system.

This separation means the orchestration engine can be embedded in other contexts — IDE plugins, web applications, or CI/CD pipelines — without any changes to the core.

{{< spacer >}}

## Tech Stack

Built with Rust (2024 edition), tokio for async, reqwest for HTTP, clap for CLI, and serde for serialization. Sandboxing uses macOS Seatbelt and Linux bubblewrap at the kernel level.

## Status

agentiq is in early development (v0.1.0) and is dual-licensed under MIT and Apache 2.0. The source code is not yet published.
