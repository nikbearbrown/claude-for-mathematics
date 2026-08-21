# Chapter 14 — Quantitative Finance: Returns, Volatility, Options, and Monte Carlo

## Being in two places at once

Jin is a software engineer whose company went public a year ago. He holds \$800,000 of stock that just unlocked, and it has run up a long way. He wants two things that seem to contradict each other: keep the upside if the stock keeps climbing, and be protected if it crashes. Holding gives him both the gain and the risk; selling kills both. There is no way to carve out "only the good half" from a position that moves in a straight line with the stock.

And yet there is an instrument that does exactly that — a contract whose payoff bends, so that it pays Jin only when the stock falls below a floor, leaving his upside intact. It can be *priced*, and here is the part that unsettles every newcomer: the price does not depend on whether you think the stock will rise or fall. This capstone chapter builds the math behind it — **simple versus log returns**, **annualizing volatility** by the square root of time, the **random-walk model** of prices, **option payoffs** and **put–call parity**, the **intuition** behind Black–Scholes, and **Monte Carlo** valuation. Where the rigorous stochastic calculus begins, we stop and point onward to `mba-computational-finance`.

## The tool, named

A **return** measures change in price over a period; the **log return** is its time-additive cousin. **Volatility** is the standard deviation of returns, and it scales with the **square root of time**. An **option** is a contract with a kinked payoff: a **call** pays $\max(S - K, 0)$, a **put** pays $\max(K - S, 0)$. **Put–call parity** is a no-arbitrage identity linking the two. **Black–Scholes** prices a European option from five inputs. **Monte Carlo** prices anything by simulating, discounting, and averaging.

## Development

### Simple vs. log returns, and a trap

A stock rises 50% one year, falls 50% the next. Back to even? No: \$1 becomes \$1.50 becomes \$0.75 — you are down 25%. The two moves did not cancel because **simple returns compound (multiply); they do not add.** The simple return is $R = (P_{\text{end}} - P_{\text{start}})/P_{\text{start}}$; chaining periods means multiplying $(1+R_1)(1+R_2)\cdots$, not summing.

The **log return** fixes this:

$$r = \ln\!\left(\frac{P_{\text{end}}}{P_{\text{start}}}\right).$$

Because the log of a product is the sum of the logs, log returns are **time-additive**: over many periods the total log return is just the sum,

$$r_{\text{total}} = \ln\!\left(\frac{P_T}{P_0}\right) = \sum_{t=1}^{T} \ln\!\left(\frac{P_t}{P_{t-1}}\right) = r_1 + r_2 + \cdots + r_T,$$

because the intermediate prices telescope away. Check the trap: $\ln(1.5) + \ln(0.5) \approx 0.405 - 0.693 = -0.288$, and $e^{-0.288} - 1 \approx -25\%$. The log arithmetic tells the truth about the path. Simple returns are what you report to a human; log returns are what you do statistics with, precisely because sums are easier than products.

### Volatility and the square root of time

Volatility is the standard deviation of returns over a window. Suppose you have daily log returns and want annual volatility. The naïve move — multiply daily volatility by 252 (the trading days in a year) — is wrong by a factor of about sixteen. Here is why.

If daily returns are **independent and identically distributed**, the variance of a sum equals the sum of the variances. The annual return is the sum of 252 daily returns, so

$$\text{Var}(r_1 + r_2 + \cdots + r_{252}) = 252\,\text{Var}(r).$$

Variance scales with time. But volatility is the *square root* of variance, so

$$\sigma_{\text{annual}} = \sqrt{252}\,\sigma_{\text{daily}} \approx 15.87\,\sigma_{\text{daily}}.$$

A 1% daily volatility annualizes to about 15.9%, not 252%. The square root is not a convention — it is a consequence of variance adding under independence. This is the **√t scaling rule**, and Louis Bachelier derived its ancestor in his 1900 Sorbonne thesis: price uncertainty grows with the square root of elapsed time, the random walk made precise five years before Einstein's Brownian-motion paper. [verify: Bachelier 1900 thesis venue/year]

