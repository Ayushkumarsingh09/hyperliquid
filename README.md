

````md
# Hyperliquid Slippage Analysis

This project analyzes **order book depth on Hyperliquid** to understand how much of an asset can be bought without causing high slippage.

The goal is to simulate large market buy orders using **Level-2 (L2) order book data** and determine a **safe position size** based on a fixed slippage limit.

---

## Problem Statement

Paper portfolios assume perfect liquidity, which is not realistic.

This project answers:

**How much of a coin can we buy before slippage exceeds 1%?**

---

## Scope

- Exchange: Hyperliquid
- Assets: ARB, OP, SUI
- Total rebalance amount: $1,000,000
- Order sizes tested:
  - $50,000
  - $200,000
  - $1,000,000
- Maximum allowed slippage: 1%

---

## Approach

1. Fetch L2 order book data from Hyperliquid
2. Use the ask side of the order book
3. Simulate market buy orders by consuming available liquidity
4. Calculate the average execution price
5. Measure slippage compared to the mid price
6. Find the maximum order size with slippage ≤ 1%
7. Plot slippage vs order size

---

## Installation

```bash
pip install hyperliquid-python-sdk
````

---

## Configuration

Copy the example config file:

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

Optional: You can create an API wallet at
[https://app.hyperliquid.xyz/API](https://app.hyperliquid.xyz/API)

---

## Quick Start

```python
from hyperliquid.info import Info
from hyperliquid.utils import constants

info = Info(constants.MAINNET_API_URL, skip_ws=True)
order_book = info.l2_book("ARB")
print(order_book)
```

---

## Analysis Flow

```text
Order Book (L2)
   ↓
Market Buy Simulation
   ↓
Average Execution Price
   ↓
Slippage Calculation
   ↓
Safe Position Size
```

---

## Output

* Slippage vs order size charts
* Safe allocation limit for each asset
* Comparison of liquidity across assets

---

## Development

Requirements:

* Python 3.10
* Poetry

Install dependencies:

```bash
make install
```

Run checks:

```bash
make lint
make test
```

# Google Colab Notebook

This project is implemented and executed using **Google Colab**.

## 📘 Notebook Link
Access the complete Colab notebook here:  
👉 https://colab.research.google.com/drive/1b5uSEov-nvXXalLX-dnuRLEdobxqljxq?usp=sharing

## 🚀 How to Use
1. Open the link above.
2. Click on **File → Save a copy in Drive** (optional).
3. Run the cells sequentially to reproduce results.

## 🛠 Requirements
- Google account
- Internet connection

## 📌 Notes
- The notebook contains all code, explanations, and outputs.
- No local setup is required.




---

## License

MIT License.

---

## Author

Ayush Kumar Singh
[https://github.com/Ayushkumarsingh09](https://github.com/Ayushkumarsingh09)

```

