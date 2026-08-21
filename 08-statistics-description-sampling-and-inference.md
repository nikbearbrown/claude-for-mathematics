# Statistics: Description, Sampling, and Inference

*The math of learning from a sample — and the discipline of not claiming more than the sample can support.*

---

## Does the A/B test mean anything?

A product manager runs an experiment. Variant A of the checkout page converts 11.8% of visitors; variant B converts 12.1%. Variant B is "up 2.3%." The engineering team wants to ship B. The finance team wants to know whether the lift is real or just the random jitter of two coin-flippy samples. The data scientist runs a test and reports "p = 0.04, statistically significant." Marketing emails the executive team: "B wins — there's only a 4% chance this is due to chance."

Every sentence in that last quote is a different claim, and at least one of them is flatly false. Before we can tell which, we need to answer a more basic question the manager skated past: **how much would two identical pages differ by luck alone?** A sample is a window onto a population you cannot see in full. The window has a known amount of distortion, and the entire discipline of inference is the math of that distortion — how big it is, how it shrinks with sample size, and exactly what you are and are not allowed to conclude once you have looked through it. The tool will hand the manager a precise number. It will not tell her whether 0.3 percentage points is worth shipping. Keeping those two questions separate is the most important thing in this chapter.

---

## The tool, named

**Descriptive statistics** summarize the data you have: a center (mean, median) and a spread (variance, standard deviation, quartiles). **Inferential statistics** use that sample to make calibrated claims about a population you *don't* have. The bridge between them is one idea: the **sampling distribution** — treat your sample statistic (say, the sample mean) as itself a random variable, with its own expected value and its own variance, and the whole apparatus of Chapter 7 applies. From that single move come the **standard error**, the **confidence interval**, and the **hypothesis test** — and the famous, much-abused **p-value**.

---

## Development: from a sample to a calibrated claim

### Description: center and spread

Given data $x_1, \dots, x_n$, the **sample mean** is $\bar{x} = \frac{1}{n}\sum x_i$ and the **sample variance** is

$$s^2 = \frac{1}{n-1}\sum_{i=1}^{n}(x_i - \bar{x})^2,$$

with $s = \sqrt{s^2}$ the **sample standard deviation**. (The divisor $n-1$ rather than $n$ corrects a subtle downward bias from using $\bar{x}$ in place of the unknown true mean; it is a small correction that matters for small samples and that you may take on trust here.) The standard deviation $s$ describes the **spread of the individual data points**. Hold that phrase — we are about to meet a second, easily-confused quantity that describes the spread of something else entirely.

### The sampling distribution and the standard error — straight out of Chapter 7

Here is the conceptual leap. Imagine drawing not one sample but *many* samples of size $n$ from the same population, each yielding its own mean $\bar{x}$. Those means form a distribution — the **sampling distribution of the mean** — and $\bar{x}$ is now a random variable. What are its expected value and its variance?

Its expected value is the population mean $\mu$: averaging is unbiased. Its variance we *derive*, and the derivation is nothing but Chapter 7's variance algebra. Write the sample mean as a scaled sum of $n$ independent observations $X_1, \dots, X_n$, each with variance $\sigma^2$:

$$\bar{X} = \frac{1}{n}(X_1 + X_2 + \cdots + X_n).$$

Apply, in order, the two boxed identities from Chapter 7. First, **for independent variables, variances add**:

$$\operatorname{Var}(X_1 + \cdots + X_n) = \sigma^2 + \sigma^2 + \cdots + \sigma^2 = n\sigma^2.$$

Then, **scaling by $\tfrac{1}{n}$ scales the variance by $\tfrac{1}{n^2}$** (variance scales by the *square*):

$$\operatorname{Var}(\bar{X}) = \frac{1}{n^2}\cdot n\sigma^2 = \frac{\sigma^2}{n}.$$

Take the square root to get the **standard error of the mean**:

$$\boxed{\operatorname{SE}_{\bar{x}} = \frac{\sigma}{\sqrt{n}}}$$

This is the single most consequential formula in applied statistics, and it is worth pausing on *why it could only be this*. Recall the warning from Chapter 7: **standard deviations do not add — variances do.** If standard deviations added, averaging $n$ observations would do nothing to reduce uncertainty, and there would be no point in collecting data. Because *variances* add and then get divided by $n^2$, the standard deviation of the mean falls like $1/\sqrt{n}$. The practical upshot: **to halve your uncertainty about the mean, you must quadruple your sample.** Precision is expensive, and it gets more expensive the more you want.

