# Downside Risk - Maximum Drawdown Analyzer

This project provides a simple Python script to analyze the **maximum drawdown** of a given stock over the past 2 years, and to evaluate the potential returns if invested at the point of maximum drawdown.

## Features
- Fetches historical stock price data using [yfinance](https://pypi.org/project/yfinance/)
- Calculates maximum drawdown from the peak price
- Determines buy price at maximum drawdown and current portfolio value
- Plots:
  - Stock price over time with buy point highlighted
  - Drawdown percentage over time
- Customizable:
  - Stock ticker
  - Minimum drawdown percentage
  - Investment amount

## Requirements
- Python 3.7+
- yfinance
- matplotlib

## Installation
```bash
pip install -r requirements.txt
```

## Usage
Edit the script or use it in Python directly:
```python
from downside_risk_maximum_drawdown import analyze_drawdown

# Example: Analyze NVDA with a 30% drawdown threshold and $100 investment
analyze_drawdown('NVDA', 30, 100)
```

You can run the provided example directly by executing:
```bash
python downside_risk_maximum_drawdown.py
```

## Example Output
The script prints:
- Max drawdown percentage
- Buy price
- Current price
- Investment growth

And displays two plots showing price and drawdown.

## License
This project is licensed under the MIT License.