<!-- → [DIAGRAM: fan of simulated price paths spreading from a single point, the envelope widening as √t; caption: "Under a random walk, the spread of possible prices grows with √t — the same scaling that annualizes volatility by √252."] -->

The assumption — i.i.d. returns — is a simplification. Real returns show volatility clustering and fat tails, so √t is the everyday tool, honestly flagged rather than literally true.

![Volatility fan: simulated price paths spreading from a starting price of 100, with ±1σ√t and ±2σ√t envelopes widening as the square root of time over one year, forming a sideways-parabola cone with faint Monte Carlo sample paths inside](images/14-quantitative-finance-returns-volatility-options-monte-carlo-fig-02.png)
*Figure 14.2 — The √t cone: under a random walk the spread of prices grows with the square root of time — the same law that annualizes volatility by √252.*

### Option payoffs and the kink

At expiration, a **put** with strike $K$ pays $\max(K - S, 0)$: nothing if the stock $S$ is above $K$, and $K - S$ if it has fallen below — it pays only on the downside. A **call** pays $\max(S - K, 0)$: nothing below the strike, rising above it. These bent, "hockey-stick" payoffs cannot be built from straight-line stock positions; the kink is the whole point.

<!-- → [DIAGRAM: put payoff max(K−S,0) and call payoff max(S−K,0) as hockey sticks, plus stock + put combined into a floored "protective put" payoff; caption: "The kink at the strike. Stock plus a put = a floor with the upside intact — exactly insurance."] -->

Jin's solution is now visible: **hold the stock and buy a put.** Above the strike the put expires worthless and he keeps all the upside; below it the put pays off and offsets his loss, putting a floor under the position. This is *insurance*: the strike is the deductible, the put's price is the premium, expiration is the policy term.

![Two-panel payoff diagram: left, a call payoff max(S−K,0) and put payoff max(K−S,0) as hockey sticks around strike K=100; right, long stock plus a put combining into a protective-put payoff that is floored at K below the strike and rises one-for-one above it](images/14-quantitative-finance-returns-volatility-options-monte-carlo-fig-01.png)
*Figure 14.1 — The kink at the strike: stock plus a put gives a floor with the upside intact — insurance on the position.*

### Put–call parity: a price relationship with no model in it

Consider two portfolios held to a common expiration $T$:

- **Portfolio A:** one call (strike $K$) plus cash $K e^{-rT}$ (which grows to exactly $K$ at expiration).
- **Portfolio B:** one put (strike $K$) plus one share of stock.

At expiration, if $S > K$: A is worth $(S - K) + K = S$; B is worth $0 + S = S$. If $S \le K$: A is worth $0 + K = K$; B is worth $(K - S) + S = K$. **In every case the two portfolios pay identically.** Two things with identical future payoffs must cost the same today, or a riskless arbitrage exists — buy the cheap one, sell the dear one, pocket the difference for free. So their prices are equal today:

$$\boxed{C + K e^{-rT} = P + S} \quad\Longleftrightarrow\quad C - P = S - K e^{-rT}.$$

This is **put–call parity**. Notice what is *not* in it: no volatility, no probabilities, no forecast — it is a model-free identity, true by no-arbitrage alone. Robert Merton derived such bounds and parity from no-arbitrage in 1973. [verify: Merton 1973]

### Black–Scholes, by intuition

The deeper no-arbitrage idea, due to Black and Scholes (1973), is **replication**. In a simple one-step world the stock can go up or down; you can find a portfolio of stock and borrowing that exactly reproduces the option's two possible payoffs. If a portfolio matches the option in every future state, it must cost what the option costs — otherwise, again, free money. And the striking consequence: the *probability* of the stock rising never enters the replication. The option price is forced by what the future *can* look like and by the cost of carrying stock, not by anyone's view of where the stock is headed. Split the year into ever-finer steps and the binomial tree converges to continuous (geometric Brownian) motion; the option price converges to the **Black–Scholes formula**:

