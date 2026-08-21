# The Cost of Capital: Risk, Return, CAPM, and WACC

*Where the discount rate finally comes from — and why "cost of equity" is just the equation of a straight line.*

## The cold open

Three chapters ago, two offers turned on an unstated rate. Two chapters ago, a $100 project's NPV turned on a 9% discount rate that simply appeared on the slide, and we promised to come back for it. Here is the unfinished business, in the form a CFO actually faces.

An analyst presents a project valued at the firm's "8.0% weighted-average cost of capital." Where did 8.0% come from? Trace it back and it dissolves into six estimates: a risk-free rate of 4.2%, a stock beta of 1.1, an equity risk premium of 5.0%, a cost of debt of 5.2%, a tax rate of 24%, and a 30% debt weight (the structure of the WACC case in MBA-Corporate-Finance) [verify]. Change the beta to 0.9 or the equity premium to 6%, both perfectly defensible, and the "8.0%" becomes anything from about 7.5% to 9.6%. That 200-basis-point range is not rounding error — it is wide enough to flip a marginal project from accept to reject. The discount rate that looked like a fact is a contested estimate wearing one decimal place of false precision.

This chapter builds that number from the ground up, and the build is mostly arithmetic you already own: an expected value, a covariance ratio, the equation of a line, and a weighted average. The math is mechanical. The judgment about what to feed it is the whole job.

## The tool, named

The **cost of capital** is the return a firm must earn to satisfy the investors who funded it — and therefore the discount rate it should use to value its projects. It is built in three layers:

- **Expected return and risk** — return as an expected value $E[r]$, risk as variance/standard deviation. (A probability idea, previewing Part III.)
- **The Capital Asset Pricing Model (CAPM)** — the cost of *equity*, $E[r_i] = r_f + \beta_i(E[r_m] - r_f)$, where **beta** $\beta_i = \text{Cov}(r_i, r_m)/\text{Var}(r_m)$ measures how much a stock moves with the market.
- **The weighted-average cost of capital (WACC)** — the firm's blended rate, $\text{WACC} = \frac{E}{V}R_e + \frac{D}{V}R_d(1-T)$, a value-weighted average of equity and after-tax debt costs.

## Development and derivation

### Return as expectation, risk as variance

An investment's return is uncertain. We summarize the uncertainty with two numbers from probability (developed fully in Part III). The **expected return** is the probability-weighted average of possible returns,

$$E[r] = \sum_s p_s\, r_s,$$

and the **risk** is the variance (or its square root, the standard deviation), the probability-weighted average squared deviation from that mean,

$$\text{Var}(r) = \sum_s p_s\,(r_s - E[r])^2.$$

Markowitz's insight (1952) was that for a *portfolio*, what matters is not each asset's variance in isolation but how the assets **co-move** — their covariances [verify]. An asset that zigs when the market zags reduces portfolio risk even if it is volatile on its own. This is the seed of beta and of the diversification logic we develop in Chapter 10. The key takeaway here: the risk that earns a premium is not an asset's total wiggle, but the part of its wiggle that moves *with the market* — the part you cannot diversify away.

### Beta as a covariance ratio (and a regression slope)

That market-linked risk is captured by **beta**. Formally it is the covariance of the asset's return with the market's, scaled by the market's variance:

$$\boxed{\;\beta_i = \frac{\text{Cov}(r_i, r_m)}{\text{Var}(r_m)}.\;}$$

This is not finance jargon — it is exactly the **slope of the regression line** of the asset's returns on the market's returns (the least-squares slope we derive in Chapter 9 is $\text{Cov}(x,y)/\text{Var}(x)$, the same object with $x = r_m$). So beta has a plain reading: if you scatter-plot the stock's monthly returns against the market's and fit a line, beta *is* the slope. A beta of 1.1 means that when the market moves 1%, the stock tends to move 1.1% — it amplifies the market by ten percent. A beta of 0.7 dampens it; a beta of 1 tracks it.

The common student error is to read beta as "volatility." It is not. It is **co-movement** — the sensitivity to the market specifically. A wildly volatile stock whose swings are unrelated to the market has a low beta, because its idiosyncratic noise diversifies away and earns no premium.

> **Beta is an estimate, not a fact.** Its value depends on the lookback window, the return frequency, and the chosen market index. Two data providers report different betas for the same firm on the same day, with standard errors around 0.15–0.25 [verify] — so "$\beta = 1.1$" honestly means "somewhere around 0.9 to 1.3."

### CAPM: the cost of equity is $y = mx + b$

Now the payoff. The **Capital Asset Pricing Model** (Sharpe 1964, independently Lintner 1965 and Mossin 1966 — the Norwegian Mossin being the least-credited of the three) [verify] says the expected return investors demand for holding a stock is the risk-free rate plus a premium for the market risk they bear:

$$\boxed{\;E[r_i] = r_f + \beta_i\,(E[r_m] - r_f).\;}$$

Stare at this and the intimidation drains away. It is the equation of a straight line, $y = b + mx$:

