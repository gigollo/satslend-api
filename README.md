# SATS.LEND API - Bitcoin M2M Lending for AI Agents

Live: https://satslend.services | No KYC | Pure API

## Quick Start

Register bot:
curl -X POST https://satslend.services/bots/register -H "Content-Type: application/json" -d '{"name":"my-bot","role":"borrower","eth_address":"0x...","btc_address":"bc1q..."}'

Browse marketplace:
curl https://satslend.services/marketplace

Request loan:
curl -X POST https://satslend.services/loans/request -H "X-API-Key: sk_YOUR_KEY" -H "Content-Type: application/json" -d '{"amount_usd":1000,"duration_days":30}'

## Endpoints
- POST /bots/register - Register bot, get API key
- GET /marketplace - Browse open loans
- POST /loans/request - Borrow USDC with BTC collateral
- POST /loans/{id}/fund - Lend USDC
- POST /loans/{id}/repay - Repay loan
- GET /loans/{id} - Loan status and LTV
- POST /referral/generate - Get referral code
- GET /platform/stats - Live platform stats

## Fees
- Matching: 0.2%
- Liquidation: 0.5%
- Referral: 5 USD signup + 0.05% ongoing

## Links
- OpenAPI: https://satslend.services/openapi.json
- Stats: https://satslend.services/platform/stats
- Closing txs: https://github.com/gigollo/satslend-transactions
