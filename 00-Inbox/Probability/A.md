
---
# Question 1 — Joint Distribution, Covariance, Correlation (15 marks)

## Setting up the joint distribution

You have two random variables:

- $P(X=1) = P(X=-1) = \frac{1}{2}$
- $P(Y=1) = P(Y=-1) = \frac{1}{2}$
- $c = P(X=1, Y=1)$

The joint table has 4 cells. Since the marginals must hold, you can express all 4 joint probabilities in terms of $c$:

$$
\begin{array}{c|cc|c}
 & Y=1 & Y=-1 & \text{Row total} \\
\hline
X=1 & c & \frac{1}{2}-c & \frac{1}{2} \\
X=-1 & \frac{1}{2}-c & c & \frac{1}{2} \\
\hline
\text{Col total} & \frac{1}{2} & \frac{1}{2} & 1
\end{array}
$$
Or:

|           | Y = 1             | Y = -1            | Row total     |
| --------- | ----------------- | ----------------- | ------------- |
| X = 1     | $c$               | $\frac{1}{2} - c$ | $\frac{1}{2}$ |
| X = -1    | $\frac{1}{2} - c$ | $c$               | $\frac{1}{2}$ |
| Col total | $\frac{1}{2}$     | $\frac{1}{2}$     | 1             |

**How to fill the table:** Row for $X=1$ must sum to $\frac{1}{2}$, so $P(X=1, Y=-1) = \frac{1}{2} - c$. Column for $Y=1$ must sum to $\frac{1}{2}$, so $P(X=-1, Y=1) = \frac{1}{2} - c$. The last cell is $1 - c - (\frac{1}{2}-c) - (\frac{1}{2}-c) = c$.

**Valid range of $c$:** all probabilities must be $\geq 0$, so $c \geq 0$ and $\frac{1}{2} - c \geq 0$, meaning $0 \leq c \leq \frac{1}{2}$.

---

## Part (a) — Cov(X, Y) and Corr(X, Y)

**Step 1: Find E[X] and E[Y]**

$$E[X] = (1)\cdot\tfrac{1}{2} + (-1)\cdot\tfrac{1}{2} = 0$$ $$E[Y] = (1)\cdot\tfrac{1}{2} + (-1)\cdot\tfrac{1}{2} = 0$$

**Step 2: Find E[XY]**

$$E[XY] = \sum_{x,y} xy \cdot P(X=x, Y=y)$$

| $(x, y)$  | $xy$ | $P$             | contribution       |
| --------- | ---- | --------------- | ------------------ |
| $(1,1)$   | $1$  | $c$             | $c$                |
| $(1,-1)$  | $-1$ | $\frac{1}{2}-c$ | $-(\frac{1}{2}-c)$ |
| $(-1,1)$  | $-1$ | $\frac{1}{2}-c$ | $-(\frac{1}{2}-c)$ |
| $(-1,-1)$ | $1$  | $c$             | $c$                |

$$E[XY] = c - \left(\tfrac{1}{2}-c\right) - \left(\tfrac{1}{2}-c\right) + c = 4c - 1$$

**Step 3: Covariance**

$$\text{Cov}(X,Y) = E[XY] - E[X]E[Y] = (4c-1) - 0 = \boxed{4c - 1}$$

**Step 4: Variances**

$$E[X^2] = (1)^2\cdot\tfrac{1}{2} + (-1)^2\cdot\tfrac{1}{2} = 1 \implies \text{Var}(X) = 1 - 0^2 = 1$$ $$\text{Similarly, } \text{Var}(Y) = 1$$

**Step 5: Correlation**

$$\text{Corr}(X,Y) = \frac{\text{Cov}(X,Y)}{\sqrt{\text{Var}(X)}\sqrt{\text{Var}(Y)}} = \frac{4c-1}{1 \cdot 1} = \boxed{4c - 1}$$

---

## Part (b) — Value of c for independence

$X$ and $Y$ are independent iff $\text{Cov}(X,Y) = 0$ (and since Corr = Cov here, same condition):

$$4c - 1 = 0 \implies \boxed{c = \frac{1}{4}}$$

**Check:** If $c = \frac{1}{4}$, then $P(X=1,Y=1) = \frac{1}{4} = P(X=1)\cdot P(Y=1)$. ✓

---

## Part (c) — Perfect positive and negative correlation

**Perfect positive correlation:** $\text{Corr}(X,Y) = +1$ $$4c - 1 = 1 \implies 4c = 2 \implies \boxed{c = \frac{1}{2}}$$

