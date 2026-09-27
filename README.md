# ArcBounty onboarding report — first live Arc mainnet session

Date: 2026-09-27  
Wallet: MetaMask  
Wallet address: `0x41D926f3853fa2D3bdc9971d105e33210ba21c71`  
Device: MacBook Pro, macOS  
Browser: Google Chrome 153.0.8010.53  
Network: Arc mainnet, chain ID `5042`

## Summary

This report documents my first live ArcBounty onboarding session. I first completed bounty #15, then took bounty #14 during the same session so I could submit the onboarding report with actual evidence rather than a hypothetical walkthrough.

## Numbered walkthrough

1. **Opened the official Start page.** I used `https://arcbounty.app/start`. It lists Arc mainnet as chain ID `5042`, RPC `https://rpc.blockdaemon.mainnet.arc.io`, and USDC as the native gas/reward currency. See `01-arc-start.png`.

2. **Prepared MetaMask.** My existing MetaMask installation initially opened on `Import wallet / Secret Recovery Phrase` instead of a normal unlocked account. I completed the wallet recovery locally. No seed phrase or private key was copied into this report or any screenshot.

3. **Connected ArcBounty to MetaMask.** ArcBounty detected the recovered account `0x41D9…1c71`.

4. **Hit a network mismatch on the first Take attempt.** MetaMask initially prepared the transaction on **Ethereum** and showed an estimated network fee around `$0.12` in ETH. I cancelled instead of signing on the wrong chain.

5. **Added/updated Arc mainnet from the ArcBounty Start page.** MetaMask showed an `Update Arc` prompt for RPC `rpc.blockdaemon.mainnet.arc.io`. After confirmation, the wallet had Arc available in the network list. See `03-metamask-arc.png`.

6. **Hit a zero-gas balance blocker.** With Arc selected, MetaMask would not allow the Take transaction because the Arc native USDC balance was `0`. This matched the Start page explanation that USDC is both the reward asset and the gas token.

7. **Funded the wallet from Bybit.** Arc Explorer labels the sender of the funding transaction as **Bybit 2**. The wallet received exactly `2.000000 USDC` on Arc. The explorer shows the sender-side transaction fee as `0.00042 USDC`; the recipient received the full 2 USDC. See `02-arc-explorer-funding.png`.

   Funding tx: `0x3e3f8a3e14c69fe7995b5faf96fd0ad77a40ea23d2cc73827b7ea725daca03cc`

8. **Retried Take.** MetaMask briefly showed two queued requests from the retries (`1 of 2`). One simulation displayed the warning `Эта транзакция, скорее всего, не удастся` (`This transaction is likely to fail`). I cancelled the stale request instead of paying gas for a likely-failing duplicate.

9. **Completed the first job (#15).** ArcBounty showed bounty #15 as `Assigned`; I submitted the reproducible mobile-overflow bug report. The site requested a message signature containing `ArcBounty IPFS pin`, the wallet address, and a timestamp, then a normal Arc transaction. After confirmation, #15 changed to `Submitted`.

   First-job report: https://github.com/williamleewilliam1-star/arcbounty-bug-15-report-20260927

10. **Took onboarding bounty #14.** The successful Arc transaction calls `takeBounty` with job ID `14`. It succeeded at 2026-09-27 20:56:05 (+10:00). Arc Explorer reports a fee of `0.004253087 USDC`. ArcBounty now shows #14 as `Assigned` to this wallet. See `04-bounty14-assigned.png`.

   Take #14 tx: `0x9ede2178321597cfac6c0f3572650dba21cb3cf51f37eae33359d85c3b4c4f41`

## Problems and resolutions

| Problem | Expected | Actual | Resolution |
| --- | --- | --- | --- |
| MetaMask was on recovery screen | Normal unlocked wallet | `Import wallet / Secret Recovery Phrase` | Finished recovery locally; never exposed seed/private key |
| Wrong network on first Take | Arc mainnet | Ethereum, ~`$0.12` ETH fee | Cancelled; added/updated Arc from Start page |
| No gas | Take button should be signable | Arc balance `0 USDC`, confirmation unavailable | Sent 2 USDC from Bybit to the Arc address |
| Duplicate queued Take requests | One confirmation | MetaMask showed `1 of 2`; one warned it would likely fail | Cancelled stale request and kept only the valid flow |
| Need evidence for submission | Plain report link | ArcBounty additionally signs an `ArcBounty IPFS pin` message before the on-chain submit | Reviewed the message and signed only after confirming it contained no spending permission |

## Costs observed

- Funding received: `2.000000 USDC` from Bybit 2.
- Funding transaction fee shown by Arc Explorer: `0.00042 USDC` on the sender transaction.
- Take #15 fee observed in Arc Explorer: `0.00462074 USDC`.
- Submit #15 fee observed in Arc Explorer: `0.00317852 USDC`.
- Take #14 fee: `0.004253087 USDC`.
- Arc gas costs were therefore fractions of one cent per transaction.

## Screenshots

### 1. ArcBounty Start page / Arc network parameters
![ArcBounty Start](01-arc-start.png)

### 2. Arc Explorer funding history (Bybit 2 → wallet, 2 USDC)
![Arc Explorer funding](02-arc-explorer-funding.png)

### 3. MetaMask with Arc available in the network selector
![MetaMask Arc](03-metamask-arc.png)

### 4. Bounty #14 assigned to the connected wallet
![Bounty 14 assigned](04-bounty14-assigned.png)

## Security note

No seed phrase, private key, wallet password, or signing credential is included in this report or the screenshots.
