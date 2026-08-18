# Week 4 — Build Your Personal Portfolio

> From single-asset statistics to a constructed portfolio. This module turns a pile of daily prices into a working mean-variance workbook: it measures each asset's annualised return and risk, shows how **correlation** bends portfolio risk below the weighted average, and then uses **Excel Solver** to search the weight space for three named portfolios — the **minimum-variance**, the **maximum return-per-unit-of-risk**, and a **constrained** allocation that respects weight rules.

This is the second half of the two-week **Build Your Personal Portfolio** arc. Week 3 established the vocabulary — the asset universe, how a trade clears, and how a price history becomes an annualised return and a distribution — and closed on the observation that portfolio risk depends on the **correlation matrix**, not the zero-correlation shortcut. Week 4 pays that off. It is delivered as a single **transparent spreadsheet** (`excelReturnStatistics.xlsx`) whose every figure is a live formula, so students can open the hood, watch diversification work cell by cell, and run the optimiser themselves rather than read its output. Following the course rhythm, students first **replay** the return-and-risk mechanics from Week 3 on new data, the workbook then **formalises** correlation and optimisation, and the assignment applies the same machinery to a portfolio they build and defend.

---

## Contents

```
Week4_BuildYourPersonalPortfolio/
├── excelReturnStatistics.xlsx   # the transparent portfolio-construction workbook (8 sheets, live formulas)
└── README.md                    # this file
```

## Live access

- **Week 4 Workbook:** https://github.com/abhishekshyp/financial-economics/raw/main/Week4_BuildYourPersonalPortfolio/excelReturnStatistics.xlsx

