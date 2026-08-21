# Discounted Cash Flow: NPV, IRR, and Valuation

*Value is a sum of discounted cash flows — and the internal rate of return is a polynomial root, which is why it misbehaves.*

## The cold open

A capital-budgeting committee has two ways to look at the same proposed plant expansion. The finance team's model spits out two numbers. The first: a **net present value** of $8.4 million — discount every projected cash flow back to today, add them up, subtract the upfront cost, and the project creates $8.4M of value. Accept. The second: an **internal rate of return** of 19% — the project "earns 19%," comfortably above the firm's 9% cost of capital. Accept again.

Two numbers, same recommendation, and everyone relaxes. Then someone notices a competing, smaller project with a *higher* IRR — 24% — but a *lower* NPV of $5.1M. Now the two rules point in opposite directions: IRR says take the small high-rate project; NPV says take the big value-creating one. Which is right? And while we're at it — where did the 9% discount rate come from, and what happens to all these numbers if it's really 11%?

These are not trick questions. They expose the actual mathematics under capital budgeting: NPV is a discounted sum, IRR is the root of a polynomial, and the two can disagree for reasons that have nothing to do with the reinvestment story most textbooks tell (and get wrong). This chapter builds both tools, shows exactly when and why they conflict, and resolves the conflict correctly.

## The tool, named

**Discounted cash flow (DCF)** valuation says the value of any asset is the present value of the cash it will generate. Two decision rules flow from it:

- **Net present value (NPV):** discount every cash flow $\text{CF}_t$ back to today at rate $r$ and sum. Accept if positive.
  $$\text{NPV} = \sum_{t=0}^{n}\frac{\text{CF}_t}{(1+r)^t}.$$
- **Internal rate of return (IRR):** the discount rate $r^*$ that makes NPV equal zero — a *root* of the NPV-as-a-function-of-$r$ equation.

The same DCF sum, with different cash flows, prices a **bond** (coupons plus face) and a **stock** (the dividend-discount and Gordon models). The chapter's deepest point is that IRR, being a polynomial root, can multiply, vanish, or mislead in ways NPV cannot.

## Development and derivation

### NPV as a discounted sum

NPV is Chapter 4's machinery with the sign convention made explicit. A project demands an outflow today, $\text{CF}_0 < 0$, and produces inflows over time. Discount each to the present and add:

$$\text{NPV} = \text{CF}_0 + \frac{\text{CF}_1}{1+r} + \frac{\text{CF}_2}{(1+r)^2} + \cdots + \frac{\text{CF}_n}{(1+r)^n}.$$

NPV is denominated in *today's dollars* and measures **value created**: a positive NPV means the project returns more than the $r$ you could earn elsewhere, so it adds wealth. This is why NPV is the theoretically correct rule — it answers the only question that matters, "does this make us richer, in today's money?"

Often the inflows are level (an annuity) plus a lump at the end (a terminal value), so we reuse the annuity factor and the growing-perpetuity formula from Chapter 4 directly. In a typical project valuation a large share of the NPV can live in the **terminal value**, $\text{TV} = \text{FCFF}/(r-g)$ — and because that formula divides by $(r-g)$, a one-point change in the long-run growth rate $g$ can swing the terminal value (and much of the NPV) by 25–40% [verify]. The NPV is a single number resting on inputs that are anything but single numbers.

### IRR as a polynomial root

Now turn the question inside out. Instead of fixing $r$ and computing NPV, ask: *what rate makes NPV exactly zero?* That rate is the IRR, $r^*$:

$$\text{NPV}(r^*) = \sum_{t=0}^{n}\frac{\text{CF}_t}{(1+r^*)^t} = 0.$$

Here is the structural insight the percentage form hides. Substitute $x = 1/(1+r)$. Then NPV becomes

$$\text{CF}_0 + \text{CF}_1 x + \text{CF}_2 x^2 + \cdots + \text{CF}_n x^n = 0,$$

a **polynomial of degree $n$ in $x$.** The IRR is a *root* of that polynomial. This single observation explains every pathology of IRR:

- A degree-$n$ polynomial can have **up to $n$ roots**. By **Descartes' Rule of Signs**, the number of positive real roots cannot exceed the number of sign changes in the cash-flow sequence [verify]. A "conventional" project — one outflow followed by all inflows — has exactly one sign change, hence exactly one IRR, and behaves nicely. But a project with later outflows (a mine that must be remediated, an asset that needs a mid-life overhaul) has *multiple* sign changes and can have **multiple IRRs** — or none.
- When there are two IRRs, the question "is the IRR above the hurdle rate?" has no single answer. The percentage is no longer a meaningful "rate the project earns"; it is just one of several roots of a polynomial.

NPV has no such problem. $\text{NPV}(r)$ is a smooth, monotonically declining curve for a conventional project; it crosses zero exactly once (at the IRR) and gives an unambiguous accept/reject for any chosen $r$. The **NPV profile** — NPV plotted against $r$ — is the single most clarifying figure in capital budgeting: it slopes down, hits zero at the IRR, and for two competing projects the two profiles can *cross*, at a rate called the crossover rate.

