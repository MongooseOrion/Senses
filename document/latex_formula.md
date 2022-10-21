# 在 Markdown 文件中插入 Latex 格式的公式
从很久很久以前，大概是大一的时候，我写了人生中第一篇真正意义上的论文。那好像是一篇推导哈密顿算符对易性的论文，具体是什么内容我已经不记得了，但是当时满页的公式我用 word 公式编辑器一个一个敲的那种崩溃的感觉，我是记忆尤新的。从那时我就在想，有没有什么更方便地敲公式的方法。后来我知道了 Latex，用英文单词和少数单词的组合就能敲出分数、积分、上下标、希腊字母等等元素，我是震惊的。

回到现在，Github 支持 markdown 书写公式好像也不是很早之前的事情，现在还不是非常令人满意，尤其在字体显示上，有些不到位。同时，还是因为**空格**问题，我又踩了很多坑。**空格**真的很讨厌啊！！！点击[此处](https://www.latexlive.com/)访问在线 Latex 编辑器。

## 基本四则运算
Latex 保留了加号`+`和减号`-`，但是乘号和除号就需要记专门的单词了：
  * 加：`+`
  * 减：`-`
  * 乘（叉乘）；`\times`
  * 除：`\div`

一个简单的二次函数写为 `$y=x+2$`，这是行内公式的写法。而行间公式应该写为：
```
$$y=x+2$$
```
它将自动居中，试试：
$$y=x+2$$
**一定要注意**：行内公式一定要在 `$for$` 的首插入空格（尾就不是必要的了），否则就会像这样：$y=x+2$，直接不渲染 $y=x+2$ 了。同时，在`$for$`符号向内的两头不允许加空格，否则也不能渲染： $ y=x+2 $

## 带有上下标和分式的复杂公式
上标使用 “ ^ ”表示，下标使用下划线 “ _ ” 表示，x 的平方 $x^{2}$ 和漏电流 $I_{D}$ 分别这样键入：
```
$$x^{2}$$
$$I_{D}$$
```
Latex 中大括号作为分隔符使用，用来产生当前元素和下一元素的边界，不加大括号写栅源电压就变成了这个样子 $V_GS$，而我们要的应该是这样： $V_{GS}$ 。

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
而中括号和小括号在容易产生歧义的地方也可以加上`$\left[ content \right]$`，但不是必需的。

## 希腊字母
希腊字母如果会读，就没事了，否则只能硬着记，这都怪我的数学老师。我能遇到的希腊字母大致就下面这些了：
```
\alpha \beta \lambda \gamma \varepsilon \xi \eta \varphi \rho \sigma \omega \chi \psi
```
这里就以行内公式输出为： $\alpha$ $\beta$ $\lambda$ $\gamma$ $\varepsilon$ $\xi$ $\eta$ $\varphi$ $\rho$ $\sigma$ $\omega$ $\chi$ $\psi$ 。

## 量子力学、复数域或布尔运算
量子力学定义的物质波方程可以表示为 $E=\bar{h} \omega$ ，这里的约化普朗克常数这样键入：`\bar{h}`。

复数域表示的网络函数定义为电路的响应相量与电路的激励相量之比，用下述公式表示：
$$H(j\omega)=\frac{\dot{Y}}{\dot{X}}$$
其中，响应相量由`$\dot{Y}$`键入，激励向量由`$\dot{X}$`键入。

布尔运算可能用到反函数，一个简单的二端与非化或非运算由这样表示：
```
$$\overline{AB}=\overline{A}+\overline{B}$$
```
输出为：
$$\overline{AB}=\overline{A}+\overline{B}$$
不难发现，都是加一横，使用`\overline`会比`\bar`长一些，根据实际应用的不同，两者应严格区分。

## 微积分学科
首先使用 Latex 公式格式给出极限的**定义**：<br>
`$\lim_{x \to \infty}{x_n=a} \Leftrightarrow \forall \varepsilon > 0$`，`$\exists$`正整数`$N$` ，当`$n>N$`时，有`$\left| x_n-a \right| < \varepsilon$`。<br><br>
上述句子可被渲染为：<br>
$\lim_{x \to \infty}{x_n=a} \Leftrightarrow \forall \varepsilon > 0$， $\exists$ 正整数 $N$ ，当 $n>N$ 时，有 $\left| x_n-a \right| < \varepsilon$ 。<br>

### 偏微分
偏微分方程常常会用 $u_{xy}$ 来表示算子，它的定义为：
$$u_{xy}=\frac{\partial^{2} u}{\partial{y}\partial{x}}$$
其中，偏微分符号由`$\partial{}$`给出。

### 一重积分
在看过教科书，掌握了一系列微积分的知识之后，下面开始计算积分内容：
```
$$\int_{\frac{1}{2}}^{\frac{3}{2}}{\frac{1}{\left| x-x^2 \right|}\\ dx}$$
```
渲染为：
$$\int_{\frac{1}{2}}^{\frac{3}{2}}{\frac{1}{\sqrt{\left| x-x^2 \right|}}\\ dx}$$
上式定义了一个 `$x \in [a,b]$` ( $x \in [a,b]$ ) 的广义积分，其中 \\int 表示积分符号，同时还可以看出当下标和上标都需要进行标注时，**一定是遵循先写下标，再写上标的顺序**。请注意，如果我们想要在待积分函数和 dx 之间加一个空格（当然这个必须要加），直接打空格是没有作用的——这个时候我们需要请出转义字符 “\” 。**通过`func\ dx`的命令可以在他们之间插入一个空格**，然而因为 markdown 语法又有一次转义，所以使用 markdown 时应自觉再加一个 “\”，这样就变成了`func\\ dx`。来看看不对空格处理是什么效果：
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
其中`$\iint$`就表示二重积分符号，不用想三重肯定是`$\iiint$`了，`$\limits_{}$`表示限定为此区域的积分，与积分上下限不同，不可混用。

最后，还有一个曲线积分，表示为`$\oint_{}^{}$`。

### 实战
**麦克斯韦方程组**是一组描述**电场、磁场与电荷密度、电流密度**之间关系的偏微分方程。它由四个方程组成：描述电荷如何产生电场的**高斯定律**、论述磁单极子不存在的**高斯磁定律**、描述电流和时变电场怎样产生磁场的**安培定律**、描述时变磁场如何产生电场的**法拉第感应定律**。它可以这样表示：
```
// 微分形式
$$\nabla \times \vec{E} = -\frac{\partial{\vec B}}{\partial t}$$
$$\nabla \times \vec{H} = \vec{J}+\frac{\partial{\vec D}}{\partial t}$$
$$\nabla \cdot \vec{D} = \rho$$
$$\nabla \cdot \vec{B} = 0$$

// 积分形式
$$\oint{\vec{E} \cdot d\vec{l}}=-\int_{s}{-\frac{\partial{\vec{B}}}{\partial t}\cdot d\vec{s}}$$
$$\oint{\vec{H} \cdot d\vec{l}}=\int_{s}{\vec{J}+\frac{\partial{\vec{D}}}{\partial t}\\ d\vec{s}}=I+\int{\frac{\partial{\vec{D}}}{\partial t}\cdot d\vec{s}}$$
$$\int{\vec{D}\cdot d\vec{l}}=\rho \cdot s=Q$$
$$\int{\vec{B}\cdot d\vec{s}}=0$$
```
渲染为：

**// 微分形式**
$$\nabla \times \vec{E} = -\frac{\partial{\vec B}}{\partial t}$$
$$\nabla \times \vec{H} = \vec{J}+\frac{\partial{\vec D}}{\partial t}$$
$$\nabla \cdot \vec{D} = \rho$$
$$\nabla \cdot \vec{B} = 0$$
**积分形式**
$$\oint{\vec{E} \cdot d\vec{l}}=-\int_{s}{-\frac{\partial{\vec{B}}}{\partial t}\cdot d\vec{s}}$$
$$\oint{\vec{H} \cdot d\vec{l}}=\int_{s}{\vec{J}+\frac{\partial{\vec{D}}}{\partial t}\\ d\vec{s}}=I+\int{\frac{\partial{\vec{D}}}{\partial t}\cdot d\vec{s}}$$
$$\int{\vec{D}\cdot d\vec{l}}=\rho \cdot s=Q$$
$$\int{\vec{B}\cdot d\vec{s}}=0$$

其中，**矢量** $\vec{E}$ 可由`$\vec{E}$`表示，**点乘** $\cdot$ 可由`$\cdot$`表示，**劈形算符（哈密顿运算符、散度算符）** $\nabla$ 由`$\nabla$`给出。
