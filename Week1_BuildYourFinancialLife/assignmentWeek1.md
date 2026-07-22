# Week 01 — Build Your Financial Life · Assignment
### Financial Economics Tutorial

> Think for yourself. Look honestly at your own personal finances — the emergencies, the big purchases, the debts, the good years and the bad ones — and ask: *what did the tool leave out?* Then build it back in.

---

## The brief

In the tutorial we built **Build Your Financial Life** — a clean, deterministic model of a whole financial life. Its power is its simplicity, but that simplicity is also a set of assumptions we deliberately made to keep the machine legible. On the last slide we named the model's blind spots. This assignment asks you to **remove them, one at a time.**

Your task is to **extend the existing model** so that it handles the four limitations below. For each one you will find a short explanation of *why* it matters, a worked example to anchor your thinking, and a list of what you need to build and the questions your extension should answer. Treat the base model as a scaffold — you are adding the realism back.

You do **not** need a perfect model. You need a *thoughtful* one, with every assumption stated openly and every finding backed by a number or a chart.

---

## Extension 1 — Income is uncertain

The base model assumes your income arrives on schedule, every year, forever. Real incomes don't behave like that. People lose jobs, take pay cuts, fall ill, start over. The single most important stress test of any financial plan is: **what happens in a bad year?**

**Worked example.** Imagine a COVID-style shock. For a stretch of **6–12 months your salary is cut by 50%** — a layoff, a furlough, a family emergency that pulls you out of work. But your *expenses do not fall by the same amount*: rent, EMIs, food, dependents — much of your consumption is committed. So the question becomes concrete: **when income drops but consumption holds, does your model quietly fund the gap from savings? And if savings aren't enough, what then?**

**Build this:**
- Add an **income-shock input** — a start age, a duration (in months/years), and a severity (e.g. −50%).
- Hold consumption fixed (or let the student choose how much is "committed" vs. cuttable) and let the shortfall draw down the corpus.
- Track what happens to wealth **during and after** the shock.

**Answer these:**
- How deep does the corpus dip? How many years does it take to recover to the pre-shock path?
- Does wealth ever go **negative** — i.e. are you forced to borrow? At what point does the plan break?
- How large an **emergency buffer** (months of expenses) would have absorbed the shock without touching long-term savings?
- *Stretch:* instead of one fixed shock, make income **stochastic** — draw annual returns and/or income from a distribution and run it many times (a simple Monte Carlo). Report the *probability* of ruin, not a single path.

---

## Extension 2 — The glide path

The base model earns one flat return (9%) for life. But human-capital theory says that's wrong. When you are **young, your human capital is large and relatively bond-like** (a fairly safe future salary stream), so you can afford to take *more* risk with your small financial portfolio — hold more equity. As you **age, human capital runs down**, so you **de-risk** — shift from equity toward debt/safe assets. Your return should therefore **change every year**, not stay constant.

**Worked example.** A common rule of thumb sets your **equity share ≈ (100 − age)%**, with the rest in debt. At 25 that's 75% equity / 25% debt; at 60 it's 40/60. If equity returns ~11% and debt ~6%, then your **blended return each year** is `equity% × 11% + debt% × 6%` — high when young, drifting lower as you age. (You may prefer the more modern `110 − age` or `120 − age` rules — justify your choice.)

**Build this:**
- Implement an **age-based allocation** (equity% and debt%) that changes each year.
- Compute a **time-varying blended return** and feed it into the wealth-accumulation engine, replacing the flat 9%.
- Rebalance annually.

**Answer these:**
- How does the final corpus compare to the flat-9% baseline? Is it higher or lower, and *why*?
- The glide path lowers *average* return late in life — but what does it buy you in exchange? (Think about the *risk* to a corpus you can no longer rebuild with fresh salary.)
- Plot equity/debt share and blended return against age. Where does the crossover from "mostly equity" to "mostly debt" fall relative to the human-/financial-capital crossover from the lecture?

---

## Extension 3 — Real life is lumpy

The base model consumes in a smooth curve. Real lives are **lumpy** — big, discrete, often unavoidable outflows land in specific years. Your model should be able to absorb the classic life goals and tell you whether the plan survives them.

**Worked example.** Can your plan fund a **marriage, a house, two children's education, and a car**? Place each goal at a plausible age, subtract it (or its down-payment) from wealth in that year, and watch what happens to the corpus. Use the illustrative 2025–26 figures below as *starting anchors* — then **pick and justify your own** numbers for your city and lifestyle.

| Goal | Illustrative cost (2025–26, INR) | Modelling notes |
|---|---|---|
| **Wedding** | ₹10–25 lakh (middle-class) | Huge range: tier-3 town ~₹5 L; "big-fat"/destination ₹50 L–1 Cr+. Place ~age 28–30. |
| **Home** (metro 2BHK, ~1,000 sq ft) | ₹60 lakh – ₹1.5 crore | Add ~7–10% stamp duty/registration. Usually a **20% down-payment + home loan** — links to Extension 4. Place ~age 32–35. |
| **Children's education** (per child, school → one professional degree) | ₹30–60 lakh | A premier engineering degree is ~₹16 L *today*; **education inflates ~10%/yr — faster than headline CPI (~6%)**, so inflate this goal separately. Two kids → double it. Outflows ~age 45–55. |
| **Car** (mid-segment, on-road) | ₹8–12 lakh | Entry hatchback ~₹4 L; premium SUV/EV ₹20 L+. Add ~15–20% for on-road. Place ~age 30–33. |

