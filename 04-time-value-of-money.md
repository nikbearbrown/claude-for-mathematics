# The Time Value of Money

*One operation — multiply or divide by $(1+r)$ per period — generates all of finance's valuation arithmetic.*

## The cold open

Someone offers you a choice. Take $1,000,000 today, or take $1,200,000 in three years. The second number is bigger — twenty percent bigger — and the instinct in the room is that more dollars wins. A few people hesitate. They're right to.

The choice has no answer until you supply one missing number: the rate you could earn on the million if you took it now. If you can invest at 8%, the million grows to $1{,}000{,}000\times(1.08)^3 = \$1{,}259{,}712$ in three years — *more* than the $1.2M offer, so take the cash today. If you can only earn 5%, it grows to $1{,}157{,}625$ — *less* than the offer, so wait for the $1.2M. The bigger number does not win; the bigger *present value* wins, and which is bigger flips on a rate nobody stated. There is even a break-even rate that makes you indifferent: the $r$ solving $1{,}000{,}000(1+r)^3 = 1{,}200{,}000$, which is $(1.2)^{1/3} - 1 = 6.27\%$. Above it, take the cash; below it, wait.

![Cash-flow timeline comparing $1M today against $1.2M in three years, with a discount arc bringing the future amount back and two rate outcomes flipping the decision at the 6.27% break-even](images/04-time-value-of-money-fig-01.png)
*Figure 4.1 — The bigger present value wins, not the bigger number — and which is bigger flips on the rate.*

This is the time value of money, and it rests on a single operation you already met in Chapter 1: multiply by $(1+r)$ to move a dollar *forward* in time, divide by $(1+r)$ to move it *back*. Everything in this chapter — and most of the two that follow — is that one operation applied to more cash flows. Own it once and finance stops being a list of formulas.

## The tool, named

The **time value of money (TVM)** is the principle that a dollar today is worth more than a dollar later, because today's dollar can be invested to grow. The mathematical engine is the **compound-growth identity** from Chapter 1, now read as a money machine:

$$\text{FV} = \text{PV}\,(1+r)^n,$$

where PV is **present value** (the amount today), FV is **future value** ($n$ periods later), and $r$ is the per-period rate. The factor $(1+r)^n$ moves money forward; its reciprocal $1/(1+r)^n$ — the **discount factor** — moves money back. From this one relation we will build present and future value, annuities, perpetuities, growing perpetuities, and the adjustments for compounding frequency, continuous compounding, and inflation.

## Development and derivation

### The master formula and its four directions

The relation $\text{FV} = \text{PV}(1+r)^n$ has four quantities. Know any three and solve for the fourth — this is the "solve for the unknown" move of Chapter 2, now with real stakes:

- **Future value:** $\text{FV} = \text{PV}(1+r)^n$ — grow a present amount forward.
- **Present value:** $\text{PV} = \dfrac{\text{FV}}{(1+r)^n} = \text{FV}\times\dfrac{1}{(1+r)^n}$ — discount a future amount back.
- **Implied rate:** $r = \left(\dfrac{\text{FV}}{\text{PV}}\right)^{1/n} - 1$ — this is exactly the CAGR of Chapter 1.
- **Required time:** $n = \dfrac{\ln(\text{FV}/\text{PV})}{\ln(1+r)}$ — and the **Rule of 72** ($n_{\text{double}}\approx 72/r$) is the mental-math shortcut, since doubling means $\text{FV}/\text{PV}=2$ and $\ln 2 \approx 0.693$ [verify].

The discount factor $1/(1+r)^n$ deserves a stare. Lay it out across rates and horizons and the pattern is stark:

| Discount factor $1/(1+r)^n$ | $n=1$ | $n=10$ | $n=30$ |
|---|---|---|---|
| $r=4\%$ | 0.962 | 0.676 | 0.308 |
| $r=7\%$ | 0.935 | 0.508 | 0.131 |
| $r=10\%$ | 0.909 | 0.386 | 0.057 |

![Three decay curves of the discount factor over thirty years at rates of 4, 7, and 10 percent, the 10 percent curve falling below six cents at year thirty](images/04-time-value-of-money-fig-02.png)
*Figure 4.2 — The discount factor 1/(1+r)ⁿ collapses with time and rate — under six cents at 10% over 30 years.*

A dollar one year out at 4% is worth almost a full dollar today; the same dollar 30 years out at 10% is worth less than six cents. **High rates crush distant cash flows** — which is why a startup's far-future profits are worth so little today, why a small change in $r$ swings a long-horizon valuation so violently, and why the choice of $r$ (the subject of Chapter 6) matters as much as the cash-flow forecast itself.

### Valuing a stream: the annuity factor from a geometric series

Most finance problems involve not one future payment but a *stream* — a loan's payments, a bond's coupons, a retirement contribution every year. An **annuity** is a stream of equal payments $C$ for $n$ periods. Its present value is the sum of each payment discounted back:

