## Chapter 2 Matrix Games: 2-player Zero-Sum

## 2 player Zero-Sum Finite/Matrix Games 

### Ch 2.1:

#### definition, security strategies, minmax solution

◦ examples

#### no regret concept and saddle-point equilibrium

### Ch 2.2

#### mixed-strategy extension

#### mixed-strategy security strategies

#### mixed-strategy saddle-point equilibrium

### Ch 2.3

◦ Minmax Theorem 
 You Read Th 2.10, Cor. 2.11

### Ch 2.4
Computing mixed saddle-point eq. solution 

#### Dominated strategies (You Read Sec 2.4.1)

#### Graphical method in 2x2 games

Example: Matching Pennies game




### Pure Strategy

$$
\mathcal{G}(\mathcal{N}, \Omega_i, J_i)
$$

- $\mathcal{N} = \{1,2\}$: 2 players
- $\Omega_i$: action set for player $i \in \mathcal{N}$
  - action of player 1: $\vec{u}_1 \in \Omega_1$
  - action of player 2: $\vec{u}_2 \in \Omega_2$
- $J_i$: cost function for player $i \in \mathcal{N}$


  - cost of player 1: $J_1(\vec{u}_1, \vec{u}_2)$
  - cost of player 2: $J_2(\vec{u}_1, \vec{u}_2)$


### Two-Player Zero-Sum Game

$$
J_1(\vec{u}_1, \vec{u}_2) + J_2(\vec{u}_1, \vec{u}_2) = 0, 
\quad \forall$$

the set of joint actions 
$$(\vec{u}_1,\vec{u}_2) \in \Omega_1 \times \Omega_2
$$

- P1: $\min J_1, \max J_2$
- P2: $\min J_2, \max J_1$
- $J_1 = -J_2 = J$
  → we can simplify game as $\mathcal{G}(\mathcal{N}, \Omega_i, J)$


### Assume $m$ rounds finite actions (pure strategies to choose from)

- P1: $m_1 = m \Rightarrow \Omega_1 = A_1, (\vec{u}_1 = e_{1j}), j \in M_1 := \{1,\dots,m\}$
- P2: $m_2 = n \Rightarrow \Omega_2 = A_2, (\vec{u}_2 = e_{2k}), k \in M_2 := \{1,\dots,n\}$

$$
e_{1j} \in \mathbb{R}^m \quad \text{is the \(j\)-th unit vector}, \quad
e_{2k} \in \mathbb{R}^n \quad \text{is the \(k\)-th unit vector}.
$$

- $a_{jk}$ denotes the outcome if P1 chooses $j$-th action and P2 chooses $k$-th action:

  $$
  J(\vec{u}_1, \vec{u}_2) = J(e_{1j}, e_{2k}) = a_{jk}
  $$

Thus → $(m \times n)$ matrix:

$$
A_{m \times n} = [a_{jk}]_{m \times n}
$$


### Benefit of this definition

For P1, we can write its cost:

$$
J_1(\vec{u}_1, \vec{u}_2) = J_1(e_{1j}, e_{2k}) = a_{jk} = e_{1j}^T A_{m \times n} e_{2k}
$$

Thus

$$
J_1(\vec{u}_1, \vec{u}_2) = \vec{u}_1^T A \vec{u}_2, 
\quad
J_2(\vec{u}_1, \vec{u}_2) = \vec{u}_1^T B \vec{u}_2,
\quad A = -B
$$

⭐ Hence we can --identify $\mathcal{G}$ using a single cost matrix $A$:--

$$
\mathcal{G}(\mathcal{N}, \Omega_i, J) \;\Rightarrow\; \mathcal{G}(\mathcal{N}, \Omega_i, A).
$$





### Example: Matching Pennies

* If P1 chooses $H$ ($\vec{e}_{11}$)
  and P2 chooses $H$ ($\vec{e}_{21}$)

* Notation: $\vec{e}_{ij}$ = action $j$ of player $i$.


Payoff matrices:

$$
A = \begin{bmatrix}
-1 & 1 \\
1 & -1
\end{bmatrix}, 
\qquad 
B = \begin{bmatrix}
1 & -1 \\
-1 & 1
\end{bmatrix}
$$


