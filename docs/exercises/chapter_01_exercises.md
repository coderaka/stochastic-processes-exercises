# 第一章 独立随机变量 (Independent Random Variables)

## 练习 (Exercises) {: .ex-counter style="counter-reset: chapter 1 question 0;" }

### 再探奖券收集问题 (Coupon Collector Revisited)
=== "中文"
    在正文中，我们用切比雪夫不等式分析了奖券收集问题，得到了 $\Pr{Y\ge n H_n+t}\le \frac{2n^2}{t^2}$，其中 $n$ 是奖券类型总数， $Y$ 是收集齐全 $n$ 种奖券所需的抽奖次数，$H_n$ 是调和数。现在我们用另一种方法来计算这个问题的集中性。
    
    1. 请用联合界分析存在一种奖券类型在前 $n H_n + t$ 次抽奖中都没有被抽到的概率。并据此证明
    	$$
    	\Pr{Y\ge n H_n+t}\le e^{-t/n}.
    	$$
    2. 请根据上一问结论，计算在 $n=100$时，开多少包可以保证以至少 $99\%$ 的概率收集全一套？把你的界和切比雪夫不等式得到的界进行比较。
    
=== "English"
    In the main text, we analyzed the coupon collector's problem using Chebyshev's inequality and showed that $\Pr{Y\ge n H_n+t}\le \frac{2n^2}{t^2}$, where $n$ is the total number of coupon types, $Y$ is the number of draws required to collect all $n$ types, and $H_n$ is the harmonic number. Now we use an alternative approach to bound the concentration of this process.
    
    1. Use the union bound to analyze the probability that there exists a coupon type not drawn in the first $n H_n + t$ draws. Use this to prove that
    	$$
    	\Pr{Y\ge n H_n+t}\le e^{-t/n}.
    	$$
    2. Based on the previous result, calculate the number of packs required to collect a full set with probability at least $99\%$ for $n=100$. Compare your bound with the one obtained from Chebyshev's inequality.

--8<-- "solutions/chapter_01/exercises/exercise_coupon_collector.md"

### 最大负载期望上界 (Upper Bound on Expected Maximum Load)
=== "中文"
    在正文中我们证明了，当 $n$ 个球随机投入 $n$ 个箱子中时，最大负载 $X = \max_{i\in[n]} X_i$ 满足：
    $$
    \Pr{X \ge \frac{6 \log n}{\log \log n}} \le \frac{1}{n}.
    $$
    请利用这一尾部概率的结论，以及 $0\le X \le n$ 的事实，证明最大负载的期望满足 $\E{X} = O\tp{\frac{\log n}{\log\log n}}$。
=== "English"
    In the main text, we proved that when $n$ balls are randomly thrown into $n$ bins, the maximum load $X = \max_{i\in[n]} X_i$ satisfies:
    $$
    \Pr{X \ge \frac{6 \log n}{\log \log n}} \le \frac{1}{n}.
    $$
    Using this tail probability bound and the fact that $0\le X \le n$, prove that the expected maximum load satisfies $\E{X} = O\tp{\frac{\log n}{\log\log n}}$.

--8<-- "solutions/chapter_01/exercises/exercise_max_load.md"

### 精确计数内存下界 (Memory Lower Bound for Exact Counting)
=== "中文"
    在流模型计算流长度的问题中，我们提到，任何试图精确计算数据流长度 $m$ 的确定性算法，如果内存不足，则必然会出错。
    
    1. 请使用鸽巢原理，严格证明：任何状态数少于 $N+1$ 的确定性算法，必定无法对所有长度不超过 $N$ 的数据流给出精确的计数。这说明，任何保证精确计数的确定性算法至少需要 $\lceil \log_2(N+1) \rceil$ 比特的内存。
    2. 如果不限制是确定性算法，而是允许使用随机算法，但依然要求算法在任何输入下都必须零误差输出流长度 $m$，它能否比确定性算法消耗更少的峰值内存空间？请证明你的结论。
    
=== "English"
    In the problem of computing the stream length $m$ in the streaming model, we mentioned that any deterministic algorithm attempting exact counting will inevitably fail if its memory is insufficient.
    
    1. Use the pigeonhole principle to rigorously prove that any deterministic algorithm with fewer than $N+1$ states cannot output the exact count for all data streams of length up to $N$. This implies that any deterministic algorithm guaranteeing exact counting requires at least $\lceil \log_2(N+1) \rceil$ bits of memory.
    2. If we allow randomized algorithms instead of restricting to deterministic ones, but still require the algorithm to output the stream length $m$ with zero error on any input, can it consume less peak memory space than a deterministic algorithm? Prove your conclusion.

