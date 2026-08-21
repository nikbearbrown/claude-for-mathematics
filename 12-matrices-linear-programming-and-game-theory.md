# Chapter 12 — Matrices, Linear Programming, and Game Theory

## Two problems a manager cannot solve by feel

Between 1997 and 2004, executives from Procter & Gamble, Henkel, Unilever, and Colgate-Palmolive — together most of the French laundry-detergent market — met quietly in Paris cafés to agree on prices. In 2011 French regulators fined them €367.9 million. The puzzle is not that they were caught. It is *why they had to meet at all*. If a high price was best for everyone, why not simply hold it? The math will show that each firm's private incentive pulled the other way — and that no amount of goodwill could fix it, only an (illegal) agreement.

Here is a second, gentler problem. A small factory makes two products on shared machines. Each desk yields \$30 of margin and uses 2 machine-hours; each cabinet yields \$40 and uses 4 hours. There are 100 machine-hours a week and a labor limit too. What mix maximizes profit? You could guess, but the right answer is forced by the constraints — and, remarkably, it always sits at a *corner*.

Both problems are about choosing well — one against a rival, one against a constraint. This chapter builds the three tools that handle them: **matrices** (the language for systems of relationships), **linear programming** (optimizing under linear constraints), and **game theory** (optimizing when someone else is optimizing too).

## The tool, named

A **matrix** is a rectangular table of numbers with rules for adding and multiplying. **Linear programming (LP)** maximizes or minimizes a linear objective subject to linear inequality constraints. A **game** is described by a **payoff matrix**; the **Nash equilibrium** is a choice profile where no player can do better by unilaterally changing. All three are hand-computable at the scale we will work — 2×2 grids and two-variable LPs — and each carries one non-obvious result worth deriving on the page.

## Development

### Matrices as a compact language

A system of linear equations,
$$\begin{aligned} 2x + 4y &= 100 \\ x + y &= 40, \end{aligned}$$
is three things bundled: coefficients, unknowns, right-hand sides. Stack them and you can write the whole system as $A\mathbf{x} = \mathbf{b}$:

$$\underbrace{\begin{bmatrix} 2 & 4 \\ 1 & 1 \end{bmatrix}}_{A}\underbrace{\begin{bmatrix} x \\ y \end{bmatrix}}_{\mathbf{x}} = \underbrace{\begin{bmatrix} 100 \\ 40 \end{bmatrix}}_{\mathbf{b}}.$$

Matrix multiplication is just "apply the recipe": the first row $[2\ 4]$ times the column $[x\ y]^\top$ produces $2x + 4y$, the first equation. When $A$ is invertible the solution is $\mathbf{x} = A^{-1}\mathbf{b}$ — the matrix version of dividing both sides by $A$. Here, subtracting twice the second equation from the first gives $2y = 20$, so $y = 10$, $x = 30$. Matrices do not change *what* you can solve; they give you a notation that scales from two equations to two million.

<!-- → [DIAGRAM: A·x = b schematic — coefficient grid times unknown column equals right-hand-side column; caption: "Ax = b: rows of coefficients times the unknowns equal the right-hand sides."] -->

### Linear programming: why the optimum lives at a corner

Return to the factory. Let $x$ = desks, $y$ = cabinets. Maximize margin $Z = 30x + 40y$ subject to
$$2x + 4y \le 100 \quad(\text{machine-hours}), \qquad x + y \le 40 \quad(\text{labor}), \qquad x, y \ge 0.$$

Each inequality is a half-plane; together they fence off a **feasible region** — a convex polygon. The objective $Z = 30x + 40y$ is a family of parallel "iso-profit" lines; raising $Z$ slides the line outward. To maximize, push the line as far out as it can go while still touching the feasible region. Because the region is a convex polygon and the objective is linear, **the last point of contact is a vertex** (or, in a tie, an entire edge — which still includes vertices). This is the fundamental theorem of linear programming: *if an optimum exists, one occurs at a corner.* You do not need to search the infinite interior; you check finitely many corners. George Dantzig's 1947 simplex method is exactly this insight made into an algorithm — walk from vertex to better adjacent vertex until no neighbor improves. [verify: Dantzig, "Origins of the Simplex Method," 1990]

<!-- → [DIAGRAM: shaded feasible polygon from the two constraint lines, with an iso-profit line sliding outward to its last-touch vertex; corner coordinates labeled; caption: "Slide the iso-profit line outward; it leaves the feasible region at a corner. Check the corners, not the interior."] -->

Find the corners — the intersections of the constraint lines:
- Origin $(0,0)$: $Z = 0$.
- $(40, 0)$ (labor binds, all desks): $Z = 1200$.
- $(0, 25)$ (machine-hours bind, all cabinets): $Z = 1000$.
- Intersection of $2x + 4y = 100$ and $x + y = 40$: solving (as above) gives $(30, 10)$: $Z = 30(30) + 40(10) = 1300$.

