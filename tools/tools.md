# Tools and Libraries — Long-Context / RAG / Research-Synthesis Engineering

Software directly relevant to implementing or mitigating the context-window degradation problems discussed in this repository.

---

- **[FlashAttention](https://github.com/Dao-AILab/flash-attention)**
  IO-aware exact-attention CUDA implementation (Dao et al., [arXiv:2205.14135](https://arxiv.org/abs/2205.14135)). The de-facto standard kernel underlying efficient long-context training and inference in most modern LLM stacks.

- **[LangChain](https://github.com/langchain-ai/langchain)**
  Open-source framework for building LLM pipelines, including retrieval-augmented generation, document loaders, and chunking/splitting utilities used to implement the "hierarchical summarization" and "structured evidence tracking" mitigation strategies described in the paper.

- **[LlamaIndex](https://github.com/run-llama/llama_index)**
  Data-framework specializing in connecting LLMs to external document collections through indexing and retrieval — directly supports the retrieval-augmented and source-grounded verification workflow discussed in Section 4 of the paper.

- **[Haystack](https://github.com/deepset-ai/haystack)**
  End-to-end NLP framework for building production search and RAG pipelines (retrievers, rankers, and pipelines for question answering over document collections), useful for implementing claim-source traceability.

- **[vLLM](https://github.com/vllm-project/vllm)**
  High-throughput LLM inference and serving engine with PagedAttention for efficient KV-cache management, relevant to running long-context models (including StreamingLLM-style workloads) at scale.

- **[Mamba (state-spaces/mamba)](https://github.com/state-spaces/mamba)**
  Reference implementation of the Mamba selective state-space architecture ([arXiv:2312.00752](https://arxiv.org/abs/2312.00752)), an alternative to quadratic self-attention for long-sequence modeling.
