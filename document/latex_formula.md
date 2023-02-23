# 在 Markdown 文件中插入 Latex 格式的公式
从很久很久以前，大概是大一的时候，我写了人生中第一篇真正意义上的论文。那好像是一篇推导哈密顿算符对易性的论文，具体是什么内容我已经不记得了，但是当时满页的公式我用 word 公式编辑器一个一个敲的那种崩溃的感觉，我是记忆尤新的。从那时我就在想，有没有什么更方便地敲公式的方法。后来我知道了 Latex，用英文单词和少数单词的组合就能敲出分数、积分、上下标、希腊字母等等元素，我是震惊的。

回到现在，Github 支持 markdown 书写公式好像也不是很早之前的事情，现在还不是非常令人满意，尤其在字体显示上，有些不到位。同时，还是因为**空格**问题，我又踩了很多坑。**空格**真的很讨厌啊！！！点击[此处](https://www.latexlive.com/)访问在线 Latex 编辑器。

*请注意：下述内容均采用 GitHub 的 Markdown 编辑标准，可能与某些软件或服务的用法有所不同。*

## 基本四则运算
Latex 保留了加号`+`和减号`-`，但是乘号和除号就需要记专门的单词了：
  * 加：`+`
  * 减：`-`
  * 乘（叉乘）：`\times`
  * 点乘：`\cdot`
  * 除：`\div`
  * 正负：`\pm`
  * 负正：`\mp`

一个简单的二次函数写为 `$y=x+2$`，这是行内公式的写法。而行间公式应该写为：
```
$$y=x+2$$
```
它将自动居中，试试：
$$y=x+2$$
**一定要注意**：行内公式一定要在 `$for$` 的首插入空格（尾就不是必要的了），否则就会像这样：$y=x+2$，直接不渲染 $y=x+2$ 了。同时，在`$for$`符号向内的两头不允许加空格，否则也不能渲染： $ y=x+2 $ 。

### 比较
```
大于： $>$ 
小于： $<$
大于等于： $\ge$
小于等于： $\le$
远大于： $\gg$
远小于： $\ll$
```

这里以 MOSFET 以输出特性曲线划分区域时 $V_{GS}$ 取何值为例：
```
截止区：    ${V_{GS}} > {V_{TH}}$
深线性区：  $V_{GS} > V_{TH}$, $V_{DS} \ll 2(V_{GS}-V_{TH})$
三极管区：  $V_{GS} > V_{TH}$, $V_{DS} \le V_{GS}-V_{TH}$
饱和区：    $V_{DS} > V_{GS}-V_{TH}$
```
可渲染为：
  * 截止区： ${V_{GS}} > {V_{TH}}$
  * 深线性区： $V_{GS} > V_{TH}$, $V_{DS} \ll 2(V_{GS}-V_{TH})$
  * 三极管区： $V_{GS} > V_{TH}$, $V_{DS} \le V_{GS}-V_{TH}$
  * 饱和区： $V_{DS} > V_{GS}-V_{TH}$

## 带有上下标和分式的复杂公式
上标使用` ^ `表示，下标使用下划线` _ `表示，x 的平方 $x^{2}$ 和漏电流 $I_{D}$ 分别这样键入：
```
$$x^{2}$$
$$I_{D}$$
```
Latex 中**大括号作为分隔符使用**，用来产生当前元素和下一元素的边界，不加大括号写栅源电压就变成了这个样子 $V_GS$，而我们要的应该是这样： $V_{GS}$ 。

分数使用`$\frac{}{}$`来键入，其中前一个大括号填入**分子**，后一个大括号内填入**分母**。例如如果想要键入一个反比例函数 $y=\frac{1}{x}$：
```
$$y=\frac{1}{x}$$
```

现在键入一个漏电流 $I_D$ 在三极管区的函数：
```
$$I_{D}=\mu_{n}C_{ox}\frac{W}{L}[(V_{GS}-V_{TH})V_{DS}-\frac{1}{2}V_{DS}^{2}]$$
```
得到渲染结果：
$$I_{D}=\mu_{n}C_{ox}\frac{W}{L}[(V_{GS}-V_{TH})V_{DS}-\frac{1}{2}V_{DS}^{2}]$$

在编辑窗口其实可以看到编辑器将公式中括号中的内容标注上了下划线，这代表它认为这是超链接了，但是对输出内容并没有影响。

同时大括号应使用`$\left\\{ content \right \\}$`来表示，本来在 Latex 中用作公式元素的大括号只需要加一个 “\” ，但是 markdown 中转义字符会消除一个 “\”，因此需要两个 “\\”。下述式子输出 $\left\\{ 89 \right \\}$ ：
```
$$\left\\{ 89 \right \\}$$
```
当某一内容的高度比标准的文本符号`[]`还要高的时候（例如括上分式或者积分），需要这样键入：`$\left[ content \right]$`。

## 希腊字母
希腊字母如果会读，就没事了，否则只能硬着记，这都怪我的数学老师。我能遇到的希腊字母大致就下面这些了：
```
\alpha \beta \lambda \gamma \varepsilon \xi \eta \varphi \rho \sigma \omega \chi \psi
```
这里就以行内公式输出为： $\alpha$ $\beta$ $\lambda$ $\gamma$ $\varepsilon$ $\xi$ $\eta$ $\varphi$ $\rho$ $\sigma$ $\omega$ $\chi$ $\psi$ 。

## 对多个公式编号
在证明某些关系时，常常会引出多个公式联立来解决问题，这个时候需要对每个公式编号。编号的用法是在公式后加入`\tag{}`标识符，就像这样：
```
$$H(s)=\frac{v_o(s)}{v_i(s)} \tag{1.1}$$
```
将会渲染为：
$$H(s)=\frac{v_o(s)}{v_i(s)} \tag{1.1}$$

## 量子力学、复数域或布尔运算
量子力学定义的物质波方程可以表示为 $E=\bar{h} \omega$ ，这里的约化普朗克常数这样键入：`\bar{h}`。

复数域表示的网络函数定义为电路的响应相量与电路的激励相量之比，用下述公式表示：
$$H(j\omega)=\frac{\dot{Y}}{\dot{X}}$$
其中，响应相量由`$\dot{Y}$`键入，激励向量由`$\dot{X}$`键入。

布尔运算可能用到**反函数**，一个简单的二端与非化或非运算由这样表示：
```
$$\overline{AB}=\overline{A}+\overline{B}$$
```
输出为：
$$\overline{AB}=\overline{A}+\overline{B}$$
不难发现，都是加一横，使用`\overline`会比`\bar`长一些，根据实际应用的不同，两者应严格区分。

<br>有些时候，我们需要**连等**来表示某一公式的推导过程，可以使用`{align*}`环境来实现，下面是一个例子：
```
$$\begin{align*}
  f_T(t) &= \frac{a_0}{2}+\sum_{n=1}^{\infty}a_n \frac{e^{jn\omega_0 t}+e^{-jn\omega_0 t}}{2}+\sum_{n=1}^{\infty}b_n\frac{e^{jn\omega_0 t}-e^{-jn\omega_0 t}}{2j} \\
  &= \frac{a_0}{2}+\sum_{n=1}^{\infty}\frac{a_n-jb_n}{2}e^{jn\omega_0 t}+\sum_{n=1}^{\infty}\frac{a_n+jb_n}{2}e^{-jn\omega_0 t} \\
  &= \frac{a_0}{2}+\sum_{n=1}^{\infty}F_n e^{jn\omega_0 t}+\sum_{n=1}^{\infty}F_{-n} e^{-jn\omega_0 t} \\
  &= F_0+\sum_{n=1}^{\infty}F_n e^{jn\omega_0 t}+\sum_{n=-\infty}^{-1}F_n e^{jn\omega_0 t} \\
  &= \sum_{n=-\infty}^{\infty}F_n e^{jn\omega_0 t}
\end{align*}$$
```
上式表示连续周期函数的傅里叶级数，利用三角型傅里叶系数和欧拉公式导出指数型傅里叶级数，它将渲染为：

$$\begin{align*}
  f_T(t) &= \frac{a_0}{2}+\sum_{n=1}^{\infty}a_n \frac{e^{jn\omega_0 t}+e^{-jn\omega_0 t}}{2}+\sum_{n=1}^{\infty}b_n\frac{e^{jn\omega_0 t}-e^{-jn\omega_0 t}}{2j} \\
  &= \frac{a_0}{2}+\sum_{n=1}^{\infty}\frac{a_n-jb_n}{2}e^{jn\omega_0 t}+\sum_{n=1}^{\infty}\frac{a_n+jb_n}{2}e^{-jn\omega_0 t} \\
  &= \frac{a_0}{2}+\sum_{n=1}^{\infty}F_n e^{jn\omega_0 t}+\sum_{n=1}^{\infty}F_{-n} e^{-jn\omega_0 t} \\
  &= F_0+\sum_{n=1}^{\infty}F_n e^{jn\omega_0 t}+\sum_{n=-\infty}^{-1}F_n e^{jn\omega_0 t} \\
  &= \sum_{n=-\infty}^{\infty}F_n e^{jn\omega_0 t}
\end{align*}$$

可以发现，关键是符号` &= `，使用这个符号的等号将自动对齐。当然，如果某一行我只想要等号，而不需要对齐，也可以直接使用`=`，这是允许的。

必须注意的是，使用`\begin...\end`环境时，**在公式上部和下部应各空一行**，否则 GitHub 将无法渲染。

## 微积分学科
首先使用 Latex 公式格式给出极限的**定义**：<br>
`$\lim_{x \to \infty}{x_n=a} \Leftrightarrow \forall \varepsilon > 0$`，`$\exists$`正整数`$N$` ，当`$n>N$`时，有`$\left| x_n-a \right| < \varepsilon$`。<br><br>
上述句子可被渲染为：<br>
$\lim_{x \to \infty}{x_n=a} \Leftrightarrow \forall \varepsilon > 0$， $\exists$ 正整数 $N$ ，当 $n>N$ 时，有 $\left| x_n-a \right| < \varepsilon$ 。<br>

### 偏微分
偏微分方程常常会用 $u_{xy}$ 来表示算子，它的定义为：
$$u_{xy}=\frac{\partial^{2} u}{\partial{y}\partial{x}}$$
其中，**偏微分符号**由`$\partial{}$`给出。

<br>如果**多元函数求导时限定某一变量的值**，应当键入`\left . \right |`，例如规定函数 $z(x,y)$ 对变量 $y$ 求导，并使变量 $x=0$ ，应当这样：
```
\left . \frac{\partial z(x,y)}{\partial y} \right |_{x=0}
```
将被渲染为：
$$\left . \frac{\partial z(x,y)}{\partial y} \right |_{x=0}$$

### 一重积分
在看过教科书，掌握了一系列微积分的知识之后，下面开始计算积分内容：
```
$$\int_{\frac{1}{2}}^{\frac{3}{2}}{\frac{1}{\left| x-x^2 \right|}\\ dx}$$
```
渲染为：
$$\int_{\frac{1}{2}}^{\frac{3}{2}}{\frac{1}{\sqrt{\left| x-x^2 \right|}}\\ dx}$$
上式定义了一个 `$x \in [a,b]$` ( $x \in [a,b]$ ) 的广义积分，其中 `\int` 表示积分符号，同时还可以看出当下标和上标都需要进行标注时，**一定是遵循先写下标，再写上标的顺序**。请注意，如果我们想要在待积分函数和 `dx` 之间加一个空格（当然这个必须要加），直接打空格是没有作用的——这个时候我们需要请出转义字符 `\` 。**通过`func\ dx`的命令可以在他们之间插入一个空格**，然而因为 markdown 语法又有一次转义，所以使用 markdown 时应自觉再加一个 `\`，这样就变成了`func\\ dx`。来看看不对空格处理是什么效果：
$$\int_{\frac{1}{2}}^{\frac{3}{2}}{\frac{1}{\sqrt{\left| x-x^2 \right|}}dx}$$
要是你这样写，不要让人知道你是大学生。

另外，根号是通过`$\sqrt[n]{a}$`实现的，其中 *n* 表示开根阶数，*a* 表示待开根的常数或代数式，如果是二阶的，则无需写`[n]`。<br>

下面来练习一下：
```
$$\int{\frac{arcsin\\ {\sqrt{x}}+ln\\ {x}}{\sqrt{x}}\\ dx}$$
```
$$\int{\frac{arcsin\\ {\sqrt{x}}+ln\\ {x}}{\sqrt{x}}\\ dx}$$

### 多重积分
直接打内容吧：
```
$$I = \iint_{D}{f(x,y)\\ d\sigma}$$
```
$$I=\iint\limits_{D}{f(x,y)\\ d\sigma}$$
其中`$\iint$`就表示**二重积分符号**，不用想**三重积分**肯定是`$\iiint$`了，`$\limits_{}$`表示**限定为此区域的积分**，与积分上下限不同，不可混用。

最后，还有一个**曲线积分**，表示为`$\oint_{}^{}$`。

## 线性代数
表示**矩阵**时，应当使用`{bmatrix}`环境；表示**行列式**时，应当使用`{vmatrix}`环境。

例如键入一个三阶单位矩阵：
```
\begin{bmatrix}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1
\end{bmatrix}
```
它将被渲染为：

$$\begin{bmatrix}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1
\end{bmatrix}$$

其中，符号` \\ `表示换行；` & `表示空 4 格，是一个分隔符。

这个矩阵的行列式，将`{bmatrix}`替换为`{vmatrix}`即可：
```
\begin{vmatrix}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1
\end{vmatrix}
```
渲染为：

$$\begin{vmatrix}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1
\end{vmatrix}$$

### 线性方程组
线性方程组可以使用`{cases}`环境来实现，一个三元方程组可以这样键入：
```
$$\begin{cases}
a_{11}x_1+a_{12}x_2+a_{13}x_3=b_1 \\
a_{21}x_1+a_{22}x_2+a_{23}x_3=b_2 \\
a_{31}x_1+a_{32}x_3+a_{33}x_3=b_3
\end{cases}$$
```
它将渲染为：

$$\begin{cases}
a_{11}x_1+a_{12}x_2+a_{13}x_3=b_1 \\
a_{21}x_1+a_{22}x_2+a_{23}x_3=b_2 \\
a_{31}x_1+a_{32}x_3+a_{33}x_3=b_3
\end{cases}$$

`{cases}`环境实际上表示**条件等式**环境，这就意味着，**只要是需要大括号的场景，都可以使用这个环境**。

## 实战
**麦克斯韦方程组**是一组描述**电场、磁场与电荷密度、电流密度**之间关系的偏微分方程。它由四个方程组成：描述电荷如何产生电场的**高斯定律**、论述磁单极子不存在的**高斯磁定律**、描述电流和时变电场怎样产生磁场的**安培定律**、描述时变磁场如何产生电场的**法拉第感应定律**。它可以这样表示：
```
// 微分形式
// 使用条件等式 {cases} 环境
$$\begin{cases}
\nabla \times \vec{E} = -\frac{\partial{\vec B}}{\partial t} \\
\nabla \times \vec{H} = \vec{J}+\frac{\partial{\vec D}}{\partial t} \\
\nabla \cdot \vec{D} = \rho \\
\nabla \cdot \vec{B} = 0
\end{cases}$$

// 积分形式
// 使用多行对齐等式 {align*} 环境，以第一个等号对齐
$$\begin{align*}
\oint{\vec{E} \cdot d\vec{l}} &= -\int_{s}{-\frac{\partial{\vec{B}}}{\partial t}\cdot d\vec{s}} \\
\oint{\vec{H} \cdot d\vec{l}} &= \int_{s}{\vec{J}+\frac{\partial{\vec{D}}}{\partial t}\ d\vec{s}}=I+\int{\frac{\partial{\vec{D}}}{\partial t}\cdot d\vec{s}} \\
\int{\vec{D}\cdot d\vec{l}} &= \rho \cdot s=Q \\
\int{\vec{B}\cdot d\vec{s}} &= 0
\end{align*}$$
```
渲染为：

**微分形式：**

$$\begin{cases}
\nabla \times \vec{E} = -\frac{\partial{\vec B}}{\partial t} \\
\nabla \times \vec{H} = \vec{J}+\frac{\partial{\vec D}}{\partial t} \\
\nabla \cdot \vec{D} = \rho \\
\nabla \cdot \vec{B} = 0
\end{cases}$$

**积分形式：**

$$\begin{align*}
\oint{\vec{E} \cdot d\vec{l}} &= -\int_{s}{-\frac{\partial{\vec{B}}}{\partial t}\cdot d\vec{s}} \\
\oint{\vec{H} \cdot d\vec{l}} &= \int_{s}{\vec{J}+\frac{\partial{\vec{D}}}{\partial t}\ d\vec{s}}=I+\int{\frac{\partial{\vec{D}}}{\partial t}\cdot d\vec{s}} \\
\int{\vec{D}\cdot d\vec{l}} &= \rho \cdot s=Q \\
\int{\vec{B}\cdot d\vec{s}} &= 0
\end{align*}$$

其中，**矢量** $\vec{E}$ 可由`$\vec{E}$`表示，**点乘** $\cdot$ 可由`$\cdot$`表示，**劈形算符（哈密顿运算符、散度算符）** $\nabla$ 由`$\nabla$`给出。
