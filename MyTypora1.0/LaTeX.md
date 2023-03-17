# LaTeX基本认识

## LaTeX基本格式

选择 *XeLaTeX*

```latex
\documentclass[UTF8]{ctexant}
\title{你的文章标题}
\date{\today}

\begin{document}
\maketitle
\end{document}
```

LaTeX文档分为两个区域：**导言区**（前言）和**正文区**（文档区）

1. **导言区**

	```latex
	\doucument[UTF8]{ctexart}
	```
	
	即
	
	```latex
	\doucument{class}
	```
	
	（引入一个文档类）
	
	其中class类有很多：book, article, report, letter, beamer(幻灯片格式文档)
	
	如果文档中有中文，就要用ctexart的文档类型。它支持中英文混排，还要指定文档编码类型UTF8
	
	| 英文类  | 中英类   |
	| ------- | -------- |
	| article | ctexart  |
	| report  | cetxrep  |
	| book    | ctexbook |
	
	推荐使用XeLaTeX和LuaLaTeX编译
	
	```latex
	\title{你的文章标题}
	```
	
	（显示文章标题）
	
	```latex
	\author{作者的名称}
	```
	
	（显示文章作者）
	
	```latex
	\date{日期}
	```
	
	例
	
	```latex
	\date{\today} (当日日期)
	```
	
	（编辑文档的日期）

2. **正文区**

	```latex
	\begin{环境名称}
	```
	
	   （ **正文写在此处**。正文与正文所需要的命令都应写在这两个命令之间）
	
	```latex
	\end{环境名称}
	```
	
	环境的名称一般为document
	
	一个LaTeX文件有且只能有一个document环境
	
	```latex
	\maketitle
	```
	
	调用导言区中的标题。作者名称、日期等。
	
	此命令不能用于letter类

## LaTeX常用指令

1. 加粗文字

	```latex
	\textbf{}
	```

2. 斜体

	```latex
	\textit{}
	```

   3. 下划线

	```latex
	\underline{}
	```

   4. 章节

	```latex
	\section
	```

   5. 子章节

	```latex
	\subsection
	```

   6. 注释

	```latex
	%
	```

	百分号为LaTeX里的注释符号

	表示%后一行的内容将被注释

## LaTeX数学公式

​     <------文本模式------> $$ $ <---数学模式---> $$$ <-----文本模式----->

在美元符号之间称为数学模式，用于输入数学公式。而美元符号之外则为正常的文本模式

在LaTeX，单美元符号表示行内模式。双美元符号表示行间模式



```latex
\begin{equation}
```

（此环境用于表示带编号的行间公式）

```latex
\end{equation}
```



1. 蕴含

	```latex
	\rightarrow
	```
	
	或
	
	```latex
	\to
	```

2. 等价

	```latex
	\leftarrow
	```

3. 小于等于

	```latex
	\legslant
	```

4. 大于等于

	```latex
	\geqslant
	```

5. 否定

	```latex
	\neg
	```

6. 任意

	```latex
	\forall
	```

7. 存在

	```latex
	\exists
	```

8. 合取

	```latex
	\cup
	```

9. 析取

	```latex
	\cap
	```

# LaTeX的字体

LaTeX有5种字体属性：

1. 字体编码

	1. 正文字体编码：OTI, TI, EUI
	2. 数学字体编码：OML, OMS, OMX

2. 字体族

	罗马字体、无衬线字体、打字机字体

3. 字体系列

	粗细、宽度

4. 字体形状

	直立、斜体、伪斜体、小型大写

5. 字体大小

## 字体族

1. 罗马字体

	```latex
	\textrm{Roman Family}
	```
	
	字体声明：
	
	```latex
	\rmfamily
	```

2. 无衬线字体

	```latex
	\textsf{Sans Serif Family}
	```
	
	字体声明：
	
	```latex
	\sffamily
	```

3. 打字机字体

	```latex
	\texttt{Typewriter Family}
	```
	
	字体声明：
	
	```latex
	\ttfamily
	```

字体声明（字体声明后的内容都会以该字体展示。可以使用大括号括起来以限制其范围）

## 字体系列设置

1. ?

	```latex
	\textmd{Medium Series}
	```
	
	字体声明：
	
	```latex
	\mdseries
	```

2. 加粗

	```latex
	\textbf{Boldface Series}
	```
	
	字体声明：
	
	```latex
	\bfseries
	```

## 字体形状

1. 直立

	```latex
	\textup{Upright Shape}
	```
	
	字体声明：
	
	```latex
	\upshape
	```

2. 斜体

	```latex
	\textit{Italic Shape}
	```
	
	字体声明：
	
	```latex
	\itshape
	```

