# LaTeX 中的浮动体：处理超宽问题



这里有四种解决办法！



## 缩小

使用了 `graphicx` 宏包。

```latex
\documentclass{article}

\usepackage{showframe} % 【莫名其妙的不知道干什么的包】
\usepackage{graphicx} % 这个宏包可以用来调整Figure或者Table的大小。

\begin{document}


%% 创建表格 浮动体
\begin{table}[!htb]

\centering % 【卧槽，这个centering 又是哪冒出来的？】
\caption{Oh, this table is overfull!}\label{tab:overfull}%label后面的{}。是给这个表或者图命名，方方便其它地方引用。caption{}后面的才是表或者图的名字。
\rule{1.1\linewidth}{3cm} % 创建一个3cm宽的长方体

\end{table}
 
%% 创建表格 浮动体
\begin{table}[!htb]

\centering
\caption{Imagine that this is a table.}\label{tab:resized}
\resizebox{\linewidth}{!}{\rule{1.1\linewidth}{3cm}}%使用了graphicx 宏包中的 \resizebox处理了过宽的现象。

\end{table}

%% 创建图片 浮动体
\begin{figure}[!htb]

\centering
\includegraphics[width = \linewidth]{example-image} %includegraphics就是include-graphics。{这里是同名文件夹下的图片名}
%\includegraphics[width = .8\textwidth]{a.jpg} 图片的宽度会被缩放至页面宽度的百分之八十
%使用width = \linewidth的参数将图片缩放到正好填满页面宽度的大小
\caption{A fit figure.}\label{fig:example-image}

\end{figure}
%%结束图片 浮动体


\end{document}
```

<img src="https://liam.page/uploads/images/LaTeX/overfull_01.png" alt="用缩小的办法处理超宽的内容" style="zoom: 50%;" />

> 表格内容缩小后，可能看不清。

## 居中

>  内容无法居中的原因：LaTeX 在水平方向，会贴着版芯的左边边界，开始排列内容。

使用了 `\leftskip` 宏包，这是LaTeX默认加载的。不需要载入。

此外还有和`\rightskip` 宏包，确定水平方向排版的终止位置与版芯右边界之间的距离。

两个宏包可以理解为有以下功能：

- 默认情况，应该贴着两侧边界；
- 最差的情况，应该允许内容向左右两侧延伸，超过版芯但不超过纸张宽度；
- 同时具有让内容居中的能力。

默认情况下，LaTeX 将从版芯的左边边界处开始排列内容。



```latex
\documentclass{article}

\usepackage{showframe}
\usepackage{graphicx}

\begin{document}

%%创建表格 浮动体
\begin{table}[!htb]%依然是浮动体

\centering
\caption{Oh, this table is overfull!}\label{tab:overfull}
\setlength{\leftskip}{-20pt} %从版芯左边边界左边的 20pt 的位置开始排列内容
\rule{1.1\linewidth}{3cm} %3cm高的长方体。

\end{table}
%%结束创建表格 浮动体

\end{document}
```

## 使用 `adjustbox` 宏包





## 超大的图，旋转90°

使用`rotating` 宏包。

> `rotating` 宏包默认将内容逆时针旋转了 90°，可以在调用宏包时传入 `clockwise` 参数，得到顺时针旋转的版本。

```latex
\documentclass{article}

\usepackage{showframe}
\usepackage{rotating}

\begin{document}
%%插入sideways表格
\begin{sidewaystable}[!htb] %这是rotating 宏包提供的 sidewaystable环境。【在这个环境下，应该生成的正常图形表格都会旋转90°】

\centering
\caption{Let's rock!}\label{tab:rotated}  %label后面的{}。是给这个表或者图命名，方方便其它地方引用。caption{}后面的才是表或者图的名字。
\rule{0.8\linewidth}{3cm} %这里使用 0.8\linewidth 实际上是相对版芯的高度的 0.8 倍。

\end{sidewaystable}
%%结束插入sideways表格

\end{document}
```

<img src="https://liam.page/uploads/images/LaTeX/overfull_04.png" alt="旋转、跳跃，我闭着眼" style="zoom:50%;" />



参考学习：https://liam.page/2017/03/22/floats-in-LaTeX-handle-overfull-floats/
