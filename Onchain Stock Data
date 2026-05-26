# Onchain Stock Data

Tokenized stock data APIs for AI agents via x402 protocol.

## What's included

- 7 endpoints covering xStocks (60+ tokenized stocks on Solana),
  Backpack IPOs Onchain calendar, DEX liquidity tracking,
  holder maps via Helius RPC, curated alpha signals,
  and a multi-source IC memo Analyst.
- Data sources: Backed Finance (xStocks), Superstate × Solana
  (Backpack IPOs Onchain), Jupiter / Raydium / Orca / Meteora
  (DEX liquidity), Helius RPC (holders), curated X posts.
- Supports x402 v2 on Base (eip155:8453) and Solana
  (solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp).
- Multi-network payment options in every accept leg.
- CDP-hosted facilitator (api.cdp.coinbase.com/platform/v2/x402)
  with KYT/OFAC checks and Solana feePayer (gasless settlement).

## Endpoints

| Endpoint | Description | Price (USDC) |
|---|---|---|
| GET /api/stocks | xStocks registry + listed stock fundamentals | $0.01 |
| GET /api/stocks/:ticker | Single ticker detail | $0.01 |
| GET /api/ipo | Backpack IPOs Onchain calendar | $0.01 |
| GET /api/liquidity | Tokenized stock DEX liquidity + price deviation | $0.01 |
| GET /api/holders | Tokenized stock holders map + concentration | $0.01 |
| GET /api/alpha-posts | Curated alpha signals feed | $0.01 |
| POST /api/analyst (quick) | IC memo (5 sub-APIs aggregated + Claude synthesis) | $0.50 |
| POST /api/analyst (standard) | + SEC EDGAR filings | $1.50 |
| POST /api/analyst (deep) | + earnings call transcripts + comparables | $3.00 |

## Discovery

- App URL: https://osd-coral.vercel.app/
- Discovery: https://osd-coral.vercel.app/.well-known/x402.json
- GitHub: https://github.com/kato9292929/onchain-stock-data
- Operator: x402 Inc.
- Region: APAC (multi-language: English, 日本語)

## Notes

- Tokenized equities (xStocks) are issued by Backed Finance and
  have regional usage restrictions (not available to US, UK,
  Canada, Australia, or EU residents).
- The Analyst endpoint generates investment analysis using AI
  synthesis of public data. Not financial advice.
- All endpoints use x402 v2 with CAIP-2 network identifiers
  ("eip155:8453" and "solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp").
- Internal authentication via X-Internal-Key header bypasses
  payment for x402 Inc.'s own Autonomous Agent (AA Daily Brief).
