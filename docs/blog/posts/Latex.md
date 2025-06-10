---
title: LaTeX learning
date: 
  created: 2024-12-26
  updated: 2025-06-02
authors: [Pengyu-Jin]
slug: LaTeX
categories:
  - Research
---

Happy LaTeXing!

<!-- more -->

LateX 本地配置参考文章：

- [LaTeX环境配置 - TexLive](https://blog.csdn.net/BO_S__/article/details/136129229){:target="_blank"}
- [VScode写LaTeX配置](https://zhuanlan.zhihu.com/p/166523064){:target="_blank"}
- [如何优雅地使用 Sublime 编辑 LaTeX](https://zhuanlan.zhihu.com/p/635088283){:target="_blank"}


Windows: sublime + sumatraPDF：

| Shortkey | Function |
| --- | --- |
| ++ctrl+l++, then ++j++ | forward search |
| double click | reverse search |
| ++ctrl+l++, then ++backspace++ | clear tmp files |
| ++ctrl+k++, then ++ctrl+b++ | open/close sidebar |

Windows: VSCode + sumtraPDF

| Shortkey | Function |
| --- | --- |
| ++ctrl+alt+j++ | forward search |
| double click | reverse search |
| ++ctrl+alt+c++ | clear tmp files |
| ++ctrl+alt+v++| open and view the pdf|

!!! bug

    You can not just change the option setting through SumatraPDF application GUI. You must modify the   `SumatraPDF-settings.txt` file in the installation directory following the guide in LaTeX-Workshop wiki. 

    [SumatraPDF inverse search did not work well for VSCode.exe/VSCodium.exe](https://github.com/James-Yu/LaTeX-Workshop/wiki/View#using-synctex-with-an-external-viewer){:target="blank"}

## Roadmap

\(\LaTeX{}\)的学习从阅读overleaf的完整教程开始

YouTuber creation： [LaTeX Cheat Sheet](https://www.newthinktank.com/2019/01/latex-tutorial/){:target="_blank"}

## LaTeX syntax tips 

!!! tip "math code"

    === "inline math"
        内置功能：`\( ... \)`, `$ ... $`, `\begin{math} ... \end{math}`
    
    === "display math"
        内置功能： `\[ ... \]`, `$$ ... $$`, `\begin{displaymath} ... \end{displaymath}`

        amsmath package提供：

        - `\begin{equation*} ... \end{equation*}`, `\begin{equation} ... \end{equation}`(编号)
        - `\begin{align*} ... \end{align*}`, `\begin{align} ... \end{align}`(编号)

        ✨ equation仅支持单行公式；align支持多行公式，可以通过`&`指定对齐位置，但是每行都有编号。

        ✨ pairs of dollar sign is no longer recommended: [Why use `\[...\]` in place of `$$...$$`?](https://texfaq.org/FAQ-dolldoll){:target="_blank"}

        实现多行公式，但只有一个编号：
        
        ```latex
        \begin{equation}
          \begin{aligned}
            a &= b + c \\
            &= d + e + f \\
          \end{aligned}
        \end{equation}
        ```

### fonts

|typeface = family| manual setup command | application| remark|
|---|---|---|---|
|serif (roman)| `\setmainfont` | 正文字体|mostly in the `article`|
|sans serif | `\setsansfont` | 标题/强调, like `\section`,`\title`|by default `beamer` uses the sans serif font throughout the document.|
|typewriter (monospace) | `\setmonofont` | 代码|/|


- 可调用的字体族(familyfont)
    * zhsong
    * zhhei
    * zhkai
    * zhfs

=== "font settings"

    ```latex
    \defaultfontfeatures{Path=fonts/}

    \setmainfont{Cascadia Code}[
      UprightFont    = *-Regular,
      BoldFont       = *-Bold,
      ItalicFont     = *-Italic,
      BoldItalicFont = *-BoldItalic,
    ]
    \setsansfont{Arial}
    \setmonofont{Courier New}
    ```

=== "CN font settings"

    ```latex
    % 设置字体路径
    \defaultfontfeatures{Path=fonts/}

    % 设置中文字体
    \setCJKmainfont[
      AutoFakeBold = 3,
      ItalicFont   = simkai.ttf
    ]{simsun.ttc}
    \setCJKsansfont[AutoFakeBold=3]{simhei.ttf}
    \setCJKmonofont{simfang.ttf}
    \setCJKfamilyfont{zhsong}{simsun.ttc}[
      AutoFakeBold = 3,
      ItalicFont   = simkai.ttf
    ]
    \setCJKfamilyfont{zhhei}{simhei.ttf}[AutoFakeBold=3]
    \setCJKfamilyfont{zhkai}{simkai.ttf}
    \setCJKfamilyfont{zhfs}{simfang.ttf}

    \newcommand*{\songti}{\CJKfamily{zhsong}}
    \newcommand*{\heiti}{\CJKfamily{zhhei}}
    \newcommand*{\kaishu}{\CJKfamily{zhkai}}
    \newcommand*{\fangsong}{\CJKfamily{zhfs}}
    ```

## Document Class Templates

### note📒

参考UC Berkeley的CS61A课程的discussion模板

[Teemu's TU Delft LaTeX Template](https://github.com/temeweckis/tu-delft-latex-template){:target="_blank"}

### beamer🅱️

| Template                                       | Link or Reference                                                                                                                                                                                                                                                                                                                        |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| color and theme configuration                  | [beamer matix](https://mpetroff.net/files/beamer-theme-matrix/){:target="_blank"}                                                                                                                                                                                                                                                        |
| SJTU theme                                     | [SJTUBeamer](https://github.com/sjtug/SJTUBeamer){:target="_blank"}                                                                                                                                                                                                                                                                      |
| UBC(University of British Columbia) blue theme | <ul><li>[Reference1: How to Quickly Change Beamer Colors -- Adam Noel](https://ramblingacademic.com/2015/12/08/how-to-quickly-overhaul-beamer-colors/#more-2470){:target="_blank"}</li><li>[Reference2: 简洁大方的 Latex Beamer 模板分享 -- Andrew的仓库](https://mp.weixin.qq.com/s/mOrMdd_mV6sKzgiVpLJoHg){:target="_blank"}</li></ul> |
| Northwestern University theme| [wildcat: A modern, highly customizable beamer theme. -- Aaron Wolf](https://github.com/aarondwolf/wildcat){:target="_blank"}|

### book📘

| Template | Link or Reference  |
| --- | --- |
| Beautybook | <ul><li>[Reference1: A very Beautiful LaTeX Book Template, Happy LaTeXing!](https://github.com/BeautyLaTeX/Beautybook){:target="_blank"}</li><li>[Reference2: live-in-xjtu-medical-school西安交通大学医学部生活指南](https://github.com/echore/live-in-xjtu-medical-school?tab=readme-ov-file){:target="_blank"}</li></ul> |

## Mathmatical symbols fonts

`\mathcal`: calligraphic. 通常用来表示集合、函数空间等. $\LaTeX{}$默认支持，无需external package.

$$
\mathcal{A}, \mathcal{B}, \mathcal{C}, \mathcal{D}, \mathcal{E}, \mathcal{F}, \mathcal{G}, \mathcal{H}, \mathcal{I}, \mathcal{J}, \mathcal{K}, \mathcal{L}, \mathcal{M}, \mathcal{N}, \mathcal{O}, \mathcal{P}, \mathcal{Q}, \mathcal{R}, \mathcal{S}, \mathcal{T}, \mathcal{U}, \mathcal{V}, \mathcal{W}, \mathcal{X}, \mathcal{Y}, \mathcal{Z}
$$

```latex
\mathcal{A}, \mathcal{B}, \mathcal{C}...
```

`\mathbb`: blackboard bold. 通常用于表示常见的数学集合，例如实数集$\mathbb{R}$、整数集$\mathbb{Z}$、自然数集$\mathbb{N}$等. 在preamble中需要加载 amsfonts 或 amssymb 包来支持.

$$
\mathbb{A}, \mathbb{B}, \mathbb{C}, \mathbb{D}, \mathbb{E}, \mathbb{F}, \mathbb{G}, \mathbb{H}, \mathbb{I}, \mathbb{J}, \mathbb{K}, \mathbb{L}, \mathbb{M}, \mathbb{N}, \mathbb{O}, \mathbb{P}, \mathbb{Q}, \mathbb{R}, \mathbb{S}, \mathbb{T}, \mathbb{U}, \mathbb{V}, \mathbb{W}, \mathbb{X}, \mathbb{Y}, \mathbb{Z}
$$

```latex
\mathbb{A}, \mathbb{B}, \mathbb{C}...
```



## Package management

=== "preamble"

    ```latex
    \usepackage{amsmath}
    \usepackage{amssymb}
    \usepackage{graphicx}
    \graphicspath{{figures/}}
    \usepackage{float}
    \usepackage{geometry}
    \geometry{margin=1in}
    \usepackage{hyperref}
    ```



## Edit Tips

LaTeX中常见的空格命令

| 命令 | 名称 | 宽度（近似） | 典型用途 |
|---|---|---|---|
| `\,` | 小空格 thin space   | 1/6 em[^1]| 单位符号，公式中的轻微间距 |
| `␣`  | 普通空格            | 1 em  | 文本中的常规空格（可能被忽略）|
| `\␣` | 强制空格            | 1 em  | 确保不被忽略的空格 |
| `\:` | 中空格 medium space | 2/9 em| 数学模式中的中等间隔 |
| `\;` | 大空格 thick space  | 5/18 em| 数学模式中的较大间隔 |
| `~`  | 不可换行空格         | 1 em  |  保证词组不分开（如"Fig.~1"）|
| `\quad`| 1 em 空格          | 1 em  | 较大的固定间隔（如分割文本）|
| `\qquad`      | 2 em 空格          | 2 em          | 更大的固定间隔               |
| `\hspace{长度}`| 自定义空格         | 任意指定      | 精确控制间距（如`\hspace{5pt}`）|

[^1]: An em (from em quadrat) is a unit in the field of typography, equal to the currently specified point size. It corresponds to the body height of the typeface. For example, one em in a 16-point typeface is 16 points. Therefore, this unit is the same for all typefaces at a given point size.