# Week 7 — Trading Is Hazardous to Your Wealth

> Nine in ten Indian F&O traders lose money, year after year. This module asks why. It works from SEBI's own loss data, through Sharpe's arithmetic of active management, to Barber and Odean's household trading records. Once costs are counted, someone always has to lose, and it is usually the most active trader.

Weeks 3–6 built, measured and rebalanced a long-term portfolio. Week 7 looks at the opposite habit: frequent, short-horizon trading. The module is arranged as three studies, each answering one question. **SEBI** shows *what* is happening: large and persistent retail losses in equity derivatives. **Sharpe (1991)** explains *why it must happen* on average: before costs, active investors as a group earn the market return, and after costs they earn less. **Barber & Odean (2000)** shows *how* it happens to individuals: certain costs, multiplied by turnover and sustained by overconfidence. Two live demos inside the slides let you move the inputs and watch the arithmetic work. The **Crystal Ball** game then lets you test whether you could trade profitably even with tomorrow's news.

---

## Contents

```
Week7_TradingIsHazardous/
├── sl_tradingIsHazardous.html   # interactive lecture slides — the full module
├── assignmentWeek7.md           # the assignment: summarise the Sharpe and Barber & Odean papers
├── readings/                    # the five core readings cited in the slides
│   ├── 1991-SHARPE-The-arithmetic-of-active-management.pdf
│   ├── 2000-BARBER_ODEAN-Trading-is-hazardous-to-your-wealth.pdf
│   ├── 2023-SEBI-Investor-Loss-Study.pdf
│   ├── 2024-SEBI-Investor-Loss-Study.pdf
│   └── 2026-SEBI-Investor-Loss-Study.pdf
└── README.md                    # this file
```

## Live access

- **Week 7 Slides:** https://abhishekshyp.github.io/financial-economics/Week7_TradingIsHazardous/sl_tradingIsHazardous.html
- **The game — Crystal Ball Trading Challenge (Elm Wealth):** https://crystal-ball.elmwealth.com/
- **Submit your game results:** https://drive.google.com/drive/folders/1ZdmpclhUhnPu-Coymn-EdrDEBP4Yh2mL?usp=sharing

---

## What each file does

### `sl_tradingIsHazardous.html` — lecture slides

A self-contained, interactive deck (11 slides) built on the course slide chassis, in three parts:

- **Part 1 · The problem (SEBI).** The share of individual F&O traders who lost money, and their net losses, from FY22 to FY25: 89% in FY22, 93% over FY22–FY24, 91% in FY25. A second slide shows who these traders are: most loss-makers keep trading, only 1% made more than ₹1 lakh, 43% are under 30, and over 75% earn under ₹5 lakh a year. A bridge slide then asks *where the money went*. In FY24, proprietary traders and FPIs made roughly what individuals lost.
- **Part 2 · The arithmetic (Sharpe, 1991).** The four-line proof that, before costs, the average actively managed rupee earns the market return, and that after costs it must earn less than passive. The slide adds the caveat that the identity is not exact (Pedersen, 2018). **Live demo — "If professionals win, who pays?":** set the professionals' share of active money, their gross edge and the cost of trading, and the zero-sum constraint *s·α<sub>pro</sub> + (1 − s)·α<sub>retail</sub> = 0* gives the loss retail must absorb.
- **Part 3 · The reasons (Barber & Odean, 2000).** 66,465 US households, 1991–1996. The most active fifth earned 11.4% a year against 18.5% for the least active, with similar returns before costs. The slides draw out three reasons, each with a US and an Indian data point: costs are certain, frequency multiplies them, and overconfidence keeps people trading. **Live demo — "Small costs, compounded":** set annual turnover and the cost per round trip, and watch the share of 30-year wealth that trading costs absorb.

The deck closes with a synthesis slide that ties the three studies into one idea. The final slide lists the references, with links to the papers.

*Technical note:* the slides load Chart.js from a CDN, so the page needs an internet connection to render the charts and the interactive controls. It deploys as-is to GitHub Pages. Navigate with **← →**, press **O** for the slide overview and **F** for fullscreen; append `#n` to the URL to deep-link to slide *n*.

### `readings/` — the core readings

