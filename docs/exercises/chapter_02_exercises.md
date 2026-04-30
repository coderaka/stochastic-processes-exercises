# 第二章 有限状态马尔可夫链 (Finite-State Markov Chains)

## 练习 (Exercises) {: .ex-counter style="counter-reset: chapter 2 question 0;" }

### 无周期是类性质 (Aperiodicity is a Class Property)
=== "中文"
    请证明，若一个有限状态且不可约的马尔可夫链中存在一个状态是无周期的，则该马尔可夫链是无周期的。

=== "English"
    Prove that if there exists an aperiodic state in a finite-state, irreducible Markov chain, then the Markov chain itself is aperiodic.

--8<-- "solutions/chapter_02/exercises/exercise_aperiodicity_is_a_class_property.md"

### 可约的陷阱 (Traps in Reducibility)
=== "中文"
    我们在正文中提到，不可约性是有限状态马尔可夫链拥有唯一平稳分布的充分条件。在这道练习题里，我们来说明这一条件并非必要条件，并来探索真正的充分必要条件是什么。
    
    1. 请构造一个可约的有限状态马尔可夫链，并且其平稳分布存在且唯一。
    2. 我们称状态子集 $C \subseteq S$ 为*吸收子集（closed set）*，若 $\forall i \in C, \sum_{j \in C} P(i,j) = 1$。若一个吸收子集的任何真子集均不是吸收子集，则称之为极小吸收子集。请证明，任何有限状态马尔可夫链的平稳分布的支撑集（即非零分量的集合）必须包含在所有极小吸收子集的并集内。
    3. 假设 $C$ 是一个极小吸收子集（不一定是唯一的）。我们可以构造一个限制在 $C$ 上的马尔可夫链转移矩阵 $P|_C$，其状态空间为 $C$，转移概率为 $P|_C(i,j) = P(i,j)$。请说明 $P|_C$ 是合法的马尔可夫链且不可约。
    4. 请根据上述结论证明，有限马尔可夫链存在唯一平稳分布的充要条件是状态空间中存在唯一的极小吸收子集。

=== "English"
    In the main text, we mentioned that irreducibility is a sufficient condition for a finite-state Markov chain to have a unique stationary distribution. In this exercise, we will show that this condition is not necessary, and explore what the true necessary and sufficient condition is.
    
    1. Construct a reducible finite-state Markov chain that has a unique stationary distribution.
    2. We call a subset of states $C \subseteq S$ a *closed set* if $\forall i \in C, \sum_{j \in C} P(i,j) = 1$. If no proper subset of a closed set is closed, it is called a minimal closed set. Prove that the support of any stationary distribution (i.e., the set of states with non-zero probabilities) of a finite-state Markov chain must be contained in the union of all minimal closed sets.
    3. Suppose $C$ is a minimal closed set (not necessarily unique). We can construct a restricted Markov chain transition matrix $P|_C$ with state space $C$ and transition probabilities $P|_C(i,j) = P(i,j)$. Show that $P|_C$ is a valid Markov chain and is irreducible.
    4. Based on the above conclusions, prove that a finite Markov chain has a unique stationary distribution if and only if there is a unique minimal closed set in its state space.

--8<-- "solutions/chapter_02/exercises/exercise_traps_in_reducibility.md"

### 非对称的平衡 (Asymmetric Balance)
=== "中文"
    在正文中，我们证明了一个分布 $\pi$ 满足细致平衡条件为 $\pi$ 是平稳分布的充分条件，在这一题里，我们将证明它不是必要条件。请构造一个有限状态马尔可夫链，同时满足：
    
    - 平稳分布存在且唯一；
    - 从任何初始分布出发均收敛到该平稳分布；
    - 不满足细致平衡条件。
    
    请给出具体构造，并证明你的构造满足全部要求。

=== "English"
    In the main text, we proved that satisfying the detailed balance condition is a sufficient condition for a distribution $\pi$ to be stationary. In this problem, we will demonstrate that it is not a necessary condition. Construct a finite-state Markov chain that simultaneously satisfies the following:
    
    - A unique stationary distribution exists.
    - The chain converges to this stationary distribution from any initial distribution.
    - It does not satisfy the detailed balance condition.
    
    Provide the specific construction and prove that your construction meets all the requirements.

--8<-- "solutions/chapter_02/exercises/exercise_asymmetric_balance.md"

