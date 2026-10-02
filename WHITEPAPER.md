# KORSH ($KSH) CORE WHITEPAPER

**Una Criptomoneda de Consenso Híbrido: Prueba de Trabajo CPU Pura y Masternodes Deterministas**

*Versión:* 1.0 — *Red Principal (Mainnet):* Activa  
*Fecha:* Octubre 2026  
*Licencia:* Código Abierto (MIT License)  
*Repositorio Oficial de Código:* [github.com/Korsh-Dev/Korsh-Code-Mainnet](https://github.com/Korsh-Dev/Korsh-Code-Mainnet)  
*Repositorio del Whitepaper:* [github.com/Korsh-Dev/White-Paper-Korsh](https://github.com/Korsh-Dev/White-Paper-Korsh)  

---

## Índice de Contenidos

1. [Resumen Ejecutivo (Executive Summary)](#1-resumen-ejecutivo-executive-summary)
2. [Filosofía y Principios de Diseño](#2-filosofía-y-principios-de-diseño)
3. [Especificaciones Técnicas y Parámetros de Red](#3-especificaciones-técnicas-y-parámetros-de-red)
4. [Arquitectura de Consenso Híbrido: Capa 1 y Capa 2](#4-arquitectura-de-consenso-híbrido-capa-1-y-capa-2)
   - 4.1 [Capa 1: Minería CPU con Yespower 1.0 (N=256, r=8)](#41-capa-1-minería-cpu-con-yespower-10-n256-r8)
   - 4.2 [Retargeting Dinámico: Dark Gravity Wave v3 (DGW-v3)](#42-retargeting-dinámico-dark-gravity-wave-v3-dgw-v3)
   - 4.3 [Capa 2: Masternodes Deterministas (DIP0003)](#43-capa-2-masternodes-deterministas-dip0003)
   - 4.4 [Quórums LLMQ y Criptografía de Umbral BLS](#44-quórums-llmq-y-criptografía-de-umbral-bls)
   - 4.5 [InstantSend: Liquidación Instantánea y Protección Doble Gasto](#45-instantsend-liquidación-instantánea-y-protección-doble-gasto)
   - 4.6 [ChainLocks: Inmunidad Criptográfica ante Ataques de Reorganización del 51%](#46-chainlocks-inmunidad-criptográfica-ante-ataques-de-reorganización-del-51)
   - 4.7 [Gobernanza Descentralizada y Propuestas On-Chain](#47-gobernanza-descentralizada-y-propuestas-on-chain)
5. [Tokenomics y Emisión Monetaria](#5-tokenomics-y-emisión-monetaria)
   - 5.1 [Principios Económicos Fundamentales](#51-principios-económicos-fundamentales)
   - 5.2 [Formulación Matemática de la Emisión](#52-formulación-matemática-de-la-emisión)
   - 5.3 [Calendario de Emisión Multiera](#53-calendario-de-emisión-multiera)
   - 5.4 [Dinámica de Colateral y Shock de Oferta de Masternodes](#54-dinámica-de-colateral-y-shock-de-oferta-de-masternodes)
6. [Ecosistema de Software e Infraestructura](#6-ecosistema-de-software-e-infraestructura)
   - 6.1 [Korsh Core Daemon y Billetera Qt GUI](#61-korsh-core-daemon-y-billetera-qt-gui)
   - 6.2 [Software de Minería Optimizado (AVX2 / AVX-512)](#62-software-de-minería-optimizado-avx2--avx-512)
   - 6.3 [Billetera Ligera Web (Web Wallet)](#63-billetera-ligera-web-web-wallet)
   - 6.4 [Explorador Público de la Blockchain](#64-explorador-público-de-la-blockchain)
   - 6.5 [Infraestructura de Minería en Piscina (Mining Pool Stratum)](#65-infraestructura-de-minería-en-piscina-mining-pool-stratum)
   - 6.6 [Aplicación Móvil de Minería y Monitoreo](#66-aplicación-móvil-de-minería-y-monitoreo)
7. [Análisis de Seguridad y Resistencia de Red](#7-análisis-de-seguridad-y-resistencia-de-red)
   - 7.1 [Inviabilidad Económica de Alquiler de Hashrate](#71-inviabilidad-económica-de-alquiler-de-hashrate)
   - 7.2 [Resistencia a Ataques Sybil en la Red de Masternodes](#72-resistencia-a-ataques-sybil-en-la-red-de-masternodes)
   - 7.3 [Punto de Control Determinista (Checkpoints)](#73-punto-de-control-determinista-checkpoints)
8. [Hoja de Ruta (Roadmap)](#8-hoja-de-ruta-roadmap)
9. [Conclusión](#9-conclusión)
10. [Aviso Legal (Disclaimer)](#10-aviso-legal-disclaimer)

---

## 1. Resumen Ejecutivo (Executive Summary)

**Korsh ($KSH)** es una red blockchain descentralizada de Capa 1 de código abierto diseñada para materializar y proteger la visión original concebida por Satoshi Nakamoto: *"1 CPU = 1 Voto"*.

A medida que la industria de las criptomonedas maduró, los esquemas de consenso basados exclusivamente en Prueba de Trabajo (PoW) tradicional sufrieron un proceso acelerado de centralización. La minería derivó hacia granjas industriales operadas por clústeres masivos de circuitos integrados de aplicación específica (ASIC), granjas de GPU corporativas y matrices de compuertas lógicas programables en campo (FPGA). Este fenómeno expulsó gradualmente al usuario común, erigió barreras de capital inaccesibles y concentró la seguridad del libro mayor en monopolios geográficos y fabricantes exclusivos de silicio.

Korsh resuelve esta problemática de raíz mediante un modelo arquitectónico de dos capas complementarias:

1. **Lanzamiento Justo (Fair Launch) y 0% Premine:** Sin asignaciones ocultas, sin ventas privadas, sin ICO, sin asignaciones previas a desarrolladores ni inversores de capital de riesgo. Cada moneda en circulación se origina de manera transparente mediante trabajo computacional o recompensas de servicio de red.
2. **Algoritmo Yespower 1.0 ($N=256, r=8$):** Un esquema de hashing estrictamente intensivo en memoria (*memory-hard*), diseñado para residir por completo en la memoria caché L2 de los procesadores convencionales de 64 bits. Esta configuración anula cualquier ventaja comercial o de rendimiento para arquitecturas ASIC y GPU, manteniendo una eficiencia energética sobresaliente.
3. **Capa Secundaria de Masternodes Deterministas (DIP0003):** Una capa de infraestructura incentivada basada en listas deterministas de nodos en cadena (*on-chain*), protegida mediante quórums LLMQ (*Long-Living Masternode Quorums*) y firmas agregadas BLS. Provee finalización instantánea de transacciones (*InstantSend* en 2 a 3 segundos), resistencia criptográfica matemática contra ataques de reorganización profunda del 51% (*ChainLocks*) y un sistema nativo de gobernanza descentralizada.
4. **Política Monetaria Estricta y Deflacionaria:** Un límite de suministro absoluto e inmutable de **10,000,000 KSH** regido por un mecanismo de reducción a la mitad (*halving*) cada 2,500,000 bloques (~4.75 años), replicando la solidez de la escasez matemática del patrón oro digital.

---

## 2. Filosofía y Principios de Diseño

El diseño de Korsh parte de cuatro postulados innegociables:

* **Accesibilidad Universal y Soberanía Individual:** La validación y emisión monetaria no deben exigir inversiones multimillonarias en hardware industrial. Cualquier usuario dotado de una computadora personal, computadora portátil o servidor estándar con procesador de 64 bits puede participar activamente en la seguridad del consenso y recibir recompensas proporcionales a su capacidad de procesamiento.
* **Resistencia Robusta a la Centralización:** La arquitectura de hashing impone una restricción física: al requerir baja latencia de memoria con una huella de ~256 KB por hilo, optimizada para la memoria caché L2 del CPU, neutraliza la eficiencia económica del diseño de silicio dedicado (ASIC) y la paralelización masiva de las GPUs.
* **Velocidad y Utilidad en el Mundo Real:** Un intervalo de bloque de 60 segundos proporciona un flujo continuo de confirmaciones, mientras que el bloqueo instantáneo de transacciones mediante quórums de Masternodes permite transacciones comerciales con liquidación segura en 2 a 3 segundos, protegiendo a los receptores contra riesgos de doble gasto sin requerir demoras prolongadas de confirmación.
* **Transparencia Radical:** El Bloque Génesis fue emitido y auditado públicamente bajo parámetros criptográficos verificables, con el mensaje conmemorativo *"In honor of my uncle Satoshi Nakamoto"*, consolidando un compromiso inquebrantable con la ética de los orígenes de la descentralización.

---

## 3. Especificaciones Técnicas y Parámetros de Red

La siguiente tabla resume los parámetros criptográficos y operacionales que rigen la red principal de Korsh:

| Parámetro | Valor / Especificación en Mainnet |
| :--- | :--- |
| **Nombre de la Moneda** | Korsh |
| **Símbolo / Ticker** | **$KSH** |
| **Mecanismo de Consenso** | Consenso Híbrido: Prueba de Trabajo (PoW) + Masternodes Deterministas |
| **Algoritmo de Hashing PoW** | **Yespower 1.0 ($N=256, r=8$)** |
| **Ajuste de Dificultad** | **Dark Gravity Wave v3 (DGW-v3)** (Ventana móvil de 20 bloques) |
| **Tiempo Objetivo por Bloque** | **60 segundos** (1 minuto) |
| **Recompensa Base Inicial por Bloque** | **2.00 KSH** |
| **Distribución de Recompensa de Bloque** | **70% Mineros PoW** (1.40 KSH) \| **30% Masternodes** (0.60 KSH) |
| **Suministro Máximo Inmutable (Hard Cap)**| **10,000,000 KSH** |
| **Intervalo de Reducción (Halving)** | Cada **2,500,000 bloques** (~4.75 años a 60 seg/bloque) |
| **Preminado (Premine)** | **0 KSH (0.00%) — Fair Launch** |
| **Colateral Masternode Regular** | **1,500 KSH** (Peso de voto: 1) |
| **Colateral Masternode Evo (Reservado)** | **7,500 KSH** (Peso de voto: 5) |
| **Formato de Direcciones Públicas** | Base58 con prefijo **"S"** (Prefix Byte: `63` decimal / `0x3F`) |
| **Magic Bytes de Red P2P** | `0xCB 0x4B 0x53 0x48` (`\xcbKSH`) |
| **Puerto P2P por Defecto** | **8383** |
| **Puerto RPC por Defecto** | **8382** |
| **Hash del Bloque Génesis** | `000017ec1f2f978429db70495ec7653aedca360e5f251bfe2a780ae5e731d7eb` |
| **Merkle Root del Bloque Génesis** | `1dd60dd52dda0fd4b6912baca209aa327ae8b4825a23415b0a4356585897d073` |
| **Mensaje del Bloque Génesis** | *"In honor of my uncle Satoshi Nakamoto"* |

---

## 4. Arquitectura de Consenso Híbrido: Capa 1 y Capa 2

Korsh articula un modelo de seguridad cooperativo en dos niveles jerárquicos independientes pero estrechamente integrados:

```
┌────────────────────────────────────────────────────────────────────────┐
│                      TOPOLOGÍA DE RED KORSH ($KSH)                     │
└────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                   CAPA 1: MINERÍA CPU DE PRUEBA DE TRABAJO             │
│  • Algoritmo: Yespower 1.0 (N=256, r=8)                                │
│  • Huella de memoria ~256 KB ajustada a la caché L2 del procesador     │
│  • Retargeting dinámico bloque a bloque: Dark Gravity Wave v3          │
│  • Ordenamiento y ensamblaje de transacciones brutas                   │
│  • Generación de bloques cada 60 segundos                              │
│  • Percepción de incentivo: 70% del subsidio de bloque (1.40 KSH)      │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ Propagación del Bloque Candidato
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│               CAPA 2: MASTERNODES DETERMINISTAS (DIP0003)              │
│  • Nodos de alta disponibilidad con colateral de 1,500 KSH             │
│  • Quórums LLMQ con firmas agregadas BLS (Criptografía de umbral)      │
│  • InstantSend: Bloqueo irrevocable de transacciones en 2 a 3 segundos │
│  • ChainLocks: Firma de bloque que previene reorganizaciones del 51%   │
│  • Gobernanza descentralizada y superbloques de desarrollo comunitario │
│  • Percepción de incentivo: 30% del subsidio de bloque (0.60 KSH)      │
└────────────────────────────────────────────────────────────────────────┘
```

### 4.1 Capa 1: Minería CPU con Yespower 1.0 ($N=256, r=8$)

El algoritmo de prueba de trabajo adoptado por Korsh es una parametrización optimizada de la familia **Yespower**, reconocida en la criptografía aplicada por su resistencia a los circuitos ASIC y a las GPU mediante el uso intensivo de la memoria (*memory-hard hashing*).

La huella de memoria requerida por cada hilo de ejecución de Yespower se define según la fórmula:

$$\text{Memoria por Hilo} = (128 \times N \times r) \text{ bytes} + \text{S-Boxes}$$

Al establecer $N = 256$ y $r = 8$:

$$\text{Memoria de Trabajo} = (128 \times 256 \times 8) \text{ bytes} = 262,144 \text{ bytes} \approx 256 \text{ KB}$$

Sumando las tablas de sustitución (S-Boxes) y búferes locales, cada hilo de minería demanda entre 256 KB y 356 KB de memoria de ultra-baja latencia.

#### Ventajas Comparativas del Parámetro ($N=256, r=8$):

1. **Alineación con la Memoria Caché L2:** Los procesadores modernos (arquitecturas x86_64 AMD Zen, Intel Core y procesadores ARMv8/v9 contemporáneos) cuentan habitualmente con entre 512 KB y 1024 KB de memoria caché de nivel 2 (L2) dedicada por cada núcleo físico. Dado que el espacio de trabajo de 256 KB reside con holgura dentro de la caché L2, el cómputo se ejecuta a la máxima velocidad de reloj interna del procesador, sin penalizaciones por latencia externa de memoria DRAM ni contención de caché L3.
2. **Neutralización de Unidades GPU:** Las arquitecturas de procesamiento gráfico basan su rendimiento en el paralelismo masivo de miles de hilos ligeros (*Streaming Multiprocessors*), pero cuentan con cantidades insignificantes de memoria caché local por hilo (apenas 16 a 64 KB). Al exigir 256 KB por hilo, las GPU se ven forzadas a realizar lecturas continuas a través de los buses hacia la memoria VRAM global. La latencia de este acceso degrada el rendimiento de tal manera que la minería en GPU se vuelve inviable económicamente frente a un CPU de escritorio.
3. **Inviabilidad Económica de Mineros ASIC y FPGA:** La fabricación de chips ASIC o la programación de FPGA con megabytes de memoria SRAM estática de alta velocidad por cada tubería de cálculo eleva los costos de diseño, silicio y disipación térmica a niveles prohibitivos. La curva de rendimiento por dólar y rendimiento por vatio de los procesadores comerciales de consumo masivo supera permanentemente a cualquier intento de construcción de hardware propietario.

### 4.2 Retargeting Dinámico: Dark Gravity Wave v3 (DGW-v3)

Para mitigar los ataques de salto de potencia de cálculo (*hashrate hopping*) y absorber fluctuaciones repentinas de mineros que ingresan o abandonan la red, Korsh implementa el algoritmo de ajuste de dificultad **Dark Gravity Wave v3 (DGW-v3)**.

* **Ajuste Bloque a Bloque:** A diferencia de Bitcoin, cuya dificultad se recalibra cada 2016 bloques (~2 semanas), Korsh recalcula la dificultad matemática requerida con cada nuevo bloque minado.
* **Promedio Armónico Ponderado de 20 Bloques:** DGW-v3 evalúa los intervalos de tiempo y la dificultad de los últimos 20 bloques mediante una ponderación no lineal que asigna mayor peso estadístico a los bloques más recientes.
* **Límites de Oscilación Estricta:** El algoritmo restringe los saltos de dificultad dentro de factores controlados para prevenir la manipulación de marcas temporales (*time-warp attacks*).

### 4.3 Capa 2: Masternodes Deterministas (DIP0003)

La segunda capa de Korsh abandona el obsoleto modelo de masternodes basados en mensajes P2P no deterministas (*legacy masternodes*) e implementa la especificación **DIP0003 (Deterministic Masternode Lists)**.

En este paradigma, el conjunto de Masternodes válidos se calcula y valida de forma determinista directamente dentro del consenso de la blockchain mediante transacciones especiales del mempool:

* **Transacción de Registro de Proveedor (ProRegTx):** El operador congela un UTXO con la cantidad exacta de colateral requerida (**1,500 KSH** para un Masternode Regular o **7,500 KSH** para un Masternode Evo) y publica las claves criptográficas diferenciadas en la cadena.
* **Separación de Llaves Criptográficas:**
  * **Owner Key (Clave de Propietario):** Utilizada exclusivamente para actualizar parámetros administrativos del nodo o delegar el colateral. Nunca se expone en el servidor que ejecuta el nodo.
  * **Operator Key (Clave de Operador - BLS):** Clave pública de firma BLS utilizada por el servidor remoto para firmar mensajes de consenso de red, quórums y bloques.
  * **Voting Key (Clave de Votación):** Utilizada para emitir votos en el sistema de gobernanza descentralizada.
  * **Payout Address (Dirección de Pago):** Dirección estándar de la billetera fría donde se deposita de manera directa y automática el 30% de las recompensas del bloque (0.60 KSH), protegiendo los fondos contra cualquier vulnerabilidad del servidor en la nube.

```
┌────────────────────────────────────────────────────────────────────────┐
│            ESQUEMA DE CLAVES DIP0003 EN KORSH CORE                     │
├───────────────────┬────────────────────────────────────────────────────┤
│ Clave             │ Responsabilidad y Aislamiento de Seguridad         │
├───────────────────┼────────────────────────────────────────────────────┤
│ Owner Key         │ Control del colateral; en almacenamiento frío.     │
│ Operator Key      │ Firma BLS en el servidor VPS activo de Capa 2.     │
│ Voting Key        │ Sufragio en propuestas de gobernanza comunitaria.  │
│ Payout Script     │ Destino de cobro del 30% de la recompensa.         │
└───────────────────┴────────────────────────────────────────────────────┘
```

### 4.4 Quórums LLMQ y Criptografía de Umbral BLS

Los Masternodes se agrupan periódicamente en **Quórums de Masternodes de Larga Duración (LLMQ - Long-Living Masternode Quorums)** formados de manera pseudoaleatoria y determinista mediante el protocolo de Generación de Claves Distribuidas (DKG - *Distributed Key Generation*).

Los miembros del quórum emplean el esquema de firmas agregadas **Boneh-Lynn-Shacham (BLS)** sobre la curva elíptica BLS12-381. Cuando un subconjunto umbral del quórum valida un mensaje o bloque, sus firmas parciales se combinan en una única firma de umbral compacta, verificable por cualquier nodo de la red con mínimo costo computacional y sin sobrecargar el ancho de banda del protocolo P2P.

### 4.5 InstantSend: Liquidación Instantánea y Protección Doble Gasto

La tecnología **InstantSend** aprovecha los quórums LLMQ para otorgar finalidad casi instantánea a las transacciones ordinarias en la red Korsh:

1. El emisor transmite una transacción de transferencia.
2. Los quórums LLMQ verifican que las entradas (UTXOs) no hayan sido gastadas previamente y emiten un bloqueo determinista (*InstantSend Lock - ISLOCK*).
3. Una vez generado el ISLOCK (en un lapso habitual de **2 a 3 segundos**), los nodos completos y billeteras marcan la transacción como definitiva e irreversible.
4. Cualquier intento concurrente de transmitir un conflicto de doble gasto es rechazado de inmediato por todos los nodos, permitiendo a comerciantes, cajeros y pasarelas de pago entregar bienes o servicios sin aguardar múltiples confirmaciones de minería.

### 4.6 ChainLocks: Inmunidad Criptográfica ante Ataques de Reorganización del 51%

Uno de los mayores peligros para cadenas PoW de mediana capitalización es el riesgo de ataques de reorganización profunda del 51%, donde un minero malicioso acumula poder de cómputo privado para revertir bloques anteriores. Korsh neutraliza esta amenaza mediante **ChainLocks**:

1. Tan pronto como un minero de Capa 1 encuentra un bloque válido y lo propaga a la red, el quórum LLMQ activo evalúa el bloque recibido.
2. Si el bloque cumple las reglas de consenso, cada miembro del quórum firma un mensaje `CLSIG` (ChainLock Signature).
3. Al alcanzarse el umbral de firmas, se difunde la firma combinada del ChainLock.
4. **Regla de Inmutabilidad:** A partir del instante en que un bloque es sellado con un ChainLock, todos los nodos de la red Korsh rechazan deterministamente cualquier bloque alternativo con la misma o menor altura, independientemente de cuánta dificultad o trabajo acumulado pretenda presentar una cadena competidora.
5. De este modo, la probabilidad de reorganización se reduce a cero, brindando la seguridad de liquidación de una red multimillonaria desde sus fases tempranas.

### 4.7 Gobernanza Descentralizada y Propuestas On-Chain

La red Korsh integra un sistema de tesorería y gobernanza en cadena gestionado directamente por los operadores de Masternodes. Los miembros de la comunidad pueden formular propuestas presupuestarias para financiar el desarrollo de software, auditorías de seguridad, campañas de difusión o mejoras de infraestructura.

Mediante su clave de votación (`Voting Key`), cada Masternode activo emite un voto (*Sí*, *No* o *Abstención*). Las propuestas que alcancen un respaldo neto positivo superior al umbral establecido son liquidadas automáticamente por el protocolo mediante **superbloques** programados, garantizando la sostenibilidad financiera del proyecto a perpetuidad sin intermediarios ni tesorerías centralizadas.

---

## 5. Tokenomics y Emisión Monetaria

### 5.1 Principios Económicos Fundamentales

1. **Escasez Matemática Absoluta:** El suministro total está fijado en un máximo inmutable de **10,000,000 KSH**. Ninguna función ni actualización futura del protocolo puede violar este límite.
2. **0% Premine y Cero Venta de Tokens:** El bloque Génesis fue lanzado sin recompensas asignadas a los desarrolladores, sin rondas semilla, sin preventas ni asignaciones para fondos de riesgo.
3. **Incentivos Equilibrados:** El subsidio por bloque premia conjuntamente el aporte energético y físico de los mineros PoW (70%) y el sostenimiento de infraestructura de alta disponibilidad provisto por los Masternodes (30%).

### 5.2 Formulación Matemática de la Emisión

La recompensa de subsidio de bloque $S(h)$ a una altura determinada $h$ está descrita por la función escalonada de reducción a la mitad:

$$S(h) = \left\lfloor \frac{S_0}{2^{\lfloor h / H \rfloor}} \right\rfloor$$

Donde:
* $S_0 = 2.00 \text{ KSH}$ (Subsidio base inicial por bloque).
* $H = 2,500,000$ (Intervalo de halving expresado en bloques).
* $\lfloor x \rfloor$ denota la función piso (redondeo hacia el entero inferior más cercano).

La asignación económica interna entre mineros y operadores de Masternodes se computa como:

$$\text{Recompensa Minero: } R_{\text{miner}}(h) = 0.70 \times S(h)$$

$$\text{Recompensa Masternode: } R_{\text{mn}}(h) = 0.30 \times S(h)$$

### 5.3 Calendario de Emisión Multiera

Dado el intervalo objetivo de 60 segundos por bloque, un ciclo de halving de 2,500,000 bloques corresponde con exactitud a:

$$T_{\text{era}} = \frac{2,500,000 \times 60 \text{ s}}{86,400 \text{ s/día} \times 365.25 \text{ días/año}} \approx 4.752 \text{ años} \ (\approx 4 \text{ años y } 9 \text{ meses})$$

A continuación se detalla la trayectoria completa de emisión por eras:

| Era | Rango de Bloques | Duración Estimada | Subsidio Total | Minero (70%) | Masternode (30%) | Emisión de la Era | Suministro Acumulado | % del Total |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Era 1** | $0 - 2,499,999$ | Años 0.00 – 4.75 | **2.00 KSH** | 1.40 KSH | 0.60 KSH | 5,000,000 KSH | **5,000,000 KSH** | 50.00% |
| **Era 2** | $2,500,000 - 4,999,999$ | Años 4.75 – 9.50 | **1.00 KSH** | 0.70 KSH | 0.30 KSH | 2,500,000 KSH | **7,500,000 KSH** | 75.00% |
| **Era 3** | $5,000,000 - 7,499,999$ | Años 9.50 – 14.25 | **0.50 KSH** | 0.35 KSH | 0.15 KSH | 1,250,000 KSH | **8,750,000 KSH** | 87.50% |
| **Era 4** | $7,500,000 - 9,999,999$ | Años 14.25 – 19.00 | **0.25 KSH** | 0.175 KSH | 0.075 KSH | 625,000 KSH | **9,375,000 KSH** | 93.75% |
| **Era 5** | $10,000,000 - 12,499,999$ | Años 19.00 – 23.75 | **0.125 KSH** | 0.0875 KSH | 0.0375 KSH | 312,500 KSH | **9,687,500 KSH** | 96.88% |
| **Era 6** | $12,500,000 - 14,999,999$ | Años 23.75 – 28.50 | **0.0625 KSH** | 0.04375 KSH | 0.01875 KSH | 156,250 KSH | **9,843,750 KSH** | 98.44% |
| **Cola** | $\ge 15,000,000$ | Años 28.50+ | $\to 0$ | $\to 0$ | $\to 0$ | Remanente | **10,000,000 KSH** | **100.00%** |

Al alcanzar la cota superior del suministro máximo, la recompensa de bloque por emisión cesa de forma determinista y los validadores de la red (tanto mineros como Masternodes) pasarán a ser remunerados exclusivamente mediante las tarifas y comisiones de transacción generadas en el bloque.

### 5.4 Dinámica de Colateral y Shock de Oferta de Masternodes

El requerimiento de inmovilización de **1,500 KSH** por cada Masternode Regular actúa como un poderoso estabilizador macroeconómico de la oferta circulante.

Con una producción regular de 1 bloque por minuto (1,440 bloques diarios), el fondo de recompensas anual distribuido a los Masternodes durante la Era 1 es de:

$$\text{Fondo Anual de Masternodes} = 1,440 \text{ bloques/día} \times 365.25 \text{ días} \times 0.60 \text{ KSH} = \mathbf{315,576 \text{ KSH / año}}$$

El rendimiento porcentual anual estimado (**ROI**) para un operador de Masternode individual se calcula como:

$$\text{ROI Anual Estimado} = \left( \frac{\text{Fondo Anual de Masternodes}}{M_{\text{activos}} \times C} \right) \times 100\%$$

Donde $M_{\text{activos}}$ es la cantidad de Masternodes activos en la red y $C = 1,500 \text{ KSH}$ es el colateral requerido.

#### Análisis de Sensibilidad y Absorción de Oferta:

| Masternodes Activos | KSH Bloqueados en Colateral | % de Oferta Bloqueada (sobre 5M KSH) | KSH Anuales por Masternode | **ROI Anual Estimado** |
| :---: | :---: | :---: | :---: | :---: |
| **50** | 75,000 KSH | 1.50% | 6,311.5 KSH | **420.8%** |
| **100** | 150,000 KSH | 3.00% | 3,155.8 KSH | **210.4%** |
| **250** | 375,000 KSH | 7.50% | 1,262.3 KSH | **84.1%** |
| **500** | 750,000 KSH | 15.00% | 631.2 KSH | **42.1%** |
| **1,000** | 1,500,000 KSH | 30.00% | 315.6 KSH | **21.0%** |
| **1,500** | 2,250,000 KSH | 45.00% | 210.4 KSH | **14.0%** |
| **2,000** | 3,000,000 KSH | 60.00% | 157.8 KSH | **10.5%** |

Este modelo genera un efecto autorregulador denominado **Mecanismo de Absorción de Oferta**:
* A menor cantidad de Masternodes en funcionamiento, el rendimiento anual por nodo escala dramáticamente, atrayendo de inmediato nuevos operadores dispuestos a adquirir KSH en el mercado secundario para poner en marcha sus nodos.
* A mayor cantidad de Masternodes en línea, una fracción masiva de la masa monetaria líquida (entre el 15% y el 45%+) queda bloqueada y retirada de la venta, generando un shock de oferta positivo que protege el valor fundamental del token.

---

## 6. Ecosistema de Software e Infraestructura

El proyecto Korsh dispone de un conjunto integral de aplicaciones nativas y herramientas de infraestructura listas para producción:

```
┌────────────────────────────────────────────────────────────────────────┐
│                   SUITE DE SOFTWARE DE LA RED KORSH                    │
├────────────────────────────────────────────────────────────────────────┤
│  [korshd]           Nodo completo y demonio de consenso de servidor    │
│  [korsh-qt]         Billetera con GUI nativa y asistente de Masternode │
│  [korsh-miner]      Minero CPU C/C++ optimizado para AVX2 y AVX-512    │
│  [wallet.korsh.org] Billetera web ligera sin descarga de blockchain    │
│  [explorer.korsh.org] Explorador público en tiempo real                │
│  [pool.korsh.org]   Servidor de minería en piscina compatible Stratum  │
│  [Mobile App]       App móvil para monitoreo y gestión de red          │
└────────────────────────────────────────────────────────────────────────┘
```

### 6.1 Korsh Core Daemon y Billetera Qt GUI
El software base de la red comprende el demonio sin interfaz (`korshd`), la herramienta de línea de comandos (`korsh-cli`) y el cliente de escritorio con interfaz gráfica (`korsh-qt`):
* **Asistente Integrado de Masternodes (MN Setup Wizard):** Interfaz gráfica intuitiva que guía al usuario en la generación de claves, preparación del colateral y despliegue del nodo determinista sin requerir manipulación avanzada de comandos.
* **Billetera Unificada y Tema Oscuro:** Diseño visual ergonómico con visualización en tiempo real del saldo, transacciones bloqueadas por InstantSend y estado de sincronización de la cadena.
* **Seguridad Criptográfica:** Cifrado completo del almacén de claves local y soporte para respaldo determinista.

### 6.2 Software de Minería Optimizado (AVX2 / AVX-512)
Para maximizar el aprovechamiento de la memoria caché y las unidades aritmético-lógicas de los procesadores actuales, el equipo de Korsh distribuye un software de minería de CPU independiente y altamente optimizado:
* Escrito en C/C++ de bajo nivel con rutinas vectoriales intrínsecas para **AVX2**, **AVX-512**, **SHA-NI** y extensiones **NEON** en procesadores ARM64.
* Control dinámico de afinidad de núcleos para evitar sobrecalentamiento y maximizar el rendimiento por ciclo de reloj (*hash/watt*).
* Compatibilidad nativa con el protocolo Stratum para conexiones a piscinas públicas y privadas.

### 6.3 Billetera Ligera Web (Web Wallet)
Disponible en `wallet.korsh.org`:
* Permite a usuarios sin capacidad de almacenamiento local gestionar fondos, enviar pagos instantáneos con InstantSend y monitorear balances.
* Criptografía client-side: las claves privadas se generan y cifran localmente en el navegador del usuario y nunca abandonan su dispositivo.

### 6.4 Explorador Público de la Blockchain
Accesible a través de `explorer.korsh.org`:
* Herramienta pública e independiente para la auditoría de bloques, transacciones, direcciones, dificultad DGW-v3, altura de red y hashrate global.
* Monitor de quórums LLMQ, Masternodes activos y firmas de ChainLocks en tiempo real.

### 6.5 Infraestructura de Minería en Piscina (Mining Pool Stratum)
Operando en `pool.korsh.org`:
* Infraestructura de minería colaborativa con arquitectura de baja latencia, soporte de pagos automáticos y panel estadístico en vivo.
* Opciones de minería grupal (PPLNS) y minería en solitario (Solo Mining) a través del protocolo Stratum estándar.

### 6.6 Aplicación Móvil de Minería y Monitoreo
Una solución móvil orientada a democratizar la interacción con la red, facilitando la consulta del estado de los Masternodes propios, el monitoreo del hashrate de la red y la gestión segura de transacciones.

---

## 7. Análisis de Seguridad y Resistencia de Red

### 7.1 Inviabilidad Económica de Alquiler de Hashrate
En redes que emplean algoritmos estándar dependientes de memoria DRAM o SHA-256/Scrypt, atacantes externos pueden alquilar rápidamente hashrate masivo en plataformas de computación en la nube (e.g. NiceHash) para ejecutar un ataque sorpresivo. 

Bajo **Yespower 1.0 ($N=256, r=8$)**, el factor limitante es la memoria caché L2 del procesador. Las granjas de servidores en la nube virtualizadas sufren una severa penalización de rendimiento cuando múltiples hilos virtuales compiten por recursos de caché compartidos. No existe un mercado global de alquiler de hashrate Yespower consolidado que permita adquirir el 51% de la red de forma económica.

### 7.2 Resistencia a Ataques Sybil en la Red de Masternodes
Para alcanzar una influencia maliciosa en los quórums LLMQ de Capa 2, un atacante requeriría controlar más del 40-50% de los Masternodes activos. 

Considerando una red base de tan solo 500 Masternodes, el atacante necesitaría acaparar más de 375,000 KSH en colaterales. Debido a que el suministro total es de únicamente 10,000,000 KSH y la liquidez circulante en los primeros años es limitada, la compra masiva de monedas en los libros de órdenes causaría un deslizamiento de precio exponencial (*slippage*). El atacante sufriría un costo económico devastador, destruyendo el valor de su propia inversión en caso de pretender vulnerar la red.

### 7.3 Punto de Control Determinista (Checkpoints)
El cliente Korsh Core incorpora puntos de control criptográficos (*checkpoints*) periódicos en cada versión de lanzamiento oficial, impidiendo que cadenas bifurcadas con antigüedades profundas puedan ser reconocidas como válidas por nodos recién conectados.

---

## 8. Hoja de Ruta (Roadmap)

```
┌────────────────────────────────────────────────────────────────────────┐
│                        HOJA DE RUTA DE KORSH ($KSH)                    │
└────────────────────────────────────────────────────────────────────────┘

 [Fase 1: Génesis y Consenso Base] ─────────────► (COMPLETADO)
  • Lanzamiento de la Mainnet con 0% de preminado y Fair Launch.
  • Activación del algoritmo Yespower 1.0 (N=256, r=8).
  • Emisión verificada del Bloque Génesis con mensaje tributo.
  • Publicación de binarios completos multiplataforma (Linux, Win, macOS).

 [Fase 2: Infraestructura y Comunidad] ─────────► (COMPLETADO / ACTIVO)
  • Despliegue del explorador de bloques oficial (explorer.korsh.org).
  • Publicación de la Billetera Web cliente (wallet.korsh.org).
  • Apertura de la Mining Pool oficial Stratum (pool.korsh.org).
  • Creación y expansión de canales comunitarios (Discord, Telegram).

 [Fase 3: Herramientas de Minería y Adopción] ──► (EN PROGRESO)
  • Distribución del software minero propietario optimizado para AVX-512/AVX2.
  • Expansión de pools de minería con servidores Stratum de baja latencia global.
  • Asistente automatizado de configuración rápida de Masternodes en un clic (VPS).
  • Auditoría integral de seguridad de componentes web y aplicaciones móviles.

 [Fase 4: Integración en Mercados e Interoperabilidad] ─► (PRÓXIMO)
  • Indexación en plataformas de seguimiento de hashrate y analítica
    (MiningPoolStats, CoinGecko, CoinMarketCap).
  • Integración en directorios y plataformas especializadas de Masternodes.
  • Listados en casas de cambio descentralizadas (DEX) y plataformas centralizadas (CEX).
  • Desarrollo de librerías y SDKs ligeros para integración con comercios electrónicos.
```

---

## 9. Conclusión

**Korsh ($KSH)** representa una respuesta firme y técnicamente rigurosa a la degradación de los principios de descentralización que han afectado a las criptomonedas de primera y segunda generación.

Al unificar la soberanía y accesibilidad computacional de la **Prueba de Trabajo pura en CPU (Yespower 1.0)** con la velocidad de liquidación comercial, la gobernanza descentralizada y la invulnerabilidad ante reorganizaciones del 51% aportada por los **Masternodes Deterministas (DIP0003 + ChainLocks)**, Korsh logra un equilibrio armónico entre seguridad, descentralización y escalabilidad práctica.

Respaldado por un **lanzamiento 100% justo, sin preminado**, un límite de suministro inmutable de **10,000,000 KSH** y una suite completa de software de código abierto, Korsh se consolida como una alternativa monetaria robusta, orientada a empoderar a la comunidad y a garantizar la libertad transaccional para la era digital.

---

## 10. Aviso Legal (Disclaimer)

*Este documento técnico (Whitepaper) tiene fines estrictamente informativos, educativos y de divulgación arquitectónica. Korsh es un proyecto de software de código abierto distribuido y descentralizado, libre de intermediarios financieros centralizados con fines de lucro.*

*La adquisición, minería, operación de nodos y tenencia de activos digitales conlleva riesgos operacionales y fluctuaciones inherentes a los mercados tecnológicos. Ningún fragmento de este documento debe interpretarse como asesoramiento financiero, recomendación de inversión, oferta pública de valores o promesa garantizada de rentabilidad económica. Los participantes asumen la responsabilidad técnica y regulatoria exclusiva según la jurisdicción legal aplicable a su actividad.*

---

**© 2026 Korsh Open Source Development Community**  
*Licencia MIT — Código y especificaciones accesibles públicamente.*
