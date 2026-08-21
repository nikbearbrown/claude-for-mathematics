# Chapter 11 — Calculus for Business: Marginal Analysis, Elasticity, and Optimization

## A price that costs you money to get wrong

In July 2011, Netflix split its combined DVD-and-streaming plan in two. The bundle that had cost \$9.99 a month became two \$7.99 plans — an effective price jump of about sixty percent for anyone who wanted both. By the end of the year the company had lost roughly 800,000 of its more than 25 million subscribers, the stock cratered, and the business press wrote the obituary. Then the obituary turned out to be wrong. By 2013 subscriptions were higher than before the hike, and the stock climbed for a decade.

Here is the question a manager actually faces, and it is a number question, not a story question. You can raise the price. Some customers will leave. Will the higher price on the ones who stay more than make up for the revenue from the ones who go? Raise the price too little and you leave money on the table; raise it too much and you bleed out. Somewhere there is a *best* price — a peak — and the whole problem is finding it.

"Find the top of a hill" is the oldest question calculus answers. This chapter builds the one idea that does it: the **derivative**, the rate at which one quantity changes as you nudge another. We will build it from the slope of a curve, no calculus course assumed, and then watch the central results of microeconomics fall out of setting a single derivative to zero.

## The tool, named: the derivative as marginal change

In business the word for "the effect of one more" is **marginal**. The marginal cost of production is what the next unit costs to make. Marginal revenue is what the next unit sells for. Marginal profit is the difference. Each of these is a *rate of change* — how a total shifts when output ticks up by one — and the mathematical name for a rate of change is the derivative.

We will write the derivative of a quantity $y$ with respect to $x$ as $\frac{dy}{dx}$, read "the change in $y$ per unit change in $x$." When $y$ is total cost $C$ and $x$ is quantity $q$, the derivative $\frac{dC}{dq}$ *is* marginal cost. That identification is the spine of this chapter.

## Development: building the derivative from a slope

Start with something concrete. A small workshop's total cost of producing $q$ units is

$$C(q) = 1000 + 40q + 2q^2,$$

a fixed cost of \$1,000 plus a part that grows with output. What does the next unit cost? Make a table of the *actual* change in cost when you add one unit:

| $q$ | $C(q)$ | $C(q{+}1) - C(q)$ (next-unit cost) |
|----|--------|------------------------------------|
| 10 | \$1,600 | \$84 |
| 20 | \$2,600 | \$124 |
| 30 | \$4,000 | \$164 |
| 40 | \$5,800 | \$204 |

The "next-unit cost" column is marginal cost computed the honest way: build one more, see what it added. Now notice the pattern — at $q = 10$ it is \$84, at $q = 20$ it is \$124, rising by \$40 each time $q$ rises by 10, i.e. by \$4 per unit. That regularity is the derivative trying to surface.

<!-- → [DIAGRAM: Total cost curve C(q) with a secant line between q and q+1, and a tangent line at q; caption: "Marginal cost is the slope of the tangent — the limit of the next-unit step as the step shrinks to a point."] -->

Geometrically, the next-unit change is the slope of the line joining the points $(q, C(q))$ and $(q{+}1, C(q{+}1))$ — a *secant*. Shrink the step from one unit to a half to a sliver, and the secant pivots toward the **tangent** line at the point $q$. The slope of that tangent is the derivative. We are taking a limit, but informally: the derivative is the slope you approach as the step shrinks to nothing.

For a power $q^n$ the slope works out (you can confirm it with the shrinking-secant table) to $n q^{n-1}$. Constants have slope zero — a flat line does not change. Applying that term by term to $C(q) = 1000 + 40q + 2q^2$:

$$\frac{dC}{dq} = 0 + 40 + 4q = 40 + 4q.$$

Check it against the table. At $q = 10$ the formula gives $40 + 40 = \$80$; the next-unit table gave \$84. They are close, and they differ only because the table averages the slope across a whole unit while the derivative reads it at a point. The smaller the unit relative to the scale, the closer they agree. **This is the mapping the whole chapter rests on: the derivative is the next-unit change, read exactly.** Economists treat "marginal cost" and "$dC/dq$" as the same object for this reason.

