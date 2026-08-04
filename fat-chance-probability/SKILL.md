---
name: fat-chance-probability
description: 'Knowledge base from "Fat Chance: Probability from 0 to 1". Use when the user asks about probability, combinatorics, counting, Bayes theorem, expected value, normal distribution, or statistical pitfalls. Also trigger on probability, combinatorics, statistics keywords.'
---

# Fat Chance: Probability from 0 to 1

You are a probability tutor who knows the book *Fat Chance* inside out. The book has three parts: **Counting (Ch1-7) → Probability (Ch8-11) → Big Picture Probability (Ch12-14)**. The core methodology is "reduction": transform an unfamiliar problem into a solved one.

Always explain concepts in plain language first, then show the formula. Prefer examples.

---

## Core Frameworks

### Counting: The Four Principles

**Reduction (化归)**: The book's core method. Don't solve a new problem from scratch — transform it into something you already know how to solve.

**Multiplication Principle**: If you make a sequence of independent choices, the total count = product of choices at each step.
- Sequences with repetition allowed: n^k
- Sequences without repetition: n!/(n-k)!
- Trick: If you get stuck, try **changing the order of choices** (e.g., for a 3-digit odd number, pick the units digit first).

**Subtraction Principle**: Count what you DON'T want and subtract from the total. For "at least one X", count "zero X" and subtract — almost always easier.

**Inclusion-Exclusion**: If you subtract overlapping categories, you must ADD BACK the intersection.
- #(A ∪ B) = #A + #B − #(A ∩ B)
- For three sets: #A + #B + #C − #(A∩B) − #(A∩C) − #(B∩C) + #(A∩B∩C)

### Combinations and Binomial Coefficients

**Combination vs Sequence**: Order matters = sequence; order doesn't matter = combination.
- C(n,k) = n! / (k!(n-k)!) — "n choose k"
- Symmetry: C(n,k) = C(n,n-k) — choosing k is the same as choosing n-k to exclude

**Four-Formula Table**:
| Type | Order matters? | Repetition? | Formula |
|------|---------------|-------------|---------|
| Passwords, license plates | Yes | Yes | n^k |
| Officers, rankings | Yes | No | n!/(n-k)! |
| Committees, poker hands | No | No | C(n,k) |
| Fruit bowl, prizes | No | Yes | C(n+k-1, k) |

**Multinomial Coefficients**: (n; a_1,...,a_k) = n!/(a_1!···a_k!) — for grouping, anagrams.

**Pascal's Recurrence**: C(n,k) = C(n-1,k-1) + C(n-1,k). Each coefficient = sum of the two above it.

**Binomial Theorem**: (x+y)^n coefficient of x^k·y^(n-k) is C(n,k). Set x=y=1 → row sum = 2^n. Set x=1, y=-1 → alternating sum = 0.

**Catalan Numbers**: c_n = C(2n,n)/(n+1) — counts legal parentheses, paths staying below diagonal, triangulations. Use the **reflection principle** to count violating paths.

### Probability Fundamentals

**Equally Likely Paradigm**: P(event) = favorable outcomes / total outcomes. Prerequisite: all outcomes equally likely.

**Expected Value**: ev = Σ p_i·a_i — the long-run average payout per round. Always compare strategies by EV.

**Conditional Probability**: P(W|A) = P(W and A) / P(A).
- Total probability: P(W) = Σ P(A_i)·P(W|A_i)
- P(A|B) ≠ P(B|A) — this inversion error is the most common statistical trap.

**Bayes Theorem**: P(M|A) = P(A|M)·P(M) / P(A). Used to reverse conditional probabilities.

**Monty Hall**: ALWAYS switch doors. Win rate from switching = probability your initial choice was WRONG (2/3 with three doors).

**Independence**: P(W|A) = P(W), or equivalently P(W and A) = P(W)·P(A). Coin tosses are independent; card draws from a deck are not.

**Bernoulli Trials**: n independent trials, each with success probability p.
- P(exactly k successes) = C(n,k)·p^k·(1-p)^(n-k)
- Peak is around np

**Gambler's Ruin**: P(winning) = (s^a − 1) / (s^b − 1), where s = q/p, a = your stake, b = total stake.
- If p < 1/2, small bets over long periods → nearly certain ruin
- The optimal strategy when odds are against you: go ALL IN (one big bet)

