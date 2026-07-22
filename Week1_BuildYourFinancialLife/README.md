# Week 1 — Build Your Financial Life

> An interactive life-cycle finance model that turns personal inputs into a full lifetime of income, consumption, saving, and wealth — and uses it to teach the Life-Cycle Hypothesis, the Permanent Income Hypothesis, human vs. financial capital, and the time value of money. 

This is the opening module of the course. A student enters a handful of assumptions about their career and spending, and the model projects their entire financial life year by year — from the first salary to a bequest at life's end — exposing the core identities of personal finance and the classical consumption theories that explain them. It ships in two forms: a self-contained **web app** for exploration and demonstration, and a **transparent spreadsheet** for inspecting the mechanics formula by formula.

---

## Contents

```
week1-build-your-financial-life/
├── index.html                  # interactive single-file web app
├── financial-life-model.xlsx   # live spreadsheet model (formulas, not hardcoded)
├── sl_FinancialLifeModel.html  # interactive lecture slides
├── assignmentWeek1.md          # week 1 assignment
└── README.md                   # this file
```

## Live access
Week 1 Slides: https://abhishekshyp.github.io/financial-economics/Week1_BuildYourFinancialLife/sl_FinancialLifeModel#1

Week 1 Tool: https://abhishekshyp.github.io/financial-economics/Week1_BuildYourFinancialLife/

---

## What the two files do

The two artifacts implement the **same model**. They serve different pedagogical purposes: the app builds intuition and is ideal for live demonstration; the spreadsheet makes every calculation auditable and is ideal for homework and "open the hood" sessions.

### `index.html` — interactive web app

A single, self-contained HTML file (no build step, no server). A student adjusts the eight inputs and the model recomputes instantly, presenting:

- **Eight headline outputs** as cards (lifetime income, consumption, savings, their present values, retirement corpus, total taxes).
- **An accounting-identity reconciliation table** showing that gross income = taxes + consumption + savings, exactly.
- **Retirement diagnostics** — corpus adequacy, bequest or depletion age, average saving rate, borrowing years, crossover age.
- **Four charts**: (i) human capital vs. financial capital and the *crossover* point; (ii) income, consumption, and saving over the life cycle; (iii) actual consumption vs. the *permanent-income* benchmark; (iv) the net-worth "hump."
- **A nominal / real toggle** so students can see the same life in current rupees and in today's purchasing power.
- **A PDF report export** capturing inputs, assumptions, all outputs, the year-by-year ledger, and the charts — optionally stamped with a student name/roll number.

*Technical note:* charts and PDF export load small libraries (Chart.js, jsPDF) from a CDN, so the page needs an internet connection to render fully. It deploys as-is to GitHub Pages.

### `financial-life-model.xlsx` — the transparent model

A five-sheet workbook where **every figure is a live formula** driven by the input cells — change an assumption and the whole model recalculates.

| Sheet | Purpose |
|---|---|
| **Inputs** | The 8 inputs + 4 assumptions in editable (yellow) cells, then a derived block (working years, first- and final-year consumption, human capital, permanent income, real rates) computed by formula, with a documented notes panel. |
| **Summary** | The eight outputs in *nominal / real / present-value* columns, plus a retirement-and-diagnostics block (corpus, bequest, depletion age, saving rate, crossover age). |
| **Charts** | The four life-cycle charts. |
| **Projection** | The year-by-year engine: age, phase, gross, tax, post-tax, consumption, savings, wealth, human & financial capital, discount/deflation factors, permanent income. |
| **Checks** | Five accounting/finance identities computed live, each showing a residual ≈ 0 and an OK/CHECK status — the model audits itself. |

---

## Course content

This module covers the following concepts, each made concrete by a specific feature of the model:

- **Income, consumption, and savings** as flows, and the accounting identity that binds them.
- **The time value of money** — compounding a saving stream over a multi-decade horizon, and discounting future flows to a present value.
- **Nominal vs. real values** and the **Fisher relation** — why a large future rupee figure shrinks in today's purchasing power, and why present value is invariant to the nominal/real framing.
- **Human capital vs. financial capital** — labour income as the present value of future earnings, its depletion with age, and the **crossover** at which accumulated savings overtake remaining earning power.
- **The Life-Cycle Hypothesis** (Modigliani–Brumberg) — saving during working years to fund a consumption "hump" that outlives income.
- **The Permanent Income Hypothesis** (Friedman) — consumption as a function of lifetime, not current, resources, and the idea of consumption smoothing.
- **Retirement adequacy** — building a corpus, drawing it down in real terms, and the risk of depletion vs. leaving a bequest.
- **Model literacy** — reading a projection critically and interrogating its assumptions (see *Limitations*).

