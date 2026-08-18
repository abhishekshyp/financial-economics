# Week 4 — Build Your Personal Portfolio

> You are handed ₹1 crore of other people's money and 85 stocks. Pick **exactly 25**, weight them so the portfolio earns the **most return per unit of risk**, and then watch it face the one judge that matters — the **live market**.

This assignment closes the two-week **Build Your Personal Portfolio** arc. Week 3 taught you to turn a price history into an annualised return, a volatility, and a reward-per-unit-of-risk score; the Week 4 workbook then showed how **correlation** bends portfolio risk below the weighted average and how **Solver** searches the weight space. Now you run the whole pipeline yourself, on real return data, under real constraints — and, unlike every assignment so far, your answer is scored **out-of-sample**.

---

## The mandate

IIT Roorkee has launched a mutual-fund scheme, and IITR management has appointed **you** as the fund manager. You have raised **₹1,00,00,000 (₹1 crore)** from retail investors, and now that money has to be **deployed in the equity market**.

You are given the **daily returns of 85 stocks** (`historicalStockReturns.csv`, symbols, **1,733 daily observations**, oldest date first). This is your **training set** — the only history you get to see before you build a portfolio.

Your job is to build the portfolio with the **maximum return/risk ratio**. But you cannot spread ₹1 crore across all 85 names — that is **over-diversification**. Nor can you bet it on a **handful** of stocks — that is **under-diversification**, where a single blow-up sinks the fund. Your experience says the sweet spot is **exactly 25 stocks**.

**Data:** [`historicalStockReturns.csv`](https://github.com/abhishekshyp/financial-economics/blob/main/Week4_BuildYourPersonalPortfolio/historicalStockReturns.csv) — in the Week 4 tutorial folder.

---

## The constraints

Your portfolio must satisfy **all three**:

1. **Cardinality.** Exactly **25 stocks** out of the 85 — no more, no fewer.
2. **Weight floor.** Every included stock gets a weight **wᵢ ≥ 0%**. (There is **no maximum** cap and **no other minimum** — you are free to choose how much beyond 0% any name gets.)
3. **Full investment.** The 25 weights **sum to 100%** (Σwᵢ = 1). No leverage, no cash drag, no short selling (wᵢ ≥ 0).

---

## The real test — live, next tutorial

The portfolio you build is fitted to the **training history**. But a fund manager is not paid for how well the past would have gone — only for what happens **next**. So your submitted weights will be run forward on **live / hold-out market returns in class next tutorial**, and the fund's value tracked from its ₹1 crore starting point.

- **Every valid submission earns +2 marks.**
- **The top 3 portfolios by live performance earn a further +2 marks.** *(Let's see by how much you can grow the ₹1 crore.)*

---

## Submission format

A single **`.csv` file with two columns**:

| Column A — `Symbol` | Column B — `Weight` |
|---|---|
| the stock symbol (e.g. `STK1042`) | its portfolio weight |
| … 25 rows total … | … must sum to 100% … |

- **Column A:** the 25 chosen stock symbols, exactly as they appear in the header.
- **Column B:** the weights — as decimals (`0.04`) or percentages (`4%`), stated clearly. **They must sum to 100%.**
- 25 rows of holdings (a header row is fine). No omitted names, no 26th line.

---

## Teams

Work **individually** — you are each running your own fund.

---

## What to submit

1. **The weights file** — the two-column `.csv` above. This is what gets run live.
2. **Your workings** — the Excel workbook or Python script/notebook that produced the weights.
3. **A short write-up (1–3 pages)** — your selection rule, the portfolio's annualised μ, σ and `S(w)`, the diversification and concentration diagnostics, the sub-window robustness check, and one paragraph on **why you expect this portfolio to survive out-of-sample**.

**State every assumption clearly.** A modest, well-argued portfolio you can defend beats an over-fitted one you cannot.

---

## Grading

- **+2 marks** for a valid submission (all three constraints satisfied, plus workings and write-up).
- **+2 marks** for a **top-3 live performance** next tutorial.

## Submission

- **Deadline:** before the next tutorial. The Google Drive folder closes at the deadline — **no late submissions and no alternative modes** (email, WhatsApp, Teams) will be accepted.
- **Naming convention:** `RollNumber_FullName.extension` (e.g. `21112001_AbhishekKashyap.csv`, `..._Portfolio.ipynb`, `..._Workbook.xlsx`). Submit the weights file as `RollNumber_FullName_Weights.csv`. If you submit multiple files, place them in a folder named `RollNumber_FullName/`.
- **Upload folder:** https://drive.google.com/drive/folders/1BfSc4kjbYR0chZ-s9zM_qmQM9XMktgKw?usp=sharing

---

*Figures in this brief are illustrative and for teaching only — not financial advice.*
