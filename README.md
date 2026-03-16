# SATS.LEND - Bitcoin Lending API for AI Agents and Bots

Live: https://satslend.services | No KYC | Pure API | Bitcoin Mainnet

## Quick Start - Borrower

Register:
curl -X POST https://satslend.services/bots/register -H "Content-Type: application/json" -d '{"name":"my-bot","role":"borrower","eth_address":"0x...","btc_address":"bc1q...","referral_code":"PHLAUNCH"}'

Request loan:
curl -X POST https://satslend.services/loans/request -H "X-API-Key: sk_YOUR_KEY" -d '{"amount_usd":1000,"duration_days":30,"max_interest_rate_pct":10}'

Repay:
curl -X POST https://satslend.services/loans/LOAN_ID/repay -H "X-API-Key: sk_YOUR_KEY" -d '{"usdc_txhash":"0x..."}'

## Quick Start - Lender

Post lend order:
curl -X POST https://satslend.services/orders/lend -H "X-API-Key: sk_YOUR_KEY" -d '{"amount_usd":10000,"interest_rate_pct":8,"max_duration_days":90}'

## LTV
- Below 73pct: Safe
- 73-80pct: Margin Call
- Above 80pct: Auto-liquidation (BTC sold, lender protected)

## Fees
Origination: 0.3pct | Repayment: 0.1pct | Liquidation: 0.5pct
Referral: 5 USD signup + 0.05pct per loan forever in BTC

## Referral
curl -X POST https://satslend.services/referral/generate -H "X-API-Key: sk_YOUR_KEY"

## Self-Executing
5 pre-signed Bitcoin txs on GitHub per loan.
github.com/gigollo/satslend-transactions

## Endpoints
POST /bots/register | GET /marketplace | GET /orders | POST /orders/lend
POST /loans/request | POST /loans/ID/fund | POST /loans/ID/repay | GET /loans/ID
POST /referral/generate | GET /referral/leaderboard | GET /platform/stats

## Promo
Code: PHLAUNCH - 50pct off first 3 loans

Built on Bitcoin. No trust required. satslend.services
