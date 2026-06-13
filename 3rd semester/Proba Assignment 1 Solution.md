
Below are the step‑by‑step solutions for all the exercises.  
I have shown the working as requested, and left probabilities as fractions unless stated otherwise.

---

## Question 1 (5 marks)

We are given:

\[
P(A \cup B) = 0.7, \quad P(A \cup B') = 0.9
\]

We know:
\[
P(A \cup B') = P(A) + P(B') - P(A \cap B')
\]
But \(P(A \cap B') = P(A) - P(A \cap B)\).

Also:
\[
P(A \cup B) = P(A) + P(B) - P(A \cap B)
\]

Add the two equations:
\[
P(A \cup B) + P(A \cup B') = [P(A)+P(B)-P(A\cap B)] + [P(A)+P(B')-P(A\cap B')]
\]
But \(P(B)+P(B')=1\) and \(P(A\cap B) + P(A\cap B') = P(A)\).

So:
\[
0.7 + 0.9 = 2P(A) + 1 - P(A)
\]
\[
1.6 = P(A) + 1
\]
\[
P(A) = 0.6
\]

**Answer:**
\[
\boxed{0.6}
\]

---

## Question 2 (5 marks)

Given:
- \(E_1\) and \(E_3\) mutually exclusive: \(P(E_1 \cap E_3)=0\)
- \(E_1\) and \(E_2\) independent
- \(P(E_1)=\frac{2}{5},\ P(E_3)=\frac{1}{3},\ P(E_1 \cup E_2)=\frac{5}{8}\)

### (a) Venn diagram – not possible to draw here, but description:
Draw three overlapping circles.  
\(E_1 \cap E_3 = \emptyset\), so no overlap between \(E_1\) and \(E_3\).  
Independence of \(E_1,E_2\) means \(P(E_1 \cap E_2) = P(E_1)P(E_2)\).

### (b) \(P(E_1 \cup E_3)\)
Since mutually exclusive:
\[
P(E_1 \cup E_3) = P(E_1) + P(E_3) = \frac{2}{5} + \frac{1}{3}
\]
Common denominator 15:
\[
\frac{6}{15} + \frac{5}{15} = \frac{11}{15}
\]
**Answer (b):**
\[
\boxed{\frac{11}{15}}
\]

### (c) \(P(E_2)\)
From independence:
\[
P(E_1 \cap E_2) = P(E_1)P(E_2) = \frac{2}{5}P(E_2)
\]
Also:
\[
P(E_1 \cup E_2) = P(E_1) + P(E_2) - P(E_1 \cap E_2)
\]
Substitute:
\[
\frac{5}{8} = \frac{2}{5} + P(E_2) - \frac{2}{5}P(E_2)
\]
\[
\frac{5}{8} - \frac{2}{5} = P(E_2)\left(1 - \frac{2}{5}\right)
\]
\[
\frac{25}{40} - \frac{16}{40} = P(E_2) \cdot \frac{3}{5}
\]
\[
\frac{9}{40} = \frac{3}{5}P(E_2)
\]
\[
P(E_2) = \frac{9}{40} \cdot \frac{5}{3} = \frac{45}{120} = \frac{3}{8}
\]
**Answer (c):**
\[
\boxed{\frac{3}{8}}
\]

---

## Question 3 (5 marks)

Total men: 937  
Died from heart disease (HD): 210  
At least one parent with HD: 312  
Of those 312, died from HD: 102

We want \(P(\text{died from HD} \mid \text{neither parent HD})\).

Let \(A\) = died from HD, \(B\) = at least one parent HD.

We have:
\[
P(A) = \frac{210}{937},\quad P(B) = \frac{312}{937},\quad P(A \cap B) = \frac{102}{937}
\]
We need \(P(A \mid B') = \frac{P(A \cap B')}{P(B')}\).

First:
\[
P(A \cap B') = P(A) - P(A \cap B) = \frac{210}{937} - \frac{102}{937} = \frac{108}{937}
\]
\[
P(B') = 1 - P(B) = 1 - \frac{312}{937} = \frac{625}{937}
\]
So:
\[
P(A \mid B') = \frac{108/937}{625/937} = \frac{108}{625}
\]

**Answer:**
\[
\boxed{\frac{108}{625}}
\]

---

## Question 4 (10 marks)

### (a) Tree diagram – described:
Game 1: S (success, prob 3/4), F (fail, prob 1/4)  
Game 2:  
- If Game 1 S: next success prob = 1/2 of previous = (1/2)*(3/4)=3/8; fail prob = 5/8  
- If Game 1 F: simple maze, success prob = 3/4, fail prob = 1/4  
Game 3:  
- If Game 2 S: next success prob = 1/2 of previous success prob  
- If Game 2 F: simple maze, success prob = 3/4

### (b) Probability exactly one success in 3 games
We need sequences with exactly one S:  
S F F, F S F, F F S

1. S F F:  
P(S1)=3/4, P(F2|S1)=5/8, P(F3|F2,S1)=?  
After F2, simple maze, P(F3|F2)=1/4  
So = (3/4)*(5/8)*(1/4) = 15/128

2. F S F:  
P(F1)=1/4, after F1 simple maze: P(S2)=3/4, after S2: harder maze, P(F3|S2)=?  
P(S2)=3/4, so P(F3|S2)=1 - (1/2 * 3/4)=1 - 3/8=5/8  
So = (1/4)*(3/4)*(5/8) = 15/128

3. F F S:  
P(F1)=1/4, after F1: simple maze P(F2|F1)=1/4, after F2: simple maze P(S3)=3/4  
So = (1/4)*(1/4)*(3/4) = 3/64 = 6/128

Sum = (15+15+6)/128 = 36/128 = 9/32 ✅

### (c) Conditional probability: two consecutive successes given exactly two successes
Exactly two successes in 3 games: sequences S S F, S F S, F S S  
Two consecutive successes: S S F and F S S (S F S has no consecutive S)

Compute probabilities:
- S S F:  
P(S1)=3/4, P(S2|S1)=3/8, after S2: harder maze P(F3|S2)=5/8  
= (3/4)*(3/8)*(5/8) = 45/256

- F S S:  
P(F1)=1/4, after F1: simple maze P(S2)=3/4, after S2: harder maze P(S3|S2)=3/8  
= (1/4)*(3/4)*(3/8) = 9/128 = 18/256

Sum consecutive = (45+18)/256 = 63/256

- S F S (not consecutive):  
P(S1)=3/4, P(F2|S1)=5/8, after F2: simple maze P(S3)=3/4  
= (3/4)*(5/8)*(3/4) = 45/128 = 90/256

Total exactly two successes = (63+90)/256 = 153/256

Conditional = (63/256) / (153/256) = 63/153 = simplify divide by 9: 7/17

**Answer (c):**
\[
\boxed{\frac{7}{17}}
\]

---

## Question 5 (5 marks)

\[
P(N=n) = \frac{1}{(n+1)(n+2)},\quad n=0,1,2,\dots
\]
We want \(P(N \ge 1 \mid N \le 4) = \frac{P(1 \le N \le 4)}{P(N \le 4)}\).

First compute \(P(N \le 4) = \sum_{n=0}^{4} \frac{1}{(n+1)(n+2)}\).

Note: \(\frac{1}{(n+1)(n+2)} = \frac{1}{n+1} - \frac{1}{n+2}\) (telescoping).

So:
\[
\sum_{n=0}^{4} \left( \frac{1}{n+1} - \frac{1}{n+2} \right) = \left(1 - \frac12\right) + \left(\frac12 - \frac13\right) + \left(\frac13 - \frac14\right) + \left(\frac14 - \frac15\right) + \left(\frac15 - \frac16\right)
\]
Everything cancels except \(1 - \frac16 = \frac56\).

So \(P(N \le 4) = \frac56\).

Now \(P(N \ge 1 \mid N \le 4) = \frac{P(N \le 4) - P(N=0)}{P(N \le 4)}\).

\(P(N=0) = \frac{1}{1 \cdot 2} = \frac12\).

So numerator = \(\frac56 - \frac12 = \frac56 - \frac36 = \frac26 = \frac13\).

Thus:
\[
P = \frac{1/3}{5/6} = \frac{1}{3} \cdot \frac{6}{5} = \frac{6}{15} = \frac{2}{5}
\]

**Answer:**
\[
\boxed{\frac{2}{5}}
\]

---

Let me know if you’d like a drawn version of the Venn diagram or tree diagram described.