P1’s cost function:

$$
J_1(\vec{e}_{11}, \vec{e}_{21}) 
= \vec{e}_{11}^T A \vec{e}_{21}
= [1 \; 0]
\begin{bmatrix}
-1 & 1 \\
1 & -1
\end{bmatrix}
\begin{bmatrix}
1 \\ 0
\end{bmatrix}
= [-1 \; 1]
\begin{bmatrix}
1 \\ 0
\end{bmatrix}
= -1
$$


*What a coincidence:*

$$
J(\vec{e}_{1j}, \vec{e}_{2k}) = a_{jk}
$$




### Definition 2.1 — Security Strategy

* **P1 chooses row–min**
* **P2 chooses col–max**


#### Player 1 (minimizer)

* Given cost matrix $A = [a_{jk}] \in \mathbb{R}^{m \times n}$
* P1’s security strategy (worst case): chooses row $j^*$ minimizing row–max cost

$$
\max_k a_{jk} = \max_{k} a_{jk}, \quad j=1,\dots,m
$$

$$
J_U := \min_{j \in M_1} \max_{k \in M_2} a_{jk}, \quad 
j^* \in \arg\min_{j \in M_1} \max_{k \in M_2} a_{jk}
$$


#### Player 2 (maximizer)

* Given P1’s cost matrix $A = [a_{jk}] \in \mathbb{R}^{m \times n}$
* P2’s security strategy (worst case): chooses column $k^*$ maximizing col–min gain

$$
\min_j a_{jk} = \min_{j} a_{jk}, \quad k=1,\dots,n
$$

$$
J_L := \max_{k \in M_2} \min_{j \in M_1} a_{jk}, \quad 
k^* \in \arg\max_{k \in M_2} \min_{j \in M_1} a_{jk}
$$


### Consequence

* $J_U, J_L$ will be a scalar on the matrix $A$.
* If the pair $(j^*, k^*) \in M_1 \times M_2$, then it is a **saddle-point equilibrium**.
* The value of the game is $J = J_U = J_L$.


### Properties

* Security strategies are **conservative** → do not guarantee equilibrium.
* Equilibrium requires **no regret**.
* In any matrix game, there always exists at least a security strategy for each player $i \in \mathcal{N}$.
* In pure strategy:

  $$
  (\text{pure}) \;\; \max\min \;\; \le \;\; (\text{pure}) \;\; \min\max
  $$

  i.e.

  $$
  J_L \le a_{j^* k^*} \le J_U
  $$



### Definition 2.2

Given $A_{m \times n} = [a_{jk}]$:

If

$$
a_{j^* k} \;\le\; a_{j^* k^*} \;\le\; a_{j k^*}, 
\quad \forall j \in M_1, \; \forall k \in M_2
$$

then $(j^*, k^*)$ is a **saddle-point equilibrium**.

### Course Note

* Last time
* Today
* Recap:

* For player 1: $|\Omega_1| = m_1, \; M_1 = \{1, \dots, m\}$

  $$
  e_{1j} =
  \begin{bmatrix}
  0 \\ \vdots \\ 1 \\ \vdots \\ 0
  \end{bmatrix}
  \quad \text{(j-th unit vector)}
  $$

  Action: $\vec{u}_1 = e_{1j}$.

  $$
  \min_{\vec{u}_1} J_1(\vec{u}_1, \vec{u}_2), \quad \vec{u}_1 = e_{1j}
  $$

* For player 2: $|\Omega_2| = m_2, \; M_2 = \{1, \dots, n\}$

  $$
  e_{2k} =
  \begin{bmatrix}
  0 \\ \vdots \\ 1 \\ \vdots \\ 0
  \end{bmatrix}
  \quad \text{(k-th unit vector)}
  $$

  Action: $\vec{u}_2 = e_{2k}$.

  $$
  \min_{\vec{u}_2} J_2(\vec{u}_1, \vec{u}_2), \quad \vec{u}_2 = e_{2k}
  $$

### Two-Player Zero-Sum (2PZS)

$$
J_1 + J_2 = 0 
\quad \Leftrightarrow \quad \text{use single cost function } J
$$

* P1: $\min \max J$
* P2: $\max \min J$




