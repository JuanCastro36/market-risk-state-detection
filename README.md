# market-risk-state-detection
Econophysics-inspired analysis of financial market regimes using rolling correlations, Power Map noise suppression, MDS, K-Means and transition matrices.

# Financial Market Regime Detection

This project implements an econophysics-inspired pipeline to identify financial market regimes from stock-return correlation patterns.

The analysis is based on rolling correlation matrices, Power Map noise suppression, zeta distance matrices, Multidimensional Scaling (MDS), K-Means clustering and transition probability matrices.

The goal is not to predict crashes, but to explore how the market moves between low-correlation, intermediate and high-correlation regimes.

## Motivation

Financial markets are complex systems whose correlation structure changes over time. During periods of stress, assets often become more correlated, reducing diversification and increasing systemic risk.

This project studies whether recurring correlation patterns can be grouped into interpretable market states.

## Methodology

The pipeline follows these steps:

1. Download adjusted closing prices for a selected universe of S&P 500 stocks.
2. Compute daily logarithmic returns.
3. Build rolling correlation matrices using 20-day windows and 10-day shifts.
4. Apply the Power Map transformation to suppress noise in short-window correlation matrices.
5. Compute the zeta distance matrix between correlation structures.
6. Use MDS to embed correlation matrices into a two-dimensional space.
7. Apply K-Means to identify market states.
8. Order states by mean market correlation.
9. Compute transition probability matrices between consecutive market states.

## Reference

This project is inspired by:

Pharasi, H. K., Sharma, K., Chatterjee, R., Chakraborti, A., Leyvraz, F., & Seligman, T. H. (2018). *Identifying long-term precursors of financial market crashes using correlation patterns*. New Journal of Physics, 20, 103041.

## Main Results

Models with k = 3, k = 4 and k = 5 were compared.

The k = 4 model is closer to the original study for the U.S. market. However, in the extended 1985–2026 sample used here, two intermediate states showed very similar mean correlations.

The k = 3 model provides a clearer portfolio interpretation:

- S1: low-correlation regime
- S2: intermediate regime
- S3: high-correlation stress regime

The transition matrix shows that market states are persistent: the probability of remaining in the same regime is higher than transitioning to another state.

## Selected Figures

### Temporal evolution of correlation structures

![Zeta Matrix](https://github.com/JuanCastro36/market-risk-state-detection/blob/main/reports%20/figures/zeta_matrix.png)

### MDS map of market states

![MDS Market States](https://github.com/JuanCastro36/market-risk-state-detection/blob/main/reports%20/figures/mds_market_states_k3.png)

### Representative correlation matrices by state

![Average Correlation Matrices](https://github.com/JuanCastro36/market-risk-state-detection/blob/main/reports%20/figures/average_correlation_matrix_by_state_k3.png)

### Transition probability matrix

![Transition Matrix](https://github.com/JuanCastro36/market-risk-state-detection/blob/main/reports%20/figures/transition_probability_matrix_k3.png)

## Technologies

- Python
- pandas
- NumPy
- scikit-learn
- Matplotlib
- Seaborn
- NetworkX
- yfinance

## How to Run

Install dependencies:

```bash
pip install -r requirements.txt