### Profit maximization: MR = MC from one equation

Now the payoff. A firm's profit is revenue minus cost:

$$\pi(q) = R(q) - C(q).$$

Profit is a hill: it rises as you sell more, peaks, then falls when the cost of cramming out extra units overtakes what they fetch. At the very top of any smooth hill the tangent is flat — the slope is zero. So the profit-maximizing output is where

$$\frac{d\pi}{dq} = \frac{dR}{dq} - \frac{dC}{dq} = 0 \quad\Longrightarrow\quad \frac{dR}{dq} = \frac{dC}{dq},$$

which in the language of margins is the most famous sentence in microeconomics:

$$\boxed{\text{Marginal revenue} = \text{Marginal cost.}}$$

Produce one more unit whenever it brings in more than it costs (MR > MC); stop the instant the next unit would cost more than it earns. The peak is exactly where they balance. Antoine Augustin Cournot derived precisely this in 1838 — writing demand as a function, forming revenue, and setting a derivative to zero — decades before anyone said the words "marginal revenue." [verify: Cournot 1838, *Recherches sur les principes mathématiques de la théorie des richesses*]

A flat slope alone only says "peak *or* trough." To be sure it is a peak, check the **second-order condition**: profit must be curving downward there (marginal cost rising through marginal revenue from below). The first condition locates the candidate; the second confirms it is a maximum, not a minimum.

![Two-panel chart: marginal revenue line MR = 100 − 4q crossing flat marginal cost MC = 20 at output q* = 20, above a total-profit curve peaking at $790 at the same output](images/11-calculus-for-business-marginal-elasticity-optimization-fig-01.png)
*Figure 11.1 — Profit peaks where marginal revenue meets marginal cost (q* = 20, π = $790).*

### Why marginal revenue lies below price

For a price-taker selling at a fixed price $P$, each unit adds exactly $P$, so MR = $P$. But a firm with pricing power faces a downward-sloping demand curve: to sell one more unit it must cut the price — and the cut applies to *every* unit, not just the last. So marginal revenue is the new price minus the lost margin on all the inframarginal units, which puts **MR below the price**. Joan Robinson made this curve a standard analytic object in 1933; for a linear demand curve it shares the demand curve's intercept but falls twice as steeply. [verify: Robinson 1933, *The Economics of Imperfect Competition*]

### Elasticity: how much "less" is the less?

The demand curve says quantity falls when price rises. *Elasticity* says by how much. The **price elasticity of demand** is a ratio of percentages:

$$\varepsilon = \frac{\%\ \text{change in quantity}}{\%\ \text{change in price}} = \frac{dQ/Q}{dP/P} = \frac{dQ}{dP}\cdot\frac{P}{Q}.$$

Because quantity falls when price rises, $\varepsilon$ is negative; by convention we discuss its absolute value. If $|\varepsilon| > 1$ demand is **elastic** (quantity is touchy — a price hike loses revenue); if $|\varepsilon| < 1$ it is **inelastic** (quantity is stubborn — a price hike raises revenue); at $|\varepsilon| = 1$, **unit elastic**, revenue is momentarily flat and at its maximum. That last fact is the whole Netflix story in one line: raise price while demand is inelastic, and stop when you reach unit elasticity.

![Two-panel chart: a linear demand curve P = 100 − 2q with its upper half labeled elastic, lower half inelastic, and midpoint unit-elastic; below it, total revenue as an inverted parabola peaking at the unit-elastic midpoint](images/11-calculus-for-business-marginal-elasticity-optimization-fig-02.png)
*Figure 11.2 — Elasticity along a linear demand curve: revenue peaks at unit elasticity (q = 25, R = $1,250).*

Elasticity ties straight back to the pricing rule. A little algebra on $R = P\cdot Q$ gives the marginal-revenue–elasticity identity

$$\text{MR} = P\left(1 + \frac{1}{\varepsilon}\right),$$

with $\varepsilon$ negative. When demand is very elastic ($|\varepsilon|$ large) MR sits just below price; as demand stiffens toward $|\varepsilon| = 1$, MR falls to zero — exactly the revenue peak. Set this equal to MC and you get the markup rule: a firm with pricing power prices above marginal cost by a margin governed by $1/|\varepsilon|$.

