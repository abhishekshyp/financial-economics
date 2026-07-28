# Week 2 — What's Your Risk Appetite?

> An interactive tutorial on decision-making under uncertainty. A biased-coin betting game opens the session; live tools then build expected value, volatility, correlation, and risk aversion from first principles; and a Bodie–Kane–Marcus risk-tolerance questionnaire, scored in real time, turns the abstract question *"how much risk should you hold?"* into a number you can compute for yourself.

This is the second module of the course. Week 1 built a **deterministic** financial life — one fixed path from first salary to bequest — and closed on its own most important limitation: *there was no uncertainty; the corpus was a single number, not a distribution.* Week 2 supplies the missing ingredient. It teaches students to **measure** uncertainty (expected value, standard deviation, correlation), to **price** it (the risk-free rate and the risk premium), and to **quantify their own tolerance** for it (a questionnaire, revealed preference, and the risk-aversion coefficient) — the exact inputs the portfolio-construction weeks (3–4) will need. It ships as a set of **interactive lecture slides** and a **standalone risk-tolerance questionnaire** that deploys as-is to GitHub Pages.

---

## Contents

```
Week2_WhatsYourRiskAppetite/
├── sl_RiskAppetite.html                 # interactive lecture slides (18 slides, live tools)
├── riskAversionScoreQuestionnaire.html  # Bodie–Kane–Marcus risk-tolerance quiz, scored live
└── README.md                            # this file
```

## Live access

Week 2 Slides: https://abhishekshyp.github.io/financial-economics/Week2_WhatsYourRiskAppetite/sl_RiskAppetite.html

Week 2 Questionnaire: https://abhishekshyp.github.io/financial-economics/Week2_WhatsYourRiskAppetite/riskAversionScoreQuestionnaire.html

---

## What the tool does — the risk-tolerance questionnaire

`riskAversionScoreQuestionnaire.html` is a single, self-contained web page that implements the classic **risk-tolerance questionnaire from Bodie, Kane & Marcus (*Investments*, Ch. 6)** and scores it live on the published **9–27** scale. A student answers each item as themselves; the tool tallies the score, places them on a Conservative → Moderate → Aggressive band, and shows where they fall as the marker slides along a "tolerance rises →" axis.

**How the score is built.** Each answer is weighted by its letter — **a → 1, b → 2, c → 3** — and the score is the plain sum across all scored items. Because every item ladders from the safest choice (a) to the most risk-seeking (c), the total is **monotone in risk tolerance**: a higher number means a greater willingness to bear risk.

**Why nine items, not seven.** Question 2 re-poses the same *"a 20% loss"* scenario across three time horizons — five, fifteen, and thirty years (items 2A, 2B, 2C) — and each is scored separately. That yields **9 scored items** (Q1, 2A, 2B, 2C, Q3, Q4, Q5, Q6, Q7). The all-*a* floor is 9 × 1 = 9 and the all-*c* ceiling is 9 × 3 = 27, which is exactly why the bands run from 9 to 27.

| Score band | Category | Interpretation |
|---|---|---|
| **9 – 14** | Conservative | penalises risk heavily; prefers principal safety |
| **15 – 21** | Moderate | the "middle-of-the-road" majority |
| **22 – 27** | Aggressive | accepts large variance for upside |

> **Read the direction carefully.** The questionnaire scores risk *tolerance* — higher is *more* risk-seeking. The risk-aversion coefficient **A** used on the slides (Method 2, revealed preference) runs the other way — higher **A** is *more* conservative. They are inverse framings of the same underlying trait; students should not conflate the two directions.

**The slides** (`sl_RiskAppetite.html`) carry the full lecture as an 18-slide interactive deck (arrow-key navigation, `O` for overview, `F` for fullscreen). Every concept is backed by a live tool: a two-minute round timer for the coin game, a real-time expected-value calculator, an outcome-distribution chart for the ELM experiment, a drawdown-recovery curve, a systematic-vs-unsystematic classification quiz, side-by-side volatility (distribution *and* simulated-path) demos with a correlation slider, a revealed-preference risk-aversion calculator, an uncorrelated five-asset diversification game, and a human-capital → term-cover calculator.

---

## Course content

This module covers the following concepts, each made concrete by a specific tool in the deck:

