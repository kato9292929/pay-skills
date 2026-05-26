---
name: onchain-stock-data
title: "Onchain Stock Data"
description: "Tokenized stock data APIs for AI agents covering xStocks registry, Backpack IPOs Onchain calendar, DEX liquidity, holder maps via Helius RPC, curated alpha signals, and a multi-source IC memo Analyst on Base and Solana."
use_case: "Use for tokenized equity analysis: aggregate xStocks data, scan DEX vs official price deviation, identify large holders, and synthesize IC memos across multiple data sources."
category: finance
service_url: https://osd-coral.vercel.app
openapi:
  url: https://osd-coral.vercel.app/.well-known/x402.json
---

Onchain Stock Data is a unified API for AI agents operating on tokenized equity markets. It aggregates xStocks (60+ tokenized stocks issued by Backed Finance on Solana), Backpack IPOs Onchain (Superstate × Solana), DEX liquidity from Jupiter / Raydium / Orca / Meteora, holder maps from Helius RPC, and curated alpha signals. All endpoints accept payment in USDC on Base (eip155:8453) or Solana (solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp).

The Analyst endpoint (POST /api/analyst) aggregates five sub-APIs in parallel and synthesizes an IC memo via Claude. Three depth tiers are available: quick ($0.50), standard ($1.50), and deep ($3.00).

## Spend-aware usage

- Use single-ticker lookups (`/api/stocks/:ticker`) over the full registry (`/api/stocks`) when only one symbol is needed.
- For liquidity arbitrage scanning, use `/api/liquidity?arbitrage=true` to filter pre-arbitrage opportunities (deviation > 1%) instead of paginating full liquidity data.
- The Analyst endpoint includes upstream sub-API costs; calling Analyst at `quick` depth ($0.50) is cheaper than calling all five sub-APIs separately ($0.05 + Claude synthesis cost).
- Holder maps (`/api/holders`) are cached for 60 seconds upstream; repeated calls within that window return identical data, so batch agent queries near the cache boundary.
- IPO calendar (`/api/ipo`) updates daily; agents should not poll faster than once per hour.

## Notes

- Tokenized equities (xStocks) are issued by Backed Finance and have regional usage restrictions (not available to US, UK, Canada, Australia, or EU residents).
- The Analyst endpoint generates investment analysis using AI synthesis of public data. Not financial advice.
- All endpoints use x402 v2 with CAIP-2 network identifiers.
- CDP-hosted facilitator (api.cdp.coinbase.com/platform/v2/x402) with KYT/OFAC checks and Solana feePayer (gasless settlement).
