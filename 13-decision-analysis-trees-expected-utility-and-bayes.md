# Chapter 13 — Decision Analysis: Trees, Expected Utility, and Bayes' Rule

## A lawsuit, and a coin you would not flip

A company is sued. The plaintiff offers to settle for \$400,000 today. Go to trial instead and your counsel estimates a 60% chance of winning (you pay nothing) and a 40% chance of losing (you pay \$1.2 million, all in). Settle, or fight? The arithmetic looks easy: the trial's expected cost is $0.6(0) + 0.4(1{,}200{,}000) = \$480{,}000$, which is worse than settling for \$400,000. Take the settlement.

But hold on. Most CFOs facing that exact choice would *still* settle even if the trial's expected cost were a bit *below* \$400,000 — and they would be right to. Why would anyone refuse a gamble with a better expected value? The answer is the difference between expected *money* and expected *welfare*, and it is the same reason no one will pay much for a coin-flip game whose expected payout is infinite. This chapter builds the machinery that handles decisions under uncertainty honestly: the **decision tree** and its rollback, **expected monetary value** and its limits, **expected utility** and risk aversion, the **value of information**, and **Bayes' rule** for updating beliefs as evidence arrives.

## The tool, named

A **decision tree** lays out choices and chance events in sequence; you evaluate it by **rolling back** — taking expectations at chance nodes and the best option at decision nodes. **Expected monetary value (EMV)** is the probability-weighted average payoff. **Expected utility** replaces money with a utility function when the decision-maker is risk-averse. The **expected value of perfect information (EVPI)** caps what any study could be worth. **Bayes' rule** turns a prior belief plus evidence into an updated belief. Each is built here, not handed down.

## Development

### The decision tree and roll-back

Draw decisions as squares, chance events as circles, and label each branch with its probability and payoff. The litigation problem is two branches off a single decision:

<!-- → [DIAGRAM: decision tree — square (settle vs. trial); "settle" leads to −$400K; "trial" leads to a chance circle with 0.6 → $0 and 0.4 → −$1.2M; rolled-back EMV −$480K written at the chance node; caption: "Roll back: expectation at the chance circle, best choice at the decision square."] -->

To evaluate, work *backward* from the tips:
- At a **chance node**, compute the expected value — the probability-weighted average. Trial: $0.6(0) + 0.4(-1{,}200{,}000) = -\$480{,}000$.
- At a **decision node**, pick the branch with the best rolled-back value. Settle (−\$400,000) beats trial (−\$480,000).

Rolling back collapses an entire tree, however bushy, into a single number and a recommended first move. Howard Raiffa made the decision tree the standard representation of choice under uncertainty. [verify: Raiffa 1968, *Decision Analysis*] One discipline the tree enforces: only *future* cash flows belong at the nodes. Money already spent — legal fees to date, sunk R&D — is gone and must not appear; the tree, like the derivative in Chapter 11, looks only forward.

![Decision tree: a decision square branching to a Settle path ending at −$400K (marked chosen, in red) and a Trial path leading to a chance circle with EMV −$480K that splits into 0.6 → $0 and 0.4 → −$1.2M](images/13-decision-analysis-trees-expected-utility-and-bayes-fig-01.png)
*Figure 13.1 — Rolling back the litigation tree: settle (−$400K) beats the trial gamble (EMV −$480K).*

### Why EMV is not the whole story: expected utility

EMV treats \$1.2 million lost as exactly twelve times as bad as \$100,000 lost. For a firm that can absorb \$100,000 easily but would be crippled by \$1.2 million, that is false. Daniel Bernoulli saw this in 1738 while puzzling over the **St. Petersburg paradox**: a coin-flip game that pays $2^n$ if the first head appears on toss $n$ has *infinite* expected monetary value, yet no one will pay more than a few dollars to play. [verify: Bernoulli 1738, *Specimen theoriae novae de mensura sortis*] Bernoulli's resolution: people maximize expected **utility**, not expected money, and the utility of wealth rises with *diminishing* increments — the tenth thousand dollars matters less than the first.