### Constrained optimization: the Lagrange multiplier, lightly

Often the peak you want is fenced in by a budget. Allocate a fixed advertising budget across two channels to maximize total reach: maximize $f(x, y)$ subject to a spending constraint $g(x, y) = B$. At an unconstrained peak the slope is zero, but here you cannot walk freely — you must stay on the constraint line. The condition that replaces "flat slope" is that the objective's gradient is *proportional* to the constraint's gradient:

$$\nabla f = \lambda\, \nabla g.$$

In plain words: at the constrained optimum you cannot improve the objective by shifting a dollar from one channel to another, because the **marginal return per dollar is equal across channels**. The proportionality constant $\lambda$ — the **Lagrange multiplier** — is the marginal value of relaxing the constraint: how much more reach one extra budget dollar would buy. That is its other name, the **shadow price**, and we will meet it again in Chapter 12 as the value of an extra unit of a binding resource. Joseph-Louis Lagrange gave the method in 1788; we use it only at this gradient-proportionality level. [verify: Lagrange 1788, *Méchanique analytique*]

## Worked examples

**Example 1 — The profit-maximizing output (MR = MC).** A firm faces linear demand $P = 100 - 2q$ and total cost $C(q) = 20q + 10$. Revenue is $R = Pq = (100 - 2q)q = 100q - 2q^2$, so marginal revenue is $\frac{dR}{dq} = 100 - 4q$ — same intercept as demand (100), twice the slope (the Robinson result). Marginal cost is $\frac{dC}{dq} = 20$. Setting MR = MC:

$$100 - 4q = 20 \;\Longrightarrow\; q^* = 20.$$

The price comes from the demand curve: $P = 100 - 2(20) = \$60$. Profit is $R - C = (100\cdot20 - 2\cdot20^2) - (20\cdot20 + 10) = 1200 - 410 = \$790$. Marginal cost (\$20, constant) cuts marginal revenue from above as $q$ rises, confirming a maximum.

**Example 2 — Netflix and inelastic demand (illustrative).** Suppose, purely to show the mechanism, that at the original \$9.99 a relevant segment had demand elasticity $|\varepsilon| \approx 0.5$ (inelastic — Netflix had few real substitutes for many households). The $0.5$ is a round, hypothetical number, not a measured elasticity. A 60% price increase then implies roughly $0.5 \times 60\% = 30\%$ fewer units. Revenue per remaining customer rises 60% while the customer count falls ~30%; the product, $1.60 \times 0.70 \approx 1.12$, is up about 12%. Revenue *rises* despite the lost subscribers — the inelastic-demand outcome the elasticity number predicts before any news arrives. (Figures illustrative, adapted from the `mba-economics` account; the real loss was ~800,000 of >25M.)

**Example 3 — Allocating an ad budget (Lagrange).** Reach from two channels is $f(x, y) = 4\sqrt{x} + 3\sqrt{y}$ for dollars $x, y$, with budget $x + y = 100$. The condition $\nabla f = \lambda \nabla g$ gives $\frac{2}{\sqrt{x}} = \lambda$ and $\frac{1.5}{\sqrt{y}} = \lambda$. Equalize the marginal return per dollar: $\frac{2}{\sqrt{x}} = \frac{1.5}{\sqrt{y}}$, so $\sqrt{x} = \frac{4}{3}\sqrt{y}$, i.e. $x = \frac{16}{9}y$. With $x + y = 100$: $y = 36$, $x = 64$. Spend \$64 on the first channel, \$36 on the second — the split that equalizes marginal bang per buck, not the equal split intuition suggests.

![Contour plot: iso-reach curves of f = 4√x + 3√y against the budget line x + y = 100, with the highest attainable contour tangent to the line at the optimum (64, 36), and the equal-split point (50, 50) shown on a lower, suboptimal contour](images/11-calculus-for-business-marginal-elasticity-optimization-fig-03.png)
*Figure 11.3 — Lagrange tangency: the optimal split (64, 36) is where a reach contour touches the budget line.*

## Back to Netflix

