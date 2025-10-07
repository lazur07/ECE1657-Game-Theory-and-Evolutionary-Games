## Chapter 1 The Name of the Game


### 1.1 Terminology & Notation 

- **Game** $\mathcal{G}$

- **Players** $\mathcal{N}
=\{1,...,N\}$ 

- **Action sets** $\Omega_i$ for player $i$
    - finite → matrix game
    - infinite → continuous-action game
- **Strategy space**  $\displaystyle \Omega = \prod_{i\in\mathcal N}\Omega_i$
    - Pure strategy: $u_i \in \Omega_i$ (action = strategy in normal-form)
    - Mixed strategy: probability distribution $\mathbf{x}_i$ over $\Omega_i$
    - Strategy profile: $\mathbf{u} = (u_1,\ldots,u_N) \in \Omega$

- **Cost function** $J_i: \Omega \to \mathbb{R}$ depends on all players' actions: $$J_i(\mathbf{u}) = J_i(\mathbf{u}_i, \mathbf{u}_{-i})$$


### 1.2 Game Forms
The **extensive form** shows structure; the **normal form** summarizes into cost mappings.

#### 1.2.1 Extensive Form
Tree graph with nodes (game states) and edges (possible moves).

![Extensive Form](../images/extensive-form.png)

- Terminal nodes with cost function
- Non-terminal nodes partitioned by player:
    - $\mathscr{S}^0$: chance nodes (Nature)
    - $\mathscr{S}^i$: nodes where player $i \in \mathcal{N}$ moves

#### 1.2.2 Normal Form

Condensed table with strategy spaces and cost functions.

A game is $\mathcal{G}=(\mathcal{N},\Omega_i,J_i)$ where:
- $\mathcal{N}=\{1,\ldots,n\}$ is the set of players  
- $\Omega_i$ is player $i$'s **pure action set**, and $\Omega=\Omega_1\times\Omega_2$ the **action profile** space  
- $J_i:\Omega\to\mathbb{R}$ is player $i$'s **cost** 


Confused? One example is the Matching Pennies game $\mathcal{G}(\mathcal{N}, \Omega_i, J)$.

![Normal Form](../images/normal-form.png)

1. **The player set** is $\mathcal{N}=\{1,2\}$ with players $P_1, P_2$.

2. **Action sets**:
   - $P_1$: $\Omega_1=\{H,T\}$ with $u_1\in\Omega_1$ (i.e., $u_1=H$ or $u_1=T$)  
   - $P_2$: $\Omega_2=\{H,T\}$ with $u_2\in\Omega_2$ (i.e., $u_2=H$ or $u_2=T$)

   The resulting pure action pairs:
   $$\Omega=\Omega_1\times\Omega_2=\{(H,H),(H,T),(T,H),(T,T)\}$$

3. **Strategy space**:
   
   To make calculations easier, we represent each pure action as a one-hot vector.
   
   For player $i$:
   $$H \;\mapsto\; \mathbf{e}_{i1} = \begin{bmatrix}1 \\ 0\end{bmatrix}, \qquad T \;\mapsto\; \mathbf{e}_{i2} = \begin{bmatrix}0 \\ 1\end{bmatrix}$$

   and the chosen action is represented by $\mathbf{u}_i\in\{\mathbf{e}_{i1},\mathbf{e}_{i2}\}$.

   In this case, $P_1$ has $\mathbf{u}_1\in\left\{\begin{bmatrix}1 \\ 0\end{bmatrix}, \begin{bmatrix}0 \\ 1\end{bmatrix}\right\}$ and $P_2$ has $\mathbf{u}_2\in\left\{\begin{bmatrix}1 \\ 0\end{bmatrix}, \begin{bmatrix}0 \\ 1\end{bmatrix}\right\}$.
   
   A strategy profile $\mathbf{u}$ is a tuple containing each player's chosen strategy:
   
   If $P_1$ chooses $H$ and $P_2$ chooses $T$:
   $$\mathbf{u}=(\mathbf{u}_1,\mathbf{u}_2)=\left(\begin{bmatrix}1 \\ 0\end{bmatrix},\begin{bmatrix}0 \\ 1\end{bmatrix}\right)$$

