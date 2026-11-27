# ATLAS

**16 tools for AI agents, payments and privacy on Robinhood Chain. All of them work.**

[atlasboard.dev](https://atlasboard.dev) is a map of tools for Robinhood Chain mainnet, grouped as Agent, Payment, Data and Tools. Every tool has its own page, and the site has Trust, Status, Developers, Roadmap and Changelog pages with what it is in plain words, an example, who it is for, how it works and how to build a first version. Every tool works right on its page, on mainnet.

## All 16 tools are live

| Tool | What it does |
| --- | --- |
| [Protocol](https://atlasboard.dev/#/swap) | Four tabs: **Swap** any token at the best route; **Pools**, every Uniswap v4 pool for a token; **Create Pool**, start a pool or add full-range liquidity via the PositionManager and Permit2; **Positions**, what your liquidity holds, fees to collect, collect or remove. Exact amounts, simulated first, signed in your own wallet. |
| [MCP](https://atlasboard.dev/#/mcp) | Six read-only chain tools for Claude, Cursor and any MCP client: `npx -y github:atlasboard/atlas-mcp` |
| [AI Model](https://atlasboard.dev/#/ai-model) | Pick any of 400+ models; it answers from live chain data using ATLAS tools. Your own OpenRouter key, kept in the tab. |
| [Console](https://atlasboard.dev/#/console) | A command line for the chain: block, gas, balance, token, price, tx, verify, hash. |
| [Memory](https://atlasboard.dev/#/memory) | An encrypted memory vault on your device: folders, ChatGPT/Claude import, an approval inbox, per-folder sharing, read log. |
| [Night Shift](https://atlasboard.dev/#/night-shift) | A free GitHub Action in your own repo that writes a chain report on schedule. |
| [x402](https://atlasboard.dev/#/x402) | Open any x402 endpoint, read its price, pay in USDG by signing an EIP-3009 authorization in your wallet. |
| [Seal](https://atlasboard.dev/#/seal) | Hash a file on your device and stamp the fingerprint on chain from your own wallet. |
| [Privacy](https://atlasboard.dev/#/privacy) | What strangers can read about a wallet: counterparties, active hours, open approvals. |
| [Checkout Button](https://atlasboard.dev/#/checkout-button) | A USDG pay button for any website. |
| [Smart Invoice](https://atlasboard.dev/#/smart-invoice) | An invoice in a link that marks itself PAID when the USDG arrives. |
| [Liquidity Depth](https://atlasboard.dev/#/liquidity-depth) | Live router quotes from 100 to 50,000 USDG and the price impact of each. |
| [Stock Drift](https://atlasboard.dev/#/stock-drift) | Stock tokens on chain next to their oracle prices. |
| [Notary](https://atlasboard.dev/#/notary) | A certificate that a text or file was stamped at a given block. |
| [Source Check](https://atlasboard.dev/#/source-check) | Sourcify verification and every function that can change state. |
| [Token Gate](https://atlasboard.dev/#/token-gate) | Holders prove they hold a token with a free wallet signature; anyone can check the proof. |

## Trust

What ATLAS can and cannot see, the threat model and live health: [atlasboard.dev/#/trust](https://atlasboard.dev/#/trust) and [#/status](https://atlasboard.dev/#/status).

## How it works

- One static page, no server, no database, no tracking.
- Memory is encrypted on your device; the password and the plaintext never leave the page.
- Reads Robinhood Chain mainnet (chain 4663) from the public RPC, contracts on Sourcify and route quotes from KyberSwap, straight from your browser.
- Anything that sends money or writes to the chain is simulated first (`eth_call` and `eth_estimateGas`) and then signed in **your own wallet**. ATLAS never holds funds, keys or seed phrases.
- No predictions, no scores, not financial advice.

## Run it yourself

```bash
git clone https://github.com/atlasboard/atlasboard.github.io
cd atlasboard.github.io
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Contact

hello@atlasboard.dev

## License

MIT
