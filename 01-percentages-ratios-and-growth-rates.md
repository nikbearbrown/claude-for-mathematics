# Percentages, Ratios, and Growth Rates

*The one operation — multiply by $(1+r)$ — that the rest of the book is built on.*

## The cold open

A division head stands up in a planning meeting and reports the year. "Revenue grew 40% in the first half," she says, "then the second half was rough — it fell 40%. So we ended roughly where we started." Heads nod. It sounds right. Up forty, down forty, back to even.

She started the year at $100 million. She ended it at $84 million — sixteen million dollars short of "where we started," a gap nobody in the room has noticed. The error is not in her arithmetic; each 40% is correct on its own base. The error is in the word *so*. She has added two percentage changes that the world multiplies, and the difference between adding and multiplying is exactly the $16 million that quietly went missing.

![Number line tracing $100M up 40% to $140M then down 40% to $84M, with the $16M gap marked as the dropped cross-term](images/01-percentages-ratios-and-growth-rates-fig-01.png)
*Figure 1.1 — Up 40%, then down 40%, lands at $84M — the $16M gap is the cross-term ab.*

This is the most common quantitative mistake in business, and it is not really about percentages. It is about a single operation — turning a percentage change into a *factor* and multiplying — that recurs, unchanged, as a price change, an interest rate, an inflation adjustment, a stock return, and a growth assumption. Get this one operation into your hands and a surprising amount of the rest of this book becomes one idea applied over and over. Get it wrong and you will lose $16 million in a sentence.

## The tool, named

A **percentage change** is multiplicative, not additive. A quantity that changes by $r$ (written as a decimal: 40% is $r = 0.40$) becomes

$$\text{new} = \text{old} \times (1 + r).$$

The object $(1+r)$ is the **growth factor**. Successive changes *multiply their factors*; they do not add their rates. From this single fact flow compound growth, the compound annual growth rate (CAGR), the difference between percentage points and percent, and the difference between nominal and real figures. Everything in this chapter is a consequence of $\text{new} = \text{old}\times(1+r)$.

## Development and derivation

### Why successive changes don't add

Take a base of $100. Apply a change of $a$, then a change of $b$. The first change gives $100(1+a)$. The second change applies to *that* new amount, not the original:

$$100 \,(1+a)(1+b).$$

Multiply the two factors out:

$$(1+a)(1+b) = 1 + a + b + ab.$$

There it is. The additive intuition expects $1 + a + b$ — "just add the two rates." The world delivers $1 + a + b + \mathbf{ab}$. That extra cross-term $ab$ is the entire discrepancy. It is the interest-on-interest, the growth-on-growth, the piece additive reasoning silently drops.

Return to the cold open with $a = +0.40$ and $b = -0.40$:

$$(1 + 0.40)(1 - 0.40) = 1 + 0.40 - 0.40 + (0.40)(-0.40) = 1 - 0.16 = 0.84.$$

The $a + b$ part cancels to zero, exactly as intuition expects. What remains is the cross-term $ab = -0.16$ — a 16% loss no matter what order the changes come in. Up-then-down or down-then-up, $(1.4)(0.6) = (0.6)(1.4) = 0.84$. You cannot undo an $x\%$ gain with an $x\%$ loss, because the loss is taken on a larger base.

> **Reversal error.** The mathematics-education literature has long documented that even the easiest version — up 50%, then down 50% — trips up a substantial share of students, the dominant wrong answer being "it returns to the original" (a well-established finding in the percentage-reasoning literature; the exact rate here is illustrative). The fix is not a warning; it is seeing the $ab$ term on the page.

### Percentage points versus percent

A second, related trap. Suppose an interest rate moves from 4% to 6%. How much did it rise?

- In **percentage points**: $6 - 4 = 2$ percentage points. (You subtract the rates directly.)
- In **percent**: the rate is $50\%$ higher, because $\frac{6-4}{4} = 0.50$.

Both are correct; they answer different questions. "Two percentage points" describes the change in the rate's *level*; "fifty percent" describes the change *relative to the starting rate*. A central bank that raises rates from 4% to 6% has raised them by 2 points or by 50% — and a headline that mixes the two is misinforming its readers. Define which you mean at first use, every time.

### Compound growth and CAGR

Now let the same factor repeat. A quantity growing at a constant rate $g$ per period for $n$ periods is multiplied by $(1+g)$ each period:

$$\text{end} = \text{start} \times (1+g)^n.$$

This is the **compound-growth identity** — the master formula of Part II already, in miniature. Often we observe the start and the end and want the constant rate that connects them. Solve for $g$. Divide:

$$\frac{\text{end}}{\text{start}} = (1+g)^n.$$

Take the $n$-th root of both sides:

$$\left(\frac{\text{end}}{\text{start}}\right)^{1/n} = 1 + g,$$

and subtract one:

