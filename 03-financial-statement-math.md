# Financial-Statement Math: Ratios, Depreciation, and Amortization

*Three pieces of pure math — a quotient, a geometric sequence, and a geometric series — hiding inside ordinary accounting.*

## The cold open

Two companies cross your desk. Each reported $30 million in net income last year. The first is a regional retailer with $100 million in revenue; the second is a global manufacturer with $50 billion in revenue. A junior analyst, seeing the identical $30M, calls them equally profitable.

They are nothing alike. The retailer earned thirty cents of profit on every revenue dollar — an extraordinary 30% net margin, the kind of number that makes you check the books twice. The manufacturer earned six hundredths of a penny on the dollar — a 0.06% margin, a firm one bad quarter from a loss. Same $30 million; opposite stories. The number $30M, by itself, is unreadable. It means nothing until you divide it by something — until you give it a denominator that controls for the scale of the business that produced it.

That act of division is a **ratio**, and it is the first of three pieces of mathematics this chapter pulls out of the accounting. The other two are hiding in how firms expense assets and pay off loans, and both turn out to be the compound-growth machinery of Chapter 1 in a new costume.

## The tool, named

This chapter names three quantitative tools that accounting uses as givens:

1. A **financial ratio** is a quotient — one statement figure divided by another — that strips out scale so two firms (or one firm across time) can be compared. Ratios cluster into families: **liquidity, leverage, profitability, efficiency**.
2. **Depreciation** spreads an asset's cost over its useful life. Straight-line spreads it evenly; **declining-balance** spreads it front-loaded — and declining-balance turns out to be a **geometric sequence**.
3. An **amortization schedule** splits each level loan payment into interest and principal. The schedule is generated mechanically from one number — the payment — and rests on a **geometric series** (the annuity formula of Chapter 4).

## Development and derivation

### Ratios as scale-free quotients

The cold open already gave the master move: divide to remove scale. Net margin is $\text{Net income}/\text{Revenue}$ — the retailer's $30/100 = 30\%$ versus the manufacturer's $30/50{,}000 = 0.06\%$. The five ratio families are five distinct *questions* you ask with a quotient, not ten formulas to memorize:

| Family | The question it answers | A representative ratio |
|---|---|---|
| **Liquidity** | Can it pay its near-term bills? | Current ratio = Current assets / Current liabilities |
| **Leverage** | How much does it borrow, and can it service the debt? | Debt-to-equity; Times-interest-earned = EBIT / Interest |
| **Profitability** | How much profit per dollar of sales, assets, equity? | Net margin; Return on equity = Net income / Equity |
| **Efficiency** | How hard do its assets work? | Asset turnover = Revenue / Total assets |

A ratio's number means nothing in isolation — a current ratio of 0.8 is alarming for a manufacturer and unremarkable for a fast-food chain that collects cash before it pays suppliers. This is precisely why Alexander Wall's 1919 study computing seven ratios across 981 firms, stratified by industry, *created* the practice we now take for granted: comparing a firm to its industry, not to an absolute standard [verify].

**The DuPont identity — algebra revealing structure.** The showcase of "ratios are not arbitrary formulas" is the DuPont decomposition (F. Donaldson Brown at DuPont, ~1912–1919) [verify]. Return on equity is $\text{ROE} = \text{Net income}/\text{Equity}$. Now perform the oldest trick in algebra — multiply by 1, twice, in a useful disguise:

$$\text{ROE} = \frac{\text{NI}}{\text{Equity}} = \frac{\text{NI}}{\text{Sales}}\times\frac{\text{Sales}}{\text{Assets}}\times\frac{\text{Assets}}{\text{Equity}}.$$

Check it: the Sales cancel, the Assets cancel, and you are back to $\text{NI}/\text{Equity}$ — the identity is exact. But look at what fell out. ROE is the product of three independent drivers:

$$\text{ROE} = \underbrace{\text{Net margin}}_{\text{profitability}}\times\underbrace{\text{Asset turnover}}_{\text{efficiency}}\times\underbrace{\text{Equity multiplier}}_{\text{leverage}}.$$

![Flow diagram splitting ROE into the product of net margin, asset turnover, and equity multiplier, with two firms both at 25% ROE reached by leverage versus operations](images/03-financial-statement-math-fig-02.png)
*Figure 3.2 — DuPont: one ROE, three drivers — and 25% can be fragile leverage or durable operations.*

Two firms can post an identical 25% ROE for opposite reasons: one through a fat margin and light debt, the other through thin margins and heavy leverage (a high equity multiplier). In a downturn the first holds and the second collapses, because leverage amplifies losses as surely as gains [verify]. The algebra was mechanical; the *diagnosis* — "this ROE is fragile leverage, not durable operations" — is the analyst's judgment, and it is exactly what a spreadsheet computing ROE will never tell you.