- **Expected value under risk** — weighting outcomes by probability, and the decision rule that a rational agent maximises EV because it drives long-run average wealth.
- **Why a positive edge still loses** — the three lessons of the ELM biased-coin experiment: a positive EV is *necessary but not sufficient*; overbetting destroys wealth (maximise lifetime wealth, not a single bet); and percentage losses hurt more than equal percentage gains help.
- **Risk versus uncertainty** — Knight's (1921) distinction between *measurable* risk (known probabilities) and *immeasurable* uncertainty, and why the ELM game was solvable only because every probability was known.
- **A taxonomy of risk** — market, sector/industry, company, financial, liquidity, and concentration risk, resolved into the single split that matters: **systematic vs. unsystematic**.
- **Quantifying an asset's risk** — expected return, variance and standard deviation as the measure of dispersion, and why two assets with the same mean are not equally attractive.
- **Correlation and diversification** — covariance and the correlation coefficient, two-asset portfolio variance, and the result that diversification only reduces risk when assets do not move in lockstep.
- **Quantifying the investor** — three routes to a risk number: a psychometric **questionnaire**, **revealed preference** from observed holdings, and the mean-variance **risk-aversion coefficient A**.
- **Managing personal risk** — diversification across geographies, asset classes, sectors, and market caps; and **insurance** as protection for human capital (term life as a hedge on the present value of future earnings — a direct callback to Week 1).

---

## Maths & stats formulas

The notation is standard: *p* is a probability, *r* a return, *E[·]* an expectation, *σ* a standard deviation, *w* a portfolio weight.

**Expected value of a bet**

```
EV = p · (gain) − (1 − p) · (loss)
```
ELM coin-flip challenge (even-money on a 60/40 coin, $20 staked): `EV = 0.60·(+20) + 0.40·(−20) = +$4` per flip — a **+20% edge** on the amount staked.

**The recovery asymmetry** — the gain needed to erase a drawdown of size *L*:

```
g = L / (1 − L)      →   L = 50%  requires  g = 100%
```
The gain required rises faster than the loss itself; symmetry in *percentages* is an illusion. *(For the curious, this is the seed of volatility drag: the geometric growth rate ≈ arithmetic mean − ½σ², so variance is a direct tax on compounded wealth.)*

**Expected return, variance, and standard deviation**

```
E[r] = Σ pᵢ rᵢ
Var(r) = σ² = Σ pᵢ (rᵢ − E[r])²
σ = √Var(r)
```

**Covariance and correlation**

```
Cov(A, B) = Σ pᵢ (rᵢᴬ − E[rᴬ]) (rᵢᴮ − E[rᴮ])
ρ(A, B) = Cov(A, B) / (σᴬ σᴮ),      ρ ∈ [−1, +1]
```

**Two-asset portfolio variance** (the correlation demo on the slides)

```
σₚ² = wᴬ² σᴬ² + wᴮ² σᴮ² + 2 wᴬ wᴮ ρ σᴬ σᴮ
```
For a 50/50 mix of two assets with equal volatility σ: `σₚ = σ · √((1 + ρ) / 2)` — falling from σ at ρ = +1 to 0 at ρ = −1.

**n-asset diversification, uncorrelated case** (the five-firm game, ρ = 0)

```
return:   E[rₚ] = Σ wᵢ rᵢ
risk:     σₚ = √( Σ wᵢ² σᵢ² )
benefit:  (Σ wᵢ σᵢ) − σₚ           # naïve weighted-average risk minus true portfolio risk
```
The gap is risk that simply *disappears* — the "only free lunch in finance."

**Risk aversion — mean-variance utility (Bodie, Ch. 6)**

```
utility:            U = E[r] − ½ A σ²
optimal risky wt:   y* = (E[r] − r_f) / (A σ²)
revealed A:         A  = (E[r] − r_f) / (y σ²)
```
Worked example (r_f = 7%, E[r] = 13%, σ = 20% ⇒ σ² = 0.04): a holder of **y = 20%** reveals `A = 0.06 / (0.20·0.04) = 7.5` (conservative); a holder of **y = 70%** reveals `A ≈ 2.1` (aggressive). Rule of thumb: **A > 6** conservative, **3–6** moderate, **A < 3** aggressive.

**Questionnaire score**

```
score = Σ (letter weight),   a → 1, b → 2, c → 3,   over 9 items   ⇒   score ∈ [9, 27]
```

**Human capital → insurance cover**