- $y = E[r_i]$, the expected return (what we want — the cost of equity),
- $b = r_f$, the intercept (the risk-free rate),
- $x = \beta_i$, the horizontal variable (the amount of market risk),
- $m = (E[r_m] - r_f)$, the slope (the **equity risk premium**, the extra return per unit of beta).

Plotted with expected return on the vertical axis and beta on the horizontal, this line is the **Security Market Line**. Every asset, in theory, sits on it.

![Security Market Line of expected return against beta with intercept at the 4.2% risk-free rate and slope equal to the 5% equity risk premium; a beta-1.1 stock lands at a 9.7% cost of equity](images/06-cost-of-capital-capm-and-wacc-fig-01.png)
*Figure 6.1 — The Security Market Line: cost of equity is y = mx + b — intercept r_f, slope the equity risk premium.* The "cost of equity" — a phrase that sounds like accounting — is just where your stock's beta lands you on a line whose height is set by the risk-free rate and whose tilt is set by the market's risk premium. High-school algebra, dressed for a board meeting.

The contested input here is the **equity risk premium** $(E[r_m] - r_f)$ — "the most contested input in corporate finance." Historical estimates run 4–7% depending on the period, the geography, and whether you use an arithmetic or geometric mean; forward-looking estimates cluster around 4–5%; and the *equity-premium puzzle* (Mehra and Prescott, 1985) notes that the historical premium is hard to reconcile with plausible risk aversion at all [verify]. There is no settled value. CAPM itself is empirically imperfect — Fama and French (1992) showed beta alone poorly explains the cross-section of returns, and size and value factors do better — yet CAPM remains the practitioner default, a genuine theory-versus-practice gap worth naming honestly [verify].

### WACC: a value-weighted average

A firm is funded by both equity and debt, which demand different returns. The **weighted-average cost of capital** blends them by their market values. Let $E$ and $D$ be the market values of equity and debt, $V = E + D$, with $R_e$ the cost of equity (from CAPM) and $R_d$ the cost of debt:

$$\boxed{\;\text{WACC} = \frac{E}{V}\,R_e + \frac{D}{V}\,R_d\,(1 - T).\;}$$

The structure is a plain weighted average — the same arithmetic as a grade-point average, weights summing to one. Two refinements carry real content:

- **Use market weights, not book.** The relevant cost is what current investors require, which attaches to market values; book values are historical accounting artifacts.
- **Debt is after-tax.** Interest is tax-deductible, so each dollar of interest costs the firm only $R_d(1-T)$ after the tax shield. This is the Modigliani–Miller (1963) result — the tax-deductibility of interest adds value and is *why* the debt term carries the $(1-T)$ factor [verify]. It is also why moderate leverage can lower WACC: cheap, tax-favored debt replaces expensive equity, up to the point where rising bankruptcy risk pushes both costs back up.

### Putting it together — and reporting honestly

Build the cold open's number from the parts. Cost of equity by CAPM: $R_e = 4.2\% + 1.1\times 5.0\% = 4.2\% + 5.5\% = 9.7\%$. After-tax cost of debt: $5.2\%\times(1 - 0.24) = 3.95\%$. Weighted by 70% equity and 30% debt:

$$\text{WACC} = 0.70\times 9.7\% + 0.30\times 3.95\% = 6.79\% + 1.19\% = 7.98\% \approx 8.0\%.$$

![Stacked contribution bar showing WACC of 7.98% built from 70% equity at 9.7% contributing 6.79 points and 30% debt at 3.95% after-tax contributing 1.19 points, beside a 7.5 to 9.6 percent sensitivity band](images/06-cost-of-capital-capm-and-wacc-fig-02.png)
*Figure 6.2 — WACC as a value-weighted average: 7.98% built from its parts, with a 200-bp band once β and the equity premium flex.*

There is the 8.0%. But now flex the two contested inputs across a sensitivity grid — beta over $\{0.9, 1.1, 1.3\}$ and equity premium over $\{4.5\%, 5.0\%, 6.0\%\}$ — and the WACC ranges from about 7.5% to 9.6% [verify], with the headline 8.0% sitting near the *low* (optimistic) corner. The right deliverable is not "8.0%." It is "between roughly 7.5% and 9.6%, most likely near 8%, and here is exactly which input would change the decision." A CFO who treats WACC as a looked-up fact has quietly handed capital-allocation authority to whoever last updated the beta cell.

## Worked examples

**Example 1 — Cost of equity from CAPM.** Risk-free rate 4%, beta 1.2, equity risk premium 5%. Then $R_e = 4\% + 1.2\times 5\% = 10\%$. Raise beta to 1.4 and $R_e = 4\% + 7\% = 11\%$ — the line is steeper for riskier stocks. Read it off the Security Market Line: higher beta, higher demanded return.