### 群上的随机游走 (Random Walk on Groups)
=== "中文"
    许多常见的马尔可夫链都具有某种对称性，利用*群（group）*的语言可以很好地刻画这类结构。回顾群的定义，一个群 $(G, \oplus)$ 包含一个集合 $G$ 和一个满足结合律的二元运算 $\oplus$，存在单位元 $e\in G$ 使得对于任意的 $g\in G$，有 $e \oplus g = g \oplus e = g$，且每个元素 $g$ 都有逆元 $g^{-1}\in G$ 使得 $g \oplus g^{-1} = g^{-1} \oplus g = e$。
    
    给定群 $G$ 上的一个概率分布 $\mu$（称为增量分布），我们定义群 $G$ 上的随机游走如下：这是一个状态空间为 $G$ 的马尔可夫链，其单步转移通过在当前状态的左侧乘以一个从 $\mu$ 中采样得到的随机元素来实现。即转移概率满足：
    
    $$ P(g, h \oplus g) = \mu(h), \quad \forall g, h \in G. $$
    
    1. 假设 $G$ 是有限的，请证明：无论增量分布 $\mu$ 如何选取，该随机游走的平稳分布都是均匀分布。
   
        ??? hint "提示"
            可能要用到的群的性质：对于任意的 $g\in G$，有 $\{g\oplus h: h\in G\}$ 等价于 $G$
    2. 考虑正文中讲过的图上的随机游走，假设该图是一个有 $n$ 个顶点的环，请说明它对应于集合 $\{0, 1, \dots, n-1\}$ 上的模 $n$ 加法群（即相应的二元运算是加法，其相加结果要取对 $n$ 的余数）上的随机游走，写出其增量分布 $\mu$，并利用第 1 问的结论直接给出其平稳分布。
    3. 考虑正文中讲的超立方体上的随机游走，请说明它对应于集合 $\{0, 1\}^d$ 上的按位模 $2$ 加法群（即相应的二元运算是把两个向量按位相加，然后模 $2$），写出其增量分布 $\mu$，并利用第 1 问的结论直接给出其平稳分布。

=== "English"
    Many common Markov chains exhibit a certain symmetry, which can be well characterized using the language of *groups*. Recall the definition of a group: a group $(G, \oplus)$ consists of a set $G$ and an associative binary operation $\oplus$. There exists an identity element $e\in G$ such that $e \oplus g = g \oplus e = g$ for any $g\in G$, and every element $g$ has an inverse $g^{-1}\in G$ such that $g \oplus g^{-1} = g^{-1} \oplus g = e$.
    
    Given a probability distribution $\mu$ (called the increment distribution) on a group $G$, we define a random walk on $G$ as follows: it is a Markov chain with state space $G$, where a single-step transition is performed by multiplying the current state on the left by a random element sampled from $\mu$. Thus, the transition probabilities satisfy:
    
    $$ P(g, h \oplus g) = \mu(h), \quad \forall g, h \in G. $$
    
    1. Assuming $G$ is finite, prove that regardless of the choice of increment distribution $\mu$, the stationary distribution of this random walk is the uniform distribution. 
   
        ??? hint "Hint"
            A property of groups that might be useful: for any $g\in G$, $\{g\oplus h: h\in G\}$ is equivalent to $G$.
    2. Consider the random walk on a graph mentioned in the main text, assuming the graph is a cycle with $n$ vertices. Show that it corresponds to a random walk on the modulo-$n$ addition group over the set $\{0, 1, \dots, n-1\}$ (i.e., the binary operation is addition modulo $n$). Write down its increment distribution $\mu$, and directly give its stationary distribution using the result from part 1.
    3. Consider the random walk on a hypercube discussed in the main text. Show that it corresponds to a random walk on the bitwise modulo-$2$ addition group over the set $\{0, 1\}^d$ (i.e., the binary operation is bitwise addition modulo $2$). Write down its increment distribution $\mu$, and directly give its stationary distribution using the result from part 1.

--8<-- "solutions/chapter_02/exercises/exercise_random_walk_on_groups.md"

### 以局部见全局 (Global from Local)
=== "中文"
    在正文中，我们给出了针对给定目标分布 $\pi$ 采样的Metropolis-Hastings算法，在本题中，我们给出另一个可以达到同样目的的算法。
    
    !!! theorem "算法 MH-Alt"
        **输入:** 当前状态 $i$，目标分布 $\pi$，转移图 $(V,E)$
        
        1 &nbsp;&nbsp;抛一枚均匀硬币  
        2 &nbsp;&nbsp;如果结果为反面：  
        3 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;返回 $i$ （原地踏步）  
        4 &nbsp;&nbsp;均匀随机选取 $i$ 的一个邻居 $j$  
        5 &nbsp;&nbsp;$d(i) \gets$ 节点 $i$ 的度数，$d(j) \gets$ 节点 $j$ 的度数  
        6 &nbsp;&nbsp;以概率 $\min\left\lbrace\frac{\pi(j)d(i)}{\pi(i)d(j)},\; 1\right\rbrace$ 令 $i \gets j$ （接受提议）  
        7 &nbsp;&nbsp;返回 $i$  
    
    注意到，该算法保留了Metropolis-Hastings算法的优点，即我们不需要知道 $\pi(i)$ 的准确值，只要知道 $\frac{\pi(i)}{\pi(j)}$ 的比值即可。此外，该算法是一个纯局部的算法，我们甚至不需要知道图的最大度数 $\Delta$，只需要知道当前点和邻居的度数。
    
    假设图 $G$ 是连通且无环的无向图，请证明该马尔可夫链不可约且无周期，且平稳分布为 $\pi$。并写出该马尔可夫链的转移矩阵。

