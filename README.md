

### 🪙 Tokenomics & Coin Details

* **Name:** PrimeAxionux
* **Ticker:** $PEXN
* **Total Max Supply:** 18,000,000 PEXN
* **Genesis Mint (Pre-mine):** 1,000 PEXN (Minted to deployer at launch)
* **Base Block Reward:** 365 PEXN per Epoch
* **Epoch Duration (Block Time):** 18 Minutes
* **Halving Cycle:** The block reward automatically halves every time 1,000,000 PEXN is minted, ensuring long-term deflationary pressure.


### ⛏️ The Mining Engine (True PoW)

Unlike standard staking contracts, Prime Axionux requires actual cryptographic work, mirroring Bitcoin's philosophy but running natively on the EVM.

* **Network Capacity:** Hardcapped at strictly **365 Miners** globally.
* **Sybil Resistance (The Deposit):** To join the network, a miner must stake **0.01 ETH**. This prevents malicious actors from flooding the network with fake wallets.
* **Refundable Exits:** Miners can call `leaveMining()` at any time to claim their unpaid PEXN and get their 0.01 ETH deposit fully refunded.
* **The Puzzle:** Miners must calculate a hash using `keccak256(Miner_Address + Session_Blockhash + Nonce)` that falls below a difficulty target of `type(uint256).max / 100,000`.



### 🛡️ Security & Anti-Bot Features

This is where the contract shines. It is rigged with traps specifically designed to break automated botnets and flash-loan attackers.

* **The "Anti-Ghost" Speed Limit (`MIN_HACK_WINDOW`):** If a miner submits a valid mathematical proof in under **15 seconds**, the contract assumes they are using an illegal supercomputer/botnet and instantly rejects the proof, forcing them to restart.
* **Session Expiration (`MAX_HACK_WINDOW`):** A mining session expires if the proof takes longer than **5 minutes** to submit, keeping the network hash rate actively competitive.
* **Dynamic Blockhash Sync:** Because the puzzle requires the specific blockhash from the moment the session started, hackers cannot "pre-compute" nonces offline.
* **Gas-Limit Trap Bypass:** The contract uses a `gasleft() > 2_000_000` rule during massive treasury syncs. If a transaction lacks sufficient gas, it gracefully pauses the sync rather than reverting and burning the user's gas fees.



### 🏦 Macroeconomic & Admin Controls

The contract is designed to run autonomously for 18 years, but it gives the owner absolute control over network maintenance.

* **The Treasury Sweep (Ghost Network):** If no miners solve a block during an 18-minute epoch, the 365 PEXN reward isn't lost. It is permanently minted to the `maintenanceWallet`. This ensures the 18-year halving schedule stays mathematically perfect, even if the network is empty.
* **The Zombie Sweeper (`ZOMBIE_TIMEOUT`):** If a registered miner fails to submit a proof for **30 Days**, the owner can execute `kickZombieMiner()`. This forcibly boots the dead node to free up a slot for a new miner, and seizes their 0.01 ETH deposit and unpaid PEXN to the maintenance wallet.
* **Immutable Contract:** The `renounceOwnership()` function is hardcoded to revert. The contract can never be accidentally abandoned, ensuring the network always has a maintainer.
* **Safe ETH Rescue:** If someone accidentally sends raw ETH to the contract, the owner can sweep it using `rescueTrappedETH()`. However, the math strictly protects `totalLockedDeposits`, meaning the owner can *never* steal the 0.01 ETH deposits that belong to active miners.

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