--8<-- "solutions/chapter_01/exercises/exercise_exactness.md"

### 多数人的智慧 (Wisdom of the Majority)
=== "中文"
    假设你有一个预测股市明天涨跌的算法。该算法每次独立进行预测时，都会以 $\frac{3}{4}$ 的概率给出正确的建议。为了提升预测的准确率，你决定让该算法独立运行 $N$ 次，并采用多数表决（majority vote）的方式得出最终的投资决策。请证明：对于任意给定的允许出错的概率上限 $\delta \in (0, 1)$，只要运行次数满足
    $$
    N \ge 8 \ln\tp{\frac{1}{\delta}},
    $$
    这种多数表决策略就能以至少 $1 - \delta$ 的概率给出正确的投资决策。
    
=== "English"
    Suppose you have an algorithm that predicts whether the stock market will go up or down tomorrow. Each time the algorithm makes an independent prediction, it gives the correct advice with probability $\frac{3}{4}$. To improve the prediction accuracy, you decide to run the algorithm independently $N$ times and use a majority vote to make the final investment decision. Prove that for any given error probability bound $\delta \in (0, 1)$, as long as the number of runs satisfies
    $$
    N \ge 8 \ln\tp{\frac{1}{\delta}},
    $$
    this majority vote strategy will yield the correct investment decision with probability at least $1 - \delta$.

--8<-- "solutions/chapter_01/exercises/exercise_majority_vote.md"

### 高斯分布的集中性 (Concentration of Gaussian Distribution)
=== "中文"
    设 $X \sim \+N(0, 1)$ 为标准高斯随机变量。我们来探究其尾部概率的精确上下界。

    1. 请证明对于任意 $x > 0$，有如下积分不等式成立：
    	$$
    	(x^{-1} - x^{-3})e^{-x^2/2} \le \int_x^{+\infty} e^{-y^2/2} \dd y \le x^{-1} e^{-x^2/2}.
    	$$
    2. 利用上述结论，证明标准高斯分布的尾部概率 $\Pr{\abs{X} \ge t}$ 的上下界（$t>0$），并说明当 $t$ 足够大时，该概率为 $\Theta\tp{t^{-1} \exp(-t^2/2)}$。进一步地，证明当 $t \to +\infty$ 时，有如下渐近等价关系：
    	$$
    	\Pr{\abs{X} \ge t} \sim \sqrt{\frac{2}{\pi}} t^{-1} \exp(-t^2/2).
    	$$
=== "English"
    Let $X \sim \+N(0, 1)$ be a standard Gaussian random variable. We explore tight upper and lower bounds for its tail probability.

    1. Prove that for any $x > 0$, the following integral inequalities hold:
    	$$
    	(x^{-1} - x^{-3})e^{-x^2/2} \le \int_x^{+\infty} e^{-y^2/2} \dd y \le x^{-1} e^{-x^2/2}.
    	$$
    2. Using the above result, prove the upper and lower bounds for the tail probability $\Pr{\abs{X} \ge t}$ of the standard Gaussian distribution (for $t>0$), and show that when $t$ is sufficiently large, this probability is $\Theta\tp{t^{-1} \exp(-t^2/2)}$. Furthermore, prove that as $t \to +\infty$, the following asymptotic equivalence holds:
    	$$
    	\Pr{\abs{X} \ge t} \sim \sqrt{\frac{2}{\pi}} t^{-1} \exp(-t^2/2).
    	$$

--8<-- "solutions/chapter_01/exercises/exercise_gaussian_concentration.md"

### 纠缠的极值 (Entangled Extremes)
=== "中文"
    设 $X_1, X_2, \dots, X_n$ 为 $n$ 个标准高斯分布的随机变量，即对所有 $i \in [n]$ 有 $X_i \sim \+N(0, 1)$。这里我们不要求它们是相互独立的。令 $Z = \max_{i \in [n]} X_i$ 表示它们的最大值。请证明：
    $$
    \E{Z} \le \sqrt{2 \log n}.
    $$
=== "English"
    Let $X_1, X_2, \dots, X_n$ be $n$ standard Gaussian random variables, i.e., $X_i \sim \+N(0, 1)$ for all $i \in [n]$. Here, we do not require them to be mutually independent. Let $Z = \max_{i \in [n]} X_i$ denote their maximum value. Prove that:
    $$
    \E{Z} \le \sqrt{2 \log n}.
    $$

--8<-- "solutions/chapter_01/exercises/exercise_entangled_extremes.md"

