# PSAR Index Options

- The **Parabolic SAR (PSAR)** indicator is used to form a curve made of small dots positioned either above or below the price of an asset. When these dots are below the price, they signify an upward trend and act as a support/trailing stop. Conversely, when the price drops below the dots, it triggers stop-losses, sell orders, or short-sell signals.

- The dots move based on price movements, which provides trading cues:
  - If **PSAR is above the price**, I would short the **ATM CALL option**.
  - If **PSAR is below the price**, the strategy calls for shorting the **ATM PUT option**.


### Objective:
The primary goal of this strategy is to identify trends using the **PSAR (Parabolic SAR)** indicator on the following indices:  
- **Bank Nifty Weekly Options**  
- **Nifty Weekly Options**  
- **Nifty Monthly Options**  

---

## Bank Nifty Weekly  
**Backtest Results:**  
- A backtest with an acceleration factor of 0.015 was performed.  
- **CAR (Compounded Annual Returns):** 22.40%  
- **MDD (Maximum Drawdown):** -9.69%  
- **Trading Edge (TE):** 8.54%  

[![Screenshot-2024-11-29-at-6-20-19-AM.png](https://i.postimg.cc/K8JLLcb0/Screenshot-2024-11-29-at-6-20-19-AM.png)](https://postimg.cc/75Jfrkfz)

### Optimizations:
- The analysis used data from **01-06-2016 to 30-11-2022**, sourced from custom-built SQL database.  
- I optimized the system for both in-sample and out-of-sample periods, experimenting with acceleration factors ranging from **0.005 to 0.04**. 
[![Screenshot-2024-11-29-at-6-22-10-AM.png](https://i.postimg.cc/HnyRcP7t/Screenshot-2024-11-29-at-6-22-10-AM.png)](https://postimg.cc/V0zD2ggS) 
- The strategy was tested under two specific conditions:  
  1. Trading the **next expiry on the expiry day**.  
  2. Trading the **next expiry after 3:20 PM on expiry day**.
[![Screenshot-2024-11-29-at-6-22-56-AM.png](https://i.postimg.cc/RhKpV6js/Screenshot-2024-11-29-at-6-22-56-AM.png)](https://postimg.cc/CnMsc1Mk)  
  

**Key Findings:**  
- As the acceleration factor increases, the number of trades also rises, which reduces the trading edge due to transaction costs.  
- Combining the equity curves from five different systems (acceleration ranging from 0.005 to 0.025) showed improved performance.  

[![Screenshot-2024-11-29-at-6-24-07-AM.png](https://i.postimg.cc/bNRLCh8t/Screenshot-2024-11-29-at-6-24-07-AM.png)](https://postimg.cc/Vddjv2Jf) 

 
**Conclusion:**  
I found it more effective to place trades **after 3:20 PM** to allow current expiry options to expire worthless and the lower volatility impact as a result.

---

## Nifty Weekly  
**Data Source:**  
- Data was extracted from Nifty Weekly databases for the period **11-02-2019 to 30-11-2022**.

**Backtest Results:**  
- **CAR:** Ranged from **16.91% to 17.56%**.  
- **Drawdown:** Daily drawdowns remained within acceptable limits.  

[![Screenshot-2024-11-29-at-6-26-18-AM.png](https://i.postimg.cc/sD0GD64L/Screenshot-2024-11-29-at-6-26-18-AM.png)](https://postimg.cc/dLrV59XR) 

**Observations:**  
- Similar optimizations were performed as with Bank Nifty, though the shorter backtest time frame limits the robustness of the results.  

[![Screenshot-2024-11-29-at-6-27-28-AM.png](https://i.postimg.cc/Kj3S78CB/Screenshot-2024-11-29-at-6-27-28-AM.png)](https://postimg.cc/QKDyhh8d)

---

## Nifty Monthly  
**Backtest Period:**  
- From **04-01-2011 to 30-11-2022**, I tested this strategy with an acceleration factor of **0.015**.

**Results:**  
- **CAR:** 8.20%  
- **MDD:** -9.36%  
- **TE:** 3.20%  

[![Screenshot-2024-11-29-at-6-28-17-AM.png](https://i.postimg.cc/qB2zdBNz/Screenshot-2024-11-29-at-6-28-17-AM.png)](https://postimg.cc/z3XJCrSr) 

### Optimizations:
- I conducted both in-sample and out-of-sample optimizations and compared the results with weekly data included.

[![Screenshot-2024-11-29-at-6-30-51-AM.png](https://i.postimg.cc/rpFM7cvR/Screenshot-2024-11-29-at-6-30-51-AM.png)](https://postimg.cc/cvjpnq1d)

- Adding **Bank Nifty Out-of-the-Money (OTM) hedges** at varying levels (1%-5%) significantly improved performance.  
  - At 5% OTM, CAR increased to **16.6%**, and drawdowns were minimized.  

[![Screenshot-2024-11-29-at-6-32-14-AM.png](https://i.postimg.cc/9MdbT5Q1/Screenshot-2024-11-29-at-6-32-14-AM.png)](https://postimg.cc/wyBD8rJs) 

**Overnight Protection:**  
- Testing overnight OTM protection for Bank Nifty showed even better results, with the highest CAR of **18.8%** achieved at 5% OTM.  

[![Screenshot-2024-11-29-at-6-32-59-AM.png](https://i.postimg.cc/gkCw9wDX/Screenshot-2024-11-29-at-6-32-59-AM.png)](https://postimg.cc/JGQ7ZzSM)