---

## Learning outcomes

By the end of this module, a student should be able to:

1. **Construct** a lifetime cash-flow projection from a small set of personal assumptions and explain each mechanical step.
2. **Distinguish** nominal from real magnitudes, convert between them, and state why present value is framing-invariant (the Fisher argument).
3. **Interpret** human capital as the present value of future earnings and explain why the human-to-financial capital crossover is the central event of a saver's life.
4. **Apply** the Life-Cycle and Permanent Income Hypotheses to predict how consumption and saving should behave across the life cycle, and compare that benchmark to an actual (non-smoothed) consumption path.
5. **Assess** retirement adequacy — whether a corpus sustains a target lifestyle, and how sensitive the answer is to growth, return, and inflation assumptions.

---

## The model at a glance

### Inputs (student-controlled)

| Input | Default | Meaning |
|---|---|---|
| Starting income age | 23 | Age at first salary |
| Yearly income (CTC, gross) | ₹12,00,000 | Gross annual compensation |
| Tax rate | 15% | Effective rate on income |
| Income growth rate | 8% | Annual nominal raise |
| Consumption rate (year 1) | 70% | Share of *post-tax* income consumed in year 1 |
| Expense growth rate | 7% | Annual growth of consumption |
| Return on savings | 9% | Nominal, untaxed |

### Assumptions (editable, but fixed by default)

| Assumption | Default | Rationale |
|---|---|---|
| Retirement age | 60 | No labour income thereafter |
| Life expectancy | 85 | Consumption funded to age 84 |
| Inflation (CPI) | 6% | Deflator for real values |
| Discount rate | 9% | A 60:40 portfolio: 0.6 × 11% equity + 0.4 × 6% debt |

### Core mechanics

With age index $t = 0, 1, \dots$ (age $= \text{startAge} + t$), working years $N = \text{retireAge} - \text{startAge}$:

| Quantity | Definition |
|---|---|
| Gross income | $Y_t = \text{CTC}\,(1+g_\text{inc})^t$ |
| Post-tax income | $YD_t = Y_t(1-\tau)$ |
| Consumption (working) | $C_t = C_0(1+g_\text{exp})^t,\quad C_0 = c\cdot\text{CTC}\,(1-\tau)$ |
| Saving (residual) | $S_t = YD_t - C_t$ (may be negative → borrowing) |
| Wealth | $W_t = W_{t-1}(1+r) + S_t,\quad W_{-1}=0$ |

The **accounting identity** $Y_t = \text{Tax}_t + C_t + S_t$ holds every year by construction.

**Two phases.** During *accumulation* (working years) the household earns, consumes, and saves the residual. During *decumulation* (retirement to end of life) there is no labour income; consumption holds the **final working-year lifestyle constant in real terms** (grows at CPI), funded by drawing down the corpus.

**Human capital** at age $i$ is the present value of remaining post-tax earnings:

```math
HC_i = \sum_{k=i}^{N-1} \frac{YD_k}{(1+d)^{\,k-i}}
```

**Permanent income** is the level *real* annuity whose present value equals lifetime resources $HC_0$ over the full horizon $T = \text{lifeExp} - \text{startAge}$ — Friedman's benchmark for what smoothed consumption "should" be.

### Outputs

Eight headline figures (lifetime income, consumption, savings, each in nominal and present-value terms; retirement corpus; total taxes), plus diagnostics: **crossover age** (financial capital ≥ human capital), **depletion age** or **bequest**, average saving rate, and borrowing years.

**Baseline result (default inputs):** 37 working years; lifetime income ₹24.37 Cr nominal / ₹3.78 Cr present value; retirement corpus ₹28.54 Cr; human capital at 23 ≈ ₹3.21 Cr; permanent income ≈ ₹10.75 L/yr; crossover at age 50; corpus lasts (no depletion). Use these to confirm your copy is behaving correctly.

---

## Using the module