**Perfect negative correlation:** $\text{Corr}(X,Y) = -1$ $$4c - 1 = -1 \implies 4c = 0 \implies \boxed{c = 0}$$

**Intuition check:**

- $c = \frac{1}{2}$: $X$ and $Y$ always take the same value (both $+1$ or both $-1$). Perfect positive correlation makes sense.
- $c = 0$: $X$ and $Y$ always take opposite values. Perfect negative correlation makes sense.

---

---

# Question 2 — Central Limit Theorem (5 marks)

Let $S = X_1 + X_2 + \cdots + X_{81}$, where each $X_i$ has $\mu = 5$, $\sigma^2 = 4$.

**Step 1: Find the mean and variance of S**

$$E[S] = 81 \times 5 = 405$$ $$\text{Var}(S) = 81 \times 4 = 324 \implies \sigma_S = \sqrt{324} = 18$$

**Step 2: Standardize**

$$P(S > 369) = P\left(Z > \frac{369 - 405}{18}\right) = P\left(Z > \frac{-36}{18}\right) = P(Z > -2)$$

**Step 3: Use symmetry of the standard normal**

$$P(Z > -2) = P(Z < 2) = \Phi(2)$$

From Z-tables: $\Phi(2) = 0.9772$

$$\boxed{P(S > 369) \approx 0.9772}$$

---
# Correct Q3

This is a crucial clarification. Each compartment connects to exactly **2** others. Let me re-derive the connections:

From your examples:

- **1** → reaches 2 or 3 (1 step), needs 2 steps for 4
- **5** → reaches 4 or 6 (1 step), needs 2 steps for 3

So 5 connects to **4 and 6 only**, NOT to 2 or 3. Let me rebuild the full connection table:

|Compartment|Direct neighbors (1 step)|
|---|---|
|1|2, 3|
|2|1, 4|
|3|1, 6|
|4|2, 5|
|5|4, 6|
|6|3, 5|

**Every compartment has exactly 2 neighbors ✓**

This is actually a simple **loop/cycle**: $1 \leftrightarrow 2 \leftrightarrow 4 \leftrightarrow 5 \leftrightarrow 6 \leftrightarrow 3 \leftrightarrow 1$

---

# Question 3 — Fully Corrected Solution

### Figure for Q3:
```plaintext
				  +--------------------+
				  |                    |
				  |    |               |
		+---------+    |      4        |
        |              |----------     |
+-------+   |          |               |
|           |   2      |               |
|   1       |          |      5        |
|           |----------|               |
+-------+   |          |               |
        |   |   3      |-----    ------+
        |              |               |
        +---------+    |               |
		          |    |      6        |
				  |                    |
			      +--------------------+
				   
```
## Part (a) — Transition Matrix

Since every compartment has exactly **2 neighbors**, every transition probability is $\frac{1}{2}$.
$$
P = \begin{array}{c|cccccc}
& 1 & 2 & 3 & 4 & 5 & 6 \\
\hline
1 & 0 & \frac{1}{2} & \frac{1}{2} & 0 & 0 & 0 \\
2 & \frac{1}{2} & 0 & 0 & \frac{1}{2} & 0 & 0 \\
3 & \frac{1}{2} & 0 & 0 & 0 & 0 & \frac{1}{2} \\
4 & 0 & \frac{1}{2} & 0 & 0 & \frac{1}{2} & 0 \\
5 & 0 & 0 & 0 & \frac{1}{2} & 0 & \frac{1}{2} \\
6 & 0 & 0 & \frac{1}{2} & 0 & \frac{1}{2} & 0
\end{array}
$$
**What to draw:** Six circles in a hexagonal cycle: $1-2-4-5-6-3-1$. Every arrow between adjacent pairs labeled $\frac{1}{2}$ in both directions.

---

## Part (b) — Starting in compartment 4

### i. At time 1

From compartment 4, the mouse goes to **2 or 5**, each with probability $\frac{1}{2}$. Cannot reach 4 in one step.

$$\boxed{P(X_1 = 4 \mid X_0 = 4) = 0}$$

---

### ii. At time 2

At $t=1$: $P(X_1 = 2) = \frac{1}{2}$, $P(X_1 = 5) = \frac{1}{2}$

From each, probability of reaching 4:

- From 2: neighbors are {1, 4} → $P_{24} = \frac{1}{2}$
- From 5: neighbors are {4, 6} → $P_{54} = \frac{1}{2}$

