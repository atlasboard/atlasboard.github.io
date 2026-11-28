# Security

ATLAS is a static web page. It has no server, no database and no account system, so there is nothing of yours stored with us.

## What ATLAS can and cannot do

| | |
| --- | --- |
| Hold your funds | No. Every write is signed in your own wallet. |
| See your private key or seed phrase | No. ATLAS never asks for them. If anything claiming to be ATLAS does, it is not us. |
| Move tokens without asking | No. Each transaction is shown in your wallet, and is simulated on mainnet first. |
| Get an unlimited approval | No. Approvals are for the exact amount of the action, and Permit2 permissions last one hour. |
| Read your Memory vault | No. It is encrypted on your device (AES-256-GCM, key from your password with PBKDF2). The password never leaves the page. |
| Keep your OpenRouter key | No. It stays in the memory of the open tab and is sent only to openrouter.ai. |

## Threat model, honestly

- **The page itself.** Anyone who could change the files in this repository could change what the page does. Read the code, or run it yourself from a commit you checked (see the README).
- **Third parties.** Prices come from the KyberSwap router, verified source from Sourcify, chain data from the public Robinhood Chain RPC, and model lists from OpenRouter. If one of them is down or wrong, the tool that uses it says so or shows less. It never invents a number.
- **Your wallet.** ATLAS can only ask. Always read the popup: the contract, the amount, and for approvals the spender.
- **Not audited.** The page uses audited, public contracts (Uniswap v4 PositionManager, Permit2, the USDG token) and deploys none of its own.

## Reporting a problem

Email hello@atlasboard.dev or send a DM to [@atlasboard_](https://x.com/atlasboard_). Please include the page, what you did, and what you saw. We will answer, fix it in the open, and credit you in the changelog if you want.
