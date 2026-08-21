# Probability and Expected Value

*The math of acting under uncertainty — and why the right number is never the whole answer.*

---

## A room full of professionals gets the math backwards

Daniel Kahneman puts two scenarios in front of a room of investment professionals — people who price risk for a living.

In Scenario A, a firm can lock in a guaranteed profit of \$240,000. In Scenario B, it flips a coin: heads, it makes \$500,000; tails, it makes nothing. The coin flip's *average* payoff is \$250,000 — ten thousand dollars more than the sure thing. On the arithmetic alone, the coin flip wins.

Nobody takes the coin flip.

Then Kahneman flips the framing. Now both options are losses. Option A is a guaranteed loss of \$240,000. Option B is a coin flip: heads, lose \$500,000; tails, lose nothing — an average loss of \$250,000, *worse* than the certain loss. On the arithmetic, the sure loss wins.

They all take the coin flip.

![Two number lines comparing a sure $240k payoff (zero spread) against a coin flip paying $0 or $500k with the same expected value but a $250k standard deviation](images/07-probability-and-expected-value-fig-02.png)
*Figure 7.1 — Same expected value, opposite spread: the dimension EV cannot see.*

Same arithmetic, opposite decisions. The only thing that changed was the word *gain* or *loss*. Before we can even ask why trained professionals reverse themselves, we need to be able to compute that \$250,000 in the first place — to say precisely what "the average payoff of a coin flip" *means* when the flip happens exactly once and you will never see "the average." That number is an **expected value**, and the gap between computing it correctly and acting on it correctly is the subject of this chapter. The math gives you the number. It does not give you the decision. Knowing exactly where that boundary falls is the most useful thing this chapter can teach you.

---

## The tool, named

We need a way to reason about events that have not happened yet — a launch that may or may not succeed, a customer who may or may not respond, a market that may rise or fall. The tool is **probability**: a number between 0 and 1 attached to each possible outcome, measuring how likely it is. From probabilities we build a **random variable** — a quantity whose value depends on the outcome — and we summarize that random variable with two numbers: its **expected value** $E[X]$ (the long-run average) and its **variance** $\operatorname{Var}(X)$ (how spread out the outcomes are around that average).

That is the entire engine. Finance calls $E[X]$ "expected return" and $\operatorname{Var}(X)$ "risk." Marketing calls a response count a "binomial." Management calls $E[X]$ "expected monetary value." Every one of them is the same machine, relabeled. We build it once here.

---

## Development: from sample spaces to expected value

### The sample space and the three rules

Start with the set of everything that *could* happen. Roll one die: the **sample space** is $S = \{1,2,3,4,5,6\}$. An **event** is any subset — "roll an even number" is $\{2,4,6\}$. A **probability** $P$ assigns a number to each event. Andrey Kolmogorov, in 1933, reduced all of probability to three axioms:

1. **Non-negativity.** $P(A) \ge 0$ for every event $A$. Likelihoods are never negative.
2. **Total mass one.** $P(S) = 1$. Something in the sample space must happen.
3. **Additivity.** If $A$ and $B$ cannot both occur (they are *disjoint*), then $P(A \cup B) = P(A) + P(B)$.

Everything else follows. The **complement rule**, $P(\text{not }A) = 1 - P(A)$, comes from axioms 2 and 3 applied to $A$ and "not $A$," which together fill $S$. The general **addition rule**, for events that *can* overlap, corrects for double-counting:

$$P(A \cup B) = P(A) + P(B) - P(A \cap B).$$

Notice what the axioms do *not* tell you: what the probabilities actually *are*. That you must supply. For a fair die, symmetry gives each face $1/6$. For "this product launch succeeds," there is no symmetry and no long run — you must estimate $p$ from judgment, comparable launches, or a model. This is the first appearance of the chapter's recurring theme: **the math operates on probabilities; it never hands them to you.** Two readings of "probability" both satisfy Kolmogorov's axioms — the *frequentist* reading (the long-run fraction of times the event occurs in many repetitions) and the *subjective* reading (your calibrated degree of belief). The one-off launch has no long run, so the MBA almost always works in the second sense, whether they admit it or not.

