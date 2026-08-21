# Chapter 8 — Statistics

## TL;DR

- Two Million Wrong Answers, and How to Get a Thousand Right Ones.
- The chapter moves through Where data come from, The story in the middle, Spread: the story the mean cannot tell, The shape of the data, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

*Two Million Wrong Answers, and How to Get a Thousand Right Ones.*

In October 1936, the most prestigious polling organization in the United States announced its prediction for the presidential election: Alf Landon would defeat Franklin Roosevelt by eighteen percentage points. The organization was the *Literary Digest*. It had correctly predicted every presidential election since 1916. It had surveyed two million people — the largest poll in American history to that point.

Roosevelt won by eighteen percentage points in the other direction.

The *Digest* had polled from three lists: its own subscribers, telephone directories, and automobile registration records. All three, in 1936, were lists of wealthy people. The magazine was polling during the Great Depression, in an election that turned almost entirely on whether you had survived it. The poor and working-class voters who adored Roosevelt were not on any of those lists. Two million responses from the wrong population are worth less than a hundred responses from the right one.

This is the lesson that carries through everything in this chapter. Statistics is not about collecting large amounts of data. It is about collecting *honest* data, describing it accurately, and knowing what you can and cannot conclude from it. Get any of those three things wrong and the numbers will deceive you — or, if someone else controls the numbers, they will use them to deceive you.

---

## Where data come from

The *Digest* had a **sampling** problem. It needed to know what the voting population thought, but it could not ask all voters. No one ever can. So it chose a sample — a subset meant to represent the whole. And the sample was wrong, not because it was too small, but because the method of choosing it introduced a systematic tilt toward one kind of person.

The principle here is simple but important: a sample is valid only if every member of the population had a fair and equal chance of being included. When that is true, the sample is called **random**, and random samples have a beautiful property — they tend to look like the population they came from, including its diversity, its spread, its center.

The main sampling methods are distinguished by how they achieve (or fail to achieve) this:

A **simple random sample** gives every member of the population an equal probability of selection. You have a list of all voters; a random number generator picks 1,500 of them. No human judgment involved. No systematic tilt. This is the gold standard.

A **systematic random sample** takes every $k$th item from an ordered list, starting at a randomly chosen point. If you want a 2% sample of a list of 10,000 names, you pick a random start between 1 and 50, then take every 50th name. This works well unless the list itself has a periodic pattern — say, if every 50th entry happens to be a department head.

A **stratified sample** divides the population into groups — income brackets, age groups, geographic regions — and randomly samples within each group. The *Digest* should have done this. Had they stratified by income and sampled randomly within each income bracket, Roosevelt's supporters would have had equal representation. They did not.

A **cluster sample** selects entire clusters at random — five city blocks, twenty classrooms, a dozen precincts — and surveys everyone in the selected clusters. Convenient for surveys that must be conducted in person. Risky if the clusters are not themselves representative.

The worst option, the one responsible for most bad polling, is the **convenience sample** — asking whoever is available. Stand at a street corner, call whoever answers their phone at 6pm, email your subscriber list. You will systematically miss everyone who is not there. The missed people are rarely missing at random.

| Method | How it works | Key strength | Key risk | failure mode" — |
| --- | --- | --- | --- | --- |
| simple random, systematic random, stratified, cluster, convenience | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | The pattern becomes easy to misuse or overlook. |
| the convenience row should be visually flagged (e.g., shaded or marked with a warning symbol) to signal it is not a valid random method | student should be able to scan this and immediately identify which method the Literary Digest used and why it failed | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | The pattern becomes easy to misuse or overlook. |

There is a second failure mode, subtler than a bad list: **non-response bias**. Even with a random sample, if only some people respond, you have a problem. The people who answer political surveys are not the same as the people who hang up. The ones who respond may feel more strongly, more informed, more angry, or more at leisure. Whatever systematically distinguishes responders from non-responders will show up in your data as a distortion.

The *Digest* sent ten million surveys. Two million came back. Even if the original list had been perfect, a 20% response rate from an unknown subset is a serious problem. When you see a poll, the first question to ask is not how many people were surveyed — it is how they were chosen, and whether there is any reason to think the sample is tilted.

