## 第一题

![](./Picture%20Assets/hw5/1.png)

对任意 $y \geq 0$ ，有

$$
\begin{align*}
P(Y>y)
&=P(X_1>y,X_2>y,\ldots,X_n>y) \\
&=\prod_{i=1}^{n}P(X_i>y) \\
&=\prod_{i=1}^{n}e^{-\lambda_i y} \\
&=e^{-(\sum_{i=1}^{n}\lambda_i)y}.
\end{align*}
$$

因此

$$
Y \sim \operatorname{Exp}\left(\sum_{i=1}^{n}\lambda_i\right).
$$

也即其分布函数为

$$
F_Y(y)=
\begin{cases}
0, & y<0, \\
1-e^{-(\sum_{i=1}^{n}\lambda_i)y}, & y\geq 0.
\end{cases}
$$

## 第二题

![](./Picture%20Assets/hw5/2.png)

(1)

由于 $U=X+Y$ ，由卷积公式

$$
f_U(u)=\int_{-\infty}^{+\infty}f_X(x)f_Y(u-x)\,dx.
$$

被积函数非零当且仅当 $0<x<1$ 且 $0<u-x<1$ ，于是

$$
f_U(u)=
\begin{cases}
u, & 0<u<1, \\
2-u, & 1\leq u<2, \\
0, & \text{其他}.
\end{cases}
$$

同理 $V=X-Y$ ，有

$$
f_V(v)=\int_{-\infty}^{+\infty}f_X(y+v)f_Y(y)\,dy,
$$

被积函数非零当且仅当 $0<y<1$ 且 $0<y+v<1$ ，故

$$
f_V(v)=
\begin{cases}
1-|v|, & -1<v<1, \\
0, & \text{其他}.
\end{cases}
$$

(2)

由

$$
u=x+y,\qquad v=x-y
$$

可得

$$
x=\frac{u+v}{2},\qquad y=\frac{u-v}{2}.
$$

Jacobian 为

$$
\left|\frac{\partial(x,y)}{\partial(u,v)}\right|
=
\left|
\begin{matrix}
\frac{1}{2} & \frac{1}{2} \\
\frac{1}{2} & -\frac{1}{2}
\end{matrix}
\right|
=\frac{1}{2}.
$$

又因为 $0<x<1$ 且 $0<y<1$ ，所以

$$
0<u+v<2,\qquad 0<u-v<2.
$$

于是

$$
f_{U,V}(u,v)=
\begin{cases}
\frac{1}{2}, & 0<u+v<2,\ 0<u-v<2, \\
0, & \text{其他}.
\end{cases}
$$

(3)

由联合密度积分可得

$$
f_U(u)=\int_{\max\{-u,u-2\}}^{\min\{u,2-u\}}\frac{1}{2}\,dv,
$$

从而仍有

$$
f_U(u)=
\begin{cases}
u, & 0<u<1, \\
2-u, & 1\leq u<2, \\
0, & \text{其他}.
\end{cases}
$$

类似地

$$
f_V(v)=
\begin{cases}
1-|v|, & -1<v<1, \\
0, & \text{其他}.
\end{cases}
$$

由于 $(U,V)$ 的支撑集不是两个边际支撑集的笛卡尔积，并且一般有

$$
f_{U,V}(u,v)\neq f_U(u)f_V(v),
$$

所以 $U$ 与 $V$ 不相互独立。

(4)

当 $0<u<1$ 时， $v$ 的可取范围为 $-u<v<u$ ，且 $f_U(u)=u$ ，因此

$$
f_{V|U=u}(v)=
\begin{cases}
\frac{1}{2u}, & -u<v<u, \\
0, & \text{其他}.
\end{cases}
$$

当 $1\leq u<2$ 时， $v$ 的可取范围为 $u-2<v<2-u$ ，且 $f_U(u)=2-u$ ，因此

$$
f_{V|U=u}(v)=
\begin{cases}
\frac{1}{2(2-u)}, & u-2<v<2-u, \\
0, & \text{其他}.
\end{cases}
$$

(5)

有

$$
\begin{align*}
\operatorname{Cov}(U,V)
&=\operatorname{Cov}(X+Y,X-Y) \\
&=\operatorname{Var}(X)-\operatorname{Var}(Y) \\
&=0.
\end{align*}
$$

又 $U$ 与 $V$ 的方差均非零，因此

$$
\operatorname{Corr}(U,V)=0.
$$

所以 $U$ 与 $V$ 不相关，但由上一问知它们不相互独立。

## 第三题

