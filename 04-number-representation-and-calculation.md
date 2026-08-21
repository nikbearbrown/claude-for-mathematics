# Chapter 4 — Number Representation and Calculation

## TL;DR

- The Notation Is the Engine, Not Just the Label.
- The chapter moves through The first thing to get clear: numbers versus numerals, Tally marks: the floor, not the ceiling, The idea that changed everything, Zero: the hardest invention in mathematics, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

*The Notation Is the Engine, Not Just the Label.*

Here is a fact about the year 1492 that has nothing to do with Columbus: you could record it in four symbols. 1, 4, 9, 2. Four symbols that any schoolchild could write in two seconds. That same year, in Roman numerals, is MCDXCII — longer, and harder to multiply by anything. And if you tried to record 1492 using the oldest human method, tally marks, you would need 1,492 of them. An entire afternoon of scratching.

The quantity didn't change. The year is still the year. What changed is the notation — the choice of how to write the number down. And that choice, it turns out, is one of the most consequential engineering decisions in human history.

---

## The first thing to get clear: numbers versus numerals

A **number** is an abstract idea. The concept of five-ness. The quantity of fingers on one hand.

A **numeral** is a written symbol for that idea. The digit 5. The Roman V. The tally marks ⬜⬜⬜⬜⬜. The word *five*. They all point at the same concept from different angles.

This sounds like the kind of distinction only a philosopher would care about. It isn't. Everything that follows depends on it. The quantity never changes. What changes — what humans have been tinkering with for five thousand years — is the system of symbols we use to represent it. And some systems are dramatically better than others, for reasons we can pin down precisely.

| The Number" (abstract quantity) | right column: "The Numeral" (written symbol) — rows for five | twelve | and one thousand | each showing the same quantity rendered in Hindu-Arabic digits |
| --- | --- | --- | --- | --- |
| two-column reference | left | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |

---

## Tally marks: the floor, not the ceiling

The oldest recording system we know of is simple: one mark per object. Scratch a line for every sheep, every day, every jug of wine. Group them in fives to make counting easier. This is an *additive* system — you add up the marks and get the quantity.

Tally marks work. They require no training to understand. Any human who can count can read them. But they scale terribly. The year 1492 requires 1,492 marks. A Roman census recorded in tally marks would require a warehouse of papyrus. The system hits its ceiling fast.

The Romans saw the problem and engineered around it. Instead of one symbol, use several, each standing for a different quantity: I for one, V for five, X for ten, L for fifty, C for one hundred, D for five hundred, M for one thousand. Then add them up. MCMLII means one thousand, plus (one thousand minus one hundred), plus fifty, plus two. The number is the sum of the symbol-values.

This is still an additive system. You're still just adding. But now you need far fewer symbols — the whole Roman system uses only seven. MCDXCII (1492) is six symbols instead of 1,492 marks. Progress.

The Romans also invented a subtraction shorthand: writing a smaller symbol before a larger one means "subtract." IV is five minus one, so four. IX is ten minus one, so nine. This made the numerals more compact, but it also made them harder to compute with.

Try this: multiply XXVII by XLII. With Roman numerals. Go ahead. It's not impossible, but it's closer to solving a puzzle than doing arithmetic. You have to translate, compute, retranslate. Roman accountants could do it, but only after considerable practice. The system doesn't help the arithmetic. It just records the result.

![Timeline of numeration systems ](images/04-number-representation-and-calculation-fig-01.png)
*Figure 4.1 — Timeline of numeration systems *

---

## The idea that changed everything

Somewhere around the fifth century CE in India, a set of mathematicians worked out a different approach. Instead of having separate symbols for different magnitudes, use the *position* of a digit to carry that information.

In the numeral 27, the 2 is in the tens place, so it means two tens — twenty. The 7 is in the ones place, so it means seven ones — seven. The number is twenty plus seven. Now here's the radical part: you can reuse the same symbol in a different position and it means something completely different. In 222, the leftmost 2 means two hundreds. The middle 2 means two tens. The rightmost 2 means two ones. Same symbol. Three different values. Because of position.

