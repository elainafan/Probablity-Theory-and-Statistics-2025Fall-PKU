## 第一题

![](./Picture%20Assets/hw8/1.png)

当对所有 $1\leq i\leq n$ 均有 $x_i=0$ 时，模型退化为

$$
y_i=\alpha+\epsilon_i.
$$

最小二乘估计量满足

$$
\hat{\alpha}
=\arg\min_\alpha\sum_{i=1}^{n}(y_i-\alpha)^2.
$$

对目标函数求导：

$$
\frac{d}{d\alpha}\sum_{i=1}^{n}(y_i-\alpha)^2
=-2\sum_{i=1}^{n}(y_i-\alpha).
$$

令导数为 $0$ ，得到

$$
\hat{\alpha}=\bar{y}=\frac{1}{n}\sum_{i=1}^{n}y_i.
$$

因为 $E(\epsilon_i)=0$ ，所以

$$
E(\hat{\alpha})
=\frac{1}{n}\sum_{i=1}^{n}E(y_i)
=\alpha.
$$

因此偏差为

$$
\operatorname{Bias}(\hat{\alpha})=0.
$$

又因为 $\epsilon_i$ 相互独立且 $\operatorname{Var}(\epsilon_i)=\sigma^2$ ，

$$
\operatorname{Var}(\hat{\alpha})
=\operatorname{Var}\left(\frac{1}{n}\sum_{i=1}^{n}\epsilon_i\right)
=\frac{\sigma^2}{n}.
$$

由于 $\hat{\alpha}$ 无偏，其均方误差为

$$
\operatorname{MSE}(\hat{\alpha})=\frac{\sigma^2}{n}.
$$

## 第二题

![](./Picture%20Assets/hw8/2.png)

记

$$
w_i=\frac{1}{\sigma_i^2}.
$$

由于 $\epsilon_i\sim N(0,\sigma_i^2)$ 且相互独立，对数似然函数在忽略常数项后为

$$
\ell(\alpha,\beta)
=-\frac{1}{2}\sum_{i=1}^{n}w_i(y_i-\beta x_i-\alpha)^2.
$$

因此极大似然估计等价于最小化加权平方和

$$
\sum_{i=1}^{n}w_i(y_i-\beta x_i-\alpha)^2.
$$

定义

$$
S_w=\sum_{i=1}^{n}w_i,\quad
S_x=\sum_{i=1}^{n}w_ix_i,\quad
S_y=\sum_{i=1}^{n}w_iy_i,
$$

以及

$$
S_{xx}=\sum_{i=1}^{n}w_ix_i^2,\qquad
S_{xy}=\sum_{i=1}^{n}w_ix_iy_i.
$$

正规方程为

$$
\begin{cases}
S_y=\hat{\alpha}S_w+\hat{\beta}S_x, \\
S_{xy}=\hat{\alpha}S_x+\hat{\beta}S_{xx}.
\end{cases}
$$

令

$$
D=S_wS_{xx}-S_x^2.
$$

由于 $x_i$ 不全相同且 $w_i>0$ ，有 $D>0$ 。解得

$$
\hat{\beta}=\frac{S_wS_{xy}-S_xS_y}{D},
\qquad
\hat{\alpha}=\frac{S_{xx}S_y-S_xS_{xy}}{D}.
$$

用矩阵形式看，令设计矩阵第一列全为 $1$ ，第二列为 $x_i$ ，并令

$$
W=\operatorname{diag}(w_1,\ldots,w_n).
$$

则

$$
\begin{bmatrix}
\hat{\alpha} \\
\hat{\beta}
\end{bmatrix}
=(X^\top WX)^{-1}X^\top Wy.
$$

由于 $E(y)=X(\alpha,\beta)^\top$ ，所以

$$
E
\begin{bmatrix}
\hat{\alpha} \\
\hat{\beta}
\end{bmatrix}
=
\begin{bmatrix}
\alpha \\
\beta
\end{bmatrix}.
$$

二者偏差均为 $0$ 。

又因为 $\operatorname{Cov}(y)=W^{-1}$ ，所以

