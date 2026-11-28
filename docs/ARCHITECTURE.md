# How ATLAS works

ATLAS is one HTML file (plus `three.min.js` and two background images). There is no backend. Everything below happens in your browser.

```
 your browser ──▶ Robinhood Chain RPC   (blocks, logs, balances, eth_call, eth_simulateV1)
      │      ──▶ KyberSwap router API   (best route quotes, swap calldata)
      │      ──▶ Sourcify               (verified source and ABI)
      │      ──▶ OpenRouter             (model list; chat only with your own key)
      ▼
 your wallet  ◀── every write: prepared ▶ simulated on mainnet ▶ shown to you ▶ signed by you
```

## Reading

- **Blocks and balances** come from the public RPC. Long log searches are split into windows the RPC accepts (one address and one value per topic for long ranges).
- **Prices** are live route quotes from the KyberSwap router into USDG. Stock Drift compares them with the on-chain oracle.
- **Pools** are found from the Uniswap v4 PoolManager's own `Initialize` events, and each pool's price and liquidity are read with `extsload`.
- **Verified source** comes from Sourcify; Source Check lists every function that can change state.

## Writing

Every action that sends money or writes to the chain follows the same three steps:

1. **Prepare** the exact transaction (target, amount, calldata).
2. **Simulate** it on mainnet with `eth_call` and `eth_estimateGas` (and `eth_simulateV1` for multi-step flows). If it would fail, nothing is sent.
3. **Sign** in your own wallet, which shows you the details first.

Approvals are always for the exact amount. Liquidity uses Permit2 with a one-hour, exact-amount permission for the PositionManager. After each wallet approval, ATLAS reads the allowance back from the chain and stops if your wallet approved less than needed.

## Proofs

- **Seal** stamps a SHA-256 fingerprint made on your device as a 0 ETH transaction from your wallet to itself. Notary turns that into a certificate anyone can re-check.
- **Token Gate** checks a `personal_sign` signature in the browser (secp256k1 recovery) and reads the token balance on chain.

## The board

The squares, the wires and the signals are plain HTML, SVG and CSS. The heartbeat polls `eth_blockNumber` every few seconds and runs a pulse along the wires when the block changes. Animations stop when the tab is hidden and respect reduced-motion settings.
