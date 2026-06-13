
Good catch! Let me redo everything cleanly with the corrected graph.
## My Correction

| Node | Children (alphabetical) | Edge Costs |
| ---- | ----------------------- | ---------- |
| S    | A, B, C                 | 2, 1, 4    |
| A    | D, E                    | 2, 5       |
| B    | E, F                    | 3, 3       |
| C    | F, H                    | 1, 6       |
| D    | A, I                    | 2, 4       |
| E    | I, J                    | 1, 3       |
| F    | B, J, K                 | 3, 2, 2    |
| H    | K, L                    | 1, 5       |
| J    | M                       | 1          |
| M    | J, G1                   | 1, 3       |
| K    | F, G2                   | 2, 6       |
| L    | G3                      | 2          |

---

# Corrected Search Algorithms on Figure 3

## Graph Reference (Corrected)

|Node|Children|Edge Costs|
|---|---|---|
|S|A, B, C|2, 1, 4|
|A|D, E|2, 5|
|B|E, F|3, 3|
|C|F, H|1, 6|
|D|A, I|2, 4|
|E|I, J|1, 3|
|F|B, J, K|3, 2, 2|
|H|K, L|1, 5|
|J|M|1|
|M|J, G1|1, 3|
|K|F, G2|2, 6|
|L|G3|2|

> **Loop avoidance rule:** If a node already exists on the **current path**, skip it. Alphabetical order when tie-breaking.

---

## 1. Depth-First Search (DFS)

**Strategy:** Deepest node first, alphabetical when tied. Backtrack if dead end or loop detected.

### Traversal (trace every step):

```
S → A → D → A (ancestor, skip) → I (dead end, backtrack)
      → E → I (dead end) → J → M → J (ancestor, skip) → G1 ✓
```

**Order:** $$S \rightarrow A \rightarrow D \rightarrow I \rightarrow E \rightarrow J \rightarrow M \rightarrow G1$$

**Path taken:** S→A→E→J→M→G1

**Cost:** $2+5+3+1+3 = \textbf{14}$

**a) Goal: G1** **b) Nodes visited: S, A, D, I, E, J, M, G1**

---

## 2. Breadth-First Search (BFS)

**Strategy:** Expand all nodes at current depth before going deeper. Alphabetical within same level.

### Level by level:

|Level|Node Expanded|Children Added to Queue|
|---|---|---|
|0|S|A, B, C|
|1|A|D, E|
|1|B|E, F|
|1|C|F, H|
|2|D|I (A is ancestor on S→A→D path, skip)|
|2|E|I, J|
|2|F|J, K (B is ancestor, skip)|
|2|H|K, L|
|3|I|dead end|
|3|J|M|
|3|K|G2 ✓|

> K is expanded at level 3 and G2 is found immediately.

**Order:** $$S \rightarrow A \rightarrow B \rightarrow C \rightarrow D \rightarrow E \rightarrow F \rightarrow H \rightarrow I \rightarrow J \rightarrow K \rightarrow G2$$

**Shortest path to G2:** S→B→F→K→G2

**Cost:** $1+3+2+6 = \textbf{12}$

**a) Goal: G2** **b) Nodes visited: S, A, B, C, D, E, F, H, I, J, K, G2**

---

## 3. Iterative Deepening Search (IDS)

**Strategy:** DFS with increasing depth limit $d = 0, 1, 2, \ldots$

### Depth limit = 0:

$$S \quad \text{no goal}$$

### Depth limit = 1:

$$S \rightarrow A,\ B,\ C \quad \text{no goal}$$

### Depth limit = 2:

$$S \rightarrow A \rightarrow D,\ E$$ $$S \rightarrow B \rightarrow E,\ F$$ $$S \rightarrow C \rightarrow F,\ H \quad \text{no goal}$$

### Depth limit = 3:

$$S \rightarrow A \rightarrow D \rightarrow I$$ $$S \rightarrow A \rightarrow E \rightarrow I,\ J$$ $$S \rightarrow B \rightarrow E \rightarrow I,\ J$$ $$S \rightarrow B \rightarrow F \rightarrow J,\ K$$ $$S \rightarrow C \rightarrow F \rightarrow J,\ K$$ $$S \rightarrow C \rightarrow H \rightarrow K,\ L \quad \text{no goal — goals are 1 level deeper}$$

