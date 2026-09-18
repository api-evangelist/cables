---
name: Text & NLP analysis
description: Sentiment, toxicity, keyword extraction, embeddings, and extractive QA over text using Cables' TensorFlow.js NLP tools.
api: openapi/cables-openapi.yml
mcp: https://mcp.cables.live/mcp
operations: [analyze-text, detect-sentiment, detect-toxicity, extract-keywords, embed-text, answer-question]
---

# Text & NLP analysis

> **Payment (x402).** Every tool call is metered. Send the request; on an unpaid call the server returns **HTTP 402** with a Base64-encoded x402 `PaymentRequired` object in the `Payment-Required` header. Settle **$0.05 USDC on Solana devnet** (scheme `exact`, fixed `payTo`) and retry. Discovery (`tools/list`, `/openapi.json`, `/health`) is free.\n> **Errors.** `400` = malformed/missing input; `500` = model/inference failure (`{error, code}` envelope).\n> **Transport.** Call as MCP tools at `https://mcp.cables.live/mcp` (initialize → tools/list → tools/call) or POST the matching `POST /tools/{name}` OpenAPI operation.

## Steps
1. **Sentiment** — `detect-sentiment` with `{ "text": "..." }` returns `{ score, sentiment }`.
2. **Toxicity** — `detect-toxicity` with `{ "text": "..." }` flags toxic content.
3. **Keywords** — `extract-keywords` with `{ "text": "..." }`.
4. **Embeddings** — `embed-text` with `{ "text": "..." }` (Universal Sentence Encoder vectors) for clustering/similarity.
5. **Extractive QA** — `answer-question` with `{ "text": "<context>", ... }`.
6. **General** — `analyze-text` for a combined pass.
