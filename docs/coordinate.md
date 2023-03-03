# coordinate

同一向量在不同坐标系下的关系

## 坐标的表达

$$
\begin{aligned}
    F &= f_1 i_1 + f_2 i_2 + f_3 i_3 \\
    &=
    \begin{bmatrix}
        i_{ 1 } , i_{ 2 } , i_{ 3 }
    \end{bmatrix}
    \begin{bmatrix}
        f_{ 1 } \\
        f_{ 2 } \\
        f_{ 3 }
    \end{bmatrix} \\
    &= i f^i
\end{aligned}
$$

- $i$: 坐标系矩阵
- $f^i$: 坐标系下的向量

## 坐标系的变换

- $e$是新的坐标系
- $i$是旧的坐标系

$$
\begin{bmatrix} { e_{ 1 } , e_{ 2 } , e_{ 3 } } \end{bmatrix} =\begin{bmatrix} { i_{ 1 } , i_{ 2 } , i_{ 3 } } \end{bmatrix}
\begin{bmatrix}
p_{11} & p_{12} & p_{13} \\
p_{21} & p_{22} & p_{23} \\
p_{31} & p_{32} & p_{33}
\end{bmatrix}
$$

或

$$e = i P$$

## 变换

用物体坐标系思考

e 为物体坐标系, i 为世界坐标系

e 坐标系下的向量为$f^e$, 则世界坐标系下的表达

$$F = e f^e = (i P) f^e = i (P f^e)$$

得到坐标点的变换

$$f^i = P f^e$$

## 链式

递归地思考

$$e_n = e_{n-1} P_{n-1}^n$$

形成链式

$$e_n = e_{1} P_{1}^2 P_{2}^3 \cdots P_{n-1}^n$$

得到

$$P_{1}^n = P_{1}^2 P_{2}^3 \cdots P_{n-1}^n$$

> $P_{n-1}^n$像分数一样理解$\frac{n}{n-1}$, $P_1^n$代表在 1 的坐标系下的观察 n 的坐标系的点
>
> $$
> \begin{aligned}
>     e_j &= e_i P_i^j \\
>     f^i &= P_i^j f^j \\
> \end{aligned}
> $$

- 从左往右思考

  对 1 坐标系进行相对 1 变换$P_1^2$得到 2

  > 相对自身平移 30

  对 2 坐标系进行相对 2 变换$P_2^3$得到 3

  > 相对自己旋转 60°

  对 3 坐标系进行相对 3 变换$P_3^4$得到 4

  > 相对自己伸缩 2

- 从右往左

  需要用归纳的视角, 用归纳假设

  ?> 很像 [fold](https://dzylikecode.github.io/lang-hs/#/diving/fold?id=foldl) 的理解

  $$P_1^n = P_1^{n-1} P_{n-1}^n$$

  先将点变换到 n-1 坐标系下, 但是有一个假设$P_1^{n-1}$

## 坐标点与坐标系

- 对坐标系的变换

  $$e = i P$$

- 对坐标点的变换

  $$f^e = P f^i$$

---

?> 对坐标系变换等于对坐标点变换的逆

$$
\begin{aligned}
    F &= e_1 f_1 \\
    &= e_1 P_1^n (P_1^n)^{-1} f_1 \\
    &= e_n (P_1^n)^{-1} f_1 \\
\end{aligned}
$$

对于坐标系 A, $e_n = e_1 P_1^n$代表了 A 由状态 1 变换到状态 n. 在坐标系 A 的视角下看待坐标点 f, 相当于做了变换$(P_1^n)^{-1}f_1$

## rotation

正交矩阵 orthogonal Matrix

$$e = i P$$

由于$e_1$这些是向量, 所以$e, i$是矩阵, 且是正交矩阵

$$
\begin{aligned}
P &= i^{-1}e \\
&= i^{T}e \\
&= \begin{bmatrix}
i_{1}^{T} \\
i_{2}^{T} \\
i_{3}^{T}
\end{bmatrix}
\begin{bmatrix}
e_{1} & e_{2} & e_{3}
\end{bmatrix} \\
&= \begin{bmatrix}
i_{1}^{T}e_{1} & i_{1}^{T}e_{2} & i_{1}^{T}e_{3} \\
i_{2}^{T}e_{1} & i_{2}^{T}e_{2} & i_{2}^{T}e_{3} \\
i_{3}^{T}e_{1} & i_{3}^{T}e_{2} & i_{3}^{T}e_{3}
\end{bmatrix}
\end{aligned}
$$

所以有$$p_{ij} = i_{i}^{T}e_{j} = \cos (i_i, e_j)$$

点乘本身使用$cos$表达, 所以可以用$cos$来表达

> 可以用$cos$来表达旋转矩阵,

## 正交性

$$I = e^{T}e = (i P)^{T} i P = P^{T} P$$

$P$也是正交矩阵

由

$$f^i = P f^e$$

可得

$$f^e = P^{-1} f^i = P^{T} f^i$$

## 描述力

$$R = \sum_{i=1}^n F_i$$

根据

$$F_i = i f_i^i = e f_i^e$$

可得

$$R_i = \sum_{i=1}^n i f_i^i$$

$$R_e = \sum_{i=1}^n e f_i^e$$