![Three bell curves on a shared axis for sample sizes n equals 10, 40, and 160; as n grows the curve narrows and rises while its center stays fixed, illustrating the standard error shrinking like one over root n](images/08-statistics-description-sampling-and-inference-fig-01.png)
*Figure 8.1 — The sampling distribution narrows as n grows: SE = σ/√n.*

Notice the two quantities you must never confuse. The **standard deviation $\sigma$** is the spread of the individual data points and does *not* shrink with $n$ — a bigger sample reveals the population's spread, it doesn't reduce it. The **standard error $\sigma/\sqrt{n}$** is the spread of the *sample mean* and shrinks toward zero as $n$ grows. Mixing them up is the most common computational error in the chapter. They differ by exactly the factor $\sqrt{n}$ that Chapter 7's variance algebra produced.

### The central limit theorem

We derived the standard error without saying what *shape* the sampling distribution has. The **central limit theorem** (de Moivre 1733 for the binomial; Laplace 1812 in general) answers: regardless of the population's shape — skewed, lumpy, bimodal — the sampling distribution of the mean approaches a **normal** distribution as $n$ grows. This is why the normal bell from Chapter 7 governs sample means even when the underlying data look nothing like a bell. The CLT is what lets us attach probabilities to "how far is $\bar{x}$ likely to be from $\mu$" using the normal curve.

### The confidence interval

Combine the standard error (how far off) with the CLT (the normal shape) and you can build an interval. Because about 95% of a normal distribution lies within $\pm 1.96$ standard deviations of its center, about 95% of sample means lie within $1.96\,\operatorname{SE}$ of $\mu$. Turning that around gives the **95% confidence interval**:

$$\bar{x} \pm 1.96\,\frac{\sigma}{\sqrt{n}}.$$

In practice $\sigma$ is unknown, so we use the sample $s$ and replace $1.96$ with a slightly larger critical value $t^*$ from **Gosset's $t$-distribution** — more on that below. The structure is always the same: **point estimate $\pm$ critical value $\times$ standard error.**

Now the hardest honesty in the chapter, due to Jerzy Neyman (1937), who invented the confidence interval. The correct interpretation is *frequentist*: if you repeated the whole sampling procedure many times, about 95% of the intervals so constructed would contain the true $\mu$. It is **not** correct to say "there is a 95% probability that $\mu$ lies in *this particular* interval." Once computed, this interval either contains $\mu$ or it doesn't — there is no probability left; the randomness was in the sampling, not in the fixed-but-unknown $\mu$. The "95%" describes the *long-run reliability of the method*, not the *credibility of one answer*. This distinction is genuinely counterintuitive and no phrasing makes it fully comfortable — but stating it wrong is the most common confidence-interval error, documented even among researchers (Hoekstra et al., 2014). [verify]

### The hypothesis test and the p-value

The A/B test asks: is B *really* better, or could this gap arise by chance if the two pages were identical? Inference answers by entertaining a **null hypothesis** $H_0$ — "the pages are identical; the true lift is zero" — and asking how surprising the observed data would be *if that null were true*.

The logic: assume $H_0$, compute the sampling distribution of the difference under that assumption, locate the observed difference, and measure how far into the tail it falls. The **p-value** is that tail area: *the probability, if the null hypothesis were true, of observing data at least as extreme as what we got.* A small p-value means the data are surprising under the null — weak comfort for the idea that nothing is going on.

Read that definition twice, because almost every plain-English restatement of it is wrong. The p-value is $P(\text{data this extreme} \mid H_0 \text{ true})$. It is a conditional probability about the *data given the hypothesis* — and as Chapter 7 hammered, $P(A\mid B) \ne P(B\mid A)$. The p-value is emphatically **not** $P(H_0 \text{ true} \mid \text{data})$, the probability the null is true. Marketing's email — "only a 4% chance this is due to chance" — silently flipped the conditional and produced a false statement. The honest sentence is: "*If* the two pages were truly identical, we'd see a gap this large only about 4% of the time."

The 0.05 threshold is a *convention* Ronald Fisher offered as a rough rule, not a law of nature. The accept/reject machinery — Type I error (rejecting a true null, with rate $\alpha$) versus Type II error (failing to reject a false null, rate $\beta$, with **power** $= 1 - \beta$) — comes from a different, competing framework due to Neyman and Pearson (1933). The hypothesis test taught in every MBA course is an uneasy *hybrid* of Fisher's evidential p-value and Neyman–Pearson's decision rule — a stitched-together procedure neither camp fully endorsed. That mongrel origin is a real source of the confusion, and you should know it is there.

### Small samples: Gosset's correction