### Conditional probability and independence

New information changes probabilities. The probability of $A$ *given that* $B$ has occurred is

$$P(A \mid B) = \frac{P(A \cap B)}{P(B)}, \qquad P(B) > 0.$$

You shrink the sample space to the world where $B$ is true and ask what fraction of *that* world also has $A$. Rearranging gives the **multiplication rule**:

$$P(A \cap B) = P(A \mid B)\,P(B).$$

Two events are **independent** when learning one tells you nothing about the other: $P(A \mid B) = P(A)$, equivalently $P(A \cap B) = P(A)P(B)$. Independence is an *assumption about the world*, not a property you can read off the algebra — and getting it wrong is how careful people produce confident nonsense.

The sharpest trap here is confusing $P(A \mid B)$ with $P(B \mid A)$ — they are almost never equal. Kahneman and Tversky (1973) gave people a personality sketch of a man — tidy, introverted, fond of detail — drawn from a pool that was 70% lawyers and 30% engineers, and asked his profession. People answered "engineer" because the sketch *sounds* like an engineer: they reported $P(\text{sketch} \mid \text{engineer})$ and ignored the base rate $P(\text{engineer}) = 0.30$. But the question asked for $P(\text{engineer} \mid \text{sketch})$, and a 30% prior drags that answer well below intuition. This same error — a positive drug test, a flagged transaction, a positive diagnostic where $P(\text{test}^+ \mid \text{guilty})$ is high but $P(\text{guilty} \mid \text{test}^+)$ is low because guilt is rare — sits behind nearly every screening decision a manager signs off on. The machinery for *correctly* flipping $P(A\mid B)$ into $P(B\mid A)$ is **Bayes' rule**; we have planted its seed here and develop it fully in **Chapter 13**.

### Random variables, expected value, and variance

A **random variable** $X$ is a function that attaches a number to each outcome. Let $X$ be the payoff of a gamble: win \$500,000 with probability $0.5$, win \$0 with probability $0.5$. The **expected value** is the probability-weighted average of the possible values:

$$E[X] = \sum_i x_i\, p(x_i).$$

For the coin flip, $E[X] = 0.5(500{,}000) + 0.5(0) = 250{,}000$. That is Kahneman's \$250,000. It is a *weighted average* — the same operation as Chapter 1's averages, with probabilities as the weights — and physically it is the **balance point** of the distribution: place a weight $p(x_i)$ at each position $x_i$ on a number line, and $E[X]$ is where the line balances. Crucially, the coin pays \$500,000 or \$0; it *never* pays \$250,000. The expected value is a number the decision-maker may never actually experience on a single play. Hold that thought — it is the cold open's whole point.

Expected value alone cannot distinguish a coin flip worth \$250,000 from a sure \$250,000. We need a measure of *spread*. The **variance** is the expected squared distance from the mean:

$$\operatorname{Var}(X) = E\!\left[(X - \mu)^2\right], \qquad \mu = E[X].$$