$$C = S\,N(d_1) - K e^{-rT} N(d_2), \qquad d_1 = \frac{\ln(S/K) + (r + \tfrac{1}{2}\sigma^2)T}{\sigma\sqrt{T}}, \quad d_2 = d_1 - \sigma\sqrt{T},$$

where $N(\cdot)$ is the standard-normal CDF. Five inputs: stock price $S$, strike $K$, risk-free rate $r$, time $T$, volatility $\sigma$. Four you can look up right now. Only $\sigma$ must be estimated — and everything interesting in options trading lives in disagreement about $\sigma$. We state the formula and its replication logic; the stochastic-calculus derivation of the underlying PDE belongs to `mba-computational-finance`, ch. 7, and we send you there deliberately rather than wave at it.

### Monte Carlo: price anything by averaging

When no clean formula exists, simulate. The risk-neutral valuation principle says an option's price equals the discounted expected payoff under a risk-neutral price process. You estimate that expectation directly: simulate many random price paths to expiration, compute each path's payoff, discount each back to today, and **average**:

$$\hat{C} = e^{-rT}\,\frac{1}{N}\sum_{i=1}^{N} \text{payoff}(S_T^{(i)}).$$

That is the entire method — Phelim Boyle introduced it for options in 1977. It is the most general valuation tool in finance: give it any payoff rule, however path-dependent, and it returns a price, with accuracy improving as $1/\sqrt{N}$ (more paths, tighter estimate — the same √-law, now governing simulation error).

## Worked examples

**Example 1 — Log returns add; simple returns don't.** A fund returns +20%, −10%, +15% over three years. Simple compounding: $1.20 \times 0.90 \times 1.15 = 1.242$, a +24.2% total — *not* the sum 25%. Log returns: $\ln 1.20 + \ln 0.90 + \ln 1.15 \approx 0.1823 - 0.1054 + 0.1398 = 0.2167$, and $e^{0.2167} - 1 \approx 24.2\%$. The log returns added cleanly to the same answer; the simple returns had to be multiplied.

**Example 2 — Annualizing volatility.** A stock's daily log returns have standard deviation 1.2%. Annual volatility = $0.012 \times \sqrt{252} \approx 0.012 \times 15.87 = 0.190$, i.e. about 19%. If a careless analyst had multiplied by 252, they would report 302% — the tell-tale "16× too large" error. To convert monthly volatility to annual instead, multiply by $\sqrt{12}$.

**Example 3 — A protective put via Black–Scholes (illustrative).** Jin holds AAPL at $S = \$185$ and wants a six-month floor at $K = \$170$, with $r = 4.5\%$, $T = 0.5$, $\sigma = 25\%$. Working $d_1$: numerator $\ln(185/170) + (0.045 + 0.03125)(0.5) \approx 0.0846 + 0.0381 = 0.1227$; denominator $0.25\sqrt{0.5} \approx 0.1768$; so $d_1 \approx 0.694$, $d_2 \approx 0.517$. The put comes out near \$5.16 per share — about \$5.27 in the market, a gap of roughly eleven cents, inside the bid–ask spread. (Market data ages fast; treat the numbers as illustrative, adapted from `mba-computational-finance` ch. 7.) Run the formula in reverse on the \$5.27 market price and you back out an **implied volatility** of about 25.5% — the market's own estimate of $\sigma$, the one input no one can observe.

## Back to Jin

Jin can be in two places at once. Stock plus a put gives him a floor at the strike and unlimited upside above it — insurance on his concentrated position. Put–call parity tells him the put and the call are two faces of one relationship; Black–Scholes prices the put from five inputs; and the price falls out of the no-free-money/replication argument, *not* from any opinion about Apple's direction. What the math cannot tell him is whether he *should* buy it. The premium — a few percent a year — is a real, compounding drag, and sometimes the honest answer is to simply sell some stock. The formula prices the contract; it does not tell you whether the contract is worth buying. Those are different questions, and only one has an objective answer.

## Where it generalizes

