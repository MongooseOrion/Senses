# Markdown 语法备忘录
## 如何不解析语句为对应的 Markdown 语法？
使用 HTML 标签可以令某些内容不被显示，也即：\<!-- content -->。 <br><br>
\<!-- 这行代码原本是不能显示的 -->，但由于在内容前加入转义字符 “\”，内容可被显示。<br><br>
现在我们来做一个实验，在引号中加入 Markdown 语法：“这是一个*例子*”。可以看到被解析，再来试试在星号前加入“\”，“这是一个\*例子*”，可以看到不被解析了。<br><br>
**总结**：“\” 可以强制将隐藏的 html 原始代码显示，同时也可在 markdown 语法前加入以去掉 markdown 的效果。

## 如何插入代码块？
Markdown 语法给出了一种简单的插入代码的方式：[围栏式代码块](https://docs.github.com/cn/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks)<br><br>
\```ruby<br>
module anti(<br>
  input       a,<br>
  input       b,<br>
  output  reg q<br>
);<br>
\```<br>
其中，“ruby” 代表加入高亮效果，上述写法将渲染为：

```ruby
module anti(
  input       a,
  input       b,
  output  reg q
);
```

在代码块的上下行打上三个 “ ``` ” 符号，可渲染围栏式代码块，**注意是制表键上面的那个打 “\`timescale” 的按键**，而不是单引号。

## 加入行内高亮效果（行内引用）
行内引用可以使用行内代码来实现，例如：**行内代码是使用 \`符号\` 来实现的**，中间的部分将渲染为下述的样子：<br><br>
行内代码是使用 `符号` 来实现的。<br><br>
其中，行内代码两边插入空格不是必要的：<br><br>
行内代码是使用`符号`来实现的。

## 如何插入图片？
这里借用我在项目 [基于 FPGA 的超声波测距雷达](https://github.com/MongooseOrion/UltraSonic-Design_based-on-FPGA/) 中的图片。<br><br>
通过插入 HTML 标签可以实现对图片的高级设置：<br>

\<img src="https://github.com/MongooseOrion/UltraSonic-Design_based-on-FPGA/blob/main/v1.1/Picture/%E7%BB%98%E5%9B%BE5.png" width = '300' alt="图片alt" title="波形发生子模块程序设计框图" />（<- 如果两张图片之间想要插入空格，输入 **“ \&nbsp; ”**）<br>
\<img src="https://github.com/MongooseOrion/UltraSonic-Design_based-on-FPGA/blob/main/v1.1/Picture/%E7%BB%98%E5%9B%BE8.png" width = '327' alt="图片alt" title="高速计数子模块程序设计框图" /><br>

通过使用 “width=” 属性可以调整图片的大小，比例不会更改。如果想要两张图片并排放在一起，可以调整好宽度尺寸， markdown 渲染会自动并列放置。<br>

示例 (中间插入 3 个空格，加上它自己渲染 1 个，共 4 个空格)：<br><br>
<img src="https://github.com/MongooseOrion/UltraSonic-Design_based-on-FPGA/blob/main/v1.1/Picture/%E7%BB%98%E5%9B%BE5.png" width = '300' alt="图片alt" title="波形发生子模块程序设计框图" />&nbsp;&nbsp;&nbsp;
<img src="https://github.com/MongooseOrion/UltraSonic-Design_based-on-FPGA/blob/main/v1.1/Picture/%E7%BB%98%E5%9B%BE8.png" width = '327' alt="图片alt" title="高速计数子模块程序设计框图" /><br><br>

## 行间引用和自动编号的语法
在键入 1 个制表位后，markdown 编辑器会识别语法，使用 “>” 可以实现行间引用：
```
  > 中国智造  （两个空格才可以实现换行，或者直接加<br>）
  > 惠及全球  
```
可显示为：
  > 中国智造  
  > 惠及全球  

使用缩进，键入 “\*” 或输入 “1.” 可自动编号：
```
  * 第一点
  * 第二点
  或者：
  1. 第一点
  1. 第二点（只要写一个任意的阿拉伯数字，会自动渲染为有序列表）
```
显示为：
  * 第一点
  * 第二点

或：
  1. 第一点
  1. 第二点

## 注意空格和缩进
根据我的实际体验来讲，Markdown 的语法对空格的要求是比较混乱的。一方面，有些内容渲染必需空格或必须不加空格；另一方面，有些部分则有或者没有空格区别不大。这就导致我有时候写一些很简单的内容就会出一些匪夷所思的问题。

### 基本语法时的情况
  * 加入 “\#” 以调整文本的大纲级别时，井号后的空格**一定需要**，否则不能被识别为标题；<br>
  * 当插入**行内代码** \`this is an example\` 时，符号内和符号外的空格均**不是必要的**，当区域外插入空格则在外渲染一个空格，在代码区域内插入空格则不起效果。例如 `alpha` 和` alpha `；
  * 当插入**行内公式** 时，符号外两边的空格是**必要**的。例如直接键入`$\alpha$`无效，而 `$\alpha$` 就可以正常渲染为 $\alpha$ ，**注意全角符号后接公式也必须加入空格**；
  * 当**编辑列表**时，符号前面**必须有 1 个制表位**，同时符号和后面的文字之间也**必须有空格或者缩进**；
