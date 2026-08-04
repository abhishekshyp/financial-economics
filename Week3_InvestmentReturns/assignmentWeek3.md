# Week 3 — Investments and Investment Returns

> Characterise the different asset classes on the **return–risk plane**, then use what you find to **construct a portfolio that is genuinely yours** — and report how much reward it earns per unit of risk.

This assignment turns the tutorial's concepts — expected returns, annualised returns, the return *distribution*, and reward-per-unit-of-risk — into a hands-on measurement exercise. You will pull real historical data for seven asset classes, estimate each one's expected return and risk, place them on a single return-vs-risk chart, and then allocate ₹1,00,000 across them according to *your own* risk appetite.

---

## The seven asset classes

Pick one liquid, investable proxy for each class, and **state which proxy you used and why**. Suggested proxies (you may substitute with justification):

| Asset class | Suggested proxy | Where to get data |
|---|---|---|
| **Gold ETF** | Nippon / SBI Gold ETF, or domestic gold price (₹/10g) | niftyindices.com, World Gold Council |
| **Large cap** | NIFTY 50 TRI | niftyindices.com |
| **Mid cap** | NIFTY Midcap 150 TRI | niftyindices.com |
| **Small cap** | NIFTY Smallcap 250 TRI | niftyindices.com |
| **S&P 500 (USA)** | S&P 500 TR index | Yahoo Finance (`^SP500TR`) |
| **Government bonds** | 10-yr G-sec yield | RBI, NSE, AMFI |
| **Fixed deposit** | Representative 1-yr FD rate (treat as ~risk-free, σ ≈ 0) | Bank published rates |

> **Use total-return (TRI) series wherever possible** — TRI indices accounts for dividends and bonuses. If you can only get a normal price index, it is totally fine.

---

## Part A — Characterise each asset class

For **every** asset class, compute and report:

1. **A periodic return series.** Choose daily *or* weekly *or* monthly returns and be consistent. Use simple returns `r_t = (P_t − P_{t−1}) / P_{t−1}` (or log returns `ln(P_t/P_{t−1})`).
2. **Expected (average) return**, annualised: `μ_ann = μ_period × N` (`N` = 252 daily, 52 weekly, 12 monthly).
3. **Risk (volatility)**, annualised: `σ_ann = σ_period × √N`. Remember the asymmetry — **mean scales with time, risk with √time**.
4. **The return-vs-risk scatter** — plot all seven points with σ on the x-axis and μ on the y-axis. This is your empirical *opportunity set*.

**Fix your assumptions and keep them common across assets:**
- **Sample window** — pick one (e.g. last 10 years, or last 5) and use the *same* window for all assets so they are comparable. State it.
- **Currency** — the S&P 500 in USD is not directly comparable to a rupee investor's experience. Either (a) convert to ₹ using the INR/USD series (this adds FX return *and* FX risk), or (b) keep it in USD and flag the mismatch. Justify your choice.

---

## Part B — Build your portfolio

You have just graduated from IIT Roorkee with ₹1,00,000 in savings. You know your own risk appetite. Ten asset classes are open to you. Allocate, score your reward-per-unit-of-risk — then find out whether your portfolio survives a crisis.

Play the game: https://abhishekshyp.github.io/financial-economics/Week3_InvestmentReturns/portfolioChallenge.html#1

---

## Answer these

- Which single asset class offers the **best standalone reward-per-unit-of-risk**? Is it the one with the highest return?
- Does your **portfolio** achieve a better reward/risk ratio than its best individual component? If so, where does the improvement come from — and which correlations did the heavy lifting?
- How much does your answer move if you **switch the sample window** (e.g. include vs. exclude the 2020 crash)? What does that fragility tell you about estimating μ and σ from history?
- Does adding the **S&P 500** help or hurt a rupee investor once FX risk is included?

---

## How to do it

Pick **one** — all are equally acceptable; choose the one that lets you think best.

- **Excel** — a transparent workbook: returns as live formulas, `STDEV`/`AVERAGE` for μ and σ, `CORREL` for the matrix, and a scatter chart. Keep every figure a formula, not a hard-coded number.

**Cite every data source** — include the exact links / tickers and the download date. Reproducibility is graded.

---

## Teams

Work **individually**.

---

## What to submit

1. **Your workings** — Excel workbook.
2. **A short write-up (1–3 pages)** — the seven μ/σ estimates, the return-vs-risk chart, your correlation matrix, your chosen weights and the reasoning that ties them to your risk score, and your portfolio's μ, σ, and reward/risk ratio.

**State every assumption clearly.** A modest analysis with honest, well-argued assumptions beats an elaborate one you can't defend.

---

## Grading

This is a **completion grade — 2 marks for submitting.** Complete all the tasks, and the marks are yours; there's no quality scoring.

## Submission

- **Deadline:** before the next tutorial.
- **Naming convention:** `RollNumber_FullName.extension` (e.g. `21112001_AbhishekKashyap.ipynb`, `..._RiskScore.xlsx`, `..._Tool.html`). Submit the coin-flip result as `RollNumber_FullName_Coin.pdf` (or the site's native file). For teams, submit one set under the team lead's `RollNumber_FullName` and list all members on page 1.
- **Upload folder:** https://drive.google.com/drive/folders/1iGKPvFCisDUvshyZjz474NDy_SrkOCTv?usp=sharing

---

*Figures in this brief are illustrative and for teaching only — not financial advice.*
