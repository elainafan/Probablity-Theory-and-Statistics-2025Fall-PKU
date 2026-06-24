## 第一题

![](./Picture%20Assets/hw7/1.png)

设

$$
X_{(1)}=\min\{X_1,X_2,\ldots,X_n\}.
$$

似然函数为

$$
L(\theta)=\prod_{i=1}^{n}\frac{\theta}{X_i^2}\mathbf{1}_{\theta\leq X_i}
=
\theta^n\prod_{i=1}^{n}\frac{1}{X_i^2}\mathbf{1}_{\theta\leq X_{(1)}}.
$$

在可行范围 $0<\theta\leq X_{(1)}$ 内， $L(\theta)$ 关于 $\theta$ 单调递增，因此最大似然估计量为

$$
\hat{\theta}=X_{(1)}.
$$

下面计算其分布。对 $t\geq \theta$ ，

$$
P(X_{(1)}\geq t)
=P(X_1\geq t,\ldots,X_n\geq t)
=\left(\frac{\theta}{t}\right)^n.
$$

于是 $X_{(1)}$ 的密度为

$$
f_{X_{(1)}}(t)=\frac{n\theta^n}{t^{n+1}},\qquad t\geq \theta.
$$

因此

$$
E(\hat{\theta})
=\int_{\theta}^{+\infty}t\frac{n\theta^n}{t^{n+1}}\,dt
=\frac{n}{n-1}\theta.
$$

所以 $\hat{\theta}$ 不是无偏估计量，其偏差为

$$
\operatorname{Bias}(\hat{\theta})=\frac{\theta}{n-1}.
$$

但偏差趋于 $0$ ，故它是渐进无偏估计量。

又

$$
E(\hat{\theta}^2)
=\int_{\theta}^{+\infty}t^2\frac{n\theta^n}{t^{n+1}}\,dt
=\frac{n}{n-2}\theta^2.
$$

均方误差为

$$
\begin{align*}
\operatorname{MSE}(\hat{\theta})
&=E((\hat{\theta}-\theta)^2) \\
&=E(\hat{\theta}^2)-2\theta E(\hat{\theta})+\theta^2 \\
&=\frac{2\theta^2}{(n-1)(n-2)}.
\end{align*}
$$

由于对任意 $\epsilon>0$ ，

$$
P(\hat{\theta}>\theta+\epsilon)
=\left(\frac{\theta}{\theta+\epsilon}\right)^n\to 0,
$$

且 $\hat{\theta}\geq \theta$ 恒成立，所以 $\hat{\theta}$ 是一致估计量。

最后构造置信区间。令

$$
T=\frac{X_{(1)}}{\theta}.
$$

则对 $t\geq 1$ ，有 $P(T\leq t)=1-t^{-n}$ 。取 $t=\alpha^{-1/n}$ ，得到

$$
P\left(T\leq \alpha^{-1/n}\right)=1-\alpha.
$$

等价于

$$
P\left(\alpha^{1/n}X_{(1)}\leq \theta\leq X_{(1)}\right)=1-\alpha.
$$

所以置信水平为 $1-\alpha$ 的置信区间为

$$
\left[\alpha^{1/n}X_{(1)},\,X_{(1)}\right].
$$

## 第二题

![](./Picture%20Assets/hw7/2.png)

记

$$
S=\sum_{i=1}^{n}X_i.
$$

则

$$
S\sim \Gamma(n,\lambda),
$$

这里采用 rate 参数化。由于 $\bar{X}=S/n$ ，有

$$
\hat{\lambda}_0=\frac{1}{\bar{X}}=\frac{n}{S}.
$$

(1)

对 $S\sim \Gamma(n,\lambda)$ ，有

$$
E\left(\frac{1}{S}\right)=\frac{\lambda}{n-1}.
$$

因此

$$
E(\hat{\lambda}_0)=nE\left(\frac{1}{S}\right)=\frac{n}{n-1}\lambda.
$$

