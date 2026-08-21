# Algebra, Functions, and Break-Even Analysis

*Solving for an unknown — the universal move — wearing the dress of contribution margin and break-even.*

## The cold open

A team in a case-study course is deciding whether to launch a new product line. The numbers on the slide are clean: it will cost $600,000 to set up the line — tooling, a small marketing push, a year of a product manager's salary — before a single unit ships. Each unit sells for $50 and costs $30 to make. The room argues for twenty minutes about whether the market is big enough, whether the price holds, whether the competition responds. Nobody can answer the only question that decides the case: *how many units must we sell before this thing stops losing money?*

It is one equation. Not a forecast, not a strategy — one line of high-school algebra. Profit is what comes in minus what goes out; set it to zero and solve for the quantity. The team has been arguing about the inputs to an equation they have not written down. Once they write it, the answer is immediate: 30,000 units. Whether 30,000 is reachable is a business judgment. *That* it is 30,000 is arithmetic, and arithmetic is what tells the strategy where its burden of proof lies.

This chapter is about that one move — write the relationship as a function, set it to what you want, and solve for the unknown — and the surprising mileage it gets in business when the unknown is a break-even volume, a target-profit quantity, or the point where a pricing assumption collapses.

## The tool, named

A **function** is a rule that turns inputs into an output: feed it a quantity, it returns a profit. The **cost-volume-profit (CVP)** model is the function that connects how much you sell to what you earn, and **break-even analysis** is the act of solving that function for the quantity that makes profit zero. The load-bearing algebra is a single linear equation:

$$\text{Profit} = (P - V)\,Q - F,$$

where $P$ is price per unit, $V$ is variable cost per unit, $Q$ is quantity sold, and $F$ is total fixed cost. Set $\text{Profit} = 0$ and solve for $Q$ and you have the break-even quantity. That is the whole tool. The rest is knowing what to put in it and when the linear form stops being honest.

## Development and derivation

### The contribution-margin identity

Start from the definition of profit and build it up, term by term. Revenue is price times quantity, $R = P\cdot Q$. Total variable cost rises with output, $V\cdot Q$. Fixed cost $F$ does not move with output (within reason — more on that shortly). So:

$$\text{Profit} = \underbrace{P\cdot Q}_{\text{revenue}} - \underbrace{V\cdot Q}_{\text{variable cost}} - \underbrace{F}_{\text{fixed cost}}.$$

Factor $Q$ out of the first two terms:

$$\boxed{\;\text{Profit} = (P - V)\,Q - F.\;}$$

The quantity $P - V$ has a name: the **unit contribution margin**. It is what each unit sold contributes toward covering fixed cost and, after that, toward profit. In the cold open it is $\$50 - \$30 = \$20$ per unit. The identity says something the team's twenty-minute argument missed entirely: every unit you sell hands you $20 toward the $600,000 hole, and nothing else about the business changes that $20. This is the **contribution-margin identity**, and it reframes the whole problem — you are not "making money on each sale," you are *filling a fixed-cost hole* $20 at a time and only then making money.

The **contribution-margin ratio** is the same idea per dollar of sales: $(P-V)/P$. Here $\$20/\$50 = 0.40$, so 40 cents of every revenue dollar is contribution.

### Break-even by solving for the unknown

Break-even is the quantity at which profit is exactly zero — you have filled the hole and not an inch more. Set the identity to zero:

$$(P - V)\,Q - F = 0.$$

Now do the only algebra in the chapter. Add $F$ to both sides:

$$(P - V)\,Q = F.$$

Divide both sides by the contribution margin $(P-V)$:

$$\boxed{\;Q^* = \frac{F}{P - V}.\;}$$

The break-even quantity is the fixed cost divided by the unit contribution margin — the number of $20 contributions it takes to fill a $600,000 hole. Notice we did not *memorize* this formula; we *derived* it by isolating $Q$. That matters, because the next two variants are the same move with a different right-hand side.

![Cost-volume-profit chart with a flat fixed-cost line, an upward total-cost line, and a steeper revenue line crossing at 30,000 units, the profit region shaded](images/02-algebra-functions-and-break-even-fig-01.png)
*Figure 2.1 — Break-even is where revenue crosses total cost: 30,000 units, $1.5M.*

**Target profit.** Suppose the team doesn't want to break even — they want to clear $200,000. Set Profit to $200,000 instead of zero and solve the same way:

$$Q = \frac{F + \text{target}}{P - V} = \frac{600{,}000 + 200{,}000}{20} = 40{,}000 \text{ units.}$$

A target profit is just a bigger hole to fill. Same equation.