MBAs rarely have the luxury of large $n$ — a handful of stores, a dozen test batches, a short return history. When $n$ is small and $\sigma$ is estimated by $s$, the extra uncertainty in estimating the spread fattens the tails: the right reference curve is not the normal but **Student's $t$-distribution**, derived by William Sealy Gosset in 1908. Gosset was a brewer at Guinness, working with tiny barley samples, and published under the pseudonym "Student" because his employer forbade staff from publishing. The $t$ uses **degrees of freedom** $\nu = n-1$; it looks like a normal with heavier tails that thin toward the normal as $n$ grows (by $n \approx 30$ the difference is negligible). The practical consequence: a confidence interval from $n = 12$ is *wider* than the normal would suggest — the small sample honestly admits how little it knows. We let software supply the $t^*$ values; the concept, not the table, is what matters.

---

## The ASA principles: what a p-value does and does not license

The misreadings above are not a student failing — they are near-universal. Haller and Krauss (2002) gave a single test result ($t = 2.7$, $\mathrm{df} = 18$, $p = .01$) with six false interpretations to statistics students, psychology professors, and statistics *instructors* at six German universities. Essentially every student, about 80% of the methodology instructors — *including the statistics teachers* — and roughly 90% of the practicing psychologists endorsed at least one false statement.
 In 2016 the American Statistical Association took the unusual step of issuing an official statement [contested — see pantry] to correct the record. Its six principles, which anchor everything in this chapter, are worth stating plainly:

1. P-values can indicate how incompatible the data are with a specified statistical model.
2. P-values do **not** measure the probability that the studied hypothesis is true, or the probability that the data were produced by chance alone.
3. Scientific conclusions and business decisions should **not** be based only on whether a p-value passes a threshold.
4. Proper inference requires full reporting and transparency — p-hacking and cherry-picking render p-values uninterpretable.
5. A p-value, or statistical significance, does **not** measure the size of an effect or the importance of a result.
6. By itself, a p-value does **not** provide a good measure of evidence regarding a model or hypothesis.

Principle 5 is the one an MBA will hit hardest in practice, so it gets its own worked example below. The field has not settled on a replacement: some argue to lower the default threshold to 0.005 (Benjamin et al., 2018) [verify], others to **retire** statistical significance entirely in favor of effect sizes with confidence intervals (Amrhein, Greenland & McShane, 2019, *Nature*) [verify; contested — see pantry]. There is no consensus successor. You will meet the standard test everywhere; your job is to use it while knowing exactly what it does and does not license.

---

## Worked examples

### Example 1 — The A/B test, done honestly

Return to the checkout test. Variant A: 11.8% of $n_A = 8{,}000$ visitors convert. Variant B: 12.1% of $n_B = 8{,}000$. The lift is $0.121 - 0.118 = 0.003$, i.e. 0.3 percentage points (the "2.3% relative lift").

For a proportion $\hat{p}$, the standard error is $\sqrt{\hat{p}(1-\hat{p})/n}$ — itself just the binomial variance $np(1-p)$ from Chapter 7, divided through by $n^2$ and rooted. The standard error of the *difference* of two independent proportions adds the variances (Chapter 7 again):

$$\operatorname{SE}_{\text{diff}} = \sqrt{\frac{\hat{p}_A(1-\hat{p}_A)}{n_A} + \frac{\hat{p}_B(1-\hat{p}_B)}{n_B}}.$$

Plugging in: each term is about $\frac{0.12 \times 0.88}{8000} \approx 1.32 \times 10^{-5}$; the sum is $2.64\times10^{-5}$, and $\operatorname{SE}_{\text{diff}} \approx 0.00514$. The observed difference in standard-error units is $z = 0.003 / 0.00514 \approx 0.58$.

![Bell curve for the lift if the two checkout pages were identical, with the observed result marked at z equals 0.58 deep inside the curve and the two shaded tails beyond making a two-sided p-value of about 0.56, well short of the plus-or-minus 1.96 significance markers](images/08-statistics-description-sampling-and-inference-fig-03.png)
*Figure 8.2 — The p-value as a tail area: the observed lift sits comfortably inside the null distribution.*