所以 $\hat{\lambda}_0$ 不是无偏估计量，偏差为

$$
\operatorname{Bias}(\hat{\lambda}_0)=\frac{\lambda}{n-1}.
$$

偏差随 $n\to\infty$ 收敛到 $0$ ，所以 $\hat{\lambda}_0$ 是渐进无偏估计量。

(2)

由上一问可知

$$
\hat{\lambda}_1=\frac{n-1}{n}\hat{\lambda}_0
=\frac{n-1}{S}
$$

是 $\lambda$ 的无偏估计量。

(3)

还需要

$$
E\left(\frac{1}{S^2}\right)=\frac{\lambda^2}{(n-1)(n-2)}.
$$

于是

$$
E(\hat{\lambda}_1^2)
=(n-1)^2E\left(\frac{1}{S^2}\right)
=\frac{(n-1)\lambda^2}{n-2}.
$$

因为 $\hat{\lambda}_1$ 无偏，所以

$$
\operatorname{MSE}(\hat{\lambda}_1)
=\operatorname{Var}(\hat{\lambda}_1)
=\frac{\lambda^2}{n-2}.
$$

该均方误差趋于 $0$ ，故 $\hat{\lambda}_1$ 是一致估计量。

(4)

因为 $2\lambda X_i\sim \chi_2^2$ ，且样本相互独立，所以

$$
2\lambda S\sim \chi_{2n}^2.
$$

令 $F^{-1}$ 表示 $\chi_{2n}^2$ 分布函数的逆函数。取

$$
q_L=F^{-1}\left(\frac{\alpha}{2}\right),\qquad
q_R=F^{-1}\left(1-\frac{\alpha}{2}\right).
$$

则

$$
P(q_L\leq 2\lambda S\leq q_R)=1-\alpha.
$$

因此

$$
P\left(
\frac{q_L}{2S}\leq \lambda\leq \frac{q_R}{2S}
\right)=1-\alpha.
$$

也即

$$
\hat{\lambda}_L=\frac{F^{-1}(\alpha/2)}{2n\bar{X}},
\qquad
\hat{\lambda}_R=\frac{F^{-1}(1-\alpha/2)}{2n\bar{X}}.
$$

## 第三题

![](./Picture%20Assets/hw7/3%281%29.png)
![](./Picture%20Assets/hw7/3%282%29.png)

(1)

分布函数为

$$
F_X(x)=
\begin{cases}
0, & x\leq 0, \\
x^{\theta+1}, & 0<x<1, \\
1, & x\geq 1.
\end{cases}
$$

(2)

总体期望为

$$
E(X)=\int_0^1 x(\theta+1)x^\theta\,dx
=\frac{\theta+1}{\theta+2}.
$$

设 $\mu=E(X)$ ，则

$$
\mu=\frac{\theta+1}{\theta+2}.
$$

解得

$$
\theta=\frac{2\mu-1}{1-\mu}.
$$

将 $\mu$ 替换为样本均值 $\bar{X}$ ，得到矩估计量

$$
\hat{\theta}_1=\frac{2\bar{X}-1}{1-\bar{X}}.
$$

(3)

似然函数为

$$
L(\theta)=\prod_{i=1}^{n}(\theta+1)X_i^\theta.
$$

对数似然为

$$
\ell(\theta)=n\ln(\theta+1)+\theta\sum_{i=1}^{n}\ln X_i.
$$

令导数为 $0$ ，得到

$$
\frac{n}{\theta+1}+\sum_{i=1}^{n}\ln X_i=0.
$$

因此最大似然估计量为

$$
\hat{\theta}_2=-\frac{n}{\sum_{i=1}^{n}\ln X_i}-1.
$$

注意到

$$
P(-\ln X\leq y)=P(X\geq e^{-y})=1-e^{-(\theta+1)y},
$$

所以

$$
-\ln X_i\sim \operatorname{Exp}(\theta+1).
$$

令

