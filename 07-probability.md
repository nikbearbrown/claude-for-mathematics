# Chapter 7 — Probability

## TL;DR

- Here is a question that looks like it's about luck but isn't: why does a casino always make money?
- The chapter moves through What probability actually is, The complement trick, The counting problem, When order matters: permutations, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

*The House Doesn't Cheat. It Does Math.*

Here is a question that looks like it's about luck but isn't: why does a casino always make money?

It doesn't always make money on any particular night. Some nights a player walks away with thousands. Some nights two players walk away with thousands. The casino has bad nights. But the casino never has bad years. And the reason isn't that the wheel is rigged or the cards are marked. The wheel is fair. The cards are honest. Every outcome is genuinely random. And the casino profits anyway — consistently, predictably, mathematically.

This chapter is about how that works. It's about the language mathematicians built for talking about uncertainty. Not uncertainty as a gesture — "well, who knows" — but uncertainty as a number, as a precisely measured thing you can reason with. Once you have that language, you'll see that the casino's profit isn't luck at all. It's a theorem.

---

## What probability actually is

A probability is a number between 0 and 1 assigned to an event. Zero means the event is impossible. One means it's certain. Everything else lives in between.

The event you're assigning a probability to is called an *event*, and it's always a subset of something called the *sample space* — the complete set of possible outcomes of an experiment. You met both concepts in Chapter 1: sample spaces are universal sets; events are subsets. The machinery is the same. What's new here is the fraction.

Roll a standard six-sided die. The sample space is $S = \{1, 2, 3, 4, 5, 6\}$. The event "roll an even number" is $E = \{2, 4, 6\}$. If the die is fair — if each face is equally likely — then the probability of that event is the ratio of the number of outcomes in the event to the number of outcomes in the sample space:

$$P(E) = \frac{n(E)}{n(S)} = \frac{3}{6} = \frac{1}{2}$$

This is *theoretical probability*, and it's the cleanest version of the idea. It requires two things: that you can list all the outcomes in the sample space, and that they're all equally likely. When both conditions hold, you count and divide.

When the outcomes aren't equally likely — a weighted die, a baseball batter against a particular pitcher — you use *empirical probability* instead: the observed frequency of the event across many trials. A batter who gets 122 hits in 531 at-bats has an empirical probability of $122/531 \approx 0.23$ of getting a hit on his next plate appearance. That estimate will improve as you accumulate more data. With a small sample, it's noisy; with a large sample, it settles.

And when you can't list outcomes and you have no past data — a new rocket design, an unprecedented medical treatment — you use *subjective probability*: an educated estimate from someone who knows the domain. Useful when necessary. The weakest of the three. State clearly which kind you're using, because they have different strengths and different failure modes.

