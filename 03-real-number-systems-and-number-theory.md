# Chapter 3 — Real Numbers and Number Theory


## TL;DR

- The lock that has no key and the fraction that has no end.
- The chapter moves through What Divides What, The Prime Pieces, The Fundamental Theorem of Arithmetic, How to Factor, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

*The lock that has no key and the fraction that has no end.*

---

There is a number sitting on a server right now that no one on Earth knows how to factor. It has several hundred digits. It is the product of exactly two primes. The bank that generated it published this number openly — told everyone in the world exactly what it is — because they are completely confident that knowing the number does not help you find the two primes it came from. Not in your lifetime. Not in anyone's lifetime with current technology.

That is the situation. A multiplication problem that takes a fraction of a second to run forward cannot be reversed in 300 trillion years.

This is not a quirk or a clever trick layered on top of arithmetic. It is a consequence of the deepest structural fact about the integers: every number above 1 is either prime or breaks uniquely into primes, and while the breaking-down is guaranteed to exist, no one has found a fast way to find it. The guarantee of existence and the computational difficulty of discovery live in the same theorem. That tension is what cryptographers are renting when they build encryption.

![Two-column asymmetry diagram ](images/03-real-number-systems-and-number-theory-fig-01.png)
*Figure 3.1 — Two-column asymmetry diagram *

This chapter teaches you to see inside numbers — how they factor, how they combine with signs, how they subdivide into fractions. Not as rules to memorize but as things that are true for reasons you can understand.

---

## What Divides What

Start here: when does one number divide another evenly?

A natural number $m$ **divides** $n$ if you can write $n = m \times k$ for some integer $k$ with no remainder. Twelve divides 60 because $60 = 12 \times 5$. Twelve does not divide 58, because $58 = 12 \times 4 + 10$ — there is a remainder of 10 left over.

That's the whole idea. Everything else in this section is built on it.

To avoid long division for common cases, mathematicians developed divisibility tests — fast shortcuts that check divisibility without performing the division.

| Divisor | Test |
|---------|------|
| 2 | Last digit is even |
| 3 | Sum of all digits is divisible by 3 |
| 5 | Last digit is 0 or 5 |
| 10 | Last digit is 0 |

