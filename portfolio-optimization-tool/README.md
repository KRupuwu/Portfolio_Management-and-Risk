# Markowitz Portfolio Optimizer (CLI)

This repository contains a single Python script that performs **mean–variance portfolio optimization** using historical price data from Yahoo Finance (via `yfinance`). It:
- Fetches adjusted closing prices for user-provided tickers and dates
- Computes **annualized expected returns** and the **covariance matrix**
- Finds the **Maximum Sharpe Ratio** portfolio and the **Minimum Volatility** portfolio (no short-selling)
- Generates the **efficient frontier** and a scatter of random portfolios
- Plots everything in a single chart

> 📌 The script is fully interactive from the terminal: you’ll be prompted for tickers and a date range when you run it.

---

## Features
- **Data ingestion**: pulls historical prices with `yfinance`
- **Risk/return stats**: annualized expected returns, annualized covariance
- **Optimization**: Max Sharpe and Min Vol portfolios via SLSQP
- **Efficient frontier**: constrainted min-vol optimization across target returns
- **Visualization**: matplotlib plot of random portfolios, efficient frontier, and the two optimal portfolios

---

## Quickstart

### 1) Clone and enter the repo
```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

### 2) (Recommended) Create and activate a virtual environment
```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate
```

### 3) Install dependencies
```bash
pip install -r requirements.txt
```

### 4) Run the optimizer
```bash
python portfolio_optimizer.py
```
You’ll be prompted for:
- **Tickers** (comma-separated, e.g., `AAPL,MSFT,GOOG`)
- **Start date** (e.g., `2020-01-01`)
- **End date** (e.g., `2023-01-01`)

A plot window will open on success and you’ll see printed statistics in the terminal.

---

## Example
```
Enter comma-separated stock tickers (e.g., AAPL,MSFT,GOOG): AAPL,MSFT,GOOGL,AMZN,TSLA
Enter start date (YYYY-MM-DD, e.g., 2020-01-01): 2020-01-01
Enter end date (YYYY-MM-DD, e.g., 2023-01-01): 2024-12-31
```

**Output (terminal):**
- Annualized expected returns per asset
- Annualized covariance matrix
- Max Sharpe portfolio (return, volatility, Sharpe, and weights)
- Min Vol portfolio (return, volatility, Sharpe, and weights)

**Output (plot):**
- Random portfolios colored by Sharpe ratio
- Dashed red efficient frontier
- Blue star (Minimum Volatility)
- Green star (Maximum Sharpe)

---

## How it Works (brief)
1. **Returns & covariance**
   - Convert prices to daily returns, drop NaNs
   - Annualize with 252 trading days
2. **Portfolio metrics**
   - \(E[R_p] = \sum w_i \mu_i\)
   - \(\sigma_p = \sqrt{w^T \Sigma w}\)
   - **Sharpe**: \( (E[R_p] - r_f) / \sigma_p \)
3. **Optimization**
   - Constrained **SLSQP** with bounds \(0 \le w_i \le 1\), \(\sum w_i = 1\)
   - Max Sharpe: minimize negative Sharpe
   - Min Vol: minimize volatility
4. **Efficient frontier**
   - For a grid of target returns, minimize volatility subject to hitting that return

---

## Configuration & Notes
- **Risk-free rate** is set to `0.02` (2% annual) inside the script. You can change it.
- **No short selling**: weights are bounded in `[0, 1]` and must sum to 1.
- **Data quality**: If tickers have sparse data or corporate actions, `dropna()` may reduce usable rows.
- **Runtime**: The Monte Carlo scatter uses 10,000 random portfolios by default; you can lower this if needed.
- **Plot display**: The script calls `plt.show()` which opens a window; in headless environments, save the figure instead (e.g., `plt.savefig('frontier.png')`).

---

## File Structure
```
.
├── portfolio_optimizer.py   # <-- Your script (rename if needed)
├── requirements.txt
└── README.md
```

> If your script file name is not `portfolio_optimizer.py`, update the commands above accordingly.

---

## Requirements
- Python 3.9+
- See `requirements.txt` for packages

---

## Troubleshooting
- **“No data found for tickers …”**: Verify ticker symbols and date range; consider expanding the range.
- **Optimization warnings**: The script suppresses a benign SLSQP message; for debugging, remove the warning filter.
- **Plot doesn’t show**: Ensure you’re not running headless; or replace `plt.show()` with `plt.savefig('frontier.png')`.

---

## Acknowledgments
- Price data via [`yfinance`](https://github.com/ranaroussi/yfinance)
- Optimization via `scipy.optimize.minimize`
- Plotting via `matplotlib`

---

*Optional: add a license (e.g., MIT) to clarify how others may use your code.*