$$
\operatorname{Cov}
\begin{bmatrix}
\hat{\alpha} \\
\hat{\beta}
\end{bmatrix}
=(X^\top WX)^{-1}
=
\frac{1}{D}
\begin{bmatrix}
S_{xx} & -S_x \\
-S_x & S_w
\end{bmatrix}.
$$

因此

$$
\operatorname{MSE}(\hat{\alpha})=\operatorname{Var}(\hat{\alpha})=\frac{S_{xx}}{D},
$$

以及

$$
\operatorname{MSE}(\hat{\beta})=\operatorname{Var}(\hat{\beta})=\frac{S_w}{D}.
$$

## 第三题

![](./Picture%20Assets/hw8/3.png)

一元线性回归的最小二乘估计满足正规方程

$$
\sum_{i=1}^{n}(y_i-\hat{y}_i)=0,
\qquad
\sum_{i=1}^{n}x_i(y_i-\hat{y}_i)=0.
$$

又有

$$
\hat{y}_i=\hat{\alpha}+\hat{\beta}x_i.
$$

由第一条正规方程可得

$$
\bar{y}=\frac{1}{n}\sum_{i=1}^{n}\hat{y}_i
=\hat{\alpha}+\hat{\beta}\bar{x}.
$$

因此

$$
\hat{y}_i-\bar{y}=\hat{\beta}(x_i-\bar{x}).
$$

现在分解

$$
y_i-\bar{y}=(y_i-\hat{y}_i)+(\hat{y}_i-\bar{y}).
$$

平方求和得到

$$
\begin{align*}
\operatorname{SST}
&=\sum_{i=1}^{n}(y_i-\bar{y})^2 \\
&=\sum_{i=1}^{n}(y_i-\hat{y}_i)^2
+\sum_{i=1}^{n}(\hat{y}_i-\bar{y})^2
+2\sum_{i=1}^{n}(y_i-\hat{y}_i)(\hat{y}_i-\bar{y}).
\end{align*}
$$

交叉项为

$$
\begin{align*}
\sum_{i=1}^{n}(y_i-\hat{y}_i)(\hat{y}_i-\bar{y})
&=\hat{\beta}\sum_{i=1}^{n}(y_i-\hat{y}_i)(x_i-\bar{x}) \\
&=\hat{\beta}\left[
\sum_{i=1}^{n}x_i(y_i-\hat{y}_i)
-\bar{x}\sum_{i=1}^{n}(y_i-\hat{y}_i)
\right] \\
&=0.
\end{align*}
$$

所以

$$
\operatorname{SST}=\operatorname{SSE}+\operatorname{SSR}.
$$

## 第四题

![](./Picture%20Assets/hw8/4%281%29.png)
![](./Picture%20Assets/hw8/4%282%29.png)

(1)

由定义

$$
q_1=\left[\frac{1}{\sqrt{n}},\frac{1}{\sqrt{n}},\ldots,\frac{1}{\sqrt{n}}\right]^\top.
$$

显然 $\|q_1\|=1$ 。又

$$
q_2=\left[
\frac{x_1-\bar{x}}{\sqrt{s_{xx}}},
\frac{x_2-\bar{x}}{\sqrt{s_{xx}}},
\ldots,
\frac{x_n-\bar{x}}{\sqrt{s_{xx}}}
\right]^\top,
$$

因此

$$
\|q_2\|^2
=\frac{\sum_{i=1}^{n}(x_i-\bar{x})^2}{s_{xx}}
=1.
$$

并且

$$
q_1^\top q_2
=\frac{1}{\sqrt{n}\sqrt{s_{xx}}}\sum_{i=1}^{n}(x_i-\bar{x})
=0.
$$

所以 $q_1,q_2$ 是标准正交向量组。由 Gram-Schmidt 正交化，可以将其扩充为 $\mathbb{R}^n$ 的一组标准正交基

$$
q_1,q_2,q_3,\ldots,q_n.
$$

(2)

把 $y$ 看作向量，则

$$
y=\alpha\mathbf{1}+\beta x+\epsilon,
$$

其中

$$
\epsilon\sim N(0,\sigma^2I_n).
$$

令 $Q$ 的第 $i$ 行为 $q_i^\top$ ，则 $Q$ 为正交矩阵，故