---

## The story in the middle

Once you have honest data, you need to describe it. And the first question is: what is the *center*?

There are three answers to that question, and they are not interchangeable.

The **mean** is the sum of all values divided by how many there are. If a basketball league has ten players with salaries of 90, 90, 95, 100, 102, 105, 110, 115, 120, and 190 (in thousands of dollars), the mean salary is $\frac{90 + 90 + 95 + 100 + 102 + 105 + 110 + 115 + 120 + 190}{10} = \frac{1117}{10} = 111.7$ thousand dollars. The mean is $111,700.

The **median** is the middle value when the data are sorted. With ten values, the median is the average of the fifth and sixth: $\frac{102 + 105}{2} = 103.5$ thousand dollars. The median is $103,500.

The mean is higher than the median by about $8,000. Why? Because the player earning $190,000 pulls the mean upward. The mean is sensitive to extreme values; it gets tugged toward outliers. The median does not care about the outlier's exact value — it only cares that one value is above the middle and one is below.

The **mode** is the most frequently occurring value. In this dataset, $90,000 appears twice and nothing else does, so the mode is $90,000. The mode answers the question: if I pick a random data point, what am I most likely to see?

These three measures answer three different questions. The mean answers: if you split the total equally, what does each person get? The median answers: what does the person in the middle earn? The mode answers: what is the most common value?

| Measure | What it computes | The question it answers | When to use it | Sensitive to outliers?" — |
| --- | --- | --- | --- | --- |
| mean, median, mode | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| the basketball salary dataset (90, 90, 95, 100, 102, 105, 110, 115, 120, 190) runs as a worked column alongside each row showing the computed value | student should see at a glance why the mean ($111.7K) and median ($103.5K) diverge and what that gap means | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |

The choice between them is not arbitrary. It depends on what you are trying to communicate — and on whether the data are symmetric or skewed.

If income data are **skewed right** — most people earn modest salaries, but a few earn enormous ones — the mean gets pulled up by the high earners and overstates what a typical person earns. The median is more honest. This is why median household income is always reported in economics: a small number of very wealthy households would inflate the mean into a number that most families cannot recognize as representing their experience.

If you see a data summary that uses the mean where the data are skewed, ask why. Sometimes it is honest (the mean really is what the question requires). Sometimes it is chosen precisely because it makes the number larger, or smaller, than the typical experience.

### Spread: the story the mean cannot tell

Two classes both have a mean test score of 80. In class A, every student scored between 75 and 85. In class B, half scored 100 and half scored 60. The same mean describes two entirely different situations. To distinguish them, you need a measure of **spread**.

The simplest is the **range**: the difference between the highest and lowest values. Class A's range is 10. Class B's range is 40. But the range depends entirely on the two extreme values, and a single outlier can make it misleading.

The more informative measure is the **standard deviation** — the average distance of data points from the mean. Its formula is:

$$s = \sqrt{\frac{\sum (x - \bar{x})^2}{n - 1}}$$

Read this step by step. Take each value $x$. Subtract the mean $\bar{x}$. Square the result (so negative differences count the same as positive ones). Add them all up. Divide by $n - 1$ (not $n$ — a technical correction that makes the estimate better for small samples). Take the square root to undo the squaring and return to the original units.

For the three scores 75, 80, 85 (mean = 80): the differences are $-5, 0, 5$. Squared: $25, 0, 25$. Sum: 50. Divided by $n - 1 = 2$: 25. Square root: 5. Standard deviation is 5. Roughly speaking, a typical score is about 5 points from the mean.

The standard deviation has a feel once you work with it. A low standard deviation means the data cluster tightly around the mean — consistent, predictable. A high standard deviation means the data scatter widely — diverse, variable, possibly with outliers driving the spread. Two datasets with the same mean can have entirely different stories, and the standard deviation is what tells you which story you are in.

![Dot plots for two datasets with the same](images/08-statistics-fig-01.png)
*Figure 8.1 — Dot plots for two datasets with the same*