![](./Picture%20Assets/hw5/3%281%29.png)
![](./Picture%20Assets/hw5/3%282%29.png)

(1)

将 $A$ 的行向量记为 $a_1^\top,a_2^\top,\ldots,a_m^\top$ 。由于 $\operatorname{rank}(A)=m$ ，这些行向量线性无关。对它们做 Gram-Schmidt 正交化，得到标准正交行向量 $q_1^\top,q_2^\top,\ldots,q_m^\top$ 。

每个 $a_i^\top$ 都可以唯一表示为 $q_1^\top,\ldots,q_i^\top$ 的线性组合。令 $Q$ 的第 $i$ 行为 $q_i^\top$ ，令 $R$ 为对应的系数矩阵，则

$$
A=RQ.
$$

Gram-Schmidt 中每一步得到的对角系数均非零，因此 $R$ 为可逆矩阵。并且 $Q$ 的每一行均为单位向量，不同行相互正交。

(2)

因为 $q_1,\ldots,q_m$ 是 $\mathbb{R}^n$ 中的标准正交向量组，可以将其扩充为 $\mathbb{R}^n$ 的一组标准正交基

$$
q_1,q_2,\ldots,q_m,q_{m+1},\ldots,q_n.
$$

令 $\widetilde{Q}$ 的第 $i$ 行为 $q_i^\top$ ，则 $\widetilde{Q}$ 是正交矩阵，且其前 $m$ 行与 $Q$ 相同。

(3)

若 $Z\sim N(0,I_n)$ ，则其密度函数只依赖于 $\|z\|_2^2$ 。由于 $\widetilde{Q}$ 是正交矩阵，有

$$
\|\widetilde{Q}z\|_2=\|z\|_2.
$$

因此

$$
\widetilde{Q}Z\sim N(0,I_n).
$$

而 $QZ$ 是 $\widetilde{Q}Z$ 的前 $m$ 个坐标，所以

$$
QZ\sim N(0,I_m).
$$

(4)

由 $A=RQ$ ，有

$$
AZ+b=RQZ+b.
$$

上一问说明 $QZ\sim N(0,I_m)$ ，所以

$$
AZ+b\sim N(b,RR^\top).
$$

又 $QQ^\top=I_m$ ，因此

$$
AA^\top=RQQ^\top R^\top=RR^\top.
$$

故

$$
AZ+b\sim N(b,AA^\top).
$$

(5)

设 $X\sim N(\mu,B)$ ，取 $Z\sim N(0,I_n)$ ，可写成

$$
X=B^{1/2}Z+\mu.
$$

于是

$$
AX+b=A\mu+b+AB^{1/2}Z.
$$

先说明 $AB^{1/2}$ 行满秩。若 $c^\top AB^{1/2}=0$ ，由于 $B^{1/2}$ 可逆，得到 $c^\top A=0$ 。又 $A$ 行满秩，所以 $c=0$ 。因此 $AB^{1/2}$ 行满秩。

由上一问可得

$$
AB^{1/2}Z\sim N(0,AB^{1/2}(AB^{1/2})^\top)=N(0,ABA^\top).
$$

从而

$$
AX+b\sim N(A\mu+b,ABA^\top).
$$

## 第四题

![](./Picture%20Assets/hw5/4.png)

(1)

由于 $G_1,\ldots,G_n$ 独立同分布且均服从 $N(0,1)$ ，任意线性组合仍为高斯随机变量。显然

$$
E(X)=E(Y)=0.
$$

又因为 $\|a\|=\|b\|=1$ ，有

$$
\operatorname{Var}(X)=1,\qquad \operatorname{Var}(Y)=1.
$$

同时

$$
\operatorname{Cov}(X,Y)=E(XY)=\sum_{i=1}^{n}a_i b_i=\rho.
$$

因此

$$
(X,Y)\sim N\left(
\begin{bmatrix}
0 \\
0
\end{bmatrix},
\begin{bmatrix}
1 & \rho \\
\rho & 1
\end{bmatrix}
\right).
$$

(2)

记 $s=\sqrt{1-\rho^2}$ 。由题设

$$
x=r(s\cos\theta+\rho\sin\theta),\qquad y=r\sin\theta.
$$

于是

$$
\begin{align*}
x^2+y^2-2\rho xy
&=r^2(s\cos\theta+\rho\sin\theta)^2+r^2\sin^2\theta \\
&\quad -2\rho r^2(s\cos\theta+\rho\sin\theta)\sin\theta \\
&=r^2\left(s^2\cos^2\theta+(1-\rho^2)\sin^2\theta\right) \\
&=r^2(1-\rho^2).
\end{align*}
$$