### Depth limit = 4:

Expanding M (from J) and checking K's children:

$$S \rightarrow A \rightarrow D \rightarrow I \text{ (dead end)}$$ $$S \rightarrow A \rightarrow E \rightarrow J \rightarrow M$$ $$S \rightarrow B \rightarrow F \rightarrow K \rightarrow \mathbf{G2}\ \checkmark$$

> G2 is found at depth 4 via S→B→F→K→G2

**a) Goal: G2** **b) Nodes visited (final iteration):** S, A, B, C, D, E, F, H, I, J, K, L, M, G2

**Cost of path found:** $1+3+2+6 = \textbf{12}$

---

## 4. Uniform Cost Search (UCS)

**Strategy:** Always expand the node with the **lowest cumulative cost** from start.

### Priority queue trace:

|Step|Node Expanded|Cumulative Cost|Frontier (node: cost)|
|---|---|---|---|
|1|S|0|A:2, B:1, C:4|
|2|B|1|A:2, C:4, E:4, F:4|
|3|A|2|C:4, D:4, E:4, E:7, F:4|
|4|C|4|D:4, E:4, E:7, F:4, F:5, H:10|
|5|D|4|E:4, E:7, F:4, F:5, H:10, I:8|
|6|E (via B)|4|E:7, F:4, F:5, H:10, I:5, I:8, J:7|
|7|F (via B)|4|E:7, F:5, H:10, I:5, I:8, J:6, J:7, K:6|
|8|I (via E,B)|5|E:7, F:5, H:10, I:8, J:6, J:7, K:6|
|9|F (via C)|5|E:7, H:10, I:8, J:6, J:6, J:7, K:6, K:6|
|10|J|6|E:7, H:10, I:8, J:7, K:6, K:6, M:7|
|11|K|6|E:7, H:10, I:8, J:7, K:6, M:7, G2:12|
|12|M|7|E:7, G2:12, H:10, I:8, J:7, J:8, G1:10|
|13|G1|10|✓|

> G1 (cost 10) is dequeued before G2 (cost 12) and G3 (cost 4+6+5+2=17).

**Path to G1:** S→B→F→J→M→G1

**Cost:** $1+3+2+1+3 = \textbf{10}$

**a) Goal: G1, Lowest cost = 10** **b) Nodes visited: S, B, A, C, D, E, F, I, J, K, M, G1**

---

## Comparison & Best Algorithm

|Algorithm|Goal Found|Path Cost|Optimal?|Complete?|
|---|---|---|---|---|
|DFS|G1|14|✗|✗|
|BFS|G2|12|✗|✓|
|IDS|G2|12|✗|✓|
|UCS|G1|**10**|✓|✓|

### Best Algorithm: Uniform Cost Search

- **DFS** found G1 but at cost 14 — it got lucky with the goal but ignored edge weights entirely
- **BFS and IDS** both found G2 at cost 12 — they optimise for fewest hops, not lowest cost
- **UCS** is the only one that found the true cheapest path (cost 10 to G1) because it always expands the lowest cumulative cost node first
- In any graph with **varying edge costs**, UCS is the correct choice when the objective is minimising total path cost

---
## Exercice 3:

# A* and Greedy Best-First Search on Warehouse Grid

## Step 0 — Map the Grid

First, let's clearly define what's in the grid (row, col) where (1,1) is top-left:

**Obstacles (black — cannot enter):** (1,5), (2,1), (2,3), (3,4), (2,2) — wait, let me read carefully from the image.

From the figure:

- **R (start):** (1,1) — green
- **P (goal):** (6,6) — blue
- **Black obstacles:** (2,1), (2,2), (2,3), (3,4), (1,5)...

Let me re-read systematically row by row:

|Cell|Type|
|---|---|
|(1,1)|Start R|
|(1,5)|Black obstacle|
|(2,1)|Black obstacle|
|(2,2)|Black obstacle|
|(2,3)|Black obstacle|
|(3,4)|Black obstacle|
|(2,5)|Orange (cost 3)|
|(4,3)|Orange (cost 3)|
|(4,4)|Orange (cost 3)|
|(4,5)|Orange (cost 3)|
|(5,4)|Orange (cost 3)|
|(5,5)|Orange (cost 3)|
|(6,6)|Goal P|
|All others|Grey (cost 1)|

