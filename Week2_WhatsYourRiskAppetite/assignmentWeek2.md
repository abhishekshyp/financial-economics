# Week 02 — What's Your Risk Appetite? · Assignment
### Financial Economics Tutorial

> "Risk appetite" is one word for four different things. This week we test all of them. First you'll *feel* risk-taking under a known edge — bet a biased coin and try to walk away with the maximum payout. Then you'll build a score for what a person can *objectively afford* to lose, and make it talk to the questionnaire (what you *say*) and the revealed-preference method (what you *do*).

---

## The brief

The assignment has two tasks.

- **Task 1 — Play & read.** Read the ELM write-up on betting a biased coin, play the game, and bring your official downloaded result.
- **Task 2 — Build your personal risk score.** Turn objective inputs (age, salary, industry, liabilities, assets, human capital, dependents, consumption rate) into a defensible risk-capacity score, then reconcile it against the questionnaire and revealed-preference methods from the lecture.

---

## Task 1 · Play & read — Beat the biased coin

You are handed **$25** and told a coin is biased **60% heads / 40% tails**. You may bet any amount on heads *or* tails, on each of ~300 flips in 30 minutes, and you keep your ending balance up to a **$250 cap** (ten times the stake). A positive-expected-value game, handed to you on a plate.

The uncomfortable result from the original experiment: only **21% reached the cap**, a **third finished below their starting $25**, and **28% went bust** — on a coin they *knew* was favourable.

**The link to this week.** The coin's return/risk ratio (~0.20) is close to what many expect from equities. Bet sizing *is* the risky-asset allocation decision. Kelly gives the growth-optimal share; a risk-averse investor rationally holds a *fraction* of Kelly. That fraction is what Task 2 tries to pin down from a person's balance sheet.

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

| Bucket | Higher risk-taking capacity when… | Reference weight (/100) |
|---|---|---|
| Human capital | large & stable relative to financial wealth (implicit safe asset) | 20 |
| Age / horizon | younger — more time to recover | 15 |
| Industry stability | income uncorrelated with markets (govt > cyclical > finance/founder) | 15 |
| Net-worth buffer | assets cover many years of spending | 15 |
| Liabilities / leverage | little fixed debt to service | 15 |
| Savings rate | high (low consumption rate → replenishable) | 10 |
| Dependents | few committed mouths to feed | 10 |

The reference vector deliberately puts ~half the weight on human capital, income stability, and leverage — the three things that decide whether a person can survive a drawdown *without being forced to sell at the bottom*. Beat it or depart from it, but say why.

**Answer these (keep it tight):**
- Justify your weights and your three cut-offs. Anchor at least one choice in a reading.
- Run one profile through it end-to-end (yourself, anonymised, or a persona) and report the score and label.
- Compare your label to what the questionnaire and the person's actual risky share would say. Where they disagree, which should win?

---

## What to submit

1. **Task 1** — the official downloaded coin-flip result (target: the $250 cap).
2. **Task 2** — your weights, your scoring, your cut-offs, and one worked profile with its label. A small Excel/Python sheet is enough. **State every assumption.**

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

---

## Submission

- **Deadline:** before the next tutorial.
- **Naming convention:** `RollNumber_FullName.extension` (e.g. `21112001_AbhishekKashyap.ipynb`, `..._RiskScore.xlsx`, `..._Tool.html`). Submit the coin-flip result as `RollNumber_FullName_Coin.pdf` (or the site's native file). For teams, submit one set under the team lead's `RollNumber_FullName` and list all members on page 1.
- **Upload folder:** _[insert Week 2 Google Drive link — folder closes at the deadline; no late or alternative submissions]_

---

*Figures in this brief are illustrative and for teaching only — not financial advice.*
