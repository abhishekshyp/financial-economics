# Week 6 · Tutorial 6 · Portfolio Rebalancing

## Overview

This tutorial covers how and when to rebalance a multi-asset portfolio. It uses a three-asset, equal-weighted portfolio of Nifty 50, S&P 500 and a Gold ETF, held from 4 Jan 2010 to 28 Aug 2026.

Topics covered:

1. **The problem.** An equal-weighted portfolio of ₹1,00,000 invested on 4 Jan 2010.
2. **Why portfolios drift.** The drift equation and the buy-and-hold weights on 28 Aug 2026.
3. **Anatomy of a rebalancing rule.** The three decision variables: frequency, threshold and target weights.
4. **Calendar-based rebalancing.** Mechanics, pros and cons, with a worked example.
5. **Threshold-based rebalancing.** Mechanics, pros and cons, with a worked example.
6. **Calendar + threshold (hybrid).** Mechanics, with a worked example.
7. **The game.** A group exercise on the same data set.

## Folder contents

| File | Description |
|---|---|
| `Week6_PortfolioRebalancing.html` | Tutorial slides (9 slides) |
| `portfolio-rebalancing.xlsx` | Daily closing prices and the buy-and-hold portfolio |
| `README.md` | This file |

## Data

The workbook `portfolio-rebalancing.xlsx` contains three sheets:

| Sheet | Contents |
|---|---|
| `data` | Daily closing values of `NIFTY50`, `SPUS500` and `GOLDETF`, 4 Jan 2010 – 28 Aug 2026 (4,133 trading days) |
| `portfolio` | Buy-and-hold portfolio: value of each holding, total portfolio value, daily returns and summary statistics |
| `weights` | Daily weight of each asset in the buy-and-hold portfolio |

## Key formula

The weight of asset *i* evolves as:

```
w(i, t+1) = w(i, t) × (1 + r_i) / (1 + r_p),     where r_p = Σ w(i, t) × r_i
```

---

## Group assignment: The game

The class is divided into groups of 4–5 students. All groups use the same data from `portfolio-rebalancing.xlsx`.

### Common setup

- Initial capital is ₹1,00,000, invested at 33.33% in each asset at the close of **4 Jan 2010**.
- The target weight is 33.33% for each asset.
- Use closing prices from the `data` sheet.
- The end date is **28 Aug 2026**.

### Task 1 (2 marks per member)

Each group is assigned one strategy:

| Group | Strategy |
|---|---|
| A | Monthly (calendar) |
| B | Quarterly (calendar) |
| C | Yearly (calendar) |
| D | 5% threshold, checked daily |

Rules:

- **Calendar strategies.** Rebalance all three assets to 33.33% at the close of the last trading day of each month, quarter or year in the data. Each scheduled date counts as one rebalancing event.
- **Final period.** The incomplete final period (Aug 2026, Q3 2026, or the year 2026) is not rebalanced.
- **Threshold strategy.** At every daily close, check the weights. If any weight is outside **28.33%–38.33%**, rebalance all three assets back to 33.33% at that close.
- **Costs.** There are no transaction costs in Task 1.

### Task 2 (3 marks per member)

All groups use the same strategy for Task 2:

- **Check dates.** Check the weights at each quarter-end, i.e. the last trading day of each quarter in the data.
- **Trade condition.** Rebalance only if any weight is outside **28.33%–38.33%** on that date.
- **Transaction cost.** The cost is 0.5% of the amount sold.
- **Tax.** GST is 18% of the transaction cost.
- **When costs are deducted.** The total cost (transaction cost + GST) is deducted from the portfolio value **before** rebalancing. Each asset is then set to V′/3.

Worked example of the cost calculation:

| Step | Amount (₹) |
|---|---|
| Holdings: Nifty · S&P · Gold (weights 30% · 40% · 30%) | 33,000 · 44,000 · 33,000 |
| Portfolio value V | 1,10,000 |
| Target per asset, V/3 | 36,666.67 |
| Amount sold (S&P) | 44,000 − 36,666.67 = 7,333.33 |
| Transaction cost (0.5%) | 36.67 |
| GST (18% of cost) | 6.60 |
| Total cost | 43.27 |
| V′ = V − total cost | 1,09,956.73 |
| New value per asset, V′/3 | 36,652.24 |

### What to submit

For each task, submit:

1. The **final portfolio value on 28 Aug 2026**, rounded to the nearest rupee.
2. The **number of rebalancing events**.
3. The **Excel sheet** containing your calculations.

Suggested file name: `Group<Letter>_Week6_Task<1 or 2>.xlsx` (for example, `GroupA_Week6_Task1.xlsx`).

### Submission link

**Submit your group assignment here:**
https://drive.google.com/drive/folders/1dHCyJPZnJT2nC4J7t-tbq9x-VpwFUJVi

### Marking

| Task | Marks per member | Condition |
|---|---|---|
| Task 1 | 2 | Final value and number of events match the answer key |
| Task 2 | 3 | Final value and number of events match the answer key |

If an answer does not match, the group receives zero marks for that task.

---

## References and reading

- Zhang, Y., Ahluwalia, H., Ying, A., Rabinovich, M., & Geysen, A. (2022). *Rational rebalancing: An analytical approach to multiasset portfolio rebalancing decisions and insights*. The Vanguard Group.
- Perold, A. F., & Sharpe, W. F. (1988). Dynamic strategies for asset allocation. *Financial Analysts Journal*, 44(1), 16–27.
- Zilbering, Y., Jaconetti, C. M., & Kinniry, F. M., Jr. (2015). *Best practices for portfolio rebalancing*. The Vanguard Group.
- Kritzman, M., Myrgren, S., & Page, S. (2009). Optimal rebalancing: A scalable solution. *Journal of Investment Management*, 7(1), 9–19.
- Donohue, C., & Yip, K. (2003). Optimal portfolio rebalancing with transaction costs. *The Journal of Portfolio Management*, 29(4), 49–63.