$$\text{PV} = \frac{C}{(1+r)} + \frac{C}{(1+r)^2} + \cdots + \frac{C}{(1+r)^n}.$$

This is a **finite geometric series** — each term is the previous one times the constant ratio $x = 1/(1+r)$. We can sum it in closed form rather than adding $n$ terms. Factor out $C$ and write $S = x + x^2 + \cdots + x^n$. Multiply $S$ by $x$:

$$xS = x^2 + x^3 + \cdots + x^{n+1}.$$

Subtract the second line from the first; all the middle terms cancel:

$$S - xS = x - x^{n+1} \quad\Longrightarrow\quad S(1-x) = x(1 - x^n) \quad\Longrightarrow\quad S = \frac{x(1-x^n)}{1-x}.$$

Now substitute back $x = 1/(1+r)$. After simplifying (multiply top and bottom by $(1+r)$, so $1 - x = r/(1+r)$), the present value becomes the clean **annuity factor**:

$$\boxed{\;\text{PV} = C\cdot\frac{1 - (1+r)^{-n}}{r}.\;}$$

That bracketed term is the same denominator that produced the loan payment in Chapter 3's amortization schedule — a loan is just an annuity viewed from the lender's side. We did not memorize this; we summed a geometric series. Every variant below is the same series with a tweak.

### Perpetuities: the $n\to\infty$ limit

What if the payments never stop? Let $n\to\infty$ in the annuity factor. Since $r > 0$, the term $(1+r)^{-n}\to 0$, and the factor collapses to $1/r$:

$$\boxed{\;\text{PV of a perpetuity} = \frac{C}{r}.\;}$$

A stream of $C$ forever is worth $C/r$ today. At $r=5\%$, a perpetual $1,000/year is worth $1{,}000/0.05 = \$20{,}000$ — finite, even though the payments are infinite, because the discount factor crushes distant payments to nothing. This is the deepest counterintuitive result in the chapter and the foundation of stock valuation.

### Growing perpetuities: where the Gordon model comes from

Now let the payment *grow* each period at rate $g$: $C, C(1+g), C(1+g)^2, \dots$. The present value is

$$\text{PV} = \frac{C}{1+r} + \frac{C(1+g)}{(1+r)^2} + \frac{C(1+g)^2}{(1+r)^3} + \cdots.$$

This is again a geometric series, now with ratio $x = (1+g)/(1+r)$. It converges only if $x < 1$ — that is, only if $r > g$ (the rate must exceed the growth, or the sum explodes). Summing the infinite geometric series $C/(1+r)\cdot\frac{1}{1-x}$ and simplifying gives the famous result:

$$\boxed{\;\text{PV of a growing perpetuity} = \frac{C}{r - g}.\;}$$

This is the engine of the Gordon growth model for stocks (Chapter 5) and of the terminal value in a discounted-cash-flow valuation. It also explains a notorious fragility: if $r = 8\%$ and $g$ moves from 2% to 3%, the denominator goes from 6% to 5% and the value jumps 20%. A one-point change in an assumption nobody can pin down swings the valuation enormously — a danger we return to repeatedly.

### Compounding frequency and continuous compounding

A "12% annual rate" compounded monthly is not 12% earned. Split it into $m$ periods of $r/m$ each, compounded $m$ times. The **effective annual rate** is

$$\text{EAR} = \left(1 + \frac{r}{m}\right)^m - 1.$$

At 12% nominal compounded monthly, $\text{EAR} = (1 + 0.12/12)^{12} - 1 = 12.68\%$ — the gap is the interest-on-interest of Chapter 1. Push $m\to\infty$ (compounding every instant) and the limit is **continuous compounding**:

$$\lim_{m\to\infty}\left(1+\frac{r}{m}\right)^{mn} = e^{rn},$$

so $\text{FV} = \text{PV}\cdot e^{rn}$. This is the definition of $e$ in disguise, and it is the bridge to the continuous-time math of later finance.

Finally, the **Fisher equation** from Chapter 1 — $(1 + i_{\text{nom}}) = (1 + i_{\text{real}})(1+\pi)$ — reminds us that the $r$ we discount with should match the dollars we are discounting: nominal cash flows at a nominal rate, real cash flows at a real rate. Mixing them is a category error a spreadsheet will happily commit.

> **When the intuition inverts.** The principle "a dollar today beats a dollar later" assumes $r > 0$. With **negative rates** — episodes seen in Japan, Switzerland, and the Eurozone in the 2010s [verify] — the discount factor $1/(1+r)^n$ exceeds 1, and a future dollar is worth *more* than a dollar today. The *math* is untouched; the *intuition* flips. The arithmetic holds for any $r$, including $r<0$; what is contingent is the sign of the rate the world happens to offer. This is a useful reminder that the formula is permanent while the number it consumes is a fact about a particular time and place.

## Worked examples