$$
S=-\sum_{i=1}^{n}\ln X_i.
$$

则 $S\sim \Gamma(n,\theta+1)$ ，且

$$
\hat{\theta}_2=\frac{n}{S}-1.
$$

于是

$$
E(\hat{\theta}_2)
=\frac{n(\theta+1)}{n-1}-1
=\frac{n\theta+1}{n-1}.
$$

所以 $\hat{\theta}_2$ 不是无偏估计量，其偏差为

$$
\operatorname{Bias}(\hat{\theta}_2)=\frac{\theta+1}{n-1}.
$$

偏差趋于 $0$ ，故它是渐进无偏估计量。

(4)

由 Gamma 分布的负矩公式

$$
E\left(\frac{1}{S^2}\right)=\frac{(\theta+1)^2}{(n-1)(n-2)}.
$$

因此

$$
\begin{align*}
\operatorname{MSE}(\hat{\theta}_2)
&=E\left(\frac{n}{S}-(\theta+1)\right)^2 \\
&=
\frac{n^2(\theta+1)^2}{(n-1)(n-2)}
-\frac{2n(\theta+1)^2}{n-1}
+(\theta+1)^2 \\
&=
\frac{(n+2)(\theta+1)^2}{(n-1)(n-2)}.
\end{align*}
$$

该均方误差趋于 $0$ ，所以 $\hat{\theta}_2$ 是一致估计量。

## 第四题

![](./Picture%20Assets/hw7/4.png)

(1)

泊松分布的似然函数关于 $\lambda$ 的最大似然估计为

$$
\hat{\lambda}=\bar{X}.
$$

由于 $p=e^{-\lambda}$ 是 $\lambda$ 的函数，由最大似然估计的不变性，

$$
\hat{p}_1=e^{-\bar{X}}
$$

是 $p=e^{-\lambda}$ 的最大似然估计。

对任意实数 $t$ ，泊松分布有

$$
E(e^{tX})=\exp(\lambda(e^t-1)).
$$

于是

$$
E(\hat{p}_1)
=E(e^{-\bar{X}})
=\prod_{i=1}^{n}E(e^{-X_i/n})
=\exp(n\lambda(e^{-1/n}-1)).
$$

它一般不等于 $e^{-\lambda}$ ，所以 $\hat{p}_1$ 不是无偏估计量。但

$$
n\lambda(e^{-1/n}-1)\to -\lambda,
$$

故

$$
E(\hat{p}_1)\to e^{-\lambda}.
$$

因此 $\hat{p}_1$ 是渐进无偏估计量。

由大数定律 $\bar{X}\xrightarrow{P}\lambda$ ，连续映射定理给出

$$
\hat{p}_1=e^{-\bar{X}}\xrightarrow{P}e^{-\lambda}=p,
$$

所以 $\hat{p}_1$ 是一致估计量。

最后计算均方误差：

$$
\begin{align*}
\operatorname{MSE}(\hat{p}_1)
&=E\left((e^{-\bar{X}}-e^{-\lambda})^2\right) \\
&=E(e^{-2\bar{X}})-2e^{-\lambda}E(e^{-\bar{X}})+e^{-2\lambda} \\
&=\exp(n\lambda(e^{-2/n}-1))
-2e^{-\lambda}\exp(n\lambda(e^{-1/n}-1))
+e^{-2\lambda}.
\end{align*}
$$

(2)

令

$$
I_i=\mathbf{1}_{X_i=0}.
$$

则 $I_i\sim B(1,p)$ ，且

$$
\hat{p}_2=\frac{1}{n}\sum_{i=1}^{n}I_i.
$$

因此

$$
E(\hat{p}_2)=p.
$$

所以 $\hat{p}_2$ 是无偏估计量，也自然是渐进无偏估计量。

同时

$$
\operatorname{MSE}(\hat{p}_2)
=\operatorname{Var}(\hat{p}_2)
=\frac{p(1-p)}{n}
=\frac{e^{-\lambda}(1-e^{-\lambda})}{n}.
$$

