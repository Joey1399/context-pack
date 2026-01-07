# context-pack

context-pack builds a budgeted context bundle for a user prompt: retrieve only the most relevant snippets, rerank, dedupe, and pack them into a fixed token budget with citations. It also places the most important constraints/evidence at the beginning/end to reduce “lost in the middle” failures in long contexts. Outputs a clean “context pack” you can paste into any LLM chat or API call.

## Big context windows still feel unusable (effective context length / “lost in the middle”)

**Goal:** don’t “stuff context”; *stage it*.

- **Retrieval-first:** store docs and fetch only the top snippets for the current question (hybrid search + reranking). This avoids burying the “needle” mid-context. ([arXiv][2])
- **Put “what matters” at the edges:** the lost-in-the-middle effect is real—models often do best when key info is at the beginning or end. ([arXiv][2])
- **Pack a “context bundle” with a fixed budget:** e.g., 2–6 snippets + a 10-line “state” + citations. Your product can auto-build this every time.
- **Reprompting / in-context retrieval:** for long documents, repeat the *instruction and key constraints* periodically or reinsert retrieved evidence near where it’s used (there’s published work showing this can help mitigate lost-in-the-middle behavior). ([ACL Anthology][3])

COMING SOON
