# Week 8 — Active Investing: Reading a Business

> Before you can pick a stock, you have to read the business behind it. This module opens a coffee shop at IIT Roorkee, follows one year of money in and out, and builds the three financial statements and the ratios an active investor reads from them.

Week 7 showed why frequent trading usually loses money. Week 8 turns to the other kind of active investing: choosing a company by understanding what it owns, what it earns and how it is financed. The module starts with a question, *"If you bought one share of Zomato today, what exactly do you own?"* It answers by building a small business from scratch. A coffee shop at IIT Roorkee raises capital, buys equipment, pays staff and rent, and sells 30,000 cups in its first year. From that one year of transactions the deck builds the **Profit & Loss statement**, the **Balance Sheet** and the **Cash Flow Statement**, shows how they link, and reads them through **ratios** and **common size analysis**. These are the same figures you will find on any listed company's page on Screener.in.

This is **Part 1** of Week 8.

---

## Contents

```
Week8_ReadingBusiness/
├── sl_ReadingABusiness.html   # interactive lecture slides — Part 1
└── README.md                  # this file
```

## Live access

- **Week 8 Slides:** https://abhishekshyp.github.io/financial-economics/Week8_ReadingBusiness/sl_ReadingABusiness.html

---

## What each file does

### `sl_ReadingABusiness.html` — lecture slides

A self-contained, interactive deck (9 slides) built on the course slide chassis:

- **What is a stock?** An opening question, answered in writing before the class moves on.
- **What is a business?** A company as a separate legal person under the Companies Act, 2013: it owns assets, can sue and be sued, and continues when its owners change, and its shareholders have limited liability. The slide sets out the common business forms in India, from sole proprietorship to listed company.
- **The coffee shop.** What the shop needs (raw material, equipment, premises), where its ₹6,00,000 of capital comes from (owner's savings, a 12% bank loan, a friend's investment), and how its performance is measured. Year 1 revenue is 30,000 cups × ₹80 = ₹24,00,000.
- **Money in and out.** Every rupee that enters the shop (from customers, the owner, the investor and the bank) and every rupee that leaves it (to equipment sellers, suppliers, employees, the landlord, the bank and the government). Year-end cash is ₹3,49,500.
- **The three statements and how they link.** The Year 1 P&L, Balance Sheet and Cash Flow Statement side by side. **Interactive:** tap a link (profit → equity, depreciation, working capital, equipment bought, loan & equity, cash) to highlight where the same number appears in each statement. The balance sheet balances at ₹7,29,500.
- **Ratios.** Margins (gross, operating, PAT), returns (ROI, ROE, ROA, ROCE), asset turnover and debt to equity, each computed from the coffee shop's statements.
- **Common size analysis.** The coffee shop compared with a hypothetical 50-outlet chain. **Interactive:** switch between the P&L and the balance sheet, and between ₹ values and % common size, to see why percentages make businesses of different sizes comparable.

The final slide lists the references.

*Technical note:* the slides load Chart.js from a CDN, so the page needs an internet connection to render the interactive elements. It deploys as-is to GitHub Pages. Navigate with **← →**, press **O** for the slide overview and **F** for fullscreen; append `#n` to the URL to deep-link to slide *n*.

---

## Concepts covered

- **What a share is:** a claim on a business, not a ticker price.
- **The company as a legal entity:** separate legal personality, perpetual succession and limited liability under the Companies Act, 2013.
- **Sources of capital:** owner's equity, outside equity and debt.
- **The three financial statements:** the P&L (performance over a year), the Balance Sheet (position on one day) and the Cash Flow Statement (where the cash came from and went), and the links between them: profit into retained earnings, depreciation, working capital, capital expenditure and financing.
- **Profit is not cash:** why PAT (₹1,54,500) and cash from operations (₹1,89,500) differ.
- **Financial ratios:** gross, operating and PAT margins; ROI, ROE, ROA and ROCE; asset turnover; debt to equity.
- **Common size statements:** the P&L as a % of revenue and the balance sheet as a % of total assets, for comparing companies of different sizes.

---

## Readings & references

- Penman, S. H. (2013). *Financial Statement Analysis and Security Valuation* (5th ed.). McGraw-Hill.
- Bodie, Z., Kane, A., & Marcus, A. J. (2021). *Investments* (12th ed.). McGraw-Hill. Ch. 19: Financial Statement Analysis.
- Ministry of Corporate Affairs. *The Companies Act, 2013*, Section 2(20) and Schedule III. Government of India.
- Zerodha Varsity. *Module 3: Fundamental Analysis*.
- Screener.in. Company financials and ratios.

---

## Disclaimers

- **Not investment advice.** This module is for teaching only. Nothing in it is a recommendation to buy, sell or hold any security. Companies named in the slides (such as Zomato, now Eternal Ltd) are used as examples only.
- **Hypothetical business.** The IIT Roorkee coffee shop and "Chain X" are invented for teaching. Their figures are illustrative and do not describe any real business.
- **Simplified accounting.** The statements are simplified to show the main ideas. For example, they use straight-line depreciation, a flat 25% tax rate and no GST. Real company accounts in India follow Ind AS and Schedule III of the Companies Act, 2013, and contain much more detail.
- **Ratios are a starting point.** A ratio is only as reliable as the statements behind it. Definitions also vary between sources (for example, ROCE on Screener.in may differ from the version on the slides), so always check how a ratio is calculated before comparing companies.

---

*Part of the personal-finance and financial-economics course. Figures in this module are illustrative and for teaching only — not financial advice.*