A $z$ of 0.58 is deep inside the bell — the two-sided p-value is about 0.56. **The result is nowhere near significant.** (The data scientist's "p = 0.04" would require a much larger sample or a larger gap; with these numbers the lift is comfortably within sampling noise.)

The 95% confidence interval on the lift is $0.003 \pm 1.96(0.00514) = [-0.007,\ 0.013]$ — it straddles zero. We cannot rule out that B is *worse*. The honest report to the executives: "B is up 0.3 points, but our sample can't distinguish that from noise; the true difference is somewhere between $-0.7$ and $+1.3$ points. We'd need a far larger test to call it."

### Example 2 — The large-$n$ trap (significance $\ne$ importance)

Now suppose the same 0.3-point lift held but each variant got $n = 5{,}000{,}000$ visitors. The standard error shrinks by $\sqrt{5{,}000{,}000/8{,}000} \approx 25$, to about $0.0002$. Now $z = 0.003/0.0002 = 15$ — wildly "significant," $p < 10^{-15}$. The statistician is certain the lift is real.

![Two-panel comparison of the identical 0.3-point lift: a wide bell at n equals 8,000 with z equals 0.58 and p about 0.56 not significant, beside a needle-thin bell at n equals 5,000,000 with z about 15 and p below ten to the minus fifteenth, significant but trivial](images/08-statistics-description-sampling-and-inference-fig-04.png)
*Figure 8.4 — Significance is not importance: the same tiny effect flips verdicts on sample size alone.*

And it still might not be worth shipping. A 0.3-percentage-point lift is *real* and *trivially small*; whether it pays for the engineering, the risk, and the maintenance is an economic question the p-value is structurally incapable of answering (ASA Principle 5). At large $n$, **statistical significance and practical importance come apart entirely** — everything becomes significant, including effects too small to care about. This is the single most relevant statistical fact for a modern data-rich business: the question is never only "is it significant?" but "is it *big enough to act on*?" — and that second question is yours, not the test's.

### Example 3 — How wide is "past performance"? (finance)

A fund reports five annual returns: 22%, −5%, 14%, 9%, 1%. The sample mean is $\bar{x} = (22 - 5 + 14 + 9 + 1)/5 = 8.2\%$. The sample standard deviation (using the $n-1$ divisor) works out to about $s \approx 10.6\%$. The standard error of the mean is $s/\sqrt{n} = 10.6/\sqrt{5} \approx 4.75\%$. With $n = 5$ we use the $t$-distribution ($\nu = 4$, $t^* \approx 2.78$), giving a 95% confidence interval

$$8.2\% \pm 2.78(4.75\%) = [-5.0\%,\ 21.4\%].$$

![Number line of annual returns showing a point estimate of 8.2 percent and a 95 percent confidence interval bracket from negative 5.0 percent to 21.4 percent that visibly crosses the emphasized zero line](images/08-statistics-description-sampling-and-inference-fig-02.png)
*Figure 8.3 — A 95% confidence interval that straddles zero: five years cannot prove the mean is positive.*

The interval runs from a *loss* to over 20%. Five years of history — more than many funds advertise — cannot even establish that the fund's true mean return is positive. This is why "past performance is no guarantee of future results" is not legal boilerplate but a mathematical fact: with the short histories investors actually have, the standard error is so large that the confidence interval is nearly useless. The single "22% year" from Chapter 7 is one draw from a distribution this wide.

---

## Back to the A/B test

We can now grade marketing's email line by line. "B wins" — unsupported; with $n=8{,}000$ the interval straddles zero (Example 1). "There's only a 4% chance this is due to chance" — false twice over: the p-value isn't 0.04 with this sample, *and* even a true 0.04 would be $P(\text{data}\mid H_0)$, not $P(H_0\mid\text{data})$; it flipped the conditional, the exact Chapter 7 error. "Statistically significant" — would, at large $n$ (Example 2), be true and *still not* settle whether 0.3 points is worth shipping (ASA Principle 5).

The manager's original question — "does the result mean anything?" — splits cleanly into two the tool keeps separate. **Is the lift distinguishable from noise?** A standard-error-and-interval question the math answers precisely. **Is the lift big enough to act on?** An economic question about engineering cost, downside risk, and strategy that the math cannot touch. The discipline of inference is partly mechanical — compute the standard error, build the interval, find the p-value — and partly a refusal: a refusal to let "significant" smuggle in "important," and a refusal to claim the sample supports more than it does. That refusal is where the book's tool-versus-judgment thesis is sharpest.

---

## Where this generalizes

The standard error built here reappears wherever someone estimates from a sample: a poll's "margin of error" is just $2 \times$ the standard error of a proportion (the familiar $\pm 3\%$ at $n \approx 1{,}000$); a defect-rate estimate, an engagement survey, a demand forecast all carry one. **Chapter 9** runs the hypothesis test on a regression *coefficient* (is the slope distinguishable from zero?) — same logic, new estimate — and inherits all the same cautions about significance versus importance. The frequentist confidence interval here contrasts with the *credible* interval of Bayesian analysis, which **Chapter 13** develops via Bayes' rule; that approach answers the question people *wish* the p-value answered, at the cost of requiring a prior. And every standard error in this chapter rests on Chapter 7's $\operatorname{Var}(aX) = a^2\operatorname{Var}(X)$ — the variance algebra is the engine; inference is one of its largest customers.

---

## Exercises

1. **(Compute.)** A sample of 36 stores has mean weekly sales \$42,000 with sample standard deviation \$9,000. Compute the standard error of the mean and a 95% confidence interval for true mean weekly sales (use $z = 1.96$). Then state, in one sentence, the *correct* frequentist interpretation of your interval — and one sentence saying what it does *not* mean.

2. **(Compute the cost of precision.)** Using $\operatorname{SE} = \sigma/\sqrt{n}$, show how large $n$ must be to halve the standard error of a survey, starting from $n = 400$. State the general rule relating precision to sample size, and explain why it makes high-precision surveys expensive.

3. **(Catch the error.)** A report reads: "The new ad's effect was not statistically significant ($p = 0.21$), so the ad has no effect on sales." Identify the two distinct mistakes (Hint: one is about absence of evidence; one is about a threshold). Rewrite the conclusion honestly.

4. **(Build/derive.)** Starting from $\bar{X} = \frac{1}{n}\sum_{i=1}^n X_i$ with each $X_i$ independent and having variance $\sigma^2$, derive $\operatorname{Var}(\bar{X}) = \sigma^2/n$ using the variance algebra from Chapter 7. State explicitly where you use "variances of independent variables add" and where you use "scaling by $a$ scales variance by $a^2$." Then explain in one sentence why the result would be *wrong* if you had instead "added standard deviations."

5. **(Reason about the boundary.)** An A/B test on 10 million users finds a 0.05-percentage-point conversion lift with $p < 0.001$. Write the email you would send the executive team. Your email must (a) report the statistical result correctly, (b) refuse to conflate significance with importance, and (c) name the specific business inputs needed to decide whether to ship.

---

## Sources

- Laplace, P.-S. (1812). *Théorie analytique des probabilités*. — The central limit theorem in general form. [verify]
- de Moivre, A. (1733). Normal approximation to the binomial — the CLT's first special case. [verify]
- Gosset, W. S. ("Student") (1908). "The Probable Error of a Mean," *Biometrika* 6(1), 1–25. — The $t$-distribution for small samples. [verify]
- Fisher, R. A. (1925). *Statistical Methods for Research Workers*; (1935). *The Design of Experiments*. — The significance test and the p-value as a measure of evidence; the 0.05 convention. [verify]
- Neyman, J., & Pearson, E. S. (1933). "On the Problem of the Most Efficient Tests of Statistical Hypotheses," *Philosophical Transactions of the Royal Society A* 231, 289–337. — Type I/II errors, power, accept/reject testing. [verify]
- Neyman, J. (1937). "Outline of a Theory of Statistical Estimation," *Philosophical Transactions of the Royal Society A* 236, 333–380. — The confidence interval and its correct frequentist interpretation. [verify]
- Wasserstein, R. L., & Lazar, N. A. (2016). "The ASA Statement on p-Values: Context, Process, and Purpose," *The American Statistician* 70(2), 129–133. — The six principles. [contested — see pantry: the p-value debate is live.]
- Haller, H., & Krauss, S. (2002). "Misinterpretations of Significance," *Methods of Psychological Research Online* 7(1), 1–20. — Near-universal p-value misinterpretation, including among instructors (≈100% of students, ≈80% of methodology instructors, ≈90% of practicing psychologists endorsed ≥1 false interpretation).
- Hoekstra, R., Morey, R. D., Rouder, J. N., & Wagenmakers, E.-J. (2014). "Robust Misinterpretation of Confidence Intervals," *Psychonomic Bulletin & Review* 21(5), 1157–1164. [verify]
- Cohen, J. (1994). "The Earth Is Round (p < .05)," *American Psychologist* 49(12), 997–1003. [verify]
- Benjamin, D. J., et al. (2018). "Redefine Statistical Significance," *Nature Human Behaviour* 2, 6–10. [verify]
- Amrhein, V., Greenland, S., & McShane, B. (2019). "Scientists rise up against statistical significance," *Nature* 567(7748), 305–307.
- *MBA Marketing*, Chapter 8 (Marketing Research and Market Intelligence). — The A/B-test cold open and the research-process framing.
- *MBA Finance*, Chapter 13 (Statistical Analysis in Finance). — The short-return-history sampling problem (Example 3).
