# Chapter 1 — Sets

## TL;DR

- The Art of Deciding What Belongs Together.
- The chapter moves through What a set actually is, Writing sets down, Counting what's inside, Equal versus equivalent — the picky distinction, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

*The Art of Deciding What Belongs Together.*

There is a move so old in mathematics that we barely notice we're making it anymore. You take a bunch of things — any things — and you decide to treat the bunch itself as a single thing. That's it. That's the whole idea. Everything in this chapter is a consequence of taking that step seriously.

The bunch has a name: a *set*. The things in it are *elements*. And the reason mathematicians care about this — the reason it's Chapter 1 — is that almost every other structure in mathematics is built on top of it. Logic. Probability. Statistics. Graph theory. Database queries. Blood banks. They're all doing the same thing in different clothes.

---

## What a set actually is

A set is a collection of things, treated as a single object, where membership is unambiguous. That last part matters. Either something is in the collection or it isn't. Any two people looking at the same thing should agree on whether it belongs.

The collection of all U.S. vice presidents is a set. You can look up each name and check. Either they held the office or they didn't. No argument.

The collection of *old cats* is not a set — not yet. "Old" depends on who you ask. My neighbor thinks her seven-year-old tabby is old. My grandmother's fourteen-year-old cat she calls middle-aged. The membership rule doesn't give the same answer to different observers. You'd have to sharpen "old" into something precise — "cats at least ten years of age" — before mathematics can touch it.

This is not pedantry. Vague terms cannot be reasoned with. A definition that wobbles is a foundation that cracks. Set theory insists on this discipline at the very first step, and that insistence is what makes everything downstream reliable.

---

## Writing sets down

Mathematicians like compact notation. The simplest way to write a set is just to list its elements, separated by commas, inside curly braces. If my kitchen drawer contains a fork, a spoon, a knife, a meat thermometer, and a can opener:

$$F = \{\text{fork}, \text{spoon}, \text{knife}, \text{meat thermometer}, \text{can opener}\}$$

Capital letter for the set. Curly braces. Commas. This is the *roster method*.

Two things to know about roster notation that trip people up.

First, order doesn't matter. $\{1, 2, 3\}$ and $\{3, 1, 2\}$ are the same set — the same collection of things, just listed in a different sequence. Mathematicians chose curly braces precisely to signal this: unordered. When order matters, they use parentheses instead.

Second, repetition adds nothing. $\{a, a, b\}$ and $\{a, b\}$ are the same set. An element is either in or it isn't. Listing it twice doesn't put it in twice.

For larger sets, you don't always want to list everything. The lowercase English alphabet has twenty-six letters. You could write them all, but it's faster to write:

$$A = \{a, b, c, \ldots, z\}$$

The three dots — the *ellipsis* — say *and so on, in the obvious pattern, until*. Establish the pattern with the first few elements, drop the dots, end with the last. For infinite sets, there's no last element, so you just leave the dots open:

$$\mathbb{N} = \{1, 2, 3, \ldots\}$$

The blackboard-bold $\mathbb{N}$ is standard notation for the natural numbers — the counting numbers. The integers, which include negatives and zero, go forever in both directions:

$$\mathbb{Z} = \{\ldots, -2, -1, 0, 1, 2, \ldots\}$$

The $\mathbb{Z}$ comes from *Zahlen*, German for "numbers."

Sometimes the elements are easier to *describe* than to list. The set of rational numbers — all fractions — is one of those. You can't roster the first three fractions in any sensible order and dot-dot-dot your way to the rest. Instead you write a membership rule:

$$\mathbb{Q} = \left\{ \frac{p}{q} \;\middle|\; p \text{ and } q \text{ are integers and } q \neq 0 \right\}$$

The vertical bar reads *such that*. Everything before it says what elements look like; everything after is the rule that determines membership. This is *set-builder notation*, and it's the right tool whenever listing fails.

