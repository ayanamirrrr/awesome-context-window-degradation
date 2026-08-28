# Datasets — Long-Context / Research-Synthesis Evaluation

Datasets used to measure context-window degradation, positional bias, and long-document reasoning. Each entry includes source, description, and how it applies to this topic.

---

- **RULER**
  Source: [github.com/NVIDIA/RULER](https://github.com/NVIDIA/RULER) · Paper: [arXiv:2404.06654](https://arxiv.org/abs/2404.06654)
  Synthetic benchmark generator covering multi-needle retrieval, multi-hop tracing, aggregation, and variable-length QA/summarization tasks. Used to test whether a model's *effective* context length matches its *advertised* context length.

- **BABILong**
  Source: [github.com/booydar/babilong](https://github.com/booydar/babilong) · Paper: [arXiv:2406.10149](https://arxiv.org/abs/2406.10149)
  Embeds bAbI reasoning tasks inside long natural-text "haystacks" of arbitrary length (tested up to 10M+ tokens). Used to evaluate distributed multi-fact reasoning rather than single-fact retrieval — directly relevant to cross-document research synthesis.

- **LongBench / LongBench v2**
  Source: [huggingface.co/datasets/zai-org/LongBench](https://huggingface.co/datasets/zai-org/LongBench) · Papers: [arXiv:2308.14508](https://arxiv.org/abs/2308.14508), ACL 2025 (LongBench v2, DOI [10.18653/v1/2025.acl-long.183](https://doi.org/10.18653/v1/2025.acl-long.183))
  Bilingual (English/Chinese) benchmark spanning single/multi-document QA, summarization, few-shot learning, synthetic tasks, and code completion; v2 adds realistic multi-step reasoning over contexts up to ~2M words.

- **SCROLLS / ZeroSCROLLS** (bundles GovReport, QMSum, NarrativeQA, Qasper, QuALITY, SummScreenFD, MuSiQue)
  Source: [ZeroSCROLLS leaderboard](https://www.zero.scrolls-benchmark.com/) · Papers: SCROLLS (EMNLP 2022, [ACL Anthology](https://aclanthology.org/2022.emnlp-main.823/)), ZeroSCROLLS ([arXiv:2305.14196](https://arxiv.org/abs/2305.14196))
  A family of real long-document tasks: government-report summarization (GovReport), query-based meeting summarization (QMSum), book/movie-script comprehension (NarrativeQA), and scientific-paper QA (Qasper). Used here as realistic (non-synthetic) stand-ins for research-synthesis-style long-document tasks, since they involve genuine qualifications, contradictions, and long narrative structure rather than inserted "needles."

> Datasets are directly applicable to this topic (long-context degradation in research synthesis) because each stresses a different failure mode discussed in the paper: RULER and BABILong isolate positional/multi-hop retrieval failure in synthetic settings, while LongBench and SCROLLS/ZeroSCROLLS test the same failure modes on realistic documents closer to actual literature-review material.