### 次高斯分布初探 (Introduction to Sub-Gaussian Distributions)
=== "中文"
    如果一个均值为 $0$ 的随机变量 $X$，其矩生成函数满足，对于任意 $\lambda \in \bb R$，有 $\E{e^{\lambda X}} \le \exp\tp{\frac{\lambda^2 \sigma^2}{2}}$，我们称 $X$ 是参数为 $\sigma^2$ 的次高斯随机变量。

    1. **（集中性）**请模仿正文中切尔诺夫界的证明，证明如果 $X$ 是均值为 $0$、参数为 $\sigma^2$ 的次高斯随机变量，则对于任意 $t>0$，有 $\Pr{X \ge t} \le \exp\tp{-\frac{t^2}{2\sigma^2}}$。
    2. **（可加性）**证明：若 $X_1$ 和 $X_2$ 是相互独立的次高斯随机变量，均值为 $0$ 且参数分别为 $\sigma_1^2$ 和 $\sigma_2^2$，那么它们的和 $X_1 + X_2$ 也是次高斯随机变量，并且其参数为 $\sigma_1^2 + \sigma_2^2$。
    3. **（有界变量即次高斯）**请结合正文中证明过的霍夫丁引理，说明：如果随机变量 $X$ 满足 $\E{X} = 0$ 且 $X\in[a, b]$，那么 $X$ 是一个参数为 $\sigma^2 = \frac{(b-a)^2}{4}$ 的次高斯随机变量。
    
=== "English"
    A random variable $X$ with mean $0$ is called a sub-Gaussian random variable with parameter $\sigma^2$ if its moment generating function satisfies $\E{e^{\lambda X}} \le \exp\tp{\frac{\lambda^2 \sigma^2}{2}}$ for all $\lambda \in \bb R$.

    1. **(Concentration)** Emulating the proof of the Chernoff bound in the main text, prove that if $X$ is a zero-mean sub-Gaussian random variable with parameter $\sigma^2$, then for any $t>0$, $\Pr{X \ge t} \le \exp\tp{-\frac{t^2}{2\sigma^2}}$.
    2. **(Additivity)** Prove that if $X_1$ and $X_2$ are independent zero-mean sub-Gaussian random variables with parameters $\sigma_1^2$ and $\sigma_2^2$ respectively, then their sum $X_1 + X_2$ is also a sub-Gaussian random variable with parameter $\sigma_1^2 + \sigma_2^2$.
    3. **(Bounded implies sub-Gaussian)** Using Hoeffding's lemma proved in the main text, show that if a random variable $X$ satisfies $\E{X} = 0$ and $X\in[a, b]$, then $X$ is a sub-Gaussian random variable with parameter $\sigma^2 = \frac{(b-a)^2}{4}$.

--8<-- "solutions/chapter_01/exercises/exercise_sub_gaussian_intro.md"

### 次指数分布初探 (Introduction to Sub-Exponential Distributions)
=== "中文"
    在前面的练习中我们探讨了次高斯分布。然而，许多常见的随机变量（例如高斯随机变量的平方，即卡方分布）的尾部比高斯分布更厚，它们并不满足次高斯分布的条件。为此，我们引入次指数分布的概念。

    我们称一个随机变量 $X$ 为参数为 $(\nu, \alpha)$ 的次指数（sub-exponential）随机变量（其中 $\nu, \alpha > 0$），如果其中心化后的矩生成函数满足：对于任意 $\abs{\lambda} \le \frac{1}{\alpha}$，有
    $$
    \E{e^{\lambda (X - \E{X})}} \le \exp\tp{\frac{\lambda^2 \nu}{2}}.
    $$
    1. **（集中性）**请证明：如果 $X$ 是参数为 $(\nu, \alpha)$ 的次指数随机变量，那么对于任意 $t \ge 0$，有
    	$$
    	\Pr{X - \E{X} \ge t} \le
        \left\lbrace\begin{aligned}
    &\exp\tp{-\frac{t^2}{2\nu}}, && \text{若 } t \in \stp{0, \frac{\nu}{\alpha}}; \cr
    &\exp\tp{-\frac{t}{2\alpha}}, && \text{若 } t \in \tp{\frac{\nu}{\alpha}, \infty}.
    \end{aligned}\right.
    	$$
    2. **（可加性）**假设 $X_1, \dots, X_N$ 是相互独立的随机变量，且每个 $X_i$ 都是参数为 $(\nu_i, \alpha_i)$ 的次指数随机变量。证明：对于任意常数 $w_1, \dots, w_N \in \bb R$，加权和 $\sum_{i=1}^N w_i X_i$ 也是次指数随机变量，且其参数为 $\tp{\sum_{i=1}^N w_i^2 \nu_i, \max_{i \in [N]} \abs{w_i} \alpha_i}$。
   
    3. **（广义伯恩斯坦不等式）**结合前两问的结论，证明广义伯恩斯坦不等式（generalized Bernstein inequality）：在上一问的条件下，记 $S_N = \sum_{i=1}^N w_i X_i$，对于任意 $t \ge 0$，有
    	$$
    	\Pr{S_N - \E{S_N} \ge t} \le
        \left\lbrace\begin{aligned}
    &\exp\tp{-\frac{t^2}{2\sum_{i=1}^N w_i^2 \nu_i}}, && \text{若 } t \in \stp{0, \frac{\sum_{i=1}^N w_i^2 \nu_i}{\max_{i \in [N]} \abs{w_i} \alpha_i}}; \cr
    &\exp\tp{-\frac{t}{2\max_{i \in [N]} \abs{w_i} \alpha_i}}, && \text{其他情况.}
    \end{aligned}\right.
    	$$
