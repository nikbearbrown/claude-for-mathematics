# Chapter 12 — Graph Theory


## TL;DR

- The map Euler threw away — and what he saw without it.
- The chapter moves through The Vocabulary of Connection, Euler's Argument, Two Vertices of Odd Degree, When the Route Doesn't Close: The Postman Problem, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

*The map Euler threw away — and what he saw without it.*

---

In 1736, Leonhard Euler received a puzzle from the city of Königsberg. The city sat on the Pregel River, which split the land into four regions connected by seven bridges. The question was whether you could walk through the city crossing each bridge exactly once and return to where you started.

People had been trying this for years. Nobody succeeded. Nobody could prove it was impossible either. They kept walking routes in their heads, getting stuck, starting over with a different bridge, getting stuck again somewhere else.

Euler looked at the problem and did something that at first seems like cheating: he threw away the city.

Not metaphorically. He replaced each of the four land regions — north bank, south bank, large island, small island — with a single dot. He replaced each bridge with a line connecting two dots. The actual geography: gone. The distances: gone. The shape of the riverbanks, the size of the islands, the names of the streets: all gone. What remained was a picture with four dots and seven lines. It looked nothing like Königsberg. But it preserved the only fact that mattered: which regions were connected to which.

That picture is called a *graph*. Not the kind with axes and curves — that's a different use of the word. A graph in the sense Euler invented: a collection of *vertices* (the dots) connected by *edges* (the lines), stripped of everything except the pattern of connection.

![Panel ](images/12-graph-theory-fig-01.png)
*Figure 12.1 — Panel *

Euler stared at the picture for a short while and proved the walk was impossible. Not just for Königsberg — for any city with the same connection pattern. He proved it by asking one question about the dots: how many lines meet at each one?

That number — the *degree* of a vertex — contained the entire answer.

---

## The Vocabulary of Connection

Before we can follow Euler's argument, we need the vocabulary.

A **graph** $G = (V, E)$ consists of a set of vertices $V$ and a set of edges $E$, where each edge connects a pair of vertices. That's the whole definition. No distances, no directions (for now), no geography. Just: which things are connected to which.

The **degree** of a vertex is the number of edges meeting at it. In Königsberg, the four land regions had degrees 3, 3, 3, 5 — counting how many bridges connected to each one. (The large island had five bridges; each bank had three.)

A **simple graph** has no loops (an edge from a vertex to itself) and no multiple edges (two separate edges between the same pair of vertices). Simple graphs are the version we use when we only care about whether two things are connected at all.

There is one theorem about degrees that every calculation in this chapter depends on. Count every degree and add them up. In Königsberg: $3 + 3 + 3 + 5 = 14$. Count the edges: 7. Notice that $14 = 2 \times 7$.

This is not a coincidence. It is always true.

**The Sum of Degrees Theorem:** For any graph,

$$\sum_{v \in V} \deg(v) = 2|E|$$

The sum of all degrees equals twice the number of edges. The reason is immediate: every edge has two endpoints. When you sum the degrees, you count each edge once at each end — so you count it exactly twice.

