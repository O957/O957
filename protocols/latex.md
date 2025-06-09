# LaTeX Usage

_This document covers my usage of LaTeX on my Macintosh system._

<details markdown=1>

<summary> Environments & Machine </summary>

```
OS Version: ProductName: macOS
ProductVersion:	13.3.1
BuildVersion: 22E261
Kernel: arm64
Architecture: 22.4.0
CPU Brand: Apple M1
Python Version: Python 3.13.1
UV Version: uv 0.7.3 (3c413f74b 2025-05-07)
Ruby Version: ruby 3.2.3 (2024-01-18 revision 52bb2ac0a6) [arm64-darwin22]
Quarto Version: 1.6.40
Rscript Version: Rscript (R) version 4.4.2 (2024-10-31)
Git Version: git version 2.40.0
Current Date: 2025-06-08
```

</details>

Historically, I have used `pandoc` for more formal documents.

For example, I often copy-paste this header:

<details markdown=1>

<summary> Common Header </summary>

```md
---
title: ""
subtitle: ""
author: ""
date: "2025-01-26"
geometry:
- lmargin=1.0in
- rmargin=1.0in
- tmargin=0.75in
- bmargin=0.75in
parindent: 0
parskip: 15
toc: true
toc-depth: 3
numbersections: true
documentclass: extarticle
fontsize: 14pt
papersize: letter
linkcolor: black
urlcolor: gray
filecolor: magenta
citecolor: cyan
link-citations: true
mainfont: TeX Gyre Schola
header-includes:
- \usepackage{fontspec}
- \usepackage{lettrine}
- \usepackage{fvextra}
- \fvset{fontsize=\small, frame=single,framesep=2mm,rulecolor=\color{black}, breaklines=true, breakanywhere=true, framerule=0.4mm}
- \usepackage{float}
- \let\origfigure\figure
- \let\endorigfigure\endfigure
- \renewenvironment{figure}[1][H]{\origfigure[H]}{\endorigfigure}
- \usepackage{pifont}
- \renewcommand{\labelitemi}{\ding{71}}
- \usepackage{pgfornament}
---

\begin{center}
\hrulefill
\hspace{0.1cm}
\scalebox{0.25}{\pgfornament{8}}
\hspace{0.1cm}
\hrulefill
\end{center}
```

</details>
