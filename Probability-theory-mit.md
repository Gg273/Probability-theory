### Lecture 1 概率模型和公理

**样本空间的定义：**实验的所有可能结果的有限集合，集合中的元素必须是互相排斥的，不能两种结果同时出现，且实验的所有结果必须在这个集合中；

离散的样本空间示例：

​	滚动两次四个面的骰子，它的可能结果如下，可以有两种表示的方法：

<img src="W:\Starting from scratch\math\Probability-theory\printscreen\Probabilistic_mit1.png" alt="Probabilistic_mit1" style="zoom:80%;" />

连续的样本空间示例：

​	对于随机投掷飞镖在一方框中的可能结果为：

<img src="W:\Starting from scratch\math\Probability-theory\printscreen\Probabilistic_mit2.png" alt="Probabilistic_mit2" style="zoom:80%;" />

基本概率公理：

1. 非负性：$P(A) \ge 0$
2. 标准化：$P(\Omega) = 1$
3. 可加性：$if A \cap B = \phi  , then \ \ P(A\cup B) = P(A) + P(B)$

由上面几个公理可以简易的推出一个相关公理：$P(A) + P(A^c) = P(A\cup A^c)= P(\Omega) = 1 \rightarrow P(A) = 1 - P(A^c) \le 1$

可数可加定理：如果样本空间中有$A_1,A_2\cdots A_n$为不相交事件，则有$P(A_1\cup A_2\cup \cdots \cup A_n) = P(A_1) +\cdots+ P(A_n)$

对于可数可加定理的简单证明：
$$
P(A_1\cup A_2\cup\cdots\cup A_n) = P((A_1\cup A_2\cup\cdots\cup A_{n-1})\cup A_n)  \\
=P(A_1\cup A_2\cup\cdots\cup A_{n-1}) + P(A_n) \\
=P(A_1) + P(A_2) + \cdots + P(A_n)
$$


Discrete uniform law：

若对于样本空间中的每种可能结果的概率相同，则有：
$$
P(A) = \frac{事件A中的所有结果数}{样本空间中的所有结果数}
$$

### Lecture 2 条件概率和贝叶斯法则

对于可数可加定理在连续的样本空间中的误区：

​	设定一个连续样本空间为 $\Omega = \{(x,y)|0 \le x,y \le 1\}$：
$$
1=P(\Omega) = P(\bigcup_{x,y}{(x,y)}) = \sum_{x,y}P({x,y}) = \sum0 = 0
$$
​	显而易见这里是发生了一些错误的，因为可数可加定理应用的场景应该为可数的序列，而在这里使用可数可加定理的话不可能加完所有的位于连续样本空间中的元素，所以错误出现；

​	而且对于连续样本空间中的 $P=0$ 并不意味着一定不可能发生，比如对于 $P(0.2,0.5) = 0$ 但是它还是有发生的概率，只是极低，同理连续样本空间中 $P=1$ 也不意味着一定会发生；

**条件概率定义：$假设 \ P(B) != 0,  \ P(A|B) = \frac{P(A\cap B)}{P(B)}，而P(B) = 0, P(A|B) 是未定义的$ **

我对于条件概率的理解，可以把发生了的事件B理解为一个新的样本空间；

**Multiplication rule 乘法法则：$P(A\cap B\cap C) = P(A)P(B|A)P(C|A\cap B)$**

简单证明：
$$
P(A\cap B\cap C) = P((A\cap B)\cap C) = P(A\cap B)P(C|A\cap B) \\
=P(A)P(B|A)P(C|A\cap B)
$$
可以通过决策树加深理解

<img src="W:\Starting from scratch\math\Probability-theory\printscreen\Probabilistic_mit3.png" alt="Probabilistic_mit3" style="zoom: 80%;" />

**Total probability theorem 全概率定理：$P(B) = P(B|A_1) + P(B|A_2) + P(B|A_3)$**

这里运用的是分而治之的理解方法，直接上图方便理解

![Probabilistic_mit4](W:\Starting from scratch\math\Probability-theory\printscreen\Probabilistic_mit4.png)

可以推广到更一般的情况：$对于，不相交的事件A_1\cdots A_n，P(B) = P(B|A_1) +P(B|A_2) + \cdots + P(B|A_n)$

