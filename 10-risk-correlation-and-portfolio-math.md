# Risk, Correlation, and Portfolio Math

*The math of why combining risky things can be safer than holding one — and why that proof depends on inputs the math can't supply.*

---

## Why would owning more risky things make me safer?

Maya's father has held the stock of one company for thirty-one years — the company he worked for, the one he knows better than any analyst ever could. When Maya suggests he sell some and buy a broad fund of companies he's never studied, he asks the obvious question: *Why would owning a pile of things I don't understand be safer than owning the one thing I understand completely?* It sounds like advice to trade knowledge for ignorance.

He is not being foolish. The claim genuinely is counterintuitive: that you can take two risky assets, combine them, and end up with something *less* risky than either — that risk, unlike cost, does not simply add up. Most people who have "learned" this still don't believe it in their bones, which is why under-diversified retirement accounts are everywhere. Before we can answer Maya's father, we need to make "risk" a number we can do arithmetic on, and then watch what that arithmetic does when we combine assets. The punchline is going to fall straight out of Chapter 7's variance algebra — the cross term you've already met. The math will *prove* diversification works. Whether *his* diversification works will turn out to depend on something the formula takes for granted.

---

## The tool, named

We measure risk as **variance** (or its square root, **standard deviation**) of returns: how widely outcomes spread around their average. To combine assets we need **covariance** and **correlation** — how two assets' returns move together. The central result is the **two-asset portfolio variance** formula, which we derive by expanding $\operatorname{Var}(w_1 R_1 + w_2 R_2)$. From it comes **diversification** — the reduction of risk by combining imperfectly correlated assets — its **limit** (the floor more assets cannot remove), and the **efficient frontier**, the boundary of best-possible risk–return trade-offs.

---

## Development: risk that does not add up

### Variance and standard deviation as risk

A risky asset's return $R$ is a random variable (Chapter 7). Its expected return $E[R] = \mu$ is what you expect on average; its **variance** $\operatorname{Var}(R) = \sigma^2$ and **standard deviation** $\sigma$ measure how far actual returns scatter around $\mu$. In finance, $\sigma$ *is* risk — the volatility of outcomes. Two assets with the same expected return but different $\sigma$ are not equally attractive: the one with smaller $\sigma$ delivers that average with less white-knuckle variation.

### Covariance and correlation: how two assets move together

The whole game turns on whether two assets move *together*. The **covariance** of returns $R_1$ and $R_2$ is the average product of their deviations from their means:

$$\operatorname{Cov}(R_1, R_2) = E\!\left[(R_1 - \mu_1)(R_2 - \mu_2)\right].$$

