# Pairs Trading Strategy Implementation

## Overview

This repository contains a Python implementation of a Pairs Trading Strategy using a statistical arbitrage approach based on cointegration. The strategy identifies pairs of stocks that exhibit a stable relationship over time, allowing traders to capitalize on temporary deviations from this relationship.

## Features

- **Data Fetching**: Automatically fetches historical stock data for Nifty 100 stocks using the `yfinance` and `niftystocks` libraries.
- **Correlation and Cointegration Analysis**: Identifies highly correlated and cointegrated pairs of stocks.
- **Hedge Ratio Calculation**: Computes the hedge ratio for the selected pairs to optimize trading positions.
- **Signal Generation**: Generates trading signals based on the z-score of the price spread.
- **Backtesting**: Simulates trading based on historical data to evaluate the strategy's performance.
- **Performance Metrics**: Calculates key performance metrics such as CAGR, Sharpe Ratio, Sortino Ratio, and Maximum Drawdown.
- **Visualization**: Provides comprehensive visualizations of price movements, spread, z-scores, portfolio value, and performance metrics.

## Logic Behind the Strategy

### 1. Pairs Trading Concept

Pairs trading is a market-neutral trading strategy that involves identifying two stocks that historically move together. The idea is to take advantage of temporary divergences in their price relationship. When the prices diverge, the trader goes long on the undervalued stock and short on the overvalued stock, expecting the prices to converge back to their historical relationship.

### 2. Data Fetching

The strategy begins by fetching historical price data for a set of stocks (in this case, Nifty 100 stocks). This data is used to analyze correlations and cointegration between stock pairs.

### 3. Correlation Analysis

The first step in identifying potential pairs is to calculate the correlation matrix of the stock prices. Correlation measures the degree to which two stocks move in relation to each other. A high correlation indicates that the stocks tend to move together.

### 4. Cointegration Testing

While correlation indicates a relationship, it does not imply that the relationship is stable over time. Cointegration tests (using the Engle-Granger method) are performed to determine if a linear combination of the two stock prices is stationary. If two stocks are cointegrated, it suggests that they have a long-term equilibrium relationship.

### 5. Hedge Ratio Calculation

Once cointegrated pairs are identified, the hedge ratio is calculated. The hedge ratio indicates how many units of one stock should be held for each unit of the other stock to minimize risk. This is calculated using the covariance of the stock prices.

### 6. Spread Calculation and Z-Score

The spread between the two stocks is calculated based on the hedge ratio. The z-score of the spread is then computed to identify how far the current spread is from its mean in terms of standard deviations. This helps in determining entry and exit points for trades.

### 7. Signal Generation

Trading signals are generated based on the z-score:
- **Long Signal**: When the z-score is below a certain negative threshold (e.g., -1), it indicates that the spread is wider than usual, suggesting that the undervalued stock may rise.
- **Short Signal**: When the z-score is above a certain positive threshold (e.g., +1), it indicates that the spread is narrower than usual, suggesting that the overvalued stock may fall.

### 8. Backtesting

The strategy is backtested using historical data to simulate trades based on the generated signals. This involves calculating the profit and loss (PnL) for each trade and tracking the overall portfolio value over time.

### 9. Performance Metrics

Key performance metrics are calculated to evaluate the effectiveness of the strategy:
- **CAGR (Compound Annual Growth Rate)**: Measures the mean annual growth rate of the investment.
- **Sharpe Ratio**: Indicates the risk-adjusted return of the strategy.
- **Sortino Ratio**: Similar to the Sharpe Ratio but focuses on downside risk.
- **Maximum Drawdown**: Measures the largest peak-to-trough decline in portfolio value.

### 10. Visualization

The strategy provides various visualizations to help analyze the results, including:
- Price movements of selected pairs
- Spread and its mean
- Z-score with trading signals
- Portfolio value over time
- Drawdown analysis
- Rolling metrics (Sharpe ratio and volatility)

## Requirements

To run this code, you need to have the following Python packages installed:

- `numpy`
- `pandas`
- `yfinance`
- `niftystocks`
- `statsmodels`
- `quantstats`
- `matplotlib`
- `seaborn`

You can install the required packages using pip:


## Usage

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/pairs-trading-strategy.git
   cd pairs-trading-strategy
   ```

2. Open the Python script (e.g., `pairs_trading.py`) in your preferred IDE or text editor.

3. Modify the `start_date` and `end_date` parameters in the `main()` function to set the desired backtesting period.

4. Run the script:

   ```bash
   python pairs_trading.py
   ```

5. The script will fetch market data, identify correlated and cointegrated pairs, generate trading signals, backtest the strategy, and display performance metrics along with visualizations.

## Code Structure

- **PairsTrading Class**: Contains methods for fetching data, finding correlated and cointegrated pairs, calculating hedge ratios, generating signals, backtesting, and plotting results.
- **Main Function**: Initializes the PairsTrading class and executes the strategy steps.

## Example Output

The script will output the following:

- Selected pairs of stocks
- Trading signals
- Performance metrics (CAGR, Sharpe Ratio, etc.)
- Visualizations of price movements, spread, z-scores, and portfolio performance

## Contributing

Contributions are welcome! If you have suggestions for improvements or new features, feel free to open an issue or submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [yfinance](https://pypi.org/project/yfinance/) for fetching stock data.
- [niftystocks](https://pypi.org/project/niftystocks/) for Nifty stock tickers.
- [statsmodels](https://www.statsmodels.org/stable/index.html) for statistical tests.
- [quantstats](https://github.com/enzoampil/quantstats) for performance metrics.
- [matplotlib](https://matplotlib.org/) and [seaborn](https://seaborn.pydata.org/) for data visualization.