This is **place value**: the position of a digit in a numeral determines what it represents. Each position is a power of the base. In base 10, reading right to left, the positions represent $10^0 = 1$, $10^1 = 10$, $10^2 = 100$, $10^3 = 1{,}000$, and so on.

The numeral 738 means:

$$7 \times 10^2 + 3 \times 10^1 + 8 \times 10^0 = 700 + 30 + 8$$

That's the *expanded form* — you're unpacking what each position is contributing. The full numeral is just a shorthand for that sum. This is so automatic to you that it's invisible, which is exactly what good engineering looks like.

![Diagram of the numeral 738 ](images/04-number-representation-and-calculation-fig-02.png)
*Figure 4.2 — Diagram of the numeral 738 *

But place value needs something tally marks never needed: a symbol for zero. Consider the number one thousand and nine. In that number there are no hundreds and no tens. How do you write it? If you just write the digits you have — 1, 9 — you get 19, which means something completely different. You need a placeholder that says: *this position is empty*. You need 1,009.

Zero is that placeholder. And inventing it was not easy.

---

## Zero: the hardest invention in mathematics

For most of human history, nobody used zero as a number. This isn't stupidity — it's philosophy. Aristotle didn't believe void could exist. You can't have zero sheep in a field; you just have an empty field. The concept of *nothing as a thing* required a conceptual leap that most civilizations didn't make for millennia.

The Babylonians around 700 BCE used a *space* to indicate an empty position. That's almost zero, but it's easy to misread — one slightly wider gap could be ambiguous. The Mayans, around 400 CE, drew a glyph resembling a shell for zero. It was a full symbol, a legitimate placeholder.

In India, around 600 CE, Brahmagupta did something further: he treated zero not just as a placeholder but as a *number*. You can add it, subtract it, multiply by it. He worked out the rules. He made zero an object of mathematics, not just a notational convenience.

Once you have place value and zero together, the system is complete. You need exactly as many symbols as your base. For base 10, that's ten symbols: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9. Ten symbols, and you can write any number in the universe. Because the position of each symbol tells you what power of ten to multiply it by, and zero tells you when a position is empty.

The numeral 1,009 can now be read unambiguously: one in the thousands place, zero in the hundreds place, zero in the tens place, nine in the ones place. $1 \times 1{,}000 + 0 \times 100 + 0 \times 10 + 9 \times 1 = 1{,}009$. The zeros are doing work. Remove them and you change the number entirely.

![Zero is not decoration. It holds the position open.](images/04-number-representation-and-calculation-fig-03.png)
*Figure 4.3 — Comparison of two numerals *

---

## How other cultures solved the same problem differently

Calling the Hindu-Arabic system the "right" one would be too simple. Other cultures faced the same challenge and found different solutions, each reflecting different needs and different contexts.

The Babylonians, around 1800 BCE, built a positional system based on powers of 60, not 10. Their base was sixty — *šūšu* in Akkadian — chosen probably because 60 is divisible by 2, 3, 4, 5, 6, 10, 12, 15, 20, and 30. That's a lot of convenient divisors. Base 60 makes fractions easier.

Their two symbols — a wedge for 1, a wider wedge for 10 — could be combined to form any "digit" from 1 to 59. Then positions worked like ours: each position represents the next higher power of 60.

$$4 \times 60^1 + 27 \times 60^0 = 240 + 27 = 267$$

The Babylonian system is why we have 60 seconds in a minute, 60 minutes in an hour, and 360 degrees in a circle. That's not a coincidence or a cultural accident — it's Babylonian base 60 fossilized in our measurement of time and angle.

The Mayans, in Mesoamerica around 400 CE, built a base 20 system — probably because they counted on both fingers and toes. Their numerals were written vertically, lowest power at the bottom, higher powers stacked above. They had a genuine zero symbol. The system was positionally sound and worked beautifully for their calendar.

Here's the twist: for their astronomical calendar, the Mayans modified the base slightly. Instead of pure powers of 20, they used $1, 20, 20 \times 18 = 360, 360 \times 20 = 7{,}200$. The second step is $18$, not $20$, because 360 is close to the number of days in a solar year. They bent their mathematical system to fit the sky. That's not error — that's engineering.

