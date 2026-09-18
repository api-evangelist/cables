---
name: Social-media analytics
description: Per-platform engagement forecasting, comment sentiment, trend detection, thumbnail analysis and topic clustering across YouTube, Instagram, TikTok, Twitter/X, Facebook, Discord, Twitch, Reddit, LinkedIn, Threads, Bluesky, Mastodon, GitHub, Spotify and Pinterest.
api: openapi/cables-openapi.yml
mcp: https://mcp.cables.live/mcp
operations: [youtube-comment-sentiment, predict-youtube-views, youtube-trend-detection, youtube-forecast, classify-youtube-content, analyze-youtube-thumbnails]
---

# Social-media analytics

Each of 15 platforms exposes the same ~10-tool pattern (`<platform>-` prefix). YouTube shown as the template.

> **Payment (x402).** Every tool call is metered. Send the request; on an unpaid call the server returns **HTTP 402** with a Base64-encoded x402 `PaymentRequired` object in the `Payment-Required` header. Settle **$0.05 USDC on Solana devnet** (scheme `exact`, fixed `payTo`) and retry. Discovery (`tools/list`, `/openapi.json`, `/health`) is free.\n> **Errors.** `400` = malformed/missing input; `500` = model/inference failure (`{error, code}` envelope).\n> **Transport.** Call as MCP tools at `https://mcp.cables.live/mcp` (initialize → tools/list → tools/call) or POST the matching `POST /tools/{name}` OpenAPI operation.

## Steps (YouTube template — swap the prefix for other platforms)
1. **Comment sentiment** — `youtube-comment-sentiment` with `{ "texts": [ ... ] }`.
2. **Predict views** — `predict-youtube-views` with `{ titleLen, descLen, hasNumbers, hasEmoji, wordCount, likes, comments }`.
3. **Trend / forecast** — `youtube-trend-detection` and `youtube-forecast` over `{ "dataPoints": [ ... ] }`.
4. **Thumbnails** — `analyze-youtube-thumbnails` (`{ imageUrls }`) and `youtube-thumbnail-comparison` (`{ imageUrl1, imageUrl2 }`).
5. **Topics** — `youtube-topic-clustering` and `classify-youtube-content` over `{ "texts": [ ... ] }`.

Available prefixes: youtube, instagram, tiktok, twitter, facebook, discord, twitch, reddit, linkedin, threads, bluesky, mastodon, github, spotify, pinterest.
