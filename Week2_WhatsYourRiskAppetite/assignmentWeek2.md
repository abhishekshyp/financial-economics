# Week 02 — What's Your Risk Appetite? · Assignment
### Financial Economics Tutorial

> "Risk appetite" is one word for four different things. This week we test all of them. First you'll *feel* risk-taking under a known edge — bet a biased coin and try to walk away with the maximum payout. Then you'll build a score for what a person can *objectively afford* to lose, and make it talk to the questionnaire (what you *say*) and the revealed-preference method (what you *do*).

---

## The brief

The assignment has three tasks.
 
- **Task 1 — Play & read.** Read the ELM write-up on betting a biased coin, play the game, and bring your official downloaded result.
- **Task 2 — Build your personal risk score.** Turn objective inputs (age, salary, industry, liabilities, assets, human capital, dependents, consumption rate) into a defensible risk-capacity score, then reconcile it against the questionnaire and revealed-preference methods from the lecture.
- **Task 3 — The concentration case study.** Work through a sector shock that hits your salary and your ESOPs at once, and decide what to do about it.

---

## Task 1 · Play & read — Beat the biased coin

You are handed **$25** and told a coin is biased **60% heads / 40% tails**. You may bet any amount on heads *or* tails, on each of ~300 flips in 30 minutes, and you keep your ending balance up to a **$250 cap** (ten times the stake). A positive-expected-value game, handed to you on a plate.

The uncomfortable result from the original experiment: only **21% reached the cap**, a **third finished below their starting $25**, and **28% went bust** — on a coin they *knew* was favourable.

**The link to this week.** The coin's return/risk ratio (~0.20) is close to what many expect from equities. Bet sizing *is* the risky-asset allocation decision. Kelly gives the growth-optimal share; a risk-averse investor rationally holds a *fraction* of Kelly. That fraction is what Task 2 tries to pin down from a person's net worth.

**Do this:**
- Read the write-up: https://elmwealth.com/lessons-from-betting-on-a-biased-coin-cool-heads-and-cautionary-tales/
- Play the game: https://elmwealth.com/coin-flip/
- Grow your $25 to the **$250 maximum payout**, then **download the official result from the site** and submit it.

---

## Task 2 · Build your personal risk score

In class we scored risk two ways: the **questionnaire** (what a person *says*) and **revealed preference** (what they *hold* in risky assets). Both miss a third thing — what a person can objectively *afford* to risk. Build a score for that from these inputs, and use it to label them **Aggressive / Moderate / Conservative**:

`age · salary · industry · liabilities · assets (risky vs risk-free) · human capital · dependents · consumption rate`

**The hint — the whole method is three moves:**

1. **Assign weights out of 100** across the eight buckets (they must sum to 100). This is the graded part — *defend* each weight with economic reasoning, not taste. Use the table below as a reference direction for each bucket.
2. **Score and combine.** Rate each bucket 0–100 for how much it *supports* risk-taking (100 = most), then take the weighted average → a single 0–100 risk score.
3. **Label the output.** Map the score to a band — e.g. **0–40 Conservative, 40–70 Moderate, 70–100 Aggressive**. Pick and justify your own cut-offs.

**Answer these (keep it tight):**
- Justify your weights and your three cut-offs.
- Run one profile through it end-to-end (yourself, anonymised, or a persona) and report the score and label.
- Compare your label to what the questionnaire and the person's actual risky share would say. Where they disagree, which should win?

---

## Task 3 · The concentration case study
 
**The setup.** Pick the one sector you'd most like to work in — **your** sector (tech, banking, pharma, energy, autos, whatever pulls you). Now live in it:
 
> You are 27, single, no debt. On the risk score from Task 2 you land firmly **Aggressive** — long horizon, no dependents, high capacity to take risk. You draw a good salary from a firm in this sector, and a chunk of your pay is **ESOPs** in that same firm. Life is good, and the standard advice — "you're young, own equities, take risk" — feels right.
 
Then the sector turns. A shock hits: your **salary falls by x%** (bonus cut, then a pay freeze, then layoff risk) and, in the same quarter, your **ESOP value falls by y%**. Pick your own x and y, or use **x = 25%, y = 60%** as the base case. Both hits land together — because they are the same bet.
 
**Work through this — three moves:**
 