The winner is $(30, 10)$ with \$1,300 — a *mix*, where both constraints bind. Now the **shadow price**: relax the machine-hour limit from 100 to 101 and re-solve, and $Z$ rises by a fixed amount per hour. That increment is what one more machine-hour is worth to you — exactly the Lagrange multiplier $\lambda$ from Chapter 11, now wearing operations clothing. The shadow price tells the manager *which* constraint to spend money loosening.

![Feasible-region plot: two constraint lines fencing a shaded polygon with corners at (0,0), (40,0), (30,10), and (0,25), each labeled with its Z-value, and a red dashed iso-profit line touching the optimal corner (30,10) where Z = 1300](images/12-matrices-linear-programming-and-game-theory-fig-01.png)
*Figure 12.1 — The LP optimum sits at a corner: (30, 10), Z = $1,300, where both constraints bind.*

### Game theory: the payoff matrix and Nash equilibrium

When your best move depends on a rival's move, optimization becomes strategic. Lay out the payoffs in a grid. Take the detergent firms, simplified to two, each choosing a High or Low price (payoffs in \$M, *(Firm A, Firm B)*):

| | B: High | B: Low |
|----------|----------|----------|
| **A: High** | (50, 50) | (10, 80) |
| **A: Low** | (80, 10) | (20, 20) |

Read it as Firm A. *If B plays High*, A gets 50 by matching or 80 by undercutting — undercut. *If B plays Low*, A gets 10 by holding High or 20 by matching Low — match Low. Low is better for A no matter what B does: it is a **dominant strategy**. By symmetry Low is dominant for B too. So both play Low and land in (20, 20) — even though both prefer (50, 50). This is the **prisoner's dilemma**: individually rational choices produce a collectively worse outcome.

The cell (Low, Low) is a **Nash equilibrium** — a profile where neither player can gain by changing alone. Check it: from (20, 20), if A switches to High it gets 10 (worse); same for B. No unilateral deviation helps, so the cell is stable. The 2×2 best-response test you just ran is the finite, hand-computable case of John Nash's 1950 result: every finite game has at least one equilibrium (possibly in mixed strategies). [verify: Nash 1950, "Equilibrium Points in N-Person Games," *PNAS*]

![Two-by-two payoff grid for two firms pricing High or Low, with cells (50,50), (10,80), (80,10), and (20,20); the (Low,Low) = (20,20) cell highlighted in red as the Nash equilibrium and (High,High) annotated as jointly best but unstable](images/12-matrices-linear-programming-and-game-theory-fig-02.png)
*Figure 12.2 — The prisoner's dilemma: both firms play their dominant strategy (Low) and land at (20, 20), the stable Nash cell, though both prefer (50, 50).*

This is why the café meetings happened. (High, High) is better for both firms but is *not* a Nash equilibrium — each firm itches to defect to the 80 corner. Cooperation has to be imposed by explicit agreement, which is precisely why it must be secret and illegal, and why cartels tend to collapse. When the game repeats, observable cheating can be punished, which is how OPEC-style coordination is sometimes sustained — but the one-shot logic always tugs toward defection.

Not every game has a *pure*-strategy equilibrium like this one. In games of pure conflict — penalty kicks, bluffing, audit-versus-cheat — any predictable choice can be exploited, so there is no cell that survives the best-response test. The resolution is a **mixed strategy**: each player randomizes, choosing each action with a probability calibrated so the *opponent* is left indifferent between their own options. Nash's 1950 theorem guarantees that with mixing allowed, every finite game has at least one equilibrium. We stop at the existence result and the intuition — randomize so your rival cannot read you — and leave the algebra of solving for the mixing probabilities to a fuller treatment.

## Worked examples

**Example 1 — Solve a 2×2 system as a matrix equation.** A firm's two plants satisfy $3x + 2y = 1800$ (total output) and $x - y = 200$ (capacity gap). In matrix form $\begin{bmatrix} 3 & 2 \\ 1 & -1\end{bmatrix}\begin{bmatrix}x\\y\end{bmatrix} = \begin{bmatrix}1800\\200\end{bmatrix}$. From the second equation $x = y + 200$; substitute: $3(y+200) + 2y = 1800 \Rightarrow 5y = 1200 \Rightarrow y = 240$, $x = 440$. The matrix is just bookkeeping; the algebra is the same algebra.

**Example 2 — Product mix at the corner.** A bakery makes bread (\$3 margin, 1 oven-hour, 2 labor-hours) and cake (\$5 margin, 2 oven-hours, 1 labor-hour). Limits: 60 oven-hours, 60 labor-hours. Maximize $Z = 3x + 5y$ s.t. $x + 2y \le 60$, $2x + y \le 60$. Corners: $(0,0)\to0$; $(30,0)\to90$; $(0,30)\to150$; intersection of the two binding lines, $x + 2y = 60$ and $2x + y = 60$, solves to $(20, 20)\to Z = 60 + 100 = 160$. Optimum at the mixed corner $(20, 20)$, \$160. Check the corners; the interior never wins.