$$
z=Qy\sim N(Q(\alpha\mathbf{1}+\beta x),\sigma^2I_n).
$$

先计算均值。因为

$$
x=\bar{x}\mathbf{1}+\sqrt{s_{xx}}q_2,
$$

所以

$$
\alpha\mathbf{1}+\beta x
=(\alpha+\beta\bar{x})\mathbf{1}+\beta\sqrt{s_{xx}}q_2.
$$

于是

$$
E(z_1)=q_1^\top E(y)=\sqrt{n}(\alpha+\beta\bar{x}),
$$

$$
E(z_2)=q_2^\top E(y)=\beta\sqrt{s_{xx}},
$$

且对 $i\geq 3$ ，由于 $q_i$ 同时正交于 $q_1$ 和 $q_2$ ，

$$
E(z_i)=0.
$$

因此

$$
z\sim N\left(
\begin{bmatrix}
\sqrt{n}(\alpha+\beta\bar{x}) \\
\beta\sqrt{s_{xx}} \\
0 \\
\vdots \\
0
\end{bmatrix},
\sigma^2I_n
\right).
$$

特别地， $z_1,z_2,\ldots,z_n$ 相互独立。

(3)

由定义

$$
z_1=q_1^\top y
=\frac{1}{\sqrt{n}}\sum_{i=1}^{n}y_i
=\sqrt{n}\bar{y}.
$$

同时

$$
\begin{align*}
z_2
&=q_2^\top y \\
&=\frac{1}{\sqrt{s_{xx}}}\sum_{i=1}^{n}(x_i-\bar{x})y_i \\
&=\frac{1}{\sqrt{s_{xx}}}\sum_{i=1}^{n}(x_i-\bar{x})(y_i-\bar{y}) \\
&=\sqrt{s_{xx}}\hat{\beta}.
\end{align*}
$$

(4)

由第三题中的结论

$$
\hat{y}_i-\bar{y}=\hat{\beta}(x_i-\bar{x}).
$$

因此

$$
\sum_{i=1}^{n}(\hat{y}_i-\bar{y})^2
=\hat{\beta}^2\sum_{i=1}^{n}(x_i-\bar{x})^2
=s_{xx}\hat{\beta}^2
=z_2^2.
$$

另一方面，最小二乘拟合向量 $\hat{y}$ 是 $y$ 在 $\operatorname{span}\{q_1,q_2\}$ 上的正交投影。因此残差向量 $y-\hat{y}$ 是 $y$ 在 $\operatorname{span}\{q_3,\ldots,q_n\}$ 上的投影。由于 $q_1,\ldots,q_n$ 是标准正交基，

$$
\sum_{i=1}^{n}(y_i-\hat{y}_i)^2
=\sum_{i=3}^{n}z_i^2.
$$

结合 $s^2$ 的定义，

$$
(n-2)s^2=\sum_{i=1}^{n}(y_i-\hat{y}_i)^2=\sum_{i=3}^{n}z_i^2.
$$

(5)

由第二问可知，对 $i\geq 3$ ，

$$
z_i\sim N(0,\sigma^2)
$$

且它们相互独立。因此

$$
\frac{(n-2)s^2}{\sigma^2}
=\sum_{i=3}^{n}\left(\frac{z_i}{\sigma}\right)^2
\sim \chi_{n-2}^2.
$$

又 $\hat{\beta}=\frac{z_2}{\sqrt{s_{xx}}}$ ，且

$$
\hat{\alpha}=\bar{y}-\hat{\beta}\bar{x}
=\frac{z_1}{\sqrt{n}}-\frac{\bar{x}}{\sqrt{s_{xx}}}z_2.
$$

所以 $\hat{\alpha}$ 和 $\hat{\beta}$ 都只是 $z_1,z_2$ 的函数，而 $(n-2)s^2/\sigma^2$ 只是 $z_3,\ldots,z_n$ 的函数。由于 $z_1,z_2,\ldots,z_n$ 相互独立，得到

$$
\frac{(n-2)s^2}{\sigma^2}
$$

与 $\hat{\alpha}$ 和 $\hat{\beta}$ 均相互独立。
