# Chapter 2 — Logic

## TL;DR

- How to Build an Argument Nobody Can Escape.
- The chapter moves through What counts as a statement, Negation, Compound statements, A concrete case, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

*How to Build an Argument Nobody Can Escape.*

There is a habit of mind that separates people who can argue from people who can only disagree. It is not a talent. It is a technique. And once you see it, you cannot unsee it.

The technique is this: take any claim that can be decided as true or false, give it a name, and then ask what else *must* be true if that claim is. Not might be. Not is likely to be. Must be. That shift — from "probably follows" to "cannot possibly not follow" — is what logic is about. Everything in this chapter lives inside that shift.

---

## What counts as a statement

Start with the simplest possible question: what kinds of sentences can logic even work with?

A **proposition** — logicians sometimes call it a logical statement — is a complete sentence that makes a claim decidable as true or false. Not a question. Not a command. Not a wish. A claim.

"Tiger Woods won the Masters at least five times" is a proposition. It is true. He won in 1997, 2001, 2002, 2005, and 2019.

"All roses are red" is a proposition. It is false. There are pink, white, and yellow roses.

"What time is it?" is not a proposition. Questions cannot be true or false; they are requests. Commands — "Sit down," "Please stop talking" — are not propositions either. Exclamations fall outside too.

The proposition is the atom of logic. Everything else we will do — joining statements, negating them, building arguments out of them — requires that we start with sentences that have definite truth values. They can be unknown to us. They can be contested. But they must be decidable in principle.

| Sentence | right column: "Proposition? (Yes | No) | Why not?" — rows include a statement | a question |
| --- | --- | --- | --- | --- |
| left | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | It makes the underlying reasoning visible instead of implied. | A concrete checkpoint for applying the chapter concept. |

We represent propositions with lowercase letters. Say $p$ is "It is raining in Boston right now." Say $q$ is "The sidewalks are wet." Both are decidable. Neither of us is in Boston, so we do not know their truth values at this moment. That is fine. The sentences still have truth values. We just have not determined them.

This distinction matters. A lot of confusion in arguments — real arguments, not just textbook exercises — comes from treating questions as if they were propositions, or from treating contested claims as if they were undecidable. Logic forces you to be precise about which kind of sentence you are using.

### Negation

The simplest thing you can do to a proposition is reverse it. The **negation** of $p$ is written $\sim p$. Read it "not $p$." If $p$ is true, $\sim p$ is false. If $p$ is false, $\sim p$ is true. The double negation returns you where you started: $\sim(\sim p) = p$.

In English, negation often means inserting or removing "not." "Michael Phelps was an Olympic swimmer" becomes "Michael Phelps was not an Olympic swimmer." Fine.

The tricky cases involve quantifiers — words like *all*, *some*, and *none*. These are the logical words that tell you how many things satisfy a condition.

"All horses are mammals" is true. Its negation is not "No horses are mammals." That would be claiming something much stronger than the negation requires. The negation only has to break the original claim. If I said all horses are mammals and I was wrong, the only thing we can be sure of is that *at least one* horse is not a mammal. We cannot conclude that *none* are.

So: the negation of "All A are B" is "Some A are not B."

And: the negation of "Some A are B" is "No A are B."

And: the negation of "No A are B" is "Some A are B."

| Original quantifier | Original statement form | Negation form | How to read it" — |
| --- | --- | --- | --- |
| All | Some...not, Some | No, No | Some |
| this is the pattern card students will return to when constructing negations on exams | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |

Check each one. If the original is true, the negation must be false. If the original is false, the negation must be true. Run through them and satisfy yourself that these patterns work.

Here is an example to make it concrete. Take three claims:

$p$ = "All eagles are birds."
$q$ = "Some penguins can fly."
$r$ = "No ostriches have long beaks."

$p$ is true. Its negation, $\sim p$, is "Some eagles are not birds" — false, as expected.

$q$ is false. Penguins cannot fly. Its negation, $\sim q$, is "No penguins can fly" — true.

$r$ is false. Ostriches have long beaks. Its negation, $\sim r$, is "Some ostriches have long beaks" — true.

In every case the negation flips the truth value and does nothing more than break the original claim. That is the rule.

---

## Compound statements

