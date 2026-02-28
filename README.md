## 🪙 Economic Architecture & Tokenomics

PrimeAxionux ($PEXN) is engineered with a strict, algorithmic monetary policy. Designed around the principles of sound money, it combines the absolute scarcity of a hard-capped supply with a predictable, mathematically enforced emission schedule. 

### Core Contract Specifications
| Metric | Specification |
| :--- | :--- |
| **Token Name** | PrimeAxionux |
| **Ticker** | `$PEXN` |
| **Network** | Polygon (Amoy Testnet / Mainnet Ready) |
| **Maximum Supply (Hard Cap)** | 18,000,000 PEXN |
| **Contract Standard** | ERC-20 |
| **Decimals** | 18 |

### Genesis & Fair Launch Protocol
* **Genesis Allocation:** 1,000 PEXN (Exactly 0.005% of Total Supply).
* **Allocation Purpose:** Bootstrapping the network, initial liquidity provision, and deployer wallet verification.
* **Fair Mining:** There are no venture capital presales, no massive team unlocks, and no hidden reserves. The remaining **99.995%** of the total supply is strictly locked behind the Proof-of-Work smart contract and can only be extracted through active network participation.

### Emission Schedule & The Halving Algorithm
 $PEXN utilizes a dynamic **Supply-Based Halving Model** designed to create severe, predictable supply shocks:
* **Era 1 Base Reward:** 365 PEXN per solved block.
* **Target Block Time:** 18 Minutes (Max 80 blocks per day).
* **Maximum Daily Emission (Era 1):** ~29,200 PEXN.
* **The Halving Trigger (`HAL_INT`):** The block reward automatically cuts in half every time exactly **1,000,000 PEXN** is minted. 
* **Economic Eras:** This structure guarantees exactly 18 distinct economic "Eras," naturally increasing the scarcity and difficulty of acquiring $PEXN as the network matures.

### The "Ghost Network" Treasury Sync
To maintain the mathematical integrity of the 18-year macroeconomic timeline, the contract features a continuous ledger. If an 18-minute epoch passes without a miner successfully solving the block, the macroeconomic clock does not stop. The unmined 365 PEXN reward is automatically synced to the decentralized Maintenance Treasury. This ensures the halving schedule remains perfectly aligned with real-world time, even during periods of low network activity.