=== "English"
    In the main text, we introduced the Metropolis-Hastings algorithm for sampling from a given target distribution $\pi$. In this problem, we present another algorithm that achieves the same goal.
    
    !!! theorem "Algorithm MH-Alt"
        **Input:** Current state $i$, target distribution $\pi$, transition graph $(V,E)$
        
        1 &nbsp;&nbsp;Toss a fair coin.  
        2 &nbsp;&nbsp;If the result is tails:  
        3 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Return $i$ (stay in place).  
        4 &nbsp;&nbsp;Uniformly at random choose a neighbor $j$ of $i$.  
        5 &nbsp;&nbsp;Let $d(i)$ be the degree of node $i$, and $d(j)$ be the degree of node $j$.  
        6 &nbsp;&nbsp;With probability $\min\left\lbrace\frac{\pi(j)d(i)}{\pi(i)d(j)},\; 1\right\rbrace$, set $i \gets j$ (accept the proposal).  
        7 &nbsp;&nbsp;Return $i$.  
    
    Note that this algorithm retains the advantage of the Metropolis-Hastings algorithm: we do not need to know the exact value of $\pi(i)$, only the ratio $\frac{\pi(i)}{\pi(j)}$. Furthermore, it is a purely local algorithm; we do not even need to know the maximum degree $\Delta$ of the graph, only the degrees of the current node and its neighbors.
    
    Assuming the graph $G$ is a connected and loopless undirected graph, prove that this Markov chain is irreducible and aperiodic, and its stationary distribution is $\pi$. Also, write down the transition matrix of this Markov chain.

--8<-- "solutions/chapter_02/exercises/exercise_global_from_local.md"

### 总变差距离界限 (Total Variation Distance Bounds)
=== "中文"
    设 $P$ 为一个有限状态空间上不可约、非周期的马尔可夫链的转移矩阵，$\pi$ 为其平稳分布。考虑该空间上两个分布 $\mu_0$ 和 $\nu_0 $ 以及从这两个分布出发的马尔可夫链，定义 $ \mu_t $ 和 $ \nu_t $ 为满足 $ \mu_t^{\top}=\mu_0^{\top}P^t $ 以及 $ \nu_t^{\top}=\nu_0^{\top}P^t $ 的分布。对于 $ t \ge 0$，定义
    
    $$
    d(t) \defeq \sup_{\mu_0} \dTV(\mu_t,\pi) \quad \text{和} \quad \tilde{d}(t) \defeq \sup_{\mu_0, \nu_0} \dTV(\mu_t, \nu_t).
    $$
    
    请证明：$d(t) \le \tilde{d}(t) \le 2d(t)$。

=== "English"
    Let $P$ be the transition matrix of an irreducible, aperiodic Markov chain on a finite state space, and let $\pi$ be its stationary distribution. Consider two distributions $\mu_0$ and $\nu_0$ on this space, and the Markov chains starting from these distributions. Define $\mu_t$ and $\nu_t$ as distributions satisfying $\mu_t^{\top}=\mu_0^{\top}P^t$ and $\nu_t^{\top}=\nu_0^{\top}P^t$. For $t \ge 0$, define
    
    $$
    d(t) \defeq \sup_{\mu_0} \dTV(\mu_t,\pi) \quad \text{and} \quad \tilde{d}(t) \defeq \sup_{\mu_0, \nu_0} \dTV(\mu_t, \nu_t).
    $$
    
    Prove that: $d(t) \le \tilde{d}(t) \le 2d(t)$.

--8<-- "solutions/chapter_02/exercises/exercise_total_variation_distance_bounds.md"

### 求同存异 (Coupling Lemma)
=== "中文"
    设 $\mu$ 和 $\nu$ 是定义在有限状态空间 $\Omega$ 上的两个概率分布。为了证明正文给出的耦合引理，我们需要构造一个联合分布 $\omega^*$，使得 $\Pr[(X,Y)\sim \omega^*]{X\neq Y} = \dTV(\mu, \nu)$。请给出 $\omega^*(x, y)$ 的精确表达式，并证明它是一个满足要求的耦合。