Each of these systems reflects the problems its inventors were trying to solve: divisibility, astronomical cycles, ease of teaching. The Hindu-Arabic system won the historical competition not because it's mathematically superior in every dimension, but because it makes *multiplication and division* fast and teachable. Once commerce needed large-scale arithmetic, the system that made arithmetic easy was the one that spread.

| Base | Has zero symbol | Positional | Best suited for | Major weakness — student sees all five systems on one surface |
| --- | --- | --- | --- | --- |
| Tally, Roman, Babylonian, Mayan, Hindu-Arabic | columns: Base, Has zero symbol, Positional, Best suited for, Major weakness | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |

---

## The general machinery: any base, the same principle

Here is the key idea, and I want you to really sit with it: **place value is not specific to base 10**. It is a general principle. You can build a positional system in any base, and the machinery is identical.

In any base $b$:
- Use $b$ symbols: $0, 1, 2, \ldots, b-1$.
- The rightmost position represents $b^0 = 1$.
- The next position left represents $b^1 = b$.
- The next represents $b^2$.
- And so on.
- An $n$-digit numeral $d_{n-1} d_{n-2} \cdots d_1 d_0$ represents the quantity $d_{n-1} \times b^{n-1} + \cdots + d_1 \times b^1 + d_0 \times b^0$.

The symbols change. The base changes. The machinery — write a digit, multiply by the appropriate power of the base, add — never changes.

Let's work through base 6. In base 6, the legal symbols are 0, 1, 2, 3, 4, 5. Once you've used them all up, you start a new position. The number six, in base 6, is written $10_6$ — one group of six, zero ones. The number twelve is $20_6$. The number thirty-five is $55_6$ — five sixes plus five ones.

To convert $3024_6$ to base 10, apply the machinery:

$$3 \times 6^3 + 0 \times 6^2 + 2 \times 6^1 + 4 \times 6^0$$
$$= 3 \times 216 + 0 \times 36 + 2 \times 6 + 4 \times 1$$
$$= 648 + 0 + 12 + 4 = 664$$

Same principle you use every day reading base 10, just with 6 as the base instead of 10.

Going the other direction — converting from base 10 to another base — requires a different process: repeated division with remainder.

Convert $298$ to base 6. Divide by 6, keep the remainder, repeat:

- $298 \div 6 = 49$, remainder $4$
- $49 \div 6 = 8$, remainder $1$
- $8 \div 6 = 1$, remainder $2$
- $1 \div 6 = 0$, remainder $1$

Read the remainders from bottom to top: $1, 2, 1, 4$. So $298_{10} = 1214_6$.

Check it: $1 \times 216 + 2 \times 36 + 1 \times 6 + 4 = 216 + 72 + 6 + 4 = 298$. ✓

The reason remainders read bottom to top is that the division process extracts the *lowest* position first. The last remainder is the highest-power digit, so reading backward gives you the correct order.

![Step-by-step diagram of the repeated-division algorithm for 298](images/04-number-representation-and-calculation-fig-04.png)
*Figure 4.4 — Step-by-step diagram of the repeated-division algorithm for 298*

---

## Base 2: why computers speak binary

The most extreme case of small base is base 2, called *binary*. In base 2 there are exactly two symbols: 0 and 1. Every position represents a power of 2.

The number one hundred, in base 2, is:

$$1 \times 2^6 + 1 \times 2^5 + 0 \times 2^4 + 0 \times 2^3 + 1 \times 2^2 + 0 \times 2^1 + 0 \times 2^0$$
$$= 64 + 32 + 0 + 0 + 4 + 0 + 0 = 100$$

So $100_{10} = 1100100_2$. Three digits in base 10 becomes seven digits in base 2. Smaller bases require more digits to represent the same quantity.

Why would anyone want a system that requires more digits? Because the two symbols 0 and 1 can be stored electronically with extraordinary reliability. High voltage or low voltage. Magnetized or not. Hole or no hole. Any physical phenomenon with two clearly distinguishable states can encode a binary digit. Build enough of those states together and you can represent any number, any text, any image, any sound — all as sequences of 0s and 1s. The machinery inside every computer is doing exactly the arithmetic we've been doing in this chapter, just in base 2, billions of times per second.