| Notation Type | How to Write It | When to Use It — rows for Roster | listing | Ellipsis |
| --- | --- | --- | --- | --- |
| three-column reference — | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |

---

## Counting what's inside

For a finite set, its *cardinality* — written $n(A)$ — is just the number of elements. The kitchen drawer has five things, so $n(F) = 5$. Pretty simple.

But there's one set whose cardinality deserves its own moment: the *empty set*, written $\emptyset$ or $\{\}$. It's the set with nothing in it. $n(\emptyset) = 0$.

The empty set shows up more than you'd expect. The set of women who served as U.S. vice president before January 20, 2021, is empty. The set of prime numbers less than two is empty. The set of mammals that are also birds is empty. These are not defective sets — they're perfectly well-defined sets that happen to contain no elements.

Here is the trap: $\{0\}$ is *not* the empty set. It's a set containing one element, which happens to be the number zero. The set is the box; zero is something in the box. A box containing zero is not an empty box.

![The empty set is an empty container. {0} is a container holding zero. They are not the same thing.](images/01-sets-fig-01.png)
*Figure 1.1 — Illustration of two boxes *

---

## Equal versus equivalent — the picky distinction

Two sets are *equal* if they have exactly the same elements. $\{1, 2, 3\} = \{3, 1, 2\}$. Same elements, same set.

Two sets are *equivalent* if they have the same number of elements — the same cardinality — even if the elements are completely different. The kitchen drawer $F$ and the set of weekdays $\{\text{Mon}, \text{Tue}, \text{Wed}, \text{Thu}, \text{Fri}\}$ both have five elements. They are equivalent: $F \sim \{\text{Mon}, \text{Tue}, \text{Wed}, \text{Thu}, \text{Fri}\}$. They are not equal — a fork is not Monday.

Equal implies equivalent. Equivalent does not imply equal. Use the picky word when you mean the picky thing.

![One-way arrow diagram ](images/01-sets-fig-02.png)
*Figure 1.2 — One-way arrow diagram *

---

## Subsets

A set $A$ is a *subset* of $B$, written $A \subseteq B$, if every element of $A$ is also in $B$. The fork-and-knife pair $\{\text{fork}, \text{knife}\}$ is a subset of the full kitchen drawer $F$, because everything in the pair is also in the drawer.

A *proper subset*, written $A \subset B$, is a subset that isn't the whole thing — $B$ has at least one element not in $A$.

Two edge cases worth memorizing.

Every set is a subset of itself. $B \subseteq B$ is always true. But $B$ is not a *proper* subset of itself.

The empty set is a proper subset of every non-empty set. This sounds strange until you think about what the subset relation is actually checking: every element of $A$ must also be in $B$. The empty set has no elements. There is no element that fails the test. The requirement is vacuously satisfied. Mathematicians call this *vacuously true*, and it comes up constantly.

---

## Counting subsets — the doubling rule

Suppose you have a set with three elements: $\{a, b, c\}$. How many subsets does it have?

You can list them. All three elements: $\{a, b, c\}$. Every pair: $\{a, b\}$, $\{a, c\}$, $\{b, c\}$. Every singleton: $\{a\}$, $\{b\}$, $\{c\}$. The empty set: $\{\}$. That's $1 + 3 + 3 + 1 = 8$.

Here is the pattern. A one-element set has 2 subsets. A two-element set has 4. A three-element set has 8. Each additional element *doubles* the count.

The doubling makes sense if you think about it as a sequence of decisions. To build a subset of $\{a, b, c\}$, you make three independent yes-or-no choices: Is $a$ in? Is $b$ in? Is $c$ in? Two choices per element, three elements: $2 \times 2 \times 2 = 2^3 = 8$.

In general, for a set $A$ with $n(A) = n$ elements:

$$\text{number of subsets of } A = 2^{n(A)}$$

The empty set satisfies this too: $2^0 = 1$, and the empty set has exactly one subset — itself.

