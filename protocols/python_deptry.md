# Deptry In Python For Dependency Management

_This document covers my usage of the Python package deptry for ensuring the proper grouping of dependencies in my projects._


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

Description:

> deptry is a command line tool to check for issues with dependencies in a Python project, such as unused or missing dependencies. It supports projects using Poetry, pip, PDM, uv, and more generally any project supporting PEP 621 specification.
>
> Dependency issues are detected by scanning for imported modules within all Python files in a directory and its subdirectories, and comparing those to the dependencies listed in the project's requirements.

Note:

> deptry should be run within the root directory of the project to be scanned, and the project should be running in its own dedicated virtual environment.

Useful Links:

* Deptry Homepage: <https://deptry.com/>
* Deptry Usage And Configuration: <https://deptry.com/usage/>

Installation:

```
pip3 install deptry
```

or

```
uv add deptry --optional dev
```

As Pre-Commit Hook:

```yaml
###############################################################################
# DEPTRY UNUSED DEPENDENCIES
###############################################################################
-  repo: https://github.com/fpgmaas/deptry.git
   rev: "0.23.0" # from https://github.com/fpgmaas/deptry/tags
   hooks:
   # some items from: https://github.com/fpgmaas/deptry/pull/124
   -    id: deptry
        entry: deptry .
        language: system
        args: [
            "--requirements-files",
            "requirements.txt",
            "--pep621-dev-dependency-groups",
            "test,dev"
        ]
```

Usage Output Example (Local):

```
Assuming the corresponding module name of package 'pytest' is 'pytest'. Install the package or configure a package_module_name_map entry to override this behaviour.
Scanning 0 file...

pyproject.toml: DEP002 'matplotlib' defined as a dependency but not used in the codebase
Found 1 dependency issue.

For more information, see the documentation: https://deptry.com/
```

I had trouble getting the hook to work on GitHub, so I am using