**Bayes’ rule 贝叶斯法则：是通过条件概率的定义变形得来**
$$
P(A|B) = \frac{P(A\cap B)}{P(B)} \rightarrow P(A\cap B) = P(B)P(A|B) = P(A)P(B|A) \\
P(A|B) = \frac{P(A)P(B|A)}{P(B)}
$$
**再使用全概率定理结合可以得到进一步的贝叶斯公式：**
$$
P(A_i|B) = \frac{P(A_i)P(B|A_i)}{\sum_j P(A_j)P(B|A_j)}
$$
该公式的意义在于，**通过结果的概率，寻找原因的概率**

$A_i$导致了B，我们知道了所有情境下B发生的概率

于是通过贝叶斯公式，我们就可以得知在B发生的情境下，“原因事件”$A_i$发生的概率

### Lecture 3 独立性

**Independence of two events 对于两个事件的独立性定义：$P(B|A) =P(B) \ or \ P(A\cap B) = P(A)P(B)$ 即事件A发生与否都不影响事件B的发生，事件A和事件B对称成立**

示例思考：一颗6面的骰子，丢到每面的概率都相等为1/6，第一次丢到6的概率应该为1/6，第二次丢到6的概率应该为1/6，不管第多少次丢到6的概率都应该为1/6；

**Conditioning may affect independence 条件作用可能会影响独立性**

示例：两枚不公平的硬币A和B，$P(H | coin A)=0.9, P(H | coin B)=0.1$ 选两枚硬币的概率相同，可以画出决策图

<img src="W:\Starting from scratch\math\Probability-theory\printscreen\Probabilistic_mit5.png" alt="Probabilistic_mit5"  />

如果我们不知道选取的硬币是哪枚，每次抛硬币时是否具有独立性？
$$
P(toss 11 = H) = \frac{1}{2}*0.9 + \frac{1}{2}*0.1 = 0.5 \\
P(toss 11 = H| \ first  \ 10  \ tosses  \ are \  heads) \approx 0.9
$$
**Independence of a collection of events 事件集合的独立性**

**Mathematical definition 数学定义：如果事件 $A_1,A_2 \cdots A_n$ 具有独立性, $P(A_i\cap A_j\cap \cdots \cap A_q) = P(A_i)P(A_j) ··· P(A_q)$ **；

对于一系列事件中每两个事件都具有独立性，并不意味着这一系列事件具有独立性，必须每两个，每三个、到每n个事件都互有独立性，这一系列事件才具有独立性；

示例思考：两公平的抛硬币，记事件A：第一次抛硬币出现的是H，事件B：第二次抛硬币出现的是H，事件C：第一次和第二次抛硬币出现相同的面；

![InkedProbabilistic_mit6](W:\Starting from scratch\math\Probability-theory\printscreen\InkedProbabilistic_mit6.jpg)
$$
P(A) = \frac{1}{2} \ \  P(B) = \frac{1}{2} \ \ P(C) = \frac{1}{2} \\
p(A\cap B) = \frac{1}{4} = P(A)P(B) \\
P(A\cap C) = \frac{1}{4} = P(A)P(C)\\
P(B\cap C) = \frac{1}{4} = P(B)P(C)
P(A\cap B\cap C) = \frac{1}{4} \neq P(A)P(B)P(C)
$$
由上述等式可以明显地得出事件A、B互相独立，事件A、C互相独立，事件B、C互相独立，但是事件A、B、C之间不互相独立；

**一个经典问题的思考：一对夫妻，生了两个孩子，其中一个是男孩，另一个是女孩的概率是多少？**

​	乍一看两个孩子之间的性别是互相独立的，所以另一个是女孩的概率一下就得出来应该为1/2，但其实这个问题应该作为条件概率问题来思考，这一对夫妻生两个孩子的可能结果分别是男男、男女、女男、女女，但是这里已经给出有一个孩子是男孩，所以这里的 $P(另一个是女孩|一个是男孩) = \frac{P(一个是男孩一个是女孩)}{P(一个是男孩)} = \frac{2}{4}/\frac{3}{4} = \frac{2}{3}$ ；

**另一个经典的问题（三门问题）思考：游戏《糖豆人》中有一个关卡，有三个门，其中只有一扇能打开，在你前面有一个人，你一开始想选的是最左边的门，而你前面那个人选的是最右边的门，他撞过去的时候你发现撞不开，这时你选择中间那扇门并且一次撞开的概率是多少？**

​	和上面那个问题有一些类似，看似在最右边的门打不开，在最左边和中间的门中选，选中能开的门的概率为1/2；但是在你开始选中的最左边的门是可以打开的门的概率为1/3，选中不可打开的们的概率为2/3，此时在知道最右边的门是不可打开的时候，你换选择中间的门可以打开的概率实际上是2/3；

### Lecture 4 计数

