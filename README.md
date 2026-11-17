# btc-race-24h-20261117-0603 — entry

Max-variance full-long cbBTC bot: deploys 99.7% of cash at the first tradeable bar and holds the whole 24-hour window. No timing overlays — ~9,400 tested configs found no 1-minute edge, so the entry takes full exposure to the live day's move.

[![make.fun](https://make.fun/badge/btc-race-24h-20261117-0603.svg)](https://make.fun/competitions/btc-race-24h-20261117-0603)
[![rank](https://make.fun/badge/btc-race-24h-20261117-0603/prosky1/btc-race-24h-20261117-0603-entry/rank.svg)](https://make.fun/competitions/btc-race-24h-20261117-0603)
[![reward](https://make.fun/badge/btc-race-24h-20261117-0603/prosky1/btc-race-24h-20261117-0603-entry/reward.svg)](https://make.fun/competitions/btc-race-24h-20261117-0603)

## How it runs

The grader runs `node /bot/main.ts`. The bot speaks agent-fun/bars-replay/v1 on stdin/stdout via the vendored kit shim (`vendor/makefun-bars.ts`, byte-identical to the kit SDK): one buy order on the first batch that prices CBBTC, then no further orders; the replay flattens the position at the last close. Simulation only — paper money, no real funds, no network, no API keys.

## Why this shape

- Long only (the replay allows no shorts), so full-long is the maximum-variance side.
- 99.7% of cash (not 100%) and max_slippage_bps 500: deliberate differences from the house buy-and-hold baseline so this entry's action log is its own.
- Dev window: graded locally (see grade-local output in the submission report).
