# Chapter 5 — Algebra

## TL;DR

- What You Already Do, Written Down So It Always Works.
- The chapter moves through What an equation actually is, The hard part is not solving — it is writing the equation, Functions: naming a relationship, Domain and range, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

*What You Already Do, Written Down So It Always Works.*

Here is the thing nobody tells you about algebra: you already do it. Every time you check your change, estimate whether you can afford something, or figure out how long a drive will take, you are doing algebra. You are reasoning about an unknown quantity using what you do know. The only difference between that and what this chapter teaches is that we are going to write it down — give the unknown a name, state the constraints precisely, and solve mechanically. That shift from informal arithmetic to formal symbol-manipulation is smaller than it looks. But it is enormously powerful, because it works in cases where the informal version breaks down completely.

The informal version breaks down the moment there are two unknowns, or twenty steps, or when the answer is not a nice integer. The formal version does not care. Write it down. Apply the rules. The answer appears.

Here is the hook that will carry us through the chapter. A small restaurant sells two items: tacos at some price, and burritos at some price. You order two tacos and one burrito; the bill is $8.50. Your friend orders one taco and two burritos; the bill is $9.00. How much does a taco cost?

You could guess. You could try values. But you would spend a long time at it — and if the prices were not round numbers, you might never land on the exact answer. Algebra solves this in a few lines. By the end of this chapter, you will know exactly how, and you will know *why* it works.

---

## What an equation actually is

An equation is a statement that two expressions are equal. That is the whole thing. Nothing mysterious. $3x + 5 = 20$ is a claim: the expression $3x + 5$ and the number $20$ name the same quantity, for some value of $x$. Your job is to find that value.

The tool for finding it is one principle, applied repeatedly: **whatever you do to one side of an equation, you must do to the other.** This keeps the statement true. It does not change the solution; it only changes the form of the equation, ideally toward a form where the answer is obvious.

From $3x + 5 = 20$, I want to isolate $x$. The $+5$ is in my way. I subtract 5 from both sides:

$$3x + 5 - 5 = 20 - 5$$
$$3x = 15$$

Now the $3$ is in my way. I divide both sides by 3:

$$\frac{3x}{3} = \frac{15}{3}$$
$$x = 5$$

That is it. Substitute back to check: $3(5) + 5 = 15 + 5 = 20$. Correct.

The steps are mechanical, but the reasoning behind them matters. I am not applying rules by rote. I am *undoing* operations. The original equation had $x$ multiplied by 3, then increased by 5. To find $x$, I undo those operations in reverse order — subtract first, then divide. This is the same logic as unwrapping a package: you remove the outer layers before the inner ones.

![Vertical "unwrapping" diagram for 3x + 5 =](images/05-algebra-fig-01.png)
*Figure 5.1 — Vertical "unwrapping" diagram for 3x + 5 =*

Now try one where the unknown appears on both sides. Solve $5y - 3 = 2y + 9$.

There is no mystery here. The unknown is just in two places at once. Collect it on one side. Subtract $2y$ from both sides:

$$5y - 2y - 3 = 2y - 2y + 9$$
$$3y - 3 = 9$$

Then add 3 to both sides:

$$3y = 12$$
$$y = 4$$

Check: left side is $5(4) - 3 = 17$; right side is $2(4) + 9 = 17$. Both are 17. The equation holds.

The check is not optional formality. It is the only moment you know for certain that you have not made an error. Algebra errors are common and easy. The check catches them.

### The hard part is not solving — it is writing the equation

I want to pause here, because students consistently find the same thing difficult. The manipulation — subtracting from both sides, collecting terms, dividing — is mechanical. You learn it quickly. What takes longer is translating a word problem into an equation in the first place.

A gym charges $10 per month plus $5 per class. Your budget is $75. How many classes can you take?

The translation step: let $c$ be the number of classes. Monthly cost is $10 + 5c$. Set that equal to the budget:

$$10 + 5c = 75$$

