# Awesome Context-Window Degradation

A curated, human-verified collection of research papers, datasets, tools, implementations, and learning resources on **context-window degradation and its impact on long-document research synthesis** — built from an AI-assisted research paper and an independent citation-integrity audit.

---

## Contents

- [Overview](#overview)
- [AI-Assisted Research Paper](#ai-assisted-research-paper)
- [Citation Integrity Audit](#citation-integrity-audit)
- [Curated Research Papers](#curated-research-papers)
  - [Foundational Architecture](#1-foundational-architecture)
  - [Positional Bias and Degradation Evidence](#2-positional-bias-and-degradation-evidence)
  - [Long-Context Benchmarks](#3-beyond-needle-in-a-haystack-long-context-benchmarks)
  - [Retrieval-Augmented Generation](#4-retrieval-augmented-generation-and-provenance)
  - [Long-Document Summarization](#5-long-document-summarization)
  - [Context-Window Extension Methods](#6-context-window-extension-methods)
- [Datasets](#datasets)
- [Tools and Libraries](#tools-and-libraries)
- [GitHub Implementations](#github-implementations)
- [Tutorials and Learning Resources](#tutorials-and-learning-resources)
- [License](#license)

---

## Overview

Large language models can now accept context windows spanning hundreds of thousands to millions of tokens, creating the impression that entire literature collections, technical reports, or books can be synthesized simply by placing them inside a single prompt. However, **technical context capacity and reliable context *use* are different properties**. A growing body of empirical work — beginning with Liu et al.'s "Lost in the Middle" (2024) — shows that model accuracy depends heavily on *where* relevant information sits within a long input, and that accuracy can degrade well before a model's nominal token limit is reached.

This matters directly for **research synthesis**: a task that requires identifying relevant evidence across many documents, comparing findings, preserving methodological qualifications, reconciling contradictions, and connecting conclusions back to their sources. Unlike simple question answering, research synthesis cannot tolerate silent evidence omission, because a single missed limitation or contradictory result can invalidate a review's conclusions.

This repository organizes literature and tools around four themes: (1) **why** degradation happens (positional bias, attention allocation, architectural limits), (2) **how it is measured** (needle-in-a-haystack tests and more realistic multi-hop/aggregation benchmarks), (3) **what mitigates it** (retrieval-augmented generation, hierarchical summarization, structured evidence tracking, efficient architectures, and context-extension methods), and (4) **what remains unresolved** (benchmark design, evaluation of faithful evidence integration rather than pure retrieval, and the lack of a single definition of "long-context understanding").

The central, practical lesson threading through this collection: **a model's ability to accept a long document is not the same as its ability to use every part of it correctly** — reliable research workflows require selective retrieval, source-aware compression, structured evidence tracking, and explicit verification rather than "put everything in the prompt."

## AI-Assisted Research Paper

**Context-Window Degradation and Its Impact on Long-Document Research Synthesis**
Author: Ayan Amir · AI tool used: ChatGPT (GPT-5.6 Luna, free tier) · Date: 21 August 2026

The paper reviews the causes of context-window degradation (positional sensitivity, attention allocation, architectural constraints) and its consequences for research synthesis (evidence omission, cross-document reasoning failure, loss of qualifications, citation/provenance risk), then evaluates mitigation strategies: larger context windows, retrieval-augmented generation, hierarchical summarization, structured evidence tracking, and source-grounded verification.

[View the full paper →](paper/AI_Assisted_Research_Paper.pdf)

## Citation Integrity Audit

Before curating this repository, every reference in the AI-generated paper was systematically audited against scholarly sources (arXiv, ACL Anthology, DOI/Crossref, and publisher records) — **not accepted merely because the AI produced it**. This is the core discipline behind every entry below: any AI system can generate a scholarly-looking reference list, but only independent verification confirms it is trustworthy.

**Audit result:** 10 references sampled (all references, since the paper cited ≤10) → **9 fully verified (A)**, **1 with incomplete/incorrect metadata (B)**, 0 fabricated, 0 identifier mismatches. Authenticity Score: **97.5/100**. Prediction accuracy (pre- vs. post-verification belief): **100%**.

[View the full citation-integrity audit →](citation-audit/Citation_Integrity_Audit.pdf)

## Curated Research Papers

At least 20 verified scholarly papers, organized by subtopic. Every reference below was independently checked (title, authors, year, venue, and persistent identifier) against arXiv, ACL Anthology, or a DOI/Crossref record — see [`references/references.md`](references/references.md) for full annotations and one-line relevance notes for each paper, plus the source/verification-source for every entry.

### 1. Foundational Architecture
Transformer self-attention, FlashAttention, Mamba, Longformer, StreamingLLM — the architectural building blocks that make (and constrain) long-context processing possible. → [Full list](references/references.md#1-foundational-architecture)

### 2. Positional Bias and Degradation Evidence
"Lost in the Middle" and follow-up work isolating *where* and *why* long-context accuracy fails. → [Full list](references/references.md#2-positional-bias-and-degradation-evidence)

### 3. Beyond Needle-in-a-Haystack: Long-Context Benchmarks
RULER, BABILong, LongBench/LongBench v2, SCROLLS/ZeroSCROLLS — benchmarks that go beyond single-fact retrieval to multi-hop reasoning and aggregation. → [Full list](references/references.md#3-beyond-needle-in-a-haystack-long-context-benchmarks)

### 4. Retrieval-Augmented Generation and Provenance
RAG and its survey literature — the primary mitigation strategy for evidence-grounding and citation traceability. → [Full list](references/references.md#4-retrieval-augmented-generation-and-provenance)

### 5. Long-Document Summarization
Architectures and datasets purpose-built for long-input summarization (GovReport, EACL/NAACL work). → [Full list](references/references.md#5-long-document-summarization)

### 6. Context-Window Extension Methods
Positional interpolation and related techniques for extending a pretrained model's usable context window. → [Full list](references/references.md#6-context-window-extension-methods)

## Datasets

RULER, BABILong, LongBench/LongBench v2, and SCROLLS/ZeroSCROLLS (GovReport, QMSum, NarrativeQA, Qasper, QuALITY) — see [`datasets/datasets.md`](datasets/datasets.md) for sources, descriptions, and how each applies to research-synthesis evaluation.

## Tools and Libraries

FlashAttention, LangChain, LlamaIndex, Haystack, vLLM, and the Mamba reference implementation — see [`tools/tools.md`](tools/tools.md) for descriptions and links.

## GitHub Implementations

Official repositories for RULER, StreamingLLM, FlashAttention, Mamba, and Hugging Face's Longformer integration, selected for documentation quality, maintenance activity, and direct connection to a cited paper — see [`implementations/github-repositories.md`](implementations/github-repositories.md).

## Tutorials and Learning Resources

Official documentation and guides on long-context prompting, retrieval-augmented generation, and benchmark reproduction — see [`tutorials.md`](tutorials.md).

## License

Original content in this repository (this README, the curated lists, and the organizational structure) is released under the [MIT License](LICENSE). The author's own AI-assisted paper and citation-integrity audit are included with permission per the course instructions. All third-party papers, datasets, and tools are linked, not redistributed, and remain under their original licenses/copyrights.
