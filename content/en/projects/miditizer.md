---
title: "Miditizer"
description: "Piano transcription model on Hugging Face — turns raw audio into MIDI notes."
weight: 2
---

## Miditizer

A piano transcription model published on [Hugging Face](https://huggingface.co/citan/miditizer). It takes raw audio and produces the notes that were played — a fully automatic music transcription pipeline for piano recordings.

{{< spacer >}}

## What it does

Given an audio recording, the model outputs the notes the pianist played, each with pitch, timing, and a loudness estimate, written to MIDI. The published pipeline is set up as an `audio-classification` task, with weights shipped as a PyTorch model.

{{< spacer >}}

## Where to find it

- [Miditizer on Hugging Face](https://huggingface.co/citan/miditizer) — the model card and weights (gated on HF; account and terms acceptance required)
- [citan's Hugging Face profile](https://huggingface.co/citan) — hub page that links both models

{{< spacer >}}

## Technical Details

- **Task:** audio-classification (piano transcription)
- **Framework:** PyTorch
- **License:** CC-BY-NC-SA-4.0
- **Reference:** arXiv:2404.09466 (third-party comparison system, linked from the model card)
