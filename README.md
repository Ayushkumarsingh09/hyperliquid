````md
# Hyperliquid Order Book Slippage & Safe Position Sizing

<div align="center">

[![Dependencies Status](https://img.shields.io/badge/dependencies-up%20to%20date-brightgreen.svg)]
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)]
[![Security: bandit](https://img.shields.io/badge/security-bandit-green.svg)]
[![Pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)]
[![License](https://img.shields.io/badge/license-MIT-blue.svg)]

**Liquidity-aware execution and slippage analysis using Hyperliquid L2 Order Books**

</div>

---

## Project Context

A paper portfolio ignores liquidity.  
This project analyzes **real execution risk** using **Hyperliquid Level-2 order book depth** to answer:

> **How much of an asset can be bought before price impact exceeds acceptable slippage?**

The repository simulates large market buy orders, computes execution slippage, and defines **safe position size caps** under a strict risk constraint.

---

## Objective & Scope

- Exchange: **Hyperliquid**
- Assets: **ARB, OP, SUI**
- Rebalance size: **$1,000,000**
- Order sizes tested: **$50k, $200k, $1M**
- Slippage tolerance: **≤ 1%**

---

## Methodology (Analysis Logic)

1. Fetch **L2 order book snapshots** from Hyperliquid
2. Extract and sort **ask-side price levels**
3. Simulate **market buy execution** by walking the ask ladder
4. Compute **average execution price**
5. Calculate **slippage vs mid-price**
6. Identify **maximum notional size** with slippage ≤ 1%
7. Plot **Slippage (%) vs Order Size ($)**

---

## Installation

```bash
pip install hyperliquid-python-sdk
````

---

## Configuration

Create configuration file:

```bash
cp examples/config.json.example examples/config.json
```

Edit `examples/config.json`:

```json
{
  "account_address": "<YOUR_PUBLIC_WALLET_ADDRESS>",
  "secret_key": "<YOUR_PRIVATE_KEY>"
}
```

Optional: Generate an API wallet at
[https://app.hyperliquid.xyz/API](https://app.hyperliquid.xyz/API)

Use the API wallet private key as `secret_key`, while keeping the **main wallet** as `account_address`.

---

## Quick Start

```python
from hyperliquid.info import Info
from hyperliquid.utils import constants

info = Info(constants.MAINNET_API_URL, skip_ws=True)
l2_book = info.l2_book("ARB")
print(l2_book)
```

---

## Analysis Flow

```text
L2 Order Book Snapshot
        ↓
Market Buy Simulation
        ↓
Average Execution Price
        ↓
Slippage Calculation
        ↓
Safe Position Size Cap
```

---

## Outputs

* Slippage vs order size charts
* Safe allocation caps per asset
* Liquidity comparison across assets
* Execution-risk-aware allocation framework

---

## Development Setup

* Python **3.10**
* Poetry **1.x**

```bash
make install
make lint
make test
```

---

## Deliverables Supported

* Jupyter / Colab Notebook
* Slippage vs Order Size charts
* PDF execution risk summary
* Loom explanation of slippage logic

---

## Key Concepts Demonstrated

* Market microstructure
* Order book depth analysis
* Liquidity-aware execution
* Slippage modeling
* Risk-managed index rebalancing

---

## License

MIT License. See [LICENSE](LICENSE.md).

---

## Citation

```bibtex
@misc{hyperliquid-slippage-safe-caps,
  author = {Ayush Kumar Singh},
  title = {Hyperliquid Order Book Slippage and Safe Position Sizing},
  year = {2025},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/Ayushkumarsingh09/hyperliquid}}
}
```

---

## Credits

Built using Hyperliquid’s official Python SDK and inspired by institutional execution cost and market microstructure models.

```
```
