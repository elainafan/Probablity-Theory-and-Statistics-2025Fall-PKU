## 第一题

![](./Picture%20Assets/hw6/1.png)

(1)

因为 $X\sim \operatorname{Exp}(1)$ ，所以 $E(X)=1$ 。由马尔可夫不等式

$$
P(X\geq a)\leq \frac{E(X)}{a}=\frac{1}{a}.
$$

(2)

又有 $\operatorname{Var}(X)=1$ 。因为 $a>1$ ，所以

$$
\{X\geq a\}\subseteq \{|X-1|\geq a-1\}.
$$

由切比雪夫不等式

$$
P(X\geq a)\leq P(|X-1|\geq a-1)\leq \frac{1}{(a-1)^2}.
$$

(3)

对任意正整数 $k$ ，有

$$
E(X^k)=\int_0^{+\infty}x^ke^{-x}\,dx=\Gamma(k+1)=k!.
$$

因此由马尔可夫不等式

$$
P(X\geq a)=P(X^k\geq a^k)\leq \frac{k!}{a^k}.
$$

(4)

对任意 $0<t<1$ ，有

$$
E(e^{tX})=\int_0^{+\infty}e^{tx}e^{-x}\,dx=\frac{1}{1-t}.
$$

由 Chernoff bound

$$
P(X\geq a)\leq \frac{E(e^{tX})}{e^{ta}}=\frac{e^{-ta}}{1-t}.
$$

令

$$
g(t)=-ta-\ln(1-t).
$$

则 $g'(t)=-a+\frac{1}{1-t}$ ，最优点为 $t=1-\frac{1}{a}$ 。代入得

$$
P(X\geq a)\leq a e^{-a+1}.
$$

(5)

直接计算可得

$$
P(X\geq a)=\int_a^{+\infty}e^{-x}\,dx=e^{-a}.
$$

(6)

第三问中取最佳 $k$ 时，得到的上界为

$$
\min_{k\in \mathbb{N}}\frac{k!}{a^k}.
$$

下面说明它不弱于第四问的 Chernoff 上界。固定 $0<t<1$ ，令 $K\sim \pi(ta)$ ，并设

$$
f(k)=\frac{k!}{a^k}.
$$

则

$$
\begin{align*}
E(f(K))
&=\sum_{k=0}^{+\infty}e^{-ta}\frac{(ta)^k}{k!}\frac{k!}{a^k} \\
&=e^{-ta}\sum_{k=0}^{+\infty}t^k \\
&=\frac{e^{-ta}}{1-t}.
\end{align*}
$$

右边正是参数 $t$ 给出的 Chernoff 上界。因此

$$
\min_k f(k)\leq E(f(K))=\frac{e^{-ta}}{1-t}.
$$

对 $t$ 再取最优，得到第三问选取最佳 $k$ 的上界不大于 Chernoff bound 的最优上界。因此本题中“最佳矩方法”的上界至少同样紧，通常会更紧。

## 第二题

![](./Picture%20Assets/hw6/2.png)

(1)

对任意 $0<\epsilon<1$ ，有

$$
P(|X_n-0|\geq \epsilon)=P(X_n=1)=\frac{1}{n}\to 0.
$$

所以 $X_n$ 依概率收敛于 $0$ 。

但是事件 $\{X_n=1\}$ 相互独立，且

$$
\sum_{n=1}^{+\infty}P(X_n=1)=\sum_{n=1}^{+\infty}\frac{1}{n}=+\infty.
$$

由 Borel-Cantelli 引理， $X_n=1$ 会发生无穷多次的概率为 $1$ 。因此 $X_n$ 不几乎必然收敛于 $0$ 。

(2)

对任意 $\epsilon>0$ ，由 Hoeffding 不等式

$$
P(|Y_n-p|\geq \epsilon)\leq 2e^{-2n\epsilon^2}.
$$

于是

$$
\sum_{n=1}^{+\infty}P(|Y_n-p|\geq \epsilon)
\leq
\sum_{n=1}^{+\infty}2e^{-2n\epsilon^2}<+\infty.
$$

再次由 Borel-Cantelli 引理可知，对任意固定 $\epsilon>0$ ，事件 $|Y_n-p|\geq \epsilon$ 只会发生有限次。因此

$$
Y_n \xrightarrow{\mathrm{a.s.}} p.
$$

## 第三题

![](./Picture%20Assets/hw6/3.png)

构造程序 $C$ 如下：