![Two downward-sloping NPV profiles against the discount rate; the Big project crosses zero at 19% IRR with higher NPV at the 9% hurdle, the Small project at 24% IRR but lower NPV](images/05-dcf-npv-irr-and-valuation-fig-01.png)
*Figure 5.1 — NPV profiles: each hits zero at its IRR; at the 9% hurdle the higher-NPV Big project wins despite its lower IRR.*

### When NPV and IRR conflict — and the reinvestment myth

For a single accept/reject decision on a conventional project, NPV and IRR always agree (positive NPV $\Leftrightarrow$ IRR above the hurdle rate). They conflict only when **ranking mutually exclusive projects** that differ in **scale** or **timing**. The cold open is the scale case: a small project can have a high *percentage* return (IRR) but create less *dollar* value (NPV) than a big project with a lower percentage. IRR is scale-blind — 24% on a small base can be worth less than 19% on a large one. Since the goal is to create wealth, **NPV is the correct tiebreaker.**

Now the correction. Many textbooks "explain" the conflict by claiming IRR *assumes intermediate cash flows are reinvested at the IRR*, while NPV assumes reinvestment at the discount rate — and that this hidden assumption is why IRR overstates returns. **This is a documented error** [contested — see pantry]. As Magni and Martin argue, there is *no* reinvestment-rate assumption built into either IRR or NPV; both are simply functions of the project's own cash flows and a rate [verify]. The myth arose from misreading a *sufficient condition* for IRR–NPV agreement as if it were a built-in assumption. The honest explanation of the conflict is the one above: it is about **scale and timing** and about IRR being a **polynomial root**, not about a phantom reinvestment rate. A student who understands IRR as a root will never parrot the false reinvestment story — which is exactly why deriving the math beats memorizing the recipe.

(When IRR misbehaves and you still want a single rate, the **modified IRR (MIRR)** is a patch that specifies an explicit reinvestment rate and produces one root. It is a convenience, not a principle; NPV remains the principled answer.)

### Payback, and why it's a screen not a rule

The **payback period** — how long until cumulative cash flows recover the initial outlay — ignores the time value of money entirely and ignores everything after payback. **Discounted payback** at least discounts the flows first, but still ignores the tail. Both are liquidity *screens* useful to a cash-constrained firm ("how fast do we get our money back?"), not value rules. They answer a different question than NPV, and they answer it crudely.

### Bonds and stocks: the same sum, different cash flows

A **bond** is the cleanest DCF in finance because its cash flows are contractual and its discount rate (the yield to maturity, $y$) is observable in the market. Price is the present value of the coupon annuity plus the discounted face value:

$$P = \underbrace{C\cdot\frac{1-(1+y)^{-n}}{y}}_{\text{PV of coupons (annuity)}} + \underbrace{\frac{F}{(1+y)^n}}_{\text{PV of face value}}.$$

Both pieces are Chapter 4 verbatim — an annuity and a single discounted payment. Because price and yield sit on opposite sides of a discount factor, they move inversely: when market yields rise, existing bond prices fall.

A **stock** is the messiest DCF, because its cash flows (dividends) must be forecast and its discount rate must be estimated. The **dividend-discount model** (John Burr Williams, 1938 — whose publisher reportedly balked at the "algebraic symbols," forcing him to help fund the printing) says a share is worth the present value of all its future dividends [verify]. If dividends grow at a constant rate $g$ forever, the infinite sum collapses, via the growing-perpetuity formula of Chapter 4, into the **Gordon growth model** (Gordon and Shapiro, 1959) [verify]:

$$\boxed{\;P = \frac{D_1}{r - g},\;}$$

where $D_1$ is next year's dividend. The same fragility from Chapter 4 returns: the value lives in the small difference $r - g$, so the estimate is only as good as those two contested inputs.

![Curve of stock price against the growth rate g for a $2 dividend at 8% required return, rising from $40 at g=3% to $50 at g=4% and shooting toward infinity as g approaches r](images/05-dcf-npv-irr-and-valuation-fig-02.png)
*Figure 5.2 — Gordon-model fragility: a one-point rise in g (3% → 4%) lifts price 25%; near r, value explodes.*

## Worked examples

**Example 1 — A clean NPV.** A project costs $100 today and returns $40, $50, and $50 at years 1–3; the discount rate is 9%.
$$\text{NPV} = -100 + \frac{40}{1.09} + \frac{50}{1.09^2} + \frac{50}{1.09^3} = -100 + 36.7 + 42.1 + 38.6 = \$17.4.$$
Positive, so accept. The IRR is the rate making this zero; solving $\text{NPV}(r^*) = 0$ gives $r^* \approx 18.5\%$, well above 9% — agreement, because the cash flows are conventional (one sign change, one IRR).