=== "English"
    Let $\mu$ and $\nu$ be two probability distributions defined on a finite state space $\Omega$. To prove the coupling lemma given in the main text, we need to construct a joint distribution $\omega^*$ such that $\Pr[(X,Y)\sim \omega^*]{X\neq Y} = \dTV(\mu, \nu)$. Provide the exact expression for $\omega^*(x, y)$ and prove that it is a valid coupling that satisfies the requirement.

--8<-- "solutions/chapter_02/exercises/exercise_coupling_lemma.md"

### 硬币的记忆 (Memory of Coins)
=== "中文"
    重复扔一枚均匀硬币，每次出现正面 $H$ 和反面 $T$ 的概率均为 $1/2$。我们来考察不同的正反面序列在整个扔硬币结果序列中首次出现的时间，令 $T_1$ 表示序列 $HH$ 第一次出现的时间，$T_2$ 表示序列 $HT$ 第一次出现的时间。 
    
    1. 分别求出期望时间 $\E{T_1}$ 和 $\E{T_2}$，平均来说，$ HH $ 和 $ HT$ 哪一个序列更先出现？

        ??? hint "提示"
            可以考虑状态空间 $S = \{\emptyset, HH, HT, TT, TH\}$ 上的随机游走，其中 $\emptyset$ 代表初始状态。
    2. 解释出现上述情况的直观原因。

=== "English"
    Repeatedly toss a fair coin, where the probability of a heads $H$ and tails $T$ appearing is $1/2$ each time. We examine the first time different sequences of heads and tails appear in the entire sequence of coin tosses. Let $T_1$ denote the first time the sequence $HH$ appears, and $T_2$ denote the first time the sequence $HT$ appears.
    
    1. Calculate the expected times $\E{T_1}$ and $\E{T_2}$. On average, which sequence appears first, $HH$ or $HT$?

        ??? hint "Hint"
            Consider a random walk on the state space $S = \{\emptyset, HH, HT, TT, TH\}$, where $\emptyset$ represents the initial state.
    2. Explain the intuitive reason for this phenomenon.

--8<-- "solutions/chapter_02/exercises/exercise_memory_of_coins.md"

### 环上的随机游走 (Random Walk on a Cycle)
=== "中文"
    考虑一个由 $n$ 个点构成的环上的随机游走，每一步以 $1/2$ 的概率原地不动，以 $1/2$ 的概率从当前点的邻居中均匀随机选择一个移过去。为计算方便，假设 $n$ 可被 4 整除。本题里我们来分析该随机游走的混合时间上下界。
    
    1. 证明该马尔可夫链 $\tau_{\text{mix}}=O(n^2)$。
    2. 不妨设该环上顶点集合为 $\{0,1,\dots,n-1\}$，令 $A = \{n/2, \dots, n-1\}$，证明对于某个 $\alpha_0 > 0$，当 $\alpha \le \alpha_0$ 时，令 $t = \alpha n^2$，有
       $$ P^t(n/4, A) < \frac{1}{4}. $$ 
    3. 由上一问结论，证明
       
       $$ \tau_{\text{mix}} =\Omega(n^2). $$

   
    <p class="note-inline">注：在后面学到鞅的时候，我们可以用一种更巧妙的方法来证明该随机游走混合时间的上界。</p>

=== "English"
    Consider a random walk on a cycle with $n$ vertices. At each step, the walk stays in place with probability $1/2$ and moves to a uniformly chosen neighbor of the current vertex with probability $1/2$. For convenience, assume $n$ is divisible by 4. In this problem, we will analyze the upper and lower bounds of the mixing time for this random walk.
    
    1. Prove that for this Markov chain, $\tau_{\text{mix}}=O(n^2)$.
    2. Let the set of vertices on this cycle be $\{0,1,\dots,n-1\}$, and let $A = \{n/2, \dots, n-1\}$. Prove that for some $\alpha_0 > 0$, when $\alpha \le \alpha_0$, letting $t = \alpha n^2$, we have
       $$ P^t(n/4, A) < \frac{1}{4}. $$
    3. From the conclusion of the previous part, prove that
       
       $$ \tau_{\text{mix}} =\Omega(n^2). $$
       
    <p class="note-inline">Note: When we study martingales in later chapters, we can use a more elegant method to prove the upper bound on the mixing time for this random walk.</p>

--8<-- "solutions/chapter_02/exercises/exercise_random_walk_on_a_cycle.md"
