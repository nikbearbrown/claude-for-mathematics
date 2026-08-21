# Regression and Forecasting

*The math of fitting a line to data and predicting from it — and the discipline of not mistaking a slope for a cause.*

---

## How much will another dollar of advertising sell?

A marketing director has two years of monthly data: how much the company spent on advertising each month, and how much it sold. Plotted, the points slope upward — months with more ad spend tend to be months with more sales. She wants one number: *if we spend one more dollar on advertising, how many more dollars will we sell?* That number sets the budget. The CFO will approve it or kill it on the strength of that single slope.

There are two traps waiting, and they are different traps. The first is purely mechanical: of all the lines you could draw through a cloud of points, *which one* is "the" line, and how do you compute its slope from the data? The second is conceptual and far more dangerous: even once you have the slope, does it tell you what another dollar of advertising will *cause*? Or does it merely describe a pattern — perhaps ad spend and sales both rise in the holiday season, and the line is reading the calendar, not the campaign? This chapter builds the tool that answers the first question exactly, and then spends its hardest pages on why the tool cannot, by itself, answer the second. The director will get a precise slope. Whether she may call it "the return on a marketing dollar" depends on something the regression never sees.

---

## The tool, named

**Linear regression** fits a straight line $\hat{y} = a + bx$ through a cloud of paired data $(x_i, y_i)$, choosing the slope $b$ and intercept $a$ that make the line fit "best." The criterion for "best" is **least squares**: minimize the total squared vertical distance between the points and the line. The slope $b$ estimates how much $y$ changes per unit of $x$; **R²** measures how much of the variation in $y$ the line accounts for; and **multiple regression** extends the line to several predictors at once. **Forecasting** uses a fitted trend to project beyond the data — the most useful and most dangerous thing regression does.

---

## Development: deriving the least-squares line

### Correlation: measuring linear association

