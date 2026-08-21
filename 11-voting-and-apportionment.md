# Chapter 11 — Voting and Apportionment

## TL;DR

- In 1972, an economist named Kenneth Arrow won the Nobel Prize partly for proving that no fair voting system can exist.
- The chapter moves through What fairness requires, The machinery: voting methods and what they sacrifice, The theorem itself, The same impossibility, in a different room, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

*Every Fair System Is Impossible. Here Is Why That Is Useful to Know.*

In 1972, an economist named Kenneth Arrow won the Nobel Prize partly for proving that no fair voting system can exist.

Not "no perfect voting system." Not "no voting system without flaws." No *fair* one. He defined four properties that any reasonable person would demand of a fair election — four criteria so obvious that stating them feels redundant — and then proved, with mathematical rigor, that no voting system based on ranked preferences can satisfy all four simultaneously. You must sacrifice at least one. Always. With no exceptions.

This is not a political claim. It is a theorem. It has a proof. And it applies to every democracy on Earth.

This chapter unpacks what Arrow actually proved, shows you the machinery that makes it true, and then shows you the same impossibility appearing again — in a completely different problem — eleven years later. The pattern is not a coincidence. It is something deep about what fairness means when resources are indivisible and populations are diverse.

---

## What fairness requires

Before you can prove that fair voting is impossible, you need to say what fair means. Arrow identified four criteria. Each one, stated alone, seems so reasonable that you might wonder why anyone would bother to write it down.

**The majority criterion.** If more than half the voters rank a candidate first, that candidate should win. A majority preference should produce a majority winner.

**The Condorcet criterion.** If one candidate would beat every other candidate in a direct head-to-head matchup, that candidate should win the full election. Call this the head-to-head winner. If the voters collectively prefer A to B, and A to C, and A to D, then A should win regardless of the counting method.

**The monotonicity criterion.** If a candidate wins, and then some voters change their ballots to rank that candidate *higher* — and nothing else changes — that candidate should still win. Voting for someone more enthusiastically should not hurt them.

**Independence of irrelevant alternatives.** If candidate A beats candidate B in an election, and then candidate C (who lost) is removed from the ballot, A should still beat B. The outcome between two candidates should not depend on the presence or absence of a third candidate who is not winning.

Read these again. Each one is just a formalization of something you already believe about fairness. Together, they describe a voting system that cannot be gamed, cannot be spoiled, and rewards genuine majority preference. Arrow's theorem says: you cannot have all four.

| Criterion | Plain-language statement | The intuition behind it | What violating it looks like in practice" — |
| --- | --- | --- | --- |
| majority, Condorcet, monotonicity, independence of irrelevant alternatives | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| the "what violation looks like" column should use one-line real examples (e.g., IIA: "Nader's presence changes Gore vs. Bush outcome") | student should be able to scan this table and immediately recognize a criterion violation when they see one in the exercises | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |

---

## The machinery: voting methods and what they sacrifice

To see why the impossibility is real and not just a mathematical abstraction, you need to know how different voting systems work and which criterion each one gives up. There are six main methods. None of them passes Arrow's test.

**Plurality voting.** The candidate with the most votes wins. This is the method used in most American elections. It is fast, simple, and transparent. What it sacrifices: the Condorcet criterion and independence of irrelevant alternatives.

The Condorcet failure is worth seeing concretely. Suppose a town of 100 voters chooses among three school board candidates — Alice, Bob, and Carol. Alice gets 40 votes, Bob gets 37, Carol gets 23. Plurality says Alice wins. But Carol's 23 voters, and Bob's 37 voters, all prefer Bob to Alice. In a direct matchup, Bob beats Alice 60 to 40. Alice won the plurality election despite the fact that a clear majority prefer someone else. Bob is the Condorcet candidate. Plurality ignored him.

The independence failure is the spoiler effect. In the 2000 U.S. presidential election in Florida, Ralph Nader received 97,488 votes for the Green Party. Exit polling and subsequent analysis consistently showed that Nader's voters' second choice was overwhelmingly Al Gore. Without Nader on the ballot, Gore wins Florida, and the presidency. The outcome between Gore and Bush — the two serious candidates — was changed by the presence of Nader, who lost badly. Independence of irrelevant alternatives was violated. The "irrelevant" candidate was not irrelevant at all.