---

## Heuristic Function

$$h(n) = |6 - row| + |6 - col|$$

Pre-compute h for key nodes:

|Node|h(n)|
|---|---|
|(1,1)|5+5 = 10|
|(1,2)|5+4 = 9|
|(1,3)|5+3 = 8|
|(1,4)|5+2 = 7|
|(1,6)|5+0 = 5|
|(2,4)|4+2 = 6|
|(2,6)|4+0 = 4|
|(3,1)|3+5 = 8|
|(3,5)|3+1 = 4|
|(3,6)|3+0 = 3|
|(4,6)|2+0 = 2|
|(5,6)|1+0 = 1|
|(6,6)|0|

**Tie-breaking order: Right, Down, Up, Left**

---

## Part (a) — A* Search

**A* uses:** $f(n) = g(n) + h(n)$

where $g(n)$ = actual cost from start, $h(n)$ = Manhattan distance to goal.

### Expansion Table:

|Step|Node Expanded|g(n)|h(n)|f(n)|Neighbours Generated|
|---|---|---|---|---|---|
|1|(1,1)|0|10|10|Right→(1,2): g=1,h=9,f=10 ; Down→(2,1): BLACK skip|
|2|(1,2)|1|9|10|Right→(1,3):g=2,h=8,f=10 ; Down→(2,2): BLACK skip ; Up: wall ; Left→(1,1): visited|
|3|(1,3)|2|8|10|Right→(1,4):g=3,h=7,f=10 ; Down→(2,3): BLACK skip|
|4|(1,4)|3|7|10|Right→(1,5): BLACK skip ; Down→(2,4):g=4,h=6,f=10|
|5|(2,4)|4|6|10|Right→(2,5):g=7,h=5,f=12 ; Down→(3,4): BLACK skip ; Up→(1,4):visited ; Left→(2,3):BLACK|
|6|(1,6)|—|—|—|Need to check — can we reach (1,6)? From (1,5) blocked. Must go via (2,4)→(2,5)→...|

> Let me retrace — from (2,4): Right goes to (2,5) which is **orange cost 3**, so g=4+3=7. Down goes to (3,4) which is **black**. Up goes to (1,4) visited. Left is black.

|Step|Node Expanded|g(n)|h(n)|f(n)|Open List After|
|---|---|---|---|---|---|
|1|**(1,1)**|0|10|10|(1,2):f=10|
|2|**(1,2)**|1|9|10|(1,3):f=10|
|3|**(1,3)**|2|8|10|(1,4):f=10|
|4|**(1,4)**|3|7|10|(2,4):f=10|
|5|**(2,4)**|4|6|10|(2,5):f=12, (2,6) via? — check neighbors|

From (2,4): neighbors are:

- Right → (2,5): orange, g=4+3=7, h=4, **f=11**
- Down → (3,4): BLACK
- Up → (1,4): visited
- Left → (2,3): BLACK

|Step|Node|g|h|f|Open List|
|---|---|---|---|---|---|
|6|**(2,5)**|7|4|11|From (2,5): Right→(2,6):g=8,h=3,f=11 ; Down→(3,5):g=8,h=3,f=11 ; Up→(1,5):BLACK|
|7|**(2,6)**|8|3|11|tie with (3,5) — Right wins but (2,6) was right. Now from (2,6): Down→(3,6):g=9,h=2,f=11 ; (3,5):f=11 still open|
|8|**(3,5)**|8|3|11|From (3,5): Right→(3,6):g=9,h=2,f=11 ; Down→(4,5):orange,g=11,h=2,f=13 ; Up→(2,5):visited|
|9|**(3,6)**|9|2|11|From (3,6): Down→(4,6):g=10,h=1,f=11|
|10|**(4,6)**|10|1|11|From (4,6): Down→(5,6):g=11,h=1,f=12... wait h(5,6)=1, f=12. Also (4,5):orange already in open|
|11|**(5,6)**|11|1|12|Down→(6,6):g=12,h=0,f=12|
|12|**(6,6)**|12|0|12|**GOAL ✓**|

---

### A* Final Answer:

**Path:** (1,1)→(1,2)→(1,3)→(1,4)→(2,4)→(2,5)→(2,6)→(3,6)→(4,6)→(5,6)→(6,6)