1. 同时运行程序 $A$ 和程序 $B$ 。
2. 如果二者输出相同，则输出这个共同结果并停止。
3. 如果二者输出不同，则重新运行这一轮。

若输入是质数，程序 $A$ 一定输出“质数”，程序 $B$ 以 $\frac{1}{2}$ 的概率输出“质数”。因此每一轮以 $\frac{1}{2}$ 的概率停止，且停止时一定输出“质数”。

若输入是合数，程序 $B$ 一定输出“合数”，程序 $A$ 以 $\frac{1}{2}$ 的概率输出“合数”。因此每一轮仍以 $\frac{1}{2}$ 的概率停止，且停止时一定输出“合数”。

所以程序 $C$ 总能正确判断。轮数服从成功概率为 $\frac{1}{2}$ 的几何分布，期望轮数为 $2$ 。每轮调用 $A,B$ 各一次，故期望运行时间为

$$
O(T).
$$

## 第四题

![](./Picture%20Assets/hw6/4.png)

设 $\mu=E(X)=np$ 。

(1)

二项分布的矩母函数为

$$
M_X(t)=(1-p+pe^t)^n.
$$

由 $1+x\leq e^x$ ，有

$$
\begin{align*}
M_X(t)
&=(1+p(e^t-1))^n \\
&\leq \exp(np(e^t-1)) \\
&=e^{(e^t-1)E(X)}.
\end{align*}
$$

(2)

对任意 $t>0$ ，由马尔可夫不等式

$$
\begin{align*}
P(X\geq (1+\epsilon)\mu)
&=P(e^{tX}\geq e^{t(1+\epsilon)\mu}) \\
&\leq \exp((e^t-1)\mu-t(1+\epsilon)\mu).
\end{align*}
$$

取 $t=\ln(1+\epsilon)$ ，得到

$$
P(X\geq (1+\epsilon)\mu)
\leq
\left(\frac{e^\epsilon}{(1+\epsilon)^{1+\epsilon}}\right)^\mu.
$$

对下尾，令 $s>0$ ，则

$$
\begin{align*}
P(X\leq (1-\epsilon)\mu)
&=P(e^{-sX}\geq e^{-s(1-\epsilon)\mu}) \\
&\leq \exp((e^{-s}-1)\mu+s(1-\epsilon)\mu).
\end{align*}
$$

取 $s=-\ln(1-\epsilon)$ ，即 $e^{-s}=1-\epsilon$ ，可得

$$
P(X\leq (1-\epsilon)\mu)
\leq
\left(\frac{e^{-\epsilon}}{(1-\epsilon)^{1-\epsilon}}\right)^\mu.
$$

(3)

这里 $X_i\sim B(n,\frac{1}{n})$ ，所以 $E(X_i)=1$ 。令

$$
a=c\frac{\ln n}{\ln\ln n}.
$$

由上一问的上尾 Chernoff bound，在 $a>1$ 时

$$
P(X_i\geq a)\leq \left(\frac{e}{a}\right)^a.
$$

因此

$$
P(Y\geq a)
\leq
\sum_{i=1}^{n}P(X_i\geq a)
\leq
n\left(\frac{e}{a}\right)^a.
$$

当 $n$ 充分大时，

$$
a\ln a=(c+o(1))\ln n.
$$

取足够大的常数 $c=c_1$ ，例如任取 $c_1>2$ 后再令 $n$ 足够大，就有

$$
n\left(\frac{e}{a}\right)^a\leq \frac{1}{n}.
$$

于是存在常数 $c_1>0$ ，使得对充分大的 $n$ 有

$$
P\left(Y\geq c_1\frac{\ln n}{\ln\ln n}\right)\leq \frac{1}{n}.
$$

(4)

取上一问中的

$$
a=c_1\frac{\ln n}{\ln\ln n}.
$$

由于 $Y\leq n$ ，有

$$
\begin{align*}
E(Y)
&=E(Y\mathbf{1}_{Y<a})+E(Y\mathbf{1}_{Y\geq a}) \\
&\leq a+nP(Y\geq a) \\
&\leq c_1\frac{\ln n}{\ln\ln n}+1.
\end{align*}
$$

因此存在常数 $c_2>0$ ，使得

$$
E(Y)\leq c_2\frac{\ln n}{\ln\ln n}.
$$

## 第五题

![](./Picture%20Assets/hw6/5%281%29.png)
![](./Picture%20Assets/hw6/5%282%29.png)