**Example 2 — The ranking conflict (the cold open).** Two mutually exclusive projects at a 9% hurdle. *Big:* NPV $\$8.4\text{M}$, IRR 19%. *Small:* NPV $\$5.1\text{M}$, IRR 24%. IRR ranks Small first; NPV ranks Big first. Take **Big** — it creates $3.3M more value in today's dollars. The Small project's higher *percentage* is on a smaller base and simply produces fewer dollars. No reinvestment assumption is involved; the conflict is pure scale.

**Example 3 — Bond price.** A 5-year bond pays a $40 annual coupon on $1,000 face; the market yield is 5%.
$$P = 40\cdot\frac{1-(1.05)^{-5}}{0.05} + \frac{1{,}000}{1.05^5} = 40(4.3295) + 783.5 = 173.2 + 783.5 = \$956.7.$$
The bond trades below par because its 4% coupon is below the 5% market yield — the discount compensates the buyer. Raise the yield and the price falls further; the inverse relationship is built into the discount factor.

**Example 4 — Gordon model.** A stock will pay a $2.00 dividend next year, growing 3% forever; investors require 8%.
$$P = \frac{2.00}{0.08 - 0.03} = \frac{2.00}{0.05} = \$40.00.$$
Nudge $g$ to 4% and the price jumps to $2/0.04 = \$50$ — a 25% move from a one-point change in a growth rate nobody can pin down. The formula is exact; its inputs are not.

## Return to the cold open

Both numbers said "accept," and for a single project they always agree, so that part was never in doubt. The conflict appeared only when *ranking* two mutually exclusive projects of different scale — and there NPV, which measures dollars of value created, is the rule to follow: take the project with the higher NPV, not the higher IRR. The seductive textbook explanation — "IRR assumes reinvestment at the IRR" — is wrong and should be discarded; the real reason IRR can mislead is that it is a scale-blind percentage and, more deeply, a root of a polynomial that need not even be unique. As for the discount rate: 9% versus 11% can flip a marginal project from accept to reject, which is why the rate deserves a chapter of its own. NPV is not a machine that produces correct answers; it is a structure for having the right argument about cash flows, growth, and risk — and the next chapter supplies the missing piece of that argument, the rate $r$ itself.

## Where it generalizes

DCF is the master valuation method of the MBA core, and every instance is the same discounted sum with different cash flows: **capital budgeting** (project NPV and the accept/reject and ranking decisions), **bond valuation** (coupons plus face at an observable yield), **equity valuation** (dividend-discount, Gordon, and multi-stage DCF models), and **mergers, acquisitions, and intellectual-property valuation** (discounting a target's or a patent's projected cash flows). The "IRR is a polynomial root" insight generalizes to any place a rate is backed out of a price — yield to maturity is itself an IRR. And the one input DCF cannot supply — the discount rate $r$ — is the subject of **Chapter 6**, which closes the loop opened in Chapter 4.

## Exercises

1. A project costs $250 and returns $120, $120, and $80 at years 1–3. Compute its NPV at a 10% discount rate and state the decision.

2. A 4-year bond has a $60 annual coupon on $1,000 face. Find its price if the market yield is (a) 6% and (b) 8%, and explain the direction of the change.

3. A stock pays a $3.00 dividend next year, expected to grow 4% forever; the required return is 9%. Find the price with the Gordon model, then recompute it if the required return rises to 10%, and comment on the sensitivity.

4. **(Derive / reason.)** A project has cash flows $-100, +260, -165$ at years 0, 1, 2. Using the substitution $x = 1/(1+r)$, write NPV as a polynomial in $x$, count the sign changes, and use Descartes' Rule of Signs to state how many IRRs are possible. Then explain in two sentences why NPV gives a clean accept/reject here while IRR does not.

5. **(Argue against a myth.)** A classmate claims project A is worse than project B "because IRR assumes you reinvest A's cash flows at A's high IRR, which is unrealistic." Explain why this reasoning is mistaken, and give the correct reason NPV and IRR can rank mutually exclusive projects differently.

## Sources

- John Burr Williams, *The Theory of Investment Value* (Harvard University Press, 1938) — the origin of discounted-cash-flow and the dividend-discount model. [verify]
- Myron J. Gordon and Eli Shapiro, "Dividends, Earnings, and Stock Prices," *Review of Economics and Statistics* (1959) — the constant-growth (Gordon) model. [verify]
- Joel Dean, *Capital Budgeting* (Columbia University Press, 1951) — NPV and IRR brought into corporate decision-making. [verify]
- Carlo Alberto Magni and John D. Martin, "The Reinvestment Rate Assumption Fallacy for IRR and NPV" (working paper; and *The Engineering Economist*, 2025) — the correction that no reinvestment-rate assumption is built into IRR or NPV. [verify]
- "Internal rate of return" / Descartes' Rule of Signs — the bound on the number of IRRs by the number of cash-flow sign changes. [verify]
- MBA-Corporate-Finance, capital-budgeting chapter — the project-NPV case and terminal-value sensitivity to $g$. [verify]
- MBA-Finance, bond- and equity-valuation chapters — bond pricing and the Gordon-model worked numbers. [verify]