The number of symbols in your base is a trade-off: larger bases need fewer digit-positions (compact) but require more distinct symbols (complex). Smaller bases need more digit-positions (verbose) but work with very few symbols (simple to implement physically). Base 10 sits in a comfortable middle range for human use. Base 2 sits at the extreme simple end, which is why it's ideal for machines.

![Scatter plot or table ](images/04-number-representation-and-calculation-fig-05.png)
*Figure 4.5 — Scatter plot or table *

---

## What makes notation matter

Let me end where I started: at the price tag, at the question of which system forces your brain to work less.

The answer isn't about complexity or intelligence. A Roman accountant was not less intelligent than a medieval Indian merchant. The Roman was just working with notation that made arithmetic hard. The machinery didn't help. Multiplication in Roman numerals is essentially translation work — you decode the symbols, compute in your head, and recode the answer. The notation carries no scaffolding for the computation.

The Hindu-Arabic system with place value carries scaffolding inside it. When you multiply two multi-digit numbers, you use the positions. You compute partial products for each place. The positions tell you where to put the results. The notation is doing some of the work. That's the difference.

Aryabhata and Brahmagupta didn't just invent symbols. They invented a notation that cooperated with arithmetic rather than fighting it. A student who learns this system — ten symbols, the place-value rule, a zero — can multiply any two numbers after a few hours of practice. That student would have spent years achieving less facility in the Roman system.

The notation spread because it was genuinely better for the work people needed to do. Commerce needed it. Astronomy needed it. Eventually engineering needed it. And now computers — which are, at their core, very fast arithmetic machines — carry the same idea into base 2 and work with it billions of times per second.

The quantity never changed. The year 1492 was always 1492. What changed was how we agreed to write it down. And that agreement, it turns out, shapes what mathematics becomes possible.

---

## Exercises

### Warm-up

**Exercise 4.1** Write each of the following base 10 numerals in expanded form using exponents. (a) 4,029. (b) 70,300. (c) 1,000,001.

**Exercise 4.2** Convert each base 6 numeral to base 10 using expanded form. (a) $43_6$. (b) $105_6$. (c) $524_6$.

**Exercise 4.3** For each base, list every legal digit symbol. (a) Base 4. (b) Base 9. (c) Base 12.

### Application

**Exercise 4.4** Convert the following base 10 numerals to the specified base using repeated division. Show each division step. (a) 47 to base 6. (b) 100 to base 2. (c) 255 to base 16.

**Exercise 4.5** Convert the Roman numeral MDCCCLXXXIV to base 10. Then write the result in base 2.

**Exercise 4.6** The number $267_{10}$ appears in the chapter as the result of a Babylonian place-value calculation. Verify this by working backward: express 267 in base 60 using repeated division by 60, and confirm the result matches the chapter's worked example ($4 \times 60 + 27$).

### Synthesis

**Exercise 4.7** The same quantity, one thousand, can be written as $1000_{10}$, $1750_8$, and $3E8_{16}$ (where E represents 14). (a) Verify all three conversions using expanded form. (b) Why does base 16 need fewer digits than base 10 to represent the same number? (c) Computer scientists often use base 16 rather than base 2 when displaying binary data. What advantage does base 16 offer over base 2 for this purpose?

**Exercise 4.8** A Mayan calendar system uses position values of 1, 20, 360, 7,200 (not pure powers of 20). A Mayan numeral has four positions, from bottom to top: 9, 4, 3, 2. (a) What base 10 number does this represent? (b) Why does this system use 360 rather than 400 ($20^2$) as its third position value? What does that choice reveal about the Mayans' priorities?

### Challenge

**Exercise 4.9** Base 12 has divisors 2, 3, 4, and 6. Base 10 has divisors 2 and 5. (a) In which base is it easier to express one-third as a terminating "decimal"? Explain why. (b) Design a base whose first four position values would make dividing by 3, 4, 5, and 7 all terminate cleanly. Is that possible, and if so, what base would you choose?