Squaring makes deviations positive (so they don't cancel) and punishes large misses disproportionately. Expanding the square and using $E[\mu] = \mu$ gives the computational form, derived once and used forever:

$$\operatorname{Var}(X) = E[X^2] - (E[X])^2.$$

For the coin flip: $E[X^2] = 0.5(500{,}000)^2 + 0.5(0)^2 = 1.25 \times 10^{11}$, and $(E[X])^2 = (250{,}000)^2 = 6.25 \times 10^{10}$, so $\operatorname{Var}(X) = 6.25 \times 10^{10}$. The **standard deviation** $\sigma = \sqrt{\operatorname{Var}(X)} = 250{,}000$ — back in dollars, the natural scale of spread. The sure thing has $\sigma = 0$. *That* is the difference the room responded to, and it is invisible to expected value.

### The variance algebra — the shared engine of the rest of this book

Two identities about how $E$ and $\operatorname{Var}$ behave under scaling and addition are so important that the next three chapters are built on them. Read this section slowly.

**Expectation is linear.** For constants $a$ and $b$,

$$E[aX + b] = a\,E[X] + b.$$

Scaling and shifting the variable scales and shifts its average. Nothing surprising.

**Variance is not linear — it scales by the square.** A shift $b$ moves every outcome equally and changes spread not at all; a scale $a$ stretches every deviation by $a$, and since variance squares deviations,

$$\boxed{\operatorname{Var}(aX + b) = a^2 \operatorname{Var}(X).}$$

In standard-deviation terms, $\sigma_{aX+b} = |a|\,\sigma_X$. Double a payoff and you double its standard deviation but *quadruple* its variance.

**For independent variables, variances add — standard deviations do not.** If $X$ and $Y$ are independent,

$$\boxed{\operatorname{Var}(X + Y) = \operatorname{Var}(X) + \operatorname{Var}(Y).}$$

This is the single most misremembered fact in applied statistics, so state it as a warning: **standard deviations do not add.** If $X$ and $Y$ each have $\sigma = 10$, then $X+Y$ has *variance* $100 + 100 = 200$ and standard deviation $\sqrt{200} \approx 14.1$ — **not** $20$. The standard deviation of a sum of independent things grows like the square root of the count, not linearly. Get this wrong and every standard error and every portfolio risk you compute later will be wrong.

Why does this matter beyond this chapter? Because two of the most important formulas you will meet are *nothing but* this algebra applied to a sum:

- **Chapter 8's standard error of the mean, $\sigma/\sqrt{n}$,** is what you get when you compute $\operatorname{Var}$ of an average of $n$ independent observations. The $\sqrt{n}$ comes directly from "variances add, then we divide by $n^2$." If standard deviations added, the standard error would be $\sigma$ and sampling would never help.
- **Chapter 10's portfolio variance** is $\operatorname{Var}(w_1 R_1 + w_2 R_2)$ expanded. When the assets are *not* independent, a covariance term appears — but the skeleton is exactly the boxed identities above. The entire counterintuitive result that combining risky assets can lower risk falls out of variance algebra you already know.

![Box diagram showing two independent variables each with standard deviation 10 combining to variance 200 and standard deviation about 14.1, with the tempting answer of 20 crossed out](images/07-probability-and-expected-value-fig-03.png)
*Figure 7.3 — Variances add, standard deviations do not: the most misremembered fact in applied statistics.*

If only one equation from this chapter survives in your memory, make it the boxed pair. Everything analytical in the back half of the book inherits them.

### Two named distributions: binomial and normal

Most business random variables are built from repeated yes/no trials. Send a mailing to $n$ customers; each responds independently with probability $p$. The number of responses $X$ is a **binomial** random variable, $X \sim \text{Binomial}(n, p)$. Each customer is a single Bernoulli trial $X_i$ — $1$ for a response, $0$ otherwise — with $E[X_i] = p$ and (using the computational form) $\operatorname{Var}(X_i) = E[X_i^2] - p^2 = p - p^2 = p(1-p)$. Because $X = X_1 + \dots + X_n$ is a sum of $n$ independent trials, the variance algebra hands us the answers directly — no new formula to memorize:

$$E[X] = np, \qquad \operatorname{Var}(X) = np(1-p).$$

Send to 10,000 customers with a 2% response rate: expect $np = 200$ responses, with standard deviation $\sqrt{10{,}000 \times 0.02 \times 0.98} \approx 14$.

Now stack the bars of a binomial for growing $n$. Abraham de Moivre noticed in 1733 that they settle into a smooth, symmetric bell — the **normal distribution**. The normal is not a mysterious gift from heaven; it is *what binomial counting turns into at scale*. A normal distribution is fixed by two numbers, its mean $\mu$ and standard deviation $\sigma$, and obeys the empirical rule: about 68% of outcomes fall within $\mu \pm \sigma$, 95% within $\mu \pm 2\sigma$, and 99.7% within $\mu \pm 3\sigma$. We treat the normal as a *shape* and read areas from software or tables; the calculus that defines those areas precisely waits for **Chapter 11**. The reason the normal appears everywhere — sample means in Chapter 8, returns in Chapter 10 — is the same reason de Moivre found it: sums and averages of many independent pieces pile up into a bell.

---

## Worked examples

### Example 1 — The insurance premium (why a fair price isn't the price)

A firm faces a 1-in-100 chance of a \$1,000,000 loss this year; otherwise it loses nothing. Let $L$ be the loss. Then

$$E[L] = 0.01(1{,}000{,}000) + 0.99(0) = \$10{,}000.$$

![Probability tree splitting the firm's year into a 1-in-100 chance of a $1,000,000 loss and a 99-in-100 chance of no loss, the branch products summing to an expected loss of $10,000](images/07-probability-and-expected-value-fig-01.png)
*Figure 7.2 — The insurance loss as a probability tree: branch payoffs times probabilities sum to E[L].*

The **expected loss** is \$10,000. An insurer offers coverage for \$13,000 — a premium *above* the expected loss. Should the firm buy it?

Compute the variance the firm carries if it self-insures. $E[L^2] = 0.01(1{,}000{,}000)^2 = 10^{10}$, so $\operatorname{Var}(L) = 10^{10} - (10{,}000)^2 = 9.9 \times 10^9$, giving $\sigma_L \approx \$99{,}500$. The firm's *average* loss is \$10,000, but the spread around it is enormous: in the bad year it is out a million dollars, possibly enough to end the firm.

Now look at the insurer. It writes this same policy for 10,000 firms with *independent* risks. Its total payout is a binomial-like sum; by the variance algebra, the *variance of its average payout per policy* is $\operatorname{Var}(L)/10{,}000$ — the $\sigma/\sqrt{n}$ effect again — so its standard deviation per policy shrinks by a factor of $\sqrt{10{,}000} = 100$, to about \$995. The expected loss is \$10,000 for *both* parties. The insurer faces almost no spread; the single firm faces ruinous spread. **That gap — not the expected value, which is identical — is what the \$3,000 markup buys.** A risk-averse firm rationally pays more than the fair value to move variance it cannot survive onto a party that has diversified it away. (We compute that variance reduction rigorously in Chapter 10; here, notice that EV alone says "never pay above \$10,000," and EV alone is wrong.)

### Example 2 — A direct-mail campaign as a binomial

Marketing plans a campaign to 50,000 customers; historical response rate is $p = 0.03$. Each customer responds independently. Let $X$ be the number of responses.

$$E[X] = np = 50{,}000 \times 0.03 = 1{,}500.$$
$$\operatorname{Var}(X) = np(1-p) = 50{,}000 \times 0.03 \times 0.97 = 1{,}455, \quad \sigma_X = \sqrt{1{,}455} \approx 38.1.$$

Because $n$ is large, the binomial is well-approximated by a normal with $\mu = 1{,}500$, $\sigma \approx 38$. By the empirical rule, we expect responses in $1{,}500 \pm 2(38)$, i.e. roughly **1,424 to 1,576**, about 95% of the time. ![Bell curve for campaign responses with mean 1,500 and standard deviation about 38, shading the plus-or-minus-two-sigma band from 1,424 to 1,576 that holds about 95 percent of outcomes](images/07-probability-and-expected-value-fig-04.png)
*Figure 7.4 — The direct-mail binomial as a normal: 95% of outcomes fall in 1,424–1,576.*

The planner who budgets fulfillment for exactly 1,500 and panics at 1,540 has confused the expected value with the realized outcome — the very confusion the chapter exists to prevent. The spread is not error; it is the irreducible randomness of 50,000 independent decisions. (This binomial-to-normal bridge is exactly the machinery Chapter 8 uses to put a confidence interval around the response *rate*.)

### Example 3 — The St. Petersburg paradox (infinite EV, near-zero value)

Here is a gamble. Flip a fair coin repeatedly until it lands heads. If the first heads comes on flip $k$, you win $2^k$ dollars. What is it worth?

The probability the first heads is on flip $k$ is $(1/2)^k$, and the payoff is $2^k$, so each term of the expected value is $(1/2)^k \cdot 2^k = 1$:

$$E[X] = \sum_{k=1}^{\infty} \left(\tfrac{1}{2}\right)^k 2^k = 1 + 1 + 1 + \cdots = \infty.$$

The expected payoff is *infinite*. The EV-maximizer should pay any finite price — a million dollars, a billion — to play. Yet almost no one will pay even \$20. Daniel Bernoulli posed this in 1738 and resolved it: people value not dollars but the *usefulness* of dollars, and each additional dollar is worth a little less than the one before (diminishing marginal utility). If you value money by, say, $\log(\text{wealth})$ rather than wealth itself, the expected *utility* of the gamble is finite and modest. This is the founding argument — formalized two centuries later by von Neumann and Morgenstern's expected-utility theory — that **a rational agent maximizes expected utility, not expected monetary value.** The St. Petersburg gamble is the cleanest proof that EV is not the whole story: here EV is literally infinite and the right price is about lunch money.

---

## Back to the room of professionals

We can now name exactly what happened. The expected values were never in dispute — \$250,000 for the coin flip, \$240,000 for the sure thing; we computed that on the first page. So why did a room of professionals reverse course when "gain" became "loss"?

Three answers, in order of how much each chapter can claim:

1. **EV is necessary but not sufficient.** The two options differ not only in expected value but in *variance*: the coin flip has $\sigma = 250{,}000$, the sure thing has $\sigma = 0$. A risk-averse decision-maker — one with diminishing marginal utility, exactly Bernoulli's resolution — can rationally prefer the lower-EV sure thing in the gain frame. So far the math accommodates the choice.

2. **But the *reversal* is not rational on any fixed utility function.** Kahneman and Tversky's point in *prospect theory* (1979) is that people are risk-averse over gains and risk-*seeking* over losses — they reach for the gamble to avoid a sure loss — and that this flips with mere reframing of identical outcomes. No single expected-utility function reverses like that. The professionals were not pricing risk; they were responding to the words *gain* and *loss*.

3. **The math told them the right number and then stopped.** Expected value computed \$250,000 correctly. Variance flagged the risk correctly. What neither could supply was the utility function — *how much a dollar of loss hurts relative to a dollar of gain* — and that is precisely the input a human must bring, and precisely the input the human in this experiment supplied *inconsistently*.

The lesson is the boundary itself. Compute the expected value; you must. Compute the variance; you must. Then recognize that the decision lives on the far side of a line the math will not cross — and that even trained professionals cross it badly when the framing shifts. The tool is necessary. You are still responsible for the choice.

---

## Where this generalizes

The random-variable-with-a-distribution is the most reused object in the MBA curriculum. **Chapter 8** turns the sample mean into a random variable and discovers its standard error is $\sigma/\sqrt{n}$ — a direct application of the variance algebra boxed above. **Chapter 9** defines the regression slope as $\operatorname{Cov}(x,y)/\operatorname{Var}(x)$, leaning on the same variance machinery. **Chapter 10** expands $\operatorname{Var}(w_1 R_1 + w_2 R_2)$ to show why diversification works — pure variance algebra plus a covariance term. **Chapter 11** supplies the calculus behind the normal curve's areas. **Chapter 13** picks up the conditional-probability seed and grows it into Bayes' rule and decision trees, finishing the "EV isn't the whole story" argument with formal expected utility. Probability is not one chapter's topic; it is the language the analytics half of the book is written in.

---

## Exercises

1. **(Compute.)** A startup's exit is worth \$0 with probability 0.6, \$5M with probability 0.3, and \$50M with probability 0.1. Find $E[X]$ and $\sigma_X$. A risk-neutral investor and a risk-averse founder are looking at the same numbers — explain in one sentence why they might disagree about whether to sell now for a sure \$4M.

2. **(Compute.)** A quality inspector pulls $n = 200$ units from a line with a true defect rate $p = 0.04$, each unit independent. Find the expected number of defects and its standard deviation. Within what range would you expect the defect count to fall about 95% of the time? State the assumption you used to get there.

3. **(Catch the error.)** A colleague writes: "Each of our three product lines has revenue with standard deviation \$2M, and the lines are independent, so total revenue has standard deviation \$6M." Find the mistake, give the correct standard deviation, and state the general rule in one sentence.

4. **(Build/derive.)** Starting from the definition $\operatorname{Var}(X) = E[(X-\mu)^2]$, derive the computational form $\operatorname{Var}(X) = E[X^2] - (E[X])^2$. Then, using $\operatorname{Var}(aX+b) = a^2\operatorname{Var}(X)$, show that converting a return measured as a fraction (e.g. 0.07) to a percentage (7) multiplies the standard deviation by 100 but the variance by 10,000. Explain why a shift $b$ drops out.

5. **(Reason about the boundary.)** Construct two gambles with *equal* expected value where a sensible manager would clearly prefer one. Identify which feature of the distribution drives the preference, and state in one sentence what the manager must supply that the expected-value calculation cannot.

---

## Sources

- Kolmogorov, A. N. (1933). *Grundbegriffe der Wahrscheinlichkeitsrechnung* (Foundations of the Theory of Probability). — The three probability axioms. [verify — primary German text not consulted directly; axioms are standard and uncontroversial.]
- Bernoulli, J. (1713, posthumous). *Ars Conjectandi*. — The binomial distribution and the law of large numbers. [verify]
- Bernoulli, D. (1738). "Specimen theoriae novae de mensura sortis," *Commentarii Academiae Scientiarum Imperialis Petropolitanae*. — The St. Petersburg paradox and the resolution by expected utility / diminishing marginal utility. [verify — substance settled; primary translation not consulted directly.]
- de Moivre, A. (1733/1738). *The Doctrine of Chances*. — The normal curve as the large-$n$ limit of the binomial. [verify]
- von Neumann, J., & Morgenstern, O. (1944). *Theory of Games and Economic Behavior*. Princeton University Press. — Expected-utility theory; the formal case that rational agents maximize expected utility, not expected monetary value. [verify]
- Kahneman, D., & Tversky, A. (1973). "On the Psychology of Prediction," *Psychological Review* 80(4), 237–251. — Base-rate neglect; the lawyer–engineer experiment.
- Kahneman, D., & Tversky, A. (1979). "Prospect Theory: An Analysis of Decision under Risk," *Econometrica* 47(2), 263–291. — The gain/loss framing reversal.
- delMas, R., Garfield, J., Ooms, A., & Chance, B. (2007). "Assessing Students' Conceptual Understanding After a First Course in Statistics," *Statistics Education Research Journal* 6(2). — Students compute correctly while holding incoherent ideas about variability. (Volume/issue confirmed; exact page range approximate.)
- *MBA Management*, Chapter 6 (Perception and Managerial Decision-Making). — The Kahneman gain/loss framing cold open, adapted as this chapter's opening.
- *MBA Economics*, Chapter 16 (Information, Risk, and Insurance). — The insurance/risk-transfer worked example.
- *MBA Finance*, Chapter 13 (Statistical Analysis in Finance). — The "single 22% year" distinction between an outcome and its expectation.