*(The workbook downloads rather than rendering in the browser — Excel's Solver add-in is required for the optimisation sheets; see [Using the module](#using-the-module).)*

---

## What the file does

`excelReturnStatistics.xlsx` is a single workbook that walks the full construction pipeline top-down, from one asset's statistics to a Solver-optimised six-asset portfolio. It carries **two independent datasets** — a *single-stock* set for the intuition-building sheets and an *asset-class* set for the optimisation sheets — so the diversification lesson is taught first on securities a student recognises and then on the broad building blocks a real allocation actually uses.

| Sheet | Dataset | Purpose |
|---|---|---|
| **Daily** | NIFTY 50, daily | Recaps the Week 3 result on fresh data: average daily return × 252 and daily σ × √252 recover the annualised figures. |
| **Weekly** | NIFTY 50, resampled weekly | The same annualisation at a weekly frequency (× 52, × √52) — a sampling-frequency robustness check. |
| **Monthly** | NIFTY 50, resampled monthly | The same at monthly frequency (× 12, × √12); the three annualised returns should agree up to sampling noise. |
| **Data** | 5 stocks + Gold ETF, daily | Daily simple returns for SBILIFE, EICHERMOT, NESTLEIND, ETERNAL, GOLDBEES (plus NIFTY 50 as benchmark), and each asset's **annualised return, annualised σ, and return/risk**. |
| **Portfolio** | same five holdings | A **constrained, fixed-weight** portfolio: user weights, a ₹1,00,000 initial investment converted to share quantities, the daily portfolio value via `SUMPRODUCT`, and the resulting annualised return, risk, and return/risk — benchmarked against an equal-weighted portfolio (EWP) and NIFTY 50, with the portfolio's correlation to the index. |
| **Data2** | 6 asset-class proxies, daily from 2016 | Clean price history for the optimisation set: Nifty TRI, Midcap TRI, Smallcap TRI, GoldBeES, G-Sec, S&P 500. |
| **Correlation** | Nifty TRI + G-Sec | The **two-asset diversification demo**: portfolio risk computed *ignoring* correlation (a naïve weighted average) versus *with* correlation, and a scenario block that sweeps ρ ∈ {+1, 0, −1} to show the risk curve collapse. |
| **Optimal Risky Portfolio** | all 6 asset classes | The **mean-variance optimiser**: per-asset annualised return and σ, the variance–covariance matrix, the weight decision cells, and the portfolio summary — expected return (`SUMPRODUCT`), risk via the matrix form `√(wᵀΣw · 252)`, the Σw = 1 check, and return/risk — the objective and constraints Solver operates on. |

> **This is a template, by design.** On *Optimal Risky Portfolio* the **variance–covariance matrix** (`P11:U16`) and the **weight vector** (`P6:U6`) ship **empty**, and the ρ = +1/0/−1 block on *Correlation* is blank. Populating the matrix and running Solver **is the exercise** — the workbook is meant to be built, not merely read.

---

## The mathematics

Notation is standard: *r* a return, *E[·]* an expectation, *σ* a volatility, *ρ* a correlation, *w* a weight vector, **Σ** the annualised variance–covariance matrix. Daily statistics are annualised with a 252-trading-day convention throughout.

**Simple daily return and annualisation**

```
rₜ = Pₜ / Pₜ₋₁ − 1
μ_ann = mean(rₜ) · 252
σ_ann = stdev(rₜ) · √252
```
The asymmetry — mean scales with time, risk with its square root — is the reason a longer horizon improves the return/risk ratio even when nothing about the asset changes.

**Return per unit of risk (the workbook's scoring metric)**

```
Return/Risk = μ_ann / σ_ann
```
This is a Sharpe ratio under the **assumption rₑ = 0**; it is stated here explicitly because it makes the "maximum return/risk" portfolio the tangency portfolio of a zero-rate capital allocation line. With a non-zero risk-free rate the objective becomes `(μₚ − rₑ) / σₚ`.

**Two-asset portfolio return and risk**

```
E[rₚ] = w_A E[r_A] + w_B E[r_B]
σₚ    = √( w_A²σ_A² + w_B²σ_B² + 2 w_A w_B ρ σ_A σ_B )
```
The naïve "without-correlation" figure the workbook contrasts against is the weighted-average risk `σₚ,naïve = w_Aσ_A + w_Bσ_B`, which is exactly the ρ = +1 case. The diversification benefit is the wedge `σₚ,naïve − σₚ`, positive whenever ρ < 1.

For a 50/50 mix of two assets of equal volatility σ this collapses to `σₚ = σ · √((1 + ρ)/2)` — from σ at ρ = +1, to σ/√2 at ρ = 0, to 0 at ρ = −1.

**n-asset portfolio, matrix form** (the *Optimal Risky Portfolio* sheet)

```
E[rₚ] = wᵀ μ                         # SUMPRODUCT(returns, weights)
σₚ²   = wᵀ Σ w                       # MMULT(MMULT(w, Σ), TRANSPOSE(w))
σₚ    = √( wᵀ Σ w · 252 )            # array-entered; daily Σ annualised in the SQRT
```
where `Σᵢⱼ = ρᵢⱼ σᵢ σⱼ` and the diagonal `Σᵢᵢ = σᵢ²`. The quadratic form is the whole point of the module: as n grows, the n diagonal variance terms are swamped by the n(n−1) covariance terms, so **the correlation structure — not the individual volatilities — governs portfolio risk.**

**The three optimisation programs**

Minimum-variance portfolio:
```
min_w   wᵀ Σ w      s.t.  Σ wᵢ = 1   (, wᵢ ≥ 0 if long-only)
```

Maximum return/risk (tangency, rₑ = 0):
```
max_w   (wᵀ μ) / √(wᵀ Σ w)      s.t.  Σ wᵢ = 1   (, wᵢ ≥ 0)
```

Constrained / target-return portfolio:
```
min_w   wᵀ Σ w      s.t.  Σ wᵢ = 1,  wᵀ μ ≥ r*,  Lᵢ ≤ wᵢ ≤ Uᵢ
```
Each is a single Solver run: the objective cell is `σₚ²` or `Return/Risk`, the decision cells are `P6:U6`, and the constraints are entered in the Solver dialog. The min-variance and max-return/risk solves trace two named points on the efficient frontier; the constrained solve shows the frontier-relative cost of the weight rules.

---

## Using the module

**Open it.** Open `excelReturnStatistics.xlsx` in Excel (LibreOffice Calc opens the workbook and recalculates all formulas, but its solver is a separate add-in with a different dialog). The optimisation sheets need the **Solver add-in**: in Excel, *File → Options → Add-ins → Manage: Excel Add-ins → Go → tick Solver Add-in*.

**Build the covariance matrix.** On *Optimal Risky Portfolio*, fill `P11:U16` so that cell (i, j) = `COVARIANCE.S(returnsᵢ, returnsⱼ)` over the daily return ranges (the diagonal is each asset's daily variance). Keep it in **daily** units — the portfolio-risk formula annualises it inside the `SQRT` by the × 252 factor.

**Enter the risk formula.** `P20` holds the array formula `=SQRT(MMULT(MMULT(P6:U6, P11:U16), TRANSPOSE(P6:U6))*252)`. In legacy Excel confirm it with **Ctrl+Shift+Enter**; in dynamic-array Excel a plain Enter suffices.

**Run Solver — three times, once per portfolio.**
1. **Minimum variance** — Set Objective: `σₚ` (or `σₚ²`) → *Min*; By Changing: `P6:U6`; Subject To: `SUM(P6:U6) = 1` (add `P6:U6 ≥ 0` for long-only). Use the **GRG Nonlinear** engine.
2. **Maximum return/risk** — Set Objective: `Return/Risk` (`P22`) → *Max*; same decision cells and Σw = 1 constraint.
3. **Constrained** — start from either solution, then add the weight rules the assignment specifies (e.g. `U6 ≤ 0.20`, `T6 ≥ 0.10`, or a floor/cap per asset) and re-solve. Record the return/risk you give up relative to the unconstrained max — that number is the *price* of the constraint.

**Read the diagnostics.** `Total Weight` (`P21`) must equal 1 on every solve; if Solver reports no feasible solution, the constraints are contradictory (most often a set of caps that cannot sum to 1). Compare the three solutions' `(return, risk)` pairs — they are three points on the same efficient frontier.

---

## Readings & references

### Suggested textbook chapters

**Bodie, Kane & Marcus — *Investments*** (chapter titles are stable across recent editions; match by title if your numbering differs):

| Chapter | What it supports in this module |
|---|---|
| **Ch. 6 — Capital Allocation to Risky Assets** | The risky/risk-free split and the reward-to-variability (Sharpe) ratio underlying the return/risk objective. |
| **Ch. 7 — Optimal Risky Portfolios** | The core of the week: two-asset portfolio variance, the covariance/correlation matrix, the efficient frontier, and the minimum-variance and tangency portfolios that Solver reproduces. |
| **Ch. 8 — Index Models** | Why estimating a full covariance matrix is fragile at scale, and the single-index shortcut that motivates factor structure. |
| **Ch. 5 — Risk, Return, and the Historical Record** *(recap)* | Annualisation of returns and volatility — the machinery the Daily/Weekly/Monthly sheets re-derive. |

### Foundational papers

- **Markowitz, H. (1952).** "Portfolio Selection." *Journal of Finance*, 7(1), 77–91. — the paper that defines the mean-variance problem this workbook solves.
- **Markowitz, H. (1959).** *Portfolio Selection: Efficient Diversification of Investments.* Cowles Foundation / Wiley. — the book-length treatment of the frontier and the covariance form of risk.
- **Sharpe, W. F. (1966).** "Mutual Fund Performance." *Journal of Business*, 39(1), 119–138. — the reward-to-variability ratio the return/risk cell approximates.
- **Sharpe, W. F. (1963).** "A Simplified Model for Portfolio Analysis." *Management Science*, 9(2), 277–293. — the single-index model behind BKM Ch. 8, and the answer to the covariance-matrix estimation problem.
- **Michaud, R. O. (1989).** "The Markowitz Optimization Enigma: Is 'Optimized' Optimal?" *Financial Analysts Journal*, 45(1), 31–42. — why unconstrained mean-variance weights are error-maximising, and the case for the constraints in the third solve.
- **DeMiguel, V., Garlappi, L., & Uppal, R. (2009).** "Optimal Versus Naive Diversification: How Inefficient Is the 1/N Portfolio Strategy?" *Review of Financial Studies*, 22(5), 1915–1953. — the empirical benchmark for the equal-weighted comparison on the *Portfolio* sheet.

**Data sources.** NSE / NIFTY Indices (Nifty 50, Midcap, Smallcap TRI), AMFI and ETF NAVs (GoldBeES), CCIL / index providers (G-Sec), and S&P Dow Jones Indices (S&P 500), converted to INR where noted.

---

*Part of the personal-finance and financial-economics course. Figures in this module are illustrative, computed in-sample on historical data, and for teaching only — not financial advice.*