| Item | Meaning |
| --- | --- |
| Expanded divisibility rules reference | add columns for 4 (last two digits divisible by 4 |
| 6 (divisible by both 2 and 3 | A concrete checkpoint for applying the chapter concept. |
| 9 (digit sum divisible by 9 | A concrete checkpoint for applying the chapter concept. |
| with a "why it works" column giving a one-sentence plain-language explanation of each rule. Students need this as a reference card and the "why" column prevents rote memorization. | A specific, evidence-linked version that readers can verify. |

Try it on 318. Is it divisible by 3? Add the digits: $3 + 1 + 8 = 12$. Is 12 divisible by 3? Yes: $12 = 3 \times 4$. So 318 is divisible by 3. Check: $318 = 3 \times 106$. The test worked.

Why does the digit-sum test work? Because $10 \equiv 1 \pmod{3}$ — ten leaves a remainder of 1 when divided by 3 — so any power of 10 also leaves remainder 1. That means the value of a digit in any position is equivalent, modulo 3, to just the digit itself. The sum of digits captures all the information about divisibility by 3. This is a glimpse of modular arithmetic, which comes later. For now, the test is enough.

---

## The Prime Pieces

A **prime** is a natural number greater than 1 whose only divisors are 1 and itself. The primes begin: 2, 3, 5, 7, 11, 13, 17, 19, 23, 29, ...

A **composite** is a natural number greater than 1 that has at least one other divisor. The number 12 is composite: $12 = 2 \times 6 = 3 \times 4 = 2 \times 2 \times 3$.

The number 1 is neither. It has only one divisor — itself — and is excluded from both categories. This exclusion is not arbitrary. It is necessary for the theorem about to follow.

### The Fundamental Theorem of Arithmetic

Every integer greater than 1 can be expressed as a product of primes in **exactly one way**, up to the order of the factors.

That word *exactly* is doing enormous work. Let's feel the weight of it.

Take 18. You can factor it as $2 \times 9 = 2 \times 3 \times 3$. Or start differently: $3 \times 6 = 3 \times 2 \times 3$. Different paths, same destination. Rearrange the factors however you like — you always get $2 \times 3^2$, and nothing else. No other combination of primes multiplies to 18.

If 1 were prime, this would break. $18 = 2 \times 3^2 = 1 \times 2 \times 3^2 = 1 \times 1 \times 2 \times 3^2$ — suddenly there would be infinitely many factorizations, and uniqueness would be gone. So 1 is excluded. The theorem is preserved.

### How to Factor

To find the prime factorization of any composite number: repeatedly divide by the smallest prime that goes in evenly, until what remains is 1.

Example: factor 140.

- 140 is even, so divide by 2: $140 = 2 \times 70$
- 70 is even, so divide by 2 again: $70 = 2 \times 35$, so far $2^2 \times 35$
- 35 ends in 5, divisible by 5: $35 = 5 \times 7$
- 7 is prime. Stop.

Result: $140 = 2^2 \times 5 \times 7$

Check: $4 \times 5 \times 7 = 20 \times 7 = 140$. ✓

A factor tree shows the same calculation visually: write 140 at the top, branch into two factors, branch again if either factor is composite, stop when all leaves are prime. Read the leaves: $2, 2, 5, 7$.

```
        140
       /   \
      2     70
           /  \
          2    35
              /  \
             5    7
```

![Clean rendered factor tree for 140 with color](images/03-real-number-systems-and-number-theory-fig-02.png)
*Figure 3.2 — Clean rendered factor tree for 140 with color*

The leaves are always the same, regardless of which branches you chose.

### Checking Primality

To test whether a number $n$ is prime, you only need to check prime divisors up to $\sqrt{n}$. Here's why: if $n$ has a factor larger than $\sqrt{n}$, its paired factor must be smaller than $\sqrt{n}$. So if no prime up to $\sqrt{n}$ divides $n$, no factor of any kind exists, and $n$ is prime.

Is 247 prime? $\sqrt{247} \approx 15.7$, so check primes up to 15: {2, 3, 5, 7, 11, 13}.

- 247 is odd → not divisible by 2
- Digit sum $2 + 4 + 7 = 13$ → not divisible by 3
- Doesn't end in 0 or 5 → not divisible by 5
- $247 \div 7 = 35$ remainder 2 → not divisible by 7
- $247 \div 11 = 22$ remainder 5 → not divisible by 11
- $247 \div 13 = 19$ exactly → divisible

So $247 = 13 \times 19$. Both 13 and 19 are prime. 247 is composite.

One misconception worth clearing away: prime does not mean odd. The number 2 is the only even prime. All other primes are odd because any even number greater than 2 is divisible by 2. But odd does not imply prime — 9, 15, 21 are all odd and composite.

### GCD and LCM: Two Tools from the Same Machine

The **greatest common divisor** (GCD) of two integers is the largest positive integer that divides both. The divisors of 12 are {1, 2, 3, 4, 6, 12}. The divisors of 18 are {1, 2, 3, 6, 9, 18}. The common divisors are {1, 2, 3, 6}. The greatest is 6. So GCD(12, 18) = 6.

The **least common multiple** (LCM) is the smallest positive integer divisible by both. Multiples of 12: 12, 24, 36, 48, ... Multiples of 18: 18, 36, 54, ... First one they share: 36. So LCM(12, 18) = 36.

Using prime factorization makes both calculations mechanical.

$12 = 2^2 \times 3$, $\quad 18 = 2 \times 3^2$

For GCD: take the **minimum** exponent of each prime shared by both.

$$\text{GCD}(12, 18) = 2^{\min(2,1)} \times 3^{\min(1,2)} = 2^1 \times 3^1 = 6$$

For LCM: take the **maximum** exponent of each prime appearing in either.

$$\text{LCM}(12, 18) = 2^{\max(2,1)} \times 3^{\max(1,2)} = 2^2 \times 3^2 = 36$$

There is a compact relationship between the two: $\text{GCD}(a,b) \times \text{LCM}(a,b) = a \times b$. Check: $6 \times 36 = 216 = 12 \times 18$. ✓

![Venn diagram for GCD and LCM using prime](images/03-real-number-systems-and-number-theory-fig-03.png)
*Figure 3.3 — Venn diagram for GCD and LCM using prime*

GCD solves packing and division problems: a camp director with 48 sleeping bags and 64 tent stakes who wants identical kits with no leftovers needs GCD(48, 64) kits. $48 = 2^4 \times 3$, $64 = 2^6$. GCD $= 2^4 = 16$. Sixteen kits, 3 sleeping bags and 4 stakes each.

LCM solves alignment and scheduling problems: Bus A runs every 12 minutes, Bus B every 18 minutes. They just departed together. LCM(12, 18) = 36 minutes until they align again.

---

## Integers: Direction as Well as Magnitude

The natural numbers let you count. They don't let you say "below zero" or "owed" or "south of." For those, you need the integers: the full set $\{\ldots, -3, -2, -1, 0, 1, 2, 3, \ldots\}$.

An integer has two properties: a **magnitude** (how big) and a **direction** (positive, negative, or zero). On a number line, zero sits at the center. Positive numbers extend right. Negative numbers extend left. The **absolute value** of a number is its distance from zero, always non-negative: $|{-5}| = 5$, $|5| = 5$.

### Arithmetic on the Number Line

Addition moves you along the line. Start at the first number. Move right for a positive addend; move left for a negative addend.

$3 + 5 = 8$ — start at 3, move right 5, land at 8.

$3 + (-5) = -2$ — start at 3, move left 5, land at −2.

$(-3) + (-5) = -8$ — start at −3, move left 5, land at −8.

![Horizontal number line from −10 to +10, showing](images/03-real-number-systems-and-number-theory-fig-04.png)
*Figure 3.4 — Horizontal number line from −10 to +10, showing*

Subtraction reverses: $a - b$ means start at $a$ and move *against* the direction of $b$.

$7 - 3 = 4$. $3 - 7 = -4$.

Subtracting a negative is the same as adding a positive: $7 - (-3) = 7 + 3 = 10$. Two reversals bring you back to the original direction.

Multiplication has a sign rule: **same signs produce positive; opposite signs produce negative.**

$(3) \times (4) = 12$
$(-3) \times (-4) = 12$
$(3) \times (-4) = -12$

Why do two negatives make a positive? Formally, it follows from the requirement that arithmetic laws (distributive, associative) remain consistent when extended to negatives. Intuitively: multiplying by a negative reverses direction. Reversing a reversal returns to the original orientation.

Division obeys the same sign rule. $(-12) \div (-3) = 4$. $(12) \div (-3) = -4$.

### What Negative Numbers Unlock

Without negative numbers, the equation $3 + x = 2$ has no solution in the natural numbers. With integers, $x = -1$. Every linear equation $ax + b = c$ now has a solution, as long as $a \neq 0$. That generality is the price of admitting negative numbers, and it is a price worth paying.

---

## Rational Numbers: Exact Ratios

A **rational number** is any number expressible as $\frac{p}{q}$ where $p$ and $q$ are integers and $q \neq 0$. The word comes from Latin *ratio* — a proportion, a relation between two quantities.

Every integer is rational. Write 5 as $\frac{5}{1}$. Rational numbers extend beyond integers to all fractions, to terminating decimals ($0.5 = \frac{1}{2}$), and to repeating decimals ($0.333\ldots = \frac{1}{3}$).

### Equivalent Fractions and Lowest Terms

Two fractions are equal when they name the same portion of the whole. $\frac{2}{4}$ and $\frac{1}{2}$ are equal: both say "half." A fraction is in **lowest terms** when the numerator and denominator share no common factor except 1 — that is, when their GCD is 1.

To reduce: divide both numerator and denominator by their GCD.

$\frac{12}{18}$: GCD(12, 18) = 6. Divide: $\frac{12 \div 6}{18 \div 6} = \frac{2}{3}$. GCD(2, 3) = 1. Done.

### Adding and Subtracting

To add or subtract fractions, you need a common denominator. The LCM of the two denominators is the one to use — it keeps the numbers as small as possible.

$$\frac{1}{4} + \frac{1}{6}$$

LCM(4, 6): $4 = 2^2$, $6 = 2 \times 3$. LCM $= 2^2 \times 3 = 12$.

Convert:

$$\frac{1}{4} = \frac{3}{12}, \qquad \frac{1}{6} = \frac{2}{12}$$

Add:

$$\frac{3}{12} + \frac{2}{12} = \frac{5}{12}$$

Why do you need a common denominator? Because $\frac{1}{4}$ and $\frac{1}{6}$ are measuring in different units — fourths and sixths. You cannot add them directly any more than you can add 3 feet and 2 meters without converting. The LCM converts both to the same unit.

![Area-model diagram for fraction addition ](images/03-real-number-systems-and-number-theory-fig-05.png)
*Figure 3.5 — Area-model diagram for fraction addition *

### Multiplying and Dividing

Multiplication requires no common denominator. Multiply numerators, multiply denominators.

$$\frac{a}{b} \times \frac{c}{d} = \frac{a \times c}{b \times d}$$

$$\frac{2}{3} \times \frac{3}{4} = \frac{6}{12} = \frac{1}{2}$$

Division uses the reciprocal. To divide by $\frac{c}{d}$, multiply by $\frac{d}{c}$.

$$\frac{a}{b} \div \frac{c}{d} = \frac{a}{b} \times \frac{d}{c} = \frac{ad}{bc}$$

$$\frac{2}{3} \div \frac{1}{4} = \frac{2}{3} \times \frac{4}{1} = \frac{8}{3}$$

Why the reciprocal? Division asks: "how many times does $\frac{c}{d}$ fit into $\frac{a}{b}$?" Flipping and multiplying is what delivers that count exactly.

### Percent as Rational Number

A percent is a specific rational number. $n\%$ means $\frac{n}{100}$. To find 30% of 200:

$$\frac{30}{100} \times 200 = 0.30 \times 200 = 60$$

Percentages let you compare proportions across groups with different totals. If 600 of 1,000 voters in one city approve a measure, and 900 of 2,000 in another, you cannot compare those raw numbers directly. Convert: 60% vs. 45%. Now you can.

### A Worked Example: Scaling a Recipe

A cookie recipe calls for $\frac{2}{3}$ cup of sugar and $\frac{3}{4}$ cup of flour. You want to make 1.5 times the recipe.

Rewrite 1.5 as a fraction: $\frac{3}{2}$.

Sugar: $\frac{3}{2} \times \frac{2}{3} = \frac{6}{6} = 1$ cup.

Flour: $\frac{3}{2} \times \frac{3}{4} = \frac{9}{8} = 1\frac{1}{8}$ cups.

A baker does this by feel after years of practice. You now have the machinery to do it in any unfamiliar case.

### What Rational Numbers Cannot Reach

Rational numbers handle any ratio of integers. But not every length or measurement is such a ratio. The diagonal of a unit square has length $\sqrt{2}$. Can $\sqrt{2}$ be written as $\frac{p}{q}$ for integers $p$ and $q$?

Assume it can: $\sqrt{2} = \frac{p}{q}$ in lowest terms. Then $2 = \frac{p^2}{q^2}$, so $p^2 = 2q^2$. This means $p^2$ is even, which means $p$ is even (since the square of an odd number is odd). Write $p = 2k$. Then $4k^2 = 2q^2$, so $q^2 = 2k^2$. So $q$ is also even. But then both $p$ and $q$ are even — which contradicts the assumption that $\frac{p}{q}$ was in lowest terms.

The assumption fails. $\sqrt{2}$ is not rational. It is **irrational** — real, but not expressible as any fraction. The rational numbers are dense on the number line (between any two rationals there is always another rational), but they have gaps, and irrational numbers fill them. Together, rationals and irrationals form the **real numbers**.

![Number line zoomed in on the interval [1,](images/03-real-number-systems-and-number-theory-fig-06.png)
*Figure 3.6 — Number line zoomed in on the interval [1,*

---

## The Structure Underneath Everything

Now return to the cryptographer.

She multiplies two primes with hundreds of digits each. The product is a specific, unique integer. The Fundamental Theorem guarantees that no other pair of primes produces this same number. That uniqueness is the lock.

The bank's server then handles transactions. Balances are computed using integer arithmetic — additions, subtractions, sign-correct multiplications. Interest compounds monthly: a 3.6% annual rate is $\frac{3.6}{100} = \frac{9}{250}$ annually, $\frac{9}{3000} = \frac{3}{1000}$ monthly. These are rational arithmetic operations on exact fractions.

The GCD shows up in reporting: when combining data from systems with different measurement intervals, the analysts find the smallest common interval by computing LCM. When dividing resources fairly, they find GCD to eliminate waste.

Prime structure secures the whole system. Integer arithmetic runs it. Rational arithmetic measures the transactions. All three rest on the same foundation: the integers, extended by the rules of divisibility and the fact that every number factors uniquely.

![Three-layer stack diagram ](images/03-real-number-systems-and-number-theory-fig-07.png)
*Figure 3.7 — Three-layer stack diagram *

The thing to hold onto — the one idea from this chapter that matters most:

**Every composite number is built from prime pieces, and those pieces are unique.** That uniqueness is not an accident or a convenient convention. It is a structural fact about the integers, and it is why so much of mathematics — and so much of modern security — is possible.

---

## Still Open

The distribution of primes — why they become rarer as numbers grow, and whether any formula predicts exactly where the next prime falls — remains one of the deepest unsolved problems in mathematics. The Riemann Hypothesis, posed in 1859, addresses this distribution. It carries a $1,000,000 prize for its resolution. It has not been resolved.

If you find yourself drawn to it, you are in good company. Gauss, Euler, Riemann, Hardy, and thousands of working mathematicians since have looked at the prime distribution and felt the pull. The question is not exotic or esoteric. It is the natural next question after everything this chapter showed you.

---

---

## LLM Exercise — Chapter 3: Real Numbers and Number Theory (Audit a Real-World System Project)

**Project:** Audit one real-world system through 13 chapters of mathematics.
**What you're building this chapter:** the system's hidden divisibility structure — scheduling cycles, billing periods, batch sizes, packet sizes — analyzed via prime factorization, GCD, and LCM.
**Tool:** **Claude Project** (same system spec as Ch 1).

**The Prompt:**

```
Chapter 3 of my system-audit project. Chapter 3 covered: real
numbers and their subsets (naturals, integers, rationals,
irrationals); prime factorization and the Fundamental Theorem
of Arithmetic; greatest common divisor (GCD); least common
multiple (LCM); the relationship GCD(a,b) × LCM(a,b) = a × b;
the proof that √2 is irrational.

Apply to my system. Most systems have hidden divisibility
structure. Surface it.

1. **Find the cycles.** Identify three numerical cycles in
   your system. Examples:
   - Transit: train arrival intervals (every 6 min on the
     Red Line; every 10 min on the bus).
   - Streaming: billing cycles (every 30 days), promo
     cycles (90 days), content-refresh cycles.
   - Sports: game frequency, season length, playoff format.
   - Restaurant: shift lengths, ingredient delivery cycles,
     menu rotation.

2. **Apply LCM to find synchronization points.** For two of
   the cycles you identified, compute the LCM. The LCM is
   when both cycles align. Example: if Red Line trains run
   every 6 min and Green Line trains run every 10 min,
   they both arrive simultaneously every LCM(6,10) = 30 min.

3. **Apply GCD to find shared structure.** For two related
   numerical features (e.g., two prices, two batch sizes,
   two seat counts), compute the GCD. The GCD is the
   largest "natural unit" that divides both evenly. Example:
   if a streaming service offers 480p, 720p, 1080p, and 4K
   tiers, GCD analysis on the bandwidth requirements may
   reveal an underlying baseline rate.

4. **Find a fraction in the system that should be reduced.**
   Pick one ratio in the system (price-per-unit, success
   rate, conversion rate, fare-per-mile). Express it as a
   fraction. Use prime factorization to reduce it to lowest
   terms. Discuss whether the unreduced form was hiding
   something — sometimes systems advertise unreduced ratios
   ("12/15 customers approve!") that look more impressive
   than the reduced form (4/5).

5. **Find an irrational in the system (if there is one).**
   Most real systems involve irrational numbers somewhere —
   geometric calculations involving √2 (diagonal distances),
   π (round structures), or e (compound growth). Identify
   one irrational appearing in the system, prove (or sketch)
   its irrationality, and note how the system handles it
   (rounded to how many decimal places? truncated?).

End with: a one-page "divisibility audit" of the system.
Three cycles. One LCM synchronization point. One GCD shared
structure. One reduced fraction. One irrational appearance
with the precision the system uses.
```

**What this produces:** A divisibility audit revealing the system's hidden numerical structure. Cycles often determine when the system experiences peak load, when promotions overlap, when costs synchronize.

**Connection to previous chapters:** Builds on Ch 1's set-theoretic structure (the cycles you identify often correspond to the categories from Ch 1). Builds on Ch 2's logical rules (cycle-related rules often appear in the system's logic).

**Preview of next chapter:** Chapter 4 — apply place value and number representation to the system's encoding choices. Account numbers, IDs, route codes, product SKUs — every system encodes information, and the encoding choices reveal design decisions.

---

##  AI Wayback Machine
**Srinivasa Ramanujan** was self-taught Indian mathematician who produced thousands of identities and theorems in number theory before dying at 32 — many still being unpacked a century later.

**Run this:**

```
Who is Srinivasa Ramanujan, and how does their work connect to number theory we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Srinivasa Ramanujan"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Srinivasa Ramanujan's ideas to a specific concrete problem in this chapter.
- Add a constraint: "Answer including criticisms or limits of Srinivasa Ramanujan's framework."

What changes? What gets better? What gets worse?