Positive covariance: they tend to be above or below their means together. Negative: when one is up, the other tends to be down. Scaled to a unitless $[-1, 1]$ measure, this is the **correlation** (the same $\rho$ as Chapter 9's $r$):

$$\rho = \frac{\operatorname{Cov}(R_1, R_2)}{\sigma_1 \sigma_2}, \qquad -1 \le \rho \le 1.$$

Keep your eye on $\rho$. It is the single number that decides whether combining two assets helps a lot, a little, or not at all.

### The two-asset portfolio variance — expanding the cross term

Put fraction $w_1$ of your money in asset 1 and $w_2 = 1 - w_1$ in asset 2. The portfolio return is the weighted sum

$$R_p = w_1 R_1 + w_2 R_2.$$

Its expected return is the plain weighted average, $E[R_p] = w_1\mu_1 + w_2\mu_2$ — diversification does **not** change your expected return. Now compute the variance. Here is where Chapter 7's algebra earns its keep. Recall $\operatorname{Var}(aX) = a^2\operatorname{Var}(X)$, and that the variance of a *sum* of two variables that are **not** independent picks up a covariance term:

$$\operatorname{Var}(X + Y) = \operatorname{Var}(X) + \operatorname{Var}(Y) + 2\operatorname{Cov}(X, Y).$$

(For *independent* variables, $\operatorname{Cov} = 0$ and this collapses to the "variances add" rule of Chapter 7. The general case keeps the cross term.) Apply both facts to $R_p = w_1 R_1 + w_2 R_2$:

$$\boxed{\;\sigma_p^2 = w_1^2\sigma_1^2 + w_2^2\sigma_2^2 + 2 w_1 w_2 \operatorname{Cov}(R_1,R_2) = w_1^2\sigma_1^2 + w_2^2\sigma_2^2 + 2 w_1 w_2 \rho\,\sigma_1\sigma_2.\;}$$

That cross term — $2 w_1 w_2 \rho\,\sigma_1\sigma_2$ — is the entire chapter. Everything counterintuitive about diversification lives in the fact that this term shrinks as $\rho$ falls.

### Why correlation < 1 reduces risk

Watch the cross term at the three extremes of $\rho$. Take two assets with equal weights $w_1 = w_2 = \tfrac{1}{2}$ and, for clarity, equal standard deviations $\sigma_1 = \sigma_2 = \sigma$.

- **$\rho = +1$ (move in lockstep).** The formula becomes $\sigma_p^2 = \tfrac{1}{4}\sigma^2 + \tfrac{1}{4}\sigma^2 + 2\cdot\tfrac{1}{4}\cdot\sigma^2 = \sigma^2$, so $\sigma_p = \sigma$. The portfolio is exactly as risky as either asset — the standard deviations are just the weighted average. **No benefit.** Combining two assets that always move together buys you nothing.
- **$\rho = 0$ (independent).** The cross term vanishes: $\sigma_p^2 = \tfrac{1}{4}\sigma^2 + \tfrac{1}{4}\sigma^2 = \tfrac{1}{2}\sigma^2$, so $\sigma_p = \sigma/\sqrt{2} \approx 0.71\sigma$. The portfolio's risk is about 29% *lower* than either asset alone — for free, at no cost in expected return.
- **$\rho = -1$ (perfect opposites).** The cross term is maximally negative: $\sigma_p^2 = \tfrac{1}{4}\sigma^2 + \tfrac{1}{4}\sigma^2 - 2\cdot\tfrac{1}{4}\cdot\sigma^2 = 0$. **Risk vanishes entirely.** When one asset zigs exactly as the other zags, the combination is a sure thing.

The general statement: for **any** $\rho < 1$, the portfolio standard deviation is *strictly less* than the weighted average of the individual standard deviations, and it equals that weighted average only at $\rho = 1$. This is the precise refutation of the most common misconception in the chapter — the belief that a portfolio's risk is the weighted average of its assets' risks (the "risk adds up" error, the mirror of Chapter 7's "standard deviations add" mistake). Risk adds up *only* in the one case ($\rho = 1$) that never holds for genuinely different assets. **It is low correlation, not the number of holdings, that does the work.**

### N assets and the diversification limit

Spread money equally across $N$ assets, $w_i = 1/N$. The portfolio variance is a double sum of all the variance and covariance terms. Separate the $N$ "own-variance" terms from the $N(N-1)$ "cross-covariance" terms; with equal weights the algebra collapses to

$$\sigma_p^2 = \frac{1}{N}\,\overline{\sigma^2} + \left(1 - \frac{1}{N}\right)\overline{\operatorname{Cov}},$$

where $\overline{\sigma^2}$ is the average individual variance and $\overline{\operatorname{Cov}}$ is the average covariance between pairs. Now let $N \to \infty$: the first term, the individual-variance contribution, **shrinks to zero** — this is the firm-specific, *idiosyncratic* risk, and it washes out as you add assets. The second term converges to $\overline{\operatorname{Cov}}$, the average covariance, and **does not go away no matter how many assets you add.** That floor is the **systematic risk** — the risk common to everything, which diversification cannot remove.

$$\sigma_p^2 \;\longrightarrow\; \overline{\operatorname{Cov}} \quad \text{as } N \to \infty.$$

![Diversification curve showing portfolio standard deviation falling steeply as the number of holdings rises from one, then flattening toward a dashed systematic-risk floor; the gap above the floor is labeled diversifiable idiosyncratic risk and the floor itself undiversifiable systematic risk](images/10-risk-correlation-and-portfolio-math-fig-02.png)
*Figure 10.2 — The diversification curve: idiosyncratic risk washes out, systematic risk remains as a floor.*

This is the **diversification limit**, and it is the rigorous version of the empirical curve Evans and Archer (1968) found: portfolio standard deviation falls steeply as you add the first several stocks, then flattens to a floor. Their data suggested most of the benefit by roughly 8–15 stocks; later work argues for 30–50 or more for full benefit — a genuine dispute about *how many*, but not about the *shape*: steep decline, then a systematic-risk floor. The split this produces — diversifiable idiosyncratic risk versus undiversifiable systematic risk — is exactly the split Chapter 9's beta regression measures (R² = the systematic share) and the foundation on which Chapter 6's CAPM prices risk: **only the part of risk that survives diversification gets compensated with higher expected return.**

### The efficient frontier (intuition)

Plot every possible portfolio in risk–return space (σ on the horizontal axis, expected return on the vertical). For two assets, as you slide the weight from all-asset-1 to all-asset-2, you trace a curve that **bows leftward** — toward lower risk — exactly because of the cross term, and bows more the lower $\rho$ is (at $\rho = 1$ it's a straight line; at $\rho = -1$ it kinks all the way to the return axis). For many assets, the leftmost edge of the cloud of achievable portfolios is the **efficient frontier**: for each level of expected return, the portfolio with the lowest possible variance. Rational mean-variance investors hold portfolios *on* the frontier; anything in the interior is dominated by a frontier portfolio with the same return and less risk.

![Sketch of risk-return space with expected return on the vertical axis and standard deviation on the horizontal; the cloud of achievable portfolios is bounded on the upper left by a leftward-bowing efficient frontier, with the minimum-variance point marked and a dominated interior portfolio shown beneath a frontier portfolio of the same risk but higher return](images/10-risk-correlation-and-portfolio-math-fig-03.png)
*Figure 10.3 — The efficient frontier: the best return available at each level of risk.* (The full optimization — finding the frontier for many assets — is a quadratic program that belongs to computational finance; we take the *shape* and its intuition here and point onward.) Markowitz won a Nobel Prize for this picture; tellingly, he reportedly chose his *own* retirement savings 50/50 stocks/bonds "to minimize future regret" rather than by running his own optimizer — a candid acknowledgment that the math and the decision are not the same thing.

---

## Worked examples

### Example 1 — The two-coin bet (diversification in its purest form)

Two bets, same expected value, same maximum win and loss. **Bet A:** one coin, win or lose \$100. **Bet B:** two independent coins, win or lose \$50 each. Both average zero; both can swing ±\$100 in the worst case. Are they the same bet?

Variance of Bet A: a ±\$100 outcome gives $\operatorname{Var}(A) = 100^2 = 10{,}000$, so $\sigma_A = \$100$. Bet B is the sum of two independent ±\$50 coins; because they're independent, *variances add* (Chapter 7): $\operatorname{Var}(B) = 50^2 + 50^2 = 5{,}000$, so $\sigma_B = \sqrt{5{,}000} \approx \$70$. Same expected value, same extremes — but Bet B's dispersion is **30% lower**. Spreading the same stake across two independent draws cut the risk by a third at zero cost to the average. That is diversification stripped to its skeleton: with $\rho = 0$, the cross term is zero, and "the variance of the average is less than the average of the variances." Replace "coins" with "stocks" and you have Maya's father's whole problem.

### Example 2 — Two real stocks at three correlations

A defensive stock has $\sigma_1 = 18\%$; a cyclical stock has $\sigma_2 = 28\%$. Hold them 50/50. The weighted average of the standard deviations is $0.5(18) + 0.5(28) = 23\%$ — the number Maya's father would guess for the portfolio's risk. Now use the formula at three correlations:

- **$\rho = +0.9$:** $\sigma_p^2 = 0.25(18^2) + 0.25(28^2) + 2(0.5)(0.5)(0.9)(18)(28) = 81 + 196 + 226.8 = 503.8$, so $\sigma_p \approx 22.4\%$. Barely below the 23% average — high correlation, little benefit.
- **$\rho = 0.2$:** the cross term shrinks to $2(0.25)(0.2)(504) = 50.4$, giving $\sigma_p^2 = 81 + 196 + 50.4 = 327.4$, $\sigma_p \approx 18.1\%$. Now the portfolio is *less risky than the safer stock alone* — a genuine free lunch.
- **$\rho = -0.5$:** the cross term goes negative, $-126$, giving $\sigma_p^2 = 81 + 196 - 126 = 151$, $\sigma_p \approx 12.3\%$. Far below either stock.

![Curve of portfolio standard deviation against correlation for a 50/50 mix of an 18 percent and a 28 percent volatility stock, falling from 23 percent at correlation plus 1 down to 5 percent at correlation negative 1, with marked points at 22.4 percent, 18.1 percent, and 12.3 percent and a dashed reference line at the 23 percent weighted average](images/10-risk-correlation-and-portfolio-math-fig-01.png)
*Figure 10.1 — Two-asset portfolio risk versus correlation: the cross term does all the work.*

The same two assets span $\sigma_p$ from 22.4% down to 12.3% depending *only* on $\rho$. The weighted-average guess of 23% is right only in the impossible $\rho = 1$ case. **The correlation, not the holdings, is doing the work** — and notice that the portfolio's expected return was the plain weighted average in every case. Lower risk, same return: that is the result that sounds too good to be true and isn't.

### Example 3 — The concentrated position and its hidden cost

Maya's father holds 100% of his wealth in one stock with $\sigma = 35\%$. Suppose its return variance splits into a market (systematic) part and a firm-specific (idiosyncratic) part. Using the Chapter 9 decomposition, if a beta regression on his company gave R² = 0.3, then 30% of his return variance is systematic and **70% is idiosyncratic** — risk that pays him *no extra expected return* (only systematic risk is compensated, per the diversification limit and CAPM). By moving toward a broad portfolio, he can drive that 70% toward zero — keeping the compensated systematic exposure while shedding the uncompensated firm-specific gamble. He is not trading knowledge for ignorance. He is declining to be paid nothing for a risk he doesn't have to bear. His thirty-one years of knowledge are real; they simply don't earn him a risk premium, and the market won't pay him for the sleepless nights.

---

## Back to Maya's father

His question — why would owning things he doesn't understand be safer? — now has a precise answer, and an honest caveat.

The precise answer: risk is not additive. The portfolio variance formula's cross term, $2w_1 w_2 \rho\,\sigma_1\sigma_2$, shrinks whenever assets are less than perfectly correlated, so a combination of imperfectly correlated stocks has *strictly lower* standard deviation than the weighted average of their individual risks (Example 2). Most of his single stock's risk is idiosyncratic — uncompensated, and removable by diversification (Example 3). The math proves he can lower his risk without lowering his expected return. The proof is airtight.

The honest caveat — and this is the chapter's tool-versus-judgment boundary — is that the formula **takes the correlations as given**, and the real world does not hand them over cleanly. Three things the math assumes that judgment must supply: the **inputs** (the covariance matrix must be *estimated* from limited, noisy history, and mean-variance optimization punishes bad estimates savagely); the **stability of correlations** (the formula assumes a fixed $\rho$, but correlations notoriously spike toward $+1$ in a crisis — 2008, 2020 — exactly when diversification is most needed, so the cross term that protects you in normal times shrinks toward the no-benefit $\rho = 1$ case in the worst times); and the **choice of risk measure** (variance treats upside and downside symmetrically and is blind to fat tails — a return distribution can have modest variance and still hide catastrophic crash risk). So the formula proves diversification works; whether *his* diversification works depends on inputs the formula can't give him. The right move is still to diversify — broadly and cheaply — but with humility about the numbers feeding the model, not false confidence in their precision.

---

## Where this generalizes

This chapter is Chapter 7's variance algebra collecting its largest dividend: portfolio variance is nothing but $\operatorname{Var}(w_1 R_1 + w_2 R_2)$ expanded, cross term and all. The systematic/idiosyncratic split it produces is measured by **Chapter 9's** beta regression (R² = the systematic share) and priced by **Chapter 6's** CAPM, where beta — itself $\operatorname{Cov}(R_i, R_m)/\operatorname{Var}(R_m)$, a covariance ratio you can now read as the slope that survives diversification — sets the cost of equity. The same covariance logic governs an insurer pooling thousands of roughly independent risks (Chapter 7's insurance example: variance of the average $\to 0$ as correlations $\to 0$, and the nightmare is correlated catastrophe risk, $\rho \to 1$), a firm steadying cash flow across negatively correlated business lines, and the corporate-finance insight that a conglomerate diversifying for its shareholders usually destroys value — because the shareholders could diversify more cheaply themselves. The efficient frontier's full optimization, and the fat-tail risk measures variance misses, are the province of **Chapter 14** and computational finance. One cross term, paying out across the entire back half of the book.

---

## Exercises

1. **(Compute.)** Two assets: $\sigma_1 = 20\%$, $\sigma_2 = 30\%$, held 60/40. Compute the portfolio standard deviation for $\rho = +1$, $\rho = 0$, and $\rho = -1$. Confirm that $\rho = +1$ gives exactly the weighted average of the two standard deviations, and explain in one sentence why that is the *only* correlation for which "risk adds up."

2. **(Solve backward.)** Using the two-asset formula with equal-weight, equal-$\sigma$ assets, find the correlation $\rho$ needed to cut portfolio standard deviation to 80% of the individual $\sigma$. (Tests: manipulating the variance formula to solve for $\rho$ given a target.)

3. **(Catch the error.)** An investor holds five stocks, all in the same industry with pairwise correlations around 0.85, and says "I'm well diversified — I own five different companies." Explain why the count of holdings is the wrong thing to look at, and what number actually determines how diversified she is.

4. **(Build/derive.)** Starting from $R_p = w_1 R_1 + w_2 R_2$, derive the two-asset portfolio variance formula $\sigma_p^2 = w_1^2\sigma_1^2 + w_2^2\sigma_2^2 + 2w_1 w_2 \rho\sigma_1\sigma_2$ using only the Chapter 7 facts $\operatorname{Var}(aX) = a^2\operatorname{Var}(X)$ and $\operatorname{Var}(X+Y) = \operatorname{Var}(X) + \operatorname{Var}(Y) + 2\operatorname{Cov}(X,Y)$. Then show that for any $\rho < 1$ the result is strictly less than $(w_1\sigma_1 + w_2\sigma_2)^2$.

5. **(Reason about the boundary.)** The portfolio-variance formula proves diversification reduces risk. Name two specific real-world conditions under which a diversified portfolio could still suffer a severe loss the formula did not warn of, tie each to a specific assumption the formula makes, and state in one sentence what the investor must supply that the math cannot.

---

## Sources

- Markowitz, H. (1952). "Portfolio Selection," *The Journal of Finance* 7(1), 77–91. — The founding paper: portfolio variance depends on covariances; diversification works only when $\rho < 1$. (1990 Nobel Prize.)
- Markowitz, H. (1959). *Portfolio Selection: Efficient Diversification of Investments*. Cowles Foundation Monograph 16. Wiley. — The efficient frontier.
- Tobin, J. (1958). "Liquidity Preference as Behavior Towards Risk," *Review of Economic Studies* 25(2), 65–86. — Adding a risk-free asset turns the frontier into a line (two-fund separation); the bridge to CAPM. [verify]
- Sharpe, W. F. (1964). "Capital Asset Prices: A Theory of Market Equilibrium under Conditions of Risk," *The Journal of Finance* 19(3), 425–442. — Systematic vs. unsystematic risk; only systematic risk is priced. [verify]
- Evans, J. L., & Archer, S. H. (1968). "Diversification and the Reduction of Dispersion: An Empirical Analysis," *The Journal of Finance* 23(5), 761–767. — The empirical diversification curve and the ~8–15-stock benefit (contested upward to 30–50+). [verify]
- Michaud, R. O. (1989). "The Markowitz Optimization Enigma: Is 'Optimized' Optimal?" *Financial Analysts Journal* 45(1), 31–42. — Estimation risk / "error maximization." [verify]
- Statman, M. (1987). "How Many Stocks Make a Diversified Portfolio?" *Journal of Financial and Quantitative Analysis* 22(3), 353–363. — The 30–50-stock revision of Evans–Archer. [verify]
- *MBA Computational Finance*, Chapter 8 (The Diversification Miracle). — The two-coin bet (variances 10,000 vs. 5,000; SD \$100 vs. ~\$70) and the concentrated-employee-stock case, read in source.
- *MBA Finance*, Chapters 13–14 (Statistical Analysis; Regression in Finance). — Variance, covariance, beta, and the systematic/idiosyncratic decomposition.