```
HC = Σ_{t=0}^{n−1}  S · (1 + g)ᵗ / (1 + d)ᵗ,      n = retirement age − current age
recommended term cover ≈ HC
```
The present value of future salary — growing at *g*, discounted at *d* — is the asset a term policy replaces if income stops.

---

## Using the module

**Run it.** Both files are single, self-contained HTML pages — no build step, no server. Open either in a modern browser, or deploy the folder to GitHub Pages and use the live links above. The slides load Chart.js from a CDN, so the deck needs an internet connection to render its charts; the questionnaire runs fully offline.

**Navigate the slides.** `←` / `→` move between slides, `O` opens the overview grid, `F` toggles fullscreen; on touch devices, swipe. Every slider and button is live — adjust inputs and the charts and numbers recompute instantly.

**Teach with it (the four-part rhythm).**
1. **Play** — open the [ELM coin-flip game](https://elmwealth.com/coin-flip/) (slide 2, best on a phone) and run the built-in two-minute timer while students place their first bets.
2. **Lecture** — walk the deck from expected value through the three coin lessons, risk vs. uncertainty, the risk taxonomy, asset-risk measurement, and the three ways to quantify an investor.
3. **Questions** — use the systematic-vs-unsystematic reveal quiz (slide 10) as an in-session check; have students take the [risk-tolerance questionnaire](https://abhishekshyp.github.io/financial-economics/Week2_WhatsYourRiskAppetite/riskAversionScoreQuestionnaire.html) and then reconcile their *tolerance* band against the *aversion* coefficient **A** they back out on slide 13.
4. **Assignment** — students beat the biased coin ($250+) and design a methodology that turns a person's age, salary, industry, liabilities, assets, human capital, dependents, and consumption rate into a risk-aversion score.

---

## Readings & references

### Suggested textbook chapters

**Bodie, Kane & Marcus — *Investments*** (chapter titles are stable across recent editions; match by title if your numbering differs):

| Chapter | What it supports in this module |
|---|---|
| **Ch. 5 — Risk, Return, and the Historical Record** | Expected return, variance and standard deviation as risk; the historical risk–return and risk-premium record that prices risk. |
| **Ch. 6 — Capital Allocation to Risky Assets** | The risk-free vs. risky split, mean-variance utility `U = E[r] − ½Aσ²`, the optimal risky weight `y*`, and the **risk-tolerance questionnaire** the tool implements. |
| **Ch. 7 — Optimal Risky Portfolios** *(preview of Weeks 3–4)* | Covariance, correlation, and two-asset portfolio variance — the diversification mathematics this week introduces and the next builds on. |

**Mishkin — *The Economics of Money, Banking & Financial Markets***:

| Chapter | What it supports in this module |
|---|---|
| **Ch. 5 — The Behaviour of Interest Rates** *(background)* | Risk and the risk premium as determinants of asset demand — the economic reasoning behind why risky assets must offer more. |

> Chapter numbers can shift by an edition or two; the **titles** are stable, so match by title.

## Research papers

- **Knight, F. H. (1921).** *Risk, Uncertainty and Profit.* Boston: Houghton Mifflin. — the original risk-vs-uncertainty distinction.
- **Barber, B. M., & Odean, T. (2000).** "Trading Is Hazardous to Your Wealth: The Common Stock Investment Performance of Individual Investors." *Journal of Finance*, 55(2), 773–806. — the investors who traded the most earned the lowest returns; overactivity as overbetting. [[PDF]](https://faculty.haas.berkeley.edu/odean/papers%20current%20versions/individual_investor_performance_final.pdf)
- **Haghani, V., & Dewey, R.** "Lessons from Betting on a Biased Coin: Cool Heads and Cautionary Tales." Elm Wealth. — the experiment behind the coin-flip game, in which 28% of participants went bust on a 60/40 winning edge. [[link]](https://elmwealth.com/lessons-from-betting-on-a-biased-coin-cool-heads-and-cautionary-tales/)
- **Kelly, J. L. (1956).** "A New Interpretation of Information Rate." *Bell System Technical Journal*, 35(4), 917–926. — *(optional, deeper)* the growth-optimal betting fraction and the mathematics of not overbetting an edge.
- **Dimson, E., Marsh, P., & Staunton, M.** *Global Investment Returns Yearbook* (UBS). — long-run historical equity risk premia used to *price* risk.

---

*Figures and tools in this module are illustrative and for teaching only — not financial advice.*