### Sensitivity: break-even is not a fixed number

A common belief is that the break-even point is a fixed property of the product. It is not. $Q^*$ is a *function* of $P$, $V$, and $F$, and it moves whenever any of them moves. Read it straight off the formula:

- **Price up 10%** (to $55): contribution rises to $25, and $Q^* = 600{,}000/25 = 24{,}000$ units — break-even drops by a fifth.
- **Variable cost up 10%** (to $33): contribution falls to $17, and $Q^* = 600{,}000/17 = 35{,}294$ units — break-even jumps 18%.
- **Fixed cost up 10%** (to $660,000): $Q^* = 660{,}000/20 = 33{,}000$ units — break-even rises proportionally with $F$.

![Bar chart of break-even quantity under the base case and three 10% input shocks against the 38,000-unit forecast line, with the price cut pushing break-even above forecast](images/02-algebra-functions-and-break-even-fig-02.png)
*Figure 2.2 — Each input flexed 10%: a price cut moves break-even most, erasing the margin of safety.*

The break-even point is most sensitive to the contribution margin, because $P$ and $V$ sit *inside* the denominator while $F$ scales the whole thing linearly. A firm with high fixed costs and thin margins — high **operating leverage** — has a high break-even and violent profit swings around it. This is why the linear CVP model is the algebra underneath operating leverage in corporate finance.

### When the line bends: the quadratic case

The linear model assumes price is constant no matter how much you sell. Often it is not — to move more volume you must cut price, so price is itself a falling function of quantity, say $P(Q) = a - bQ$. Then revenue is

$$R(Q) = P(Q)\cdot Q = (a - bQ)\,Q = aQ - bQ^2,$$

a **quadratic** in $Q$ — a downward-opening parabola, not a straight line. Profit, $R(Q) - VQ - F$, is now quadratic too, and setting it to zero gives a quadratic equation with potentially *two* break-even points: a low volume where you first cover costs, and a high volume where falling prices drag you back into loss. Between them sits the profit-maximizing quantity. The clean formula $Q^* = F/(P-V)$ silently assumed this curvature away. Knowing *when* that assumption holds — the **relevant range** over which costs and prices behave linearly — is exactly the judgment a Goal-Seek cannot supply. (Finding the profit-maximizing $Q$ on that parabola is a calculus problem; we return to it in Chapter 11.)

> **The fixed/variable inversion.** The single most common stumbling block: fixed costs are constant *in total* but shrink *per unit* as volume grows; variable costs are constant *per unit* but grow *in total*. Spreading a $600,000 fixed cost over 10,000 units is $60/unit; over 60,000 units it is $10/unit — the same total, a falling per-unit figure. Mixing up these two views is what produces a misclassified cost and a wrong break-even.

## Worked examples

**Example 1 — The launch (the cold open).** $F = \$600{,}000$, $P = \$50$, $V = \$30$. Contribution margin $P - V = \$20$. Break-even:

$$Q^* = \frac{600{,}000}{20} = 30{,}000 \text{ units.}$$

In revenue terms that is $30{,}000 \times \$50 = \$1.5\text{M}$, or equivalently $F$ divided by the contribution-margin ratio, $600{,}000/0.40 = \$1.5\text{M}$. Either way, below 30,000 units the line loses money; above it, each unit drops $20 to the bottom line.

**Example 2 — A marketing campaign's break-even.** A brand considers a $90,000 ad campaign for a product with a $12 unit contribution margin. How many *incremental* units must the campaign generate to pay for itself? The campaign is a chunk of incremental fixed cost, so $Q^* = 90{,}000/12 = 7{,}500$ units. If the team can't believe the campaign moves 7,500 units, it shouldn't run. The CVP equation has converted a marketing argument into a falsifiable volume target.

**Example 3 — Operating leverage and the relevant range.** A plant runs at high fixed cost: $F = \$4\text{M}$, $P = \$100$, $V = \$40$, so contribution is $60 and $Q^* = 4{,}000{,}000/60 \approx 66{,}667$ units. Now suppose a downturn means the plant can only run at 60% of the volume it was sized for. Fixed costs don't fall with utilization — the building, the salaried staff, the lease stay. If planned volume was 80,000 units, 60% is 48,000 — *below* break-even. The plant loses money not because the product is unprofitable per unit (each still contributes $60) but because there aren't enough units to fill the fixed-cost hole. This is the CVP problem embedded in a capacity decision (the structure of the Halverson Plant-4 utilization case in MBA-Corporate-Finance) [verify], and it is why high-fixed-cost businesses are fragile to volume shortfalls.

