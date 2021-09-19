LateX 学习

#### 专业词汇

**控制序列（或称命令/标记）**： 以反斜杠 `\` 开头，以第一个***空格或非字母\*** 的字符结束的一串文字。它们不被输出，但是他们会影响输出文档的效果。`{article}` 代表这个控制序列有一个必要的参数。

> 分控制序列还有被方括号 `[]` 包括的可选参数。

**宏包** ： 一系列控制序列的合集。这些控制序列太常用，以至于人们会觉得每次将他们写在导言区太过繁琐，于是将他们打包放在同一个文件中，成为所谓的宏包（台湾方面称之为「巨集套件」）。`\usepackage{}` 可以用来调用宏包。

> `CTeX` 宏集的优势在于，它能适配于多种编译方式；在内部处理好了中文和中文版式的支持



## 标准实际案例：

```latex
\documentclass[UTF8]{ctexart} % 调用宏，实现支持中英文
% 这里是导言区 ：对整篇文档进行设置的区域。设置页面大小、页眉页脚样式、章节标题样式等等。

\usepackage{amsmath} %导言区加载 amsmath 宏包：用于编写数学公式。


\title{你好，world!} % 标题
\author{Liam} % 作者
\date{\today} % 日期

% 导言区 在documentclass{article}与begin{document}之间

\begin{document}
\maketitle % 这个控制序列能将在导言区中定义的标题、作者、日期按照预定的格式展现出来。

\tableofcontents % 插入目录 
%\maketitle如果在\tableofcontents后面，那么会自动将目录页与正文分开。

% 环境：两个控制序列之间的内容。
\section{你好中国} %一级节。标题：你好中国。转译后： 1.你好中国
中国在East Asia.
\subsection{Hello Beijing} %二级节。标题：Hello Beijing。转译后： 1.1 Hello Beijing
北京是capital of China.
\subsubsection{Hello District}%三级节。标题：转译后： 1.1.1 Hello District