**Node expansion order:** (1,1), (1,2), (1,3), (1,4), (2,4), (2,5), (2,6), (3,5), (3,6), (4,6), (5,6), (6,6)

**Cost breakdown:**

|Move|Cell Type|Cost|
|---|---|---|
|(1,1)→(1,2)|Grey|1|
|(1,2)→(1,3)|Grey|1|
|(1,3)→(1,4)|Grey|1|
|(1,4)→(2,4)|Grey|1|
|(2,4)→(2,5)|Orange|3|
|(2,5)→(2,6)|Grey|1|
|(2,6)→(3,6)|Grey|1|
|(3,6)→(4,6)|Grey|1|
|(4,6)→(5,6)|Grey|1|
|(5,6)→(6,6)|Grey|1|

$$\textbf{Total A* Cost} = 1+1+1+1+3+1+1+1+1+1 = \textbf{12}$$

---

## Part (b) — Greedy Best-First Search

**Greedy uses:** $f(n) = h(n)$ **only** — always expands the node that looks closest to goal, ignoring actual cost.

### Expansion Table:

|Step|Node Expanded|h(n)|Neighbours & their h|
|---|---|---|---|
|1|**(1,1)**|10|Right→(1,2):h=9 ; Down→(2,1):BLACK|
|2|**(1,2)**|9|Right→(1,3):h=8 ; Down→(2,2):BLACK|
|3|**(1,3)**|8|Right→(1,4):h=7 ; Down→(2,3):BLACK|
|4|**(1,4)**|7|Right→(1,5):BLACK ; Down→(2,4):h=6|
|5|**(2,4)**|6|Right→(2,5):h=5 ; Down→(3,4):BLACK ; Left→BLACK ; Up→visited|
|6|**(2,5)**|5|Right→(2,6):h=4 ; Down→(3,5):h=4 ; Up→(1,5):BLACK|
|7|**(2,6)**|4|tie with (3,5) — Right first → (2,6). From (2,6): Down→(3,6):h=3|
|8|**(3,6)**|3|Down→(4,6):h=2 ; Up→(2,6):visited ; Left→(3,5):h=4|
|9|**(4,6)**|2|Down→(5,6):h=1 ; Left→(4,5):h=2 — Down wins|
|10|**(5,6)**|1|Down→(6,6):h=0|
|11|**(6,6)**|0|**GOAL ✓**|

---

### Greedy Final Answer:

**Path:** (1,1)→(1,2)→(1,3)→(1,4)→(2,4)→(2,5)→(2,6)→(3,6)→(4,6)→(5,6)→(6,6)

**Node expansion order:** (1,1), (1,2), (1,3), (1,4), (2,4), (2,5), (2,6), (3,6), (4,6), (5,6), (6,6)

**Total cost** (same path, cost still calculated):

$$\textbf{Total Greedy Cost} = 1+1+1+1+3+1+1+1+1+1 = \textbf{12}$$

---

## Part (c) — Analysis & Comparison

|Feature|A*|Greedy Best-First|
|---|---|---|
|Evaluation function|f(n) = g(n) + h(n)|f(n) = h(n) only|
|Path found|(1,1)→…→(6,6)|(1,1)→…→(6,6)|
|Total cost|12|12|
|Nodes expanded|12|11|
|Optimal guarantee|✓ Yes|✗ No|

### Are the outputs the same? **Yes — same path, same cost.**

### Why?

In this particular grid, the **heuristic strongly channels both algorithms down the same corridor** due to the obstacle layout. The black cells force both algorithms through the only viable high-h-reducing path: along row 1 then column 6. Because the heuristic is never misleading in this layout, Greedy happens to find the optimal path by accident.

However, this is **not guaranteed in general:**

- **Greedy can fail** on grids where the closest-looking path leads into a dead end or expensive cells — it has no memory of actual cost $g(n)$
- **A*** would still find the optimal path in those cases because it balances $g(n)$ (what was paid) with $h(n)$ (what is estimated ahead)

> In short: they agree here **by coincidence of grid geometry**, not by design. A* is always trustworthy; Greedy got lucky.

---
## Question 5:


Here is a full, structured assignment-style solution walking through every required element — definition, cost function, neighbour generation, iterations, probability acceptance, and the flowchart.