均方误差趋于 $0$ ，故 $\hat{p}_2$ 是一致估计量。

## 第五题

![](./Picture%20Assets/hw7/5.png)

(1)

记第 $\ell$ 轮开始时的候选集合为 $S_{\ell-1}$ ，其中最优游戏机为

$$
i^\star\in \arg\max_{i\in S_{\ell-1}}p_i.
$$

第 $\ell$ 轮每台候选游戏机采样

$$
N_\ell=C\frac{\ln(1/\delta_\ell)}{\epsilon_\ell^2}
$$

次。令 $\hat{p}_{i,\ell}$ 表示第 $\ell$ 轮中第 $i$ 台游戏机的样本均值。由 Hoeffding 不等式，取常数 $C$ 足够大，可以保证

$$
P\left(
|\hat{p}_{i,\ell}-p_i|\leq \frac{\epsilon_\ell}{2}
\ \text{对所有}\ i\in S_{\ell-1}\ \text{同时成立}
\right)
\geq 1-\delta_\ell.
$$

在上述好事件发生时，若 $i^\star$ 没有被移除，则显然

$$
\max_{i\in S_\ell}p_i\geq \max_{i\in S_{\ell-1}}p_i-\epsilon_\ell.
$$

若 $i^\star$ 被移除，则所有保留下来的游戏机样本均值都不小于 $\hat{p}_{i^\star,\ell}$ 。于是对任意保留下来的 $j$ ，有

$$
p_j\geq \hat{p}_{j,\ell}-\frac{\epsilon_\ell}{2}
\geq \hat{p}_{i^\star,\ell}-\frac{\epsilon_\ell}{2}
\geq p_{i^\star}-\epsilon_\ell.
$$

因此仍然有

$$
\max_{i\in S_\ell}p_i\geq \max_{i\in S_{\ell-1}}p_i-\epsilon_\ell.
$$

综上

$$
P\left(
\max_{i\in S_\ell}p_i\geq \max_{i\in S_{\ell-1}}p_i-\epsilon_\ell
\right)
\geq 1-\delta_\ell.
$$

(2)

取

$$
\epsilon_\ell=\frac{\epsilon}{4}\left(\frac{3}{4}\right)^{\ell-1},
\qquad
\delta_\ell=\frac{1}{3\cdot 2^\ell}.
$$

则

$$
\sum_{\ell=1}^{+\infty}\epsilon_\ell=\epsilon,
\qquad
\sum_{\ell=1}^{+\infty}\delta_\ell=\frac{1}{3}.
$$

由上一问和 union bound，以至少 $1-\frac{1}{3}=\frac{2}{3}$ 的概率，每一轮的损失控制事件都成立。此时最终返回的游戏机 $o$ 满足

$$
p_o\geq \max_i p_i-\sum_{\ell\geq 1}\epsilon_\ell
=\max_i p_i-\epsilon.
$$

下面估计算法总采样次数。第 $\ell$ 轮候选游戏机数满足

$$
n_\ell\leq \frac{n}{2^{\ell-1}}.
$$

所以总采样数至多为

$$
\begin{align*}
\sum_{\ell\geq 1}n_\ell N_\ell
&\leq
\sum_{\ell\geq 1}
\frac{n}{2^{\ell-1}}
\cdot
C\frac{\ln(1/\delta_\ell)}{\epsilon_\ell^2} \\
&=
O\left(
\frac{n}{\epsilon^2}
\sum_{\ell\geq 1}
\ell\left(\frac{8}{9}\right)^{\ell-1}
\right) \\
&=O\left(\frac{n}{\epsilon^2}\right).
\end{align*}
$$

因此该算法以至少 $\frac{2}{3}$ 的概率返回满足

$$
p_o\geq \max_i p_i-\epsilon
$$

的游戏机，并且总采样次数为 $O(n/\epsilon^2)$ 。