(1)

对任意固定向量 $x$ ，题中给出的引理说明

$$
P\left(
(1-\eta)\|x\|_2^2
\leq
\left\|\frac{1}{\sqrt{k}}Ax\right\|_2^2
\leq
(1+\eta)\|x\|_2^2
\right)
\geq 1-2e^{-k\eta^2/8}.
$$

令 $\eta=\frac{\epsilon}{4}$ 。需要同时控制的向量包括 $y_i$ 以及 $y_i+y_j$ ，总数至多为 $n+n^2$ 。由 union bound，失败概率至多为

$$
2(n+n^2)e^{-k\epsilon^2/128}.
$$

取

$$
k=C\frac{\ln n}{\epsilon^2}
$$

且常数 $C$ 足够大，即可使失败概率不超过 $\frac{1}{2}$ 。因此题中两个事件以至少 $\frac{1}{2}$ 的概率同时成立。

(2)

记

$$
F(x)=\frac{1}{\sqrt{k}}Ax.
$$

在上一问的好事件上，对 $i\neq j$ ，由极化恒等式

$$
\langle F(y_i),F(y_j)\rangle
=\frac{\|F(y_i+y_j)\|_2^2-\|F(y_i)\|_2^2-\|F(y_j)\|_2^2}{2}.
$$

因此

$$
\begin{align*}
&\left|\langle F(y_i),F(y_j)\rangle-\langle y_i,y_j\rangle\right| \\
&\leq
\frac{1}{2}\left(
\frac{\epsilon}{4}\|y_i+y_j\|_2^2
+\frac{\epsilon}{4}\|y_i\|_2^2
+\frac{\epsilon}{4}\|y_j\|_2^2
\right) \\
&\leq \frac{1}{2}\cdot \frac{\epsilon}{4}\cdot (4+1+1) \\
&=\frac{3\epsilon}{4}<\epsilon.
\end{align*}
$$

当 $i=j$ 时，结论由第一类事件直接给出。因此以至少 $\frac{1}{2}$ 的概率，对任意 $i,j$ 均有

$$
\left|\left\langle \frac{1}{\sqrt{k}}Ay_i,\frac{1}{\sqrt{k}}Ay_j\right\rangle-\langle y_i,y_j\rangle\right|\leq \epsilon.
$$

(3)

若 $x_i=0$ 或 $x_j=0$ ，结论显然成立。否则令

$$
y_i=\frac{x_i}{\|x_i\|},\qquad y_j=\frac{x_j}{\|x_j\|}.
$$

对所有非零的 $x_i$ 归一化后使用上一问，得到以至少 $\frac{1}{2}$ 的概率，对任意 $i,j$ 有

$$
\left|
\left\langle F(y_i),F(y_j)\right\rangle-\langle y_i,y_j\rangle
\right|\leq \epsilon.
$$

两边乘以 $\|x_i\|\|x_j\|$ ，即得

$$
\left|
\left\langle \frac{1}{\sqrt{k}}Ax_i,\frac{1}{\sqrt{k}}Ax_j\right\rangle-\langle x_i,x_j\rangle
\right|
\leq
\epsilon\|x_i\|\|x_j\|.
$$

(4)

取 $x_i=e_i$ 为 $\mathbb{R}^n$ 中的标准基向量，并取 $\epsilon=0.1$ 。由上一问，存在 $k=O(\ln n)$ 和矩阵 $M\in \mathbb{R}^{k\times n}$ ，使得对所有 $i,j$ 有

$$
\left|
\left\langle \frac{1}{\sqrt{k}}Me_i,\frac{1}{\sqrt{k}}Me_j\right\rangle-\langle e_i,e_j\rangle
\right|\leq 0.1.
$$

令

$$
B=\frac{1}{k}M^\top M.
$$

则 $\operatorname{rank}(B)\leq k\leq c\ln n$ ，并且

$$
B_{ij}=\left\langle \frac{1}{\sqrt{k}}Me_i,\frac{1}{\sqrt{k}}Me_j\right\rangle.
$$

由于 $I_{ij}=\langle e_i,e_j\rangle$ ，所以

$$
|I_{ij}-B_{ij}|\leq 0.1.
$$

这就证明了所需矩阵存在。

## 第六题

![](./Picture%20Assets/hw6/6%281%29.png)
![](./Picture%20Assets/hw6/6%282%29.png)

(1)

因为 $Y_i=|X_i|$ ，所以当 $y\geq 0$ 时