> *Figures are illustrative ballparks for 2025–26 and vary enormously by city, scale, and choices. State the numbers **you** assume and why.*

**Build this:**
- Add a small **goals schedule**: a list of (age, goal, amount, inflation rate) rows that subtract from wealth in the relevant year.
- Inflate each goal to its future rupee value at the year it occurs (remember: **education inflation ≠ CPI**).

**Answer these:**
- Does the corpus survive all four goals, or does it go negative somewhere? Which single goal hurts the most?
- How sensitive is survival to **sequencing** — does buying the house before vs. after the kids' education change the outcome?
- What saving rate (or income) would you need for the plan to fund every goal *and* still retire comfortably?

---

## Extension 4 — Debt financing (add liabilities)

The base model has **one asset and no liabilities** — you can only spend what you've saved. But real households routinely **borrow**: home loans, car loans, education loans. Debt lets you consume *before* you've saved — at a price (interest). This extension asks you to model that price honestly.

**Worked example.** Instead of paying cash for the house or car in Extension 3, **finance part of it with a loan** — say a 20% down-payment and an 80% home loan at ~8.5–9% over 20 years, repaid as a monthly EMI. The EMI becomes a *committed* expense that eats into savings for years. The interesting question is the long-run one: **does borrowing leave you richer or poorer at the end of life — and when, if ever, is it rational?**

**Build this:**
- Add **loans**: principal, interest rate, tenure, and an **EMI** (`EMI = P·r·(1+r)^n / ((1+r)^n − 1)`, r = monthly rate, n = months).
- Route the EMI through the consumption/savings identity as a committed outflow until the loan is repaid.

**Answer these:**
- Over the whole life, does debt-financing the goals **increase or decrease** your terminal wealth versus paying cash? Explain the mechanism, not just the number.
- Debt has a cost (loan rate) but frees cash to stay **invested** (earning your portfolio return). When does borrowing *create* value — i.e. under what relationship between the **loan rate** and your **investment return** is leverage rational?
- What happens to the debt-financed plan if you also hit the **Extension 1 income shock** while carrying an EMI? (This is where plans really break.)

---

## Bonus (optional) — Your own extension

The brief started with a question: *what did the tool leave out that matters to **you**?* Add **one feature of your own** — something you personally wish the model had. Ideas: an explicit emergency fund, health-insurance premiums and a medical shock, a working spouse's income, side/freelance income, changing tax slabs, rent-vs-buy, or retirement spending that *falls* then *rises* with healthcare. Model it, and tell us what it revealed.

---

## How to do it

Pick **one** of the following. All three are equally acceptable — choose the one that lets you think best.

- **Python** — build it **from scratch, in your own way.** No template; your structure, your charts, your design. Innovation counts.
- **Excel** — extend the **spreadsheet model provided in the course**. Keep every figure a live formula; edit assumptions, not hard-coded numbers.
- **HTML tool** — extend the **existing `index.html`** from the course directory (add inputs, logic, and charts for the extensions above).

---

## Teams

Work **individually or in a team of your choice, up to a maximum of 3 students.** All members are expected to contribute across the four extensions.

---

## What to submit

1. **The extended model** — your Python code / Excel workbook / HTML file.
2. **A short write-up (1–3 pages)** — for each of the four extensions: the assumptions you made, what you changed, the key chart or number, and what you *found*. Close with one paragraph of reflection: what surprised you about your own financial life?

**State every assumption clearly.** A modest model with honest, well-argued assumptions beats an elaborate one you can't defend.

---

## Submission

- **Deadline:** **before the next tutorial.**
- The **Google Drive folder will remain open only until the deadline.** Once it passes, the folder closes — **no late submissions and no alternative modes of submission will be accepted.** Plan accordingly.
- **Upload here:** https://drive.google.com/drive/folders/17140buUAyqltJU03c-Jruv3jyyg1HFAS?usp=sharing

**Naming convention:**

```
RollNumber_FullName.extension
```

*(e.g. `21112001_AbhishekKashyap.ipynb`, `..._Model.xlsx`, or `..._Tool.html`.)*
For **teams**, submit **one** file named with the **team lead's** `RollNumber_FullName`, and list every member's name and roll number on the first page of the write-up (or as a header comment in the code).

---

## Live access

- **Week 1 Slides:** https://abhishekshyp.github.io/financial-economics/Week1_BuildYourFinancialLife/sl_FinancialLifeModel#1
- **Week 1 Tool:** https://abhishekshyp.github.io/financial-economics/Week1_BuildYourFinancialLife/

---

*Figures in this brief are illustrative and for teaching only — not financial advice.*
