<p align="center">
  <img src="assets/korsh-coins.png" alt="Korsh ($KSH) Logo" width="220" />
</p>

# KORSH ($KSH) CORE WHITEPAPER

<p align="center">
  <b>🌐 Language / Idioma:</b> <b>🇬🇧 English (Current)</b> &nbsp;|&nbsp; <a href="WHITEPAPER_ES.md">🇪🇸 Leer en Español</a>
</p>

---

**A Hybrid Consensus Cryptocurrency: Pure CPU Proof-of-Work and Deterministic Masternodes**

*Version:* 1.0 — *Network:* Mainnet (Active)  
*Date:* October 2026  
*License:* MIT Open Source License  
*Official Code Repository:* [github.com/Korsh-Dev/Korsh-Code-Mainnet](https://github.com/Korsh-Dev/Korsh-Code-Mainnet)  
*Whitepaper Repository:* [github.com/Korsh-Dev/White-Paper-Korsh](https://github.com/Korsh-Dev/White-Paper-Korsh)  

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Philosophy and Design Principles](#2-philosophy-and-design-principles)
3. [Technical Specifications and Network Parameters](#3-technical-specifications-and-network-parameters)
4. [Hybrid Consensus Architecture: Layer 1 and Layer 2](#4-hybrid-consensus-architecture-layer-1-and-layer-2)
   - 4.1 [Layer 1: CPU Mining via Yespower 1.0 (N=256, r=8)](#41-layer-1-cpu-mining-via-yespower-10-n256-r8)
   - 4.2 [Dynamic Retargeting: Dark Gravity Wave v3 (DGW-v3)](#42-dynamic-retargeting-dark-gravity-wave-v3-dgw-v3)
   - 4.3 [Layer 2: Deterministic Masternodes (DIP0003)](#43-layer-2-deterministic-masternodes-dip0003)
   - 4.4 [LLMQ Quorums and BLS Threshold Signatures](#44-llmq-quorums-and-bls-threshold-signatures)
   - 4.5 [InstantSend: Real-Time Settlement and Double-Spend Immunity](#45-instantsend-real-time-settlement-and-double-spend-immunity)
   - 4.6 [ChainLocks: Cryptographic Protection Against 51% Reorganization Attacks](#46-chainlocks-cryptographic-protection-against-51-reorganization-attacks)
   - 4.7 [Decentralized On-Chain Governance and Treasury](#47-decentralized-on-chain-governance-and-treasury)
5. [Tokenomics and Monetary Issuance](#5-tokenomics-and-monetary-issuance)
   - 5.1 [Foundational Economic Tenets](#51-foundational-economic-tenets)
   - 5.2 [Mathematical Emission Formulation](#52-mathematical-emission-formulation)
   - 5.3 [Multi-Era Emission Schedule](#53-multi-era-emission-schedule)
   - 5.4 [Collateral Mechanics and Masternode Supply Shock](#54-collateral-mechanics-and-masternode-supply-shock)
6. [Software Ecosystem and Infrastructure](#6-software-ecosystem-and-infrastructure)
   - 6.1 [Korsh Core Daemon and Qt GUI Wallet](#61-korsh-core-daemon-and-qt-gui-wallet)
   - 6.2 [Dedicated CPU Miner (AVX2 / AVX-512)](#62-dedicated-cpu-miner-avx2--avx-512)
   - 6.3 [Client-Side Web Wallet](#63-client-side-web-wallet)
   - 6.4 [Public Block Explorer](#64-public-block-explorer)
   - 6.5 [Official Mining Pool (Stratum)](#65-official-mining-pool-stratum)
   - 6.6 [Mobile Mining and Network Monitoring App](#66-mobile-mining-and-network-monitoring-app)
7. [Security Analysis and Threat Resistance](#7-security-analysis-and-threat-resistance)
   - 7.1 [Economic Infeasibility of Hashrate Rental](#71-economic-infeasibility-of-hashrate-rental)
   - 7.2 [Sybil Attack Resistance in Layer 2](#72-sybil-attack-resistance-in-layer-2)
   - 7.3 [Deterministic Checkpointing](#73-deterministic-checkpointing)
8. [Strategic Roadmap](#8-strategic-roadmap)
9. [Conclusion](#9-conclusion)
10. [Legal Disclaimer](#10-legal-disclaimer)

---

## 1. Executive Summary

**Korsh ($KSH)** is a sovereign, open-source Layer 1 decentralized blockchain engineered to realize and protect Satoshi Nakamoto's original vision: *"one CPU, one vote"*.

As the cryptocurrency landscape matured, classical Proof-of-Work (PoW) consensus mechanisms became increasingly monopolized by industrial mega-facilities operating Application-Specific Integrated Circuit (ASIC) clusters, commercial GPU arrays, and Field-Programmable Gate Arrays (FPGAs). This ongoing capital concentration disenfranchised everyday users, erected insurmountable entry barriers, and introduced central points of vulnerability through geographic and silicon manufacturing cartels.

Korsh eliminates these systemic flaws through an integrated two-tier architecture:

1. **Fair Launch and 0% Premine:** Zero developer pre-allocations, no private sales, no ICO, and no venture capital reservations. Every existing coin originates transparently from computational validation or network infrastructure service.
2. **Yespower 1.0 Algorithm ($N=256, r=8$):** A strictly memory-hard hashing function tailored to fit within the dedicated Level 2 (L2) cache of standard 64-bit consumer CPUs. This design negates the economic and physical viability of ASICs and GPUs while maintaining optimal energy efficiency per hash.
3. **Deterministic Masternode Layer (DIP0003):** An incentivized second layer running on-chain deterministic node lists, secured by Long-Living Masternode Quorums (LLMQ) and BLS threshold signatures. This tier delivers near-instant transaction finality (**InstantSend** in 2–3 seconds), mathematical immunity against 51% deep chain reorganizations (**ChainLocks**), and decentralized on-chain governance.
4. **Strict Deflationary Monetary Policy:** An immutable hard cap of **10,000,000 KSH** governed by predictable halving cycles every 2,500,000 blocks (~4.75 years), providing mathematical scarcity aligned with digital sound money principles.

---

## 2. Philosophy and Design Principles

Korsh is founded upon four foundational axioms:

* **Universal Accessibility:** Consensus participation and coin minting must not demand multi-million-dollar capital outlays. Any individual with a modern 64-bit laptop, desktop PC, or server can mine KSH profitably and validate transactions.
* **Structural Centralization Resistance:** By establishing a ~256 KB memory footprint per hashing thread aligned with L2 CPU caches, the protocol renders dedicated ASIC silicon and massive GPU thread parallelism economically uncompetitive.
* **Real-World Transactional Velocity:** While a 60-second block target guarantees steady base-layer settlement, masternode-driven InstantSend achieves transaction finality within 2–3 seconds, allowing merchants and point-of-sale systems to accept zero-confirmation payments with full cryptographic safety.
* **Radical Transparency:** The genesis block was generated and audited publicly under verifiable conditions, immortalizing the tribute: *"In honor of my uncle Satoshi Nakamoto"*.

---

## 3. Technical Specifications and Network Parameters

The table below outlines the core cryptographic and consensus parameters of the Korsh mainnet:

| Parameter | Mainnet Specification |
| :--- | :--- |
| **Coin Name** | Korsh |
| **Asset Ticker** | **$KSH** |
| **Consensus Model** | Hybrid: Pure CPU Proof-of-Work (PoW) + Deterministic Masternodes |
| **PoW Hashing Algorithm** | **Yespower 1.0 ($N=256, r=8$)** |
| **Difficulty Retargeting** | **Dark Gravity Wave v3 (DGW-v3)** (20-block rolling window) |
| **Target Block Interval** | **60 seconds** (1 minute) |
| **Initial Base Block Reward** | **2.00 KSH** |
| **Block Subsidy Allocation** | **70% PoW Miners** (1.40 KSH) \| **30% Masternodes** (0.60 KSH) |
| **Maximum Supply (Hard Cap)** | **10,000,000 KSH** (Strictly Enforced) |
| **Halving Interval** | Every **2,500,000 blocks** (~4.75 years) |
| **Premine** | **0 KSH (0.00%) — Fair Launch** |
| **Regular Masternode Collateral** | **1,500 KSH** (Voting weight: 1) |
| **Evolution Masternode Collateral** | **7,500 KSH** (Voting weight: 5) |
| **Address Encoding** | Base58 with prefix **"S"** (Prefix Byte: `63` decimal / `0x3F`) |
| **P2P Protocol Magic Bytes** | `0xCB 0x4B 0x53 0x48` (`\xcbKSH`) |
| **Default P2P Port** | **8383** |
| **Default RPC Port** | **8382** |
| **Genesis Block Hash** | `000017ec1f2f978429db70495ec7653aedca360e5f251bfe2a780ae5e731d7eb` |
| **Genesis Merkle Root** | `1dd60dd52dda0fd4b6912baca209aa327ae8b4825a23415b0a4356585897d073` |
| **Genesis Timestamp Message** | *"In honor of my uncle Satoshi Nakamoto"* |

---

## 4. Hybrid Consensus Architecture: Layer 1 and Layer 2

Korsh separates network tasks across two interconnected, collaborative tiers:

```
┌────────────────────────────────────────────────────────────────────────┐
│                        KORSH NETWORK TOPOLOGY                          │
└────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                    TIER 1: PROOF-OF-WORK CPU MINING                    │
│  • Algorithm: Yespower 1.0 (N=256, r=8)                                │
│  • Memory footprint ~256 KB tuned to CPU L2 cache                      │
│  • Per-block dynamic difficulty retargeting: Dark Gravity Wave v3      │
│  • Raw transaction collection, validation, and block assembly          │
│  • Block production rate: 60 seconds                                   │
│  • Economic subsidy: 70% of block reward (1.40 KSH in Era 1)           │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ Block Propagation
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│              TIER 2: DETERMINISTIC MASTERNODES (DIP0003)               │
│  • High-availability nodes with verifiable collateral (1,500 KSH)      │
│  • LLMQ Quorums with BLS threshold signatures                          │
│  • InstantSend: Deterministic transaction locking in 2–3 seconds       │
│  • ChainLocks: Cryptographic block signing preventing 51% reorgs       │
│  • On-chain decentralized governance and community proposal funding    │
│  • Economic subsidy: 30% of block reward (0.60 KSH in Era 1)           │
└────────────────────────────────────────────────────────────────────────┘
```

### 4.1 Layer 1: CPU Mining via Yespower 1.0 ($N=256, r=8$)

The primary consensus layer utilizes **Yespower 1.0**, an advanced memory-hard cryptographic proof-of-work algorithm designed to enforce symmetric hardware competitiveness.

The memory working set per hashing thread is governed by:

$$\text{Memory Per Thread} = (128 \times N \times r) \text{ bytes} + \text{S-Boxes}$$

Under Korsh parameters ($N = 256, r = 8$):

$$\text{Working Memory} = (128 \times 256 \times 8) \text{ bytes} = 262,144 \text{ bytes} \approx 256 \text{ KB}$$

Including substitution boxes (S-Boxes) and operating buffers, each mining thread maintains an active footprint of ~256 KB to 356 KB.

#### Architectural Ramifications:

1. **L2 Cache Residency:** Modern consumer processors (Intel Core, AMD Zen series, Apple Silicon, and contemporary ARM64 architectures) provide between 512 KB and 1024 KB of dedicated L2 cache per core. Because the 256 KB working region fits entirely within local L2 cache, computation operates at full processor core clock speeds without memory bus stalls.
2. **GPU Disqualification:** GPUs excel at performing lightweight, parallel operations across thousands of simple threads, but provide minimal on-chip cache per compute unit (frequently under 32–64 KB). Forcing a 256 KB working set per thread exhausts on-chip GPU SRAM and causes constant thrashing to external high-latency VRAM. Consequently, GPUs deliver inferior hash-per-watt ratios compared to standard CPUs.
3. **ASIC and FPGA Infeasibility:** Fabricating custom ASIC silicon with large banks of fast SRAM on-die dramatically increases die size, defect rates, and silicon fabrication costs. The cost-to-performance ratio makes custom ASIC development commercially unviable against off-the-shelf consumer CPUs.

### 4.2 Dynamic Retargeting: Dark Gravity Wave v3 (DGW-v3)

To safeguard against hashrate volatility and opportunistic multi-pool hopping, Korsh employs **Dark Gravity Wave v3**:
* **Per-Block Recalibration:** Difficulty recalculates continuously at each block instead of arbitrary fixed windows.
* **Weighted Harmonic Moving Average:** A 20-block rolling window dynamically calculates expected intervals, assigning higher statistical weights to the most recent blocks.
* **Bound Constraints:** Dampening parameters prevent runaway difficulty spikes and eliminate timestamp manipulation (*time-warp attacks*).

### 4.3 Layer 2: Deterministic Masternodes (DIP0003)

The second tier complies with the **DIP0003** specification, establishing an on-chain deterministic state machine for masternode registries:
* **Provider Registration Transaction (ProRegTx):** Operators lock an exact unspent transaction output (UTXO) of **1,500 KSH** (Regular) or **7,500 KSH** (Evolution) and broadcast cryptographic key delegations on-chain.
* **Separation of Keys:**
  * **Owner Key:** Authorizes administrative operations and collateral reassignment; kept securely in cold offline storage.
  * **Operator Key (BLS):** Used exclusively by the active VPS server to sign peer-to-peer consensus messages and quorum operations.
  * **Voting Key:** Used to participate in community governance and proposal voting.
  * **Payout Script:** Cold wallet address receiving the automated 30% masternode payment (0.60 KSH in Era 1), ensuring operational servers hold no spendable balance.

```
┌────────────────────────────────────────────────────────────────────────┐
│                   DIP0003 KEY SEGREGATION ARCHITECTURE                │
├───────────────────┬────────────────────────────────────────────────────┤
│ Key Role          │ Security Boundary & Storage Location               │
├───────────────────┼────────────────────────────────────────────────────┤
│ Owner Key         │ Collateral authority; offline cold storage.        │
│ Operator Key      │ BLS signing key on remote production server.       │
│ Voting Key        │ Governance voting privileges.                      │
│ Payout Address    │ Reward destination address; cold storage wallet.   │
└───────────────────┴────────────────────────────────────────────────────┘
```

### 4.4 LLMQ Quorums and BLS Threshold Signatures

Masternodes deterministically form **Long-Living Masternode Quorums (LLMQs)** using a non-interactive Distributed Key Generation (DKG) protocol.

By leveraging **Boneh-Lynn-Shacham (BLS12-381)** threshold cryptography, quorums aggregate individual member signatures into a single, compact threshold signature. This enables high-velocity consensus validation across thousands of network participants with minimal bandwidth and processing overhead.

### 4.5 InstantSend: Real-Time Settlement and Double-Spend Immunity

With **InstantSend**, transaction inputs are evaluated and locked by active LLMQs within **2 to 3 seconds**:
1. An incoming transaction is broadcast to the network.
2. The active quorum verifies that the referenced UTXOs are unspent and generates an *InstantSend Lock (ISLOCK)*.
3. Once an ISLOCK is propagated, all full nodes recognize the transaction as irreversible.
4. Any competing transaction attempting a double spend is deterministically dropped, enabling retail and automated payment environments to accept zero-confirmation transactions safely.

### 4.6 ChainLocks: Cryptographic Protection Against 51% Reorganization Attacks

ChainLocks effectively eliminate deep blockchain reorganization threats:
1. Upon receiving a newly mined block from Layer 1, the LLMQ evaluates block validity.
2. Once verified, quorum members sign a `CLSIG` (ChainLock Signature).
3. When the threshold is reached, the signed ChainLock is broadcast across the network.
4. **Finality Rule:** Once a block receives a ChainLock, nodes permanently reject any competing chain branch at equal or lower block height, regardless of proof-of-work difficulty.
5. This renders hostile private mining attacks completely powerless, providing institutional-grade settlement guarantees.

### 4.7 Decentralized On-Chain Governance and Treasury

Masternode operators govern protocol growth through on-chain proposals. Anyone can submit development proposals funded via protocol **superblocks**. Operators vote using their `Voting Key`, ensuring decentralized, self-sustaining development without centralized foundations.

---

## 5. Tokenomics and Monetary Issuance

### 5.1 Foundational Economic Tenets

1. **Absolute Hard Cap:** The maximum supply is strictly limited to **10,000,000 KSH**. When cumulative issuance reaches this cap, block subsidies drop to zero.
2. **Fair Launch (0% Premine):** No tokens were pre-minted or set aside for founders, investors, or foundations.
3. **Balanced Incentive Distribution:** 70% of block rewards compensate computational power (miners) while 30% rewards high-availability infrastructure (masternodes).

### 5.2 Mathematical Emission Formulation

The block subsidy $S(h)$ at block height $h$ is defined by:

$$S(h) = \left\lfloor \frac{S_0}{2^{\lfloor h / H \rfloor}} \right\rfloor$$

Where:
* $S_0 = 2.00 \text{ KSH}$ (Initial base block subsidy).
* $H = 2,500,000$ (Halving interval in blocks).
* $\lfloor x \rfloor$ denotes the floor function.

Subsidies are split as follows:

$$\text{Miner Reward: } R_{\text{miner}}(h) = 0.70 \times S(h)$$

$$\text{Masternode Reward: } R_{\text{mn}}(h) = 0.30 \times S(h)$$

### 5.3 Multi-Era Emission Schedule

At 60 seconds per block, each halving period covers:

$$T_{\text{era}} = \frac{2,500,000 \times 60 \text{ s}}{86,400 \text{ s/day} \times 365.25 \text{ days/year}} \approx 4.752 \text{ years}$$

| Era | Block Height | Est. Timeline | Block Subsidy | Miner (70%) | Masternode (30%) | Era Issuance | Cumulative Supply | % of Total Cap |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Era 1** | $0 - 2,499,999$ | Years 0.00 – 4.75 | **2.00 KSH** | 1.40 KSH | 0.60 KSH | 5,000,000 KSH | **5,000,000 KSH** | 50.00% |
| **Era 2** | $2,500,000 - 4,999,999$ | Years 4.75 – 9.50 | **1.00 KSH** | 0.70 KSH | 0.30 KSH | 2,500,000 KSH | **7,500,000 KSH** | 75.00% |
| **Era 3** | $5,000,000 - 7,499,999$ | Years 9.50 – 14.25 | **0.50 KSH** | 0.35 KSH | 0.15 KSH | 1,250,000 KSH | **8,750,000 KSH** | 87.50% |
| **Era 4** | $7,500,000 - 9,999,999$ | Years 14.25 – 19.00 | **0.25 KSH** | 0.175 KSH | 0.075 KSH | 625,000 KSH | **9,375,000 KSH** | 93.75% |
| **Era 5** | $10,000,000 - 12,499,999$ | Years 19.00 – 23.75 | **0.125 KSH** | 0.0875 KSH | 0.0375 KSH | 312,500 KSH | **9,687,500 KSH** | 96.88% |
| **Era 6** | $12,500,000 - 14,999,999$ | Years 23.75 – 28.50 | **0.0625 KSH** | 0.04375 KSH | 0.01875 KSH | 156,250 KSH | **9,843,750 KSH** | 98.44% |
| **Tail** | $\ge 15,000,000$ | Years 28.50+ | $\to 0$ | $\to 0$ | $\to 0$ | Remainder | **10,000,000 KSH** | **100.00%** |

### 5.4 Collateral Mechanics and Masternode Supply Shock

The 1,500 KSH collateral acts as an organic supply absorption mechanism. 

Annual rewards for masternodes during Era 1 total:

$$\text{Annual MN Reward Pool} = 1,440 \text{ blocks/day} \times 365.25 \text{ days} \times 0.60 \text{ KSH} = \mathbf{315,576 \text{ KSH/year}}$$

Projected individual masternode annual return on investment (ROI) is:

$$\text{Projected Annual ROI} = \left( \frac{\text{Annual MN Pool}}{M_{\text{active}} \times 1,500} \right) \times 100\%$$

| Active Masternodes | Total Locked KSH | % Circulating Locked (at 5M KSH) | Annual KSH / Node | **Estimated Annual ROI** |
| :---: | :---: | :---: | :---: | :---: |
| **50** | 75,000 KSH | 1.50% | 6,311.5 KSH | **420.8%** |
| **100** | 150,000 KSH | 3.00% | 3,155.8 KSH | **210.4%** |
| **250** | 375,000 KSH | 7.50% | 1,262.3 KSH | **84.1%** |
| **500** | 750,000 KSH | 15.00% | 631.2 KSH | **42.1%** |
| **1,000** | 1,500,000 KSH | 30.00% | 315.6 KSH | **21.0%** |
| **1,500** | 2,250,000 KSH | 45.00% | 210.4 KSH | **14.0%** |
| **2,000** | 3,000,000 KSH | 60.00% | 157.8 KSH | **10.5%** |

This mechanism stabilizes circulating market supply: high node participation locks significant proportions of liquid supply, while lower node counts automatically enhance yields to attract new infrastructure operators.

---

## 6. Software Ecosystem and Infrastructure

```
┌────────────────────────────────────────────────────────────────────────┐
│                        KORSH SOFTWARE ECOSYSTEM                        │
├────────────────────────────────────────────────────────────────────────┤
│  [korshd]           Full node consensus engine and daemon              │
│  [korsh-qt]         Desktop GUI wallet with Masternode Setup Wizard    │
│  [korsh-miner]      Dedicated CPU miner optimized for AVX2 and AVX-512 │
│  [wallet.korsh.org] Lightweight non-custodial browser wallet           │
│  [explorer.korsh.org] Real-time public blockchain explorer             │
│  [pool.korsh.org]   Stratum mining pool infrastructure                 │
│  [Mobile App]       Mobile mining and node monitoring application      │
└────────────────────────────────────────────────────────────────────────┘
```

### 6.1 Korsh Core Daemon and Qt GUI Wallet
The core client comprises `korshd` (daemon), `korsh-cli` (command line RPC), and `korsh-qt` (graphical interface):
* **Integrated Masternode Wizard:** Intuitive step-by-step guidance for key generation, collateral registration, and remote node deployment.
* **Modern UI & Dark Theme:** Clean interface displaying InstantSend locks, active peers, and balance breakdowns.
* **Encrypted Key Store:** Deterministic wallet derivation and encrypted secret storage.

### 6.2 Dedicated CPU Miner (AVX2 / AVX-512)
High-performance standalone C/C++ CPU mining binary utilizing low-level vector SIMD instructions:
* Optimized routines for **AVX2**, **AVX-512**, **SHA-NI**, and ARM64 **NEON**.
* Thread affinity management to maximize hash-per-watt efficiency.
* Full Stratum protocol compatibility for pool and solo hashing.

### 6.3 Client-Side Web Wallet
Hosted at `wallet.korsh.org`:
* Lightweight browser-based wallet without downloading the blockchain.
* Client-side private key generation: private keys never leave the browser.

### 6.4 Public Block Explorer
Hosted at `explorer.korsh.org`:
* Real-time auditing of blocks, transactions, difficulty, network hashrate, active masternodes, and ChainLock status.

### 6.5 Official Mining Pool (Stratum)
Hosted at `pool.korsh.org`:
* Low-latency Stratum servers supporting PPLNS pooled mining and solo mining.

### 6.6 Mobile Mining and Network Monitoring App
Enables convenient mobile monitoring of node statuses, network difficulty, and on-the-go wallet operations.

---

## 7. Security Analysis and Threat Resistance

### 7.1 Economic Infeasibility of Hashrate Rental
Standard GPU/ASIC algorithms allow attackers to temporarily rent massive computational power on platforms like NiceHash. Under Yespower ($N=256, r=8$), performance is bounded by CPU L2 cache latency. Cloud virtualized environments experience severe cache thrashing across virtual CPUs, making rental-based 51% attacks impractical and uneconomic.

### 7.2 Sybil Attack Resistance in Layer 2
Subverting LLMQ quorums requires acquiring a substantial percentage of all active masternodes. Given a 10,000,000 KSH total cap, attempting to accumulate sufficient collateral on open markets triggers extreme upward slippage, financially penalizing attackers before quorum thresholds can be compromised.

### 7.3 Deterministic Checkpointing
Periodic hardcoded checkpoints within core releases bound reorganization depth, preventing long-range reorganization attacks against newly connecting peers.

---

## 8. Strategic Roadmap

```
┌────────────────────────────────────────────────────────────────────────┐
│                        KORSH STRATEGIC ROADMAP                         │
└────────────────────────────────────────────────────────────────────────┘

 [Phase 1: Genesis & Base Consensus] ──────────► (COMPLETED)
  • Mainnet launch with 0% premine (Fair Launch).
  • Yespower 1.0 (N=256, r=8) activated on Layer 1.
  • Verified genesis block with memorial tribute message.
  • Multi-platform release binaries (Linux, Windows, macOS).

 [Phase 2: Infrastructure & Community] ────────► (COMPLETED / ACTIVE)
  • Public block explorer online (explorer.korsh.org).
  • Non-custodial web wallet deployed (wallet.korsh.org).
  • Official Stratum mining pool live (pool.korsh.org).
  • Active Discord and Telegram community channels established.

 [Phase 3: Mining Tools & Ecosystem Adoption] ─► (IN PROGRESS)
  • Proprietary AVX2 / AVX-512 optimized CPU miner release.
  • Global expansion of low-latency Stratum mining servers.
  • Automated one-click VPS deployment scripts for masternodes.
  • Full third-party security audits for web and mobile components.

 [Phase 4: Market Integration & Scalability] ──► (UPCOMING)
  • Indexing on hashrate tracking platforms (MiningPoolStats, CoinGecko, CMC).
  • Integration with major masternode analytical directories.
  • Exchange listings across decentralized (DEX) and centralized (CEX) venues.
  • Merchant SDKs and payment gateway integrations.
```

---

## 9. Conclusion

**Korsh ($KSH)** revitalizes the foundational ethos of cryptocurrency: accessible, trustless, and resistant to central monopolization. By uniting the democratic participation of **pure CPU Proof-of-Work (Yespower 1.0)** with the transaction speed, governance, and 51% defense of **Deterministic Masternodes (DIP0003 + ChainLocks)**, Korsh delivers a secure, scalable, and genuinely decentralized monetary network.

With an immutable cap of **10,000,000 KSH**, **0% premine**, and a comprehensive software ecosystem, Korsh stands as an enduring platform for financial sovereignty.

---

## 10. Legal Disclaimer

*This technical whitepaper is provided for informational and educational purposes only. Korsh is an open-source decentralized software initiative without a centralized corporate entity or profit-seeking governance.*

*Engaging in cryptocurrency mining, node operations, and asset holdings involves market and operational risks. Nothing within this document constitutes financial advice, investment recommendations, or an offer of securities. Participants are solely responsible for ensuring compliance with applicable regional laws and regulations.*

---

**© 2026 Korsh Open Source Development Community**  
*Licensed under the MIT License.*