**Example 3 — Find the Nash equilibrium (Coke vs. Pepsi).** Two firms choose a High or Low advertising budget (profits in \$M, *(Coke, Pepsi)*):

| | Pepsi: High | Pepsi: Low |
|----------|-------------|-------------|
| **Coke: High** | (40, 40) | (70, 30) |
| **Coke: Low** | (30, 70) | (50, 50) |

Read as Coke: if Pepsi plays High, Coke gets 40 (High) vs. 30 (Low) → High. If Pepsi plays Low, Coke gets 70 (High) vs. 50 (Low) → High. High is dominant for Coke; by symmetry for Pepsi. Equilibrium: (High, High) at (40, 40) — both spend heavily and both end up worse than the (50, 50) they would reach if they could both restrain spending. The advertising arms race is a prisoner's dilemma. (Adapted from the `mba-economics` exercise set.)

## Back to the two problems

The detergent cartel: each firm's dominant strategy was the low price, so the Nash equilibrium was mutual defection — the competitive, low-profit outcome. The monopoly-level profit at (High, High) was reachable only by agreement, because it was not an equilibrium; that is the mathematical reason the executives needed a conspiracy and the reason it was fragile. The factory: the profit-maximizing mix was \$1,300 at the corner $(30, 10)$, found not by intuition but by checking the vertices of the feasible region, with the shadow prices telling the manager which constraint to relax first.

## Where it generalizes

LP underlies supply-chain, scheduling, blending, transportation, and revenue-management systems used daily; modern solvers handle millions of variables, but the corner principle is the same one Dantzig — and, independently and earlier, Leonid Kantorovich for the Soviet plywood trust in 1939 — exploited. [verify: Kantorovich 1939] Matrices reappear wherever a system of relationships needs solving: regression normal equations (Ch. 9), portfolio covariance matrices (Ch. 10), and input–output models. Game theory frames pricing wars, bargaining, auctions, and the algorithmic-pricing question now drawing antitrust scrutiny — can pricing bots reach collusion-like outcomes without ever meeting in a café? The shadow-price link to Chapter 11's Lagrange multiplier is the unifying thread: the value of relaxing a binding constraint is one idea wearing two hats.

One honest caveat. Nash equilibrium is *normative* — what perfectly rational players who know each other's payoffs would do. Experiments find systematic deviations: people fail to iterate dominance, and simpler heuristics sometimes predict real play better. [verify: experimental game-theory deviation studies] The math is exact; the inputs — the payoffs, the constraints, the assumption that your rival is rational and informed — are where business judgment lives. The matrix solves the system; it cannot tell you whether your competitor will actually play the equilibrium.

## Exercises

1. **Solve and interpret a system.** Write $4x + y = 90$, $x + 3y = 60$ as $A\mathbf{x} = \mathbf{b}$, solve by elimination, and state what units $x$ and $y$ would carry if they were two products sharing two resources.
2. **Build a feasible region (derive the corner).** Maximize $Z = 5x + 4y$ subject to $6x + 4y \le 24$, $x + 2y \le 6$, $x, y \ge 0$. Find all corner points algebraically, evaluate $Z$ at each, and identify the optimum. Sketch the region and the iso-profit line at the optimum.
3. **Shadow price.** In Exercise 2, increase the first constraint's right-hand side from 24 to 25 and re-solve. Report the change in $Z$ per unit — the shadow price of that resource — and explain what it tells a manager deciding whether to buy more of it.
4. **Find the equilibrium and the dilemma.** Two gas stations choose Regular or Discount pricing with payoffs (A, B): (R,R)=(8,8), (R,D)=(2,10), (D,R)=(10,2), (D,D)=(4,4). Identify each player's dominant strategy, the Nash equilibrium, and whether the equilibrium is the jointly best outcome. Explain the tension in one sentence.
5. **A game with no dominant strategy.** Construct a 2×2 payoff matrix in which neither player has a dominant strategy but a pure Nash equilibrium still exists, and verify it with the best-response check. (Hint: a coordination game.)

## Sources

- von Neumann, J., & Morgenstern, O. (1944). *Theory of Games and Economic Behavior*. Princeton University Press (the payoff matrix; minimax).
- Nash, J. F. (1950). "Equilibrium Points in N-Person Games." *PNAS*, 36(1), 48–49.
- Dantzig, G. B. (1990). "Origins of the Simplex Method," in *A History of Scientific Computing* (ACM Press / Addison-Wesley). (Simplex method developed 1947.)
- Kantorovich, L. V. (1939). *Mathematical Methods of Organizing and Planning Production* (independent origin of LP).
- Karmarkar, N. (1984). Interior-point method for LP (polynomial-time solving).
- Autorité de la concurrence (2011). Decision 11-D-17 of 8 December 2011 (French laundry-detergent cartel; total penalties €367.9 million as corrected 20 Dec 2011).
- Detergent-cartel and Coke–Pepsi examples adapted from `mba-economics`, ch. 10 (Monopolistic Competition and Oligopoly).