---

## The shape of the data

A mean and standard deviation describe two features of a dataset. The **histogram** — a bar chart where each bar represents the count of values in a range — shows the whole shape. And the shape matters.

Some datasets produce a symmetric, bell-shaped histogram. This shape is common enough in nature and measurement that it has a name: the **normal distribution**. Heights of adults in a population. Birth weights. SAT scores. The measurement error in repeated careful measurements of the same thing. Many processes that result from the sum of many independent small random effects produce, in the limit, this bell curve.

The normal distribution is worth understanding deeply because of one remarkable fact: if you know the mean and the standard deviation of a normally distributed dataset, you know almost everything about it.

Specifically, the **68-95-99.7 rule** tells you:

- 68% of values fall within one standard deviation of the mean
- 95% fall within two standard deviations
- 99.7% fall within three standard deviations

![Bell curve diagram ](images/08-statistics-fig-02.png)
*Figure 8.2 — Bell curve diagram *

Adult male heights in the United States are approximately normally distributed with mean 70 inches and standard deviation 2.5 inches. The rule tells us immediately: 68% of men are between 67.5 and 72.5 inches tall. 95% are between 65 and 75 inches. 99.7% are between 62.5 and 77.5 inches. If you meet a random man, there is less than a 0.3% chance he is shorter than 5'2.5" or taller than 6'5.5".

The rule is not just a memory device. It encodes the geometry of the normal distribution — the way probability mass concentrates around the mean and tapers in both directions.

Not every dataset is normal, and assuming normality when the data are skewed or bimodal is a common error. Always look at the histogram before applying the rule. If the histogram is skewed — heaped toward one side with a long tail toward the other — the normal distribution's rules do not apply, and the mean has been pulled toward the tail away from where most of the data live.

---

## Z-scores: measuring relative position

The 68-95-99.7 rule answers a question about the whole population. But sometimes you want to know about one individual: *where does this person stand relative to everyone else?*

That is what a **z-score** tells you.

$$z = \frac{x - \mu}{s}$$

Take a value $x$. Subtract the mean $\mu$ (mu). Divide by the standard deviation $s$. The result is how many standard deviations above or below the mean the value sits.

A z-score of 0 means the value is exactly at the mean. A z-score of 1 means one standard deviation above. A z-score of $-2$ means two standard deviations below.

Here is why this is useful. Suppose a student scores 1450 on the SAT and 29 on the ACT. The SAT and the ACT are different tests with different scales. You cannot directly compare 1450 and 29. But you can compare their z-scores.

The SAT has mean 1060 and standard deviation 195. The z-score for 1450 is $\frac{1450 - 1060}{195} = \frac{390}{195} = 2.0$. Two standard deviations above the mean.

The ACT has mean 21 and standard deviation 5. The z-score for 29 is $\frac{29 - 21}{5} = \frac{8}{5} = 1.6$. One-point-six standard deviations above the mean.

Both scores are excellent. But the SAT score, at z = 2.0, is at a higher percentile than the ACT score at z = 1.6. By the 68-95-99.7 rule, 95% of test-takers score within two standard deviations of the mean — so a z-score of 2.0 places a student near the 97th or 98th percentile. A z-score of 1.6 is around the 94th or 95th percentile. The SAT score is stronger relative to peers.

The z-score does one clean thing: it converts any normally distributed measurement into a common language — the language of standard deviations from the mean — so that a height, a test score, a salary, and a marathon time can all be placed on the same scale and compared.

![Two side-by-side normal distribution curves ](images/08-statistics-fig-03.png)
*Figure 8.3 — Two side-by-side normal distribution curves *

---

## From data back to the poll

Return to the telephone poll from the opening of the chapter. A polling firm surveys 1,500 randomly selected voters and finds that 52% say they support candidate A. They report a margin of error of ±3 percentage points at 95% confidence.

What does that mean, exactly?

The 1,500 people surveyed are a sample. The true population percentage — what all 200 million eligible voters actually think — is unknown. The polling firm is using the sample to estimate that unknown quantity.

