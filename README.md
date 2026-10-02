<p align="center">
  <img src="assets/korsh-coins.png" alt="Korsh ($KSH) Logo" width="220" />
</p>

# KORSH ($KSH) — Official Technical Whitepaper

<p align="center">
  <b>🌐 Language / Idioma:</b> <b>🇬🇧 English (Current)</b> &nbsp;|&nbsp; <a href="README_ES.md">🇪🇸 Leer en Español</a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License: MIT" /></a>
  <a href="WHITEPAPER.md"><img src="https://img.shields.io/badge/Consensus-PoW%20%2B%20DMN-orange.svg" alt="Consensus" /></a>
  <a href="WHITEPAPER.md"><img src="https://img.shields.io/badge/Algorithm-Yespower%201.0%20(N%3D256%2C%20r%3D8)-green.svg" alt="Algorithm" /></a>
  <a href="WHITEPAPER.md"><img src="https://img.shields.io/badge/Max%20Supply-10%2C000%2C000%20KSH-purple.svg" alt="Max Supply" /></a>
  <a href="WHITEPAPER.md"><img src="https://img.shields.io/badge/Block%20Time-60s-brightgreen.svg" alt="Block Time" /></a>
  <a href="WHITEPAPER.md"><img src="https://img.shields.io/badge/Premine-0%25%20(Fair%20Launch)-success.svg" alt="Premine: 0%" /></a>
</p>

> **A Hybrid Consensus Cryptocurrency: Pure CPU Proof-of-Work and Deterministic Masternodes**  
> *Una Criptomoneda de Consenso Híbrido: Prueba de Trabajo CPU Pura y Masternodes Deterministas*

---

## 📄 Official Whitepaper Documents / Documentos Oficiales

Select your preferred language:

| Document | Language | Description | Link |
| :--- | :---: | :--- | :---: |
| **English Whitepaper** | 🇬🇧 English | Full technical documentation, mathematical models & architecture | **[Read WHITEPAPER.md](WHITEPAPER.md)** |
| **Spanish Whitepaper** | 🇪🇸 Español | Documento técnico completo en español, modelos y arquitectura | **[Leer WHITEPAPER_ES.md](WHITEPAPER_ES.md)** |

---

## ⚡ Project Overview

**Korsh ($KSH)** is a sovereign Layer 1 open-source blockchain engineered to protect and fulfill Satoshi Nakamoto's original vision: *"one CPU, one vote"*.

Korsh couples democratic CPU mining via the memory-hard **Yespower 1.0 ($N=256, r=8$)** algorithm (strictly bounded to CPU Level 2 cache) with an incentivized second layer of **Deterministic Masternodes (DIP0003)** delivering:
* ⚡ **InstantSend:** Real-time transaction locking and settlement in **2 to 3 seconds**.
* 🛡️ **ChainLocks:** LLMQ cryptographic block signing that renders **51% deep reorganization attacks impossible**.
* 🏛️ **On-Chain Governance:** Decentralized community proposal funding and superblock voting.
* 💎 **Sound Deflationary Tokenomics:** Strictly capped supply of **10,000,000 KSH** with **0% Premine (Fair Launch)**.

---

## 📊 Key Network Specifications

| Parameter | Mainnet Specification |
| :--- | :--- |
| **Coin Name** | Korsh |
| **Ticker Symbol** | **$KSH** |
| **Consensus Model** | Hybrid: Pure CPU Proof-of-Work (PoW) + Deterministic Masternodes (DMN) |
| **Hashing Algorithm** | **Yespower 1.0 ($N=256, r=8$)** |
| **Difficulty Retargeting** | **Dark Gravity Wave v3 (DGW-v3)** (20-block window) |
| **Block Target Spacing** | **60 seconds** (1 minute) |
| **Initial Base Block Reward** | **2.00 KSH** |
| **Subsidy Split** | **70% PoW Miners** (1.40 KSH) \| **30% Masternodes** (0.60 KSH) |
| **Maximum Supply (Hard Cap)** | **10,000,000 KSH** (Immutable) |
| **Halving Interval** | Every **2,500,000 blocks** (~4.75 years) |
| **Premine** | **0%** (100% Fair Launch) |
| **Regular Masternode Collateral** | **1,500 KSH** (Voting weight: 1) |
| **Evolution Masternode Collateral** | **7,500 KSH** (Voting weight: 5) |
| **Address Encoding** | Base58 with prefix **"S"** (Prefix Byte: 63 / `0x3F`) |
| **Default Network Ports** | P2P: `8383` \| RPC: `8382` |
| **Genesis Block Hash** | `000017ec1f2f978429db70495ec7653aedca360e5f251bfe2a780ae5e731d7eb` |
| **Genesis Merkle Root** | `1dd60dd52dda0fd4b6912baca209aa327ae8b4825a23415b0a4356585897d073` |
| **Genesis Message** | *"In honor of my uncle Satoshi Nakamoto"* |

---

## 🏗️ Two-Tier Network Architecture

```
┌────────────────────────────────────────────────────────────────────────┐
│                        KORSH HYBRID ARCHITECTURE                       │
├────────────────────────────────────┬───────────────────────────────────┤
│    Tier 1: Yespower CPU Miners     │  Tier 2: Deterministic Masternodes│
├────────────────────────────────────┼───────────────────────────────────┤
│ • Pure CPU Mining (Yespower 1.0)   │ • Deterministic lists (DIP0003)   │
│ • L2 cache bound (~256 KB)         │ • LLMQ Quorums + BLS Signatures   │
│ • Dark Gravity Wave v3 retargeting │ • InstantSend finality (2-3s)     │
│ • Produces blocks every 60s        │ • ChainLocks (51% reorg defense)  │
│ • Receives 70% of block subsidy    │ • Receives 30% of block subsidy   │
└────────────────────────────────────┴───────────────────────────────────┘
```

---

## 🌐 Official Ecosystem Links

* **Core Source Code:** [github.com/Korsh-Dev/Korsh-Code-Mainnet](https://github.com/Korsh-Dev/Korsh-Code-Mainnet)
* **Lightweight Web Wallet:** [wallet.korsh.org](https://wallet.korsh.org)
* **Block Explorer:** [explorer.korsh.org](https://explorer.korsh.org)
* **Official Mining Pool:** [pool.korsh.org](https://pool.korsh.org)

---

## 📜 License

This repository and all official Korsh whitepaper specifications are released under the open-source [MIT License](LICENSE).