Single propositions are not enough to capture how arguments work. Arguments connect claims. "If this, then that." "Either this or that." "Both this and that." To handle these, we need the logical connectives.

There are four main ones.

**AND** — written $\land$ — is the conjunction. $p \land q$ is true only when both $p$ and $q$ are true. If either one fails, the whole thing fails.

**OR** — written $\lor$ — is the disjunction. $p \lor q$ is true when at least one of $p$ or $q$ is true. Both true at once is also fine. The only way the disjunction fails is when both parts fail.

**NOT** — written $\sim$ — is negation, which we have already seen.

**IF...THEN** — written $p \rightarrow q$ — is the conditional. "If $p$, then $q$." This one is worth pausing on, because it behaves in a way that surprises people.

The conditional $p \rightarrow q$ is false in exactly one situation: when $p$ is true and $q$ is false. In every other situation — including when $p$ is false — the conditional is true.

Why? Think of it as a promise. "If it rains, I will carry an umbrella." If it rains and I do not carry an umbrella, I have broken my promise. The conditional is false. But if it does not rain, my promise is not put to the test at all. I have not broken it. And if it rains and I do carry an umbrella, I have kept it. The conditional is true in both the "no rain" cases and the "rain + umbrella" case. It is only false in the "rain, no umbrella" case.

To track truth values for combinations of propositions, we build **truth tables** — a systematic listing of every possible combination of truth values for the component statements, with a column showing the compound result.

For two propositions $p$ and $q$, there are four possible combinations. Here are the main ones:

| $p$ | $q$ | $p \land q$ | $p \lor q$ | $p \rightarrow q$ |
|---|---|---|---|---|
| T | T | T | T | T |
| T | F | F | T | F |
| F | T | F | T | T |
| F | F | F | F | T |

![Version of this truth table with color-coded columns](images/02-logic-fig-01.png)
*Figure 2.1 — Version of this truth table with color-coded columns*

Read the AND column: true only in the top row, where both parts are true. Read the OR column: false only in the bottom row, where both parts fail. Read the IF...THEN column: false only in the second row, where $p$ is true but $q$ is false.

The truth table is not an opinion. It is a mechanical tool. Once you know the connective, the table tells you the truth value of any compound statement for any combination of truth values of its parts. You do not need to think about what the sentences mean. You only need to know whether each component is true or false.

That is the power of formal logic. Once an argument is in symbolic form, evaluation becomes mechanical.

### A concrete case

Let $p$ = "The store opens at 9am" and $q$ = "The store is open on Sundays." You are standing outside at 9am on a Sunday.

If both are true, $p \land q$ is true. The store should be open.

If $p$ is true but $q$ is false, $p \land q$ is false. The time is right; the day is wrong. You wait for nothing.

If you only have the OR claim — "The store opens at 9am or it opens on Sundays" — and you are there at 9am on a Sunday, you know the disjunction is true. You have satisfied at least one condition, possibly both. Whether the store is actually open depends on whether the disjunction accurately reflects the store's policy.

This seems obvious when we say it in plain English. The machinery becomes important when the sentences are complex and the argument has twenty steps. At that point you cannot hold the whole thing in your head. The truth table can.

---

## Valid arguments

Now we can talk about what logic really is for: deciding whether an argument is valid.

A **valid argument** is one where, if all the premises are true, the conclusion must be true. The conclusion follows necessarily. There is no possible situation where the premises are all true and the conclusion is false.

Notice what I did not say. I did not say the premises are actually true. An argument can be valid with false premises. I will come back to this.

The most basic valid argument form is the **law of detachment**, also called *modus ponens*:

- Premise 1: $p \rightarrow q$
- Premise 2: $p$
- Conclusion: $q$

Here is why it is valid. Look at the truth table for the conditional. The only row where $p \rightarrow q$ is false is the second one, where $p$ is true and $q$ is false. If premise 1 tells us $p \rightarrow q$ is true, we eliminate that row. If premise 2 tells us $p$ is true, we eliminate the rows where $p$ is false — the third and fourth rows. What remains is only the first row: $p$ is true, $q$ is true. The conclusion is forced.

In plain English: "If it rains, the game is cancelled. It is raining. Therefore, the game is cancelled." If you accept both premises, you cannot deny the conclusion without contradicting yourself.