**Example 1 — The two offers (the cold open).** $1M today vs. $1.2M in three years. Compare present values at the opportunity rate $r$. The future offer's PV is $1{,}200{,}000/(1+r)^3$. At $r=8\%$: $1{,}200{,}000/1.2597 = \$952{,}600 < \$1\text{M}$, so take the cash. At $r=5\%$: $1{,}200{,}000/1.1576 = \$1{,}036{,}600 > \$1\text{M}$, so wait. The break-even rate, $(1.2)^{1/3}-1 = 6.27\%$, is the knife's edge.

**Example 2 — The early-vs-late saver.** Friend A invests $5,000/year from age 22 to 30 (nine deposits, ~$45,000 contributed), then stops and lets it compound. Friend B waits, then invests $5,000/year from age 30 to 65 (~$175,000 contributed). At an 8% return, A — despite contributing a quarter as much — finishes slightly *ahead* at 65 (the structure of a worked example in MBA-Finance) [verify].

![Two wealth curves at 8 percent growth: early saver A contributing $45k total finishing ahead of late saver B contributing $175k total, because A's early dollars compound longest](images/04-time-value-of-money-fig-03.png)
*Figure 4.3 — Saver A ($45k, ages 22–30) edges out Saver B ($175k, ages 30–65): time does the heavy lifting.* The reason is the discount/compound factor: A's early dollars compound for an extra decade, and $(1.08)^{43}$ is a very large number. Time, not the amount contributed, does the heavy lifting. This is the visceral case for starting early.

**Example 3 — Discounting a single future payment.** A 30-year savings bond pays $1,000 at maturity. At 5%, its value today is $1{,}000/(1.05)^{30} = \$231$ [verify]. A $50,000 lottery payout in 5 years, at 5%, is worth $50{,}000/(1.05)^5 = \$39{,}176$ today [verify]. The discount factor is doing all the work; the further out and the higher the rate, the smaller the present value.

## Return to the cold open

"More dollars wins" was the trap. The right tool is the discount factor: bring the $1.2M back to today by dividing by $(1+r)^3$ and compare it to the $1M in hand. Which offer is larger depends entirely on the rate $r$ you could earn — a number the problem never stated. Above the 6.27% break-even rate, the cash today is worth more; below it, the future $1.2M is. The arithmetic of moving money through time is *exact*; what is *approximate*, and genuinely yours to judge, is the rate you feed it. That gap — exact machinery, contestable rate — is the through-line of all of finance.

## Where it generalizes

This chapter is the spine of Part II and beyond. **Chapter 5** stacks discounted cash flows into net present value (NPV is just "PV of a stream minus the upfront cost"), defines the internal rate of return as the discount rate that zeroes that sum, prices a bond as an annuity of coupons plus a discounted face value, and values a stock with the growing-perpetuity formula $C/(r-g)$ derived above. **Chapter 6** finally answers the question this chapter deliberately leaves open — *what rate $r$ do we use?* — by building it from risk and return (CAPM and WACC). And the geometric-series sum behind the annuity factor reappears in **Chapter 3**'s amortization schedule and anywhere a level stream must be valued: pensions, leases, mortgages, structured settlements. One operation, multiply-or-divide by $(1+r)$, learned once.

## Exercises

1. You will receive $25,000 in 8 years. At a 6% discount rate, what is it worth today? At 9%? Explain in one sentence why the higher rate gives the lower value.

2. An investment turns $10,000 into $18,000 over 6 years. What compound annual rate did it earn? Roughly check your answer with the Rule of 72.

3. A retirement plan will pay $40,000 per year for 20 years, first payment one year from now, at a 5% discount rate. Find its present value using the annuity factor. Then find the value if the payments instead continued *forever* (a perpetuity), and explain why the two numbers are close.

4. **(Derive.)** Starting from the sum $S = x + x^2 + \cdots + x^n$, derive the finite-geometric-series formula and use it to obtain the annuity factor $\frac{1-(1+r)^{-n}}{r}$. Then take the limit $n\to\infty$ to obtain the perpetuity value $C/r$, stating the condition on $r$ that makes the limit valid.

5. **(Derive and stress-test.)** Derive the growing-perpetuity formula $C/(r-g)$ from the infinite geometric series, stating the convergence condition. Then, with $C = \$2$, $r = 8\%$, compute the value at $g = 2\%$ and at $g = 3\%$, and report the percentage change in value caused by the one-point change in $g$.

## Sources

- Irving Fisher, *The Theory of Interest* (Macmillan, 1930) — interest as "the price of time"; present value, discounting, and the Fisher equation. [verify]
- Leonardo of Pisa (Fibonacci), *Liber Abaci* (1202) — early worked compound-interest and present-value problems for merchants. [verify]
- Edmond Halley (1693) — early life-table valuation of life annuities, an actuarial origin of present-value calculation. [verify]
- MBA-Finance, time-value-of-money chapter — the two-offers break-even, the early-vs-late saver, the Rule of 72, and the savings-bond/lottery discounting examples. [verify]
- MBA-Corporate-Finance, capital-budgeting chapter — terminal value as a growing perpetuity, $\text{TV} = \text{FCFF}/(r-g)$. [verify]
