# 📈 Portfolio Manager

A detailed and robust Python library for managing stock and equity portfolios with support for **long** and **short positions**, **realized/unrealized P&L tracking**, **day gains**, and **FIFO-based cost accounting**.

---

## 🚀 Features

- ✅ Buy, sell, short, and cover stock positions with FIFO lot tracking
- 📊 Accurate calculation of realized and unrealized profit/loss
- 🧮 Aggregated and per-lot P&L summaries
- 📈 Real-time price updates and day gain tracking
- 📝 Transaction history and portfolio summary reports
- 🧠 Built-in lot- and symbol-level metrics
- 📦 Clean, modular structure — easy to integrate into larger apps

---

## 📦 Installation

Clone this repository or install it as a module:

```bash
pip install tickie
```
🛠️ Usage Example
python
```
from portfolio import Portfolio

portfolio = Portfolio()

# Add long positions
portfolio.buy("AAPL", 100, 150.00, "2024-05-01", "Apple Inc.") Adds a long position
portfolio.buy("GOOG", 50, 120.00, "2024-05-05", "Alphabet Inc.") Sells long shares using FIFO
portfolio.short_sell("MSFT", 10, 49.00, "2025-05-26", "MICROSOFT CORP") Opens a short position
portfolio.buy_to_cover("MSFT", 10, 180.00, "2024-05-01") Closes a short position using FIFO

# Update market data
portfolio.update_current_price("AAPL", 155.00) Sets live price for unrealized P&L
portfolio.update_previous_closing_price("AAPL", 152.00) Sets prices to cacluate Day gain P&L
```
```
get_portfolio_summary()	Returns a pandas DataFrame summary

  symbol    Company Name  quantity  Avg. Price/Share  Current Price  Unrealized P/L  Unrealized Gain %  Day Gain  Day Gain %
0   GOOG   Alphabet Inc.        80        131.250000          130.0          -100.0          -0.952381     400.0    4.000000
1   MSFT  MICROSOFT CORP       -10         49.000000           45.0            40.0           8.163265      20.0    4.255319
2   NVDA     NVIDIA Corp        75        200.000000          210.0           750.0           5.000000     375.0    2.439024
3   TSLA      Tesla Inc.       -30        203.333333          190.0           400.0           6.557377     150.0    2.564103
Total Realized P/L: $2800.00
Total Unrealized P/L: $1090.00
Total Portfolio P/L: $3890.00
```
```
get_pnl_per_lot_summary()	Returns P&L at the individual lot level

--- P/L Per Lot ---
  Symbol    Company Name                                Lot ID Position Type Transaction Action Security Type  Quantity  Original Quantity  Purchase/Short Price  Total Lot Cost Basis        Date  Current Price  Unrealized P/L  Unrealized Gain %  Day Gain  Day Gain %
0   GOOG   Alphabet Inc.  ba67a953-6484-4ff8-a8b1-5ad829705ed5          Long                Buy  Common Stock        30                100                 100.0               10000.0  2024-01-10          130.0           900.0          30.000000     150.0    4.000000
1   GOOG             N/A  4def8a80-2884-4d20-bf5c-5bc098c25160          Long                Buy  Common Stock        50                 50                 150.0                7500.0  2024-01-15          130.0         -1000.0         -13.333333     250.0    4.000000
2   MSFT  MICROSOFT CORP  43bd932e-18c8-45c8-88fd-12bbba541826         Short         Sell Short  Common Stock        10                 10                  49.0                 490.0  2025-05-26           45.0            40.0           8.163265      20.0    4.255319
3   NVDA     NVIDIA Corp  0d9aff37-d5d0-4c76-8709-72c4d428330b          Long                Buy  Common Stock        75                 75                 200.0               15000.0  2024-02-01          210.0           750.0           5.000000     375.0    2.439024
4   TSLA      Tesla Inc.  575a93e6-82b9-4f3e-a589-ab2302671011         Short         Sell Short  Common Stock         5                 20                 200.0                4000.0  2024-04-01          190.0            50.0           5.000000      25.0    2.564103
5   TSLA             N/A  7c626a0a-f4dc-48ad-89f5-68f19e6c2994         Short         Sell Short  Common Stock        10                 10                 210.0                2100.0  2024-04-05          190.0           200.0           9.523810      50.0    2.564103
```
```
get_transaction_history()	View all recorded buys/sells

--- Transaction History ---
                         transaction_id        date symbol        action  quantity  price    company_name
0  ba67a953-6484-4ff8-a8b1-5ad829705ed5  2024-01-10   GOOG           Buy       100  100.0   Alphabet Inc.
1  4def8a80-2884-4d20-bf5c-5bc098c25160  2024-01-15   GOOG           Buy        50  150.0             N/A
2  0d9aff37-d5d0-4c76-8709-72c4d428330b  2024-02-01   NVDA           Buy        75  200.0     NVIDIA Corp
3  43bd932e-18c8-45c8-88fd-12bbba541826  2025-05-26   MSFT    Sell Short        10   49.0  MICROSOFT CORP
4  ec359af6-b1f2-4d71-9e69-f1c08f71e15d  2024-03-01   GOOG          Sell        70  140.0   Alphabet Inc.
5  575a93e6-82b9-4f3e-a589-ab2302671011  2024-04-01   TSLA    Sell Short        20  200.0      Tesla Inc.
6  7c626a0a-f4dc-48ad-89f5-68f19e6c2994  2024-04-05   TSLA    Sell Short        10  210.0             N/A
7  3c2d6709-946f-4679-99fc-96fdcfb0174c  2024-05-01   TSLA  Buy to Cover        15  180.0      Tesla Inc.
```
🧪 Testing
Run the script directly to execute a full demo:


📜 License
MIT License. Free to use, modify, and distribute.