There is a trap here that many people fall into, and it is important enough to name. The trap is called **affirming the consequent**:

- Premise 1: $p \rightarrow q$
- Premise 2: $q$
- (Invalid) Conclusion: $p$

"If it rains, the game is cancelled. The game is cancelled. Therefore, it rained." This seems convincing until you think of alternatives. Maybe the coach got sick. Maybe the field flooded from a burst pipe. Maybe the visiting team's bus broke down. The game being cancelled does not prove rain. The argument is invalid.

The truth table shows why. When $p \rightarrow q$ is true and $q$ is true, $p$ can be either true (row 1) or false (row 3). We cannot determine $p$ from these premises. The conclusion does not follow.

### A second valid form

The **law of denying the consequent**, also called *modus tollens*:

- Premise 1: $p \rightarrow q$
- Premise 2: $\sim q$
- Conclusion: $\sim p$

"If it rains, the game is cancelled. The game was not cancelled. Therefore, it did not rain."

This is valid. Check it against the truth table. When is $p \rightarrow q$ true and $q$ is false? Only in the fourth row, where $p$ is also false. So knowing the conditional is true and knowing $q$ is false forces $p$ to be false.

Intuitively: the conditional says that rain brings cancellation. If there is no cancellation, there was no rain. This contrapositive direction is just as tight as the forward direction.

### Chaining arguments

A third form is the **chain rule** — also called *hypothetical syllogism*:

- Premise 1: $p \rightarrow q$
- Premise 2: $q \rightarrow r$
- Conclusion: $p \rightarrow r$

"If I study, I will pass. If I pass, I will graduate. Therefore, if I study, I will graduate."

This is valid. The chain can be extended indefinitely. Every legal syllogism, every multi-step mathematical proof, every piece of reasoning with more than one "if-then" is using this form.

