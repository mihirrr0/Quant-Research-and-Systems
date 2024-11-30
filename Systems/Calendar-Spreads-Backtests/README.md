# **Calendar Spreads**

A calendar spread is an options trading strategy where we simultaneously hold a **long and short position on the same underlying asset**, but with **different expiry dates**. Typically, this involves **buying a longer-term contract** while **selling a shorter-term contract** with the **same strike price**. 

## **Backtest Details**

### Data Used:
- Index options data for **weekly contracts** (Weeks I, II, III, IV) and **monthly contracts** (Months I, II).
- Different expiry dates were analyzed to evaluate performance.

## **Optimizations**

To refine this strategy, I conducted various tests to identify the setups with the best outcomes. Here are the different configurations and findings:

### **1. Standard Calendar Spread:**
- Strategy: **Short the current expiry contract** and **long the next expiry contract**.
- Tested on:
  - Weekly and monthly contracts.
  - Call options, put options, and combinations of both.
- **Observation**: The results for this setup were mostly flat or slightly negative.

### **2. Reverse Calendar Spread:**
- Strategy: **Short the next expiry contract** and **long the current expiry contract**.
- Similar testing methodology as the standard calendar spread.
- **Observation**: This variation performed better and warranted further exploration.

### **3. First Week vs. Third Week Spread:**
- Strategy: **Short first week expiry contract** and **long third week expiry contract**.
- Tested both the regular and reverse setups.
- Evaluated on calls, puts, and their combinations.

### **4. First Week vs. Fourth Week Spread:**
- Strategy: **Short first week expiry contract** and **long fourth week expiry contract**.
- Same testing methodology as above.

### **5. Second Week vs. Third Week Spread:**
- Strategy: **Short second week expiry contract** and **long third week expiry contract**.
- Similar testing approach.

### **6. Second Week vs. Fourth Week Spread:**
- Strategy: **Short second week expiry contract** and **long fourth week expiry contract**.
- Reverse setups were tested for all combinations as well.

---

### **Special Case Testing**

**8. Selecting Longer-Term Contracts Based on Shorter-Term Premiums:**
For this test:
- I based the strike price of the longer-term contract on the **premium of the shorter-term contract**.
- Strike prices were selected such that the premium of the longer-term contract was **a percentage (from 25% to 200%) of the shorter-term premium**.
- This process was applied to all variations of calendar spreads.

**9. Filtering Contracts by Premium:**
To ensure better-quality data:
- I excluded contracts with low premiums from the backtests. 
- This helped focus on more liquid and meaningful trades.

**10. Testing Opening Positions on Different Days:**
Separate backtests were conducted to evaluate performance based on the day of the week positions were opened.

---