**Discrete uniform law 离散均匀法：让所有样本点发生的概率都相等，然后有 $P(A)=\frac{A的元素数目}{样本点的总数目}=\frac{|A|}{|\Omega|}$**

**Basic counting principle 基础计数原理**

**乘法计数：共有r个阶段，第 $r_i$ 个阶段有 $n_i$ 种可能的结果，所以共有 $n_1n_2\cdots n_r$ 种的可能结果；**

**排列：对于n个元素排序的数目，可以这么思考，第一个排序的有n种可能，第二个有n-1种可能，以此类推，总的排序数目应该为 $n*(n-1)*\cdots *2*1$ 种，记作为 $n!$**

对于集合 $\{1,2,\cdots n\}$ 的子集数目，我们可以理解为共n个人，其中自愿参加志愿者的可能性为，每个人都有两种情况出现，所以子集数目为 $2*2\cdots 2 = 2^n$ 个

**Combinations 组合：记$(^n_k)$ 从n个元素中选出k个元素的全部可能结果；**

一个一个的从n个元素中选出k个元素可能结果为 $n(n-1)\cdots (n-k+1)$ 种可能，这里选出的k个元素是经过排列的，而$(_k^n)$ 是不需要排序的，所以可以得到下面的式子并且得到 $(^n_k)$ 的代数式：
$$
(^n_k)k! = n(n-1)\cdots (n-k+1) \\
(^n_k) = \frac{n(n-1)\cdots (n-k+1)}{k!} = \frac{n!}{k!(n-k)!}
$$
此时有 $\sum^{n}_{k=0}(^n_k) = 2^n$

**Binomial probabilities 二项概率：对于n次重复的独立事件，其中有k次事件发生的概率；**

示例：抛n次不公平的硬币，其中 $P(H) = p$ ，抛n次硬币有k次出现正面的概率为多少？

我们这么考虑，k次正面，则n-k次都是反面，这种情况发生的概率为 $k^p(n-k)^{1-p}$，而这种情况发生的次数应该为 $(^n_k)$ 或者 $(^n_{n-k})$ ，这两种的结果应该是一样的，所以可以得到总的概率为 $(^n_k)k^p(n-k)^{1-p}$，且应该有 $\sum_{k=0}^n(^n_k)k^p(n-k)^{1-p} = 1$

**Partitions 划分：把n个不同的元素划分成k部分，第i部分的元素个数为 $m_i$ ，且有 $\sum_{i=0}^km_i = n$ ，则一共有 $\frac{n!}{m_1!m_2!\cdots m_k!}$ 种方法**

利用组合的办法理解，我们可以理解为先从n个元素中选出了$m_1$个，然后以此类推选出其他元素，可得如下：
$$
(^n_{m_1})(^{n-m_1}_{m_2})\cdots(^{m-\sum_{i=1}^{k-1}m_i}_{m_k}) = \frac{n!}{m_1!(n-m_1)!}\frac{(n-m_1)!}{m_2!(n-m_1-m_2)!}\cdots = \frac{n!}{m_1!m_2!\cdots m_k!}
$$

### Lecture 5 离散随机变量，概率质量函数，期望

**Random variables 随机变量：对实验的每个可能的结果赋值，从数学上说是一个从样本空间到实数的函数，这个函数（随机变量）可以是离散的（discrete）也可以是连续的（ continue），一个相同的样本空间可以有几个随机变量；我们通常使用符号 $X、x$ 来区分随机变量、数值，**

示例：对于一个班的学生，随机选两个测量他们的身高，分别测得为174cm、178cm；这里的174、178就是我们称之为随机变量高度的数值，也可以选取体重作为另一个随机变量，测得这两个人的体重分别为65kg、70kg；这里的65、70就是另一个随机变量体重的数值；

**Probability mass function（PMF）概率质量函数：对随机变量函数X的概率分布，**
$$
p_X(x) = P(X=x) = P(\{\omega \in \Omega  \  \ s.t. \ \ X(\omega) = x\}) \\
p_X(x) \geq 0 \  \ \ \ \sum_x{p_X(x)} = 1
$$
**Expected value of random variable 随机变量的期望值：类似为带权重的平均值，期望值 $E[x] = \sum_xxp_X(x)$**

**expectations 期望：让X成为一个样本空间的随机变量，然后使得 $Y=g(X)$ ，有 $E[Y]=\sum_yyp_Y(y)$  或者 $E[Y]=\sum_xg(x)p_X(x)$ ；通常使用后面的公式进行计算，注意：通常$E[g(X)] \neq g(E[X])$ ，只有在$g(x)$为线性的时候相等；**