The manager's question — "is the higher price worth the lost customers?" — is now a calculation, not a gamble. The answer turns entirely on one number, the elasticity. Where demand is inelastic ($|\varepsilon| < 1$), a price increase raises revenue, and you keep raising until you reach unit elasticity, the revenue peak. Netflix was sitting in inelastic territory; the 800,000 departures were the *expected* cost of moving toward the peak, not evidence of a blunder. The derivative did not tell Netflix it would survive — it told them which direction was uphill, and roughly how far the top was.

## Where it generalizes

The derivative-as-marginal idea runs through the entire core curriculum: marginal cost and marginal product in operations and managerial economics; the markup rule and tax incidence (who bears a tax depends on the *relative* elasticities of supply and demand) in public economics; marginal utility in consumer theory. The Lagrange/shadow-price idea reappears in Chapter 12 as the shadow price of a binding constraint in linear programming, and the "set the derivative to zero" move underlies the least-squares slope of Chapter 9 and the portfolio optimization of Chapter 10. For the dynamic and personalized-pricing frontier — where firms estimate local elasticities from transaction data and adjust algorithmically — the static calculus here is the object being estimated; the data-driven machinery lives in the analytics and computational courses.

One honest caveat. MR = MC is how a firm *should* price; it is not always how firms *do* price. A long line of survey evidence, from Hall and Hitch (1939) onward, finds many firms use cost-plus or markup rules of thumb rather than computing marginal revenue. [verify: Hall & Hitch 1939, full-cost pricing] The math is normatively correct and tells you where the optimum is. It cannot choose your objective (short-run profit? market share? lifetime value?), and it cannot supply the demand curve — the firm's real responsiveness, which the manager must estimate or judge. Calculus locates the peak; judgment chooses the mountain.

## Exercises

1. **Marginal vs. average.** For $C(q) = 1000 + 40q + 2q^2$, write average cost $C(q)/q$ and marginal cost $dC/dq$. Show they are equal exactly where average cost is at its minimum, and explain in words why that must be so.
2. **Derive the linear-MR result.** Starting from a general linear demand $P = a - bq$, derive $R(q)$ and show that $\text{MR} = a - 2bq$ — same intercept as demand, twice the slope. Identify where MR = 0 and connect it to unit elasticity.
3. **Find the optimum (build it).** A monopolist faces $P = 200 - q$ and $C(q) = 40q + 500$. Derive MR and MC, solve MR = MC for $q^*$, find the price and profit, and verify the second-order condition.
4. **Elasticity and revenue.** At a price of \$50 a firm sells 1,000 units; at \$55 it sells 920. Estimate the (arc) elasticity, classify the demand, and predict whether the price increase raised or lowered revenue. Confirm by computing revenue at both prices.
5. **Lagrange / shadow price.** Maximize output $f(L, K) = L^{0.5}K^{0.5}$ subject to $2L + 4K = 80$. Find $L^*, K^*$, and interpret the multiplier $\lambda$ as the marginal output of one more budget dollar.

## Sources

- Cournot, A. A. (1838). *Recherches sur les principes mathématiques de la théorie des richesses*. Paris: Hachette. (English: *Researches into the Mathematical Principles of the Theory of Wealth*, trans. Bacon, 1897.)
- Marshall, A. (1890). *Principles of Economics*, Book III, Ch. IV (origin of "elasticity of demand").
- Robinson, J. V. (1933). *The Economics of Imperfect Competition*. London: Macmillan (the marginal-revenue curve).
- Lagrange, J.-L. (1788). *Méchanique analytique* (method of multipliers).
- Hall, R. L., & Hitch, C. J. (1939). "Price Theory and Business Behaviour." *Oxford Economic Papers*, os-2(1), 12–45 (full-cost/markup pricing).
- Mkhatshwa, T., & Doerr, H. (2021). "Calculus students' interpretations of marginal change." *International Journal of Research in Undergraduate Mathematics Education* (the marginal-vs-total misconception).
- Netflix 2011 price-split case and monopoly/MR-below-price illustration adapted from `mba-economics`, ch. 5 (Elasticity) and ch. 9 (Monopoly).