**Runoff voting.** If no candidate wins a majority, the two candidates with the most first-round votes advance to a second election. The majority winner of the runoff wins overall.

This fixes the majority failure of plurality. It also reduces spoiler effects in the first round — if your favorite candidate doesn't advance, their elimination is at least decisive. What it sacrifices: cost, participation (different voters show up in round two), and independence of irrelevant alternatives (third-place finishers can still change who advances to the runoff).

**Ranked-choice voting.** Voters rank all candidates. Eliminate the candidate with the fewest first-place votes; redistribute those ballots to whoever was ranked second. Repeat until one candidate has a majority.

This simulates runoffs without requiring voters to return. It eliminates some spoiler effects — you can rank your true favorite first without fear of wasting your vote. It guarantees a majority winner. What it sacrifices: monotonicity.

The monotonicity failure is counterintuitive and worth pausing on. Suppose candidate A is doing well in round two of an instant runoff. Some voters, seeing A's success, decide to move A up from second place to first place on their ballots. This changes who gets eliminated in the current round, which changes who advances, which can change who A faces in the final round — and A might lose a final round they would have won under the original ballot order. More support, worse outcome. The failure is real and has been documented in actual elections.

**Borda count.** Rank the candidates and award points based on rank. With $n$ candidates, first place is worth $n-1$ points, second place $n-2$ points, and so on. The candidate with the most total points wins.

Borda count tends to elect compromise candidates — people who are not anyone's top choice but are broadly acceptable. If an electorate is polarized between two extremes, Borda often elects the moderate who sits in the middle. Some see this as wisdom; others see it as a failure to respect intensity of preference.

What it sacrifices: the majority criterion. A candidate with 51 percent of first-place votes can lose to a compromise candidate who finishes second on almost every ballot. The majority's top choice is overruled by a candidate broadly ranked "acceptable."

**Pairwise comparison.** Compare every candidate against every other in head-to-head matchups. Award one point per matchup won. The candidate with the most points wins. If a Condorcet candidate exists, this method elects them — it is the only method that guarantees this.

What it sacrifices: it fails when no Condorcet candidate exists. Voter preferences can cycle: A beats B, B beats C, C beats A. There is no winner. The method breaks down. And it still violates independence of irrelevant alternatives — removing a losing candidate can change who wins between the others.

**Approval voting.** Each voter approves any number of candidates; the most-approved candidate wins. Simple, avoids some spoiler effects, allows voters to express genuine indifference. What it sacrifices: if supporters of the frontrunner strategically approve only their candidate and no one else, the election collapses into plurality. And it still violates independence of irrelevant alternatives.

Here is the pattern Arrow identified. You can have majority rule or Condorcet satisfaction. You can have monotonicity or spoiler-proofing. You cannot have all of them. Every method surrenders something.