![Each edge contributes 1 to each of its two endpoints' degrees — counted twice in the total. Sum of degrees = 2 × number of edges, always.](images/12-graph-theory-fig-02.png)
*Figure 12.2 — A small graph (5 vertices, 6 edges) with*

A consequence: the number of vertices with odd degree is always even. If the sum of all degrees is even, and even-degree vertices contribute even amounts, then the odd-degree vertices must collectively sum to an even total — which requires an even count of them. You cannot have three odd-degree vertices. Or seven. They always come in pairs.

Euler noticed this. It is why he could say anything definitive about Königsberg.

---

## Euler's Argument

The question about Königsberg was: can you traverse every edge exactly once in a closed walk — starting and ending at the same vertex?

A walk like this is called an **Euler circuit**.

Euler asked: what must be true about a vertex's degree for an Euler circuit to be possible?

Think about any vertex that is not the starting point. Each time you pass through it, you arrive on one edge and leave on another. Those two edges are used up — one entering, one leaving. Each passage through the vertex uses edges in pairs. So the total number of edges at that vertex must be even.

What about the start vertex? You leave it at the beginning (using one edge) and return to it at the end (using another). That's two edges. Any other passage through the start vertex also uses edges in pairs. So the start vertex also needs even degree.

Every vertex. Even degree. That is the necessary condition.

![Even degree: every arrival has a departure. Odd degree: one edge is always left stranded.](images/12-graph-theory-fig-03.png)
*Figure 12.3 — Two diagrams of the same vertex side by*

It is also sufficient. If every vertex has even degree and the graph is connected, you can always find an Euler circuit. The proof is constructive — Fleury's algorithm finds the circuit greedily, removing each traversed edge and never crossing a bridge that would disconnect the remaining graph unless there is no other choice. The key insight is Euler's: the degree condition is everything.

**Euler's Theorem:** A connected graph has an Euler circuit if and only if every vertex has even degree.

Apply this to Königsberg. The four regions have degrees 3, 3, 3, 5. All four vertices have odd degree. No Euler circuit exists. The walk is impossible — not because nobody was clever enough to find the route, but because the structure of the bridges made it impossible in principle.

This is the characteristic move of mathematics: replacing a question about searching (can you find a route?) with a question about structure (what are the degrees?). The search is replaced by a check. The answer is immediate once you know what to check.

---

## Two Vertices of Odd Degree

Euler went further. Suppose you relax the requirement: you don't have to return to your starting point. You just want to traverse every edge exactly once, starting somewhere and ending somewhere possibly different.

This is called an **Euler trail**.

By the same parity argument: every interior vertex — one you pass through but don't start or end at — must have even degree. The start vertex is left once more than it is arrived at: one net departure, so odd degree is permitted. The end vertex is arrived at once more than it is left: odd degree also permitted. So start and end vertices may have odd degree, but no other vertex can.

**Euler's Theorem (for trails):** A connected graph has an Euler trail if and only if it has exactly zero or exactly two vertices of odd degree.

- Zero odd-degree vertices: Euler circuit exists.
- Two odd-degree vertices: Euler trail exists, starting at one odd vertex and ending at the other.
- Four or more: no Euler trail exists.

| Number of odd-degree vertices | What exists | Why | Example |
| --- | --- | --- | --- |
| for Euler circuits and trails — | A concrete checkpoint for applying the chapter concept. | It makes the underlying reasoning visible instead of implied. | Use the chapter example as the concrete test case. |

In Königsberg, there are four odd-degree vertices — two too many. Remove one bridge to reduce to two odd-degree regions, and a trail becomes possible (just not a circuit). The structure of the problem dictates the structure of the solution with precision.

---

## When the Route Doesn't Close: The Postman Problem

Real delivery routes don't live in textbooks. A mail carrier covers every street in a neighborhood starting and ending at the post office. Every street is an edge. Every intersection is a vertex. The carrier wants an Euler circuit.

The degree of an intersection is the number of streets meeting there. In most cities, a four-way intersection has degree 4 (even: fine), a T-intersection has degree 3 (odd: problem).

The practical consequence: if the street network has any odd-degree intersections — and most do — no Euler circuit exists. The carrier must retrace some streets. The question is not whether to repeat streets but which streets to repeat to minimize total distance.

This is the **Chinese Postman Problem**, formalized by Mei-Ko Kwan in 1962. The solution follows directly from Euler.

We know odd-degree vertices come in pairs. To create an Euler circuit, we need to make all degrees even. Adding an edge (i.e., repeating a street) between two odd-degree vertices makes both of them even — fixing two problems at once. So we pair up all the odd-degree vertices and duplicate the paths between each pair.

The constraint: choose pairings that minimize total added distance. For a network with four odd-degree vertices, there are three possible pairings. Compute the shortest-path distance between each pair of vertices, add them for each pairing, pick the cheapest. For eight odd-degree vertices, the pairing problem grows — but it remains solvable in polynomial time using minimum-weight matching algorithms.

![To eulerize the graph: pair all odd-degree vertices, duplicate the shortest paths between each pair, pick the pairing with minimum total added distance.](images/12-graph-theory-fig-04.png)
*Figure 12.4 — A small neighborhood street graph (8 intersections, 10*

Once the cheapest duplicate paths are added, every vertex has even degree. Run Fleury's algorithm. Done.

The payoff is real. A carrier serving 60 streets with 8 odd-degree intersections is going to repeat some streets regardless. The postman algorithm finds the minimum-distance set of repeats. Compounded over hundreds of carriers and millions of delivery days, the savings are substantial.

---

## A Different Question: Visiting Every Vertex

Now change the problem. Instead of visiting every edge, you want to visit every vertex — every city on a salesman's route, every bus stop on a school route, every site in a field inspection. You want a closed tour that touches every vertex exactly once.

This is called a **Hamilton cycle**.

The name comes from William Rowan Hamilton, who posed a puzzle in 1857 involving a dodecahedron: find a path along its edges that visits all twenty vertices exactly once. The puzzle was sold as a toy. But the mathematical question inside it was not.

Euler and Hamilton problems sound similar. Both involve tours. Both involve "exactly once." They differ in what gets visited exactly once — edges vs. vertices — and that difference is enormous.

For Euler circuits, we have a complete characterization: all degrees even. Check in linear time. Find the circuit efficiently.

For Hamilton cycles, we have no such condition. No simple property of the graph tells you whether a Hamilton cycle exists. The degree of every vertex could be 1,000 and a Hamilton cycle might still be absent. Degree 2 at every vertex guarantees one (the graph must be a single large cycle) — but that is a degenerate case, not a useful test. In general, you cannot look at any local property and decide.

The only known method is to search.

Why is the Hamilton problem harder? Euler circuits are determined by local structure: check each vertex's degree independently, and the global question answers itself. Hamilton cycles are determined by global structure: the arrangement of all vertices relative to all others. Local properties are easy to check; global structure requires exploration.

![Same degree sequence. Different global structure. One has a Hamilton cycle; one does not. Degree alone cannot distinguish them.](images/12-graph-theory-fig-05.png)
*Figure 12.5 — Two graphs side by side with identical degree*

---

## The Traveling Salesperson Problem

The weighted version of the Hamilton cycle problem is the **Traveling Salesperson Problem** (TSP): a salesperson must visit $n$ cities exactly once and return home, and each road between cities has a distance. Find the shortest possible tour.

This is, in a precise technical sense, one of the hardest problems in mathematics.

The brute-force approach: list every possible tour and compute its length. The number of distinct tours on $n$ cities is $(n-1)!/2$. Here is what that number means in practice.

For 10 cities: $(9)!/2 = 181{,}440$ tours. A computer handles this instantly.

For 15 cities: $(14)!/2 \approx 43{,}000{,}000{,}000$ tours. About 43 billion. At one billion tours per second: 43 seconds.

For 20 cities: $(19)!/2 \approx 6 \times 10^{16}$ tours. At one billion per second: roughly two years.

For 50 cities: the number exceeds $10^{62}$. The fastest conceivable computer running since the Big Bang would not finish.

![Log-scale line chart with x-axis "Number of cities"](images/12-graph-theory-fig-06.png)
*Figure 12.6 — Log-scale line chart with x-axis "Number of cities"*

The growth is factorial — it outruns exponential growth, outruns any polynomial. No algorithm defeats this in the worst case. TSP is **NP-hard**: a polynomial-time algorithm for it would imply polynomial-time solutions for every problem in NP. That equivalence — whether P equals NP — is one of the deepest unsolved problems in mathematics, open since 1971, carrying a $1,000,000 prize.

This is not a limitation computers will eventually overcome with more processing power. It is a structural property of the problem. Hamilton cycles depend on global structure, and no known shortcut replaces exhaustive search.

---

## What You Do Instead

The world still needs delivery routes. Millions of packages are routed daily. School buses serve hundreds of thousands of stops. Airlines schedule tens of thousands of flights. None of them use brute force.

They use **heuristics** — algorithms that find good tours quickly without guaranteeing optimality.

The simplest is the **nearest neighbor heuristic**: start at any city. At each step, go to the closest unvisited city. When all cities are visited, return home. This runs in time proportional to $n^2$ — fast enough that 10,000 cities takes seconds.

The quality is not guaranteed. Nearest-neighbor typically produces a tour within 20–30% of optimal. No certificate of optimality. But for routing 500 delivery stops per driver across thousands of routes per day, a tour that is 15% longer than optimal — delivered in milliseconds — is worth far more than a provably optimal tour computed over hours, especially since traffic and new orders change the problem hour by hour.

More sophisticated heuristics push closer to optimal: Lin-Kernighan edge exchanges, simulated annealing, branch-and-bound with clever bounds. These methods can solve instances with tens of thousands of cities to near-optimality given enough computation. The world record for exact TSP solution (as of recent years) involves instances with tens of thousands of cities — solved not by brute force but by decades of accumulated algorithmic ingenuity.

In 2016, MIT researchers applied TSP-related optimization to Boston's school bus system: 30,000 students, hundreds of routes, decades of accumulated inefficiency. The result was $5 million per year in savings and a reduction of 9,000 kilograms of CO₂ per day. The solution was not globally optimal. It was good enough to make a large practical difference — which is, in most real contexts, the right standard.

The trade-off is fundamental and will not go away:

**Exact:** guaranteed optimal, exponential time, practical only for small instances.

**Heuristic:** fast, good-but-not-proven, practical for large instances.

Which you choose depends on the cost of suboptimality vs. the cost of computation time. For most real applications, heuristic wins.

| Solution quality | Computation time | Practical limit (cities) | When to use |
| --- | --- | --- | --- |
| "Exact (brute force)", "Nearest-neighbor heuristic", "Sophisticated heuristic (Lin-Kernighan, etc.)" | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. | A concrete checkpoint for applying the chapter concept. |
| columns: "Solution quality", "Computation time", "Practical limit (cities)", "When to use". Cells filled with specific values: exact = optimal | exponential | ~15 cities | small high-stakes problems |
| nearest-neighbor = ~20-30% above optimal | $O(n^2)$ | thousands | real-time routing |
| sophisticated = ~1-5% above optimal | hours | tens of thousands | airline scheduling, chip design. Student should see the three options as a genuine trade-off space, not a ranking. |

---

## The Distinction That Carries Forward

The chapter opened with a puzzle about bridges. It ended with a puzzle about cities. They feel like variations on a theme. They are not.

Bridge puzzle: visit every **edge** exactly once.

City puzzle: visit every **vertex** exactly once.

That one word — edge vs. vertex — separates a problem solvable in seconds from one that is computationally intractable at scale.

For the Euler problem, degree is everything: a local condition, checkable in linear time, sufficient and necessary. Efficient.

For the Hamilton problem, degree tells you almost nothing: the condition is global, checkable only by search, exponential in the worst case. Hard.

This is not a coincidence or an artifact of how the problems were posed. It reflects something deep about the structure of mathematical problems. Local conditions — properties you can check vertex by vertex — collapse into fast algorithms. Global conditions — properties that depend on how the whole graph fits together — resist them.

Whether you are routing mail carriers (edges), planning delivery tours (vertices), scheduling circuit inspections (edges), or analyzing social networks (shortest paths between vertices), the first question is: what exactly am I trying to visit? The mathematical machinery, and the computational cost, depend entirely on the answer.

---

## Still Open

I do not fully understand why degree conditions are sufficient and necessary for Euler circuits but have no analogue for Hamilton cycles. The intuition is clear — edges and vertices are different objects, and local structure governs the former while global structure governs the latter. But the formal explanation of why local structure suffices for one and not the other runs into complexity theory and algebraic combinatorics that this chapter does not reach.

The gap between the two problems is one of the clearest signatures of the P vs. NP divide. Nobody fully understands why that divide exists where it does, or whether it is as absolute as we believe. The Königsberg bridges and the traveling salesman are, in some sense, still waiting for a deeper explanation.
---

## LLM Exercise — Chapter 12: Graph Theory (Audit a Real-World System Project)

**Project:** Audit one real-world system through 13 chapters of mathematics.
**What you're building this chapter:** a graph-theoretic model of the system — vertices, edges, paths, Euler / Hamilton circuits, shortest-path or coverage problem solved on the graph.
**Tool:** **Claude Project** (same system spec as Ch 1).

**The Prompt:**

```
Chapter 12 of my system-audit project. Chapter 12 covered:
graphs as vertices + edges; vertex degree; Euler's argument
(an Euler circuit exists iff every vertex has even degree —
the Königsberg bridges, 1736); the Chinese postman problem
(find the shortest route that covers every edge); the
traveling salesperson problem (find the shortest route that
visits every vertex — NP-hard).

Apply to my system. Most systems can be modeled as graphs;
the modeling itself is half the work.

1. **Model your system as a graph.** Choose vertices and
   edges deliberately. Examples:
   - Transit: stations as vertices, segments between
     adjacent stations as edges, segment travel times
     as edge weights.
   - Streaming: content items as vertices, "users who
     watched both" relationships as edges.
   - Sports: teams as vertices, games played as edges
     (or wins as directed edges).
   - Restaurant: tables and stations as vertices, server
     paths as edges.
   - Hospital: ED bays and resources as vertices, patient
     transfers as edges.
   - Election: precincts as vertices, ballot-transport
     routes as edges.
   State the choice clearly. List the vertex set and at
   least 5 representative edges with weights.

2. **Compute degrees.** What's the highest-degree vertex
   (the most-connected node)? What does that mean in real
   terms? (The most-connected station; the most-watched
   content; the busiest player; the most-allocated bay.)

3. **Check for an Euler circuit.** Does your graph have
   one? (Recall: every vertex must have even degree.) If
   yes, does the system actually use it? If no, identify
   which vertices have odd degree and what real-world
   feature creates the asymmetry.

4. **Solve a real shortest-path problem on your graph.**
   Pick two specific vertices. Find the shortest path
   between them. Show the work (Dijkstra-style if you
   want, or just by inspection on a small graph).

5. **Apply the Chinese postman or TSP framing.** Pick
   one and apply it:
   - Postman (cover every edge): if your system has a
     coverage requirement (a postal route, a maintenance
     schedule, an inspection cycle), what's the optimal
     route?
   - TSP (visit every vertex): if your system has a
     visit-every-node requirement (a tour, a delivery
     route, a meter-reader's day), what's the (approximately)
     shortest route? Explain why the exact answer is
     computationally hard and what heuristic you used.

6. **Identify one structural inefficiency the graph
   reveals.** Often the graph view exposes a missing
   edge (a connection that would dramatically shorten
   paths) or a redundant edge (a connection that adds
   cost without value). Name one for your system.

End with: a one-page "structural audit" of the system. The
graph model. The high-degree vertex. The Euler-circuit check.
The shortest-path solution. The TSP / postman framing. The
structural inefficiency identified.
```

**What this produces:** A structural audit. Graph theory's value is that it surfaces structural questions the system itself doesn't ask — a missing edge, a high-degree node, an inefficient route.

**Connection to previous chapters:** Builds on Ch 10 (geometric distances often become edge weights) and Ch 1 (the categories you identified often correspond to vertex labels).

**Preview of next chapter:** Chapter 13 — the close. Apply golden ratio, Fibonacci, equal-temperament, and aesthetic-mathematical reasoning to the system. Most systems have at least one place where pattern, proportion, or musical-ratio reasoning illuminates a design choice. Then the final synthesis: a 25-30 page integrated audit using all 13 lenses.

---

##  AI Wayback Machine
**Paul Erdős** was prolific Hungarian mathematician who wrote over 1,500 papers and lived out of suitcases his entire adult life — and built a substantial portion of modern graph theory.

**Run this:**

```
Who is Paul Erdős, and how does their work connect to graph theory we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Paul Erdős"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Paul Erdős's ideas to a specific concrete problem in this chapter.
- Add a constraint: "Answer including criticisms or limits of Paul Erdős's framework."

What changes? What gets better? What gets worse?
