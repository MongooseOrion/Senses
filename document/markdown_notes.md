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

在代码块的上下行打上三个 “ ``` ” 符号，可渲染围栏式代码块，**注意是制表键上面的那个打 “\`timescale” 的按键**，而不是单引号。<br><br>
**行内引用**可以使用行内公式来实现，例如： `这是一个引用的例子` 可以看到渲染为高亮。

## 如何插入图片？
这里借用我在项目 [基于 FPGA 的超声波测距雷达](https://github.com/MongooseOrion/UltraSonic-Design_based-on-FPGA/) 中的图片。<br><br>
通过插入 HTML 标签可以实现对图片的高级设置：<br>

\<img src="https://github.com/MongooseOrion/UltraSonic-Design_based-on-FPGA/blob/main/v1.1/Picture/%E7%BB%98%E5%9B%BE5.png" width = '300' alt="图片alt" title="波形发生子模块程序设计框图" />（<- 如果两张图片之间想要插入空格，输入 **“ \&nbsp; ”**）<br>
\<img src="https://github.com/MongooseOrion/UltraSonic-Design_based-on-FPGA/blob/main/v1.1/Picture/%E7%BB%98%E5%9B%BE8.png" width = '327' alt="图片alt" title="高速计数子模块程序设计框图" /><br>

通过使用 “width=” 属性可以调整图片的大小，比例不会更改。如果想要两张图片并排放在一起，可以调整好宽度尺寸， markdown 渲染会自动并列放置。<br>

示例 (中间插入 3 个空格，加上它自己渲染 1 个，共4个空格)：<br><br>
<img src="https://github.com/MongooseOrion/UltraSonic-Design_based-on-FPGA/blob/main/v1.1/Picture/%E7%BB%98%E5%9B%BE5.png" width = '300' alt="图片alt" title="波形发生子模块程序设计框图" />&nbsp;&nbsp;&nbsp;
<img src="https://github.com/MongooseOrion/UltraSonic-Design_based-on-FPGA/blob/main/v1.1/Picture/%E7%BB%98%E5%9B%BE8.png" width = '327' alt="图片alt" title="高速计数子模块程序设计框图" /><br><br>

## 注意空格
根据我的实际体验来讲，Markdown 的语法对空格的要求是比较混乱的