Local copies of the five readings the module is built on. Links to the original sources are listed under [Readings & references](#readings--references).

### The game — Crystal Ball Trading Challenge

An external game built by Elm Wealth. You are shown a historical *Wall Street Journal* front page with the date and market prices removed, and you trade S&P 500 and 30-year Treasury futures on it, starting from a $1,000,000 bankroll with leverage. The question it puts to you is the same one the slides end on: **if you knew tomorrow's headlines, would you make money?** A "vs. AI" mode lets you trade the same headlines against AI models.

---

## Submitting your Crystal Ball Challenge results

Play the [Crystal Ball Trading Challenge](https://crystal-ball.elmwealth.com/), then submit a screenshot of your final results screen.

Suggested file name: `<YourName>_Week7_CrystalBall.png` (for example, `AnanyaSharma_Week7_CrystalBall.png`).

### Submission link

**Submit your Crystal Ball Challenge results here:**
https://drive.google.com/drive/folders/1ZdmpclhUhnPu-Coymn-EdrDEBP4Yh2mL?usp=sharing

---

## Concepts covered

- **Retail derivatives losses in India:** the scale, persistence and concentration of individual F&O losses, read from SEBI's regulatory studies.
- **Zero-sum markets:** why every derivative position has an opposite side, and where individual losses end up (proprietary traders, FPIs).
- **The arithmetic of active management:** active investors, as a group, earn the market return before costs and less after costs. This is an accounting identity, not a model of prices, and it holds whether markets are efficient or not.
- **Trading costs and turnover:** *Net return = Market return + Skill − (Turnover × Cost per round trip)*, and how a small yearly drag compounds into a large share of lifetime wealth.
- **Behavioural finance:** overconfidence, the no-trade theorem (Milgrom & Stokey, 1982), and gender differences in trading (Barber & Odean, 2001).

---

## Readings & references

### Core readings (in `readings/`)

| Year | Reading | Link |
|---|---|---|
| 1991 | Sharpe, W. F. "The Arithmetic of Active Management." *Financial Analysts Journal*, 47(1), 7–9. | [JSTOR](https://www.jstor.org/stable/4479386?seq=1) |
| 2000 | Barber, B. M., & Odean, T. "Trading Is Hazardous to Your Wealth: The Common Stock Investment Performance of Individual Investors." *Journal of Finance*, 55(2), 773–806. | [SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=219228) |
| 2023 | SEBI. *Analysis of Profit and Loss of Individual Traders Dealing in Equity F&O Segment* (FY19–FY22). January 2023. | [SEBI](https://www.sebi.gov.in/reports-and-statistics/research/jan-2023/study-analysis-of-profit-and-loss-of-individual-traders-dealing-in-equity-fando-segment_67525.html) |
| 2024 | SEBI. *Updated Study on Profit and Loss of Individual Traders in Equity F&O* (FY22–FY24). September 2024. | [SEBI](https://www.sebi.gov.in/media-and-notifications/press-releases/sep-2024/updated-sebi-study-reveals-93-of-individual-traders-incurred-losses-in-equity-fando-between-fy22-and-fy24-aggregate-losses-exceed-1-8-lakh-crores-over-three-years_86906.html) |
| 2026 | SEBI. *Profitability of Individual Traders in the Equity Derivatives Segment* (FY25–FY26). August 2026. | [SEBI](https://www.sebi.gov.in/reports-and-statistics/research/aug-2026/study-profitability-of-individual-traders-in-the-equity-derivatives-segment-fy25-fy26-_103835.html) |

### Further reading

- Barber, B. M., & Odean, T. (2001). "Boys Will Be Boys: Gender, Overconfidence, and Common Stock Investment." *Quarterly Journal of Economics*, 116(1), 261–292.
- Milgrom, P., & Stokey, N. (1982). "Information, Trade and Common Knowledge." *Journal of Economic Theory*, 26(1), 17–27.
- Odean, T. (1998). "Volume, Volatility, Price, and Profit When All Traders Are Above Average." *Journal of Finance*, 53(6), 1887–1934.
- Pedersen, L. H. (2018). "Sharpening the Arithmetic of Active Management." *Financial Analysts Journal*, 74(1), 21–36.
- SEBI (2024, July). *Analysis of Intraday Trading by Individuals in Equity Cash Segment* (FY23).
- SEBI (2025, July). *Study on Trading Activity in the Equity Derivatives Segment* (FY25).

---

## Disclaimers

- **Not investment advice.** This module is for teaching only. Nothing in it is a recommendation to buy, sell or trade any security or derivative, or to adopt any trading or investment strategy.
- **Derivatives carry a high risk of loss.** Trading futures and options can lose more than the capital you start with. SEBI's own studies, cited in this module, find that roughly nine in ten individual traders in equity F&O lose money.
- **Data as published.** SEBI figures are reproduced from the studies listed above as of their publication date. Later studies may revise them. For example, the August 2026 study revises FY25 net losses upward because it uses a larger broker sample. Some figures on the slides are derived from the reported totals, and each slide notes how.
- **The demos are illustrative.** The two live demos use simplified assumptions: a 12% yearly market return, zero skill, no taxes and a fixed passive cost. They show a mechanism, not a forecast of any real portfolio.
- **Third-party game.** The Crystal Ball Trading Challenge is built and operated by Elm Wealth, not by this course. It has no affiliation with this course, and its own terms and privacy policy apply. Game results are simulated and say nothing about real trading ability.
- **Readings.** The papers and reports in `readings/` remain the copyright of their authors and publishers. They are provided for the private study of course participants only and must not be redistributed. Please cite and obtain them from the original sources linked above.

---

*Part of the personal-finance and financial-economics course. Figures in this module are illustrative and for teaching only — not financial advice.*