1. **Size the joint loss on your total net worth.** Estimate your wealth *including human capital*: `Human capital H` = PV of your remaining salary (a rough `salary × annuity factor` is fine), plus `ESOPs`, plus any diversified financial assets and cash. State your assumptions (salary, growth g, discount rate r, years to 65). Now apply the shock and report the loss in **rupees/dollars and as a % of total wealth**.
2. **Calculate the correlation.** One shock is one data point — you cannot get a correlation from it. So build a small **sector-scenario table** (say: boom / normal / mild downturn / crash), and in each state write your salary growth and your ESOP return; the crash row is your (x%, y%) shock. Then compute
   `ρ = Cov(Δsalary, ΔESOP) / (σ_salary · σ_ESOP)`
   across the states. Report ρ and explain *why* it comes out where it does. (It will sit near **+1** — both are driven by the same sector factor. That is the finding, not an accident.)
3. **Write your forward plan — assuming you must stay in this sector.** You love the work; quitting is not the answer. So the fix has to come from the *financial* side of the net worth. In one tight paragraph, say what you will do differently — e.g. sell and reinvest ESOPs as they vest rather than letting them ride, keep your fund portfolio *underweight* your own sector (hedge the paycheck instead of doubling it), hold a larger uncorrelated buffer given that a sector shock threatens income and savings at once. Tie each move back to ρ: the higher your income-to-portfolio correlation, the harder your financial capital must lean the other way.
Human capital shrinks toward zero as you approach retirement, while financial capital accumulates; suppose they **cross at age 45**. Does the concentration problem *solve itself* at that crossover?

---

## What to submit

1. **Task 1** — the official downloaded coin-flip result (target: the $250 cap).
2. **Task 2** — your weights, your scoring, your cut-offs, and one worked profile with its label. A small Excel/Python sheet is enough. **State every assumption.**
3. **Task 3** — your chosen sector, the total-wealth figure, the scenario table with the computed ρ, your one-paragraph forward plan, and the H-vs-F crossover question.

---

## Readings & references
 
**Play & read (Task 1)**
- Haghani, V., & Dewey, R. (2016). *Lessons from Betting on a Biased Coin: Cool Heads and Cautionary Tales.* Elm Wealth.
- Haghani, V., & White, J. (2023). *The Missing Billionaires.* Wiley. — bet-sizing and expected-utility as the missing half of finance education.

**Build the score (Task 2)**
- Bodie, Kane & Marcus, *Investments* — **Ch. 6** (Capital Allocation to Risky Assets; the `y* = (E[r]−r_f)/(A σ²)` rule) and **Ch. 28** (investor life cycle, human capital, tolerance vs capacity).
- Merton, R. C. (1969). *Lifetime Portfolio Selection under Uncertainty.* — `w* = (μ−r_f)/(γσ²)`.
- Bodie, Merton & Samuelson (1992). *Labor Supply Flexibility and Portfolio Choice in a Life-Cycle Model.* — why human capital lets the young hold more equity.
- Campbell, J. Y., & Viceira, L. M. (2002). *Strategic Asset Allocation.* — human capital as an implicit bond; horizon effects.
- Grable, J., & Lytton, R. (1999). *Financial Risk Tolerance Revisited.* — the questionnaire lineage (Method 1).
- Barsky, Juster, Kimball & Shapiro (1997). *Preference Parameters and Behavioral Heterogeneity.* — plausible ranges for γ.
- Kahneman, D., & Tversky, A. (1979). *Prospect Theory.* — the caveat: stated and revealed risk attitudes are reference-dependent and unstable.

**The concentration case study (Task 3)**
- Markowitz, H. (1952). *Portfolio Selection.* Journal of Finance. — diversification as the only free lunch; correlation is the lever.
- Bodie, Kane & Marcus, *Investments* — **Ch. 7** (Optimal Risky Portfolios; how variance falls with n and the systematic-risk floor).
- Benartzi, S. (2001). *Excessive Extrapolation and the Allocation of 401(k) Accounts to Company Stock.* — the employer-stock trap, exactly this case.
- Davis, S. J., & Willen, P. (2000). *Occupation-Level Income Shocks and Asset Returns.* — why your portfolio should hedge, not amplify, your career risk.
- Statman, M. (2004). *The Diversification Puzzle.* — how much diversification is enough, and why people hold too little.

---

# Grading

This is a **completion grade — 2 marks for submitting.** All three tasks in, and the marks are yours; there's no quality scoring.

---

## Submission

- **Deadline:** before the next tutorial.
- **Naming convention:** `RollNumber_FullName.extension` (e.g. `21112001_AbhishekKashyap.ipynb`, `..._RiskScore.xlsx`, `..._Tool.html`). Submit the coin-flip result as `RollNumber_FullName_Coin.pdf` (or the site's native file). For teams, submit one set under the team lead's `RollNumber_FullName` and list all members on page 1.
- **Upload folder:** https://drive.google.com/drive/folders/1iGKPvFCisDUvshyZjz474NDy_SrkOCTv?usp=sharing

---

*Figures in this brief are illustrative and for teaching only — not financial advice.*