(3)

二维正态密度为

$$
f_{X,Y}(x,y)=\frac{1}{2\pi\sqrt{1-\rho^2}}
\exp\left(-\frac{x^2-2\rho xy+y^2}{2(1-\rho^2)}\right).
$$

由上一问可知指数部分为 $e^{-r^2/2}$ 。再计算变换的 Jacobian：

$$
\left|\frac{\partial(x,y)}{\partial(r,\theta)}\right|
=r\sqrt{1-\rho^2}.
$$

因此

$$
f_{R,\Theta}(r,\theta)=
\begin{cases}
\frac{r}{2\pi}e^{-r^2/2}, & r\geq 0,\ 0\leq \theta\leq 2\pi, \\
0, & \text{其他}.
\end{cases}
$$

边际密度分别为

$$
f_R(r)=
\begin{cases}
re^{-r^2/2}, & r\geq 0, \\
0, & r<0,
\end{cases}
$$

以及

$$
f_\Theta(\theta)=
\begin{cases}
\frac{1}{2\pi}, & 0\leq \theta\leq 2\pi, \\
0, & \text{其他}.
\end{cases}
$$

并且

$$
f_{R,\Theta}(r,\theta)=f_R(r)f_\Theta(\theta),
$$

所以 $R$ 与 $\Theta$ 相互独立。

(4)

令 $\varphi=\arccos\rho$ ，则

$$
X=R\sin(\varphi+\Theta),\qquad Y=R\sin\Theta.
$$

由于 $R\geq 0$ ，且 $\Theta$ 在 $[0,2\pi]$ 上均匀分布，事件 $X\geq 0,Y\geq 0$ 等价于

$$
\sin\Theta\geq 0,\qquad \sin(\varphi+\Theta)\geq 0.
$$

在 $[0,2\pi]$ 中满足条件的 $\Theta$ 区间长度为 $\pi-\varphi$ 。故

$$
P(X\geq 0,Y\geq 0)=\frac{\pi-\arccos\rho}{2\pi}
=\frac{1}{4}+\frac{\arcsin\rho}{2\pi}.
$$

(5)

若 $a,b$ 均非零，令

$$
\rho=\frac{a^\top b}{\|a\|\|b\|}.
$$

由于正数倍缩放不改变符号，仍有

$$
P(X\geq 0,Y\geq 0)=\frac{1}{4}+\frac{\arcsin\rho}{2\pi}.
$$

该公式也覆盖 $\rho=1$ 和 $\rho=-1$ 的退化情形，分别得到 $\frac{1}{2}$ 与 $0$ 。

若 $a=0,b\neq 0$ 或 $a\neq 0,b=0$ ，则其中一个随机变量恒为 $0$ ，另一个为中心正态变量，因此概率为 $\frac{1}{2}$ 。若 $a=b=0$ ，则概率为 $1$ 。

## 第五题

![](./Picture%20Assets/hw5/5.png)

(1)

由于 $X_1,\ldots,X_n$ 独立同分布且均服从标准正态分布，

$$
Y=\sum_{i=1}^{n}X_i^2\sim \chi_n^2.
$$

(2)

对任意 $t<\frac{1}{2}$ ，卡方分布的矩母函数给出

$$
E(e^{tY})=(1-2t)^{-n/2}.
$$

因此当 $t<\frac{1}{4}$ 时

$$
E(e^{t(Y-n)})=e^{-tn}(1-2t)^{-n/2}.
$$

只需证明

$$
-t-\frac{1}{2}\ln(1-2t)\leq 2t^2.
$$

令

$$
h(t)=2t^2+t+\frac{1}{2}\ln(1-2t).
$$

则

$$
h'(t)=\frac{2t(1-4t)}{1-2t}.
$$

当 $t<\frac{1}{4}$ 时， $h(t)$ 在 $t=0$ 处取得最小值，且 $h(0)=0$ 。因此 $h(t)\geq 0$ ，从而

$$
E(e^{t(Y-n)})\leq e^{2t^2n}.
$$

(3)

对任意 $t>0$ ，由马尔可夫不等式和上一问

$$
\begin{align*}
P(Y\geq (1+\Delta)n)
&=P(e^{t(Y-n)}\geq e^{t\Delta n}) \\
&\leq e^{-t\Delta n}E(e^{t(Y-n)}) \\
&\leq e^{(2t^2-t\Delta)n}.
\end{align*}
$$

取 $t=\frac{\Delta}{4}$ 。由于 $0\leq \Delta<1$ ，有 $t<\frac{1}{4}$ ，故

