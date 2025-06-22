# Portfolio-Optimization-with-Python
Created by Jiyen Khullar

## Introduction

This project aims to construct an optimal combination of Nifty 50 stocks using advanced portfolio management tools such as Markowitz Mean-Variance Optimization, Monte Carlo simulation, and Value at Risk (VaR). The goal is to enhance returns while minimizing risk and to compare a broad Nifty 50 portfolio against a focused five-stock subset.

## Data Collection and Risk-Free Rate

* **Historical Stock Data**: Adjusted closing prices for all Nifty 50 symbols over the past three years were fetched via the `yfinance` library.
* **Risk-Free Rate**: The 10-year government bond yield (6.8%) from the Reserve Bank of India was hard-coded as `0.068` for Sharpe ratio calculations.

### Sharpe Ratio Formula

```text
Sharpe Ratio = (Portfolio Return − Risk-Free Rate) / Portfolio Standard Deviation
```

## Optimization and Simulation

### Markowitz Mean-Variance Optimization

* **Objective**: Maximize Sharpe ratio under constraints:

  * Sum of weights = 1 (full investment)
  * Weights ∈ \[0,1] (no short selling or leverage)
* **Method**: Minimize inverse Sharpe ratio using SLSQP.
* **Outputs**: Optimized weights, expected return, standard deviation, and Sharpe ratio (annualized by 252 trading days).

### Monte Carlo Simulation

* **Process**:

  1. Generate random weight vectors via `np.random.random()`.
  2. Normalize to sum 1.
  3. Compute return, volatility, and Sharpe ratio for each of N simulations.
  4. Plot the Efficient Frontier (return vs. risk).
* **Assumptions**: No short selling, constant risk-free rate of 6.8%.

## Value at Risk (VaR) Analysis

* **Definition**: Maximum expected daily loss at a given confidence level.

* **Formula**:

  ```text
  VaR = Expected Return + z · Volatility
  ```

  where *z* = −1.645 for 95% confidence.

* **Results**:

  * **Nifty 50 Portfolio**: VaR = 3.29%
  * **Five-Stock Portfolio**: VaR = 8.78%

## Results

### Nifty 50 Portfolio

* **Markowitz Optimization**:

  * Return: 47.54%
  * Volatility: 16.20%
  * Sharpe Ratio: 251.54%
* **Monte Carlo Simulation**:

  * Best Random Return: 27.41%
  * Volatility: 14.66%
  * Sharpe Ratio: 140.57%
* **VaR (95%)**: 3.29%

### Five-Stock Portfolio

* **Selected Stocks**:

  * ABB India (ABB.NS)
  * The Indian Hotels Company (INDHOTEL.NS)
  * TVS Motor Company (TVSMOTOR.NS)
  * Oberoi Realty (OBEROIRLTY.NS)
  * Usha Martin (USHAMART.NS)

* **Markowitz Optimization**:

  * Return: 50.43%
  * Volatility: 25.31%
  * Sharpe Ratio: 172.40%

* **Monte Carlo Simulation**:

  * Best Random Return: 50.14%
  * Volatility: 25.15%
  * Sharpe Ratio: 172.34%

* **VaR (95%)**: 8.78%

## Rationale for Stock Selection

* **Technical Filter**: Weekly 60 RSI breakout strategy.
* **Fundamental Analysis**: Revenue growth, margins, leverage, and institutional holdings.
* **Backtested Performance** (Nifty 50 weighted):

  * Annual Return: 26%
  * Volatility: 18%
  * Sharpe Ratio: 1.20

---

*All data sourced via Yahoo Finance, RBI, and ICICI Direct.*

