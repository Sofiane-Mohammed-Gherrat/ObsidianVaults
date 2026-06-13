# Question 3 — Mouse Maze Markov Chain (10 marks)

Since the maze diagram is not visible to me, I'll use the **most standard version** of this 4-compartment maze that appears in probability textbooks. **Please verify your maze matches this layout:**

```
+-------+-------+
|       |       |
|   1   |   2   |
|       |       |
+---+---+---+---+
        |
    +---+---+
    |       |
    |   3   |
    |       |
    +---+---+
        |
    +---+---+
    |       |
    |   4   |
    |       |
    +-------+
```

With connections: 1↔2, 1↔3, 2↔3, 3↔4. (Compartment 4 connects only to 3.)

> ⚠️ **If your maze has different connections, the transition matrix changes. Adjust accordingly using the same method below.**

---

## Part (a) — Transition Diagram

From the adjacency above:

|From \ To|1|2|3|4|
|---|---|---|---|---|
|**1**|0|1/2|1/2|0|
|**2**|1/2|0|1/2|0|
|**3**|1/3|1/3|0|1/3|
|**4**|0|0|1|0|

**Logic:** Each row must sum to 1, and each adjacent compartment gets equal probability.

- Compartment 1 has 2 neighbors (2 and 3) → each gets probability $\frac{1}{2}$
- Compartment 2 has 2 neighbors (1 and 3) → each gets probability $\frac{1}{2}$
- Compartment 3 has 3 neighbors (1, 2, 4) → each gets probability $\frac{1}{3}$
- Compartment 4 has 1 neighbor (3 only) → gets probability $1$

**What to draw:** Circles labeled 1, 2, 3, 4 with directed arrows and the probabilities labeled on each arrow.

---

## Part (b) — Starting in compartment 4

Let $\mathbf{p}^{(0)} = [0, 0, 0, 1]$ (mouse starts in compartment 4).

The transition matrix $P$ is as above. Let rows/columns be ordered 1, 2, 3, 4.

**i. At time 1:**

From compartment 4, the mouse can only go to compartment 3 (prob = 1).

$$P(X_1 = 4 \mid X_0 = 4) = P_{44} = 0$$

$$\boxed{P(X_1 = 4) = 0}$$

---

**ii. At time 2:**

At time 1 the mouse is in compartment 3 with probability 1. From compartment 3, the mouse goes to compartment 4 with probability $\frac{1}{3}$.

$$P(X_2 = 4 \mid X_0 = 4) = P_{43} \cdot P_{34} = 1 \times \frac{1}{3}$$

$$\boxed{P(X_2 = 4) = \frac{1}{3}}$$

---

**iii. At time 3:**

At time 2, the mouse is in compartment 4 with prob $\frac{1}{3}$, and in compartments 1, 2 with some probability. Let's track the full state vector at $t=2$:

From $t=0$: in state 4. From $t=1$: in state 3 (prob 1). From $t=2$, using row 3 of $P$: $$\mathbf{p}^{(2)} = \left[\frac{1}{3},\ \frac{1}{3},\ 0,\ \frac{1}{3}\right]$$

Now at $t=3$, we want $P(X_3 = 4)$. Only compartment 3 can reach compartment 4. So:

$$P(X_3 = 4) = P(X_2 = 1)\cdot P_{14} + P(X_2 = 2)\cdot P_{24} + P(X_2 = 3)\cdot P_{34} + P(X_2 = 4)\cdot P_{44}$$

$$= \frac{1}{3}\cdot 0 + \frac{1}{3}\cdot 0 + 0\cdot\frac{1}{3} + \frac{1}{3}\cdot 0 = 0$$

$$\boxed{P(X_3 = 4) = 0}$$

**Intuition:** To be in compartment 4 at time $t$, you must have been in compartment 3 at time $t-1$. To be in compartment 3 at time $t-1$, you can't have been in compartment 4 (since from 4 you go to 3, not stay). There's a parity pattern here — the mouse can only be in compartment 4 at even times after $t=0$.

---