The formula looks innocent. It isn't. Ten elements gives $2^{10} = 1{,}024$ subsets. Twenty elements gives $2^{20} = 1{,}048{,}576$. Fifty gives more than a quadrillion. Combinatorial problems explode in exactly this way, and Chapter 7 will spend a great deal of time managing the explosion.

![Bar chart or table showing n (0 through](images/01-sets-fig-03.png)
*Figure 1.3 — Bar chart or table showing n (0 through*

---

## A short detour: infinity gets weird here

When Galileo Galilei was thinking about motion and mathematics in the early seventeenth century, he noticed something that bothered him. The set of natural numbers $\{1, 2, 3, \ldots\}$ contains the set of perfect squares $\{1, 4, 9, 16, 25, \ldots\}$ as a proper subset. The squares get rarer as you go — by the time you reach a thousand, only about 3% of the numbers you've passed are perfect squares. Intuitively, there should be "fewer" squares than naturals.

But you can pair them off, one for one:

$$1 \leftrightarrow 1, \quad 2 \leftrightarrow 4, \quad 3 \leftrightarrow 9, \quad 4 \leftrightarrow 16, \quad n \leftrightarrow n^2, \quad \ldots$$

Every natural number has a unique square. Every perfect square has a unique natural-number root. The pairing is perfect and goes on forever. By the equivalence definition — same cardinality — the natural numbers and the perfect squares are the same size.

Galileo concluded, sensibly, that greater than and less than don't apply to infinite sets the way they apply to finite ones, and he stopped there.

Two hundred fifty years later, Georg Cantor showed the situation is more interesting than Galileo realized. Not all infinite sets are equivalent. The natural numbers and the integers and the rationals are all the same size — *countably infinite*, cardinality $\aleph_0$. You can construct pairings between all of them. But the real numbers — every point on the number line — cannot be paired with the naturals. There is no pairing. The reals are a strictly larger infinity. Cantor proved this, and it disturbed people enough that some of his contemporaries attacked not just his results but him personally. He died in a sanatorium in 1918.

We won't prove Cantor's theorem here. But the result sits in the room whenever we talk about infinite sets, and it's worth knowing it's there.

![Two-column comparison ](images/01-sets-fig-04.png)
*Figure 1.4 — Two-column comparison *

---

## Combining sets: union, intersection, complement

Sets can be combined. There are three basic operations.

The **union** of $A$ and $B$ is everything in either one:

$$A \cup B = \{x \mid x \in A \text{ or } x \in B\}$$

The symbol $\cup$ looks like a cup — you pour both sets into it. An element qualifies for the union if it belongs to at least one of the sets, possibly both.

The **intersection** of $A$ and $B$ is what they share:

$$A \cap B = \{x \mid x \in A \text{ and } x \in B\}$$

The symbol $\cap$ looks like a hat — both sets have to claim the element for it to appear in the intersection.

The **complement** of $A$ is everything that's not in it, within some agreed-upon universe $U$:

$$A' = \{x \in U \mid x \notin A\}$$

The complement always depends on the universe. This is not a formality — it matters. If $A = \{2, 4, 6, 8\}$ and $U = \{1, 2, \ldots, 10\}$, then $A' = \{1, 3, 5, 7, 9, 10\}$. If $U$ is all natural numbers, $A'$ is an infinite set containing every natural number except 2, 4, 6, and 8. Same $A$, different universe, completely different complement. Always specify the universe first.

When two sets share no elements — $A \cap B = \emptyset$ — they are called *disjoint*. Lions and tigers in a zoo are disjoint subsets of the big-cat enclosures. Neither is the complement of the other within big cats — there are also leopards and jaguars. Disjoint just means no overlap; complement is a stronger relationship.

![Three labeled Venn diagrams side by side ](images/01-sets-fig-05.png)
*Figure 1.5 — Three labeled Venn diagrams side by side *

---

## The cardinality formula for unions

If you want to count how many elements are in $A \cup B$, you can't just add $n(A) + n(B)$ when the sets overlap. Elements in both sets would get counted twice.

Subtract the double-count once:

$$n(A \cup B) = n(A) + n(B) - n(A \cap B)$$

If the sets are disjoint, $n(A \cap B) = 0$ and the formula reduces to simple addition. If they overlap, the subtraction corrects for the shared elements.

Here is a quick example. Don Woods is hosting a Juneteenth celebration for 54 guests. 30 took cake. 20 took ice cream. 12 took neither. How many took both?

The 12 who took neither tell us that 42 guests took cake or ice cream (or both): $n(C \cup I) = 54 - 12 = 42$. Now apply the formula:

$$42 = 30 + 20 - n(C \cap I)$$
$$n(C \cap I) = 50 - 42 = 8$$

Eight people had both. Check it: cake-only is $30 - 8 = 22$, ice-cream-only is $20 - 8 = 12$, both is 8, neither is 12. Total: $22 + 12 + 8 + 12 = 54$. ✓

---

## Venn diagrams

John Venn, an English logician, formalized the picture for set operations in 1881. (Leonhard Euler had used overlapping circles a century earlier; Venn systematized them.) The convention: draw the universal set as a rectangle. Draw each subset as a circle inside the rectangle. Overlapping circles represent sets that share elements. Disjoint circles represent sets that don't.

Two overlapping circles divide the rectangle into four regions: in $A$ only, in $B$ only, in both, in neither. Three overlapping circles create eight regions. Each additional set roughly doubles the complexity, which is why Venn diagrams stop being convenient beyond three or four sets — the math keeps going, but the picture becomes unusable.

The value of the diagram is that it turns the bookkeeping into geometry. Instead of tracking which elements belong to which combination of sets, you place a count in each region and read the answers off the picture. The three-set version of this — filling in regions from the inside outward, starting with the all-three intersection and working out — is one of the most useful problem-solving routines in this course.

![Two-set Venn diagram with regions labeled: "only A",](images/01-sets-fig-06.png)
*Figure 1.6 — Two-set Venn diagram with regions labeled: "only A",*

---

## De Morgan's laws

Augustus De Morgan, a contemporary of Venn's, proved a pair of identities that reveal something deep about the structure of sets:

$$(A \cup B)' = A' \cap B'$$
$$(A \cap B)' = A' \cup B'$$

Read the first one aloud: the things not in (A or B) are exactly the things not in A *and* not in B. To be outside the union, you have to be outside both. Read the second: the things not in (A and B) are the things not in A *or* not in B. To miss the intersection, you only need to miss one of the sets.

Notice what the complement operation does: it flips union into intersection, and intersection into union. There is a duality here that runs all the way through mathematics. You will see it again in Chapter 2, where it becomes the logical rule that *not (P and Q)* is equivalent to *not P or not Q*.

Verify De Morgan on a small example to make it concrete. Let $U = \{1, 2, 3, 4, 5, 6, 7\}$, $A = \{2, 3, 4\}$, $B = \{3, 4, 5, 6\}$.

Left side of the first law: $A \cup B = \{2, 3, 4, 5, 6\}$, so $(A \cup B)' = \{1, 7\}$.

Right side: $A' = \{1, 5, 6, 7\}$, $B' = \{1, 2, 7\}$, and $A' \cap B' = \{1, 7\}$.

Both sides give $\{1, 7\}$. ✓ A specific check isn't a proof — to prove it properly you'd shade two Venn diagrams and show the regions match for any sets, not just these. But checking a specific case is a good way to build intuition before you trust the general statement.

![Two-row Venn diagram proof of the first De](images/01-sets-fig-07.png)
*Figure 1.7 — Two-row Venn diagram proof of the first De*

---

## The blood bank, done right

Return to the Saturday-morning blood drive. The cooler holds 100 donor bags sorted into eight compartments by blood type: O−, O+, A−, A+, B−, B+, AB−, AB+. Suppose the counts come out:

| Blood type | Count |
|---|---|
| O− | 7 |
| A− | 6 |
| B− | 2 |
| O+ | 12 |
| A+ | 36 |
| B+ | 33 |
| AB− | 1 |
| AB+ | 3 |

Sum: $7 + 6 + 2 + 12 + 36 + 33 + 1 + 3 = 100$. ✓

![Three-set Venn diagram for blood types ](images/01-sets-fig-08.png)
*Figure 1.8 — Three-set Venn diagram for blood types *

Think of this as a three-set Venn diagram. Circle $A$ catches everyone with the type-A antigen. Circle $B$ catches everyone with type-B. Circle $\text{Rh}^+$ catches everyone with the Rh-positive factor. Each of the eight blood types corresponds to one of the eight regions of the diagram.

How many donors carry the A factor? The four regions inside circle $A$ are A−, A+, AB−, and AB+: $6 + 36 + 1 + 3 = 46$.

How many are Rh+? The four regions inside circle $\text{Rh}^+$ are O+, A+, B+, AB+: $12 + 36 + 33 + 3 = 84$.

How many are Rh−? Complement: $100 - 84 = 16$. Or sum the four Rh− regions directly: $7 + 6 + 2 + 1 = 16$. Both methods agree.

Julio needs surgery and can accept any bag without the type-A antigen. How many of today's 100 bags can his team use? Everything outside circle $A$: $7 + 2 + 12 + 33 = 54$. Or by complement: $100 - 46 = 54$.

The phlebotomist sorted 100 strangers into eight cells without thinking about set theory. The hospital's protocol then asks the cells a question. The cells answer in numbers. That is set theory doing real work.

---

## Why this is Chapter 1

Every chapter that follows uses this vocabulary. Logic uses AND and OR — the same operations as intersection and union. Probability is the ratio of one set to another, within a universal set called the sample space. Statistics groups data into sets and asks how those groups behave. Graph theory builds networks out of sets of vertices and edges. Voting theory begins with the set of voters and the set of candidates, and asks which subsets satisfy various fairness conditions.

The reason this is Chapter 1 is that it is the alphabet. Every later chapter spells things with it. Once you can say *universe*, *element*, *subset*, *union*, *intersection*, *complement*, and *cardinality* — and mean exactly those things — the rest of the book opens up.

The one thing to carry forward, the one place where students consistently go wrong in every later chapter: **always state the universe**. Almost every set-theory mistake, and almost every probability mistake, comes from being sloppy about what universe you're working in. State it first. State it explicitly. What you can include in a complement, what counts as an event, what probability sums to — all of it depends on the universe. Name it before you start.

---

## Exercises

### Warm-up

**Exercise 1.1** Let $V = \{a, e, i, o, u\}$. (a) What is $n(V)$? (b) Is $\{a, e\} \subseteq V$? Is it a proper subset? (c) Write $V$ in set-builder notation using the membership rule "lowercase vowels of the English alphabet."

**Exercise 1.2** For each of the following, decide whether the described collection is a well-defined set. If it isn't, explain what would need to be specified to make it one. (a) The set of even integers between 10 and 20. (b) The set of tall buildings in Boston. (c) The set of U.S. states that border the Pacific Ocean.

**Exercise 1.3** For each pair, state whether the two sets are equal, equivalent but not equal, or neither. (a) The set of letters in *listen* and the set of letters in *silent*. (b) $\{2, 4, 6, 8, 10\}$ and $\{1, 3, 5, 7, 9\}$. (c) $\{a, b, c\}$ and $\{c, a, b\}$.

### Application

**Exercise 1.4** You have four bills in your wallet: \$1, \$5, \$10, \$20. (a) How many distinct subsets of bills can you take out, including taking nothing? (b) List the subsets whose total equals exactly \$15.

**Exercise 1.5** A gym surveyed 120 members about two classes: yoga and spin. 70 attended yoga. 50 attended spin. 20 attended both. (a) How many attended yoga or spin (or both)? (b) How many attended neither? Draw a two-set Venn diagram and fill in all four regions.

**Exercise 1.6** Let $U = \{1, 2, 3, \ldots, 12\}$, $P = \{2, 3, 5, 7, 11\}$ (primes in $U$), $E = \{2, 4, 6, 8, 10, 12\}$ (evens in $U$). Find: (a) $P \cup E$, (b) $P \cap E$, (c) $P'$, (d) $n(P \cup E)$ — first by listing, then by the formula. Do both methods agree?

### Synthesis

**Exercise 1.7** A college surveyed 150 students about three streaming services: 90 use Service A, 60 use Service B, 50 use Service C. 30 use both A and B. 20 use both A and C. 15 use both B and C. 10 use all three. (a) Build a three-set Venn diagram and fill in all eight regions. (b) How many use none of the three? (c) How many use exactly one service?

**Exercise 1.8** Let $U = \{1, 2, 3, \ldots, 10\}$, $A = \{1, 2, 3, 4, 5\}$, $B = \{4, 5, 6, 7\}$. (a) Compute $A \cup B$, $A \cap B$, $A'$, $B'$. (b) Verify $(A \cup B)' = A' \cap B'$. (c) Verify $(A \cap B)' = A' \cup B'$. (d) In one sentence each, state what both laws say in plain English.

### Challenge

**Exercise 1.9** Cantor showed that the natural numbers and the positive even numbers have the same cardinality. (a) Write an explicit pairing between $\mathbb{N} = \{1, 2, 3, \ldots\}$ and the positive even numbers $\{2, 4, 6, \ldots\}$. (b) Now construct a pairing between $\mathbb{N}$ and $\mathbb{Z}$ — all integers, including negatives and zero. (Hint: alternate signs, handle zero somewhere.) (c) The same trick cannot establish a pairing between $\mathbb{N}$ and the real numbers. Describe in your own words why the real numbers resist being listed, without writing a formal proof.

**Exercise 1.10** You're managing a small conference with 30 attendees. You track three attributes: who registered early, who has a dietary restriction, and who is presenting. Choose plausible cardinalities for each set and for each overlap (making sure all counts are internally consistent), draw a three-set Venn diagram with your numbers, and answer: (a) How many attendees are only presenters, with no other flags? (b) How many require a dietary accommodation? (c) How many are in all three categories? State your assumed numbers clearly so your arithmetic can be checked.

### LLM exercises

**LLM Exercise 1.1** Ask an AI assistant to explain the difference between equal sets and equivalent sets, then write a paragraph evaluating whether its explanation would be clear to a student who just finished this chapter. What did the AI get right? What, if anything, did it obscure or leave out?

**LLM Exercise 1.2** Give an AI the following problem: *A survey of 200 people found that 110 drink coffee, 80 drink tea, and 150 drink at least one of the two. How many drink both?* Have the AI solve it. Then solve it yourself using the union cardinality formula. Do the answers agree? Did the AI show its reasoning, or did it state the answer without derivation? What's the risk of relying on a tool that gives answers without showing steps?

**LLM Exercise 1.3** Ask an AI to state De Morgan's laws and explain them in plain English. Then check the explanation against the version in this chapter. Does the AI's version make the duality between union and intersection visible, or does it just state the formulas? Write two sentences on what the AI's explanation does well and what it would need to add for a student to really understand why the laws are true.

**LLM Exercise 1.4** Prompt an AI: *List all subsets of the set $\{1, 2, 3, 4\}$ and tell me how many there are.* Check the AI's output. Did it list all $2^4 = 16$ subsets? Did it include the empty set and the full set? If it made any errors, describe them precisely using the vocabulary from this chapter.

**LLM Exercise 1.5** Ask an AI to explain Cantor's diagonal argument — why the real numbers are uncountably infinite while the natural numbers are countably infinite. You haven't learned the proof in this chapter, and you're not expected to fully evaluate the mathematics. But you can evaluate whether the AI's explanation is clear, whether it distinguishes between countable and uncountable infinity, and whether it gives you any intuition for why the two sizes are genuinely different. Write a paragraph reporting what you found.
---

## LLM Exercise — Chapter 1: Sets (Audit a Real-World System Project)

**Project:** Pick one specific real-world system and analyze it through every chapter's mathematics. By Chapter 13 you will have produced a 25-30 page comprehensive analysis demonstrating 13 mathematical lenses on one target. The system you choose in this chapter carries through every later chapter.
**What you're building this chapter:** the system specification + the first analytical pass — a set-theoretic diagram of the system's user / customer / product / category groupings.
**Tool:** **Claude Project** (set the system spec at the top so every later chapter references it) + Cowork for the audit folder.

**The Prompt:**

```
I'm starting a 13-chapter project where I analyze ONE real-world
system through every chapter of a contemporary-mathematics
textbook. I need to pick the system and then do the first
analytical pass.

Step 1 — Pick the system. Help me choose ONE of the following
that I can actually research:

   a. A city's transit network (NYC subway, Boston T, your
      hometown bus system).
   b. A streaming-service catalog (Netflix, Spotify, Disney+).
   c. A sports league (NBA, NFL, English Premier League).
   d. A fast-food chain's menu and pricing (McDonald's, Chipotle).
   e. A university's enrollment / course-catalog system.
   f. An apartment building / housing complex.
   g. A hospital's emergency department workflow.
   h. A grocery store's inventory and pricing.
   i. Your country's tax brackets and deductions.
   j. A specific election (with public ballot results).

Reject any "system" too vague to count things in — the system
must have countable elements (users, customers, products,
categories, routes, items, slots).

Step 2 — Specify the system. Once chosen, write a 200-word
specification: what the system is, who uses it, what it
produces, what numerical / quantitative data is publicly
available about it, where I can find that data.

Step 3 — Apply Chapter 1's machinery (sets) to the system:

   1. Identify 3-4 meaningful set-categorizations of the
      system's elements. (Example for a transit network:
      lines, stations, fare zones, time periods.)

   2. Pick TWO of the categorizations and build a Venn
      diagram showing their intersection. (Example:
      stations that are on the Red Line AND in fare
      zone 1.)

   3. Calculate cardinalities — how many elements in each
      set, in each intersection, in each union.

   4. Apply the cardinality formula:
      |A ∪ B| = |A| + |B| − |A ∩ B|. Verify your numbers.

   5. Identify one real subset relationship in the system
      and one pair of complement sets. Use proper set
      notation.

   6. Apply De Morgan's laws to one specific case in the
      system. (Example: "stations that are NOT (Red Line
      OR fare zone 1)" vs. "stations that are NOT Red Line
      AND NOT fare zone 1.")

End with: a one-paragraph "system spec" + a Venn diagram (drawn
in markdown / ASCII / image) + a table of cardinalities. Save the
system spec at the top of your Claude Project — every later
chapter references it.
```

**What this produces:** A locked-in system specification + first analytical pass demonstrating set theory on the system. The system spec is the foundation document.

**Connection to previous chapters:** None — this is the project foundation.

**Preview of next chapter:** Chapter 2 — apply logic and truth tables to the if-then rules your system runs on (eligibility rules, billing rules, scheduling rules). You'll formalize at least three of the system's logical rules and check whether the system's stated logic matches what it actually does.

---

##  AI Wayback Machine

![Georg Cantor](../images/georg-cantor-mv8.png)

*Puppet Art by [Nik Bear Brown](https://www.nikbearbrown.com/).*

**Run this:**

```
Who is Georg Cantor, and how does their work connect to set theory we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Georg Cantor"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Georg Cantor's ideas to a specific concrete problem in this chapter.
- Add a constraint: "Answer including criticisms or limits of Georg Cantor's framework."

What changes? What gets better? What gets worse?
