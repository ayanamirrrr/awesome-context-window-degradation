# Curated References — Context-Window Degradation & Long-Document Research Synthesis

Every paper below was independently checked against a scholarly source (arXiv, ACL Anthology, DOI/Crossref, or the publisher record) **after** the AI-assisted draft paper and citation-integrity audit were completed. Papers 1–9 are the sources originally cited by the AI-generated paper and were verified in [`../citation-audit/`](../citation-audit); papers 10–20 were added afterward through independent literature search to bring the collection to the 20-paper minimum and to broaden coverage of mitigation strategies (efficient architectures, RAG, benchmarks, and position-extension methods).

Legend: ✅ Verified — publication exists and metadata (title/authors/year/venue/identifier) matched an authoritative record.

---

## 1. Foundational Architecture

- **Attention Is All You Need** ✅
  Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, Ł., & Polosukhin, I. (2017). *Advances in Neural Information Processing Systems 30 (NeurIPS)*.
  [arXiv:1706.03762](https://arxiv.org/abs/1706.03762)
  Introduces the Transformer and self-attention — the architectural basis for every long-context LLM discussed in this repository.

- **FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness** ✅
  Dao, T., Fu, D. Y., Ermon, S., Rudra, A., & Ré, C. (2022). *NeurIPS 2022*.
  [arXiv:2205.14135](https://arxiv.org/abs/2205.14135)
  IO-aware exact-attention algorithm that made long-context training/inference computationally practical; foundational infrastructure for later long-context models.

- **Mamba: Linear-Time Sequence Modeling with Selective State Spaces** ✅
  Gu, A., & Dao, T. (2023). *arXiv preprint*.
  [arXiv:2312.00752](https://arxiv.org/abs/2312.00752)
  A non-Transformer, linear-time alternative for long-sequence modeling — relevant as an architectural mitigation to quadratic attention cost.

- **Longformer: The Long-Document Transformer** ✅
  Beltagy, I., Peters, M. E., & Cohan, A. (2020). *arXiv preprint*.
  [arXiv:2004.05150](https://arxiv.org/abs/2004.05150)
  Local + global attention pattern enabling linear-complexity processing of long documents; used for long-document summarization.

- **Efficient Streaming Language Models with Attention Sinks (StreamingLLM)** ✅
  Xiao, G., Tian, Y., Chen, B., Han, S., & Lewis, M. (2023). *ICLR 2024*.
  [arXiv:2309.17453](https://arxiv.org/abs/2309.17453)
  Identifies the "attention sink" phenomenon and enables stable generation over millions of tokens without fine-tuning — directly relevant to context-window scaling limits.

## 2. Positional Bias and Degradation Evidence

- **Lost in the Middle: How Language Models Use Long Contexts** ✅
  Liu, N. F., Lin, K., Hewitt, J., Paranjape, A., Bevilacqua, M., Petroni, F., & Liang, P. (2024). *Transactions of the Association for Computational Linguistics (TACL), 12*, 157–173.
  DOI: [10.1162/tacl_a_00638](https://doi.org/10.1162/tacl_a_00638) · [arXiv:2307.03172](https://arxiv.org/abs/2307.03172)
  The central empirical result motivating this topic: model accuracy drops sharply when relevant evidence sits in the middle of a long context.

- **Context Length Alone Hurts LLM Performance Despite Perfect Retrieval** ✅
  Du, Y., Tian, M., Ronanki, S., Rongali, S., Bodapati, S., Galstyan, A., et al. (2025). *arXiv preprint*.
  [arXiv:2510.05381](https://arxiv.org/abs/2510.05381)
  Shows degradation persists even when the model is forced to attend only to relevant tokens — isolating raw input length as an independent cause of failure.

- **LongICLBench: Long-context LLMs Struggle with Long In-context Learning** ✅
  Li, T., et al. (2024). *arXiv preprint*.
  [arXiv:2404.02060](https://arxiv.org/abs/2404.02060)
  Evaluates 13 long-context LLMs and finds performance degrades — sometimes linearly — as demonstration length in the prompt grows.

## 3. Beyond Needle-in-a-Haystack: Long-Context Benchmarks

- **RULER: What's the Real Context Size of Your Long-Context Language Models?** ✅
  Hsieh, C.-P., Sun, S., Kriman, S., Acharya, S., Rekesh, D., Jia, F., Zhang, Y., & Ginsburg, B. (2024). *arXiv preprint*.
  [arXiv:2404.06654](https://arxiv.org/abs/2404.06654) · [Official code](https://github.com/NVIDIA/RULER)
  Extends needle-in-a-haystack testing to multi-hop tracing and aggregation; shows large accuracy drops as context length grows despite near-perfect simple-retrieval scores.

- **BABILong: Testing the Limits of LLMs with Long Context Reasoning-in-a-Haystack** ✅
  Kuratov, Y., Bulatov, A., Anokhin, P., Rodkin, I., Sorokin, D., Sorokin, A., & Burtsev, M. (2024). *NeurIPS 2024 Datasets and Benchmarks Track*.
  [arXiv:2406.10149](https://arxiv.org/abs/2406.10149)
  Tests reasoning over facts distributed through long natural-text contexts, closer to real research-synthesis demands than synthetic single-needle tests.

- **LongBench: A Bilingual, Multitask Benchmark for Long Context Understanding** ✅
  Bai, Y., Lv, X., Zhang, J., Lyu, H., Tang, J., Huang, Z., Du, Z., Liu, X., Zeng, A., Hou, L., Dong, Y., Tang, J., & Li, J. (2023/2024). *ACL 2024*, 3119–3137.
  DOI: [10.18653/v1/2024.acl-long.172](https://doi.org/10.18653/v1/2024.acl-long.172) · [arXiv:2308.14508](https://arxiv.org/abs/2308.14508)
  Six task categories (single/multi-doc QA, summarization, few-shot learning, synthetic tasks, code) across long-context settings.

- **LongBench v2: Towards Deeper Understanding and Reasoning on Realistic Long-context Multitasks** ✅
  Bai, Y., Tu, S., Zhang, J., Peng, H., Wang, X., Lv, X., Cao, S., Xu, J., Hou, L., Dong, Y., Tang, J., & Li, J. (2025). *ACL 2025*, 3639–3664.
  DOI: [10.18653/v1/2025.acl-long.183](https://doi.org/10.18653/v1/2025.acl-long.183)
  Realistic multi-step reasoning tasks over contexts up to ~2M words; a step toward evaluating faithful evidence integration rather than pure retrieval.

- **SCROLLS: Standardized Comparison Over Long Language Sequences** ✅
  Shaham, U., Segal, E., Ivgi, M., Efrat, A., Yoran, O., Haviv, A., Gupta, A., Xiong, W., Geva, M., Berant, J., et al. (2022). *EMNLP 2022*, 12007–12021.
  [ACL Anthology](https://aclanthology.org/2022.emnlp-main.823/)
  Seven-dataset benchmark (including GovReport, QMSum, NarrativeQA) standardizing long-text summarization and QA evaluation.

- **ZeroSCROLLS: A Zero-Shot Benchmark for Long Text Understanding** ✅
  Shaham, U., Ivgi, M., Efrat, A., Berant, J., & Levy, O. (2023). *Findings of ACL: EMNLP 2023*, 7977–7989.
  [arXiv:2305.14196](https://arxiv.org/abs/2305.14196)
  Extends SCROLLS to a fully zero-shot regime across ten long-document tasks; used here to source the dataset descriptions in `../datasets/`.

## 4. Retrieval-Augmented Generation and Provenance

- **Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks** ✅
  Lewis, P., Perez, E., Piktus, A., Petroni, F., Karpukhin, V., Goyal, N., Küttler, H., Lewis, M., Yih, W.-t., Rocktäschel, T., Riedel, S., & Kiela, D. (2020). *NeurIPS 33*.
  [arXiv:2005.11401](https://arxiv.org/abs/2005.11401)
  The original RAG paper — combines parametric LLM memory with non-parametric retrieval; the basis of the RAG mitigation strategy discussed in the paper.

- **Retrieval-Augmented Generation for Large Language Models: A Survey** ✅
  Gao, Y., Xiong, Y., Gao, X., Jia, K., Pan, J., Bi, Y., Dai, Y., Sun, J., Wang, M., & Wang, H. (2023). *arXiv preprint*.
  [arXiv:2312.10997](https://arxiv.org/abs/2312.10997)
  Comprehensive review of Naive/Advanced/Modular RAG paradigms; useful map of retrieval design choices referenced in the mitigation-strategies section.

## 5. Long-Document Summarization

- **Globalizing BERT-based Transformer Architectures for Long Document Summarization** ✅
  Grail, Q., Perez, J., & Gaussier, E. (2021). *EACL 2021*, 1792–1810.
  DOI: [10.18653/v1/2021.eacl-main.154](https://doi.org/10.18653/v1/2021.eacl-main.154)
  Long-input-specific summarization architecture, cited as evidence that qualifications/nuance require methods designed for long documents rather than short-document summarizers.

- **Efficient Attentions for Long Document Summarization** ✅
  Huang, L., Cao, S., Parulian, N., Ji, H., & Wang, L. (2021). *NAACL 2021*, 1419–1436.
  DOI: [10.18653/v1/2021.naacl-main.112](https://doi.org/10.18653/v1/2021.naacl-main.112)
  Introduces the GovReport summarization dataset (used in `../datasets/datasets.md`) alongside an efficient long-document attention mechanism.

## 6. Context-Window Extension Methods

- **Extending Context Window of Large Language Models via Positional Interpolation** ✅
  Chen, S., Wong, S., Chen, L., & Tian, Y. (2023). *arXiv preprint*.
  [arXiv:2306.15595](https://arxiv.org/abs/2306.15595)
  Linearly rescales RoPE position indices to extend context windows with minimal fine-tuning — a widely adopted practical mitigation, contrasted in the paper with naive extrapolation.

---

### Note on the original paper's 10th reference (R10)
The AI-generated paper's original reference list included a 10th entry ("Zhang, Y., et al. (2021). A Study on Summarizing and Evaluating Long Documents. OpenReview") that the citation-integrity audit (see `../citation-audit/`) classified as **B — Wrong/Incomplete Metadata**: the underlying OpenReview record exists, but author and identifier information could not be fully confirmed. It has been **excluded** from this curated list per the assignment's "no fabricated/unverifiable references" rule and is retained only as an audit artifact in the citation-audit folder.