Before fitting a line, measure the strength of the linear relationship. The **covariance** of $x$ and $y$ (from Chapter 7's variance machinery) is the average product of their deviations:

$$\operatorname{Cov}(x,y) = \frac{1}{n}\sum_{i=1}^{n}(x_i - \bar{x})(y_i - \bar{y}).$$

When $x$ and $y$ tend to be above their means together, the products are positive and covariance is positive. But covariance has awkward units (dollars × units sold) and no fixed scale. Dividing by the two standard deviations strips the units and bounds the result to $[-1, 1]$, giving the **Pearson correlation coefficient**:

$$r = \frac{\operatorname{Cov}(x,y)}{s_x s_y}.$$

An $r$ of $+1$ means the points lie exactly on an upward line; $0$ means no linear association; $-1$, an exact downward line. Correlation is symmetric — $r$ for $(x,y)$ equals $r$ for $(y,x)$ — and that symmetry is your first warning that correlation, by itself, cannot tell you which way causation runs, or whether it runs at all.

### Which line? Minimizing squared error

For each candidate line $\hat{y}_i = a + bx_i$, the **residual** $e_i = y_i - \hat{y}_i$ is the vertical miss at point $i$. We want the line that makes the misses small overall. Why *squared* misses rather than absolute ones? Squaring keeps positive and negative misses from cancelling, punishes large misses more (a line that's wildly off on one point is penalized hard), and — crucially — produces a smooth function we can minimize with calculus. Define the total squared error as a function of the two unknowns:

$$S(a, b) = \sum_{i=1}^{n}(y_i - a - bx_i)^2.$$

This is a bowl-shaped (convex) function of $a$ and $b$; its single lowest point is the least-squares line. To find it, set the partial derivatives to zero (the calculus is Chapter 11's; here we use only that a minimum has zero slope). Differentiating with respect to $a$ and setting it to zero:

$$\frac{\partial S}{\partial a} = -2\sum (y_i - a - bx_i) = 0 \;\Longrightarrow\; \sum y_i = na + b\sum x_i.$$

Dividing by $n$, this says $\bar{y} = a + b\bar{x}$ — **the least-squares line passes through the point of means $(\bar{x}, \bar{y})$.** That is not an accident or a convenience; it falls out of the minimization. It also lets us write $a = \bar{y} - b\bar{x}$, eliminating the intercept. Now differentiate with respect to $b$:

$$\frac{\partial S}{\partial b} = -2\sum x_i(y_i - a - bx_i) = 0.$$

Substitute $a = \bar{y} - b\bar{x}$ and grind through the algebra (centering each variable on its mean makes the cross terms vanish). What survives is clean and worth memorizing:

$$\boxed{\,b = \frac{\sum (x_i - \bar{x})(y_i - \bar{y})}{\sum (x_i - \bar{x})^2} = \frac{\operatorname{Cov}(x,y)}{\operatorname{Var}(x)}\,}$$

![Scatterplot of five months of ad spend versus sales with the least-squares line y-hat equals 11.5 plus 3.75 x drawn through them, passing through the circled point of means at 6 and 34, with short vertical residual segments connecting each point to the line](images/09-regression-and-forecasting-fig-01.png)
*Figure 9.1 — The least-squares line minimizes total squared residuals and runs through the point of means.*

**The least-squares slope is the covariance of $x$ and $y$ divided by the variance of $x$.** Read it as: how $x$ and $y$ move together, scaled by how much $x$ moves on its own. Pearson (1896) put this in a third equivalent form by substituting the correlation:

$$b = r\,\frac{s_y}{s_x}.$$

The slope is the correlation, rescaled from "standard-deviation units" back into the natural units of $y$ per unit of $x$. Three faces of one number — and notice that the engine is, once again, Chapter 7's covariance and variance. Regression is variance algebra wearing a business suit.

### R²: how much variation the line explains

The slope gives direction and magnitude; R² gives strength. Decompose the total variation in $y$ — the sum of squared deviations from $\bar{y}$ — into the part the line captures and the part it leaves as residual. The fraction captured is

$$R^2 = 1 - \frac{\sum e_i^2}{\sum (y_i - \bar{y})^2}.$$

In simple regression this equals $r^2$.

![Horizontal bar showing the total variance of a stock's return splitting into an explained share of R-squared equals 0.40, labeled systematic and market-driven, and an unexplained residual share of 0.60, labeled idiosyncratic and firm-specific](images/09-regression-and-forecasting-fig-03.png)
*Figure 9.2 — R² splits the variation in y into the part the line explains and the part it leaves as scatter.* An $R^2$ of 0.6 means the line accounts for 60% of the variation in $y$ and leaves 40% as scatter the line cannot explain. Two warnings, both echoing Chapter 8's "significance ≠ importance." First, **a high R² does not mean the model is correct, causal, or useful out of sample** — you can fit a high-R² line to a spurious relationship. Second, **a low R² does not mean a predictor is unimportant** — a small, noisy, but real effect can still be worth large money (the advertising slope might explain only 15% of sales variation and still pay for itself many times over). R² answers "how tightly do the points hug the line?" — a different question from "does $x$ drive $y$?" and from "does this effect matter economically?"

### Coefficient significance

A slope computed from finite, noisy data might be nonzero purely by chance — the Chapter 8 hypothesis test applied to $b$. A serviceable rule of thumb: with $n$ paired observations, a correlation is statistically distinguishable from zero at roughly the 5% level when $|r| \ge 2/\sqrt{n}$. With 60 months of data, that threshold is $2/\sqrt{60} \approx 0.26$. This is the bridge back to Chapter 8: a regression coefficient is an *estimate* with a standard error, and "is the slope real?" is a hypothesis test — carrying every caution about significance versus importance with it.

### Multiple regression: "holding the others constant"

Real outcomes have several drivers. Multiple regression fits

$$\hat{y} = b_0 + b_1 x_1 + b_2 x_2 + \cdots + b_k x_k,$$

by the same least-squares principle (minimize squared residuals in higher dimensions). The interpretation gains a critical clause: $b_1$ is the predicted change in $y$ per unit of $x_1$ **holding the other predictors fixed**. Add "month is December" as a predictor $x_2$ alongside ad spend $x_1$, and $b_1$ now estimates the ad-spend effect *within* a given calendar condition — a partial step toward separating the campaign from the season. But be honest about what this buys: holding a variable "constant" in a regression is a *statistical* control, not an *experimental* one. You have only controlled for the confounders you thought to measure and include. The regression cannot tell you about the ones you left out. This is exactly where the correlation-causation reckoning bites.

---

## A necessary note on Francis Galton

The word "regression" comes from Francis Galton, who in 1886 plotted the heights of 928 adult children against their parents' heights and found the slope was *less than one*: tall parents had tall children, but on average less tall — heights "regressed toward mediocrity." That observation gave us both the name of the method and one of its most useful warnings, **regression to the mean** (extreme values tend to be followed by less-extreme ones, for purely statistical reasons — the "sophomore slump," the "Sports Illustrated jinx," the consultant hired right after a bad year who "turns things around").

Galton was also the founder of eugenics, and his height study was motivated by hereditarian aims that the eugenics movement turned to monstrous ends. The intellectual debt — the word, the concept of regression to the mean — is real and we use it. The man's project was the application of these statistical ideas to a pseudoscience of human "betterment" that did profound harm. We name both, because pretending the mathematics arrived clean would be a lie, and because confusing regression to the mean with a causal force is precisely the error his own discovery should inoculate you against.

---

## The reckoning: correlation is not causation

Here is the chapter's central caution, and the one the MBA core most often gets wrong. **A regression coefficient is an association.** The least-squares slope tells you that $x$ and $y$ move together in your data. It does not tell you that changing $x$ would change $y$. Three distinct ways the move from "associated" to "causal" fails:

![Confounder diagram in which the holiday season drives both ad spend and sales with solid causal arrows, while the observed correlation between ad spend and sales is shown as a dashed link that requires no direct causal connection](images/09-regression-and-forecasting-fig-02.png)
*Figure 9.3 — A confounder manufactures correlation: the season drives both spend and sales.*

- **Confounding.** A third variable $Z$ drives both $x$ and $y$, manufacturing a correlation with no direct link. Ice-cream sales correlate with drownings — because summer heat ($Z$) drives both. The director's ad spend and her sales may both be driven by the holiday season. Regress sales on ad spend alone and the slope absorbs the season's effect, *overstating* the causal return on a marketing dollar.
- **Reverse causation.** Maybe high sales months *cause* high ad spend (the firm spends more when business is booming), not the other way around. The regression is symmetric in a way the world is not.
- **Spurious correlation.** Two unrelated series that happen to trend together over time will show a high correlation that means nothing — Udny Yule's "nonsense correlations." Per-capita cheese consumption and the number of engineering doctorates can march in step for a decade by sheer coincidence.

The modern fix — randomized experiments, natural experiments, instrumental variables, difference-in-differences — is the domain of econometrics and beyond this chapter's scope, but the principle is not: **the regression gives you a number; you supply the causal claim and the willingness to defend it.** A coefficient becomes causal only when you can argue, from outside the data, that confounders are controlled or randomized away. The math will run on any two columns of numbers and never once warn you that the story you're telling about them is false.

---

## Worked examples

### Example 1 — Beta: the one regression that prices risk (finance)

Finance runs exactly one regression so often it has a name for the slope. Regress a stock's monthly returns ($y$) on the market's monthly returns ($x$); the slope **is the stock's beta**:

$$\beta = \frac{\operatorname{Cov}(R_{\text{stock}}, R_{\text{market}})}{\operatorname{Var}(R_{\text{market}})}.$$

This is the boxed least-squares slope formula with $x = R_{\text{market}}$, $y = R_{\text{stock}}$ — nothing new, just relabeled. A beta of 1.2 says the stock tends to move 1.2% when the market moves 1%; a beta of 0.5 (historically, a defensive stock like a grocery chain) says it moves half as much. Plugged into CAPM (Chapter 6), beta becomes the cost of equity. And R² here has a beautiful interpretation that hands directly to Chapter 10: it is the fraction of the stock's variance that is **systematic** (market-driven, undiversifiable). The remaining $1 - R^2$ is **idiosyncratic** (firm-specific, diversifiable). If a stock's beta regression has R² = 0.4, then 40% of its return variation is the market and 60% is firm-specific noise that disappears in a diversified portfolio — the exact split Chapter 10 builds its diversification result on. With 60 months of data, the significance threshold $2/\sqrt{60} \approx 0.26$ tells you whether the estimated beta is distinguishable from zero at all.

### Example 2 — Sales on advertising, and the confounding it hides (marketing)

The director fits sales $= a + b\,(\text{ad spend})$ on her 24 months and gets $b = 4.2$: each advertising dollar is "associated with" \$4.20 in sales. The CFO is delighted. But four of her highest-spend months are November and December, when sales are seasonally high *regardless* of advertising. The naive slope credits advertising for sales the holidays would have delivered anyway.

So she adds a seasonal predictor: sales $= b_0 + b_1(\text{ad spend}) + b_2(\text{holiday month})$. Now $b_1 = 2.6$ — the ad-spend effect *holding season fixed* is far smaller. The \$1.60 difference was confounding, not causation. Even \$2.60 is only as causal as her belief that she has controlled for *every* major confounder (competitor pricing? a product launch? a viral moment?). The regression handed her two precise numbers, 4.2 and 2.6, and was equally silent about which — if either — is the true causal return. That judgment is hers, defended with knowledge the data does not contain.

### Example 3 — Forecasting revenue, and the danger zone (operations)

A firm fits a linear trend to eight quarters of revenue: $\widehat{\text{revenue}} = 100 + 8t$ (in \$M), where $t$ is the quarter index, with R² = 0.92 — a tight fit. Projecting forward, quarter 12 forecasts $100 + 8(12) = \$196$M. **Inside the data, the line is excellent. Outside it, the line is a hope.** Extrapolation assumes the relationship that held over the past eight quarters continues unchanged — no market saturation, no recession, no competitor entry, no turning point. Trend lines famously fail at exactly the turning points that matter most, because a straight line cannot bend and the world does. The honest forecast attaches a *widening* band of uncertainty as $t$ moves past the data and flags the "danger zone" explicitly: the model predicts well where it was estimated and is merely extrapolating elsewhere. A high R² measures fit to the *past*; it is not a license on the *future*.

---

## Back to the advertising dollar

The director now has everything the tool can give and a clear view of where it stops. Mechanically, the slope is settled: $b = \operatorname{Cov}(\text{ad}, \text{sales})/\operatorname{Var}(\text{ad})$, computed exactly, no ambiguity about *which* line — least squares picks it uniquely, and it runs through the point of means. That answered the first trap completely.

The second trap is hers to disarm. Her single-predictor slope of 4.2 overstated the causal return by crediting advertising for the holidays' work; controlling for season dropped it to 2.6; and even 2.6 is causal only insofar as she can defend that she has controlled for the confounders that matter and that the relationship will hold over the budget period she's forecasting. The regression will print "4.2" or "2.6" with equal, untroubled precision and tell her nothing about which to believe. The number is the math's. The causal claim — and the willingness to stake a budget on it — is hers. That division of labor *is* the chapter: a tool that fits lines flawlessly and adjudicates causes not at all.

---

## Where this generalizes

Regression is the workhorse the MBA core invokes every time it says "predict," "drive," "explain," or "control for." Its slope formula is pure Chapter 7 covariance-and-variance; its coefficient test is Chapter 8's hypothesis test; its beta feeds Chapter 6's CAPM and splits risk for **Chapter 10's** diversification math, where the R² of a beta regression *is* the systematic share of variance. Economics regresses quantity on price to estimate demand and elasticity (**Chapter 11**); operations regresses cost on output to recover the fixed/variable split of **Chapter 2**'s cost–volume–profit. The least-squares minimization previews **Chapter 11**'s "set the derivative to zero" optimization, and the forecasting caution previews the model-risk humility of **Chapter 14**. One engine — fit a line by minimizing squared error — reused under a dozen names.

---

## Exercises

1. **(Compute.)** Five months of data: ad spend $x = (2, 4, 6, 8, 10)$ (\$000s) and sales $y = (20, 25, 35, 40, 50)$ (\$000s). Compute $\bar{x}$, $\bar{y}$, $\operatorname{Cov}(x,y)$, $\operatorname{Var}(x)$, the least-squares slope $b$, and the intercept $a$. Verify your line passes through $(\bar{x}, \bar{y})$.

2. **(Interpret.)** A regression of customer lifetime value on number of support tickets gives a slope of $+\$45$ per ticket with R² = 0.08 and a significant coefficient. A manager concludes "we should generate more support tickets to raise lifetime value." Identify the likely confounding/reverse-causation story, and explain what the low R² does and does not tell you here.

3. **(Catch the error.)** A consultant reports R² = 0.96 on a model fit to 10 quarters and recommends acting on its forecast three years out. Name two distinct problems with this recommendation, one about R² and one about extrapolation.

4. **(Build/derive.)** Starting from $S(a,b) = \sum (y_i - a - b x_i)^2$, set $\partial S/\partial a = 0$ to show the least-squares line passes through $(\bar{x}, \bar{y})$, then set $\partial S/\partial b = 0$ to derive $b = \operatorname{Cov}(x,y)/\operatorname{Var}(x)$. State at which step you used the fact that the line goes through the means.

5. **(Reason about the boundary.)** Give a concrete business example where a regression coefficient is statistically significant, has a respectable R², and is still *not* a causal effect a manager should act on. Identify the specific confounder or reverse-causation mechanism, and state in one sentence what evidence — from outside the regression — would be needed to license the causal claim.

---

## Sources

- Legendre, A.-M. (1805). *Nouvelles méthodes pour la détermination des orbites des comètes* (appendix on least squares). — First published statement of least squares. [verify]
- Gauss, C. F. (1809). *Theoria motus corporum coelestium*. — Independent development of least squares and its connection to the normal error distribution; the Gauss–Legendre priority dispute. [verify]
- Galton, F. (1886). "Regression towards Mediocrity in Hereditary Stature," *Journal of the Anthropological Institute* 15, 246–263. — Origin of the term "regression" and of regression to the mean (928 children). Galton was the founder of eugenics; the ethical context is named in the text and is non-negotiable. [verify — dataset details]
- Pearson, K. (1896). "Mathematical Contributions to the Theory of Evolution. III. Regression, Heredity, and Panmixia," *Philosophical Transactions of the Royal Society A* 187, 253–318. — The correlation coefficient and $b = r(s_y/s_x)$. [verify]
- Yule, G. U. (1897). "On the Theory of Correlation," *Journal of the Royal Statistical Society* 60(4), 812–854. — Multiple regression; later, "nonsense correlations" in time series. [verify]
- *MBA Finance*, Chapter 14 (Regression Analysis in Finance). — The beta regression, OLS slope and R² = r², the $|r| \ge 2/\sqrt{n}$ significance rule, and the systematic/idiosyncratic split (Example 1), read in source.
- *MBA Marketing*, Chapter 8 (Marketing Research and Market Intelligence). — The sales-on-advertising cold open and "treating correlation as causation" named as a failure mode (Example 2), read in source.
- *MBA Economics*, Chapter 5 (Elasticity) and Chapter 3 (Demand and Supply). — Demand-curve estimation as a regression application (Where this generalizes).
