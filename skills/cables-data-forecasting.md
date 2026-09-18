---
name: Data forecasting & anomaly detection
description: Trend prediction, time-series forecasting, anomaly detection, clustering, regression and A/B analysis over numeric data points using Cables' TensorFlow.js data tools.
api: openapi/cables-openapi.yml
mcp: https://mcp.cables.live/mcp
operations: [predict-trend, forecast-data, detect-anomalies, cluster-data, regression, reduce-dimensions, ab-test]
---

# Data forecasting & anomaly detection

> **Payment (x402).** Every tool call is metered. Send the request; on an unpaid call the server returns **HTTP 402** with a Base64-encoded x402 `PaymentRequired` object in the `Payment-Required` header. Settle **$0.05 USDC on Solana devnet** (scheme `exact`, fixed `payTo`) and retry. Discovery (`tools/list`, `/openapi.json`, `/health`) is free.\n> **Errors.** `400` = malformed/missing input; `500` = model/inference failure (`{error, code}` envelope).\n> **Transport.** Call as MCP tools at `https://mcp.cables.live/mcp` (initialize → tools/list → tools/call) or POST the matching `POST /tools/{name}` OpenAPI operation.

## Steps
1. **Forecast** — `forecast-data` with `{ "dataPoints": [ ... ] }` for time-series projection.
2. **Trend** — `predict-trend` over the same `dataPoints`.
3. **Anomalies** — `detect-anomalies` to flag outliers.
4. **Cluster / reduce** — `cluster-data` and `reduce-dimensions` for structure.
5. **Regression / A-B** — `regression` and `ab-test` for relationships and experiment analysis.