Now it is mechanical again. Subtract 10: $5c = 65$. Divide by 5: $c = 13$.

The equation was the hard part. Once you have it, the solution follows automatically. And the equation comes from reading carefully: identify what you do not know (give it a letter), identify what you do know (the price structure, the budget), and write the relationship.

This is worth practicing separately from the solving, because they are different skills.

---

## Functions: naming a relationship

A single equation finds a specific unknown value. But sometimes the relationship between two quantities is what matters — not just one answer, but the whole pattern of how one quantity changes when another does.

A pizza costs $12 plus $1.50 per topping. I could ask: what is the cost of a 4-topping pizza? That is a single-value question, answered by $12 + 1.5(4) = 18$.

But the more interesting thing is the relationship itself. For any number of toppings $t$, the cost is $12 + 1.5t$. This rule — input a number of toppings, output a cost — is a **function**. We write it:

$$f(t) = 12 + 1.5t$$

Read this as "$f$ of $t$" — the value of the function $f$ at input $t$. The parentheses do not mean multiplication. They mean: put $t$ into the rule and see what comes out. $f(4) = 12 + 1.5(4) = 18$. $f(0) = 12$. $f(10) = 12 + 15 = 27$.

A function is a machine. One input in, one output out. The machine's rule can be anything — but it must be consistent. The same input always gives the same output. This is what makes it a function: no ambiguity about the output.

![Function-as-machine diagram ](images/05-algebra-fig-02.png)
*Figure 5.2 — Function-as-machine diagram *

### Domain and range

The **domain** is the set of all permitted inputs. For our pizza function, the domain might be the whole numbers $0, 1, 2, 3, \ldots$ up to some maximum (you cannot order half a topping, and there is a physical limit to how many will fit on a pizza).

The **range** is the set of all outputs the function can produce. For our pizza with domain $0$ through $5$: the range is $\{12, 13.50, 15, 16.50, 18, 19.50\}$.

The domain and range depend on context. In pure mathematics, the function $y = x^2$ has domain all real numbers and range all non-negative real numbers. In a model of human height as a function of age, the domain is roughly $0$ to $100$ years and the range is heights that human bodies can reach. The algebra does not change; only the real-world constraints do.

This is worth holding onto: mathematics gives you a tool, and then you decide what the tool is allowed to do in your specific situation. The domain and range are part of the model, not part of the algebra.

### Graphing a function

A function has a visual form. To graph $f(x) = 2x + 3$, I compute some points:

- $f(0) = 3$ — point $(0, 3)$
- $f(1) = 5$ — point $(1, 5)$
- $f(2) = 7$ — point $(2, 7)$
- $f(-1) = 1$ — point $(-1, 1)$

Connect them. The result is a straight line. That is why this is called a *linear* function — the graph is a line.

Two points are enough to draw any line. The two most useful are the **intercepts**:

The **y-intercept** is where the line crosses the vertical axis — where $x = 0$. For $f(x) = 2x + 3$, that is $f(0) = 3$. The point is $(0, 3)$.

The **x-intercept** is where the line crosses the horizontal axis — where $y = 0$. Set $2x + 3 = 0$, solve: $x = -\frac{3}{2}$. The point is $(-\frac{3}{2}, 0)$.

Plot those two points and connect them. Line drawn.

![Coordinate plane showing the graph of f(x) =](images/05-algebra-fig-03.png)
*Figure 5.3 — Coordinate plane showing the graph of f(x) =*

### Slope: what the rate of change actually is

The **slope** of a line measures how steep it is — how much the output changes per unit change in input.

$$m = \frac{\Delta y}{\Delta x} = \frac{y_2 - y_1}{x_2 - x_1}$$

Pick any two points on $y = 2x + 3$: say $(0, 3)$ and $(1, 5)$. Slope is $\frac{5-3}{1-0} = \frac{2}{1} = 2$. For every 1 unit you move right, the line moves 2 units up.