**Exercise 4.10** The chapter argues that the Hindu-Arabic system spread because it made *multiplication and division* teachable. Write a one-paragraph argument from the perspective of a medieval European merchant who has just encountered Hindu-Arabic numerals for the first time. What specific computational task would make you immediately abandon Roman numerals? Be concrete — choose an actual multiplication and work it out in both systems to make your case.

---

## LLM Exercise — Chapter 4: Number Representation and Calculation (Audit a Real-World System Project)

**Project:** Audit one real-world system through 13 chapters of mathematics.
**What you're building this chapter:** an analysis of how the system encodes information — account numbers, IDs, codes, SKUs — and what those encoding choices reveal.
**Tool:** **Claude Project** (same system spec as Ch 1).

**The Prompt:**

```
Chapter 4 of my system-audit project. Chapter 4 covered:
numbers vs. numerals; place value; the role of zero in
positional notation; bases other than 10 (especially binary,
base 6, base 60); historical numeration systems; why a base
gets chosen.

Apply to my system. Every system encodes information in
chosen formats. Surface those choices.

1. **Identify three encoding schemes the system uses.**
   Examples:
   - Transit: route IDs (Red Line, Bus 39), station IDs
     (numerical or alphabetical), fare types (zone-based
     codes).
   - Streaming: catalog IDs, user IDs, subscription tiers.
   - Sports: jersey numbers, position codes, statistical
     abbreviations (RBI, PER, xG).
   - Hospital: ICD-10 codes, medical record numbers, triage
     levels.
   For each, document: what range of values, what the
   alphabet is (digits 0-9; letters; combination), how
   long.

2. **Analyze the choice of base / alphabet for each.**
   - If purely numeric, what base implicitly? (Decimal
     for human-facing, but the underlying storage is
     binary.)
   - If alphanumeric, why? (Compactness — more compact
     than decimal-only; collision-resistance — easier to
     spell-check; accidental-confusion-resistance — like
     omitting O and 0, I and 1.)
   - If a checksum digit is used (credit card numbers, ISBN,
     MRN), describe the algorithm.

3. **Convert one system code to another base.** Take one
   number in the system (an account number, a route code, a
   batch ID). Convert it to:
   - Binary (base 2).
   - Hexadecimal (base 16).
   - One historical base — pick from base 6 (Babylonian-
     adjacent) or base 60.
   Show your work using expanded form. Note which
   representation is shortest, which is longest, which a
   human can read fastest.

4. **Find an encoding limitation.** Every encoding has a
   capacity — a fixed-length code can only represent so
   many distinct values. Calculate the capacity of one of
   the system's encodings. Predict when the system might
   run out of identifiers. (Famous examples: IPv4 address
   exhaustion in 2011; Y2K in 2000; the 2038 problem with
   32-bit Unix timestamps.)

5. **Find one place the system's representation choice
   reveals a design decision.** Why did the designers pick
   THIS encoding? What were they optimizing for? What did
   they sacrifice?

End with: a one-page "encoding audit" of the system. Three
encodings documented. One base-conversion of a real code.
One capacity calculation predicting when the encoding might
fail. One design-decision insight.
```

**What this produces:** An encoding audit. Most systems' design decisions show up in their encoding choices — what a system encodes verbosely vs. compactly says what it expects to scale.

**Connection to previous chapters:** Builds on Ch 3 (the underlying counting / cardinality dictates encoding capacity). Builds on Ch 1 (the categories you identified are often what the encoding distinguishes).

**Preview of next chapter:** Chapter 5 — apply algebra to the system's break-even, threshold, or tipping-point problems. Every system has at least one "when does X cross Y" question; this chapter solves yours.

---

##  AI Wayback Machine
**Al-Kindi** was 9th-century Arab philosopher and mathematician who developed the place-value Hindu-Arabic numeral system into a form Europe would later adopt.

**Run this:**

```
Who is Al-Kindi, and how does their work connect to number representation we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Al-Kindi"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Al-Kindi's ideas to a specific concrete problem in this chapter.
- Add a constraint: "Answer including criticisms or limits of Al-Kindi's framework."

What changes? What gets better? What gets worse?