### Declining-balance depreciation as a geometric sequence

A firm buys a $40,000 delivery truck with a $5,000 salvage value and a useful life of, say, 7 years (the structure of a worked case in MBA-Accounting) [verify]. **Straight-line** depreciation spreads the depreciable base evenly:

$$\text{annual depreciation} = \frac{\text{cost} - \text{salvage}}{\text{life}} = \frac{40{,}000 - 5{,}000}{7} = \$5{,}000\text{/yr},$$

a flat line. **Double-declining-balance (DDB)** instead applies a constant *rate* to the shrinking book value each year. The rate is twice the straight-line rate, $r = 2\times(1/7) = 28.6\%$, applied to whatever book value remains:

$$\text{Year 1: } 0.286 \times 40{,}000 = \$11{,}440; \quad \text{book value} \to 40{,}000 - 11{,}440 = \$28{,}560.$$
$$\text{Year 2: } 0.286 \times 28{,}560 = \$8{,}168; \quad \text{book value} \to \$20{,}392.$$

Each year the book value is multiplied by $(1 - r)$. After $n$ years:

$$\boxed{\;\text{Book value}_n = \text{cost}\times(1 - r)^n.\;}$$

![Two book-value curves for a $40,000 truck over seven years: a straight diagonal straight-line path to salvage versus a front-loaded double-declining-balance curve approaching the salvage floor](images/03-financial-statement-math-fig-01.png)
*Figure 3.1 — Same $35,000 total, different timing: declining-balance front-loads the expense as compound decay.*

That is a **geometric sequence** — and it is exactly the compound-growth factor of Chapter 1, $(1+g)^n$, run with a negative growth rate $g = -r$. "Accelerated depreciation" is compound *decay*. The two methods, straight-line and DDB, depreciate the *same total* (cost minus salvage) over the asset's life; they differ only in *timing* — DDB front-loads the expense. Seeing the geometric structure tells you why DDB never quite reaches zero on its own (a geometric sequence approaches but never hits zero), which is why firms switch to straight-line near the end or stop at salvage value.

> **Two depreciation traps.** First, **book value is not market value** — the most common beginning error. Book value is an accounting allocation of cost; the truck's resale price is a market fact, and they need not agree. Second, **depreciation does not move cash.** The $40,000 left the firm when it bought the truck; depreciation merely allocates that past outflow across future periods. It is a non-cash expense that nonetheless lowers taxable income — which is why firms use accelerated methods for tax.

### An amortization schedule from one payment

A loan amortization schedule looks like an accounting artifact, but it is generated mechanically from a single number: the level payment. That payment comes straight from the annuity formula we derive in Chapter 4 — a loan is an annuity from the lender's side, so the borrower's level payment $A$ on a principal $P_0$ at periodic rate $r$ over $n$ periods is

$$A = \frac{P_0 \, r}{1 - (1+r)^{-n}}.$$

(That denominator is the geometric-series sum we build next chapter; here, take it as given and watch what it generates.) With the payment fixed, every row of the schedule follows by one rule applied repeatedly:

1. **Interest this period** $= r \times (\text{beginning balance})$.
2. **Principal this period** $= A - \text{interest}$.
3. **Ending balance** $= \text{beginning balance} - \text{principal}$.

Consider a $10,000 loan at 1% per month for 12 months. The payment works out to $A = \$888.49$. The first month's interest is $0.01\times 10{,}000 = \$100$, so principal is $888.49 - 100 = \$788.49$ and the balance falls to $\$9{,}211.51$. The next month's interest is computed on that *smaller* balance, $0.01\times 9{,}211.51 = \$92.12$, so more of the same payment goes to principal. Month after month the interest share shrinks and the principal share grows, while the balance runs to exactly zero on the final payment.

![Stacked bar chart of twelve equal $888.49 monthly payments, the interest share shrinking from $100 to $8.79 while the principal share grows](images/03-financial-statement-math-fig-03.png)
*Figure 3.3 — Each level $888.49 payment shifts from mostly interest to mostly principal — never an even split.*

This kills a stubborn misconception: that a level payment splits evenly between interest and principal. It does not. Early payments are mostly interest (because the balance is largest); late payments are mostly principal. The whole schedule is a geometric process — the balance declines following the same compound machinery as everything else in Part I.

## Worked examples

**Example 1 — Reading two firms (the cold open).** Retailer: net margin $= 30/100 = 30\%$. Manufacturer: $30/50{,}000 = 0.06\%$. The ratio supplies the scale the raw $30M hid. If we add that the retailer carries $40M of equity and the manufacturer $20B, their ROEs are $30/40 = 75\%$ versus $30/20{,}000 = 0.15\%$ — the gap widens further. Same profit, two different worlds, visible only through the quotient.