| majority criterion | Condorcet criterion | monotonicity | independence of irrelevant alternatives |
| --- | --- | --- | --- |
| plurality, runoff, ranked-choice, Borda, pairwise comparison, approval voting | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| columns: majority criterion, Condorcet criterion, monotonicity, independence of irrelevant alternatives | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| each cell contains ✓ (satisfies) or ✗ (violates | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| no method has all ✓ in every column | this is the visual proof of Arrow's claim before the formal theorem is stated | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| student should see at a glance that every row has at least one ✗ | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |

---

## The theorem itself

Arrow's proof does not just survey existing methods and note their failures. It proves that *any* conceivable method based on ranked preferences must fail at least one criterion. There is no undiscovered method waiting to be found. The impossibility is structural.

The argument, stripped to its core, goes like this. Take any voting method that satisfies independence of irrelevant alternatives and the Pareto condition (if everyone prefers A to B, A should beat B — a criterion so weak it barely deserves a name). Arrow showed that any such method must be a *dictatorship*: there is some single voter whose ranking of every pair of candidates determines the outcome, regardless of what everyone else votes. A dictator in Arrow's sense is not a tyrant; it is a mathematical label for a voter whose preferences are always decisive. But a dictatorial voting system obviously violates majority rule and every other fairness criterion.

The conclusion: satisfy IIA and Pareto, and you get a dictatorship. Reject dictatorship, and you must give up IIA or Pareto or both — which means you give up at least one of the other fairness criteria.

The result is tight. You cannot escape by adding more candidates, more voters, or more rounds. The impossibility applies to any finite electorate with at least three candidates.

What the theorem does not say is also worth stating. Arrow's theorem applies to *ranked* voting systems. It does not directly apply to systems where voters give numerical ratings (score voting, range voting). Whether rating-based systems escape the impossibility or merely move the problem elsewhere is an open question in social choice theory. But ranked preferences are what most democracies use, and Arrow's theorem is what constrains them.

---

## The same impossibility, in a different room

In 1983, mathematicians Michel Balinski and H. Peyton Young proved a theorem about apportionment that has exactly the same shape as Arrow's. Different problem. Same structure. Same unavoidable trade-off.

The apportionment problem is this. The United States House of Representatives has 435 seats. These seats are distributed among the 50 states based on population. After each census, the distribution is recalculated. The problem: population divided by seats almost never produces a whole number. California's fair share might be 52.19 seats. You cannot give a state 0.19 of a representative. You must round. But how?

Every rounding method introduces a bias. Some favor large states; some favor small ones. Some produce paradoxes so strange they should not be possible.

The most famous is the **Alabama paradox**, discovered in 1880. Congressional staff were computing apportionments for different hypothetical house sizes to help decide what size the House should be. They found something alarming: if the House had 299 seats, Alabama would receive 8. If the House had 300 seats — one more seat, distributed among all states — Alabama would receive only 7. The House grew. Alabama shrank.

This is not an arithmetic error. It is a consequence of the method being used (Hamilton's method, which awards remaining seats to states with the largest fractional remainders). When the house size changes, the standard divisor changes, which changes all the fractional remainders, which changes who wins the remaining seats in the final distribution. Alabama lost out in the shuffle.

| Item | Meaning |
| --- | --- |
| illustrating the Alabama paradox | left side: House size = 299, showing each state's standard quota and final Hamilton allocation |
| right side: House size = 300, same states, same populations, showing how Alabama's allocation drops from 8 to 7 despite the house growing | A concrete checkpoint for applying the chapter concept. |
| the Alabama row should be visually highlighted | A concrete checkpoint for applying the chapter concept. |
| a caption beneath: "The house grew by one seat. Alabama lost one seat." | student should see the paradox in numbers, not just in prose |

Two other paradoxes compound the problem. The **population paradox**: a state growing faster than another can lose a seat while the slower-growing state gains one. The **new-states paradox**: when a new state is added and the house is enlarged to accommodate it, an existing state can lose a seat it previously held — even though that state's population has not changed.

Balinski and Young proved: **no apportionment method can simultaneously satisfy the quota rule (every state receives either its rounded-down or rounded-up fair share, never more or less) and avoid all three paradoxes.**

The methods that avoid paradoxes — Jefferson's method, Adams's method, Webster's method — do so by sometimes giving states more or fewer seats than their strict proportional share. Jefferson's method systematically favors large states. Adams's method favors small states. Webster's method is more balanced but still distorts.

Hamilton's method respects the quota rule strictly but produces the Alabama paradox and the others. There is no method that does both.

| Satisfies quota rule? | Alabama paradox possible? | Population paradox possible? | New-states paradox possible? | Bias (if any) |
| --- | --- | --- | --- | --- |
| Hamilton, Jefferson, Adams, Webster | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| columns: "Satisfies quota rule?", "Alabama paradox possible?", "Population paradox possible?", "New-states paradox possible?", "Bias (if any)" | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| cells: ✓ | ✗ for each property, with "favors large states" | "favors small states" | "balanced" in the bias column | the visual echo of the voting methods matrix above |
| student should see that no row is all ✓, mirroring the voting methods table and making the parallel structure of the two impossibility theorems visible | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |

---

## Why these two theorems belong in the same chapter

Arrow in 1972. Balinski-Young in 1983. Different problems — one about choosing a winner, one about distributing seats. Different proofs. Different mathematical machinery.

But the same underlying structure: you have a set of fairness criteria, each of which is individually obvious and reasonable, and together they are mutually incompatible. Any method satisfies some and violates others. No method satisfies all.

This pattern appears wherever you try to formalize fairness with mathematics and then apply it to a world where things cannot be divided indefinitely. Votes cannot be split. Seats cannot be fractional. When you try to turn continuous fairness into discrete decisions, something breaks. Arrow and Balinski-Young proved which breakages are unavoidable.

![Diagram showing the parallel structure of both impossibility](images/11-voting-and-apportionment-fig-01.png)
*Figure 11.1 — Diagram showing the parallel structure of both impossibility*

The practical consequence is exactly what the opening of this chapter suggested: choosing a voting method is not a technical decision. It is a political one. When a legislature chooses plurality voting over ranked-choice, or Hamilton's method over Webster's, it is choosing which fairness criterion to sacrifice and which constituency to advantage. The mathematics does not make that choice. It only reveals that a choice is being made — whether the people making it acknowledge it or not.

---

## Chapter summary

Arrow's Impossibility Theorem says: no voting system based on ranked preferences satisfies all four fairness criteria — majority, Condorcet, monotonicity, and independence of irrelevant alternatives — simultaneously. Every method sacrifices at least one.

Plurality gives up Condorcet and independence. Ranked-choice gives up monotonicity. Borda gives up majority. Pairwise comparison breaks when preferences cycle. Approval degrades under strategic voting. These are not bugs in particular implementations. They are structural properties of what the methods can and cannot do.

Balinski and Young proved the same structure applies to apportionment. No method distributes seats without either violating the quota rule or producing paradoxes — situations where adding seats hurts a state, fast growth loses representation, or a new state causes an old one to shrink.

The one idea that matters most: impossibility theorems are not counsel for despair. They are information. When you know that every voting method sacrifices something, you can ask the right question — not "which method is fair?" but "which fairness does our community value most, and which trade-offs are we willing to accept?" That is a harder question. It is also the honest one.

The Feynman test for this chapter: can you explain to someone who has never studied mathematics why Ralph Nader's presence in the 2000 election changed the outcome between Gore and Bush — and then explain why no voting method can fully prevent this kind of thing? If you can trace the argument from "voting for Nader hurt Gore" to "Arrow proved this is unavoidable," you understand what this chapter is about.

---

## Exercises

### Warm-up

**Exercise 11.1** *(Identify what each fairness criterion requires; LO: state the four criteria in plain language).* For each scenario, name the fairness criterion that is being violated and explain in one sentence why.

(a) Candidate A receives 55% of first-place votes but loses the election because her second-place rankings are weak under Borda count.
(b) Candidate B wins a ranked-choice election. Some voters then change their ballots to rank B higher. B now loses.
(c) Candidate C would beat every other candidate in a direct head-to-head matchup, but C loses under plurality voting.
(d) Candidate A beats B when all three candidates are on the ballot. C is removed as a spoiler. Now B beats A.

**Exercise 11.2** *(Apply plurality and Borda count to the same election; LO: show that method choice changes outcome).* Seven voters rank three candidates X, Y, Z:

$$\begin{array}{cccc}
\text{Voters} & 3 & 2 & 2 \\
\text{First} & X & Y & Z \\
\text{Second} & Y & Z & Y \\
\text{Third} & Z & X & X
\end{array}$$

(a) Who wins by plurality?
(b) Calculate the Borda scores (2 points for first, 1 for second, 0 for third) and determine the Borda winner.
(c) Is there a conflict between the two results? Which fairness criterion does the losing method violate?

**Exercise 11.3** *(Compute a standard quota; LO: set up the apportionment problem).* A country has four provinces with populations 120,000, 180,000, 300,000, and 400,000. There are 50 seats to apportion.

(a) Compute the standard divisor.
(b) Compute each province's standard quota.
(c) What are the lower and upper quotas for each province?

### Application

**Exercise 11.4** *(Apply ranked-choice voting and identify the monotonicity risk; LO: trace elimination rounds).* Nine voters rank three candidates A, B, C:

$$\begin{array}{cccc}
\text{Voters} & 4 & 3 & 2 \\
\text{First} & A & B & C \\
\text{Second} & B & C & A \\
\text{Third} & C & A & B
\end{array}$$

(a) Apply ranked-choice voting. Who wins?
(b) Now suppose the 2 voters who ranked C first change to rank A first instead. Re-run ranked-choice. Who wins now?
(c) Does this demonstrate a monotonicity violation? Explain precisely what changed and why it matters.

**Exercise 11.5** *(Apply Hamilton's method; LO: distribute seats using largest remainders).* Three states have populations 840, 1260, and 1900. There are 40 seats to apportion.

(a) Compute the standard divisor and each state's standard quota.
(b) Apply Hamilton's method to determine the final apportionment.
(c) Now apportion 41 seats using Hamilton's method. Does the Alabama paradox occur? Show your work.

**Exercise 11.6** *(Compare apportionment method biases; LO: connect method choice to who benefits).* The same three states from Exercise 11.5 are apportioned 40 seats under Jefferson's method (use a modified divisor of 98) and Adams's method (use a modified divisor of 107).

(a) Compute the Jefferson apportionment (round all quotas down).
(b) Compute the Adams apportionment (round all quotas up).
(c) Which state benefits most from Jefferson's method? Which benefits most from Adams's? What does this tell you about how method choice functions as a political decision?

### Synthesis

**Exercise 11.7** *(Connect Arrow's theorem to a real-world case; LO: trace the impossibility argument through a specific election).* The 2000 U.S. presidential election in Florida turned on approximately 537 votes out of nearly 6 million cast. Ralph Nader received 97,488 votes; exit polling suggested his voters' second choice was Al Gore by a substantial margin.

(a) Identify which fairness criterion Nader's presence violated.
(b) Name a voting method that would have prevented this specific violation. What fairness criterion does that method sacrifice in exchange?
(c) Does Arrow's theorem guarantee that no voting method could have prevented both this problem and the criterion it sacrifices? Explain.

**Exercise 11.8** *(Apply Balinski-Young to a concrete case; LO: construct a paradox from first principles).* Four states have populations 680, 720, 1400, and 1200. Apportion 20 seats using Hamilton's method. Then apportion 21 seats. Does the Alabama paradox appear? If so, which state is affected and why?

### Challenge

**Exercise 11.9** *(Open-ended synthesis across both impossibility theorems; LO: evaluate the political consequences of method choice).* A city council is redesigning its election system and its process for distributing budget allocations to five districts. They have asked for your recommendation on a voting method and an apportionment method.

Write a one-page recommendation that: (a) names a specific voting method and states which fairness criterion it sacrifices; (b) names a specific apportionment method and states whether it respects the quota rule or avoids paradoxes (it cannot do both); (c) explains, using Arrow's and Balinski-Young's theorems, why there is no recommendation that avoids all trade-offs; and (d) identifies which constituency in the city would be most advantaged and most disadvantaged by your choices.

*There is no correct answer. The quality of your response depends on how honestly it engages with the trade-offs rather than pretending they can be avoided.*

---

## Connections forward

Chapter 12 turns to graph theory. The connection is not decorative. When legislative districts are drawn — the process of dividing a state into geographic units, each sending one representative — the result is a graph: nodes are communities, edges are shared boundaries. Gerrymandering is the deliberate manipulation of that graph to favor one party. Mathematicians now use graph algorithms to test thousands of alternate district maps and determine whether the current map is an outlier — constructed, rather than neutral.

The impossibility theorems from this chapter set the context. Gerrymandering is possible precisely because the choice of district boundaries is itself a political choice that mathematics constrains but does not determine. The same pattern, again: math defines the space of what is possible; politics fills it.
---

## LLM Exercise — Chapter 11: Voting and Apportionment (Audit a Real-World System Project)

**Project:** Audit one real-world system through 13 chapters of mathematics.
**What you're building this chapter:** an analysis of any aggregation, ranking, or apportionment mechanism in the system — voting methods applied, fairness criteria checked, paradoxes surfaced.
**Tool:** **Claude Project** (same system spec as Ch 1).

**The Prompt:**

```
Chapter 11 of my system-audit project. Chapter 11 covered:
voting methods (plurality, majority, plurality-with-runoff,
Borda count, instant-runoff/IRV, Condorcet); fairness
criteria (majority, monotonicity, Condorcet, independence
of irrelevant alternatives); Arrow's impossibility theorem
(no voting method satisfies all four reasonable criteria
simultaneously); apportionment methods (Hamilton, Jefferson,
Webster); apportionment paradoxes (Alabama, population, new
states).

Apply to my system. Most systems aggregate or rank or
allocate something; the rules they pick determine which
outcomes are possible.

1. **Identify one aggregation / ranking / allocation
   mechanism in the system.** Examples:
   - Streaming: the recommendation algorithm (it ranks
     content for you using some implicit voting between
     features).
   - Sports: the playoff seeding system (multiple teams
     compete via scheduled games; ranking aggregates
     game outcomes into a final order).
   - Election: literally a voting system.
   - Restaurant: customer-rating aggregation (5-star
     averages); top-of-menu placement.
   - Hospital: triage scoring (a ranking method that
     allocates limited capacity).
   - Transit: fare zone allocation (an apportionment
     problem if revenue is divided across zones).

2. **Map the system's aggregation method to a textbook
   voting method.** Example: 5-star ratings averaged ≈
   Borda count. A leaderboard based on win count ≈
   plurality across head-to-head contests. An IRV
   election explicitly is IRV.

3. **Run a SECOND voting method on the same data.** Take
   the same input (the same ratings, the same head-to-
   heads, the same ballots) and aggregate it using a
   different method. Does the winner change? How?

4. **Test for fairness-criterion violations.** Pick two
   criteria from the chapter. Check whether the system's
   actual mechanism satisfies them on a recent real case.
   Examples:
   - Independence of irrelevant alternatives: does adding
     a small amount of new content change which of two
     other items the system recommends first?
   - Monotonicity: if a team wins MORE games, can it
     somehow drop in the standings?
   - Majority: can a candidate (or item, or recommendation)
     with 60% support lose to one with 40%?

5. **If the system involves apportionment** (allocating
   limited slots / seats / resources to categories
   proportional to size), apply at least two apportionment
   methods (Hamilton, Webster, Jefferson) to a real
   allocation case. Compare the answers. Identify any
   apportionment paradox that could arise.

6. **Connect to Arrow's theorem.** Identify one concrete
   trade-off the system has chosen. Arrow's theorem
   guarantees the system sacrifices SOMETHING — name what
   it sacrificed and what it preserved.

End with: a one-page "fairness audit" of the system. The
aggregation mechanism. Mapped to a textbook voting method.
A second method's outcome compared. Two fairness criteria
checked. The Arrow trade-off named.
```

**What this produces:** A fairness audit revealing the choices the system has made about what to optimize at the cost of what. Arrow's theorem guarantees something has been sacrificed — naming it is the chapter's point.

**Connection to previous chapters:** Builds on Ch 8 (the data being aggregated has distributions analyzed in Ch 8) and Ch 7 (probabilistic outcomes feed many aggregation systems).

**Preview of next chapter:** Chapter 12 — apply graph theory to the system. Vertices, edges, Euler paths, shortest-path problems, the traveling salesperson. Almost every system can be modeled as a graph; the right model surfaces structural questions the system itself doesn't ask.

---

##  AI Wayback Machine
**Kenneth Arrow** was economist whose 1951 impossibility theorem proved that no voting rule can simultaneously satisfy a short list of seemingly obvious fairness conditions.

![Kenneth Arrow](../images/kenneth-arrow-5fj.png)

*Puppet Art by [Nik Bear Brown](https://www.nikbearbrown.com/).*

**Run this:**

```
Who is Kenneth Arrow, and how does their work connect to voting and apportionment we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Kenneth Arrow"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Kenneth Arrow's ideas to a specific concrete problem in this chapter.
- Add a constraint: "Answer including criticisms or limits of Kenneth Arrow's framework."

What changes? What gets better? What gets worse?
