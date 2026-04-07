# ArcGate

API gateway built on Arc. Each call costs $0.001 USDC, settled onchain.

## What it does

Developers register APIs. AI agents call them and pay per request — no subscriptions, no API keys, no monthly bills. Payment settles on Arc Testnet in under 1 second using USDC as gas.

## How it works

1. Create a wallet — get an ARC address
2. Fund it at [faucet.circle.com](https://faucet.circle.com) (select Arc Testnet)
3. Call any API in the marketplace with your agent key
4. $0.001 USDC is deducted onchain, you get the data back

## Built-in APIs

| API | Source |
|-----|--------|
| Weather Pro | Open-Meteo |
| FX Rates | ECB via Frankfurter |
| GeoIP Lookup | ipapi.co |
| Country Data | restcountries.com |
| Crypto Prices | CoinGecko |
| Random Joke | official-joke-api |

## Webhook API

Subscribe to any ARC address and receive HTTP POST notifications when USDC moves. Payloads are signed with HMAC-SHA256.

## Stack

- Arc Testnet (Chain ID 5042002, USDC native gas)
- ethers.js for onchain reads and transfers
- Vercel Functions (Node.js)
- Supabase (Postgres)

## Deploy

```bash
# 1. Run schema.sql in Supabase SQL Editor
# 2. Set env vars in Vercel:
#    SUPABASE_URL
#    SUPABASE_ANON_KEY
#    ARC_PRIVATE_KEY
#    PLATFORM_ARC_ADDRESS
#    CRON_SECRET
```

## Environment variables

| Variable | Description |
|----------|-------------|
| `SUPABASE_URL` | Your Supabase project URL |
| `SUPABASE_ANON_KEY` | Supabase anon key |
| `ARC_PRIVATE_KEY` | Platform wallet private key |
| `PLATFORM_ARC_ADDRESS` | Platform wallet ARC address |
| `CRON_SECRET` | Secret for webhook worker cron |

## Network

| | |
|-|-|
| RPC | https://rpc.testnet.arc.network |
| Chain ID | 5042002 |
| USDC | 0x3600000000000000000000000000000000000000 |
| Explorer | https://testnet.arcscan.app |
