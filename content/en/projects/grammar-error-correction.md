---
title: "Grammar Error Correction"
description: "Polish grammar error correction model on Hugging Face — corrects grammar token by token, exported in ONNX and safetensors formats."
weight: 1
---

## Grammar Error Correction

A grammar error correction model for Polish, published on [Hugging Face](https://huggingface.co/citan/plgec-herbert-large-v2). It finds and fixes grammatical errors in Polish text — built as a token-classification pipeline in the GECToR style, on top of a HerBERT base model (allegro/herbert-large-cased).

{{< spacer >}}

## What it does

Given a Polish sentence, the model tags the tokens that need correcting and produces the corrected forms. The pipeline follows the GECToR pattern — grammar error correction treated as a sequence-tagging task — and the weights are exported in both ONNX and safetensors formats.

{{< spacer >}}

## Where to find it

- [Grammar error correction model on Hugging Face](https://huggingface.co/citan/plgec-herbert-large-v2) — the model card and weights
- [citan's Hugging Face profile](https://huggingface.co/citan) — hub page that links both models

{{< spacer >}}

## Technical Details

- **Task:** token-classification (GECToR-style grammar error correction)
- **Base model:** HerBERT (allegro/herbert-large-cased)
- **Exports:** ONNX and safetensors
- **License:** CC-BY-NC-4.0