3. 伪斜体

	```latex
	\textsl{Slanted Shape}
	```
	
	字体声明：
	
	```latex
	\slshape
	```

4. 小型大写

	```latex
	\textsc{Small Caps Shape}
	```
	
	字体声明：
	
	```latex
	\scshape
	```

## 中文字体声明

1. 宋体

	```latex
	\songti
	```

2. 楷书

	```latex
	\kaishu
	```

3. 黑体

	```latex
	\heiti
	```

4. 仿宋

	```latex
	\fangsong
	```

中文中粗体是用黑体表示，斜体由楷书表示

## 字体大小

**皆有声明表示**

从小到大排序:

```latex
\tiny          小
\sciptsize
\footnotesize
\small
\normalsize    大
```

```latex
\large         小
\Large
\LARGE
\huge
\Huge          大
```

# LaTeX的篇章结构

## 构建文章小节

（制作提纲、目录等）

```latex
\section{}
	\subsection{}
		\subsubsection{}
```

正文格式不会受到以上三个命令影响

## 换行

反斜杠命令（只是换行，没有缩进）

```latex
a\\b
```

效果：

```pdf
a
b
```

## 新段落

1. paragraph命令

	```latex
	\par
	```

2. 空行（两次回车）

## 创建章节

```latex
\chapter{}
```

## 生成目录

```latex
\tableofcontents
```

# LaTeX中的特殊字符

1. 空白符号
2. LaTeX控制符
3. 排版符号
4. 标志符号
5. 引号
6. 连字符
7. 非英文符号
8. 重音符号

## 空白符号

（空格，空行）

1. **空行分段，多个空行等同于一个**

2. 自动缩进。绝对不能用空格代替

3. **英文中的多个空格处理为1个空格**

	**中文中空格将被忽略**

4. 汉字与其他字符的间距会自动处理

5. 禁止使用汉字全角空格

###  产生空白字符

1. 产生1em宽度的空白（1em为当前字体中M的宽度）

	```latex
	\quad
	```
	
	```latex
	a\quad b
	```

2. 产生2em宽度的空白

	```latex
	\qquad
	```
	
	```latex
	a\qquad b
	```

3. 产生1/6em宽度的空白

	```latex
	\,
	\thinspace
	```
	
	```latex
	a\, b
	a\thinspace b
	```

4. 产生1/2em宽度的空白

	```latex
	\enspace
	```
	
	```latex
	a\enspace b
	```

5. 产生一个空格

	```latex
	a\ b
	```

6. 产生一个硬空格（不能分割的空格）

	```latex
	~
	```
	
	```
	a~b
	```

7. 产生指定宽度的空白

	```latex
	\kern
	\hspace{}
	```
	
	```latex
	a\kern 1pc b
	a\hspace{pt} b
	```
	
	(1pc = 12pt = 4.218mm)

8. 占位宽度

	```latex
	\hphanton{}
	```

9. 产生弹性长度的空白

	```latex
	\hfill
	```

## LaTeX控制符

1.  \ #
2.  \ $
3.  \ %
4.  \ {
5.  \ }
6.  \ __{}
7.  \ ~{}
8.  \ ^{}

## 排版符号

\ S --> （打不出来，可以网上查）

## LaTeX标志符号

1. ```latex

	\TeX{}
	```

2. ```latex

	\LaTeX{}
	```

3. ```latex

	\LaTeXe{}
	```

## 引号

1. 单个撇号表示左单引号（1左边，Esc下面的那个撇号）

	```latex
	`
	```

2. 单引号字符表示右单引号

	```latex
	'
	```

3. 两个撇号表示左双引号

	```latex
	``
	```

4. 两个单引号字符表示右双引号

	```latex
	''
	```

## 连字符

1. -

2. --

3. $---$

	（分别生成短、中、长三种连字符）

# LaTeX中的插图

于导言区：

```latex
\usepackage{graphicx}
\graphicspath{{file/}}
```

于正文区插入图片：

```latex
\includegraphics[参数]{文件名}
```

其中[参数]为缩放因子，用于调整图片大小（长、宽、高）

1. scale 长
2. width 宽
3. height 高
4. angle 旋转角度

**注意，file文件是图片所在文件夹名，且此文件夹要与LaTeX文件在同一级内（同一文件夹）**

例：

```latex
\includegraphics[scale = 0.1]{Klose}
```

**可以多个参数共同作用，多个参数用逗号分开**

```latex
\includegraphics[width = 0.5\textwidth]{Klose}
```

此处\textwidth表示当前文档的宽度，即指定相对宽度