$$
P(Y\geq (1+\Delta)n)\leq e^{-n\Delta^2/8}.
$$

(4)

对任意 $t>0$ ，仍由上一问对 $-t$ 使用结论，有

$$
\begin{align*}
P(Y\leq (1-\Delta)n)
&=P(e^{-t(Y-n)}\geq e^{t\Delta n}) \\
&\leq e^{-t\Delta n}E(e^{-t(Y-n)}) \\
&\leq e^{(2t^2-t\Delta)n}.
\end{align*}
$$

同样取 $t=\frac{\Delta}{4}$ ，得到

$$
P(Y\leq (1-\Delta)n)\leq e^{-n\Delta^2/8}.
$$

## 第六题

![](./Picture%20Assets/hw5/6.png)

(1)

有

$$
\operatorname{trace}(A^3)=\sum_{i,j,k}A_{ij}A_{jk}A_{ki}.
$$

由于各 $A_{ij}$ 独立且均值为 $0$ ，上式中每一项的期望均为 $0$ 。因此

$$
E(\operatorname{trace}(A^3))=0.
$$

再看

$$
\operatorname{trace}(A^4)=\sum_{i,j,k,l}A_{ij}A_{jk}A_{kl}A_{li}.
$$

非零贡献来自两类情况。

第一类是 $i=j=k=l$ ，此时贡献为

$$
E(A_{ii}^4)=3,
$$

共有 $n$ 项。

第二类是 $i=k,j=l$ 且 $i\neq j$ ，此时贡献为

$$
E(A_{ij}^2A_{ji}^2)=1,
$$

共有 $n(n-1)$ 项。

所以

$$
E(\operatorname{trace}(A^4))=3n+n(n-1)=n^2+2n.
$$

(2)

由于 $B$ 为对称矩阵，

$$
\operatorname{trace}(B^2)=\sum_{i,j}B_{ij}^2.
$$

每个 $B_{ij}$ 的二阶矩均为 $1$ ，因此

$$
E(\operatorname{trace}(B^2))=n^2.
$$

对四阶矩，写成

$$
\operatorname{trace}(B^4)=\sum_{i,j,k,l}B_{ij}B_{jk}B_{kl}B_{li}.
$$

更方便的做法是利用 $B$ 的对称性：

$$
\operatorname{trace}(B^4)=\operatorname{trace}((B^2)^2)=\sum_{i,j}(B^2_{ij})^2.
$$

当 $i=j$ 时，

$$
B^2_{ii}=\sum_{k=1}^{n}B_{ik}^2.
$$

于是

$$
\begin{align*}
E((B^2_{ii})^2)
&=\sum_{k=1}^{n}E(B_{ik}^4)+2\sum_{k<l}E(B_{ik}^2B_{il}^2) \\
&=3n+n(n-1) \\
&=n^2+2n.
\end{align*}
$$

当 $i\neq j$ 时，

$$
B^2_{ij}=\sum_{k=1}^{n}B_{ik}B_{kj}.
$$

不同 $k$ 之间的交叉项期望为 $0$ ，而每个平方项期望为 $1$ ，因此

$$
E((B^2_{ij})^2)=n.
$$

综上

$$
\begin{align*}
E(\operatorname{trace}(B^4))
&=\sum_{i=1}^{n}E((B^2_{ii})^2)+\sum_{i\neq j}E((B^2_{ij})^2) \\
&=n(n^2+2n)+n(n-1)n \\
&=2n^3+n^2.
\end{align*}
$$

这个公式在 $n=1$ 时也成立，因为此时就是 $E(B_{11}^4)=3$ 。

(3)

由于 $B$ 为实对称矩阵，其特征值为实数，且

$$
\operatorname{trace}(B^4)=\sum_{i=1}^{n}\lambda_i^4.
$$

于是

$$
\max_{1\leq i\leq n}|\lambda_i|^4\leq \sum_{i=1}^{n}\lambda_i^4=\operatorname{trace}(B^4).
$$

由马尔可夫不等式

$$
\begin{align*}
P\left(\max_{1\leq i\leq n}|\lambda_i|>12306n^{3/4}\right)
&\leq
\frac{E(\operatorname{trace}(B^4))}{12306^4 n^3} \\
&=
\frac{2n^3+n^2}{12306^4n^3} \\
&\leq \frac{3}{12306^4}<0.1.
\end{align*}
$$

因此

$$
P\left(\max_{1\leq i\leq n}|\lambda_i|\leq 12306n^{3/4}\right)\geq 0.9.
$$