---

# Simulated Annealing for Concert Seat Allocation

## 1. Problem Setup & Solution Representation

The venue has three zone tiers (distances from the stage):

| Zone                       | Sections             | Distance score (lower = closer) |
| -------------------------- | -------------------- | ------------------------------- |
| Floor (GA + A/B/C blocks)  | A1, A2, B1–B4, C1–C4 | 1                               |
| Lower bowl (blue sections) | 01-06, 14-26         | 2                               |
| Upper bowl (pink/purple)   | 27–32, 40-52         | 3                               |
| Nosebleeds (gray)          | 07-13, 33-39         | 4                               |

**Solution representation:** A solution _S_ is a list of seat assignments for a group of customers:

$$S = {(c_i, \text{section}_i, \text{row}_i, \text{seat}_i) \mid i = 1, 2, \ldots, n}$$

**Example scenario:** A group of 6 customers booking together. We want them close to the stage and seated together.

---

## 2. Cost Function

The cost function **C(S)** combines three penalties:

$$C(S) = w_1 \cdot D(S) + w_2 \cdot G(S) + w_3 \cdot P(S)$$

|Term|Meaning|Formula|
|---|---|---|
|D(S)|Average distance from stage|$\frac{1}{n}\sum_{i=1}^n d_i$ where $d_i \in {1,2,3,4}$|
|G(S)|Group scatter penalty|Number of distinct sections used|
|P(S)|Premium seat bonus (negative reward)|$-\sum_i \mathbf{1}[\text{seat is GA/floor}]$|

Using weights **w₁ = 2, w₂ = 3, w₃ = 1**.

**Initial solution (random assignment):**

|Customer|Section|Distance score|
|---|---|---|
|1|35 (gray)|4|
|2|B2 (floor)|1|
|3|42 (pink)|3|
|4|25 (blue)|2|
|5|30 (pink)|3|
|6|B3 (floor)|1|

$$D(S_0) = \frac{4+1+3+2+3+1}{6} = 2.33$$ $$G(S_0) = 6 \text{ distinct sections}$$ $$P(S_0) = -2 \text{ (two floor seats)}$$

$$C(S_0) = 2(2.33) + 3(6) + 1(-2) = 4.67 + 18 - 2 = \mathbf{20.67}$$

---

## 3. Neighbour Generation

A **neighbour solution S'** is produced by one of three random moves:

1. **Swap move:** Swap the seat of one customer with another random available seat
2. **Group move:** Move two adjacent customers into the same section
3. **Upgrade move:** Move one customer one tier closer to the stage

---

## 4. SA Parameters (Assumed)

|Parameter|Value|Justification|
|---|---|---|
|Initial temperature T₀|100|High enough to accept most early moves|
|Cooling rate α|0.85|Geometric cooling|
|Min temperature T_min|0.1|Stop condition|
|Iterations per T|3|Small demo|

At each step, a worse solution is accepted with probability:

$$P(\text{accept}) = e^{-\Delta C / T}$$

---

## 5. Iteration Walkthrough

### Iteration 1 (T = 100)

**Move:** Upgrade move — move Customer 1 from section 35 (gray, d=4) to section 22 (blue, d=2)

New cost calculation: $$D(S_1) = \frac{2+1+3+2+3+1}{6} = 2.00, \quad G(S_1) = 6, \quad P(S_1) = -2$$ $$C(S_1) = 2(2.00) + 3(6) + 1(-2) = 4 + 18 - 2 = \mathbf{20.00}$$

$$\Delta C = 20.00 - 20.67 = -0.67 \quad (\text{improvement})$$

**Decision: Accept** (ΔC < 0 → always accept). $S \leftarrow S_1$

---

### Iteration 2 (T = 85, after cooling: 100 × 0.85)

**Move:** Group move — move Customers 3 and 5 (currently sections 42 and 30) both to section 25 (blue, d=2)

$$D(S_2) = \frac{2+1+2+2+2+1}{6} = 1.67, \quad G(S_2) = 4, \quad P(S_2) = -2$$ $$C(S_2) = 2(1.67) + 3(4) + 1(-2) = 3.33 + 12 - 2 = \mathbf{13.33}$$

$$\Delta C = 13.33 - 20.00 = -6.67 \quad (\text{improvement})$$

