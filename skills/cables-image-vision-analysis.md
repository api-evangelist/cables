---
name: Image & vision analysis
description: Classify images, detect objects and faces, and run custom-label image classification using Cables' TensorFlow.js (MobileNet / COCO-SSD) vision tools.
api: openapi/cables-openapi.yml
mcp: https://mcp.cables.live/mcp
operations: [analyze-image, detect-objects, detect-faces, classify-image]
---

# Image & vision analysis

Run visual ML over an image URL.

> **Payment (x402).** Every tool call is metered. Send the request; on an unpaid call the server returns **HTTP 402** with a Base64-encoded x402 `PaymentRequired` object in the `Payment-Required` header. Settle **$0.05 USDC on Solana devnet** (scheme `exact`, fixed `payTo`) and retry. Discovery (`tools/list`, `/openapi.json`, `/health`) is free.\n> **Errors.** `400` = malformed/missing input; `500` = model/inference failure (`{error, code}` envelope).\n> **Transport.** Call as MCP tools at `https://mcp.cables.live/mcp` (initialize → tools/list → tools/call) or POST the matching `POST /tools/{name}` OpenAPI operation.

## Steps
1. **Classify content** — call `analyze-image` with `{ "imageUrl": "<https url>" }` (MobileNet high-level concepts).
2. **Detect objects** — call `detect-objects` with `{ "imageUrl": ... }` (COCO-SSD localized objects).
3. **Detect faces** — call `detect-faces` with `{ "imageUrl": ... }` for facial-feature/demographic signals.
4. **Custom labels** — call `classify-image` with `{ "imageUrl": ..., "labels": ["a","b"] }` to score against your own label set.

All inputs require a publicly reachable `imageUrl`. No credential is needed to call — only the x402 payment.