**Example 4 — Margin of safety and a sensitivity table.** Return to the launch ($F=600{,}000$, $P=50$, $V=30$, $Q^*=30{,}000$). Suppose the team forecasts sales of 38,000 units. The **margin of safety** is the cushion between forecast and break-even: $38{,}000 - 30{,}000 = 8{,}000$ units, or $8{,}000/38{,}000 = 21\%$ — sales could fall a fifth before the line loses money. Now flex each input $\pm10\%$ and watch $Q^*$ move, which exposes how fragile that cushion is:

| Change (from base $Q^*=30{,}000$) | New value | New $Q^*$ |
|---|---|---|
| Price $-10\%$ | $P=45$ | $600{,}000/15 = 40{,}000$ |
| Variable cost $+10\%$ | $V=33$ | $600{,}000/17 = 35{,}294$ |
| Fixed cost $+10\%$ | $F=660{,}000$ | $660{,}000/20 = 33{,}000$ |

A 10% price cut alone pushes break-even *above* the 38,000-unit forecast — the margin of safety vanishes and the launch is underwater. The single most dangerous assumption is the price, because $P$ sits inside the contribution-margin denominator. A spreadsheet computes each cell; the judgment that "our pricing power is the assumption to defend" is the analyst's.

## Return to the cold open

The team's real question — "how many units before we stop losing money?" — was a break-even problem all along. Profit is $(P-V)Q - F = 20Q - 600{,}000$. Set it to zero and solve: $Q^* = 30{,}000$ units. That single number reframes the entire debate. The argument about market size is now precise: *can we sell 30,000 units?* The argument about price holds is now precise: *if price slips to $45, contribution falls to $15 and break-even jumps to 40,000 — can we sell that?* The equation did not make the decision; it told the strategists exactly which assumptions the decision rests on, and how much each one matters. That is what solving for an unknown buys you — not the answer to the business question, but a sharp statement of what the business question actually is.

## Where it generalizes

"Write the relationship as a function and solve for the unknown" is the move you will make in every quantitative chapter that follows. In **Chapter 4** you solve $\text{FV} = \text{PV}(1+r)^n$ for whichever of the four variables is missing. In **Chapter 5** the internal rate of return is the unknown rate that makes a discounted-cash-flow function equal zero — break-even analysis with discounting, and a polynomial instead of a line. In **Chapter 11** the profit-maximizing quantity on the quadratic-revenue curve is found by calculus (setting the derivative to zero), the natural sequel to the two-break-even-point case here. And the contribution-margin identity is the algebra under **operating leverage** in corporate finance and **target costing** in managerial accounting. The dress changes; the move — isolate the unknown — does not.

## Exercises

1. A subscription product has $F = \$120{,}000$, a monthly price of $40, and variable cost of $10 per subscriber-month. Find the break-even number of subscriber-months and the contribution-margin ratio.

2. Using Example 1's numbers ($F=600{,}000$, $P=50$, $V=30$), find the volume needed to earn a $300,000 profit, then find the new break-even if a supplier price increase pushes $V$ to $35.

3. A firm's break-even is 50,000 units at a $25 price and $300,000 fixed cost. What is its variable cost per unit? (Solve for $V$.)

4. **(Build the model.)** A bakery's rent and salaried staff total $8,000/month (fixed); ingredients and packaging run $2.50 per loaf (variable); loaves sell for $6. But beyond 5,000 loaves/month the bakery must add a second oven and a part-time baker, raising fixed cost to $11,500. Write profit as a function of loaves over both ranges, find the break-even, and explain why a single linear equation is not enough here.

5. **(Derive.)** Suppose price falls with volume as $P(Q) = 80 - 0.01Q$, variable cost is $20/unit, and fixed cost is $40,000. Write profit as a function of $Q$, set it to zero, and use the quadratic formula to find *both* break-even quantities. Explain in one sentence why there are two.

## Sources

- Jonathan N. Harris, "What Did We Earn Last Month?", *N.A.C.A. Bulletin* (1936) — the founding statement of direct (variable) costing and the contribution margin. [verify]
- C. T. Horngren et al., *Cost Accounting: A Managerial Emphasis* — the canonical modern formulation of the CVP model and break-even/target-profit algebra. [verify]
- Walter Rautenstrauch — credited with popularizing the break-even chart that turns the CVP algebra into a picture. [verify]
- MBA-Corporate-Finance, capacity/utilization chapter — the high-fixed-cost plant utilization case underlying Example 3. [verify]
- MBA-Case-Studies — new-product-line launch problems of the cold-open type. [verify]