**Example 2 — Beta as a slope.** Over twelve months a stock and the market produce returns whose covariance is $\text{Cov}(r_i, r_m) = 0.0021$ and whose market variance is $\text{Var}(r_m) = 0.0015$. Then $\beta = 0.0021/0.0015 = 1.4$. Equivalently, regressing the stock's returns on the market's would yield a fitted line of slope 1.4 — the stock amplifies market moves by 40%.

**Example 3 — Full WACC with the tax shield.** A firm: market equity $700M, market debt $300M ($V = \$1{,}000\text{M}$), cost of equity 10%, pre-tax cost of debt 6%, tax rate 25%.
$$\text{WACC} = \frac{700}{1000}(10\%) + \frac{300}{1000}(6\%)(1 - 0.25) = 7.0\% + 0.3\times 4.5\% = 7.0\% + 1.35\% = 8.35\%.$$
Forget the tax shield and you'd overstate the debt cost (using 6% instead of 4.5%), pushing WACC to 8.8% — a 45-basis-point error from a single dropped $(1-T)$.

## Return to the cold open

The "8.0%" was real arithmetic — CAPM for the cost of equity, the after-tax debt cost, and a value-weighted average — and we reproduced it exactly. But it is arithmetic on six estimates, two of them (beta and the equity premium) genuinely contested, and flexing them within their defensible ranges moves the WACC across a 200-basis-point band that can flip the project. So the honest answer to "where did 8.0% come from?" is: from a model that is mechanical to compute and fragile to its inputs. The discount rate that Chapter 4 left unspecified and Chapter 5 used on faith is now built — and the act of building it reveals that the right output is a *range with a named decision-driver*, not a false-precision point. That is the lesson the spreadsheet cannot teach: it will compute WACC to four decimals from whatever beta you type, and it will never tell you the beta is really "0.9 to 1.3."

## Where it generalizes

The cost of capital closes the loop of Part II: the $r$ that discounted cash flows in **Chapter 4** and valued projects, bonds, and stocks in **Chapter 5** is the WACC (for whole-firm projects) or the CAPM cost of equity (for equity valuation in the Gordon model). It reaches forward, too. Beta as a covariance ratio is the regression slope of **Chapter 9** and the covariance machinery of **Chapter 10**'s portfolio math — the same statistical object, three contexts. Expected value and variance are the probability foundations of **Chapter 7**. And the judgment-call structure — a precise-looking number resting on a contested range — recurs wherever a model's output is only as trustworthy as its most arguable input, which in finance is nearly everywhere. Project- and division-specific discount rates (via comparable-firm "pure-play" betas) and capital-structure decisions (how leverage moves beta, $R_e$, and WACC) are the natural next applications, taken up in the corporate-finance course this chapter refreshes.

## Exercises

1. A stock has a beta of 0.8. The risk-free rate is 3.5% and the expected market return is 9%. Use CAPM to find the cost of equity. Then find it if beta rises to 1.3, and state which input is the "slope" and which is the "intercept."

2. Compute beta from data: the covariance of a stock's returns with the market is 0.0018 and the market variance is 0.0020. Interpret the result in one sentence about co-movement.

3. A firm has market equity of $1.2B and market debt of $0.8B, a cost of equity of 11%, a pre-tax cost of debt of 7%, and a 30% tax rate. Compute the WACC, and recompute it ignoring the tax shield to show the size of the error.

4. **(Derive / reframe.)** Show that the CAPM equation $E[r_i] = r_f + \beta_i(E[r_m]-r_f)$ has the form $y = b + mx$, identifying $y$, $x$, the slope, and the intercept. Then explain in two sentences why a stock with high *total* volatility but near-zero correlation with the market has a low beta and therefore a low cost of equity.

5. **(Build a sensitivity grid.)** Using $r_f = 4\%$, debt cost 5%, tax 25%, and weights 60% equity / 40% debt, compute WACC for every combination of $\beta \in \{0.9, 1.1, 1.3\}$ and equity risk premium $\in \{4\%, 5\%, 6\%\}$. Report the range, identify the corner that gives the lowest WACC, and write the one sentence you would actually present to a decision-maker instead of a single point estimate.

## Sources

- Harry Markowitz, "Portfolio Selection," *Journal of Finance* (1952) — mean–variance framework; portfolio risk depends on covariances. [verify]
- William F. Sharpe, "Capital Asset Prices," *Journal of Finance* (1964); John Lintner (1965); Jan Mossin (1966) — the independent developments of the CAPM. [verify]
- Franco Modigliani and Merton Miller, "The Cost of Capital, Corporation Finance and the Theory of Investment," *American Economic Review* (1958), and the 1963 tax correction — the after-tax cost of debt and the interest tax shield. [verify]
- Eugene Fama and Kenneth French (1992, 2004) — empirical evidence that beta alone poorly explains the cross-section of returns; the size and value factors. [verify]
- Rajnish Mehra and Edward Prescott, "The Equity Premium: A Puzzle" (1985) — the unresolved size of the historical equity premium. [verify]
- MBA-Corporate-Finance, cost-of-capital chapter — the six-input WACC trace and the β × ERP sensitivity grid (7.5%–9.6%). [verify]
