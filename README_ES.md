<p align="center">
  <img src="assets/korsh-coins.png" alt="Korsh ($KSH) Logo" width="220" />
</p>

# KORSH ($KSH) — Whitepaper Técnico Oficial

<p align="center">
  <b>🌐 Idioma / Language:</b> <a href="README.md">🇬🇧 English</a> &nbsp;|&nbsp; <b>🇪🇸 Español (Actual)</b>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/Licencia-MIT-blue.svg" alt="Licencia: MIT" /></a>
  <a href="WHITEPAPER_ES.md"><img src="https://img.shields.io/badge/Consenso-PoW%20%2B%20DMN-orange.svg" alt="Consenso" /></a>
  <a href="WHITEPAPER_ES.md"><img src="https://img.shields.io/badge/Algoritmo-Yespower%201.0%20(N%3D256%2C%20r%3D8)-green.svg" alt="Algoritmo" /></a>
  <a href="WHITEPAPER_ES.md"><img src="https://img.shields.io/badge/Suministro-10%2C000%2C000%20KSH-purple.svg" alt="Suministro Máximo" /></a>
  <a href="WHITEPAPER_ES.md"><img src="https://img.shields.io/badge/Tiempo%20Bloque-60s-brightgreen.svg" alt="Tiempo de Bloque" /></a>
  <a href="WHITEPAPER_ES.md"><img src="https://img.shields.io/badge/Premine-0%25%20(Fair%20Launch)-success.svg" alt="0% Preminado" /></a>
</p>

> **Una Criptomoneda de Consenso Híbrido: Prueba de Trabajo CPU Pura y Masternodes Deterministas**  
> *A Hybrid Consensus Cryptocurrency: Pure CPU Proof-of-Work and Deterministic Masternodes*

---

## 📄 Documentos del Whitepaper / Official Documents

Selecciona tu idioma preferido:

| Documento | Idioma | Descripción | Enlace |
| :--- | :---: | :--- | :---: |
| **Whitepaper en Inglés** | 🇬🇧 English | Documentación técnica completa en inglés, modelos y arquitectura | **[Leer WHITEPAPER.md](WHITEPAPER.md)** |
| **Whitepaper en Español** | 🇪🇸 Español | Documento técnico completo y formal en español | **[Leer WHITEPAPER_ES.md](WHITEPAPER_ES.md)** |

---

## ⚡ Resumen del Proyecto

**Korsh ($KSH)** es una red blockchain de Capa 1 de código abierto diseñada para materializar la visión original concebida por Satoshi Nakamoto: *"1 CPU = 1 Voto"*.

Korsh combina la minería democrática en CPU mediante el algoritmo intensivo en memoria **Yespower 1.0 ($N=256, r=8$)** (diseñado para la memoria caché L2 del procesador) con una segunda capa de **Masternodes Deterministas (DIP0003)** que provee:
* ⚡ **InstantSend:** Liquidación y bloqueo irrevocable de transacciones en **2 a 3 segundos**.
* 🛡️ **ChainLocks:** Inmunidad matemática contra ataques de reorganización del 51%.
* 🏛️ **Gobernanza On-Chain:** Financiamiento y votación comunitaria descentralizada vía superbloques.
* 💎 **Tokenomics Deflacionaria:** Suministro máximo estricto de **10,000,000 KSH** y **0% de preminado (Fair Launch)**.

---

## 📊 Especificaciones Técnicas Clave

| Parámetro | Valor / Especificación en Mainnet |
| :--- | :--- |
| **Nombre de la Moneda** | Korsh |
| **Símbolo / Ticker** | **$KSH** |
| **Mecanismo de Consenso** | Híbrido: PoW CPU Puro + Masternodes Deterministas (DMN) |
| **Algoritmo de Hashing** | **Yespower 1.0 ($N=256, r=8$)** |
| **Ajuste de Dificultad** | **Dark Gravity Wave v3 (DGW-v3)** (Ventana móvil de 20 bloques) |
| **Tiempo Objetivo por Bloque** | **60 segundos** (1 minuto) |
| **Recompensa Base Inicial** | **2.00 KSH** |
| **Distribución de Recompensa** | **70% Mineros PoW** (1.40 KSH) \| **30% Masternodes** (0.60 KSH) |
| **Suministro Máximo Inmutable** | **10,000,000 KSH** |
| **Intervalo de Halving** | Cada **2,500,000 bloques** (~4.75 años) |
| **Preminado (Premine)** | **0%** (Lanzamiento 100% Justo) |
| **Colateral Masternode Regular** | **1,500 KSH** (Peso de voto: 1) |
| **Colateral Masternode Evo** | **7,500 KSH** (Peso de voto: 5) |
| **Formato de Direcciones** | Base58 con prefijo **"S"** (Prefix Byte: 63 / `0x3F`) |
| **Puertos de Red** | P2P: `8383` \| RPC: `8382` |
| **Hash del Bloque Génesis** | `000017ec1f2f978429db70495ec7653aedca360e5f251bfe2a780ae5e731d7eb` |
| **Merkle Root del Génesis** | `1dd60dd52dda0fd4b6912baca209aa327ae8b4825a23415b0a4356585897d073` |
| **Mensaje del Bloque Génesis** | *"In honor of my uncle Satoshi Nakamoto"* |

---

## 🏗️ Topología de Red en Dos Capas

```
┌────────────────────────────────────────────────────────────────────────┐
│                        TOPOLOGÍA HÍBRIDA DE KORSH                      │
├────────────────────────────────────┬───────────────────────────────────┤
│    Capa 1: Mineros CPU Yespower    │  Capa 2: Masternodes Deterministas│
├────────────────────────────────────┼───────────────────────────────────┤
│ • Minería CPU pura (Yespower 1.0)  │ • Listas deterministas (DIP0003)  │
│ • Optimizado para caché L2 ~256 KB │ • Quórums LLMQ + Firmas BLS       │
│ • Dificultad Dark Gravity Wave v3  │ • InstantSend (liquidación 2-3s)  │
│ • Bloques cada 60 segundos         │ • ChainLocks (defensa ante el 51%)│
│ • Recibe el 70% del subsidio       │ • Recibe el 30% del subsidio      │
└────────────────────────────────────┴───────────────────────────────────┘
```

---

## 🌐 Enlaces Oficiales del Ecosistema

* **Código Fuente Principal:** [github.com/Korsh-Dev/Korsh-Code-Mainnet](https://github.com/Korsh-Dev/Korsh-Code-Mainnet)
* **Billetera Web Ligera:** [wallet.korsh.org](https://wallet.korsh.org)
* **Explorador de Bloques:** [explorer.korsh.org](https://explorer.korsh.org)
* **Mining Pool Oficial:** [pool.korsh.org](https://pool.korsh.org)

---

## 📜 Licencia

Este repositorio y toda la documentación técnica de Korsh están distribuidos bajo la licencia [MIT](LICENSE).
