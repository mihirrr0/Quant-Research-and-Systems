# BankNifty Intraday Option Selling


The **BankNifty Intraday Option Selling** strategy focuses on trading the **Bank Nifty Index Contracts**. It involves selling both an **Out-of-The-Money (OTM)** or **At-The-Money (ATM)** Call and Put option, ensuring both have the same expiration date. A percentage-based stop-loss is applied to each position, and if triggered, the position is closed. Any remaining positions are squared off at the end of the trading day. This strategy is the result of my efforts to create a balanced approach that maximizes profitability while keeping risk under control.

---

## Process

### 1. Initial Backtesting
- I started by conducting a detailed backtest using historical Bank Nifty options data. The initial tests were based on selling ATM straddles (selling both ATM Call and Put) with fixed stop-loss percentages.
- During this phase, I optimized several parameters:
  - **Entry Time**
  - **Exit Time**
  - **Stop Loss Percentage**
  - **Percent of Equity (POE)**
  - **Leverage**
- A critical aspect of this phase was calculating the "Minimum Premium," which ensures position sizing is aligned with the available margin and leverage constraints.

### 2. Exploring Strike Variations
- To improve flexibility, I expanded the strategy to include a range of strikes from **In-The-Money (ITM)** to **Out-of-The-Money (OTM)**. Each variation was tested extensively to identify the best-performing configurations.
- The optimizations included:
  - Entry and Exit timings
  - Stop Loss Percentage
  - POE and Leverage
  - Days to Expiry (DTE) in some cases

### 3. Daily Strike Selection
- One of the improvements I introduced was the **Dynamic Strike Selection Logic**, which adjusts the strikes daily based on market conditions. This adaptability allowed the strategy to react better to changes in volatility and other factors.
- Additionally, I customized stop-loss percentages for each trading day to align with the dynamically selected strikes.

### 4. Minimum Premium Logic
- A key feature of this strategy is the **Minimum Premium Logic**, where only option strikes with a premium above or at a certain threshold are eligible for selling. I implemented this to ensure the selected strikes have enough potential reward to justify the associated risk and margin usage.
- Position sizing is dynamically tied to this logic, helping to maximize returns while keeping risk within acceptable levels.

### 5. Testing Protective Options
- To further enhance the strategy, I experimented with incorporating **long options** as protective hedges. These options were optimized to reduce margin requirements and mitigate risks during volatile market conditions.
- The testing focused on finding the ideal distance between the long and short strikes while ensuring the overall strategy remained profitable.

---

## Versions

### Current Live Setup
- The live version uses the **Minimum Premium Logic** for strike selection.
- **Leverage**: 12x for position sizing
- **Stop Loss**: Dynamically optimized for daily conditions
- **Entry Timing**: 9:45 AM to 12:30 PM across six setups
- **Exit Timing**: All positions squared off by 3:15 PM

### Variations Explored
During development, I explored multiple variations of the strategy:
- Testing different **Entry/Exit Times** to identify the most profitable trading windows.
- Evaluating the performance of strikes across ITM, ATM, and OTM zones.
- Developing alternative **Stop-Loss Criteria**, such as percentage movements in premium, index price changes, and ATR-based thresholds.
- Adding long options for risk mitigation and analyzing their impact on leverage and margin requirements.