A risk-averse decision-maker has a *concave* utility function $u(w)$. Apply it to the gamble: the **certainty equivalent** is the sure amount whose utility equals the gamble's expected utility, and for a concave $u$ it lies *below* the EMV. The gap is the **risk premium** — what you would pay to be rid of the uncertainty.

![Concave utility curve u(w) = √w with the two gamble outcomes ($0 and $1M) joined by a chord; the gamble's expected utility (500) maps to a certainty equivalent of $250K on the curve, well below the $500K EMV, with the $250K horizontal gap labeled risk premium](images/13-decision-analysis-trees-expected-utility-and-bayes-fig-02.png)
*Figure 13.2 — Concave utility: the certainty equivalent ($250K) sits below the EMV ($500K); the gap is the risk premium.*

<!-- → [DIAGRAM: concave utility-of-wealth curve with the gamble's two outcomes, its EMV, its expected utility, and the certainty equivalent marked; the horizontal gap between EMV and certainty equivalent labeled "risk premium"; caption: "Concave utility: the certainty equivalent sits below the EMV. The gap is what risk aversion costs you."] -->

This is why insurance exists: a risk-averse firm pays a premium *above* the actuarial (EMV) cost of a loss to shed a low-probability catastrophe, and both sides are better off. It is also why the CFO settles even on a slightly favorable trial gamble — the small chance of a firm-threatening \$1.2 million loss carries more disutility than the expected-money math admits. The von Neumann–Morgenstern axioms (completeness, transitivity, continuity, independence) give the rigorous conditions under which "maximize expected utility" is the right rule. [verify: von Neumann & Morgenstern 1944]

### Bayes' rule, built from counting

Now the other half of decision-making: updating beliefs when evidence arrives. A due-diligence test for fraud is 90% sensitive (flags 90% of truly fraudulent firms) and has a 5% false-positive rate (flags 5% of clean firms). The base rate of fraud is 1%. A firm tests positive. How worried should you be?

Most people answer "around 90%." The right answer is far lower, and the cleanest way to see it is to *count actual firms* rather than juggle percentages — the natural-frequency presentation that has been shown to lift correct-reasoning rates dramatically — in the classic studies, from well under a quarter to roughly half (Gigerenzer & Hoffrage, 1995; the exact percentages vary by task and are illustrative here). Take 1,000 firms:

- Fraudulent: 1% of 1,000 = **10 firms**. The test flags 90% of them → **9 flagged**.
- Clean: **990 firms**. The test falsely flags 5% → **49.5 flagged** (call it ~50).
- Total flagged: $9 + 50 = 59$ firms. Of those, only **9 are actually fraudulent**.

So the probability that a flagged firm is fraudulent is $9/59 \approx 15\%$ — not 90%. The flood of false positives from the large clean population swamps the true positives from the tiny fraudulent one. This is **base-rate neglect**, and it has a formal name when reversed — the **prosecutor's fallacy**: confusing $P(\text{flag}\mid\text{fraud})$ with $P(\text{fraud}\mid\text{flag})$. They are not the same number, and Bayes' rule is exactly the correction.

![Natural-frequency tree: 1,000 firms split into 10 fraudulent and 990 clean; the fraudulent branch yields 9 flagged and 1 missed, the clean branch yields about 50 falsely flagged and 940 cleared; of 59 flagged total, only 9 are fraudulent, giving P(fraud | flag) = 9/59 ≈ 15%](images/13-decision-analysis-trees-expected-utility-and-bayes-fig-03.png)
*Figure 13.3 — Counting actual firms: of 59 flagged, only 9 are fraudulent, so a positive flag means about a 15% chance of fraud.*

<!-- → [DIAGRAM: natural-frequency tree — 1,000 firms split into 10 fraud / 990 clean, each split into flagged/not-flagged, with counts 9, 1, 50, 940; caption: "Count the firms. Of 59 flagged, only 9 are fraudulent — about 15%."] -->

The formula is just that counting written symbolically. Start from the definition of conditional probability, $P(A\mid B) = P(A \cap B)/P(B)$, applied both ways:

$$P(H \mid E) = \frac{P(H \cap E)}{P(E)}, \qquad P(E \mid H) = \frac{P(H \cap E)}{P(H)}.$$

Solve the second for the joint probability, $P(H \cap E) = P(E\mid H)\,P(H)$, and substitute:

$$\boxed{P(H \mid E) = \frac{P(E\mid H)\,P(H)}{P(E)}}$$

with the denominator $P(E) = P(E\mid H)P(H) + P(E\mid \neg H)P(\neg H)$ — the total probability of seeing the evidence. Plug in: $P(\text{fraud}\mid\text{flag}) = \frac{(0.90)(0.01)}{(0.90)(0.01) + (0.05)(0.99)} = \frac{0.009}{0.009 + 0.0495} = \frac{0.009}{0.0585} \approx 0.154$. The same 15%, now from the rule that Thomas Bayes and Richard Price set out in 1763. [verify: Bayes & Price 1763] The natural-frequency counting and the formula are the same computation; the counting is just easier on the human mind.

### The value of information: EVPI

Should you pay for a market study before launching? Information is worth something only if it would *change* what you do. The **expected value of perfect information** is the ceiling:

$$\text{EVPI} = (\text{expected payoff if you knew the outcome in advance}) - (\text{best expected payoff under current uncertainty}).$$

Suppose a launch yields +\$5M if the market is "good" (probability 0.5) and −\$3M if "bad" (0.5). Under uncertainty, launching has EMV $0.5(5) + 0.5(-3) = \$1\text{M}$ — positive, so you would launch, and risk the −\$3M outcome. With *perfect* information you would launch only when good (+\$5M) and walk away when bad (\$0): expected payoff $0.5(5) + 0.5(0) = \$2.5\text{M}$. So $\text{EVPI} = 2.5 - 1 = \$1.5\text{M}$. No study — perfect or not — is worth more than \$1.5M here, because that is the entire value of removing the uncertainty. Real studies are imperfect and worth strictly less; EVPI is the budget cap. [verify: Raiffa & Schlaifer 1961]

## Worked examples

**Example 1 — Roll back a two-stage tree.** A firm can launch now or run a \$0.2M pilot first. Launch now: +\$5M (good, 0.5) or −\$3M (bad, 0.5), EMV = \$1M. Pilot, then decide: the pilot reveals good or bad perfectly (idealized). After a "good" signal, launch → +\$5M; after "bad," abandon → \$0. Expected payoff before the \$0.2M cost: \$2.5M; net of the pilot, \$2.3M. Since \$2.3M > \$1M, run the pilot. The pilot's value, \$1.3M, is below the \$1.5M EVPI of Example reasoning above — consistent, because a one-period pilot here recovers most but the cost eats some.

**Example 2 — Certainty equivalent and the risk premium.** A firm with utility $u(w) = \sqrt{w}$ faces a gamble: \$0 or \$1,000,000, each with probability 0.5 (EMV = \$500,000). Expected utility = $0.5\sqrt{0} + 0.5\sqrt{1{,}000{,}000} = 0.5(1000) = 500$. The certainty equivalent solves $\sqrt{w} = 500$, so $w = \$250{,}000$. The firm is indifferent between the gamble and a *sure* \$250,000 — far below the \$500,000 EMV. The \$250,000 gap is the risk premium that concave utility imposes.

**Example 3 — Bayes on a quality inspection.** A supplier's parts are 4% defective. An inspection catches 95% of defective parts and wrongly rejects 8% of good parts. A part is rejected — what is the chance it is truly defective? Of 10,000 parts: 400 defective, 380 correctly rejected; 9,600 good, 768 wrongly rejected. Total rejected = 1,148; truly defective among them = 380. So $P(\text{defective}\mid\text{rejected}) = 380/1148 \approx 33\%$. Even a fairly accurate test, against a low base rate, leaves two-thirds of rejected parts actually fine — the recurring lesson of Bayes.

## Back to the lawsuit

The tree said settle: trial's EMV of −\$480,000 is worse than the −\$400,000 settlement. But notice the deeper reason the CFO would settle even on a closer call. Going to trial stakes a 40% chance of a \$1.2 million loss — and for a firm that size, the *disutility* of that tail outcome exceeds what EMV records. The certainty equivalent of the trial gamble, under any concave utility, is worse than its already-unfavorable EMV. The tree computes; the risk attitude decides. And had counsel offered to pay for an expert assessment that would sharpen the 60/40 odds, EVPI would have told the firm the most that assessment could possibly be worth.

## Where it generalizes

Decision trees and rollback structure capital-budgeting under uncertainty (invest / pilot / abandon, with chance nodes for market success — connecting to the NPV of Chapter 5 and real-options thinking), litigation strategy, R&D staging, and product launches. Expected utility underlies insurance, hedging (Chapter 14), and every "how much risk should we carry" question. Bayes' rule is now embedded in everyday analytics — A/B testing, demand forecasting, fraud and anomaly detection, spam filtering, medical and credit screening — anywhere a prior belief meets new data. This is also where Chapter 7's deferred Bayesian updating finally lands.

Two honest caveats. First, the tree is only as good as its inputs: the probabilities and the utility function are *subjective* judgments, often hard to elicit, and the crisp arithmetic can lend them false authority. Second, expected utility is the *normative* target, not a description of behavior — the Allais and Ellsberg paradoxes and Kahneman and Tversky's prospect theory document that real people systematically violate the very axioms the method assumes. [verify: Allais 1953; Ellsberg 1961; Kahneman & Tversky 1979] The math cannot tell you how risk-averse you *ought* to be, nor supply the probabilities; it can only be honest, fast, and explicit once you have owned those choices.

## Exercises

1. **Roll back a tree.** A firm chooses between Project A (sure +\$2M) and Project B (+\$6M with probability 0.4, −\$1M with probability 0.6). Compute EMV for each, draw the tree, and state the risk-neutral choice. Then say how the answer might flip for a strongly risk-averse firm.
2. **Derive Bayes' rule.** Starting from $P(A\mid B) = P(A\cap B)/P(B)$, derive $P(H\mid E) = P(E\mid H)P(H)/P(E)$, writing the denominator as a total probability. Then apply it: a test is 99% sensitive, 95% specific, base rate 0.5%; find the post-positive probability and explain why it is low.
3. **Natural frequencies vs. formula.** Re-solve Exercise 2's numbers by counting out of 100,000 cases instead of using the formula, and confirm you get the same posterior. Comment on which presentation you found clearer and why the literature recommends frequencies.
4. **EVPI (build it).** A decision yields +\$8M if a competitor exits (prob 0.3) and −\$2M if it stays (0.7). Compute the best action and its EMV under uncertainty, the expected payoff under perfect information, and the EVPI. State the maximum a manager should pay for a perfect forecast.
5. **Certainty equivalent.** With $u(w) = \ln(w)$ and current wealth \$1,000,000, a firm faces a 50/50 gamble to gain or lose \$300,000. Compute the expected utility, the certainty equivalent, and the risk premium. Interpret the sign.

## Sources

- Bernoulli, D. (1738). "Specimen theoriae novae de mensura sortis." *Commentarii Academiae Scientiarum Imperialis Petropolitanae*, V, 175–192 (Eng. trans. Sommer, *Econometrica*, 22, 1954, 23–36).
- Bayes, T., & Price, R. (1763). "An Essay towards Solving a Problem in the Doctrine of Chances." *Philosophical Transactions of the Royal Society*, 53, 370–418.
- von Neumann, J., & Morgenstern, O. (1944). *Theory of Games and Economic Behavior* (expected-utility axioms).
- Raiffa, H., & Schlaifer, R. (1961). *Applied Statistical Decision Theory*. Harvard University Press; Raiffa, H. (1968). *Decision Analysis: Introductory Lectures on Choices under Uncertainty*. Addison-Wesley (the tree and EVPI).
- Gigerenzer, G., & Hoffrage, U. (1995). "How to Improve Bayesian Reasoning Without Instruction: Frequency Formats." *Psychological Review*, 102(4), 684–704 (natural frequencies).
- Allais (1953); Ellsberg (1961); Kahneman & Tversky (1979), prospect theory (descriptive violations).
- Litigation and market-research examples adapted from `mba-business-law` and `mba-management`/`mba-marketing`.
