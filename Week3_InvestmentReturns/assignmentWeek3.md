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

You have **₹1,00,000** and you know your own risk appetite (use your Week-2 risk score, or state one).

1. **Assign weights** `w_i` across the seven classes (`Σ w_i = 1`, no shorting unless you justify it). Tie the weights explicitly to your risk score — a lower score should tilt toward FDs/G-secs; a higher score toward mid/small cap and equities.
2. **Portfolio expected return:** `μ_p = Σ w_i μ_i`.
3. **Portfolio risk:** `σ_p = √( Σ_i Σ_j w_i w_j σ_i σ_j ρ_ij )`. You will need the **correlation matrix** `ρ_ij` — estimate it from the same return series and include it in your submission. (Assuming zero correlation is *wrong* and will overstate diversification — show the real matrix.)
4. **Reward per unit of risk:** report `μ_p / σ_p`. Do the same for each individual asset so you can compare.

---

## Answer these

- Which single asset class offers the **best standalone reward-per-unit-of-risk**? Is it the one with the highest return?
- Does your **portfolio** achieve a better reward/risk ratio than its best individual component? If so, where does the improvement come from — and which correlations did the heavy lifting?
- How much does your answer move if you **switch the sample window** (e.g. include vs. exclude the 2020 crash)? What does that fragility tell you about estimating μ and σ from history?
- Does adding the **S&P 500** help or hurt a rupee investor once FX risk is included?

---

## How to do it

Pick **one** — all are equally acceptable; choose the one that lets you think best.

- **Python** — `yfinance` / CSV downloads + `pandas` / `numpy`; compute returns, the covariance matrix, and the return-vs-risk chart from scratch.
- **Excel** — a transparent workbook: returns as live formulas, `STDEV`/`AVERAGE` for μ and σ, `CORREL` for the matrix, and a scatter chart. Keep every figure a formula, not a hard-coded number.

**Cite every data source** — include the exact links / tickers and the download date. Reproducibility is graded.

---

## Teams

Work **individually or in a team of up to 3**. All members contribute across Parts A and B.

---

## What to submit

1. **Your workings** — the Python notebook / script or the Excel workbook.
2. **A short write-up (1–3 pages)** — the seven μ/σ estimates, the return-vs-risk chart, your correlation matrix, your chosen weights and the reasoning that ties them to your risk score, and your portfolio's μ, σ, and reward/risk ratio. Close with one paragraph answering: *did diversification actually pay, and why?*

**State every assumption clearly.** A modest analysis with honest, well-argued assumptions beats an elaborate one you can't defend.

Naming convention: `RollNumber_FullName`. Submit before the next tutorial.
