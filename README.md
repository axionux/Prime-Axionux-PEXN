
# ⚡ PRIME AXIONUX ($PEXN) - True PoW Mining Engine

Welcome to the official repository for the Prime Axionux Sequential Miner. This engine allows users to connect to the Polygon network and mine $PEXN using a mathematically verified Proof-of-Work algorithm.

## 📝 Official Contract & Wallet Setup

* **Network:** Polygon Amoy Testnet
* **Contract Address:** `0x952A8E1D7055075790Ff9e0FE5659FCA37E2433E`
* **Token Symbol:** PEXN
* **Decimals:** 18

**How to Add $PEXN to MetaMask:**
1. Open MetaMask and switch your network to **Polygon Amoy**.
2. Go to the "Tokens" tab, scroll to the bottom, and click **Import tokens**.
3. Paste the Contract Address: `0x952A8E1D7055075790Ff9e0FE5659FCA37E2433E`
4. The Token Symbol (PEXN) and Decimals (18) will auto-fill.
5. Click **Next**, then click **Import**. Your mined balance will now be visible in your wallet!

---

## 🚀 How to Mine

1. Install requirements: `pip install web3`
2. Clone this repository and configure your wallet address in `mine.py`.
3. Launch the engine: `python mine.py`

*Note: The engine features an autonomous UI with live hash-rate tracking and epoch maturity progress bars.*

---

## 🪙 Tokenomics & Coin Details

* **Name:** PrimeAxionux
* **Ticker:** $PEXN
* **Total Max Supply:** 18,000,000 PEXN
* **Genesis Mint (Pre-mine):** 1,000 PEXN (Minted to deployer at launch)
* **Base Block Reward:** 365 PEXN per Epoch
* **Epoch Duration (Block Time):** 18 Minutes
* **Halving Cycle:** The block reward automatically halves every time 1,000,000 PEXN is minted, ensuring long-term deflationary pressure.

## ⛏️ The Mining Engine (True PoW)

Unlike standard staking contracts, Prime Axionux requires actual cryptographic work, mirroring Bitcoin's philosophy but running natively on the EVM.

* **Network Capacity:** Hardcapped at strictly **365 Miners** globally.
* **Sybil Resistance (The Deposit):** To join the network, a miner must stake **0.01 ETH**. This prevents malicious actors from flooding the network with fake wallets.
* **Refundable Exits:** Miners can call `leaveMining()` at any time to claim their unpaid PEXN and get their 0.01 ETH deposit fully refunded.
* **The Puzzle:** Miners must calculate a hash using `keccak256(Miner_Address + Session_Blockhash + Nonce)` that falls below a difficulty target of `type(uint256).max / 100,000`.

## 🛡️ Security-First Architecture & Anti-Bot Features

This network was built with heavy defense mechanisms to ensure fair mining and prevent automated botnet extraction:

* **Dynamic Blockhash Sync:** The puzzle requires a live, synchronized session hash from the moment the session started, preventing pre-computed nonce attacks offline.
* **The "Anti-Ghost" Speed Limit (`MIN_HACK_WINDOW`):** If a miner submits a valid mathematical proof in under **15 seconds**, the contract assumes they are using an illegal supercomputer/botnet and instantly rejects the proof, forcing them to restart.
* **Session Expiration (`MAX_HACK_WINDOW`):** A mining session expires if the proof takes longer than **5 minutes** to submit, keeping the network hash rate actively competitive.
* **Gas-Limit Trap Bypass:** The contract uses a `gasleft() > 2_000_000` rule during massive treasury syncs. The Master Engine utilizes a guaranteed 3,000,000 gas limit pipeline to ensure smooth treasury syncs even during heavy network congestion without reverting and burning user gas fees.

## 🏦 Macroeconomic & Admin Controls

The contract is designed to run autonomously for 18 years, but it gives the owner absolute control over network maintenance.

* **The Treasury Sweep (Ghost Network):** If no miners solve a block during an 18-minute epoch, the 365 PEXN reward isn't lost. It is permanently minted to the `maintenanceWallet`. This ensures the 18-year halving schedule stays mathematically perfect, even if the network is empty.
* **The Zombie Sweeper (`ZOMBIE_TIMEOUT`):** If a registered miner fails to submit a proof for **30 Days**, the owner can execute `kickZombieMiner()`. This forcibly boots the dead node to free up a slot for a new miner, and seizes their 0.01 ETH deposit and unpaid PEXN to the maintenance wallet.
* **Immutable Contract:** The `renounceOwnership()` function is hardcoded to revert. The contract can never be accidentally abandoned, ensuring the network always has a maintainer.
* **Safe ETH Rescue:** If someone accidentally sends raw ETH to the contract, the owner can sweep it using `rescueTrappedETH()`. However, the math strictly protects `totalLockedDeposits`, meaning the owner can *never* steal the 0.01 ETH deposits that belong to active miners.

---
**Founder & Lead Developer:** @axionux