$$P(X_2 = 4) = \frac{1}{2}\cdot\frac{1}{2} + \frac{1}{2}\cdot\frac{1}{2} = \frac{1}{4} + \frac{1}{4}$$

$$\boxed{P(X_2 = 4 \mid X_0 = 4) = \frac{1}{2}}$$

---

### iii. At time 3

**Full state distribution at $t=2$:**

From $t=1$: $\mathbf{p}^{(1)} = [0,\ \tfrac{1}{2},\ 0,\ 0,\ \tfrac{1}{2},\ 0]$

**From state 2** (prob $\frac{1}{2}$), neighbors {1, 4}: $$\tfrac{1}{2}\times[\tfrac{1}{2},\ 0,\ 0,\ \tfrac{1}{2},\ 0,\ 0] = [\tfrac{1}{4},\ 0,\ 0,\ \tfrac{1}{4},\ 0,\ 0]$$

**From state 5** (prob $\frac{1}{2}$), neighbors {4, 6}: $$\tfrac{1}{2}\times[0,\ 0,\ 0,\ \tfrac{1}{2},\ 0,\ \tfrac{1}{2}] = [0,\ 0,\ 0,\ \tfrac{1}{4},\ 0,\ \tfrac{1}{4}]$$

$$\mathbf{p}^{(2)} = \left[\frac{1}{4},\ 0,\ 0,\ \frac{1}{2},\ 0,\ \frac{1}{4}\right]$$

_(confirms $p^{(2)}_4 = \frac{1}{2}$ ✓)_

**At $t=3$:** compartment 4 is reachable only from states **2** ($P_{24}=\frac{1}{2}$) and **5** ($P_{54}=\frac{1}{2}$). But $p^{(2)}_2 = 0$ and $p^{(2)}_5 = 0$:

$$P(X_3 = 4) = p^{(2)}_2 \cdot\frac{1}{2} + p^{(2)}_5 \cdot\frac{1}{2} = 0\cdot\frac{1}{2} + 0\cdot\frac{1}{2}$$

$$\boxed{P(X_3 = 4 \mid X_0 = 4) = 0}$$

**Intuition:** This makes perfect sense. The maze is a 6-node cycle. Starting at node 4, the mouse can only be at **even-distance** nodes at even times and **odd-distance** nodes at odd times. At $t=1,3$ (odd steps) the mouse must be in {2, 5} — it can never be back at 4 at an odd time step.

---

## Summary for Q3

|Part|Answer|
|---|---|
|(a)|Cycle graph $1-2-4-5-6-3-1$; all transitions = $\frac{1}{2}$|
|(b)(i)|$0$|
|(b)(ii)|$\frac{1}{2}$|
|(b)(iii)|$0$|

---
# Question 4 — Urban/Suburban/Rural Markov Chain (10 marks)

> ⚠️ The transition matrix appears as an image I cannot read. **Please share the matrix values** and I'll solve parts (a), (b), and (c) fully.

That said, here is the **complete method** you'd apply:

---

## Part (a) — State Transition Diagram

Draw three circles: U, S, R. For each nonzero entry $P_{ij}$ in the matrix, draw an arrow from state $i$ to state $j$ labeled with that probability. Self-loops (staying in same state) are drawn as curved arrows on the same circle.

---

## Part (b) — P(Suburban → Rural in 15 years)

15 years = 3 periods of 5 years each. Compute $P^3$ (matrix cubed). The answer is the $(S, R)$ entry of $P^3$.

**How to compute $P^3$:** $P^3 = P \cdot P \cdot P$, doing standard matrix multiplication twice.

The answer is: $\left(P^3\right)_{SR}$

---

## Part (c) — Population distribution in 15 years

Initial distribution vector: $\boldsymbol{\pi}^{(0)} = [0.50,\ 0.25,\ 0.25]$ (U, S, R).

After 15 years (3 steps): $$\boldsymbol{\pi}^{(3)} = \boldsymbol{\pi}^{(0)} \cdot P^3$$

This is a row vector times the matrix $P^3$. The result gives $[P(U),\ P(S),\ P(R)]$ after 15 years.

---

Send me the matrix and I'll compute the exact numerical answers for Q4 right away!

---


|     | U   | S   | R   |
| --- | --- | --- | --- |
| U   | 0.7 | 0.1 | 0.2 |
| S   | 0.1 | 0.8 | 0.1 |
| R   | 0.1 | 0.1 | 0.8 |