\paragraph{Tian'anmen Square} %三级节下的一级段落。段落开头加粗语句Tian'anmen Square。
\subparagraph{Chairman Mao}% is in the center of 天安门广场。

\subsection{Hello 山东} %二级节。标题：Hello 山东。转译后： 1.2 Hello 山东

Einstein 's $E=mc^2$. % 使用 $ ... $ 可以插入行内公式


\[ E=mc^2. \] % 插入行间公式

\begin{equation}
\[ z = r\cdot e^{2\pi i}. \]   %自动对着行间公式进行编号。上标或者下标如果想对连续的几个字符起作用，请将这些字符用花括号 {} 括起来。
\end{equation}


\end{document}
```

> 在`report`/`ctexrep`中，还有`\chapter{·}`；在文档类`book`/`ctexbook`中，还定义了`\part{·}`。

这里提一下关于公式标点使用的规范。行内公式和行间公式对标点的要求是不同的：行内公式的标点，应该放在数学模式的限定符之外，而行间公式则应该放在数学模式限定符之内

#### 公式

根式用 `\sqrt{·}` 来表示，分式用 `\frac{·}{·}` 来表示（第一个参数为分子，第二个为分母）。

```latex
\[ \pm\; \times \; \div\; \cdot\; \cap\; \cup\;
\geq\; \leq\; \neq\; \approx \; \equiv \] %一些小的运算符，可以在数学模式下直接输入
```

连加、连乘、极限、积分等大型运算符分别用 `\sum`, `\prod`, `\lim`, `\int` 生成。他们的上下标在行内公式中被压缩，以适应行高。我们可以用 `\limits` 和 `\nolimits` 来强制显式地指定是否压缩这些上下标。

多重积分可以使用 `\iint`, `\iiint`, `\iiiint`, `\idotsint` 等命令输入

```latex
\documentclass{article}
\usepackage{amsmath}
\begin{document}
$\sqrt{x}$, $\frac{1}{2}$.
% %平方根；分式
\[ \sqrt{x}, \]
\[ \frac{1}{2}. \]
% %

$ \sum_{i=1}^n i\quad \prod_{i=1}^n $
$ \sum\limits _{i=1}^n i\quad \prod\limits _{i=1}^n $
\[ \lim_{x\to0}x^2 \quad \int_a^b x^2 dx \]
\[ \lim\nolimits _{x\to0}x^2\quad \int\nolimits_a^b x^2 dx \]

% %多重积分
\[ \iint\quad \iiint\quad \iiiint\quad \idotsint \]
% %
\end{document}
```

### 符号（定界符、省略号等）

```latex
%% 1.定界符（括号）
\[ \Biggl(\biggl(\Bigl(\bigl((x)\bigr)\Bigr)\biggr)\Biggr) \]\[ \Biggl[\biggl[\Bigl[\bigl[[x]\bigr]\Bigr]\biggr]\Biggr] \]\[ \Biggl \{\biggl \{\Bigl \{\bigl \{\{x\}\bigr \}\Bigr \}\biggr \}\Biggr\} \]\[ \Biggl\langle\biggl\langle\Bigl\langle\bigl\langle\langle x\rangle\bigr\rangle\Bigr\rangle\biggr\rangle\Biggr\rangle \]\[ \Biggl\lvert\biggl\lvert\Bigl\lvert\bigl\lvert\lvert x\rvert\bigr\rvert\Bigr\rvert\biggr\rvert\Biggr\rvert \]\[ \Biggl\lVert\biggl\lVert\Bigl\lVert\bigl\lVert\lVert x\rVert\bigr\rVert\Bigr\rVert\biggr\rVert\Biggr\rVert \]

%% 2.省略号
\[ x_1,x_2,\dots ,x_n\quad 1,2,\cdots ,n\quad
\vdots\quad \ddots \]

%% 3.矩阵
\[ \begin{pmatrix} a&b\\c&d \end{pmatrix} \quad
\begin{bmatrix} a&b\\c&d \end{bmatrix} \quad
\begin{Bmatrix} a&b\\c&d \end{Bmatrix} \quad
\begin{vmatrix} a&b\\c&d \end{vmatrix} \quad
\begin{Vmatrix} a&b\\c&d \end{Vmatrix} \]
%行内公式的小矩阵。
Marry has a little matrix $ ( \begin{smallmatrix} a&b\\c&d \end{smallmatrix} ) $.
%% 4.多行公式
%长公式——不对齐
\begin{multline}
x = a+b+c+{} \\
d+e+f+g
\end{multline}
%长公式——对齐
\[\begin{aligned}
x ={}& a+b+c+{} \\
&d+e+f+g
\end{aligned}\]
%%5.公式组
\begin{gather}
a = b+c+d \\
x = y+z
\end{gather}
\begin{align}
a &= b+c+d \\
x &= y+z
\end{align}
%%6.分段函数
\[ y= \begin{cases}
-x,\quad x\leq 0 \\
x,\quad x>0
\end{cases} \]
```

1. 定界符（括号）

<img src="https://liam.page/uploads/teaching/LaTeX/figures/818901c1jw1e44jk66wwfj204x0a4aa0.jpg" alt="img" style="zoom:50%;" />

2. 省略号

​																	

![image-20210919191136831](C:\Users\mqc\AppData\Roaming\Typora\typora-user-images\image-20210919191136831.png)

3.  矩阵

![img](https://liam.page/uploads/teaching/LaTeX/figures/818901c1jw1e44jpqbz2aj208k024744.jpg)

​		行内公式的小矩阵	

![img](https://liam.page/uploads/teaching/LaTeX/figures/818901c1jw1e44jsd9ldbj20680200si.jpg)

4. 多行公式

   长公式——不对齐

   ![img](https://liam.page/uploads/teaching/LaTeX/figures/818901c1jw1e44jzfychej20dv02sjr6.jpg)

    长公式——对齐

   ![img](https://liam.page/uploads/teaching/LaTeX/figures/818901c1jw1e44k2acde4j205g02ft8h.jpg)

5. 公式组
   ![img](https://liam.page/uploads/teaching/LaTeX/figures/818901c1jw1e44k5od3xaj209u04lweb.jpg)

6. 分段函数

![img](https://liam.page/uploads/teaching/LaTeX/figures/818901c1jw1e44k7zto1wj205o01pt8i.jpg)



## 插入图片和表格

在 LaTeX 中插入图片，有很多种方式。最好用的应当属利用 `graphicx` 宏包提供的 `\includegraphics` 命令。比如你在你的 TeX 源文件同目录下，有名为 `a.jpg` 的图片，你可以用这样的方式将它插入到输出文档中：

```latex
\documentclass{article}
\usepackage{graphicx}
\begin{document}

%%图片
\includegraphics[width = .8\textwidth]{a.jpg} %输出图片，控制序列的可选参数来控制图片大小。图片的宽度会被缩放至页面宽度的百分之八十，图片的总高度会按比例缩放。

%%表格
\begin{tabular}{|l|c|r|}
 \hline
操作系统& 发行版& 编辑器\\
 \hline
Windows & MikTeX & TexMakerX \\
 \hline
Unix/Linux & teTeX & Kile \\
 \hline
Mac OS & MacTeX & TeXShop \\
 \hline
通用& TeX Live & TeXworks \\
 \hline
\end{tabular}


\end{document}
```

图表效果

![img](https://liam.page/uploads/teaching/LaTeX/figures/818901c1jw1e44ku9n696j20cj05haad.jpg)

# 其它:

### 辅助工具

数学公式的辅助工具。

- https://mathpix.com/ 能够通过热键呼出截屏，而后将截屏中的公式转换成 LaTeX 数学公式的代码。
- http://detexify.kirelabs.org/classify.html 允许用户用鼠标在输入区绘制单个数学符号的样式，系统会根据样式返回对应的 LaTeX 代码（和所需的宏包）。这在查询不熟悉的数学符号时特别有用。

>  
>
> 
>
> 请注意，不要使用 `eqnarray` 环境。原因可以参考：
>
> > - [`eqnarray` 是糟糕的](http://www.math.uiuc.edu/~hildebr/tex/displays.html)
> > - [`eqnarray` 是有害的](http://texblog.net/latex-archive/maths/eqnarray-align-environment/)
> > - [`eqnarray` 是恼人的](http://www.tex.ac.uk/cgi-bin/texfaq2html?label=eqnarray)
> > - [`eqnarray` 是邪恶的](http://www.tug.org/pracjourn/2006-4/madsen/)
>
> ​																

