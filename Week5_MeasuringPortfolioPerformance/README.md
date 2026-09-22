# Week 5 — Measuring Portfolio Performance

> Returns are easy; **risk-adjusted** returns tell the real story. Ten ways to answer *"how did the portfolio do?"* — each with its formula, the bias it carries, and the one situation it actually fits — worked through a single five-year fund from raw return to alpha.

With Weeks 3–4 you **built** a portfolio. Week 5 asks the harder question that comes next: once it is running, *how do you judge it?* A single "14% return" headline hides almost everything that matters — whether it beat cash, beat the index, rewarded the risk taken, or simply rode a rising market. This module builds the vocabulary of performance measurement top-down, from the plainest growth number to the risk- and model-adjusted figures a committee actually defends, and it makes the point that no single number is "the return" — the right measure is chosen from the *situation*. Unlike a play-then-lecture week, the deck here is itself the interactive tool: every measure ships with a live control, so the intuition is built *inside* the slides rather than in a separate game.

---

## Contents

```
Week5_MeasuringPortfolioPerformance/
├── sl_portfolioReturns.html   # interactive lecture slides — the full module
└── README.md                  # this file
```

## Live access

- **Week 5 Slides:** https://abhishekshyp.github.io/financial-economics/Week5_MeasuringPortfolioPerformance/sl_portfolioReturns#1

---

## What each file does

### `sl_portfolioReturns.html` — lecture slides

A self-contained, interactive deck (14 slides) built on the course slide chassis. It is organised around **one running case study** and then ten return measures, each presented in the same disciplined frame: the **formula**, an explicit **Bias** panel naming what the measure hides or distorts, a plain-language **Mental model**, and a **live widget** (slider + chart or worked table) that lets you move an input and watch the number respond.

**The case study — the IITR Startup AIF.** You manage an Alternative Investment Fund backing startups from the IIT Roorkee ecosystem: an initial ₹1 Cr, roughly ₹5 L added every quarter, a five-year horizon, benchmarked to the **Nifty Next 50**. The Investment Committee asks the only question that matters — *did we actually outperform?* Because the cash flows are dated and unequal and the question is benchmark-relative, no single measure answers it; the case threads **XIRR** (the fund's own return), **TWRR** (a like-for-like comparison with the index), and **active return** together. The deck points to an accompanying Excel workbook (daily AIF NAV, daily Nifty Next 50, and the dated cash flows) so the figures can be reproduced.

**The ten measures**, in the deck's order and logical grouping:

- **Growth of money** — **Absolute return (HPR)**, total distance travelled with no clock; and **CAGR**, one smoothed annual rate, carrying its endpoint-dependence flaw (two very different paths with the same start and end report the identical number).
- **Whose return, the strategy's or the investor's** — **XIRR** (money-weighted): the rate that zeroes the NPV of dated cash flows, so contribution size and timing drive it — the investor's *own* experience. **TWRR** (time-weighted): sub-period returns chained so external flows cancel out — the *strategy's* return and the fund-comparison standard under GIPS and SEBI. The XIRR-vs-TWRR gap is the conceptual core of the week.
- **Consistency across entry dates** — **Rolling returns**: the annualised return over every window that slides through the history, read as a *distribution* rather than a point estimate, exposing how much the answer depends on when you started.
- **Against a benchmark** — **Active return** (portfolio minus benchmark, arithmetic and geometric); **Excess return** (portfolio minus the risk-free rate), the raw reward for bearing any risk and the input that feeds both Sharpe and the CAPM regression.
- **Adjusted for the risk taken** — **Sharpe ratio**, excess return per unit of *total* volatility (the reward-to-variability ratio); **CAPM required return**, the *forward-looking* hurdle an asset must clear for its systematic risk, read off the Security Market Line; and **Jensen's alpha**, realised return minus the CAPM-predicted return — active performance *after* paying for market risk.

The deck closes with a **decision table — "which return, which situation"** — that maps each case (lumpsum vs SIP, fund vs investor, benchmark-relative, risk-adjusted, forward hurdle) to the one measure that fits, turning the ten definitions into a selection framework.

*Technical note:* the slides load Chart.js from a CDN, so the page needs an internet connection to render the charts and the interactive controls. It deploys as-is to GitHub Pages. Navigate with **← →**, press **O** for the slide overview and **F** for fullscreen; append `#n` to the URL to deep-link to slide *n*.

---

## Concepts covered

- **Return arithmetic:** holding-period (absolute) return and **CAGR**, and why CAGR's endpoint dependence makes it silent on the path — interim volatility and drawdowns.
- **Money-weighted vs time-weighted return:** **XIRR** as the investor's realised rate on dated flows vs **TWRR** as the flow-neutral measure of the strategy — why they diverge, and which one a fund is legitimately compared on (GIPS, SEBI).
- **Rolling returns** and horizon dependence: performance as a *distribution* over start dates, not a single figure.
- **Benchmark-relative performance:** active return (arithmetic vs geometric) and excess return over the risk-free rate — and the ambiguity of the word "excess."
- **Risk-adjusted performance:** the **Sharpe ratio** and the limits of using *total* volatility (symmetric penalty, fat tails, stale-price inflation).
- **CAPM, the Security Market Line, and Jensen's alpha:** the *required* return as a hurdle vs the *realised* return, and alpha as return market exposure cannot explain — with its model-dependence made explicit (single-factor pricing, unstable beta, Roll's critique, the Fama–French factors it misses).
- **A measure-selection framework:** matching the return measure to the decision at hand.

Every measure is paired with its **failure mode**, so the module reads as much as a catalogue of *biases* as of formulas — the discipline of knowing what each number quietly assumes.

---

## References & data sources

- Sharpe, W. F. (1966). "Mutual Fund Performance." *Journal of Business*, 39(1), 119–138. — the reward-to-variability (Sharpe) ratio.
- Sharpe, W. F. (1964). "Capital Asset Prices." *Journal of Finance*, 19(3), 425–442 — with Lintner (1965) and Mossin (1966). — the CAPM and the SML.
- Jensen, M. C. (1968). "The Performance of Mutual Funds, 1945–1964." *Journal of Finance*, 23(2), 389–416. — Jensen's alpha.
- Fama, E. F., & French, K. R. (1992). "The Cross-Section of Expected Stock Returns." *Journal of Finance*, 47(2), 427–465. — the factors single-factor alpha misattributes.
- Roll, R. (1977). "A Critique of the Asset Pricing Theory's Tests." *Journal of Financial Economics*, 4(2), 129–176. — the unobservable market portfolio.
- **CFA Institute — Global Investment Performance Standards (GIPS)** — on time-weighted vs money-weighted return.
- **Investments** — Bodie, Kane & Marcus (chapter on portfolio performance evaluation).
- **Market data:** NSE Indices Ltd., NIFTY 50 TRI historical returns. The Nifty Next 50 series, AIF NAV, and dated cash flows for the case study are supplied as a worked Excel workbook in the repository; SIP and path figures on individual slides are illustrative examples calibrated to the values shown.

---

*Figures and tools in this module are illustrative and for teaching only — not financial advice.*