期望的线性性质：如果 $\alpha, \beta$ 是常数，那么有以下性质
$$
E[\alpha] = \alpha \\
E[\alpha X] = \sum_xg(x)p_X(x) = \sum_x\alpha xp_X(x) = \alpha \sum_xxp_X(x) \ = \alpha E(X) \\
E[\alpha X + \beta] = \sum_xg(x)p_X(x) = \sum_x(\alpha x + \beta)p_X(x) = \sum_x\alpha xp_X(x) + \sum_x\beta p_X(x) = \alpha E(X) + \beta
$$
**Variance 方差 ：每个数值与期望之间距离的平方的期望值**
$$
var(X) = E[(X-E[X])^2] = \sum_x(x-E(X))^2p_X(x) = E[X^2] - (E[X])^2
$$
方差的性质有以下
$$
var(X) \geq 0 \\
var(\alpha X + \beta) = \alpha^2 var(X)
$$

$X$ 的标准偏差：$\sigma_X = \sqrt{var(X)}$

### Lecture 6 离散随机变量实例，联合概率质量函数

对于函数的期望和期望的函数通常不相等的实例：一段200km的路程，有两种等可能的方式到达目的地，一种是速度 $V$ 为1km/h，一种是200km/h的方式；$d=200, T=t(V)=200/V$
$$
E[V] = \frac{1}{2}*1 + \frac{1}{2}*200 = 100.5 \\
var(V) = \frac{1}{2}*(1-100.5)^2 + \frac{1}{2}*(200-100.5)^2 \approx 100^2 \\
\sigma_V = \sqrt{var_V} = 100
E[T] = E[t(V)] = \sum_vt(v)p_V(v) = \frac{1}{2}*200 + \frac{1}{2}*1 = 100.5 \\
E[TV] = 200 \neq E[T]E[V] = 10000 \\
E[200/V] = E[T] = 100.5 \neq 200/E[v] \approx 2
$$
**Conditional PMF and expectation 条件PMF和期望**
$$
p_{X|A}(x) = P(X=x|A) \\
E[X|A] = \sum_Xxp_{X|A}(x) \\
E[g(x)|A] = \sum_Xg(x)p_{X|A}(x)
$$
条件PMF和期望的实例：

![Probabilistic_mit7](W:\Starting from scratch\math\Probability-theory\printscreen\Probabilistic_mit7.png)

使得事件 $A = (X \geq 2)$
$$
p_{X|A}(x) = \frac{1}{3} \tag{x=2,3,4} \\
E[X|A] = 2*\frac{1}{3} + 3*\frac{1}{3} + 4*\frac{1}{3} = 3
$$

**Geometric PMF 几何PMF**

实例：记事件X为直到第一个正面朝上的独立抛硬币次数，则有以下
$$
p_X(k) = (1-p)^{k-1}p  \tag{k=1,2,3...} \\
E[X] = \sum_{k=1}^\infty kp_X(k) = \sum_{k=1}^\infty k(1-p)^{k-1}p
$$
Memoryless property：Given that X > 2, the r.v. X − 2 has same geometric PMF

<img src="W:\Starting from scratch\math\Probability-theory\printscreen\Probabilistic_mit8.png" alt="Probabilistic_mit8" style="zoom:80%;" />

**Total Expectation theorem 总期望定理**
$$
对于P(B) = P(A_1)P(B|A_1) + \cdots + P(A_n)P(B|A_n) \\
有p_X(x) = P(A_1)p_{X|A_1}(x) + \cdots + P(A_n)p_{X|A_n}(x) \\
和E[X] = P(A_1)E[X|A_1] + \cdots + P(X_n)E[X|A_n]
$$
几何实例：记事件X为直到第一个正面朝上的独立抛硬币次数，$A_1 : \{X=1\}$ ，$A_2 : \{X>1\}$
$$
E[X] = P(X=1)E[X|X=1] + P(X>1)E[X|X>1]\\ 
= p*1 + (1-p)*(E[X-1|X-1>0] + 1) \\
= p*1 + (1-p)*(E[X] + 1)   \\ \downarrow \\
E[X]= \frac{1}{p}
$$
**Joint PMFs 联合PMF**
$$
p_{X,Y}(x,y) = P(X=x  \ and  \ Y=y) \\
p_X(x) = \sum_yp_{X,Y}(x,y) \\
p_{X|Y}(x|y) = P(X=x|Y=y) = \frac{p_{X,Y}(x,y)}{p_Y(y)}
$$

### Lecture 7 连续随机变量