=== "English"
    In the previous exercises, we explored sub-Gaussian distributions. However, many common random variables (such as the square of a Gaussian random variable, i.e., the $\chi^2$-distribution) have heavier tails than the Gaussian distribution and do not satisfy the sub-Gaussian condition. For this reason, we introduce the concept of sub-exponential distributions.

    A random variable $X$ is called a sub-exponential random variable with parameters $(\nu, \alpha)$ (where $\nu, \alpha > 0$) if its centered moment generating function satisfies the following condition: for any $\abs{\lambda} \le \frac{1}{\alpha}$,
    $$
    \E{e^{\lambda (X - \E{X})}} \le \exp\tp{\frac{\lambda^2 \nu}{2}}.
    $$
    1. **(Concentration)** Prove that if $X$ is a sub-exponential random variable with parameters $(\nu, \alpha)$, then for any $t \ge 0$,
    	$$
    	\Pr{X - \E{X} \ge t} \le
        \left\lbrace\begin{aligned}
    &\exp\tp{-\frac{t^2}{2\nu}}, && \text{if } t \in \stp{0, \frac{\nu}{\alpha}}; \cr
    &\exp\tp{-\frac{t}{2\alpha}}, && \text{if } t \in \tp{\frac{\nu}{\alpha}, \infty}.
    \end{aligned}\right.
    	$$
    2. **(Additivity)** Suppose $X_1, \dots, X_N$ are independent random variables, and each $X_i$ is a sub-exponential random variable with parameters $(\nu_i, \alpha_i)$. Prove that for any constants $w_1, \dots, w_N \in \bb R$, the weighted sum $\sum_{i=1}^N w_i X_i$ is also a sub-exponential random variable, and its parameters are $\tp{\sum_{i=1}^N w_i^2 \nu_i, \max_{i \in [N]} \abs{w_i} \alpha_i}$.
   
    3. **(Generalized Bernstein Inequality)** Using the results from the previous two parts, prove the generalized Bernstein inequality: under the conditions of the previous part, let $S_N = \sum_{i=1}^N w_i X_i$. Then for any $t \ge 0$,
    	$$
    	\Pr{S_N - \E{S_N} \ge t} \le
        \left\lbrace\begin{aligned}
    &\exp\tp{-\frac{t^2}{2\sum_{i=1}^N w_i^2 \nu_i}}, && \text{if } t \in \stp{0, \frac{\sum_{i=1}^N w_i^2 \nu_i}{\max_{i \in [N]} \abs{w_i} \alpha_i}}; \cr
    &\exp\tp{-\frac{t}{2\max_{i \in [N]} \abs{w_i} \alpha_i}}, && \text{otherwise.}
    \end{aligned}\right.
    	$$

--8<-- "solutions/chapter_01/exercises/exercise_sub_exponential_intro.md"