### Finite Action

$$
(j,k) \;\;\Rightarrow\;\; J(e_{1j}, e_{2k}) = a_{jk} = e_{1j}^T A e_{2k}, 
\quad a_{jk} \in \mathbb{R}.
$$


### Definitions

* **P1 security strategy**

  $$
  j^* = \arg\min_j \max_k a_{jk} 
  \quad \Rightarrow \quad J_U \ne J_L \;\; \text{in general.}
  $$

* **Minimax solution**
  Both players use security strategies → $(j^*, k^*) \mapsto J_\phi$.


### Note

$*$ No regret property may **not hold** → see Example 1 & Example 2.


### Definition — Saddle Point

If

$$
a_{j^* k} \;\le\; a_{j^* k^*} \;\le\; a_{j k^*}, 
\quad \forall k \in M_2, \;\forall j \in M_1,
$$

then:

* no regret for P2 (blue)
* no regret for P1 (green)


### Additional Note

A **minimax solution** is a saddle point **when**

$$
J_U = J_L = \bar{J}.
$$




### Example 3: Matching Pennies (MP) game

$$
A = 
\begin{bmatrix}
-1 & 1 \\
1 & -1
\end{bmatrix}
$$


1. **Find security strategy** — *the problem*:

$$
j^* = \arg\min_j \max\{1,1\} \;\;\Rightarrow\;\; j^* = 1 \;\;\downarrow
$$

$$
k^* = \arg\max_k \min\{-1,-1\} \;\;\Rightarrow\;\; k^* = 1 \;\;\downarrow
$$

So there are 4 “security strategy solutions” (minimax solutions):

$$
(1,1),\; (1,2),\; (2,1),\; (2,2)
$$


### Question:

Which one has **no regret** (saddle point)?

* Pick $(j^*,k^*)=(1,2)$:
  → P1 regrets, P2 regrets → ✗ not saddle pt. sol.

* Pick $(j^*,k^*)=(1,2)$:
  → P1 regrets, P2 regrets → ✗ not saddle pt. sol.

(*all regret → no pure saddle point here*)


### Question:

What to do in such cases?

👉 Introduce **randomization** in selection of actions.

* This defines the **mixed strategy** of P1 and P2.


* Denote:

  $$
  x_j = \Pr(\text{P1 selects j-th action}), 
  \quad x = [x_1, \dots, x_j, \dots, x_{m_1}]^T \in \mathbb{R}^{m_1}
  $$

  $$
  y_k = \Pr(\text{P2 selects k-th action}), 
  \quad y = [y_1, \dots, y_k, \dots, y_{m_2}]^T \in \mathbb{R}^{m_2}
  $$

* Require:

  $$
  0 \le x_j \le 1, \quad \sum_j x_j = 1
  $$

  $$
  0 \le y_k \le 1, \quad \sum_k y_k = 1
  $$

  so that $x,y$ are valid probability vectors.


### Note

* If P1 selects $j$-th action with 100% probability:

  $$
  x = e_{1j} = [0, \dots, 1, \dots, 0]^T
  $$

  → P1’s **pure strategy**.





### Q: Where do $x$ and $y$ live?

**(2D Example):** P1 has **2 actions** to choose from

$$
\Delta_1 := \left\{ x = 
\begin{bmatrix} x_1 \\ x_2 \end{bmatrix} \in \mathbb{R}^2 \;\middle|\; 0 \le x_j \le 1,\; \sum_j x_j = 1 \right\}
$$

→ the **simplex** in $\mathbb{R}^2$ (a line segment).


**(3D Example):** P1 has **3 actions** to choose from

$$
\Delta_1 := \left\{ x = 
\begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} \in \mathbb{R}^3 \;\middle|\; 0 \le x_j \le 1,\; \sum_{j=1}^3 x_j = 1 \right\}
$$

→ the **simplex** in $\mathbb{R}^3$ (a triangle).

(Diagrams show the line segment for 2 actions and triangle for 3 actions.)


### Expected outcome (value of the cost)

When P1 selects $j$: probability $x_j$
When P2 selects $k$: probability $y_k$

Outcome:

$$
a_{jk} x_j y_k
$$

