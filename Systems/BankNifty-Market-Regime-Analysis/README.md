# Exploring Market Regimes for Bank Nifty Trading Systems

This project was created to perform a detailed analysis of how various market regimes impacted the performance of trading systems I was implementing at the time. The primary objective was to identify patterns and trends in live market conditions as well as backtested data, offering insights into how regime-specific behaviors influence profits and losses.

---

## Analysis Process

### 1. Data Collection and IV Computation
- **Dataset**: I worked with 5-minute interval data for the Bank Nifty index, covering the period from **January 1, 2016, to May 31, 2023**. This comprehensive dataset ensured robust analysis over different market cycles.
- **Implied Volatility (IV)**: To evaluate market volatility, I calculated the IV as the average of the call and put IV for at-the-money options within the same period.

### 2. Market Trend Classification
- **Trend Categories**: Days were initially categorized into **Flat, Bearish, or Bullish** based on the opening and closing prices of Bank Nifty.
- **Supporting Metrics**:
  - **Daily slope** to understand the directionality of price movement.
  - Ratios like the **high-to-low** and **close-to-low differences**, providing insights into intraday volatility.
  - **Standard deviation of price changes** relative to the Bank Nifty VIX, helping identify volatility extremes.

### 3. Market Noise Analysis
- **Definition**: Market noise refers to intraday price distortions or fluctuations that obscure clear trends.
- **Categories**: Days were classified as either **Choppy** or **Trending** based on:
  - **R-squared Value**: Higher values signify stronger correlation and trending markets, while lower values indicate market noise or choppiness.
  - **Price Density**: Measures how tightly prices are concentrated over the trading session.
  - **Efficiency Ratio**: Assesses the efficiency of price movement in a specific direction.
  - **Swing Count**: Reflects the number of price swings within a day, indicating market indecision.

### 4. Categorizing Market Days into Buckets
Using the trend and noise classifications, I assigned each day to one of six buckets:
- **Bucket 1:** Trending Bearish
- **Bucket 2:** Choppy Bearish
- **Bucket 3:** Trending Flat
- **Bucket 4:** Choppy Flat
- **Bucket 5:** Trending Bullish
- **Bucket 6:** Choppy Bullish

[![Screenshot-2024-11-24-at-10-06-14-AM.png](https://i.postimg.cc/FHXnK47K/Screenshot-2024-11-24-at-10-06-14-AM.png)](https://postimg.cc/PPKM60bG)

### 5. Trading System Performance Analysis
- **Systems Analyzed**: I evaluated the equity curves for specific Bank Nifty systems (SID, PSAR, and Long ON).
- **Key Metrics**:
  - **R-squared Threshold**: ≤ 0.3 for choppy markets, > 0.3 for trending markets.
  - **Standard Deviation**: Used to differentiate Bearish, Flat, and Bullish trends based on normalized data.

---

## Key Results and Insights

### 1. R-Squared Analysis

[![Screenshot-2024-11-24-at-10-31-40-AM.png](https://i.postimg.cc/Qtm57vg1/Screenshot-2024-11-24-at-10-31-40-AM.png)](https://postimg.cc/627yJjmp)

- **Insight**: Higher R-squared values represent a stronger correlation and a trending market. Lower values indicate deviation from the trend, signifying choppy behavior.
- **Threshold**: A value of **0.3** was identified as a key point for differentiating between trending and choppy markets. For values below this, the systems performed poorly due to market noise.

### 2. Standard Deviation and Volatility Analysis
[![Screenshot-2024-11-24-at-10-37-28-AM.png](https://i.postimg.cc/sgBg9bz7/Screenshot-2024-11-24-at-10-37-28-AM.png)](https://postimg.cc/bZhPqCsw)


- **Ranges**:
  - Below -0.25 SD: Bearish
  - Between -0.25 SD and +0.25 SD: Flat
  - Above +0.25 SD: Bullish



---

---
### 3. Yearly and Monthly Bucket Trends
[![Screenshot-2024-11-24-at-10-58-06-AM.png](https://i.postimg.cc/wT3SMmDT/Screenshot-2024-11-24-at-10-58-06-AM.png)](https://postimg.cc/jL08kC8G)



[![Screenshot-2024-11-24-at-10-58-38-AM.png](https://i.postimg.cc/0NvWYMKS/Screenshot-2024-11-24-at-10-58-38-AM.png)](https://postimg.cc/SnZfqKrQ)
- **Insight**: Over the years, **choppy days** were found to dominate in months that incurred losses. For example, February 2023 was identified as the worst-performing month due to a high frequency of flat, choppy days.
- **Observation**: When trending days (Buckets 1, 3, 5) outweighed choppy days (Buckets 2, 4, 6), system profitability improved.

### 4. Probability of Bucket Occurrences
[![Screenshot-2024-11-24-at-10-58-23-AM.png](https://i.postimg.cc/hPJ5cqqX/Screenshot-2024-11-24-at-10-58-23-AM.png)](https://postimg.cc/nCJkGgrx)

[![Screenshot-2024-11-24-at-11-14-07-AM.png](https://i.postimg.cc/y6t6js1j/Screenshot-2024-11-24-at-11-14-07-AM.png)](https://postimg.cc/9zPjF3qw)

- The counts of trending and choppy buckets for bearish, flat, and bullish days are shown below, along with their probabilities for month of February.
- **Insight**: I found that **choppy flat days (Bucket 4)** significantly impacted system profitability. When the combined probabilities of choppy buckets exceeded those of trending buckets, trading systems often underperformed.



---

## Observations and Conclusion

### Key Observations
- **Choppy Days**: These conditions were the most challenging for trading systems, often leading to unprofitable results.
- **Flat Markets**: Days with minimal price movement adversely impacted P&L.
- **Trending Days**: Clear directional trends offered better opportunities for trading systems.

### Conclusion
- Through this analysis, I discovered that trading systems underperform significantly during choppy market conditions. Both **Flat** and **Choppy** regimes tend to reduce profitability, as seen in the adverse P&L effects observed. Insights derived from these classifications can be utilized to enhance the robustness of trading strategies. By categorizing days into well-defined buckets, I was able to identify actionable insights for improving system robustness.