The slope is the coefficient of $x$ in the equation — the $m$ in $y = mx + b$. That is not a coincidence. The equation $y = mx + b$ is built to make slope visible: $m$ is the rate of change, $b$ is the starting value (the y-intercept).

In context, slope is always *something per something*. A function $d(t) = 60t$ for a car traveling at 60 mph has slope 60 — sixty miles per hour. A function $M(d) = 100 - 5d$ for money declining at $5 per day has slope $-5$ — negative because the quantity decreases. The slope is the story the function tells about rate of change.

One trap worth naming explicitly: a horizontal line has slope 0. A vertical line has undefined slope, because the denominator $\Delta x$ is zero. These are not the same situation. Zero slope means no change; undefined slope means the rule "one input, one output" breaks down entirely — a vertical line has infinitely many $y$-values for a single $x$-value, so it is not even a function.

| Line type | Equation form | Slope value | Is it a function?" — |
| --- | --- | --- | --- |
| horizontal (y = k, slope = 0, yes | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| vertical (x = k, slope = undefined, no | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| diagonal (y = mx + b, slope = m, yes | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| callout on the vertical row explaining why undefined slope and "not a function" are linked | student should be able to scan this and immediately resolve the horizontal vs. vertical confusion | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |

---

## Systems of equations: when there are two unknowns

Return to the restaurant. Tacos at price $t$, burritos at price $b$. Two orders:

$$2t + b = 8.50$$
$$t + 2b = 9.00$$

Two equations, two unknowns. One equation with two unknowns has infinitely many solutions — it describes a line, and every point on the line is a valid pair of values. But two equations together constrain the problem. The solution must satisfy both simultaneously. Geometrically, each equation is a line; the solution is the point where they intersect.

There are two clean algebraic methods for finding that point.

### Substitution

Solve one equation for one variable, then substitute into the other.

From the second equation: $t = 9 - 2b$.

Substitute into the first:

$$2(9 - 2b) + b = 8.50$$
$$18 - 4b + b = 8.50$$
$$18 - 3b = 8.50$$
$$-3b = -9.50$$
$$b = \frac{9.50}{3} \approx 3.17$$

Then: $t = 9 - 2(3.17) = 9 - 6.34 = 2.66$.

Check both equations:

- Equation 1: $2(2.66) + 3.17 = 5.32 + 3.17 = 8.49 \approx 8.50$ ✓
- Equation 2: $2.66 + 2(3.17) = 2.66 + 6.34 = 9.00$ ✓

(The tiny rounding error in equation 1 vanishes if you keep the exact fractions throughout. The exact solution is $b = \frac{19}{6}$ and $t = \frac{8}{3}$.)

### Elimination

The second method works by making a variable cancel. Multiply the second equation by $-2$:

$$-2t - 4b = -18$$

Add this to the first equation:

$$\begin{align}
2t + b &= 8.50 \\
-2t - 4b &= -18 \\
\hline
-3b &= -9.50
\end{align}$$

The $t$ terms vanish. Solve for $b$: same answer, $b \approx 3.17$. Substitute back for $t$.

Both methods reach the same place. Substitution is cleaner when one equation is already solved for a variable or is easy to solve. Elimination is cleaner when the coefficients are arranged to cancel nicely, or when substitution would produce messy fractions.

### Why two equations are needed, not one

This is worth understanding, not just accepting. One equation in two unknowns describes a line — an infinite collection of solutions. Every point $(t, b)$ on that line satisfies the equation. You have no way to narrow it down further.

The second equation adds a constraint. A second line. The solution must lie on both lines — that is, at their intersection. One intersection point (if the lines are not parallel, and not the same line). That is the unique solution.

This generalizes. Three unknowns require three equations. $n$ unknowns require $n$ equations. Each equation eliminates one dimension of ambiguity. Algebra, at its root, is about counting constraints: you need as many independent equations as you have unknowns.

### What happens when the system misbehaves

Two special cases are worth seeing.

**No solution:** If the two equations represent parallel lines — same slope, different y-intercepts — they never intersect. There is no point satisfying both. Example:

$$\begin{cases}
y = 2x + 3 \\
y = 2x + 5
\end{cases}$$

Both lines rise at the same rate, but one is shifted up by 2. They never meet. If you try to solve algebraically, the variable cancels and you are left with a false statement: $3 = 5$. That is the signal. No solution.

**Infinitely many solutions:** If the two equations represent the same line — one is a multiple of the other — every point on the line is a solution. Example:

$$\begin{cases}
2x + y = 5 \\
4x + 2y = 10
\end{cases}$$

The second is the first times two. Algebraically, the variable cancels and you are left with a true statement: $0 = 0$. The system has infinitely many solutions — any point on the line $2x + y = 5$.

These are not errors or failures. They are valid outcomes. They tell you something about the structure of the problem. "No solution" means the constraints are contradictory — they cannot both be satisfied. "Infinitely many" means the constraints are redundant — one adds no new information beyond the other.

![Side-by-side coordinate plane diagrams ](images/05-algebra-fig-04.png)
*Figure 5.4 — Side-by-side coordinate plane diagrams *

---

## The connection between it all

Step back. Equations, functions, and systems are not three separate topics. They are the same idea at different scales.

An **equation** is a constraint: one relationship, one unknown, one solution.

A **function** is a relationship: one input, one output, visualized across a whole range of inputs.

A **system** is multiple constraints: several relationships, several unknowns, a solution that satisfies all of them simultaneously.

The algebra is the same throughout — the same properties of equality, the same operations, the same logic. What changes is how many unknowns you have and how many constraints you have placed on them.

And the real world is almost always a system. Prices depend on multiple products. Schedules depend on multiple constraints. Budgets balance multiple demands. Every time you have two things you do not know and two pieces of information about them, you have a system. The taco and burrito problem is exactly that — a shopping receipt that contains two constraints, and we extracted the two prices it implied.

Thurgood Marshall's argument in Chapter 2 was a logical chain: if premise A and premise B, then conclusion C. Algebra is the same structure with numbers instead of propositions. If cost equation A and cost equation B both hold, then prices $(t, b)$ must be this value. Logic and algebra are cousins. Both are about what follows necessarily from what you are given.

---

## Chapter summary

You now have three interlocking tools.

Solving equations: identify the unknown, write the constraint, undo operations in reverse order, check your answer. The hard part is the translation from words; the solving is mechanical.

Functions: a rule that assigns one output to every input. Written $f(x)$, graphed as a curve or line, characterized by domain, range, and — for linear functions — slope. The slope is the rate of change. The y-intercept is the starting value.

Systems: two (or more) equations, two (or more) unknowns. Solve by substitution or elimination. The solution is the point where all constraints are satisfied simultaneously. No solution means contradictory constraints. Infinitely many means redundant ones.

The one idea that ties everything together: algebra is the discipline of finding what must be true, given constraints. You are given some information and asked to determine what else follows. That is the same thing logic does, the same thing proof does, the same thing the whole of mathematics does. Algebra just does it with numbers and symbols.

The mistake to watch for: writing down the wrong equation. Check your translation. Read the problem again. Make sure the equation you have written actually says what the problem says, before you solve it. A correct solution to the wrong equation is still wrong.

The Feynman test for this chapter: can you explain to someone why you need two equations to find two unknowns? If you can show them that one equation is a line — an infinite set of possibilities — and that a second equation is another line, and that the solution is where they cross, you understand what systems of equations are actually doing.

---

## Exercises

### Warm-up

**Exercise 5.1** *(Solve a one-step equation; LO: properties of equality).* Solve each equation and check your answer by substituting back into the original.

(a) $4x = 28$
(b) $y - 9 = 3$
(c) $\frac{z}{6} = 5$

*Difficulty: low. Each equation requires exactly one operation to isolate the variable.*

**Exercise 5.2** *(Solve a multi-step equation; LO: undo operations in reverse order).* Solve: $2x + 7 = 19$. Show every step and verify your answer.

**Exercise 5.3** *(Evaluate a function; LO: function notation).* A phone plan charges a flat fee of \$25 per month plus \$0.05 per text message. Write the monthly cost as a function $C(t)$, where $t$ is the number of texts. Then evaluate $C(0)$, $C(100)$, and $C(500)$. Identify the domain and range constraints imposed by real-world context.

**Exercise 5.4** *(Compute slope from two points; LO: slope as rate of change).* Find the slope of the line passing through $(1, 4)$ and $(5, 12)$. In one sentence, describe what this slope means if the horizontal axis represents hours and the vertical axis represents miles traveled.

### Application

**Exercise 5.5** *(Translate and solve; LO: writing equations from word problems).* A parking garage charges \$4 to enter plus \$2 per hour. You leave with a bill of \$14. How many hours did you park? Write the equation first, then solve it.

**Exercise 5.6** *(Graph a linear function; LO: intercepts and slope).* For the function $g(x) = -3x + 6$:

(a) Find the y-intercept.
(b) Find the x-intercept.
(c) Compute the slope.
(d) Sketch the line using the two intercept points.

**Exercise 5.7** *(Solve a system by substitution; LO: two equations, two unknowns).* Solve:

$$\begin{cases} x + y = 10 \\ x - y = 4 \end{cases}$$

Check your solution in both equations.

**Exercise 5.8** *(Solve a system by elimination; LO: elimination method).* Solve:

$$\begin{cases} 3x + 2y = 16 \\ x - 2y = 0 \end{cases}$$

State which variable you eliminated and why elimination is convenient here.

### Synthesis

**Exercise 5.9** *(Compare two cost functions; LO: set functions equal to find a break-even point).* A streaming service offers two plans: Plan A costs \$8 per month with no per-movie fee. Plan B costs \$3 per month plus \$1.50 per movie.

(a) Write a cost function for each plan in terms of $m$ (movies watched per month).
(b) Find the number of movies per month at which the two plans cost the same.
(c) For a viewer who watches 6 movies per month, which plan is cheaper?

**Exercise 5.10** *(Classify a system; LO: no solution vs. infinitely many vs. unique solution).* Without solving algebraically, determine whether each system has a unique solution, no solution, or infinitely many solutions. Explain your reasoning using slope and y-intercept.

(a) $y = 4x + 1$ and $y = 4x - 3$
(b) $y = 2x + 5$ and $2y = 4x + 10$
(c) $y = 3x + 2$ and $y = -x + 6$

**Exercise 5.11** *(Model a constraint problem; LO: translate a multi-constraint word problem into a system).* A farmer has 100 acres to plant with corn and soybeans. Corn requires 2 hours of labor per acre; soybeans require 1 hour. The farmer has 140 hours of labor available. Set up a system of two equations and solve for the number of acres of each crop. Check that your solution satisfies both constraints.

### Challenge

**Exercise 5.12** *(Open-ended; LO: construct, solve, and interpret a system from real data).* Find a situation in your own life — a budget, a schedule, a recipe scaled to a different serving size, a travel problem — that involves two unknown quantities and two constraints. Write the system of equations, solve it, and verify the solution makes sense in context. Explain in one paragraph what the solution tells you about the original situation.

*This exercise has no single correct answer. What matters is that your two equations are genuinely independent (not multiples of each other) and that your solution satisfies both.*

---

## Connections forward

Chapter 6 on money management is built on equations. Every loan payment formula, every compound interest calculation, every savings projection is an equation or a system. You will recognize the machinery immediately.

Chapter 7 on probability introduces expected value — which is a weighted sum, which is a function. You are computing the output of a rule applied to probabilities and outcomes. The function notation $f(x)$ appears in a new costume, but the idea is identical.

Chapter 8 on statistics uses linear regression, which fits a line to data. The slope and y-intercept of that line are found by solving a system of equations. Everything in this chapter reappears.

And Chapter 10 on geometry describes shapes with equations. The equation of a line is $y = mx + b$. The equation of a circle is $(x-h)^2 + (y-k)^2 = r^2$. The shapes are defined by the constraints. Algebra is the language geometry speaks.

You have learned the alphabet. What follows is learning to write.
---

## LLM Exercise — Chapter 5: Algebra (Audit a Real-World System Project)

**Project:** Audit one real-world system through 13 chapters of mathematics.
**What you're building this chapter:** the system's break-even, threshold, or tipping-point problems solved algebraically.
**Tool:** **Claude Project** (same system spec as Ch 1).

**The Prompt:**

```
Chapter 5 of my system-audit project. Chapter 5 covered:
equations as statements about unknowns; solving linear
equations; functions as named relationships; systems of
equations and the meaning of their solution; graphing.

Apply to my system. Every real system has thresholds — places
where a value crosses a line and the system's behavior
changes. Algebra finds those thresholds.

1. **Identify three thresholds in the system.** Examples:
   - Transit: when does buying a monthly pass beat per-ride
     fares (find ride count where they equal)? When does
     adding a third bus on a route stop being worth the
     marginal cost?
   - Streaming: at what subscriber count does the next
     server upgrade pay for itself?
   - Restaurant: at what daily customer count does the
     restaurant break even?
   - Sports: at what record does a team mathematically
     clinch a playoff spot?
   - Hospital: at what occupancy rate does the ED start
     diverting ambulances?

2. **Set up the algebra for one threshold.** Pick the most
   meaningful threshold. Write the equation that defines
   the crossing point. Examples:
   - Monthly pass break-even: 90 (monthly pass price) =
     2.40 × n (per-ride fare × rides). Solve for n.
   - Restaurant break-even: revenue = cost. Both are
     functions of customer count c. Solve revenue(c) =
     cost(c) for c.

3. **Solve the equation. Show every step.** Don't skip
   algebraic steps even if Claude wants to. The point of
   the chapter is the procedure.

4. **Set up a system of two equations** describing two
   features of the system. Example: the linear cost function
   AND the linear revenue function for a small operation in
   the system. Solve the system. Identify the meaning of
   the solution point graphically.

5. **Sketch (or describe) the graph.** What does it look
   like? Where's the threshold? What is the slope's real-
   world meaning (cost per ride, revenue per customer)?
   What is the y-intercept's real-world meaning (fixed
   cost, baseline price)?

6. **State the consequence.** Now that you know the
   threshold value, what does it mean for the system?
   Examples: the monthly-pass break-even at 37.5 rides
   means commuters who take fewer than 38 rides per month
   lose money buying the pass. The restaurant break-even
   at 95 customers/day means a 90-customer day costs the
   restaurant money.

End with: a one-page "threshold audit" of the system. Three
thresholds named. One solved with algebra. One system of
equations solved. The decision-relevant interpretation of the
solution.
```

**What this produces:** A threshold audit identifying the decision-relevant tipping points in the system. Algebra is most useful where it tells you when to do something (or when to stop).

**Connection to previous chapters:** Often builds on Ch 3's cycles (thresholds often appear in cyclical patterns) and Ch 4's encoded values (codes often correspond to threshold tiers).

**Preview of next chapter:** Chapter 6 — apply interest and amortization mathematics to the system's financial machinery. Every system involves money flowing through it; this chapter computes the interest, the amortization, and the credit-card-like dynamics if any.

---

##  AI Wayback Machine
**Emmy Noether** was founded modern abstract algebra in the 1920s — and proved the theorem connecting symmetries to conservation laws. She couldn't hold a salaried position in Germany because she was a woman.

![Emmy Noether](../images/emmy-noether-cb6.png)

*Puppet Art by [Nik Bear Brown](https://www.nikbearbrown.com/).*

**Run this:**

```
Who is Emmy Noether, and how does their work connect to algebra we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Emmy Noether"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Emmy Noether's ideas to a specific concrete problem in this chapter.
- Add a constraint: "Answer including criticisms or limits of Emmy Noether's framework."

What changes? What gets better? What gets worse?
