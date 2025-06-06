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
```

</details>

Useful Links:

* Radon Documentation Site: <https://radon.readthedocs.io/en/latest/intro.html>
* Radon GitHub Page: <https://github.com/rubik/radon>

Outline Of Reasoning:

* Code metrics seem helpful.
* Using `radon` does not seem difficult.
  * Code metrics from `radon` seem as though they can be automatically used via a `pre-commit` hook.
  * As per [this comment](https://github.com/rubik/radon/issues/225#issuecomment-1236058304), `xenon` is `radon`-based and fashioned as a `pre-commit` hook.

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

$$ \text{MI} = 1.71 - 5.2 \ln $$
