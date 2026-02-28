# ⚡ PRIME AXIONUX ($PEAX) - True PoW Mining Engine

Welcome to the official repository for the Prime Axionux Sequential Miner. This engine allows users to connect to the Polygon network and mine $PEAX using a mathematically verified Proof-of-Work algorithm.

## 🛡️ Security-First Architecture
This network was built with heavy defense mechanisms to ensure fair mining and prevent automated botnet extraction:
* **Dynamic Blockhash Sync:** The engine requires a live, synchronized session hash, preventing pre-computed nonce attacks.
* **Anti-Ghost Speed Limits:** Hardcoded smart contract traps automatically revert proofs submitted under 15 seconds to kill ultra-high-speed botnets.
* **Gas-Lock Bypassing:** The Master Engine utilizes a guaranteed 3,000,000 gas limit pipeline to ensure smooth treasury syncs even during heavy network congestion.

## 🚀 How to Mine
1. Install requirements: `pip install web3`
2. Clone this repository and configure your wallet address in `mine.py`.
3. Launch the engine: `python mine.py`

*Note: The engine features an autonomous UI with live hash-rate tracking and epoch maturity progress bars.*

**Founder & Lead Developer:** @axionux
