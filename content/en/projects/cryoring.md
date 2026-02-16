---
title: "CryoRing"
description: "Distributed LLM inference across your home lab — zero-config discovery, pipeline parallelism, and an OpenAI-compatible API."
weight: 2
---

## What is CryoRing?

CryoRing is a distributed inference server that lets you run large language models across multiple machines. It splits a model's layers into a pipeline, spreads them across your devices, and exposes a standard OpenAI-compatible API — so any client that talks to OpenAI can talk to your cluster instead.

The project is built for the era of massive Mixture-of-Experts models like Kimi-K2 (640GB) and DeepSeek-V3 — models that are too large for any single machine but run comfortably when spread across a small cluster of commodity hardware.

## The Problem

Running frontier-class LLMs locally typically requires a single machine with enormous amounts of memory. Most people don't have that. But many have a few machines sitting around — a Mac Studio here, a Mac Mini there, maybe a Linux box with an NVIDIA GPU. CryoRing pools those machines together and makes them work as one.

## How It Works

Start the coordinator on one machine. Start workers on the others. They find each other automatically via mDNS — no IP addresses to configure, no config files to write. The coordinator distributes model layers based on each worker's available memory, and inference requests flow through the pipeline transparently.

{{< spacer >}}

{{< cards count=3 >}}
{{< card >}}
### Zero-Config Discovery
Workers find the coordinator automatically via mDNS/Bonjour on the local network. Just run `cryoring serve` and `cryoring worker` — they handle the rest.
{{< /card >}}
{{< card >}}
### Pipeline Parallelism
Model layers are distributed across devices. Hidden states flow from worker to worker over a custom binary wire protocol built on ZeroMQ.
{{< /card >}}
{{< card >}}
### OpenAI-Compatible API
Drop-in replacement for OpenAI endpoints. Streaming and non-streaming. Any client that works with OpenAI works with CryoRing.
{{< /card >}}
{{< /cards >}}

{{< spacer >}}

## Key Features

- **Heterogeneous hardware** — Mix Apple Silicon (MLX) and NVIDIA (CUDA) workers in the same cluster. Cross-backend tensor conversion is handled transparently.
- **Massive model support** — Run 640GB+ Mixture-of-Experts models across a home lab. Includes expert routing, load balancing, and efficient scoring.
- **FP8 quantization** — Efficient inference with FP8 block-wise quantized weights, plus MLX affine quantization support.
- **131K context window** — YARN rope scaling for large context windows.
- **Automatic layer distribution** — The scheduler distributes layers proportionally based on available memory with built-in OOM prevention.
- **Web dashboard** — Real-time cluster monitoring with live WebSocket updates.
- **Testbench mode** — Spin up a full local cluster with a single command for development and testing.

{{< spacer >}}

## Architecture

The system consists of three components:

**Coordinator** — The brain. Runs the HTTP API, manages worker registration, tracks models, schedules layer distribution, and advertises itself via mDNS.

**Workers** — Execute model layer inference. Each worker registers with the coordinator, loads its assigned layers, and passes hidden states to the next worker in the pipeline.

**Data Plane** — A custom binary protocol over ZeroMQ for high-throughput tensor transfer between pipeline stages with minimal serialization overhead.

{{< spacer >}}

## Tech Stack

Built with Python, FastAPI, ZeroMQ, and Zeroconf. Inference backends are MLX for Apple Silicon and PyTorch for NVIDIA GPUs. Model weights are loaded from HuggingFace Hub.

## Status

CryoRing is in active development (alpha) and is licensed under MIT. The source code is not yet published.