| Type | How You Get It | When It Breaks Down — |
| --- | --- | --- |
| Theoretical (count equally-likely outcomes | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| Empirical (observe frequency over many trials | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| Subjective (expert estimate) | student sees the three methods as a ranked toolkit, not interchangeable options | A concrete checkpoint for applying the chapter concept. |

---

## The complement trick

For any event $E$, the complement $E'$ is everything that isn't $E$. Since every outcome is either in $E$ or it isn't:

$$P(E) + P(E') = 1$$

This rearranges to $P(E) = 1 - P(E')$, and it's more useful than it looks. Many problems are hard to attack directly but easy to attack from the opposite direction.

You flip a fair coin three times. What is the probability of getting at least one head?

Direct approach: list all outcomes with at least one head. HHH, HHT, HTH, HTT, THH, THT, TTH. Seven outcomes out of eight total. Answer: $7/8$.

Complement approach: the opposite of "at least one head" is "no heads at all" — the single outcome TTT. Its probability is $(1/2)^3 = 1/8$. So the probability of at least one head is $1 - 1/8 = 7/8$.

Same answer, but the complement approach required thinking about exactly one outcome instead of seven. When the event you want is complex and its complement is simple, the complement approach is almost always faster. In problems with large sample spaces — "at least one success in ten tries" — the complement approach is often the only practical route.

![The complement approach asks: what's the one thing I don't want?](images/07-probability-fig-01.png)
*Figure 7.1 — Comparison for the three-coin flip *

---

## The counting problem

Here's where things get interesting. The probability formula $P(E) = n(E)/n(S)$ is clean, but it assumes you can count $n(E)$ and $n(S)$. For small sample spaces that's easy. For large ones, listing every outcome isn't practical. You need a way to count without listing.

The fundamental rule is this: if you have $n$ ways to accomplish one task and $m$ ways to accomplish a second, independent task, then you have $n \times m$ ways to accomplish both in sequence.

A cupcake shop offers 3 cake flavors and 4 frosting flavors. The number of distinct cupcakes is $3 \times 4 = 12$. A license plate with 3 letters followed by 3 digits has $26^3 \times 10^3 = 17{,}576{,}000$ possible plates. The rule extends to any number of independent choices: multiply the counts.

The crucial word is *independent*. If your choices affect each other — if choosing something in step one changes what's available in step two — you have to account for that reduction. Draw a card from a deck: 52 possibilities. Draw a second card without replacing the first: 51 possibilities. The first choice reduced the sample space for the second. So the number of possible two-card draws in order is $52 \times 51 = 2{,}652$, not $52^2 = 2{,}704$.

### When order matters: permutations

Sometimes the sequence of your choices matters. Eight swimmers compete; you want to know how many ways the top three podium spots can be filled. First place has 8 candidates. Once first is decided, 7 remain for second. Once second is decided, 6 remain for third.

$$8 \times 7 \times 6 = 336$$

This is a *permutation* — an ordered arrangement. The pattern of descending multiplication comes up often enough that mathematicians gave it notation. Write $n!$ (read "$n$ factorial") for the product of all whole numbers from 1 down to 1:

$$8! = 8 \times 7 \times 6 \times 5 \times 4 \times 3 \times 2 \times 1 = 40{,}320$$

The number of permutations of $n$ objects taken $r$ at a time is:

$$P(n, r) = \frac{n!}{(n-r)!}$$

For the swimmers: $P(8, 3) = 8!/5! = 336$. The $5!$ in the denominator cancels all the terms below 6, leaving exactly the $8 \times 7 \times 6$ you calculated directly.

![Factorial cancellation diagram for P(8,3) ](images/07-probability-fig-02.png)
*Figure 7.2 — Factorial cancellation diagram for P(8,3) *

### When order doesn't matter: combinations

Deal a five-card poker hand. The order you receive the cards is irrelevant — what matters is which five cards you hold. A hand of A-K-Q-J-10 is the same hand whether it arrived in that order or in the order 10-Q-A-J-K. You want to count *selections*, not *arrangements*.

The relationship between permutations and combinations is this: every combination of $r$ objects can be arranged in $r!$ different orders. So the number of combinations is the number of permutations divided by the number of arrangements:

$$C(n, r) = \frac{P(n,r)}{r!} = \frac{n!}{r!(n-r)!}$$

For a five-card hand from 52 cards:

$$C(52, 5) = \frac{52!}{5! \times 47!} = \frac{52 \times 51 \times 50 \times 49 \times 48}{5 \times 4 \times 3 \times 2 \times 1} = \frac{311{,}875{,}200}{120} = 2{,}598{,}960$$

There are 2,598,960 possible poker hands. A royal flush (10-J-Q-K-A of the same suit) is possible in exactly 4 ways — one per suit. So:

$$P(\text{royal flush}) = \frac{4}{2{,}598{,}960} \approx 0.0000015$$

About one and a half in a million. You don't need to deal millions of hands to know this. You count and divide.

The question of whether to use permutations or combinations is always the same question: does the order of selection matter? Podium positions, sequences, passwords — order matters, use permutations. Committees, card hands, lottery numbers — order doesn't matter, use combinations. Use the wrong one and you'll be off by a factor of $r!$, which for even modest $r$ is enormous.

| Use Permutations (order matters)" with examples: podium placements | passwords | race finishing order |
| --- | --- | --- |
| two-column decision guide | left | A concrete checkpoint for applying the chapter concept. |

---

## Expected value: the number that explains the casino

Now we have the tools to get back to the opening question. Why does the casino always make money?

Set up the calculation for American roulette. The wheel has 38 slots: 18 red, 18 black, 2 green. You bet $1 on red. If red comes up, you win $1 (and keep your original dollar). If anything else comes up, you lose your $1.

What is the *average* outcome of this bet, if you played it thousands of times?

The answer is the *expected value* — the weighted average of all possible outcomes, where each outcome is weighted by its probability:

$$E(X) = \sum \text{(outcome value)} \times P(\text{outcome})$$

For this bet:

$$E(X) = (1) \times \frac{18}{38} + (-1) \times \frac{20}{38} = \frac{18 - 20}{38} = -\frac{2}{38} \approx -0.053$$

On average, you lose about 5.3 cents per dollar bet. On any single spin, you either win a dollar or lose a dollar — you never lose 5.3 cents. But play ten thousand spins and your net result will be very close to ten thousand times negative 5.3 cents, which is negative $530. This is what the Law of Large Numbers says: as the number of trials grows, the observed average converges to the expected value. Not by coincidence, not by tendency — by theorem.

Now consider the casino's side of this bet. For every dollar wagered, the casino expects to keep 5.3 cents. On a busy night, a single roulette table might handle $100,000 in total bets. Expected profit: $5,300 from one table in one night. A large casino has dozens of tables running every day of the year. The number gets large quickly, and it does so with mathematical certainty.

The casino is not beating players by being clever. It's not predicting outcomes. It's not exploiting psychology (well, it is, but that's not where the money comes from). The money comes from the structure of the payoff: the casino pays out $1 on a win but has a $20/38$ probability of winning instead of $18/38$. That asymmetry is tiny on any single bet — two extra slots on a 38-slot wheel. Repeated thousands of times, it's an iron guarantee.

![Line chart showing cumulative net winnings for a](images/07-probability-fig-03.png)
*Figure 7.3 — Line chart showing cumulative net winnings for a*

### What expected value is not

Expected value is the long-run average. It is not the most likely outcome. If you roll a fair die, the expected value is:

$$E(X) = 1 \times \frac{1}{6} + 2 \times \frac{1}{6} + 3 \times \frac{1}{6} + 4 \times \frac{1}{6} + 5 \times \frac{1}{6} + 6 \times \frac{1}{6} = 3.5$$

You will never roll a 3.5. The expected value is a statement about the average over many trials, not a prediction for any single trial.

![The expected value of a fair die is a number you can never actually roll. It's an average, not a prediction.](images/07-probability-fig-04.png)
*Figure 7.4 — Number line from 1 to 6 with each*

Expected value also doesn't guarantee anything about your personal short-run experience. A lottery ticket with an expected value of $0.50 on a $2 investment has a negative expected value of $1.50 per ticket. If you buy one ticket, you might win the jackpot. If you buy 10,000 tickets over twenty years, you will almost certainly lose close to $15,000 total. The guarantee works in the long run. How long the long run needs to be depends on the variance — how wildly outcomes jump around. High-variance games can look profitable for a long time before the expected value asserts itself.

This is the professional gambler's actual problem. Even if you find a game with a positive expected value — and they exist, in skilled poker, in sports betting with a genuine edge — you need enough capital to survive the losing streaks while the expected value slowly accumulates. Running out of money before the Law of Large Numbers has time to work is called ruin. It's why "expected value positive" is necessary but not sufficient for a winning strategy.

---

## The single calculation that would have saved her money

Return to the woman at the roulette table from the beginning of this chapter. She played for hours and lost $200. She was frustrated. She probably thought she was unlucky.

She wasn't unlucky. She was foreseeable.

Every bet she placed had an expected value of $-0.053$ per dollar. Every single one. It didn't matter whether the previous spin was red or black. It didn't matter whether she'd been on a winning streak or a losing streak. The expected value of the next bet was always the same number, $-0.053$, because the wheel has no memory. Each spin is independent.

This is the gambler's fallacy in reverse: players believe that after a string of reds, black is "due." It isn't. The wheel doesn't know what happened before. The probability of black on the next spin is always $18/38$, regardless of history. The expected value is always $-0.053$, regardless of history.

If she had done one calculation — $E(X) = -2/38 \approx -0.053$ — before placing her first bet, she would have known exactly what she was buying: entertainment at a cost of about 5.3 cents per dollar wagered. That's the honest price of roulette. Some people find it worth paying. That's a reasonable choice. What isn't reasonable is believing the math will eventually turn in your favor. It won't, because it already told you what it will do.

---

## Why this all fits together

The counting tools and the probability framework are the same machinery running at different scales.

Counting (the multiplication rule, permutations, combinations) lets you calculate $n(E)$ and $n(S)$ when the sample space is too large to list. Probability converts those counts into a ratio between 0 and 1. Expected value takes those probabilities and produces the number that governs long-run behavior.

The sequence is: count $\to$ calculate probability $\to$ calculate expected value $\to$ make a decision.

![Four-box flow diagram ](images/07-probability-fig-05.png)
*Figure 7.5 — Four-box flow diagram *

A casino uses all three. It counts the ways a bet can win or lose. It calculates the probabilities from those counts. It calculates the expected value from those probabilities. It sets the payouts so the expected value favors the house. Then it opens the doors and waits for the Law of Large Numbers to work.

Insurance companies do the same calculation with different labels. The probability of a house fire in a given year is about 0.4% for a typical American home. The insurance company calculates its expected payout per policy and charges a premium above that — the margin is their profit. Individual customers may collect more than they pay in (if their house burns) or less (if it doesn't). The insurance company, across millions of policies, collects its expected profit with near certainty.

Weather forecasters, clinical trial designers, poker players, epidemiologists modeling disease spread — all are using the same machinery in different domains. The language is the same. The insight is the same. Uncertainty has a structure, and once you measure it, you can predict the average behavior of systems that are individually unpredictable.

---

## The one thing that makes it work

The Law of Large Numbers is the theorem underneath all of this. It says: as the number of trials of a random experiment grows, the observed average of the outcomes converges to the expected value.

It doesn't say *when* it converges. With low variance (each outcome close to the expected value), convergence is fast. With high variance (wild swings between outcomes), convergence is slow. The law is silent on how many trials "enough" means. That depends on the problem.

But it says convergence happens. Always. That's what makes expected value useful: not that any single trial comes out right, but that the aggregate of many trials comes out as predicted. The individual spin is random. The year's profit is not.

And that asymmetry — random in the short run, predictable in the long run — is the deepest fact in this chapter. It's why probability is worth learning. Not to predict what will happen next, but to know exactly what will happen on average. Which, in the long run, is the only thing that matters.

---

## Exercises

### Warm-up

**Exercise 7.1** A standard die is rolled once. (a) Write out the sample space. (b) Find $P(\text{roll greater than 4})$. (c) Find $P(\text{roll an odd number})$ using the complement rule — first find $P(\text{roll an even number})$, then subtract from 1. Verify your answer by direct count.

**Exercise 7.2** A state license plate uses 2 letters followed by 3 digits. (a) How many plates are possible? (b) How many are possible if the letter O and digit 0 are excluded to avoid confusion?

**Exercise 7.3** A committee of 4 people is chosen from a group of 9. (a) How many ways can this be done? (b) If the 9 people include 5 women and 4 men, how many committees contain exactly 2 women?

### Application

**Exercise 7.4** You flip a fair coin 4 times. (a) What is the probability of getting all tails? (b) Use the complement rule to find the probability of getting at least one head. (c) List all outcomes to verify your answer from (b).

**Exercise 7.5** A baseball player has 87 hits in 340 at-bats this season. (a) What is his empirical probability of getting a hit on his next at-bat? (b) Is this theoretical, empirical, or subjective probability? Explain in one sentence. (c) Why might this estimate be unreliable for predicting his performance against a specific pitcher he has never faced?

**Exercise 7.6** You are dealt a single card from a standard shuffled deck. (a) What is $P(\text{ace})$? (b) What is $P(\text{red card})$? (c) What is $P(\text{not a heart})$? Use the complement rule for (c).

### Synthesis

**Exercise 7.7** A carnival game costs \$2 to play. You draw one card from a standard deck. If it's an ace, you win \$10. If it's a face card (J, Q, K), you win \$4. Otherwise you win nothing. (a) Set up the expected value calculation with all outcomes and their probabilities. (b) Calculate $E(X)$, where $X$ is your net gain (remember to subtract the \$2 entry cost from any winnings). (c) Is this game worth playing? What would the prize for an ace need to be to make $E(X) = 0$?

**Exercise 7.8** Eight runners compete in a race. (a) In how many ways can the gold, silver, and bronze medals be awarded? (b) In how many ways can a 3-person relay team be selected from the 8, if the order of runners in the relay matters? (c) If the relay team is selected randomly, what is the probability that the three fastest runners are chosen? (Does order matter here? Explain your reasoning before computing.)

**Exercise 7.9** A bag contains 6 red, 4 blue, and 2 green balls. You draw 2 balls without replacement. (a) What is the total number of ways to draw 2 balls from 12? (b) What is the probability that both balls are red? (c) What is the probability that at least one ball is red? Use the complement.

### Challenge

**Exercise 7.10** A casino offers the following game: Roll two fair dice. If the sum is 7, you win \$4. If the sum is 2 or 12 (the rarest outcomes), you win \$15. Otherwise you lose \$1. (a) Find the probability of each outcome. (b) Calculate the expected value per play. (c) Should the casino offer this game? Justify your answer in terms of expected value — and explain what "should" means here: favorable to the casino, the player, or both?

**Exercise 7.11** The gambler's fallacy is the belief that after a string of losses, a win is "due." Using what you know about independence and expected value, write a two-paragraph explanation of why this belief is wrong. In the first paragraph, explain why the wheel has no memory. In the second paragraph, explain what *does* happen in the long run — and why that is not the same thing as a single outcome being "due."

---

## LLM Exercise — Chapter 7: Probability (Audit a Real-World System Project)

**Project:** Audit one real-world system through 13 chapters of mathematics.
**What you're building this chapter:** a probability analysis of the system's outcomes — the chances of various user / customer / patient experiences and the expected values driving the system's design.
**Tool:** **Claude Project** (same system spec as Ch 1).

**The Prompt:**

```
Chapter 7 of my system-audit project. Chapter 7 covered:
sample spaces and events; theoretical, empirical, and
subjective probability; the complement trick (1 − P(not E));
counting principles (combinations and permutations); expected
value (∑ value × probability); independence and the gambler's
fallacy.

Apply to my system. Most systems implicitly run probability
calculations on their users.

1. **Identify three probabilistic events in the system.**
   Examples:
   - Transit: probability of catching the bus you wanted;
     probability of a delay over 5 min; probability of
     two consecutive trains being on time.
   - Streaming: probability that a given recommendation is
     watched to completion; probability of a renewal at
     end of trial; probability of a subscriber upgrading
     to ad-free.
   - Sports: probability of a team winning a given game;
     probability of a bracket "Cinderella" run; probability
     of a perfect bracket.
   - Hospital: probability of a triage misclassification;
     probability of a 4-hour ED stay; probability of
     readmission within 30 days.

2. **Compute one probability from data.** Pick one event.
   Find the actual frequency from public data (an OnTime
   percentage, a churn rate, a win rate). Translate to
   probability. State whether this is theoretical (modeled),
   empirical (observed), or subjective (estimated).

3. **Apply the complement trick.** For one event in the
   system, compute P(event happens at least once in N
   tries) using P(at least one) = 1 − P(none). Example:
   if there's a 5% chance the bus is more than 10 min
   late on any given commute, what's the probability
   you'll experience at least one such late bus over a
   month of commuting (20 trips)?

4. **Compute one expected value from the system.** Pick
   one decision the system implicitly forces. Compute the
   EV of the user's choice. Examples:
   - Transit: EV of paying per-ride vs. monthly pass given
     ride-count distribution.
   - Streaming: EV of an annual vs. monthly subscription
     given the probability you cancel mid-year.
   - Hospital: EV of an elective procedure given outcome
     probabilities.
   - Sports: EV of buying a ticket on the resale market
     for a specific game.
   Show the table: outcome, value, probability, product.

5. **Find one place the system runs a "casino" on its
   users.** Most systems have at least one feature with
   negative EV for the user that nevertheless gets
   chosen — late fees, surge pricing, in-app purchases,
   loot boxes, paid-search ads. Compute the EV. Identify
   the cognitive bias (loss aversion, overconfidence,
   gambler's fallacy) being exploited.

End with: a one-page "probability audit" of the system.
Three events. One empirical probability. One complement-
trick calculation. One EV calculation. One identified
"casino" feature with the EV computed.
```

**What this produces:** A probability audit revealing where the system's odds are stacked, what its expected outcomes actually are, and where it's running a casino on users. Most systems have at least one such feature — naming it is the chapter's point.

**Connection to previous chapters:** Builds on Ch 6's financial machinery (most "casino" features in real systems are financial) and Ch 5's thresholds (probability often determines which side of a threshold a user lands on).

**Preview of next chapter:** Chapter 8 — apply statistics to the system's published data. Distributions, measures of center, variability, polls, samples. What does the system's averaged data hide?

---

##  AI Wayback Machine
**Florence Nightingale David** was 20th-century British statistician — Karl Pearson's protégée — whose work on combinatorial probability remains in standard textbooks.

![Florence Nightingale David](../images/florence-nightingale-david-287.png)

*Puppet Art by [Nik Bear Brown](https://www.nikbearbrown.com/).*

**Run this:**

```
Who is Florence Nightingale David, and how does their work connect to probability we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Florence Nightingale David"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Florence Nightingale David's ideas to a specific concrete problem in this chapter.
- Add a constraint: "Answer including criticisms or limits of Florence Nightingale David's framework."

What changes? What gets better? What gets worse?
