# GitHub Implementations

Existing high-quality repositories directly tied to the papers and benchmarks in [`../references/references.md`](../references/references.md). Each was selected for documentation quality, maintenance activity, and direct connection to a cited paper — not merely star count.

---

- **[NVIDIA/RULER](https://github.com/NVIDIA/RULER)**
  Official implementation of the RULER benchmark ([arXiv:2404.06654](https://arxiv.org/abs/2404.06654)). Includes synthetic task generators for multi-needle retrieval, multi-hop tracing, and aggregation across configurable context lengths. Actively maintained by NVIDIA; includes a public leaderboard.

- **[mit-han-lab/streaming-llm](https://github.com/mit-han-lab/streaming-llm)**
  Official code for StreamingLLM / attention-sinks ([arXiv:2309.17453](https://arxiv.org/abs/2309.17453), ICLR 2024). Demonstrates stable generation over millions of tokens without fine-tuning; clear reproducibility instructions and pretrained-model support (Llama-2, MPT, Falcon, Pythia).

- **[Dao-AILab/flash-attention](https://github.com/Dao-AILab/flash-attention)**
  Official FlashAttention / FlashAttention-2/3 implementation ([arXiv:2205.14135](https://arxiv.org/abs/2205.14135)). Core infrastructure dependency for nearly every efficient long-context model referenced in this repository.

- **[state-spaces/mamba](https://github.com/state-spaces/mamba)**
  Official Mamba selective-state-space implementation ([arXiv:2312.00752](https://arxiv.org/abs/2312.00752)). Linear-time alternative to attention for long-sequence modeling, with training and inference code.

- **[huggingface/transformers — Longformer integration](https://github.com/huggingface/transformers)**
  Hugging Face's maintained implementation of Longformer ([arXiv:2004.05150](https://arxiv.org/abs/2004.05150)) and other long-context architectures, with extensive documentation, examples, and community support — used here as the reference implementation for the local+global attention pattern discussed in Section 2.1 of the paper.