**Decision: Accept** (ΔC < 0). $S \leftarrow S_2$

---

### Iteration 3 (T = 72.25, after cooling: 85 × 0.85)

**Move:** Swap move — move Customer 4 from section 25 (blue, d=2) to section 50 (pink, d=3) [a _worse_ move]

$$D(S_3) = \frac{2+1+2+3+2+1}{6} = 1.83, \quad G(S_3) = 5, \quad P(S_3) = -2$$ $$C(S_3) = 2(1.83) + 3(5) + 1(-2) = 3.67 + 15 - 2 = \mathbf{16.67}$$

$$\Delta C = 16.67 - 13.33 = +3.34 \quad (\text{worse solution})$$

$$P(\text{accept}) = e^{-3.34/72.25} = e^{-0.0462} \approx 0.955$$

**Random draw:** r = 0.72 < 0.955 → **Accept** ✓

> This demonstrates the hallmark of SA: at high temperatures, even worse solutions are accepted with high probability, allowing escape from local optima.

---

### Summary Table

|Iter|T|Move type|C(S)|ΔC|Accept?|Reason|
|---|---|---|---|---|---|---|
|0|100|— (initial)|20.67|—|—|Starting state|
|1|100|Upgrade|20.00|−0.67|✅ Yes|Improvement|
|2|85|Group|13.33|−6.67|✅ Yes|Improvement|
|3|72.25|Swap|16.67|+3.34|✅ Yes|P=0.955 > r=0.72|

---

## 6. Enhancement: Adaptive Cooling

**Enhancement proposed:** Replace fixed geometric cooling with _adaptive cooling_ — slow down the temperature drop when the acceptance rate is high (still exploring), and speed it up when acceptance rate drops (converging). This prevents premature convergence without wasting iterations in a cold state.

$$\alpha_t = \begin{cases} 0.95 & \text{if acceptance rate} > 0.5 \ 0.80 & \text{if acceptance rate} \leq 0.5 \end{cases}$$

**Justification:** Standard geometric cooling treats all phases equally. Adaptive cooling gives more exploration time early and faster convergence later, producing better final solutions for the same number of iterations (Kirkpatrick et al., 1983).

---

## 7. Flowchart---

## 8. References

- Kirkpatrick, S., Gelatt, C. D., & Vecchi, M. P. (1983). Optimization by simulated annealing. _Science_, 220(4598), 671–680.
- Aarts, E., & Korst, J. (1989). _Simulated annealing and Boltzmann machines_. Wiley.
- Russell, S., & Norvig, P. (2021). _Artificial intelligence: A modern approach_ (4th ed.). Pearson.

---

**Key takeaways for your answer:**

The three iterations demonstrate all required elements. Iterations 1 and 2 accept improving solutions unconditionally (ΔC < 0). Iteration 3 is the critical case — a _worse_ solution (ΔC = +3.34) is accepted because the acceptance probability P ≈ 0.955 exceeds the random draw r = 0.72. At high temperatures, SA acts like a random walk; as T cools, it becomes increasingly greedy. The adaptive cooling enhancement justifies why a fixed α alone may be suboptimal.

---

Here is the updated solution with 7 customers throughout.

---

# Updated Scenario: 7 Customers

## Corrected Initial Solution (S₀)

| Customer | Section              | Zone       | Distance score |
| -------- | -------------------- | ---------- | -------------- |
| 1        | 35 (gray nosebleed)  | Nosebleed  | 4              |
| 2        | B2 (floor)           | Floor      | 1              |
| 3        | 42 (pink upper bowl) | Upper bowl | 3              |
| 4        | 20 (lower bowl)      | Lower bowl | 2              |
| 5        | 30 (pink upper bowl) | Upperbowl  | 3              |
| 6        | B3 (floor)           | Floor      | 1              |
| 7        | 09 (gray nosebleed)  | Nosebleed  | 4              |

$$D(S_0) = \frac{4+1+3+2+3+1+4}{7} = \frac{18}{7} = 2.57$$ $$G(S_0) = 7 \text{ distinct sections}, \quad P(S_0) = -2$$ $$C(S_0) = 2(2.57) + 3(7) + 1(-2) = 5.14 + 21 - 2 = \mathbf{24.14}$$

---

