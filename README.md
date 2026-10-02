# KORSH ($KSH) — Official Technical Whitepaper

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Consensus: PoW + DMN](https://img.shields.io/badge/Consensus-PoW%20%2B%20DMN-orange.svg)](WHITEPAPER.md)
[![Algorithm: Yespower 1.0](https://img.shields.io/badge/Algorithm-Yespower%201.0%20(N%3D256%2C%20r%3D8)-green.svg)](WHITEPAPER.md)
[![Max Supply: 10M KSH](https://img.shields.io/badge/Max%20Supply-10%2C000%2C000%20KSH-purple.svg)](WHITEPAPER.md)
[![Block Time: 60s](https://img.shields.io/badge/Block%20Time-60s-brightgreen.svg)](WHITEPAPER.md)
[![Premine: 0%](https://img.shields.io/badge/Premine-0%25%20(Fair%20Launch)-success.svg)](WHITEPAPER.md)

> **Una Criptomoneda de Consenso Híbrido: Prueba de Trabajo CPU Pura y Masternodes Deterministas**  
> *A Hybrid Consensus Cryptocurrency: Pure CPU Proof-of-Work and Deterministic Masternodes*

---

## 📄 Documentos Oficiales / Official Documents

* 🇪🇸 **[Whitepaper en Español (Oficial)](WHITEPAPER.md)** — Documento técnico completo y especificaciones formales.
* 🇬🇧 **[Whitepaper in English (Official)](WHITEPAPER_EN.md)** — Full technical whitepaper and formal specifications.

---

## ⚡ Resumen del Proyecto / Project Overview

**Korsh ($KSH)** es una red blockchain de Capa 1 de código abierto diseñada para materializar la visión original de Satoshi Nakamoto: *"1 CPU = 1 Voto"*.

Korsh combina la minería democrática en CPU mediante el algoritmo intensivo en memoria **Yespower 1.0 ($N=256, r=8$)** (diseñado para la memoria caché L2 del procesador) con una segunda capa de **Masternodes Deterministas (DIP0003)** que provee:
* ⚡ **InstantSend:** Liquidación y bloqueo de transacciones en 2 a 3 segundos.
* 🛡️ **ChainLocks:** Inmunidad matemática contra ataques de reorganización del 51%.
* 🏛️ **Gobernanza On-Chain:** Financiamiento y votación comunitaria descentralizada.
* 💎 **Tokenomics Deflacionaria:** Suministro máximo estricto de **10,000,000 KSH** y **0% de preminado (Fair Launch)**.

---

## 📊 Especificaciones Técnicas Clave / Key Specifications

| Parámetro | Valor / Mainnet Specification |
| :--- | :--- |
| **Nombre / Name** | Korsh |
| **Ticker / Símbolo** | **$KSH** |
| **Consenso / Consensus** | Híbrido: PoW CPU + Masternodes Deterministas (DIP0003) |
| **Algoritmo de Hashing** | **Yespower 1.0 ($N=256, r=8$)** |
| **Ajuste de Dificultad** | **Dark Gravity Wave v3 (DGW-v3)** (20 bloques) |
| **Tiempo de Bloque** | **60 segundos** |
| **Recompensa Base Inicial** | **2.00 KSH** |
| **División de Recompensa** | **70% Mineros PoW** (1.40 KSH) \| **30% Masternodes** (0.60 KSH) |
| **Suministro Máximo** | **10,000,000 KSH** (Hard Cap inmutable) |
| **Intervalo de Halving** | Cada **2,500,000 bloques** (~4.75 años) |
| **Preminado (Premine)** | **0%** (Lanzamiento 100% Justo) |
| **Colateral Masternode Regular** | **1,500 KSH** |
| **Colateral Masternode Evo** | **7,500 KSH** |
| **Prefijo de Dirección** | Base58 con prefijo **"S"** (Prefix: 63) |
| **Puertos de Red** | P2P: `8383` \| RPC: `8382` |
| **Bloque Génesis Hash** | `000017ec1f2f978429db70495ec7653aedca360e5f251bfe2a780ae5e731d7eb` |
| **Mensaje Génesis** | *"In honor of my uncle Satoshi Nakamoto"* |

---

## 🏗️ Arquitectura de Red / Network Architecture

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

## 🌐 Enlaces Oficiales del Ecosistema / Official Links

* **Código Fuente Principal:** [Korsh-Code-Mainnet](https://github.com/Korsh-Dev/Korsh-Code-Mainnet)
* **Billetera Web Ligera:** [wallet.korsh.org](https://wallet.korsh.org)
* **Explorador de Bloques:** [explorer.korsh.org](https://explorer.korsh.org)
* **Mining Pool Oficial:** [pool.korsh.org](https://pool.korsh.org)

---

## 📜 Licencia / License

Este repositorio y toda la documentación técnica de Korsh están distribuidos bajo la licencia [MIT](LICENSE).
