## 数学字符发音

$\hat{x}$  读作：x hat 

$\bar{x}$  读作：x bar

$x\prime$  读作：x prime

$\dot{x}$  读作：x dot

$\tilde{x}$  读作： x tilde

补充相关数学字符发音：[Pronunciation of mathematical symbols](http://www.uefap.com/speaking/symbols/symbols.htm)


## 知识点

$\delta(t)$ 冲激函数  $Kronecker \ Delta$函数

$ODE:Ordinary Differential Equation$  常微分方程

$O(x^2)$表示$x^2$的同阶无穷小，$\omicron o(x^2)$表示$x^2$的高阶无穷小




<br></br>

$C^n[a, b]$：这表示在区间$[a,b]$上具有连续$n$次导数的函数集合。

$f \in C^n[a, b]$：函数$f(x)$在区间$[a,b]$上（至少）具有$n$阶连续导数。

特殊地，$f \in C^1[a, b]$：函数$f(x)$在区间$[a,b]$上（至少）具有$1$阶连续导数。

$f \in C^0[a, b]$：这不是一个常见的表示形式，因为通常表示零阶连续函数（即连续函数）的集合，而零阶导数的概念并不是很有意义。在一般的数学文献中，一般将连续函数的集合表示为$f \in C[a, b]$

$f \in C[a, b]$：函数$f(x)$在区间$[a,b]$上是连续的。

<br></br>

$\mathbb{R}^n$表示$n$维实数向量空间。这是一个由所有包含$n$个实数元素的向量组成的集合。这里的$\mathbb{R}^n$表示实数集，而上标$n$表示向量的维度，即向量中实数元素的个数。

$\mathbb{R}^n$中的一个典型元素可以写作$(x_1,x_2,...,x_n)$，其中$x_1,x_2,...,x_n$是实数。这样的元素就是$n$维实数向量，可以用来表示$n$维空间中的一个点。

<br></br>


若$\varphi_0(x),\varphi_1(x),...,\varphi_{n-1}(x)$是[a,b]上的线性无关函数，且$a_0,a_1,...,a_{n-1}$是任意实数，则

$$S(x)=a_0\varphi_0(x)+a_1\varphi_1(x)+...+a_{n-1}\varphi_{n-1}(x)$$

的全体是$C[a,b]$中的一个子集，记作

$$\Phi=span\{\varphi_0,\varphi_1,...,\varphi_{n-1}\}$$

上式表示由这组线性无关的函数$\varphi_k(x),(k=0,1,...,n-1)$，所张成的子空间，或子集。即$[a,b]$区间上连续函数空间的一个子集。

## 定理

$Rolle's \ \  Theorem:$ 若$f(x)$充分光滑，$\varphi(x_0)=\varphi(x_1)=0$，则$\exists \ \xi \in [x_0,x_1]$使得$\varphi^{'}(\xi)=0$

定理中的充分光滑指的是满足任意阶可导任意阶连续

<br></br>

二元函数的$Taylor's formula$：

$$f(x, y) = f(a, b) + \frac{\partial f}{\partial x}(a, b)(x - a) + \frac{\partial f}{\partial y}(a, b)(y - b) + \frac{1}{2!}\left(\frac{\partial^2 f}{\partial x^2}(a, b)(x - a)^2 + 2\frac{\partial^2 f}{\partial x \partial y}(a, b)(x - a)(y - b) + \frac{\partial^2 f}{\partial y^2}(a, b)(y - b)^2\right) + \cdots
$$

这里，$f(x, y)$是二元函数，$(a,b)$是展开点，而$\frac{\partial f}{\partial x}$，$\frac{\partial f}{\partial y}$，$\frac{\partial^2 f}{\partial x^2}$，$\frac{\partial^2 f}{\partial x \partial y}$，$\frac{\partial^2 f}{\partial y^2}$，等分别表示函数$f(x, y)$关于$x$和$y$的一阶和二阶偏导数。