Here is the logic. If the sampling is truly random, the sample percentage tends to be close to the population percentage. How close? That depends on the sample size and the variability in the population. The normal distribution, applied to the distribution of possible sample percentages from many such surveys, tells us the answer: there is a band around the sample percentage within which the true population percentage is likely to fall.

At 95% confidence, that band is approximately ±3 percentage points for a sample of 1,500 — which is where the margin of error comes from.

"95% confidence" does not mean there is a 95% chance the true value is in the interval. It means: if we drew many random samples of 1,500 and computed this interval each time, 95% of those intervals would contain the true population value. It is a statement about the method, not about this particular interval.

Three things affect the width of the margin of error. A larger sample produces a narrower margin — more data, more confidence. A more divided population (say, 50-50 rather than 90-10 on an issue) produces a wider margin — more variability, harder to pin down. A higher desired confidence level (99% instead of 95%) produces a wider margin — you need more room to be more certain.

| Factor | If it increases |
| --- | --- |
| sample size (larger → narrower margin | A concrete checkpoint for applying the chapter concept. |
| population variability (more divided → wider margin | A concrete checkpoint for applying the chapter concept. |
| confidence level (higher % → wider margin | A concrete checkpoint for applying the chapter concept. |
| the poll example (n=1500, ±3%, 95%) runs as a concrete anchor in the rightmost column | student should be able to read this table and immediately explain why "just survey more people" is not always the right answer |

The 68-95-99.7 rule reappears here, naturally. A margin of error at 95% confidence corresponds to approximately two standard deviations of the sampling distribution. A margin at 68% confidence would be one standard deviation; at 99.7%, three. The normal distribution is not just a description of heights and test scores. It is the foundation underneath every poll, every clinical trial, every quality-control measurement — anywhere we use a sample to estimate a population.

---

## Chapter summary

Data is not just numbers. It is numbers produced by a method, and the method determines whether the numbers can be trusted.

A biased sample — one drawn from a population that does not represent the whole — produces a biased estimate, regardless of how many responses you collect. The *Literary Digest* failed not because it was small but because it was wrong. Random sampling is the only defense against systematic bias.

Once you have honest data, the mean, median, and mode each answer a different question. The median is the honest choice when the data are skewed; the mean is appropriate when you need to account for the total. The standard deviation tells you how spread out the data are — the story the mean leaves out.

When data follow a normal distribution, the 68-95-99.7 rule lets you read the entire distribution from just two numbers. And z-scores let you compare values from different populations by translating everything into the language of standard deviations from the mean.

The margin of error is not a guess. It is a direct consequence of the normal distribution applied to sampling: a quantified statement of how much the sample estimate might differ from the true population value, at a stated level of confidence.

The mistake to watch for is the one the *Digest* made, and the one bad statistics always makes: confusing the sample for the population. Asking only people who answer phones. Reporting only the mean when the median is lower. Quoting a poll without its margin of error. The numbers are honest only if the method is. Your job, going forward, is to ask about the method every time.

The Feynman test for this chapter: can you explain to someone why two million biased responses are less trustworthy than a thousand random ones? If you can — if you can show them what "random" actually means and why it is the only thing that prevents systematic distortion — you understand what statistics is for.

---

## Exercises

### Warm-up

**Exercise 8.1** *(Classify sampling methods; LO: identify sources of bias).* A school wants to survey student opinion on a new cafeteria menu. For each method below, name the sampling type and identify one specific source of bias.

(a) The principal asks for volunteers to fill out a survey during lunch.
(b) A random number generator selects 60 student ID numbers from the school roster.
(c) Five homeroom classes are chosen at random; every student in those classes is surveyed.
(d) Students are divided by grade level; 15 are randomly selected from each grade.

**Exercise 8.2** *(Compute and interpret measures of center; LO: choose the right measure for the question).* The annual salaries (in thousands) at a seven-person startup are: 45, 48, 50, 52, 55, 60, 210.

(a) Compute the mean, median, and mode.
(b) Which measure best represents a typical employee's salary? Explain why.
(c) The CEO reports "the average salary here is \$74,286." Is this misleading? What would you report instead?

**Exercise 8.3** *(Interpret standard deviation; LO: read spread as a story).* Two hospitals report the same mean patient wait time of 40 minutes. Hospital A has a standard deviation of 5 minutes. Hospital B has a standard deviation of 25 minutes. What does this tell you about the patient experience at each hospital? Which would you prefer to use in an emergency, and why?

### Application

**Exercise 8.4** *(Apply the 68-95-99.7 rule; LO: use the normal distribution to estimate proportions).* A standardized test is normally distributed with mean 500 and standard deviation 80. Without a calculator, estimate:

(a) The percentage of test-takers who score between 420 and 580.
(b) The percentage who score above 660.
(c) The score below which approximately 2.5% of test-takers fall.

*Show which part of the 68-95-99.7 rule you are applying for each.*

**Exercise 8.5** *(Compute and compare z-scores; LO: use z-scores to compare across populations).* A student earns 88 points on a chemistry exam (class mean 78, standard deviation 6) and 72 points on a history exam (class mean 65, standard deviation 10).

(a) Compute the z-score for each exam.
(b) On which exam did the student perform better relative to classmates? Explain.
(c) What percentile (approximately) does each z-score correspond to, using the 68-95-99.7 rule?

**Exercise 8.6** *(Interpret a margin of error; LO: read polling results correctly).* A poll reports that 47% of voters support a ballot measure, with a margin of error of ±4 percentage points at 95% confidence.

(a) State the confidence interval.
(b) Can you conclude the measure is likely to pass? Explain.
(c) A different poll of the same population finds 51% support, with the same margin of error. Are the two polls in conflict? Why or why not?

### Synthesis

**Exercise 8.7** *(Connect sampling to margin of error; LO: understand what affects polling precision).* A polling firm wants to reduce its margin of error from ±4% to ±2% while maintaining 95% confidence. What must it do? Name two distinct ways the firm could achieve this reduction and explain the trade-off each involves.

**Exercise 8.8** *(Evaluate a real statistical claim; LO: identify bias and misleading summaries).* A gym advertises: "Our members lose an average of 18 pounds in their first three months." They gathered this data by surveying members who had completed a full three-month program.

Identify three distinct sources of bias in this claim. Then describe what an honest study would look like — how would you redesign the data collection to produce a trustworthy number?

### Challenge

**Exercise 8.9** *(Construct and critique an argument from data; LO: integrate all chapter concepts).* A researcher compares two high schools. School A uses a new reading curriculum; School B uses the traditional one. After one year, School A students have a mean reading score of 74 (standard deviation 9, $n = 120$). School B students have a mean of 71 (standard deviation 14, $n = 95$).

(a) Compute the z-score for a School A student who scored 83 and a School B student who scored 85. Which score is relatively stronger?
(b) Does the difference in mean scores prove the new curriculum is more effective? List two confounding factors that might explain the difference without the curriculum causing it.
(c) What would a better study design look like?

**Exercise 8.10** *(Open-ended; LO: transfer to a novel claim).* Find a statistical claim in a news article, advertisement, or public report — one that cites a number, a percentage, or a survey result. Write a one-page critique that addresses: How was the data collected? Is the sampling method described, and is it random? Is the measure of center appropriate for the data? Is a margin of error reported? What would you need to know before trusting the claim?

*There is no single correct answer. The quality of your response depends on the precision of your critique and the specificity of your evidence.*

---

Chapter 7 on probability showed you the mathematics of what *should* happen when a process is random and fair. This chapter showed you what to do when the real world produces actual data — messy, collected under imperfect conditions, summarized by people who may have reasons to mislead. Probability is the theory. Statistics is the measurement of whether the theory holds.

The inference tools built on this foundation — hypothesis testing, confidence intervals, regression — appear in virtually every field that uses data to make decisions: medicine, economics, social science, engineering, public policy. Every one of them rests on random sampling, the normal distribution, and the logic of margin of error that you have now seen from the inside.

Chapter 11 on voting and Chapter 12 on graph theory both work with populations and representative subsets. The same question reappears: is this sample representative? Is this measurement honest? Is this summary the right one for the question being asked?

You have learned to ask those questions. That is the most important thing this chapter teaches.
---

## LLM Exercise — Chapter 8: Statistics (Audit a Real-World System Project)

**Project:** Audit one real-world system through 13 chapters of mathematics.
**What you're building this chapter:** a statistical analysis of the system's published data — what averages reveal, what they hide, and what variability says.
**Tool:** **Claude Project** (same system spec as Ch 1).

**The Prompt:**

```
Chapter 8 of my system-audit project. Chapter 8 covered:
data types; sampling methods and bias; measures of center
(mean, median, mode); measures of spread (range, variance,
standard deviation); the shape of a distribution
(symmetric, skewed); the normal distribution and z-scores;
inference from sample to population.

Apply to my system. Most systems publish averaged data that
hides the more interesting story underneath.

1. **Find one published statistic the system reports.**
   Examples:
   - Transit: "average commute time"; "on-time percentage."
   - Streaming: "average viewing time per user."
   - Sports: "team's average points per game."
   - Restaurant: "average check size."
   - Hospital: "average ED wait time."
   - Election: "average voter turnout."
   Document the headline number AND the source.

2. **Identify what the average is hiding.**
   - Is the distribution skewed? (A long right tail of
     extreme cases pulls the mean above the median.)
   - Is there a bimodal pattern? (A second peak hidden
     in the average.)
   - Are there subgroups with very different distributions?
     (The fleet-wide average ED wait masks the difference
     between Mondays and Sundays; between 7 AM and 11 PM.)
   Use whatever data is publicly available to disaggregate.

3. **Compute mean, median, and mode for one disaggregated
   subset.** Example: take ED wait times for a single
   weekday vs. weekend day. Compute mean, median, and mode
   for each. Where do they differ?

4. **Compute the standard deviation (or describe the spread)
   for that subset.** A system whose mean wait is 30 min
   with a standard deviation of 5 min is very different
   from a system whose mean wait is 30 min with a standard
   deviation of 45 min — even though the headline number
   is the same.

5. **Apply z-scores to one user / customer / patient
   experience.** For a particular case (your own commute
   yesterday, a famous athlete's stat line, a published
   ED wait time), compute the z-score relative to the
   distribution. Was that experience 1 SD above the mean,
   2 SD, more? What does that tell you?

6. **Identify the sampling problem in the published data.**
   - Selection bias: who's in the sample and who isn't?
   - Survivorship bias: are dropouts excluded?
   - Response bias: do only certain people respond?
   - Self-reporting bias: are responses honest?
   Pick one and explain how it shapes the headline number.

End with: a one-page "statistical audit" of the system. The
headline statistic. What it hides. The disaggregated mean /
median / spread. One z-score interpretation. One sampling
problem.
```

**What this produces:** A statistical audit. Headline statistics are usually marketing; this exercise pulls the actual story out from underneath them.

**Connection to previous chapters:** Builds on Ch 7's probability (distributions are how probability shows up over many cases) and Ch 1's set-theoretic categories (disaggregation usually breaks the population into the categories you identified in Ch 1).

**Preview of next chapter:** Chapter 9 — apply metric measurement and dimensional analysis to the system's units. Every system has units flowing through it; many have unit-confusion problems hiding in plain sight.

---

##  AI Wayback Machine
**W.E.B. Du Bois** was built foundational statistical sociology in 'The Philadelphia Negro' (1899) — applying rigorous quantitative methods to questions of race and inequality decades before the field was named.

![W.E.B. Du Bois](../images/w-e-b-du-bois-9ef.png)

*Puppet Art by [Nik Bear Brown](https://www.nikbearbrown.com/).*

**Run this:**

```
Who is W.E.B. Du Bois, and how does their work connect to statistics we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"W.E.B. Du Bois"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply W.E.B. Du Bois's ideas to a specific concrete problem in this chapter.
- Add a constraint: "Answer including criticisms or limits of W.E.B. Du Bois's framework."

What changes? What gets better? What gets worse?