### 不相关变量集中不等式 (Concentration Inequality for Uncorrelated Variables)
=== "中文"
    在正文中，我们探讨了独立随机变量之和的集中不等式。现在我们放宽条件，看看如果随机变量仅仅是不相关的，能得到怎样的集中性。设 $X_1, X_2, \dots$ 是一系列中心化（即 $\E{X_i} = 0$）且两两不相关的随机变量，即对于任意 $i \neq j$，有 $\E{X_i X_j} = \E{X_i}\E{X_j}$。

    1. 假设存在常数 $C < +\infty$ 使得对所有 $i$ 都有 $\Var{X_i} \le C$。请证明对于任意 $t > 0$，有：
    	$$
    	\Pr{\abs{\frac{1}{n} \sum_{i=1}^n X_i} \ge t} \le \frac{C}{n t^2}.
    	$$
    2. 利用上述结论，证明 $L^2$ 弱大数定律：若 $X_1, X_2, \dots$ 是期望均为 $\mu$、方差一致有界（$\sup_i \Var{X_i} < +\infty$）且两两不相关的随机变量，则其经验均值依概率收敛到 $\mu$，即 $\frac{1}{n} \sum_{i=1}^n X_i \xrightarrow{p} \mu$。
=== "English"
    In the main text, we explored concentration inequalities for the sum of independent random variables. Now we relax this condition to see what degree of concentration can be achieved if the random variables are only uncorrelated. Let $X_1, X_2, \dots$ be a sequence of centered (i.e., $\E{X_i} = 0$) and pairwise uncorrelated random variables, meaning $\E{X_i X_j} = \E{X_i}\E{X_j}$ for any $i \neq j$.

    1. Suppose there exists a constant $C < +\infty$ such that $\Var{X_i} \le C$ for all $i$. Prove that for any $t > 0$:
    	$$
    	\Pr{\abs{\frac{1}{n} \sum_{i=1}^n X_i} \ge t} \le \frac{C}{n t^2}.
    	$$
    2. Using the above result, prove the $L^2$ weak law of large numbers: if $X_1, X_2, \dots$ are pairwise uncorrelated random variables with common mean $\mu$ and uniformly bounded variances ($\sup_i \Var{X_i} < +\infty$), then their empirical mean converges in probability to $\mu$, i.e., $\frac{1}{n} \sum_{i=1}^n X_i \xrightarrow{p} \mu$.

--8<-- "solutions/chapter_01/exercises/exercise_weaker_concentration.md"

### 两两独立下的集中性反例 (Counterexample to Concentration under Pairwise Independence)
=== "中文"
    上一题表明，仅仅是不相关的条件，就足以让我们得到多项式级别的集中不等式。那么，两两独立且有界的随机变量能否像完全独立那样，带来指数级的集中性呢？本题将给出一个反例。

    设 $U = (U_1, \dots, U_\ell)$ 是均匀分布在 $\left\{0, 1\right\}^\ell$ 上的随机向量。令 $n = 2^\ell - 1$。对于任意非零向量 $v \in \left\{0, 1\right\}^\ell \setminus \left\{\*0\right\}$，定义随机变量 $X_v = \inner{U}{v} \pmod 2$。
    1. 请证明：这 $n$ 个随机变量 $X_v$ 均服从 $\left\{0, 1\right\}$ 上的均匀分布，且它们是两两独立的。
    2. 请证明：对于任何由这 $n$ 个随机变量 $\left\{X_v\right\}_{v \neq \*0}$ 生成的事件 $A$（即 $A \in \sigma\tp{\left\{X_v\right\}_{v \neq \*0}}$），其发生的概率 $\Pr{A}$ 要么是 $0$，要么至少是 $\frac{1}{n+1}$。

    <p class="note-inline">注：这说明，由两两独立随机变量构成的系统，不能保证指数尾部概率的衰减。</p>
    
=== "English"
    The previous exercise shows that the condition of being uniformly uncorrelated is sufficient to obtain a polynomial-level concentration inequality. Can pairwise independent and bounded random variables provide exponential concentration, just as fully independent ones do? This problem constructs a counterexample.

    Let $U = (U_1, \dots, U_\ell)$ be a random vector uniformly distributed over $\left\{0, 1\right\}^\ell$. Let $n = 2^\ell - 1$. For any non-zero vector $v \in \left\{0, 1\right\}^\ell \setminus \left\{\*0\right\}$, define the random variable $X_v = \inner{U}{v} \pmod 2$.

    1. Prove that these $n$ random variables $X_v$ are uniformly distributed over $\left\{0, 1\right\}$ and are pairwise independent.
   
    2. Prove that for any event $A$ generated by these $n$ random variables $\left\{X_v\right\}_{v \neq \*0}$ (i.e., $A \in \sigma\tp{\left\{X_v\right\}_{v \neq \*0}}$), its probability $\Pr{A}$ is either $0$ or at least $\frac{1}{n+1}$.

    <p class="note-inline">Note: This implies that a system composed of pairwise independent random variables cannot guarantee exponential decay of tail probabilities.</p>

--8<-- "solutions/chapter_01/exercises/exercise_so_close_yet_far.md"

---