$$\boxed{\;\text{CAGR} = g = \left(\frac{\text{end}}{\text{start}}\right)^{1/n} - 1.\;}$$

That is the **compound annual growth rate**. It is the single constant rate that, compounded over $n$ periods, takes you from start to end. Geometrically, it is the smooth exponential path with the same endpoints as the actual jagged year-to-year series.

![Two growth curves from $5,000 to $25,000 over 40 years: the true 4.10% compound path versus the naive 10% per year average that shoots off the chart](images/01-percentages-ratios-and-growth-rates-fig-02.png)
*Figure 1.2 — A fivefold rise over 40 years is 4.10% compounded, not 10% per year.*

Notice what CAGR is *not*: it is not the average of the yearly growth rates. If revenue doubles over four years, the CAGR is $(2)^{1/4} - 1 = 18.9\%$, not $100\%/4 = 25\%$. The arithmetic average of the rates ignores compounding (the $ab$ cross-terms again); CAGR is the **geometric mean** of the growth factors, which is the only average that respects multiplication. This is why a realized multi-year return is always reported as a geometric mean, never an arithmetic one.

> **Which average?** The arithmetic mean of period returns answers "what return do I *expect* in a single typical period?" The geometric mean (CAGR) answers "what constant rate did I *actually* realize over the whole stretch?" Both are legitimate; they answer different questions, and the arithmetic mean is always at least as large. Practitioners genuinely disagree about which to headline [contested — see pantry]. State which one you mean.

### Nominal versus real

A dollar of revenue this year and a dollar five years ago are not the same dollar if prices have moved between them. A **nominal** figure is in the dollars of its own day; a **real** figure is adjusted to a common purchasing power. The exact relation is the **Fisher equation** (Irving Fisher, *The Theory of Interest*, 1930) [verify]:

$$(1 + i_{\text{nominal}}) = (1 + i_{\text{real}})(1 + \pi),$$

where $\pi$ is the inflation rate. Solving for the real rate,

$$i_{\text{real}} = \frac{1 + i_{\text{nominal}}}{1 + \pi} - 1.$$

The common shortcut $i_{\text{real}} \approx i_{\text{nominal}} - \pi$ comes from dropping the cross-term once more — it is fine for small rates and wrong for large ones. If a stock returns 8% nominal in a year of 6% inflation, the careless answer is "2% real"; the exact answer is $\frac{1.08}{1.06} - 1 = 1.89\%$. The same multiplicative structure, the same dropped cross-term.

### Index numbers

When the goal is comparison over time rather than levels, **index numbers** rescale a series so a chosen base period equals 100. Each value is divided by the base-period value and multiplied by 100:

| Year | Revenue | Index (Year 1 = 100) |
|---|---|---|
| 1 | $80M | 100.0 |
| 2 | $92M | 115.0 |
| 3 | $110M | 137.5 |

You read growth straight off the index: by Year 3 the series stands at 137.5, i.e. 37.5% above the base. The index strips out the units and the scale, so a $80M firm and an $8B firm can be laid on the same chart and compared by *shape*. Price indices like the Consumer Price Index are exactly this idea applied to a basket of goods, and they are the machinery that converts a nominal series into a real one — divide each nominal figure by the price index (rebased) and you have it in constant dollars. (The economist **Hazel Kyrk** helped establish the base-period prices behind the U.S. cost-of-living index and chaired the technical committee that revised the CPI in the mid-1940s — a direct builder of the machinery this section uses [verify].)

## Worked examples

**Example 1 — The reversal, in full.** A product line bills $100M in H1, grows 40%, then falls 40% in H2. Growth factor for the year: $(1.40)(0.60) = 0.84$. Ending revenue: $100 \times 0.84 = \$84\text{M}$. The "back to even" claim overstates the year by $\$16\text{M}$, which is precisely $100 \times |ab| = 100 \times (0.40)(0.40)$. Order doesn't matter: down 40% then up 40% also lands at $\$84\text{M}$.

**Example 2 — Tuition CAGR.** A university's annual tuition rose from $5,000 in 1985 to $25,000 in 2025 — a fivefold increase over $n = 40$ years (drawn from the MBA-Finance time-value chapter) [verify]. The "average" increase is *not* $400\%/40 = 10\%$ per year. It is

$$\text{CAGR} = (5)^{1/40} - 1 = e^{(\ln 5)/40} - 1 = e^{0.0402} - 1 = 4.10\%\text{ per year.}$$

A 4.1% compound rate, sustained for forty years, quintuples a number. (The **Rule of 72** — doubling time $\approx 72/r$ — confirms it: at 4.1%, money doubles in about $72/4.1 \approx 17.6$ years, so 40 years is a bit more than two doublings, a bit more than fourfold. Five checks out.)

