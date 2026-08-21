# pSTONKS Yield Dashboard

Static PulseChain dashboard for tracking pNVDA, pAAPL and pGOOGL rewards.

## What it does

- Accepts one or many wallet addresses.
- Remembers wallets in the visitor's browser via `localStorage`.
- Reads `pendingYields(wallet, 0)` from each pSTONKS sub-token contract.
- Reads `userYieldsPaid(wallet, payoutToken)` from each pSTONKS sub-token contract.
- Queries payout-token decimals directly from PulseChain.
- Aggregates paid, remaining due, and total earned per token and per wallet.
- Pulls USD market pricing from the most liquid PulseChain DexScreener pair for each payout token.
- Supports manual USD price overrides if a market price is missing or unsuitable.
- Requires no wallet connection and no signature.

## Deploy on Cloudflare Pages

This site has no build step.

1. Put the contents of this folder in a GitHub repository.
2. In Cloudflare, open **Workers & Pages → Create → Pages → Connect to Git**.
3. Select the repository.
4. Framework preset: **None**.
5. Build command: leave blank.
6. Build output directory: `/` (repository root).
7. Deploy.

You can also drag-and-drop the folder using Cloudflare Pages' direct-upload flow.

## Contracts

- pNVDA: `0xb78c098f3ce7d894bc77dd85922af0d439d8e7cb`
  - payout: NVDAon Pulse `0x6e1de1e0bc3ff2fd2072304e977f3193c3eb08af`
- pAAPL: `0xa1c41363ed865e5a0a65735c17157721c54d5a9e`
  - payout: AAPLon Pulse `0x71836318ddd9bd0a301ef36bf0c4e97154767599`
- pGOOGL: `0x208b7c6363e7185a5f0477f5b08433aeeab1803b`
  - payout: GOOGLon Pulse `0xf04286db459d2378586a9dae0f1425c7e46ef181`

## Important note about USD values

The dashboard uses the payout token's live on-chain market price from DexScreener, not the NASDAQ share price. A manual override can be entered in the Price Settings section if you want another valuation method.
