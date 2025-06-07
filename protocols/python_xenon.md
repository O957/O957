# Xenon In Python For Code Metrics

_This document covers my usage of the Python package xenon, for code metrics._

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
Current Date: 2025-06-07
```

</details>

Description:

> Xenon is a monitoring tool based on Radon. It monitors your code's complexity. Ideally, Xenon is run every time you commit code. Through command line options, you can set various thresholds for the complexity of your code. It will fail (i.e. it will exit with a non-zero exit code) when any of these requirements is not met.

See the [radon protocol](https://github.com/AFg6K7h4fhy2/AFg6K7h4fhy2/blob/main/protocols/python_radon.md) file for more information.

Useful Links:

* Xenon GitHub Page: <https://github.com/rubik/xenon>
* Radon Documentation Site: <https://radon.readthedocs.io/en/latest/intro.html>
* Radon GitHub Page: <https://github.com/rubik/radon>

Installation:

`pip3 install xenon`

Usage As Pre-Commit Hook:

```yaml
###############################################################################
# XENON CODE COMPLEXITY
###############################################################################
-   repo: https://github.com/rubik/xenon
    rev: v0.9.0
    hooks:
    -   id: xenon
        args: [
            # threshold for the average complexity
            # (across all the codebase).
            "--max-absolute=B",
            # threshold for modules complexity.
            "--max-modules=B",
            # absolute threshold for block complexity.
            "--max-average=A"
        ]
```