Log returns make multi-period and multi-asset return bookkeeping additive (Chapters 1 and 10); √t volatility scaling is the everyday tool of risk reporting and Value-at-Risk; option payoff diagrams and put–call parity frame hedging, structured products, employee stock options, and real options on projects (the decision trees of Chapter 13 are the discrete cousins of option valuation). Black–Scholes survives in practice less as a literal pricer than as the *definition of implied volatility* and the common language traders quote in. Monte Carlo is the workhorse for path-dependent and high-dimensional derivatives, and the same simulate-and-average logic powers risk simulation across the firm.

Two honest caveats, both pointing onward. First, the constant-volatility assumption is empirically false: real markets show a **volatility skew** — out-of-the-money puts trade at higher implied vols, reflecting fat tails (crashes happen more often than the lognormal model predicts) and hedging demand — so flat Black–Scholes can misprice skew-sensitive puts by a meaningful margin — on the order of tens of percent for deep out-of-the-money options (an illustrative magnitude, not a fixed constant; the gap depends on the option and the market). Second, √t fails when returns are autocorrelated or volatility clusters. The durable core of this chapter is the *logic* — no-arbitrage, put–call parity, log-return additivity, Monte Carlo — not the specific numbers. For the stochastic-calculus derivation of Black–Scholes, the implied-volatility surface, and local/stochastic-volatility models, go to `mba-computational-finance`. This chapter built the intuition; that one builds the machine.

<!-- → [DIAGRAM: implied-volatility skew sketch — implied vol higher for low strikes (OTM puts), curving up; caption: "Reality vs. the model: flat Black–Scholes assumes one σ; the market quotes a skew. Where the model departs from the world."] -->

## Exercises

1. **Returns don't add.** A stock returns +30% then −20%. Compute the two-year total simple return by compounding, then by summing log returns and converting back. Explain in one sentence why the naïve sum (+10%) is wrong.
2. **Derive the √t rule.** Starting from the assumption that daily returns are i.i.d. with variance $\sigma_d^2$, show that the variance over $n$ days is $n\sigma_d^2$ and therefore the standard deviation scales as $\sqrt{n}$. State the one assumption the derivation depends on and one real-world reason it can fail.
3. **Prove put–call parity (build it).** For a European call and put with the same strike $K$ and expiration $T$, construct the two portfolios in the chapter, tabulate their payoffs for $S_T > K$ and $S_T \le K$, show they are identical, and conclude $C - P = S - Ke^{-rT}$. State explicitly which no-arbitrage step you used.
4. **Read a payoff.** Draw the payoff at expiration of a portfolio that is long one share and long one put struck at \$50, for stock prices from \$0 to \$100. Mark the floor and explain why the position is equivalent to "stock with insurance."
5. **Monte Carlo by hand.** You simulate four price paths for a call struck at \$100, with terminal prices \$90, \$110, \$120, \$95, $r = 5\%$, $T = 1$. Compute each path's payoff, average them, discount the average by $e^{-rT}$, and report the Monte Carlo price estimate. Say how the estimate's error shrinks as you add paths.

## Sources

- Bachelier, L. (1900). *Théorie de la spéculation*. Doctoral thesis defended at the Sorbonne, 29 March 1900 (random-walk price model; √t uncertainty).
- Black, F., & Scholes, M. (1973). "The Pricing of Options and Corporate Liabilities." *Journal of Political Economy*, 81(3), 637–654.
- Merton, R. C. (1973). "Theory of Rational Option Pricing." *Bell Journal of Economics and Management Science*, 4(1), 141–183 (put–call parity, no-arbitrage bounds).
- Boyle, P. P. (Phelim P. Boyle) (1977). "Options: A Monte Carlo Approach." *Journal of Financial Economics*, 4(3), 323–338.
- Bronzin, V. (1908). *Theorie der Prämiengeschäfte* (option-pricing work, rediscovered c. 2002 by Hafner & Zimmermann; forgotten-pioneer sidebar).
- Returns-additivity trap, protective-put case, AAPL Black–Scholes example, and volatility-skew caveat adapted from `mba-computational-finance`, ch. 2 (Returns and Risk) and ch. 7 (Options and Derivatives).
