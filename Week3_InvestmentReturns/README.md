# Week 3 — Investments and Investment Returns

> From *"where do I put my savings?"* to a measured view of return and risk — the asset universe, the participants and regulators that make a market, how a trade actually happens, and how to turn a price history into an annualised return, a distribution, and a reward-per-unit-of-risk score.

This is the first half of the two-week **Build Your Personal Portfolio** arc. It lays the groundwork before optimisation: what **real** and **financial** assets are, the participants and intermediaries that make a market work, how the **primary** and **secondary** markets differ — and, at the analytical core, how investment returns are **measured**, **annualised**, and understood as a *distribution* rather than a single number. Following the course rhythm, students first **play** the portfolio challenge to build intuition, the lecture slides then formalise the concepts, and the assignment applies them to real market data.

---

## Contents

```
Week3_InvestmentReturns/
├── index.html                     # the portfolio challenge — the "Play" tool
├── sl_InvestmentsAndReturns.html  # interactive lecture slides
├── assignmentWeek3.md             # week 3 assignment
└── README.md                      # this file
```

## Live access

- **Week 3 Slides:** https://abhishekshyp.github.io/financial-economics/Week3_InvestmentReturns/sl_InvestmentsAndReturns#1
- **Week 3 Tool:** https://abhishekshyp.github.io/financial-economics/Week3_InvestmentReturns/

---

## What each file does

### `index.html` — the portfolio challenge (Play)

The hands-on opener. You have just graduated from **IIT Roorkee** with **₹1,00,000** in savings and know your own risk appetite. Ten asset classes are open to you: **allocate** across them, **score** your portfolio's reward-per-unit-of-risk, and then **stress-test** whether the allocation survives a crisis. It builds the intuition — the return–risk trade-off and the value of diversification — that the slides then explain formally.

### `sl_InvestmentsAndReturns.html` — lecture slides

The self-contained lecture deck (18 slides), built on the course slide chassis. It moves top-down from *why* we invest to *how* we measure what we get back:

- **The asset universe** — real vs. financial assets, and a taxonomy (fixed income, equity, collective investments, commodity-linked) with Indian examples, plus a quick classification quiz.
- **The market** — participants and the case for regulation, an **ownership-of-the-Indian-market** pie chart (NSE Market Pulse, March 2026), SEBI and the chain of intermediaries, and primary vs. secondary markets with an **animated A/B order-match** that shows how opposing views become an executed trade.
- **Returns, formally** — absolute and average returns; **annualisation** (mean × N, risk × √N) via a live daily→annual converter; the **return distribution** with an interactive bell curve, 95% confidence interval, and a **reward-per-unit-of-risk** (μ ÷ σ) readout; and strategic asset allocation across portfolio types.

*Technical note:* the slides load Chart.js from a CDN, so the page needs an internet connection to render the charts. It deploys as-is to GitHub Pages. Navigate with **← →**, press **O** for the slide overview and **F** for fullscreen.

### `assignmentWeek3.md` — the assignment

The graded take-home. Students pull real historical data for seven asset classes (Gold ETF, large/mid/small cap, S&P 500, G-secs, fixed deposits), estimate each one's **annualised return and risk**, place them on the **return-vs-risk plane**, and then construct a **personal portfolio** — computing portfolio return, portfolio risk (via the correlation matrix, not the zero-correlation shortcut), and the reward/risk ratio. Every data source must be cited and every assumption stated.

---

## Concepts covered

- Real vs. financial assets; the asset taxonomy (debt, equity, collective, commodity-linked).
- Market participants, the rationale for regulation, **SEBI**, and the intermediary chain (exchanges, brokers, depositories, DPs, clearing corporations, rating agencies).
- **Primary vs. secondary markets**, the IPO, and price discovery through order matching.
- **Return arithmetic:** absolute return, expected (average) return, and annualisation — with the key asymmetry that **mean scales with time, risk with √time**.
- The **normal distribution** of returns, confidence intervals, and **reward-per-unit-of-risk**.
- **Strategic asset allocation** across conservative-to-aggressive portfolio types.

---

## References & data sources

- **Investments** — Bodie, Kane & Marcus (Ch. 1–3 & 5).
- **Zerodha Varsity** — *Regulators*; *Financial Intermediaries*; *The IPO Markets, Part 2*.
- **NSE, Market Pulse (March 2026)** — ownership of Indian listed equity.
- **Investopedia / Peter Gratton** — *Strategic Asset Allocation: Definition & Example*.
- **Market data:** NSE, BSE, NIFTY Indices, AMFI, Yahoo / Google Finance, Screener, Tijori, TradingView.

---

## Submission

See **`assignmentWeek3.md`** for the full brief. Submit **before the next tutorial** to the Week-3 folder in the course submission drive, using the naming convention `RollNumber_FullName.extension` (e.g. `22617001_AbhishekKashyap.ipynb`). Teams of up to 3 are allowed; list every member's name and roll number on the first page.

---

*Figures in this module are illustrative and for teaching only — not financial advice.*