**Web app.** Open `index.html` in any modern browser, or publish the folder via **GitHub Pages** (Settings → Pages → deploy from branch) and share the link. Adjust inputs; toggle nominal/real; export a PDF from the toolbar.

**Spreadsheet.** Open `financial-life-model.xlsx` in Excel or LibreOffice. **Edit only the yellow cells** on the *Inputs* sheet; every other value recalculates. The *Checks* sheet should always read `OK`. (The embedded charts are sized to the default age window; the Projection and Summary tabs are exact for any inputs.)

---

## Verification

The model was validated independently: a from-scratch re-implementation reproduces every output to the rupee, and six identities hold to floating-point precision — the accounting identity, its present-value analogue, the Fisher equivalence (nominal discounted at 9% ≡ real discounted at 2.83%), $HC_0 = PV(\text{consumption}) + PV(\text{savings})$, permanent-income PV $= HC_0$, and the closed-form corpus. In the workbook, these live on the *Checks* sheet; the spreadsheet recalculates with **zero formula errors**.

---

## Model limitations (a teaching point, not a disclaimer)

This is a **deterministic accounting model** built around the LCH/PIH identity. Its simplifications are deliberate — and interrogating them is part of the learning. The most important:

- **No uncertainty.** Returns, income, and lifespan are fixed, so there is no sequence-of-returns risk, no ruin probability, and no longevity risk. The corpus is one path, not a distribution.
- **A single constant return** ignores the age-based glide path (high equity when young, de-risking with age) implied by human-capital theory.
- **Retirement spending is held flat in real terms**, whereas the empirical profile falls at retirement and rises late in life as healthcare dominates — a basket that also inflates faster than headline CPI.
- **Consumption is smooth and exogenous.** Real lives are lumpy (education, marriage, housing, vehicles, emergencies) and often debt-financed; the model has one asset, no housing, and no explicit liabilities.

---

## Readings & references

### Suggested textbook chapters

**Bodie, Kane & Marcus — *Investments*** (chapter numbers follow the 12th–13th editions):
| Chapter | What it supports in this module |
|---|---|
| **Ch. 5 — Risk, Return, and the Historical Record** | Real vs. nominal returns, inflation, and the Fisher relation; the historical risk–return record that motivates the return and discount-rate assumptions. |
| **Ch. 6 — Capital Allocation to Risky Assets** | The risky/risk-free split behind the 60:40 portfolio and the 9% blended discount rate. |
| **Ch. 14 — Bond Prices and Yields** | Present value, discounting, and yield to maturity — the time-value machinery the model runs on. |
| **Ch. 28 — Investment Policy and the Framework of the CFA Institute** | The investor life cycle, human capital, risk tolerance and horizon, and asset allocation across the life cycle (the glide-path idea in *Limitations*). |

**Mishkin — *The Economics of Money, Banking & Financial Markets*** (numbering is stable across the 11th–13th editions):
| Chapter | What it supports in this module |
|---|---|
| **Ch. 4 — The Meaning of Interest Rates** | Present (discounted) value, yield to maturity, and the real vs. nominal interest-rate distinction with the Fisher equation — the analytical backbone of the module's discounting and inflation adjustment. |
| **Ch. 2 — An Overview of the Financial System** *(background)* | How household saving is channelled into financial assets through markets and intermediaries. |

> Chapter numbers can shift by one or two between editions; the chapter **titles** are stable, so match by title if your edition differs.

### Foundational papers
- Modigliani, F., & Brumberg, R. (1954). *Utility Analysis and the Consumption Function: An Interpretation of Cross-Section Data.*
- Friedman, M. (1957). *A Theory of the Consumption Function.* Princeton University Press.
- Fisher, I. (1930). *The Theory of Interest.*
- Modigliani, F. (1966). *The Life Cycle Hypothesis of Saving, the Demand for Wealth and the Supply of Capital.*
- Merton, R. C. (1969). *Lifetime Portfolio Selection under Uncertainty.* (glide-path extension)
- Bodie, Z., Merton, R. C., & Samuelson, W. F. (1992). *Labor Supply Flexibility and Portfolio Choice in a Life-Cycle Model.*
- Yaari, M. E. (1965). *Uncertain Lifetime, Life Insurance, and the Theory of the Consumer.* (longevity / annuities)

---

*Part of the personal-finance and financial-economics course. Figures are illustrative and for teaching only — not financial advice.*
