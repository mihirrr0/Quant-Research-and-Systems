# Nifty Intraday Option Selling

---

## **Introduction**

This repository focuses on a Nifty Weekly Short Options Intraday Strategy designed for weekly expiries on the Nifty index. The core idea is to sell an out-of-the-money (OTM) or at-the-money (ATM) call and put option with matching expiration dates. A percentage-based stop-loss mechanism is applied on the option premium. Once the stop-loss condition is met for any leg, that specific leg is closed, and any remaining positions are squared off at the end of the trading day.

---

## **Process**

1. **Testing and Implementation:**
   - Initially, I conducted testing on BankNifty options, starting with ATM strikes before moving to OTM and dynamic strikes. The goal was to refine the strategy by introducing dynamic strike selection, primarily based on the minimum premium logic.
   - For Nifty Weekly Short Options, the strategy was tested using only OTM strikes and dynamic strike selection, avoiding ATM strikes.
   - The backtesting process was carried out using Nifty’s weekly continuous contracts database. A predefined stop-loss percentage was applied to option premiums to limit risk, while the remaining positions were automatically squared off at the end of the trading day.

   Key variables optimized include:
   - Entry time  
   - Exit time  
   - Stop-loss percentage  
   - Position sizing based on percentage of equity (POE)  
   - Leverage used  

   All these optimizations are stored in detailed backtest files for reference and future improvements.

2. **Dynamic Strike Selection:**
   - Instead of fixed strike selection, I optimized the method to determine which strike prices to trade each day. I also explored how stop-loss percentages could be tailored to different trading days for better results.

3. **Enhanced Minimum Premium Logic:**
   - To make strike selection more dynamic, minimum premium logic was incorporated. This approach not only influenced position sizing but also helped in picking strikes closest to the specified minimum premium value.  
   - Optimized variables for this process include entry/exit timing, stop-loss percentage, leverage, and POE.

4. **Refinement of Leverage and Long Strikes:**
   - Earlier, intraday trading used up to 25x leverage, but due to regulatory changes, this was reduced to 12x. The strategy was adjusted to comply with this requirement.  
   - Protective long options were introduced, where the long strikes ranged from one to twenty strikes away from the short options. I found this adjustment helped reduce margin requirements and provided additional flexibility.  

   Specific backtests combining ATM/OTM strikes with minimum premium adjustments were documented.

---

## **Versions**

Currently, the live strategy uses the refined minimum premium logic for strike selection, with the following configurations:
- A stop-loss percentage unique to each day
- Position sizing aligned with 3% POE
- Leverage capped at 12x  
- Trading across six different systems spanning the time range of 9:45 AM to 12:30 PM, with a gap of approximately 30–45 minutes between entries.

Here are some of the key experiments and optimizations I tested during development:
- Entry and exit timing, stop-loss percentages, and leverage adjustments
- Squaring off both the long and short legs simultaneously at the end of the day (EOD)
- Testing different levels of protection through long OTM strikes for BankNifty in multiples of 100
- Using monthly options as protection while selling weekly options
- Exploring scenarios with no additional leverage or protection when maximum upside is capped
- Testing ITM short strikes (100)  
- Applying stop-loss methods based on percentage movements or ATR (average true range)

---

## **Key Insights**

- While most strategies worked similarly for both Nifty and BankNifty, there were some differences in effectiveness between the two instruments.
- Testing on different timeframes (e.g., 5-minute intervals) helped refine stop-loss mechanisms and strike selection.
- I found that certain strategies, especially those leveraging minimum premium logic, proved more effective in managing risk and optimizing returns.