$$
f_{Y_i}(y)=f_X(y)+f_X(-y)=\frac{2}{\pi(1+y^2)}.
$$

当 $y<0$ 时， $f_{Y_i}(y)=0$ 。因此

$$
f_{Y_i}(y)=
\begin{cases}
\frac{2}{\pi(1+y^2)}, & y\geq 0, \\
0, & y<0.
\end{cases}
$$

(2)

先给出较粗但足够的上界。令

$$
Z_i=Y_i\mathbf{1}_{Y_i\leq n^2}.
$$

则

$$
E(Z_i)
=\int_0^{n^2}\frac{2y}{\pi(1+y^2)}\,dy
=\frac{1}{\pi}\ln(1+n^4)
\leq C\ln n.
$$

于是

$$
E\left(\sum_{i=1}^{n}Z_i\right)\leq Cn\ln n.
$$

由马尔可夫不等式，取常数 $C_1$ 足够大，有

$$
P\left(\sum_{i=1}^{n}Z_i>\frac{C_1}{2}n^2\right)\leq \frac{1}{6}
$$

对充分大的 $n$ 成立。另一方面

$$
P\left(\max_iY_i>n^2\right)
\leq nP(Y_1>n^2)
\leq \frac{C}{n}
\leq \frac{1}{6}
$$

对充分大的 $n$ 成立。因此

$$
P\left(\sum_{i=1}^{n}Y_i\leq C_1n^2\right)\geq \frac{2}{3}.
$$

调整常数即可覆盖有限多个较小的 $n$ 。

(3)

令

$$
I_i=\mathbf{1}_{Y_i\geq 1}.
$$

由于柯西分布关于 $0$ 对称，且

$$
P(Y_i\geq 1)=\frac{1}{2},
$$

所以

$$
\sum_{i=1}^{n}I_i\sim B\left(n,\frac{1}{2}\right).
$$

并且

$$
\sum_{i=1}^{n}Y_i\geq \sum_{i=1}^{n}I_i.
$$

由 Chernoff bound，存在常数 $c_2>0$ ，例如取 $c_2=\frac{1}{4}$ 并让 $n$ 充分大，有

$$
P\left(\sum_{i=1}^{n}I_i\geq c_2n\right)\geq \frac{2}{3}.
$$

因此

$$
P\left(\sum_{i=1}^{n}Y_i\geq c_2n\right)\geq \frac{2}{3}.
$$

(4)

正确的量级是

$$
f(n)=n\ln n.
$$

先证上界。令

$$
Z_i=Y_i\mathbf{1}_{Y_i\leq n^2}.
$$

由第二问的计算

$$
E(Z_i)\leq C\ln n.
$$

故取常数 $c_3$ 足够大，有

$$
P\left(\sum_{i=1}^{n}Z_i>c_3n\ln n\right)\leq \frac{1}{6}.
$$

同时

$$
P\left(\max_iY_i>n^2\right)\leq \frac{C}{n}\leq \frac{1}{6}
$$

对充分大的 $n$ 成立。所以

$$
P\left(\sum_{i=1}^{n}Y_i\leq c_3n\ln n\right)\geq \frac{2}{3}.
$$

再证下界。令

$$
W_i=Y_i\mathbf{1}_{Y_i\leq n}.
$$

则

$$
E(W_i)=\frac{1}{\pi}\ln(1+n^2)\geq c\ln n
$$

且

$$
E(W_i^2)=\int_0^n \frac{2y^2}{\pi(1+y^2)}\,dy
=\frac{2}{\pi}(n-\arctan n)
\leq Cn.
$$

因此

$$
\operatorname{Var}\left(\sum_{i=1}^{n}W_i\right)\leq Cn^2.
$$

而

$$
E\left(\sum_{i=1}^{n}W_i\right)\geq cn\ln n.
$$

由切比雪夫不等式

$$
P\left(
\sum_{i=1}^{n}W_i
\leq
\frac{1}{2}E\left(\sum_{i=1}^{n}W_i\right)
\right)
\leq
\frac{C}{\ln^2 n}.
$$

对充分大的 $n$ ，右侧不超过 $\frac{1}{3}$ 。又 $\sum_iY_i\geq \sum_iW_i$ ，所以存在常数 $c_4>0$ ，使得

$$
P\left(\sum_{i=1}^{n}Y_i\geq c_4n\ln n\right)\geq \frac{2}{3}.
$$