Expected cost:

$$
\mathbb{E}[J] = \sum_{j=1}^{m_1} \sum_{k=1}^{m_2} a_{jk} x_j y_k
$$

In compact form:

$$
\mathbb{E}[J] = x^T A y
$$

(This encompasses the pure strategy case.)


### Mixed Strategy Problem Formulation

* Player 1 (minimizer):

  $$
  \min_{x \in \Delta_1} x^T A y
  $$

* Player 2 (maximizer):

  $$
  \max_{y \in \Delta_2} x^T A y
  $$


### Definition — Mixed Strategy Security

* P1 has a mixed strategy $x^*$:

  $$
  x^* = \arg\min_{x \in \Delta_1} \max_{y \in \Delta_2} x^T A y, 
  \quad \text{expected cost } \bar{J}_U
  $$

* P2 has a mixed strategy $y^*$:

  $$
  y^* = \arg\max_{y \in \Delta_2} \min_{x \in \Delta_1} x^T A y, 
  \quad \text{expected cost } \bar{J}_L
  $$

Here’s the cleaned-up extraction of your manuscript across these two overlapping pages:


### Definition — Mixed Strategy Saddle-Point Equilibrium

A pair $(x^*, y^*) \in \Delta_1 \times \Delta_2$ is a **mixed strategy saddle-point equilibrium** if

$$
x^T A y^* \;\le\; x^{*T} A y^* \;\le\; x^{*T} A y, 
\quad \forall x \in \Delta_1, \; \forall y \in \Delta_2.
$$

* Note: $\bar{J}_U = \bar{J}_L = x^{*T} A y^*$.
* Equivalently: $(x^*, y^*)$ is a **mixed strategy security solution** and a **saddle point** in any 2-player zero-sum finite game.
* → This is the **Minimax Theorem**.


### Computation of Mixed Strategy Saddle-Point Equilibrium

* Graphically for $m = 2, n = 2$ games (2×2).
* Note: extendable to $m \times n$ games.

Take matrix:

$$
A = \begin{bmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{bmatrix}.
$$


#### Simplex definitions

* For P1:

$$
\Delta_1 = \left\{ x = \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} \in \mathbb{R}^2 \;\middle|\; 0 \le x_j \le 1, \; x_1+x_2=1 \right\}
$$

* For P2:

$$
\Delta_2 = \left\{ y = \begin{bmatrix} y_1 \\ y_2 \end{bmatrix} \in \mathbb{R}^2 \;\middle|\; 0 \le y_k \le 1, \; y_1+y_2=1 \right\}
$$


#### Player 1’s computation

P1 looks at:

$$
\min_{x \in \Delta_1} \max_{k \in \{1,2\}} x^T A e_{2k}.
$$

That is:

$$
\min_{x_1 \in [0,1]} \max \Big\{ x_1 a_{11} + (1-x_1)a_{21}, \;\; x_1 a_{12} + (1-x_1)a_{22} \Big\}.
$$

Define:

* $R_1(x_1) = x_1 a_{11} + (1-x_1)a_{21}$
* $R_2(x_1) = x_1 a_{12} + (1-x_1)a_{22}$

Both are linear functions of $x_1$.
Let:

$$
Q(x_1) = \max\{R_1(x_1), R_2(x_1)\}.
$$

Then:

$$
x_1^* = \arg\min_{x_1 \in [0,1]} Q(x_1).
$$


### Example: Matching Pennies

$$
A = \begin{bmatrix} -1 & 1 \\ 1 & -1 \end{bmatrix}.
$$

Compute:

$$
R_1(x_1) = -2x_1 + 1, 
\quad R_2(x_1) = 2x_1 - 1.
$$

At equilibrium:

$$
x_1^* = \tfrac{1}{2}, \quad x_2^* = 1-x_1^* = \tfrac{1}{2}.
$$

So:

$$
x^* = \begin{bmatrix} \tfrac{1}{2} \\ \tfrac{1}{2} \end{bmatrix}, 
\quad \bar{J} = 0.
$$

Similarly for P2:

$$
y^* = \begin{bmatrix} \tfrac{1}{2} \\ \tfrac{1}{2} \end{bmatrix}.
$$
