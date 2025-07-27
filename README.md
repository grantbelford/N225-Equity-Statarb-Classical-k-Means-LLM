# N225 Equity Statarb Classical (Industry) vs k-Means Clustering
Overview:

1. Using 589 days of daily N225 constituent equity closing price data, we compare statarb peformance between: 

Strat 1. Statarb - Classical Method (ie. focus on Industry classification for pairs selection - Fig2 for info) vs.

Strat 2. Statarb - k-Means Clustering (no pre-defined industry, sector or other restrictions - goal is for this approach to discover *non-intuitive* pairs with similar behaviour despite being from different industries)

Process - in both cases:
  
1. The trading pairs are selected & sorted on a custom *scoring* system which combines both cointegration strength & correlation.
ADF stat: prioritizes pairs cointegrated at 1% > 5% > 10%.
Corr: rewards higher absolute Pearson corrs.
*Score* = (ADF Level Wgt) + 2 * |Corr|.

2. The top 5 highest-scoring pairs from each approach are then selected for statarb backtesting *strat* (both under same trading signals/position sizing/tx costs/performance metrics).
Basic z-score MR *strat*: enters when spread exceeds ±2σ & exit at ±0.5σ.


Outcome: 
1. On an initial JPY 5m allocation to each strat (ie. JPY 1m per pair).
 
2. We notice a modest improvement in portfolio total return from Strat2 (0.50%) vs. Strat1 (-1.1%) - details in Fig1.
 
3. In Fig1 the narrower the width of the red & green (trading activities) areas can be interpreted as times of higher market choppiness.
  
4. In Fig1 investigating why all pairs have a large middle brown (neutral - no trading) section.

5. 1 pair (2768.T Sojitz Corp vs. 8053.T Sumitomo Corp) overlapped in both strats top 5 picks.

6. The pair showed strong cointegration (ADF p<0.01, ADF_Stat: -3.9034) & correlation (0.9692) giving it the "top score" of the 5 picks (4.9383) in the training window (90d lookback window for cointegration).

7. Strat1 thus grouped the pair because both are in the same "Conglomerates" industry.

8. Strat2 grouped the pair based on the stat results.

9. Both Sojitz and Sumitomo are sogo shosha (general trading companies) which could explain their similar return pattern.

10. However this pair performed the worse total return-wise in statarb backtesting where we saw (Mar24) Sumitomo share price (major copper mine acquisition announcement) decouple from Sojitz & (Aug24) JPY volatility spike (both names moved together but spreads widened permanently). 

11. The remaining 4 k-Means top pick pairs were all different industries and also no pair overlap with Strat1 picks (ref: Fig4).
 
