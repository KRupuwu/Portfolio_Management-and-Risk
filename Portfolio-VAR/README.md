# Portfolio Value at Risk (VaR) Analysis

This project provides a complete workflow for calculating and visualizing the **Value at Risk (VaR)** of a portfolio using multiple methods, including:

- **Historical VaR**
- **Parametric (Variance–Covariance) VaR**
- **Cornish–Fisher Adjusted VaR**
- **Monte Carlo (Univariate & Multivariate) VaR**

It also includes **90-day portfolio projections** using:
- Normal distribution simulation
- Bootstrapped returns simulation

Interactive plots and CSV reports are generated for deeper insights.

---

## Features

- 📈 **Multiple VaR methodologies** for robust risk estimation
- 🖼 **Visualizations**:
  - Portfolio performance with VaR confidence bands
  - Return distribution with VaR markers
- 📊 **Detailed reports** saved as CSV files:
  - Per-asset statistics (mean, std, skewness, kurtosis)
  - Portfolio-level VaR summaries in percentage and dollar terms
- 🔮 **90-day forward simulations** using normal and bootstrapped returns
- 💡 **Easily customizable**:
  - Ticker list
  - Weights
  - Date ranges
  - Confidence levels

---

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

---

## Usage

1. Open the `portfolio_value_at_risk.py` file and adjust:
   - `tickers` — list of stock symbols
   - `weights` — portfolio allocation weights (must sum to 1)
   - `portfolio_value` — starting portfolio value
   - `start_date` / `end_date` — historical data window
   - `confidence_level` — confidence level for VaR

2. Run the script:
   ```bash
   python portfolio_value_at_risk.py
   ```

3. Outputs:
   - `per_asset_stats.csv` — descriptive stats for each asset
   - `portfolio_var_summary.csv` — portfolio VaR summary
   - Matplotlib plots (shown interactively)

---

## Example Output

Console summary:
```
--- Portfolio VaR Analysis ---
Initial Portfolio Value: $5,000.00
Historical VaR (95%): $ 125.34 (-2.51%)
Parametric VaR (95%): $ 132.67 (-2.65%)
Cornish–Fisher VaR (95%): $ 128.90 (-2.58%)
MC Univariate VaR (95%): $ 130.45 (-2.61%)
MC Multivariate VaR (95%): $ 127.89 (-2.56%)
```

Portfolio performance plot with VaR band:

![Example Plot](example_plot.png)

---

## Requirements

- Python 3.9+
- See `requirements.txt` for package versions

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## Author

Developed by **Kudakwashe Rupuwu**.
