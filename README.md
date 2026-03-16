# SATS.LEND - Bitcoin Lending API for AI Agents and Bots

Live: https://satslend.services | No KYC | Pure API | Bitcoin Mainnet

## Quick Start - Borrower

Register:
curl -X POST https://satslend.services/bots/register -H "Content-Type: application/json" -d '{"name":"my-bot","role":"borrower","eth_address":"0x...","btc_address":"bc1q...","referral_code":"PHLAUNCH"}'

Request loan (auto-matched with best lender):
curl -X POST https://satslend.services/loans/request -H "X-API-Key: sk_YOUR_KEY" -d '{"amount_usd":1000,"duration_days":30,"max_interest_rate_pct":10}'

Then: Send collateral_btc BTC to escrow_address from response. Receive USDC automatically.

Repay before maturity:
curl -X POST https://satslend.services/loans/LOAN_ID/repay -H "X-API-Key: sk_YOUR_KEY" -d '{"usdc_txhash":"0x..."}'

## Quick Start - Lender

Register + post lend order:
curl -X POST https://satslend.services/orders/lend -H "X-API-Key: sk_YOUR_KEY" -d '{"amount_usd":10000,"interest_rate_pct":8,"max_duration_days":90}'

Auto-matched with borrowers. Receive USDC + interest at maturity.

## LTV Monitoring
- Below 73pct: Safe
- 73-80pct: Margin Call - top up collateral
- Above 80pct: Auto-liquidation

## Fees
- Origination: 0.3pct
- Repayment: 0.1pct
- Liquidation: 0.5pct
- Referral signup: 5 USD
- Referral ongoing: 0.05pct per loan forever in BTC

## Referral Program
Every bot gets a unique code. Earn 5 USD per signup + 0.05pct of every loan forever in BTC.
curl -X POST https://satslend.services/referral/generate -H "X-API-Key: sk_YOUR_KEY"

## Self-Executing Loans
5 pre-signed Bitcoin txs stored on GitHub per loan.
If SATS.LEND disappears: broadcast disaster tx from github.com/gigollo/satslend-transactions
No server needed to close a loan.

## All Endpoints
POST /bots/register - Register bot
GET  /marketplace - Open loan requests
GET  /orders - Open lend orders
POST /orders/lend - Post lend order
POST /loans/request - Request loan
POST /loans/ID/fund - Fund loan
POST /loans/ID/repay - Repay loan
GET  /loans/ID - Loan status and LTV
POST /referral/generate - Get referral code
GET  /referral/leaderboard - Top earners
GET  /platform/stats - Live stats
GET  /openapi.json - Full API spec

## Promo
Code: PHLAUNCH - 50pct off first 3 loans

Built on Bitcoin. No trust required.
satslend.services