4. **Costs**:

   $P_1$'s cost matrix: $A=\begin{bmatrix}-1&1\\[2pt]1&-1\end{bmatrix}$  
   $P_2$'s cost matrix: $B=-A$

   $P_i$'s cost function maps a profile to $\mathbb{R}$. In matrix form:
   $$J_1(\mathbf{u}_1,\mathbf{u}_2)=\mathbf{u}_1^{\!\top}A\,\mathbf{u}_2,\qquad J_2(\mathbf{u}_1,\mathbf{u}_2)=-J_1(\mathbf{u}_1,\mathbf{u}_2)$$
   
   For the concrete profile above ($H$ for $P_1$, $T$ for $P_2$):
   $$\begin{aligned}
   J_1(\mathbf{u}_1,\mathbf{u}_2)
   &=\mathbf{u}_1^{\!\top}A\,\mathbf{u}_2\\
   &=[1,0]\,
   \begin{bmatrix}-1&1\\[2pt]1&-1\end{bmatrix}
   \,\begin{bmatrix}0 \\ 1\end{bmatrix}\\
   &=1
   \end{aligned}$$

### 1.3 Game Features

#### 1.3.1 Competitive Nature

- **Cooperative Games**: Players cooperate with identical costs

- **Non-Cooperative Games**
    - **Coordination Games**: What benefits one benefits all (e.g., Stag Hunt)
    - **Constant-Sum Games**: Payoffs sum to fixed value (e.g., Rock-Paper-Scissors)  
    - **Conflicting Interest Games**: Opposing interests with compromise potential (e.g., Prisoner's Dilemma)

#### 1.3.2 Repetition

- **One-Shot Games**: Single round only

- **Repeated Games**: Same game, multiple rounds
    - Players adapt through learning
    - Can be **finite** (fixed number of time) or **infinite** horizon (repeated indefinitely)

- **Dynamic Games**: Different games across rounds. (e.g. Stochastic games, Markov games)

#### 1.3.3 Knowledge Information

Knowledge determines strategy space: more information enables better decisions.

| Information Type | Definition |
|-----------------|------------|
| **Complete** | All players' payoffs and strategies known |
| **Incomplete** | Payoffs/strategies partially unknown |
| **Perfect** | All past actions observable |
| **Imperfect** | Past actions partially observable |

### 1.4 Solution Concepts

#### 1.4.1 Minimax Solution

Minimize maximum expected loss: $\min_{\mathbf{u}_i} \max_{\mathbf{u}_{-i}} J_i(\mathbf{u})$

#### 1.4.2 Best Response (BR)
Choose strategy minimizing cost given opponents' strategies.

- **Limitations**:
    1. Beliefs about opponents may be incorrect
    2. Suboptimal in repeated games

- **Best Response Dynamics**: update rule where next-round strategies are best responses to current strategies.

#### 1.4.3 Nash Equilibrium

No player benefits from unilateral deviation: 
$$J_i(\mathbf{u}^*_i, \mathbf{u}^*_{-i}) \leq J_i(\mathbf{u}_i, \mathbf{u}^*_{-i}) \quad \forall i, \forall \mathbf{u}_i$$

#### 1.4.4 Pareto Optimality

No player improves without harming another.

**Pareto Dominated**:
- **Strictly**: $\mathbf{u}^*$ is strictly Pareto dominated if $\exists \mathbf{u} \in \Omega$ where $J_i(\mathbf{u}) < J_i(\mathbf{u}^*)$ for all $i$
- **Weakly**: $\mathbf{u}^*$ is weakly Pareto dominated if $\exists \mathbf{u} \in \Omega$ where $J_i(\mathbf{u}) \leq J_i(\mathbf{u}^*)$ for all $i$ (with at least one strict inequality)

**Pareto Efficient**:
- **Weakly**: Not **strictly** Pareto dominated
- **Strictly**: Not **weakly** Pareto dominated


### Reference

- Pavel, L. (2025). *Game Theory and Evolutionary Games*. Systems Control Group, Department of Electrical and Computer Engineering, University of Toronto.