**Example 2 — Depreciation timing, same total.** The $40,000 truck (salvage $5,000, 7-year life). Straight-line: $5,000/yr for seven years, totaling $35,000 of depreciation. DDB at 28.6%: Year 1 $11,440; Year 2 $8,168; Year 3 $5,832; and so on, the same $35,000 in total but front-loaded — over half the depreciation taken in the first three years. A firm choosing DDB for tax defers tax into later years (a real cash benefit via the time value of money) while the asset's book value plunges early. Timing differs; the total does not.

**Example 3 — DuPont diagnosis.** Two firms, each ROE = 25%. Firm A: net margin 10%, asset turnover 1.0, equity multiplier 2.5 ($0.10\times 1.0\times 2.5 = 0.25$). Firm B: net margin 12.5%, asset turnover 2.0, equity multiplier 1.0 ($0.125\times 2.0\times 1.0 = 0.25$) [verify]. Identical ROE; Firm A's comes from leverage (it carries 2.5× its equity in assets), Firm B's from operations. In a recession, Firm A's interest payments are fixed while its margins compress — the multiplier that lifted ROE in good times now amplifies the fall. The decomposition turned one number into a risk diagnosis.

## Return to the cold open

The analyst who called the two firms "equally profitable" read a numerator without a denominator. The cure is the ratio: net margin of 30% versus 0.06% tells the real story, and the DuPont decomposition would go further — splitting each firm's return into the margin, turnover, and leverage that produced it, so you could see *why* one is healthy and the other precarious. The deeper lesson is that none of this lives in the raw statement figures; it lives in the act of dividing one figure by another with judgment about *which* denominator answers your question. Excel computes the quotient. Knowing that a 0.8 current ratio is fine for a fast-food chain and a red flag for a manufacturer — that is the analyst, not the spreadsheet.

## Where it generalizes

The three tools radiate outward. **Ratios** are the language of credit (debt covenants set minimum times-interest-earned levels a borrower must hold), equity research, and the bankruptcy-prediction models that combine several ratios into one score (Altman's Z-score, 1968) [verify]. The **geometric sequence** under declining-balance depreciation is the same $(1+r)^n$ machinery you met in Chapter 1 and will meet again as compound interest in Chapter 4; recognizing it as one object is the point of the book. The **annuity/geometric-series** structure under amortization *is* Chapter 4 — the level loan payment is the annuity payment, and the schedule is what that payment generates. And the **common-size statement** (every income-statement line as a percent of revenue, every balance-sheet line as a percent of total assets) is just Chapter 1's percentage arithmetic applied down a whole statement, so firms of wildly different size can be laid side by side.

## Exercises

1. A firm has current assets of $4.2M and current liabilities of $3.0M; total debt of $9M and equity of $6M. Compute its current ratio and debt-to-equity ratio, and state in one sentence what each tells a different stakeholder (a supplier; a bondholder).

2. A company posts net income $8M, sales $80M, total assets $160M, equity $40M. Compute net margin, asset turnover, equity multiplier, and ROE, and verify that the three drivers multiply to the ROE.

3. A $25,000 machine has a $5,000 salvage value and a 5-year life. Compute the straight-line annual depreciation, and the first two years of double-declining-balance depreciation. Confirm the methods would depreciate the same total over the asset's life.

4. **(Derive.)** Show that under declining-balance depreciation at rate $r$, the book value after $n$ years is $\text{cost}\times(1-r)^n$, and use this to explain why the method never reaches exactly zero. What does a firm do about that in practice?

5. **(Build a schedule.)** A $20,000 loan carries a 0.5% monthly rate over 6 months and a level payment of $A = \$3{,}385.06$. Build the full six-row amortization schedule (interest, principal, ending balance). Then explain, citing your own numbers, why the claim "each payment is half interest, half principal" is false.

## Sources

- Alexander Wall, "Study of Credit Barometrics," *Federal Reserve Bulletin* (March 1919), and *Ratio Analysis of Financial Statements* (1924) — the founding comparative ratio study across 981 firms. [verify]
- F. Donaldson Brown / DuPont — the DuPont ROE decomposition into margin, turnover, and leverage. [verify]
- Edward I. Altman, "Financial Ratios, Discriminant Analysis and the Prediction of Corporate Bankruptcy," *Journal of Finance* (1968) — the Z-score combining ratios into a predictive score. [verify]
- MBA-Accounting, depreciation chapter — the $40,000 delivery-truck worked example across straight-line and double-declining-balance methods. [verify]
- MBA-Finance, ratio-analysis chapter — the same-number-opposite-story cold open and the DuPont leverage-vs-operations contrast. [verify]
