# LaTeX Math Formatting Guidelines

When writing or translating Markdown files with KaTeX/MathJax support (such as MkDocs Material), do **not** use `\\` for line breaks inside multi-line math environments like `\begin{aligned}`, `\begin{cases}`, etc. The markdown parser might improperly escape or swallow the backslashes before they reach the math renderer.

Instead, you must use **`\cr`** as the forced line break command in all such math environments. 

Example:
```latex
\begin{aligned}
A &= B \cr
C &= D
\end{aligned}
```
