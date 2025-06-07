# Radon In Python For Code Metrics

_This document covers my usage of the Python package radon, for code metrics._

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
Current Date: 2025-06-06
```

</details>

Description:

> Radon is a Python tool that computes various metrics from the source code. Radon can compute:
>
> * McCabe's complexity, i.e. cyclomatic complexity
> * raw metrics (these include SLOC, comment lines, blank lines, &c.)
> * Halstead metrics (all of them)
> * Maintainability Index (the one used in Visual Studio)

Useful Links:

* Radon Documentation Site: <https://radon.readthedocs.io/en/latest/intro.html>
* Radon GitHub Page: <https://github.com/rubik/radon>

Outline Of Reasoning:

* Code metrics seem helpful.
* Using `radon` does not seem difficult.
  * Code metrics from `radon` seem as though they can be automatically used via a `pre-commit` hook.
  * As per [this comment](https://github.com/rubik/radon/issues/225#issuecomment-1236058304), `xenon` is `radon`-based and fashioned as a `pre-commit` hook.

I intend to use `radon` manually, on occasion, and mostly use `xenon` for automated monitoring of code metrics in my repositories that use Python.

Terms And Definitions From Radon's Site (2025-06-06):

> Cyclomatic Complexity corresponds to the number of decisions a block of code contains plus 1. This number (also called McCabe number) is equal to the number of linearly independent paths through the code.

| Construct | Effect on CC  | Reasoning
| --- | --- | --- |
| `if` | 	 +1 	| An if statement is a single decision.|
| `elif` 	| +1 	| The elif statement adds another decision.|
| `else` 	| +0 	| The else statement does not cause a new decision. The decision is at the if.|
| `for` 	| +1 	| There is a decision at the start of the loop.|
| `while` 	| +1 	| There is a decision at the while statement.
| `except` 	| +1 	| Each except branch adds a new conditional path of execution.|
| `finally` | 	+0 	| The finally block is unconditionally executed.|
| `with` 	| +1 	| The with statement roughly corresponds to a try/except block (see PEP 343 for details).|
| `assert` 	| +1 	| The assert statement internally roughly equals a conditional statement.|
| Comprehension 	| +1 | 	A list/set/dict comprehension of generator expression is equivalent to a for loop.|
| Boolean Operator | 	+1 | 	Every boolean operator (and, or) adds a decision point.|

> Maintainability Index is a software metric which measures how maintainable (easy to support and change) the source code is. The maintainability index is calculated as a factored formula consisting of SLOC (Source Lines Of Code), Cyclomatic Complexity and Halstead volume.

Original Formula:

$$ \text{MI} = 1.71 - 5.2 \ln 0.23 G - 16.2 \ln L$$

Derivative Used (SEI):

$$ \text{MI} = 171 - 5.2 \log_2 V  - 0.23 G - 16.2 \log_2 L + 50 \sin(\sqrt{2.4C})$$

> $V$ is the Halstead Volume (see below);
> $G$ is the total Cyclomatic Complexity;
> $L$ is the number of Source Lines of Code (SLOC);
> $C$ is the percent of comment lines (important: converted to radians).


> The following are the definitions employed by Radon:
>
> * LOC: The total number of lines of code. It does not necessarily correspond to the number of lines in the file.
> * LLOC: The number of logical lines of code. Every logical line of code contains exactly one statement.
> * SLOC: The number of source lines of code - not necessarily corresponding to the LLOC.
> * Comments: The number of comment lines. Multi-line strings are not counted as comment since, to the
> * Multi: The number of lines which represent multi-line strings.
> * Blanks: The number of blank lines (or whitespace-only ones).
>
> The equation SLOC + Multi + Single comments + Blank = LOC should always hold. Additionally, comment stats are calculated:
>
> * `C % L`: the ratio between number of comment lines and LOC, expressed as a percentage;
> * `C % S`: the ratio between number of comment lines and SLOC, expressed as a percentage;
> * `C + M % L`: the ratio between number of comment and multiline strings lines and LOC, expressed as a percentage.

> Halstead Metrics
>
> $\eta_1$ = the number of distinct operators
> $\eta_2$ = the number of distinct operands
> $N_1$ = the total number of operators
> $N_2$ = the total number of operands
>
> From these numbers several measures can be calculated:
>
> Program vocabulary: $\eta = \eta_1 + \eta_2$
> Program length: $N = N_1 + N_2$
> Calculated program length: $\widehat{N} = \eta_1 \log_2 \eta_1 + \eta_2 \log_2 \eta_2$
> Volume: $V = N \log_2 \eta$
> Difficulty: D = $\dfrac{\eta_1}{2} \cdot \dfrac{N_2}{\eta_2}$
> Effort: $E = D \cdot V$
> Time required to program: $T = \dfrac{E}{18}$ seconds
> Number of delivered bugs: B = $\dfrac{V}{3000}$.


Installation:

`pip3 install radon`


Usage:

```
usage: radon [-h] [-v] {cc,raw,mi,hal} ...

positional arguments:
  {cc,raw,mi,hal}
    cc             Analyze the given Python modules and compute Cyclomatic Complexity (CC).
    raw            Analyze the given Python modules and compute raw metrics.
    mi             Analyze the given Python modules and compute the Maintainability Index.
    hal            Analyze the given Python modules and compute their Halstead metrics.

options:
  -h, --help       show this help message and exit
  -v, --version    show program's version number and exit
```

Usage Example:

```
radon cc ./guides/contributions/analyze_github_contributions.py
```

```
./guides/contributions/analyze_github_contributions.py
    F 96:0 group_by_interval - B
    F 188:0 plot_horizontal_bar_chart - A
    F 112:0 plot_over_time - A
    F 175:0 plot_pie_chart - A
    F 146:0 plot_proportion - A
```