| Name | Symbolic form (premises → conclusion) | Plain-English template" — |
| --- | --- | --- |
| Law of Detachment (modus ponens | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| Law of Denying the Consequent (modus tollens | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| Chain Rule (hypothetical syllogism | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| plus a fourth row for the INVALID form "Affirming the Consequent" marked in red or with a ✗ | student should be able to scan this table and identify which form any given argument uses | A concrete checkpoint for applying the chapter concept. |

### Validity versus truth

I said earlier that validity and truth are different things, and this is worth sitting with.

Consider: "If the Earth is flat, gravity points upward. The Earth is flat. Therefore, gravity points upward."

This argument is **valid**. If you accepted both premises, you would have to accept the conclusion. The form is law of detachment. But the premises are false, so the conclusion is unreliable. A valid argument with false premises proves nothing about the world.

An argument that is both valid and has all true premises is called **sound**. A sound argument guarantees a true conclusion. Logic alone gives you validity; knowledge of the world gives you soundness. You need both.

This distinction is why evidence matters alongside logic. Marshall's argument in *Brown v. Board* was not convincing because the form was right. It was convincing because the premises were supported by evidence — testimony, statistics, expert analysis — that made them credible. The logic made the chain of reasoning ironclad. The evidence made the premises worth believing.

---

## Logical equivalence and De Morgan's Laws

Two statements are **logically equivalent** if they have the same truth value in every possible case. Logical equivalence means the two statements carry exactly the same information, even if they look different.

The deepest equivalence in this chapter connects the conditional to the disjunction:

$$p \rightarrow q \equiv \sim p \lor q$$

"If $p$, then $q$" says the same thing as "either not-$p$, or $q$." Check: the conditional $p \rightarrow q$ is false only when $p$ is true and $q$ is false. The disjunction $\sim p \lor q$ is false only when $\sim p$ is false (meaning $p$ is true) and $q$ is false. Same condition. They are equivalent.

This equivalence is not just a curiosity. It is a tool. Sometimes an "if-then" is hard to reason about and a disjunction is easier, or vice versa. Knowing they are the same means you can switch freely.

The other essential equivalences are **De Morgan's Laws**:

$$\sim(p \land q) \equiv \sim p \lor \sim q$$

$$\sim(p \lor q) \equiv \sim p \land \sim q$$

Read the first one: "It is not the case that both $p$ and $q$" means the same thing as "either not-$p$ or not-$q$." If it is false that I both studied and passed, then at least one of those things did not happen: either I did not study, or I did not pass.

Read the second one: "It is not the case that either $p$ or $q$" means the same thing as "not-$p$ and not-$q$." If it is false that I either studied or passed, then I did not study and I did not pass. Both failed.

These laws have a satisfying symmetry. Negation distributes across AND and OR, and when it does, the connective flips: AND becomes OR, OR becomes AND.

![Visual of the two De Morgan transformations ](images/02-logic-fig-02.png)
*Figure 2.2 — Visual of the two De Morgan transformations *

This is the same duality that appeared in Chapter 1 with sets. The complement of a union is the intersection of complements: $(A \cup B)' = A' \cap B'$. De Morgan for sets. The same pattern appears here in logic. De Morgan for propositions. The algebra is identical; only the notation changes.

### Applying De Morgan

Suppose someone tells you: "It is not the case that both Alice and Bob showed up."

Let $p$ = "Alice showed up" and $q$ = "Bob showed up." The claim is $\sim(p \land q)$.

By De Morgan: $\sim(p \land q) \equiv \sim p \lor \sim q$. So the claim is equivalent to "Alice did not show up, or Bob did not show up." At least one of them is absent. You cannot conclude which one — maybe it was Alice, maybe Bob, maybe both. But you know at least one is missing.

This kind of rewriting matters in practice. A sentence full of nested negations — "it is not the case that neither X nor Y is true" — is almost impossible to parse directly. De Morgan lets you strip the nesting, layer by layer, until you have something readable.

---

## The courtroom argument, completed

Return to where the chapter started — the idea that some arguments hold and others fall apart. Here is the clearest example I know.

In 1954, Thurgood Marshall argued *Brown v. Board of Education* before the Supreme Court. His argument in schematic form:

- Premise 1: Education is vital to citizens in a democratic society.
- Premise 2: Separate educational facilities are not equal.
- Premise 3: If separate facilities are not equal, then segregation in schools violates the equal protection of the law.
- Conclusion: Segregation in schools violates the equal protection of the law.

![Linear argument-chain diagram for the Brown v](images/02-logic-fig-03.png)
*Figure 2.3 — Linear argument-chain diagram for the Brown v*

The form is chain rule plus law of detachment. Premises 1 and 2 establish the facts. Premise 3 connects those facts to a legal conclusion. The conclusion follows necessarily from the premises. If you accept all three premises, you cannot deny the conclusion without contradicting yourself. There is no logical escape.

The Court could not escape. Nine justices, unanimously, accepted the premises and were forced by the logic to accept the conclusion. *Brown* was decided 9-0.

I am not saying the decision was automatic. The justices deliberated. The legal history is complicated. But the logical structure of the argument was unassailable, and that structure was part of why. A valid argument with credible, evidence-backed premises is the hardest thing in the world to defeat.

That is what this chapter teaches. Not to win arguments by volume or persistence. To construct chains of reasoning that hold — that leave no logical exit for someone who accepts your premises.

---

## Chapter summary

A logical proposition is a sentence with a definite truth value. You can negate it, join it with AND or OR, and build conditionals out of it. Truth tables track all possible combinations of truth values for compound statements. Valid argument forms — law of detachment, law of denying the consequent, chain rule — guarantee conclusions from premises. Logical equivalences, including De Morgan's Laws, let you rewrite statements without changing their content.

The one idea that matters most: validity is a property of form, not content. An argument is valid if its form guarantees the conclusion from the premises, regardless of what the premises are about. Once you understand that, you can evaluate any argument — in law, in mathematics, in everyday life — by examining its structure. You do not have to be an expert in the subject. You only have to see the bones.

The mistake to watch for: confusing validity with soundness. A valid argument with false premises tells you nothing about the world. Always ask: is the form valid, and are the premises actually true? Only when both answers are yes do you have something that forces a conclusion about reality.

The Feynman test: can you explain to someone who has never seen logic before why affirming the consequent is invalid? If you can — if you can show them the truth table and walk them through the rows where the premises are all true but the conclusion is false — you understand this chapter.

---

## Connections forward

Chapter 3 begins with numbers, but every proof in mathematics is a logical argument. The machinery you have here — premises, valid forms, conditional reasoning — is what proofs are made of. You will use it without thinking about it, the way you use grammar when you write.

Chapter 7 on probability is logic dressed in degrees. Instead of "true" and "false," you will work with likelihoods. But the structure of conditional reasoning — "given that $p$, how does the probability of $q$ change?" — is the same structure you learned here.

And every chapter that asks you to evaluate a claim — statistical, geometric, graph-theoretic — is asking you to check whether a conclusion follows from premises. This chapter is not one tool among many. It is the tool the other tools assume.

---

## Exercises

### Warm-up

**Exercise 2.1** *(Identify statements; LO: proposition recognition).* Classify each sentence as a logical proposition or not. For those that are propositions, state their truth value if determinable; otherwise explain why it cannot be determined from the sentence alone.

(a) "The Pacific Ocean is the largest ocean on Earth."
(b) "Please close the door."
(c) "Is it cold outside?"
(d) "No prime number is divisible by 4."
(e) "This sentence is false."

*Difficulty: low. The last item is a deliberate trap — you are not expected to resolve it, only to explain what makes it unusual.*

**Exercise 2.2** *(Negate propositions; LO: negation of simple and quantified statements).* Write the negation of each statement in plain English and in symbolic form. State whether the negation is true or false, and explain briefly.

(a) $p$ = "All U.S. presidents have been born in the United States."
(b) $q$ = "Some birds cannot fly."
(c) $r$ = "No mammal lays eggs."

**Exercise 2.3** *(Compound statements from connectives; LO: translation between English and symbolic form).* Let $p$ = "The library is open" and $q$ = "The book is available."

(a) Write $p \land q$ in English.
(b) Write $p \lor \sim q$ in English.
(c) Write $\sim(p \land q)$ in English, first directly and then using De Morgan's Law.

### Application

**Exercise 2.4** *(Truth table construction; LO: evaluate compound statements).* Construct a complete truth table for $\sim p \lor q$. In which rows is the statement false? What familiar connective does this truth table match?

**Exercise 2.5** *(Conditional reasoning; LO: law of detachment and its limits).* For each pair of premises, either state the valid conclusion or explain why no valid conclusion follows.

(a) Premise 1: "If a figure is a square, then it is a rectangle." Premise 2: "This figure is a square."
(b) Premise 1: "If a figure is a square, then it is a rectangle." Premise 2: "This figure is a rectangle."
(c) Premise 1: "If a figure is a square, then it is a rectangle." Premise 2: "This figure is not a square."

*Note: (b) and (c) are traps. Name the invalid form if one appears.*

**Exercise 2.6** *(De Morgan's Laws; LO: rewrite statements using logical equivalence).* Apply De Morgan's Law to rewrite each statement without the phrase "it is not the case that."

(a) "It is not the case that both the train is on time and the bus is running."
(b) "It is not the case that either the café is open or the restaurant is open."
(c) "It is not the case that some students both studied hard and failed the exam." *(Careful — this one requires translating the quantifier first.)*

### Synthesis

**Exercise 2.7** *(Chain rule; LO: multi-step conditional argument).* A doctor's reasoning: "If a patient has fever and chills, then the patient may have an infection. If the patient may have an infection, then a blood test is warranted. If a blood test is warranted, then we should order one today."

The patient has fever and chills.

(a) Translate the three conditionals into symbolic form, defining your propositions clearly.
(b) Apply the chain rule to derive the final conclusion.
(c) Is the argument valid? Is it sound? Explain the difference in this context.

**Exercise 2.8** *(Validity check by truth table; LO: distinguish valid from invalid forms).* The following argument appears in a political debate: "If the new policy reduces crime, then it is worth implementing. Crime has been reduced. Therefore, the new policy is worth implementing."

(a) Identify the form of this argument.
(b) Construct or reference the relevant rows of the conditional truth table to determine whether the argument is valid.
(c) What additional information would you need to determine whether the argument is *sound*?

### Challenge

**Exercise 2.9** *(Verify logical equivalence by truth table; LO: De Morgan's Laws from first principles).* Construct a complete truth table to verify that $\sim(p \land q) \equiv \sim p \lor \sim q$. Your table should include columns for $p$, $q$, $\sim p$, $\sim q$, $p \land q$, $\sim(p \land q)$, and $\sim p \lor \sim q$. Confirm that the last two columns are identical in every row. Then write a one-sentence explanation, in plain English, of why this equivalence holds.

**Exercise 2.10** *(Open-ended; LO: construct and evaluate a real argument).* Find a short argument in a newspaper editorial, a legal decision summary, or a public speech transcript. Identify at least two premises and a conclusion. Translate the argument into symbolic form. Determine whether the argument form is valid. If it is invalid, name the fallacy. If it is valid, assess whether the premises are credible enough to make it sound.

*This exercise has no single correct answer. The quality of your response depends on how precisely you identify the premises, how accurately you translate them into symbolic form, and how honestly you evaluate the argument.*

---

---

## LLM Exercise — Chapter 2: Logic (Audit a Real-World System Project)

**Project:** Audit one real-world system through 13 chapters of mathematics.
**What you're building this chapter:** a logical analysis of the system's if-then rules — which are valid, which are invalid, where the stated logic and the actual behavior diverge.
**Tool:** **Claude Project** (same system spec as Ch 1).

**The Prompt:**

```
Chapter 2 of my system-audit project. Chapter 2 covered:
propositions; truth tables; conjunction (AND), disjunction (OR),
negation (NOT), conditional (IF...THEN); valid vs. invalid
arguments; affirming the consequent and denying the antecedent
as classic fallacies.

Apply to my system (use the spec from Ch 1):

1. **Identify three logical rules the system runs on.** These
   are usually if-then statements. Examples:
   - Transit: "IF you tap a card with insufficient balance,
     THEN the gate stays closed."
   - Streaming: "IF you have a Premium subscription AND you
     are in the US, THEN you can access 4K content."
   - Hospital: "IF the patient's pain score is ≥ 7, THEN
     they are seen within 30 minutes."
   For each rule, write it down precisely.

2. **Formalize each rule.** Assign propositional variables
   (p, q, r) to the simple statements. Write the rule in
   symbolic form using ∧, ∨, ∼, →. Construct the truth
   table. Identify the rows that make the rule TRUE and the
   rows that make it FALSE.

3. **Test for consistency.** For each rule, identify a real
   case (or a hypothetical that could realistically occur)
   that would violate the rule. Did the rule correctly
   classify that case?

4. **Find one invalid argument the system implicitly makes.**
   Most real systems contain at least one rule that LOOKS
   logical but isn't. Common patterns:
   - Affirming the consequent: "IF eligible THEN approved.
     This person was approved. THEREFORE this person was
     eligible." (Wrong — they could have been approved by
     mistake.)
   - Denying the antecedent: "IF you pay full fare THEN you
     get a transfer. You didn't pay full fare. THEREFORE
     you don't get a transfer." (Wrong — you might still
     get one through a different path.)
   Identify one such fallacy embedded in the system you're
   auditing. Show the truth table that proves it's invalid.

5. **Apply De Morgan to one system rule.** Take a rule with
   AND or OR and write its negation correctly. (Example:
   "service is interrupted when there's a delay AND a
   cancellation" → negation: "service is NOT interrupted
   when there's no delay OR no cancellation.") Note where
   the system's plain-English exception language is
   ambiguous between these.

End with: a one-page "logical audit" of the system. Three
rules formalized. One invalid argument identified. One De
Morgan application showing where the system's language is
ambiguous.
```

**What this produces:** A logical audit identifying where the system's stated rules are valid, where they leak, and where the language is ambiguous. Builds directly on the Ch 1 system spec.

**Connection to previous chapters:** Direct — uses the Ch 1 system spec. The set-theoretic groupings from Ch 1 often correspond to the propositions you'll formalize here.

**Preview of next chapter:** Chapter 3 — apply prime factorization, GCD, and LCM to the numerical patterns hiding in the system (scheduling cycles, billing periods, packet sizes, batch sizes). Most systems have hidden divisibility structure; this chapter surfaces it.

---

##  AI Wayback Machine
**George Boole** was developed Boolean algebra in 1854 — turning logic into mathematics. Every modern computer reasons in Boole's framework.

**Run this:**

```
Who is George Boole, and how does their work connect to logic we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"George Boole"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply George Boole's ideas to a specific concrete problem in this chapter.
- Add a constraint: "Answer including criticisms or limits of George Boole's framework."

What changes? What gets better? What gets worse?