![Bar chart of $100 rising to $150 then falling to $75, contrasting the 0% arithmetic average return with the minus 13.4% realized geometric return](images/01-percentages-ratios-and-growth-rates-fig-03.png)
*Figure 1.3 — +50% then −50%: the arithmetic average says 0%, but the money lost 13.4% per year.*

**Example 3 — Arithmetic versus geometric, made concrete.** An investment returns $+50\%$ one year and $-50\%$ the next. The *arithmetic* average return is $(50\% - 50\%)/2 = 0\%$ — which sounds like a wash. But $\$100$ grows to $\$150$, then falls to $\$75$: the *realized* (geometric) return is $(75/100)^{1/2} - 1 = -13.4\%$ per year. The investor lost a quarter of their money over two years, while the arithmetic average reported zero. The arithmetic mean answers "what is my expected return in a typical single year?"; the geometric mean (CAGR) answers "what did I actually earn?" — and the gap between them grows with volatility. Reporting the arithmetic average of volatile returns as if it were realized growth is the cold-open error in formal dress.

**Example 4 — Nominal versus real growth.** A firm reports revenue up 8% in a year when inflation ran 6%. Nominal growth: 8%. Real growth: $\frac{1.08}{1.06} - 1 = 1.89\%$. The business grew, in purchasing-power terms, by less than two points — three-quarters of the headline number was inflation. After a decade of near-zero inflation when this gap was ignorable, the 2021–2023 inflation surge made the distinction decision-relevant again; its salience rises and falls with the rate environment.

## Return to the cold open

The division head's instinct — "up 40, down 40, so we're even" — added two rates that the world multiplies. The correct statement is that her year had a growth factor of $(1.40)(0.60) = 0.84$, so the division *shrank 16%*, from $100M to $84M. The missing $16 million is the cross-term $ab$, the growth-on-growth that additive intuition drops. Had she wanted the single constant rate describing her year, it would be the CAGR over two half-years, $(0.84)^{1/2} - 1 = -8.3\%$ per half — a decline, plainly, not a wash. The math doesn't punish her for a bad year; it punishes her for treating $(1+a)(1+b)$ as $1 + a + b$.

## Where it generalizes

The operation $\text{new} = \text{old}\times(1+r)$ is the floor of this entire book. In **Chapter 4** the factor $(1+r)$ becomes the period interest rate and $(1+g)^n$ becomes the compound-growth engine of present and future value. In **Chapter 5** the growing-perpetuity formula $C/(r-g)$ — the engine of stock valuation — is this chapter's compound growth pushed to infinity. In **Chapter 3** declining-balance depreciation is $(1-r)^n$, the same factor with a minus sign. In accounting's **horizontal and common-size analysis** every year-over-year line is a percentage change; in finance, "the market returned 10%" is ambiguous between arithmetic and geometric mean and between nominal and real until you say which. Learn to move fluently between a rate, a change, and a compounded factor here, and you will not have to relearn it disguised as something else four more times.

## Exercises

1. A stock rises 25% in year one and falls 20% in year two. What is the total two-year return? What constant annual rate (CAGR) would have produced the same ending value?

2. A savings account advertises a rate that rose "from 2% to 3%." Express the increase both in percentage points and in percent, and write one sentence a journalist could use that is unambiguous.

3. Revenue goes $\$40\text{M} \to \$48\text{M} \to \$60\text{M}$ over two years. Compute the two year-over-year growth rates, their arithmetic average, and the CAGR. Explain in one sentence why the CAGR is not the arithmetic average.

4. **(Derive.)** Starting from $(1+a)(1+b) = 1 + a + b + ab$, prove that an $x\%$ gain followed by an $x\%$ loss always leaves you below your starting point for any $x > 0$, and give an exact formula for the fraction lost.

5. **(Derive and apply.)** Starting from the Fisher equation, derive the exact real return and show that the approximation $i_{\text{real}} \approx i_{\text{nominal}} - \pi$ understates or overstates the true real return — say which, and why, in terms of the dropped cross-term. Then compute the exact and approximate real return for a 12% nominal return at 9% inflation.

## Sources

- Irving Fisher, *The Theory of Interest* (Macmillan, 1930) — the Fisher equation relating nominal, real, and inflation rates. [verify]
- Irving Fisher, *The Making of Index Numbers* (Houghton Mifflin, 1922) — foundational treatment of index-number construction and geometric averaging. [verify]
- "The problem with percentages" (open-access review of percentage-misconception studies, summarizing Parker and colleagues), 2018 — the reversal-error finding. [verify]
- "Compound annual growth rate," reference entry — CAGR as the geometric mean of growth factors. [verify]
- Biographical entry for Hazel Kyrk — her role in establishing CPI base-period prices and the mid-1940s CPI revision. [verify]
- MBA-Finance, time-value-of-money chapter — the tuition CAGR and Rule-of-72 worked examples. [verify]