**Geometric Probability**: P = favorable area / total area (uniform distribution assumed).

### Big Picture Probability

**Variance**: var = Σ p_i·(a_i − ev)^2. Standard deviation: std = √var.

**Game Arithmetic**:
| Operation | Effect on EV | Effect on Variance |
|-----------|-------------|-------------------|
| Add constant c | ev + c | unchanged |
| Multiply by d | d·ev | d^2·var |
| Sum independent | sum of EVs | sum of variances |
| Repeat n times | n·ev | n·var (std grows by √n) |

**Standardization**: G^0 = (G − ev) / √var, making ev = 0, var = 1.

**Normal Distribution**: After many repetitions, the standardized distribution approaches the bell curve f(x) = e^(-x^2/2) / √(2π).
- **Z-score**: z = (A − ev) / std — measures "how many standard deviations away"
- **Z-table**: gives P(Z ≤ z); use for probability calculations
- **Margin of error**: ≈ 2·std (for two-sided 5% significance)

### Statistical Traps (Chapter 14 — Critical!)

**Inverted Conditional Probability**: The MOST common mistake. Confusing P(symptom | disease) with P(disease | symptom).

**False Positive Trap**: A 99% reliable test + 1% prevalence → positive result means only ~50% chance of actually having the disease. Rare diseases should not be universally screened.

**Simpson's Paradox**: A trend appearing in ALL subgroups CAN reverse when the groups are combined. Caused by unequal group sizes.

**Random Correlation**: Run enough tests, and some WILL appear correlated by chance. 5000 coin pairs flipped 100 times each → a few will look "mysteriously correlated". A 100-item survey will have some pairs appear highly correlated — needs follow-up study.

**Hot Hand Fallacy**: Believing a streak will continue. **Gambler's Fallacy**: Believing independent events will "self-correct." Humans underestimate streak probabilities (100 coin flips → ~6 consecutive heads on average).

---

## Key Thresholds

| Fact | Value |
|------|-------|
| 0! | 1 (convention) |
| C(n,0) = C(n,n) | 1 |
| Birthday problem >50% | 23 people |
| 50 people same birthday | 97% |
| Significance threshold | z ≈ ±2 (≈1.96) |
| Margin of error | ≈ 2·std |
| Longest run of heads in 100 flips | ~6 on average |
| All-in win rate (p<1/2) | Exactly p (optimal) |
| Small bets over time (p<1/2) | Nearly certain ruin |

---

## Decision Rules

1. **"At least one X"** → Use subtraction: count "zero X" and subtract.
2. **Overlapping exclusions** → Inclusion-exclusion. Subtract then add back overlaps.
3. **Multiplication stuck?** → Change choice order OR decompose differently.
4. **Compare gambles?** → Compare EV. Lower variance is only better when EV is positive.
5. **Large-n experiments** → Compute ev = n·ev(G), std = √(n·var(G)), then z = (A−ev)/std, check Z-table.
6. **Medical screening** → Always compute P(disease|positive) = p·r / [p·r + (1-p)(1-r)].

## Common Pitfalls Scent Guide

| Trigger | Likely trap |
|---------|------------|
| "At least one X" | Use subtraction principle |
| Two exclusions with overlap | Inclusion-exclusion |
| Mixing P(A|B) and P(B|A) | Inverted conditional probability |
| Rare disease screening ad | False positives > true positives |
| Subgroups win, combined loses | Simpson's paradox |
| "Two survey questions highly correlated" | Random correlation — follow up |
| "It's due for tails" after heads | Gambler's fallacy (independence) |
| "They're on a hot streak" | Hot hand fallacy (check statistics) |
| "Small bets are safe long-term" | Gambler's ruin (p<1/2 = inevitable loss) |
| Poll margin of error as guarantee | Only random fluctuation, not systematic bias |
| 5% significance = 98% probability | Bayesian trap — need to check prior |

## Counterintuitive Results

| Phenomenon | Intuition | Reality |
|-----------|-----------|---------|
| Birthday problem | 100+ people needed | 23 people > 50% |
| Monty Hall | Switching doesn't matter | Switching wins 2/3 |
| False positive (99% test, 1% prevalence) | Positive = 99% chance sick | Positive = ~50% |
| Chuck-A-Luck (three dice, at least one 6) | ~50% win rate | ~42% (house edge) |
| Longest heads run in 100 flips | 3-4 | Average ~6 |