## Iteration 1 (T = 100)

**Move:** Upgrade — move Customer 7 from section 09 (**nosebleed, d=4**) to section 22 (**lower bowl, d=2**)

| Customer | Section             | d     |
| -------- | ------------------- | ----- |
| 1        | 35 (nosebleed)      | 4     |
| 2        | B2 (floor)          | 1     |
| 3        | 42 (upper bowl)     | 3     |
| 4        | 20 (lower bowl)     | 2     |
| 5        | 30 (upper bowl)     | 3     |
| 6        | B3 (floor)          | 1     |
| 7        | **22 (lower bowl)** | **2** |

$$D(S_1) = \frac{4+1+3+2+3+1+2}{7} = \frac{16}{7} = 2.29$$ $$G(S_1) = 7, \quad P(S_1) = -2$$ $$C(S_1) = 2(2.29) + 3(7) - 2 = 4.57 + 21 - 2 = \mathbf{23.57}$$

$$\Delta C = 23.57 - 24.14 = -0.57 \quad \Rightarrow \textbf{Accept}$$

---

## Iteration 2 (T = 85)

**Move:** Group move — move Customers 1, 3 and 5 (sections 35, 42, 30 — nosebleed/upper bowl) into section 22 (**lower bowl, d=2**), consolidating with Customers 4 and 7 already nearby.

| Customer | Section             | d     |
| -------- | ------------------- | ----- |
| 1        | **22 (lower bowl)** | **2** |
| 2        | B2 (floor)          | 1     |
| 3        | **22 (lower bowl)** | **2** |
| 4        | 20 (lower bowl)     | 2     |
| 5        | **22 (lower bowl)** | **2** |
| 6        | B3 (floor)          | 1     |
| 7        | 22 (lower bowl)     | 2     |

$$D(S_2) = \frac{2+1+2+2+2+1+2}{7} = \frac{12}{7} = 1.71$$ $$G(S_2) = 3 \text{ distinct sections}, \quad P(S_2) = -2$$ $$C(S_2) = 2(1.71) + 3(3) - 2 = 3.43 + 9 - 2 = \mathbf{10.43}$$

$$\Delta C = 10.43 - 23.57 = -13.14 \quad \Rightarrow \textbf{Accept}$$

---

## Iteration 3 (T = 72.25) — Worse Solution Accepted

**Move:** Swap — move Customer 4 from section 20 (**lower bowl, d=2**) to section 36 (**gray nosebleed, d=4**). A deliberately worse move.

| Customer | Section            | d     |
| -------- | ------------------ | ----- |
| 1        | 22 (lower bowl)    | 2     |
| 2        | B2 (floor)         | 1     |
| 3        | 22 (lower bowl)    | 2     |
| 4        | **36 (nosebleed)** | **4** |
| 5        | 22 (lower bowl)    | 2     |
| 6        | B3 (floor)         | 1     |
| 7        | 22 (lower bowl)    | 2     |

$$D(S_3) = \frac{2+1+2+4+2+1+2}{7} = \frac{14}{7} = 2.00$$ $$G(S_3) = 4 \text{ distinct sections}, \quad P(S_3) = -2$$ $$C(S_3) = 2(2.00) + 3(4) - 2 = 4.00 + 12 - 2 = \mathbf{14.00}$$

$$\Delta C = 14.00 - 10.43 = +3.57 \quad (\textbf{worse solution})$$

$$P(\text{accept}) = e^{-3.57/72.25} = e^{-0.0494} \approx 0.952$$

**Random draw:** r = 0.72 < 0.952 → **Accept** ✓

---

## Updated Summary Table

|Iter|T|Move|From|To|ΔC|C(S)|Accept?|Reason|
|---|---|---|---|---|---|---|---|---|
|0|100|—|—|—|—|24.14|—|Initial state|
|1|100|Upgrade C7: 09→22|Nosebleed (d=4)|Lower bowl (d=2)|−0.57|23.57|✅|Improvement|
|2|85|Group C1,C3,C5→22|Nosebleed/Upper (d=3–4)|Lower bowl (d=2)|−13.14|10.43|✅|Improvement|
|3|72.25|Swap C4: 20→36|Lower bowl (d=2)|Nosebleed (d=4)|+3.57|14.00|✅|P=0.952 > r=0.72|