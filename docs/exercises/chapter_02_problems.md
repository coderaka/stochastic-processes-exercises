# 第二章 有限状态马尔可夫链 (Finite-State Markov Chains)


## 问题 (Problems) {: .prob-counter style="counter-reset: chapter 2 question 0;" }

### 再探马尔可夫链基本定理 (Revisiting the Fundamental Theorem of Markov Chains)
=== "中文"
    在正文的马尔可夫链基本定理的证明中，我们考虑了两个以 $Q\defeq P^{t^*}$ 为转移概率矩阵的马尔可夫链的耦合。在本题，我们将使用另一种“耦合的耦合”的方法来证明这个定理。
    
    已知状态空间 $\Omega=[n]$，$P$ 是一个不可约且非周期的马尔可夫链转移矩阵，给定任意初始状态$ X_0 = x$ 且 $Y_0 = y$。我们在同一概率空间中定义两组过程：
    
    - **耦合过程 $(X_t, Y_t)$**：从 $(X_0,Y_0)$ 出发，在 $X_t \neq Y_t$ 时各自独立按 $P$ 转移；一旦存在某时刻 $X_t = Y_t$，此后将永远保持一致，一起按 $P$ 转移。
    - **独立的影子过程 $(X'_t, Y'_t)$**：从相同的初始状态 $X'_0 = x, Y'_0 = y$ 出发，无论是否相遇，全程各自独立按 $P$ 转移。
    
    分别定义它们的首次相遇时间为 $\tau = \min\{t \ge 0 | X_t = Y_t\}$ 和 $\tau' = \min\{t \ge 0 | X'_t = Y'_t\}$。
    
    1. 请证明，对于任意时刻 $t$，$\Pr{X_{t} \neq Y_{t}} = \Pr{\tau' > t}$。
    2. 请利用上一问结论证明马尔可夫链基本定理。

=== "English"
    In the proof of the Fundamental Theorem of Markov Chains in the main text, we considered a coupling of two Markov chains with transition probability matrix $Q\defeq P^{t^*}$. In this problem, we will prove this theorem using an alternative "coupling of couplings" approach.
    
    Consider a state space $\Omega=[n]$ and an irreducible, aperiodic transition matrix $P$. Given any initial states $X_0 = x$ and $Y_0 = y$, we define two sets of processes on the same probability space:
    
    - **Coupled process $(X_t, Y_t)$**: Starts from $(X_0,Y_0)$. When $X_t \neq Y_t$, they evolve independently according to $P$. Once they meet (i.e., $X_t = Y_t$ for some $t$), they stay together forever, taking identical transitions according to $P$.
    - **Independent shadow process $(X'_t, Y'_t)$**: Starts from the same initial states $X'_0 = x, Y'_0 = y$. They evolve independently according to $P$ for all time, regardless of whether they meet.
    
    Define their respective first meeting times as $\tau = \min\{t \ge 0 | X_t = Y_t\}$ and $\tau' = \min\{t \ge 0 | X'_t = Y'_t\}$.
    
    1. Prove that for any time $t$, $\Pr{X_{t} \neq Y_{t}} = \Pr{\tau' > t}$.
    2. Use the result from the previous part to prove the Fundamental Theorem of Markov Chains.

--8<-- "solutions/chapter_02/problems/problem_revisiting_the_fundamental_theorem_of_markov_chains.md"

### 可逆链的谱分解 (Spectral Decomposition of Reversible Chains)
=== "中文"
    在正文以及上一题中，我们介绍了如何用耦合的方法证明马尔可夫链基本定理，在本题中，我们将用谱分解的方法来证明可逆马尔可夫链上的该定理。设 $P$ 是一个状态空间为 $\Omega=[n]$ 的可逆马尔可夫链的转移矩阵，$\pi$ 是其平稳分布。
    
    1. 定义对角矩阵 $\Pi = \text{diag}(\pi)$，定义矩阵 $Q = \Pi^{1/2} P \Pi^{-1/2}$。我们可以用以下谱分解定理给出 $Q$ 的谱分解 $Q= U \Lambda U^T$，定义列向量 $v_i = \Pi^{-1/2} u_i$，请证明：$\lambda_i$ 也是 $P$ 的特征值，且 $v_i$ 是对应的特征向量，即 $P v_i = \lambda_i v_i$。
   
        !!! theorem "定理（可直接使用）"
            设矩阵 $A \in \mathbb{R}^{n \times n}$ 为实对称矩阵，则存在正交矩阵 $U$ 和对角矩阵 $\Lambda = \text{diag}(\lambda_1, \dots, \lambda_n)$，使得 $A = U \Lambda U^T$。其中 $\lambda_1 \ge \lambda_2 \ge \dots \ge \lambda_n$ 为 $A $ 的特征值，$ U$ 的列向量 $u_1, \dots, u_n$ 构成 $\mathbb{R}^n$ 的一组标准正交基，且 $A u_i = \lambda_i u_i$。
    2. 在函数空间 $\mathbb{R}^n$ 上定义 $\pi$-内积：对于任意 $x, y \in \mathbb{R}^n$，
       
        $$ \langle x, y \rangle_\pi = \sum_{z \in [n]} \pi(z) x(z) y(z) = x^T \Pi y. $$
       
        定义转移矩阵 $P$ 关于该内积的*瑞利商 (Rayleigh quotient)* 为 $R_P(x) = \frac{\langle x, Px \rangle_\pi}{\langle x, x \rangle_\pi}$（其中 $x \neq 0$）。
        
        1. 请证明 $P$ 的第 $k$ 大特征值 $\lambda_k$ 可以表示为：
           
            $$ \lambda_k = \max_{\substack{x \neq 0 \\ \langle x, v_i \rangle_\pi = 0, \forall i < k}} \frac{\langle x, Px \rangle_\pi}{\langle x, x \rangle_\pi}. $$
           
      	1. 请证明 $\lambda_1 = 1$。并进一步证明：如果该马尔可夫链是不可约的，则 $\lambda_1 = 1$ 的几何重数为 $1$，即 $\lambda_2 < 1$。
        2. 如果该马尔可夫链是无周期的，请证明 $\lambda_n > -1$。
    3. 请利用上述谱分解结论，证明对于任意的 $(x, y)$：
       
        $$ P^t(x,y) = \sum_{i=1}^n \lambda_i^t\, v_i(x)\cdot\pi(y)v_i(y). $$
       
        并且证明当该马尔可夫链是不可约且无周期的，对于任意的 $x\in [n]$，有
       
        $$ \lim_{t \to \infty} P^t(x, \cdot) = \pi. $$

=== "English"
	In the main text and the previous problem, we introduced how to prove the fundamental theorem using coupling. In this problem, we will prove it for reversible Markov chains using spectral decomposition. Let $P$ be the transition matrix of a reversible Markov chain on state space $\Omega=[n]$ with stationary distribution $\pi$.
    
    1. Define the diagonal matrix $\Pi = \text{diag}(\pi)$ and the matrix $Q = \Pi^{1/2} P \Pi^{-1/2}$. By the spectral theorem below, $Q$ admits a spectral decomposition $Q= U \Lambda U^T$. Defining the column vectors $v_i = \Pi^{-1/2} u_i$, prove that $\lambda_i$ is also an eigenvalue of $P$, and that $v_i$ is its corresponding eigenvector, meaning $P v_i = \lambda_i v_i$.
   
        !!! theorem "Theorem (Can be used directly)"
            Let $A \in \mathbb{R}^{n \times n}$ be a real symmetric matrix. Then there exist an orthogonal matrix $U$ and a diagonal matrix $\Lambda = \text{diag}(\lambda_1, \dots, \lambda_n)$ such that $A = U \Lambda U^T$. Here, $\lambda_1 \ge \lambda_2 \ge \dots \ge \lambda_n$ are the eigenvalues of $A$, and the columns $u_1, \dots, u_n$ of $U$ form an orthonormal basis of $\mathbb{R}^n$ with $A u_i = \lambda_i u_i$.
    2. Define a $\pi$-inner product on the function space $\mathbb{R}^n$: for any $x, y \in \mathbb{R}^n$,
       
        $$ \langle x, y \rangle_\pi = \sum_{z \in [n]} \pi(z) x(z) y(z) = x^T \Pi y. $$
       
        Define the *Rayleigh quotient* of the transition matrix $P$ with respect to this inner product as $R_P(x) = \frac{\langle x, Px \rangle_\pi}{\langle x, x \rangle_\pi}$ (for $x \neq 0$).
        
        1. Prove that the $k$-th largest eigenvalue $\lambda_k$ of $P$ can be expressed as:
           
            $$ \lambda_k = \max_{\substack{x \neq 0 \\ \langle x, v_i \rangle_\pi = 0, \forall i < k}} \frac{\langle x, Px \rangle_\pi}{\langle x, x \rangle_\pi}. $$
           
        2. Prove that $\lambda_1 = 1$. Furthermore, show that if the Markov chain is irreducible, then the geometric multiplicity of $\lambda_1 = 1$ is $1$, which implies $\lambda_2 < 1$.
        3. If the Markov chain is aperiodic, prove that $\lambda_n > -1$.
    3. Using the spectral decomposition results above, prove that for any pair $(x, y)$:
       
        $$ P^t(x,y) = \sum_{i=1}^n \lambda_i^t\, v_i(x)\cdot\pi(y)v_i(y). $$
       
        Moreover, prove that if this Markov chain is both irreducible and aperiodic, then for any $x\in [n]$,
       
        $$ \lim_{t \to \infty} P^t(x, \cdot) = \pi. $$

--8<-- "solutions/chapter_02/problems/problem_spectral_decomposition_of_reversible_chains.md"

### 洗牌的艺术：交换洗牌法 (The Art of Shuffling: Transposition Shuffle)
=== "中文"
    在正文中我们讲过一种随机至顶的洗牌方法，在本题我们考虑另一种方式，对于一副有 $n$ 张牌的牌堆：
    
    - 从 $[n]$ 中均匀随机地选择两个位置 $i, j$（允许 $i = j$）；
    - 交换牌堆中第 $i$ 张和第 $j$ 张牌。
    
    <!-- -->

    1. 证明这个链是不可约的、非周期的，并且均匀分布是其唯一的平稳分布。
    2. 证明上述洗牌方法等价于以下方法：  
        - 从 $[n]$ 中随机选择一个位置 $i$，并且独立地均匀随机选择一张牌 $c$（例如 $c = \clubsuit Q$）；
        - 将牌 $c$ 与牌堆中第 $i$ 张牌交换。
    3. 证明上述洗牌方法的混合时间是 $O(n^2)$。

=== "English"
    In the main text we introduced the top-to-random shuffle. Here we consider another shuffling method. For a deck of $n$ cards:
    
    - Uniformly and randomly choose two positions $i, j$ from $[n]$ (allowing $i = j$);
    - Swap the $i$-th and $j$-th cards in the deck.
    
    <!-- -->
    
    1. Prove that this chain is irreducible and aperiodic, and that the uniform distribution is its unique stationary distribution.
    2. Prove that the shuffling method above is equivalent to the following:
        - Randomly choose a position $i$ from $[n]$, and independently uniformly pick a card $c$ (e.g., $c = \clubsuit Q$);
        - Swap card $c$ with the $i$-th card in the deck.
    3. Prove that the mixing time of this shuffling method is $O(n^2)$.

--8<-- "solutions/chapter_02/problems/problem_the_art_of_shuffling_transposition_shuffle.md"

### 洗牌的艺术：顶牌随机插入法 (The Art of Shuffling: Top-to-Random Shuffle)
=== "中文"
    正文里我们用耦合的技术分析了随机至顶洗牌方法的混合时间，现在考虑我们在第二章开头提过的另一种洗牌方法：顶牌随机插入法（Top-to-random shuffle）。
    考虑一副有 $n$ 张牌的牌堆。在每一次洗牌操作中，我们将当前牌堆顶部的第一张牌抽出，并将其以相等的概率（$1/n$）随机插入到牌堆的 $n$ 个可能位置之一（包括留在顶部）。该马尔可夫链的状态空间 $\Omega$ 为由 $n$ 张牌的所有排列组成的集合 $\mathcal{S}_n$。
    
    注意到我们无法像随机至顶洗牌法那样构造一个简单的耦合来分析混合时间，因此我们需要引入一些新的概念和工具。
    
    1. 证明：该马尔可夫链是不可约、非周期的，其唯一的平稳分布 $\pi$ 为 $\Omega$ 上的均匀分布。
    2. 对于具有平稳分布 $\pi$ 的马尔可夫链 $\{X_t\}$，定义*强平稳时间（strong stationary time）* $\tau$ 为一个可能依赖于初始状态 $x$ 的停时，满足：对于任意状态 $y$ 和时间 $t$，有：
       
        $$ \Pr[x]{\tau = t, X_\tau = y} = \Pr[x]{\tau = t}\pi(y). $$
       
        其中 $\mathbb{P}_x$ 表示初始状态为 $x$ 时的概率。换言之，在时刻 $\tau$ 时，马尔可夫链的状态 $X_\tau$ 服从平稳分布 $\pi$，且与停时 $\tau$ 独立。
        
        令 $\tau_{\text{top}}$ 为初始牌堆最底部的牌首次被洗入牌堆内部的时间（即原底牌第一次到达牌顶后，进行的再下一次洗牌的时间）。请证明：$\tau_{\text{top}}$ 是该洗牌过程的一个强平稳时间。
    3. 下面我们来证明，强平稳时间可以用来界定马尔可夫链的混合时间。
        1. 设 $\tau$ 为强平稳时间，请证明对于任意 $t \ge 0$，有：
           
            $$ \Pr[x]{\tau \le t, X_t = y} = \Pr[x]{\tau \le t}\pi(y). $$
           
        2. 利用（a）的结论证明
           
            $$ d(t) = \max_{x \in \Omega} \dTV (P^t(x, \cdot), \pi)\le \max_{x \in \Omega} \Pr[x]{\tau > t}. $$
           
            ??? hint "提示"
                定义 $s_x(t) \defeq \max_{y \in \Omega} \left[ 1 - \frac{P^t(x,y)}{\pi(y)} \right]$。可以先分别证明 $s_x(t) \le \Pr[x]{\tau > t}$ 和 $\dTV (P^t(x, \cdot), \pi) \le s_x(t)$。
    4. 结合前三小问的结论，请证明顶牌随机插入法的混合时间 $\tau_{\text{mix}}(\varepsilon)=O\left(n\log \frac{n}{\varepsilon}\right)$。

=== "English"
	In the main text, we analyzed the mixing time of the random-to-top shuffle using coupling techniques. Now, consider another shuffling method mentioned at the beginning of Chapter 2: the top-to-random shuffle.
    Consider a deck of $n$ cards. In each shuffling step, we take the top card and insert it randomly into one of the $n$ possible positions in the deck (including remaining at the top) with equal probability ($1/n$). The state space $\Omega$ of this Markov chain is the set of all permutations of the $n$ cards, denoted as $\mathcal{S}_n$.
    
    Because we cannot construct a simple coupling like we did for the random-to-top shuffle, we need to introduce some new concepts and tools to analyze its mixing time.
    
    1. Prove that this Markov chain is irreducible and aperiodic, and its unique stationary distribution $\pi$ is the uniform distribution over $\Omega$.
    2. For a Markov chain $\{X_t\}$ with stationary distribution $\pi$, define a *strong stationary time* $\tau$ as a stopping time (which may depend on the initial state $x$) satisfying: for any state $y$ and time $t$,
       
        $$ \Pr[x]{\tau = t, X_\tau = y} = \Pr[x]{\tau = t}\pi(y). $$
       
        Here, $\mathbb{P}_x$ denotes the probability given the initial state $x$. In other words, at time $\tau$, the state $X_\tau$ of the Markov chain follows the stationary distribution $\pi$, and is independent of the stopping time $\tau$.
        
        Let $\tau_{\text{top}}$ be the time when the original bottom card of the deck is first shuffled into the interior of the deck (i.e., the time of the shuffle immediately after the original bottom card reaches the top for the first time). Prove that $\tau_{\text{top}}$ is a strong stationary time for this shuffling process.
    3. Next, we will show how strong stationary times can be used to bound the mixing time of a Markov chain.
        1. Let $\tau$ be a strong stationary time. Prove that for any $t \ge 0$:
           
            $$ \Pr[x]{\tau \le t, X_t = y} = \Pr[x]{\tau \le t}\pi(y). $$
           
        2. Use the result from (a) to prove:
           
            $$ d(t) = \max_{x \in \Omega} \dTV (P^t(x, \cdot), \pi)\le \max_{x \in \Omega} \Pr[x]{\tau > t}. $$
           
            ??? hint "Hint"
                Define $s_x(t) \defeq \max_{y \in \Omega} \left[ 1 - \frac{P^t(x,y)}{\pi(y)} \right]$. You can first show that $s_x(t) \le \Pr[x]{\tau > t}$ and $\dTV (P^t(x, \cdot), \pi) \le s_x(t)$.
    4. Combining the results from the previous three parts, prove that the mixing time of the top-to-random shuffle is $\tau_{\text{mix}}(\varepsilon)=O\left(n\log \frac{n}{\varepsilon}\right)$.

--8<-- "solutions/chapter_02/problems/problem_the_art_of_shuffling_top_to_random_shuffle.md"
    
### 独立意志与从众心理 (Independent Will and Herd Mentality)
=== "中文"
    在社交网络中，用户的观点演化常常受到独立思考与从众心理的共同影响。我们考察一个由 $n$ 个用户组成的无向连通社交网络 $G=(V, E)$，假设图 $G$ 是一个 $d$-正则图，即每个用户都恰好有 $d$ 个邻居。每个用户 $v \in V$ 在时刻 $t$ 持有一个二元观点 $X_t(v) \in \{+1, -1\}$。全局状态记为 $X_t \in \{+1, -1\}^V$。在每一步里，系统按照*噪声投票者模型（noisy voter model）*进行演化：
    
    - 均匀随机地选中一个用户 $v \in V$。
    - 以概率 $\alpha \in [0, 1)$，用户 $v$ 展现独立意志，即从 $\{+1, -1\}$ 中均匀随机地选取一个新观点。
    - 以概率 $1-\alpha$，用户 $v$ 展现从众心理，从它的 $d$ 个邻居中均匀随机地选中一个邻居 $u$，并完全复制 $u$ 当前的观点，即 $X_{t+1}(v) = X_t(u)$。
    - 集合 $V \setminus \{v\}$ 中的其余用户的观点保持不变。
    
    <!-- -->
    
    1. 我们首先来分析该马尔可夫链平稳分布的唯一性。
        1. 假设网络完全没有独立意志，即 $\alpha = 0$，此为经典的投票者模型（voter model）。请说明该马尔可夫链平稳分布不唯一。
        2. 当 $\alpha \in (0, 1)$ 时，请证明该马尔可夫链是不可约且无周期的。
    2. 在一般的 $d$-正则图上，平稳分布极其复杂且不满足细致平衡条件。为了探究平稳分布的宏观特性，我们考虑完全图（$d=n-1$），考察该系统中持 $+1$ 观点的用户总数 $k \in \{0, 1, \dots, n\}$ 的演变。令参数 $\beta = \frac{\alpha(n-1)}{2(1-\alpha)}$。
        1. 请写出该链的单步转移概率 $P_{k \to k+1}$ 和 $P_{k \to k-1}$，并证明其平稳分布满足：
           
            $$ \pi(k) \propto \binom{n}{k} \cdot \Gamma(\beta+k)\cdot \Gamma(\beta+n-k) $$
           
            ，其中 $\Gamma(\cdot)$ 为伽马函数：对 $z>0$，
           
            $$ \Gamma(z)=\int_0^{\infty} t^{z-1}e^{-t}\dd t, \qquad \text{且满足}\Gamma(z+1)=z\Gamma(z). $$
           
        2. 通过分析 $\frac{\pi(k+1)}{\pi(k)}$ 的单调性，说明，当 $\alpha > \frac{2}{n+1}$ 时，宏观上看，平稳时倾向于形成一半人支持 $+1$，一半人支持 $-1$ 的无序状态；当 $\alpha < \frac{2}{n+1}$ 时，平稳状态时更倾向于形成大多数人支持同一观点的信息茧房状态。
    3. 我们回到一般的 $d$-正则图，分析 $\alpha \in (0, 1)$ 时系统收敛到平稳状态的速度，即使我们算不出平稳分布，但可以通过这个马尔可夫链快速地生成独立的近似样本，并通过这些样本来估计系统的性质。
       
        对于任意两个初始状态为 $X_0$ 和 $Y_0 $ 的马尔可夫链，构造耦合：在时刻 $ t$，两链选中同一个用户 $v$，使用同一个有偏硬币决定用户 $v$ 是否持独立意志更新；若独立，赋予其同一个随机观点；若从众，随机选择 $v$ 的同一个邻居 $u$ 并复制其观点给 $v$。
        
        定义时刻 $t$ 的汉明距离 $H(X_t, Y_t) = |D_t|$，其中 $D_t = \{ w \in V | X_t(w) \neq Y_t(w) \}$。
        
        1. 请证明单步距离变化的期望满足
           
            $$ \E{H(X_{t+1}, Y_{t+1}) - H(X_t, Y_t) | X_t, Y_t} = -\frac{\alpha}{n} H(X_t, Y_t) $$
           
        2. 请证明该马尔可夫链的混合时间满足
           
            $$ \tau_{\text{mix}}(\epsilon) = O\left( \frac{n}{\alpha} \log \frac{n}{\epsilon} \right). $$

=== "English"
    In social networks, the evolution of users' opinions is often jointly influenced by independent thinking and herd mentality. Consider an undirected connected social network $G=(V, E)$ consisting of $n$ users, and suppose $G$ is a $d$-regular graph, meaning each user has exactly $d$ neighbors. Each user $v \in V$ holds a binary opinion $X_t(v) \in \{+1, -1\}$ at time $t$. The global state is given by $X_t \in \{+1, -1\}^V$. In each step, the system evolves according to the *noisy voter model*:
    
    - A user $v \in V$ is chosen uniformly at random.
    - With probability $\alpha \in [0, 1)$, user $v$ exercises their independent will, picking a new opinion uniformly at random from $\{+1, -1\}$.
    - With probability $1-\alpha$, user $v$ exhibits herd mentality, selecting a neighbor $u$ uniformly at random from their $d$ neighbors, and directly copying $u$ 's current opinion, such that $X_{t+1}(v) = X_t(u)$.
    - The opinions of all other users in $V \setminus \{v\}$ remain unchanged.
    
    <!-- -->
    
    1. Let us first analyze the uniqueness of the stationary distribution for this Markov chain.
        1. Assume the network completely lacks independent will, i.e., $\alpha = 0$. This corresponds to the standard voter model. Explain why the stationary distribution of this Markov chain is not unique.
        2. For $\alpha \in (0, 1)$, prove that this Markov chain is irreducible and aperiodic.
    2. On a general $d$-regular graph, the stationary distribution is extremely complex and does not satisfy the detailed balance condition. To investigate the macroscopic characteristics of the stationary distribution, we consider a complete graph ($d=n-1$) and study the evolution of the total number of users $k \in \{0, 1, \dots, n\}$ holding the $+1$ opinion. Let the parameter be $\beta = \frac{\alpha(n-1)}{2(1-\alpha)}$.
        1. Provide the single-step transition probabilities $P_{k \to k+1}$ and $P_{k \to k-1}$ for this chain, and prove that its stationary distribution satisfies:
           
            $$ \pi(k) \propto \binom{n}{k} \cdot \Gamma(\beta+k)\cdot \Gamma(\beta+n-k) $$
           
            where $\Gamma(\cdot)$ is the Gamma function: for $z>0$,
           
            $$ \Gamma(z)=\int_0^{\infty} t^{z-1}e^{-t}\dd t, \qquad \text{and satisfies }\Gamma(z+1)=z\Gamma(z). $$
           
        2. By analyzing the monotonicity of $\frac{\pi(k+1)}{\pi(k)}$, show that when $\alpha > \frac{2}{n+1}$, macroscopically, the system at equilibrium tends to form a disordered state where half the population supports $+1$ and the other supports $-1$; when $\alpha < \frac{2}{n+1}$, the equilibrium state is more likely to form an echo chamber where the vast majority supports a single opinion.
    3. Returning to a general $d$-regular graph, let's analyze the rate at which the system converges to equilibrium for $\alpha \in (0, 1)$. Even if we cannot exactly compute the stationary distribution, we can rapidly generate approximately independent samples from this Markov chain to estimate the system properties.
       
        Construct a coupling for two Markov chains starting from arbitrary initial states $X_0$ and $Y_0$: at time $t$, both chains select the same user $v$, and use the same biased coin to determine if $v$ updates via independent will; if independent, both chains assign the same random opinion to $v$; if herding, they pick the same neighbor $u$ of $v$ and copy its opinion to $v$.
        
        Define the Hamming distance at time $t$ as $H(X_t, Y_t) = |D_t|$, where $D_t = \{ w \in V | X_t(w) \neq Y_t(w) \}$.
        
        1. Prove that the expected change in distance for a single step satisfies:
           
            $$ \E{H(X_{t+1}, Y_{t+1}) - H(X_t, Y_t) | X_t, Y_t} = -\frac{\alpha}{n} H(X_t, Y_t) $$
           
        2. Prove that the mixing time of this Markov chain satisfies:
           
            $$ \tau_{\text{mix}}(\epsilon) = O\left( \frac{n}{\alpha} \log \frac{n}{\epsilon} \right). $$

--8<-- "solutions/chapter_02/problems/problem_independent_will_and_herd_mentality.md"
    


