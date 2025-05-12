# UV Python Package And Project Management

_This document covers my usage of the Python package and project manager UV. Historically, I have used Poetry; however, I am transitioning towards using UV. Hence, this document also covers the transition from Poetry to UV._

<details markdown=1>

<summary> Environments & Machine </summary>

```
OS Version: macOS
ProductVersion:	13.3.1
BuildVersion: 22E261
Kernel: arm64
Architecture: 22.4.0
CPU Brand: Apple M1
Python Version: Python 3.13.1
Poetry Version: Poetry (version 1.8.3)
Ruby Version: ruby 3.2.3 (2024-01-18 revision 52bb2ac0a6) [arm64-darwin22]
```

</details>

Installation of UV, on MacOS & Linux:

```
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Description from [UV's website](https://docs.astral.sh/uv/):

> * 🚀 A single tool to replace pip, pip-tools, pipx, poetry, pyenv, twine, virtualenv, and more.
> * ⚡️ 10-100x faster than pip.
> * 🗂️ Provides comprehensive project management, with a universal lockfile.
> * ❇️ Runs scripts, with support for inline dependency metadata.
> * 🐍 Installs and manages Python versions.
> * 🛠️ Runs and installs tools published as Python packages.
> * 🔩 Includes a pip-compatible interface for a performance boost with a familiar CLI.
> * 🏢 Supports Cargo-style workspaces for scalable projects.
> * 💾 Disk-space efficient, with a global cache for dependency deduplication.
> * ⏬ Installable without Rust or Python via curl or pip.
> * 🖥️ Supports macOS, Linux, and Windows.

Given the speed upgrade and centralization of capabilities, I've decided (2025-05-12) that I will use `uv` over `poetry` for Python package and project management.

Useful Links:

* Project Setup & Structure: <https://docs.astral.sh/uv/guides/projects/>
* Scripting Setup & Running: <https://docs.astral.sh/uv/guides/scripts/>
* Tooling: <https://docs.astral.sh/uv/guides/tools/>
* Notes On Using Precommit: <https://docs.astral.sh/uv/guides/integration/pre-commit/>
* Packaging: <https://docs.astral.sh/uv/guides/package/>
* Virtual Environments: <https://docs.astral.sh/uv/pip/environments/>

Porting Over From UV To Poetry:

* Install `uv` (see above), if it's not already installed, and navigate to the target repository.
* Skip the next sub-steps if the `poetry` version is less than version 2.0.
  * Check to see if the following is in `pyproject.toml`; if the lines are not present[^more], add them:

```yaml
[tool.poetry.requires-plugins]
poetry-plugin-export = ">=1.8"
```

[^more]: For more information on `poetry` plugins, see [here](https://python-poetry.org/docs/plugins/#using-plugins); for more information on the `export` command, see [here](https://python-poetry.org/docs/cli/#export).

  * Run `poetry install`.
* Check the `pyproject.toml` file for different groups, such as `dev` and `test`; run the following command with the groups you want:

```
poetry export \
  --format=requirements.txt \
  --without-hashes \
  --with dev,test \
  --output=requirements.txt
```

* Create a `project` section in the `pyproject` file (see standard below)
  * If a section is not made, then the error when you run the next command might look like: "No `project` table found in ...".

<details markdown=1>

<summary> Standard Pyproject Project Table </summary>


```yaml
[project]
name = ""
version = ""
authors = [
  {name = "", email = ""},
]
description = ""
readme = ""
license = ""
keywords = [""]
requires-python = ">=3.13"

[project.urls]
Repository = ""
Issues = ""
"Author GitHub" = ""
```

</details>

* Remove items with `poetry` in the header:
  * `tool.poetry.dependencies`
  * `tool.poetry.group.dev.dependencies`
  * This includes removing:

```yaml
[build-system]
requires = ["poetry-core"]
build-backend = "poetry.core.masonry.api"
```

* Delete the `poetry.lock` file and remove it from the `.gitignore`.
* Add a file called `.python-version` with the version (e.g. 3.13) you want.
  * Run `uv python pin 3.13`.
* Ensure the `requirements.txt` file has the dependencies of interest before running:

```
uv add --requirements requirements.txt
```

* Run `uv lock`.
* Add the following to the `.pre-commit-config.yaml` file, if there is one and if not already present:

```yaml
-   repo: https://github.com/astral-sh/uv-pre-commit
    # uv version.
    rev: 0.7.3
    hooks:
    -   id: uv-lock
```

* Don't delete the `requirements.txt` file, since other Python users might still want to use this; if you agree with the previous statement, add the following to the `.pre-commit-config.yaml` file:


```yaml
-   id: uv-export
        args: ["--no-hashes", "--output-file=requirements.txt"]
```

* Run `uv venv` to create virtual environment.
  * Run `source .venv/bin/activate` to activate.
  * Run `deactivate` to deactivate.

Some UV Basics:

* Create a `venv`: `uv venv`
* Activate the `venv`: `source .venv/bin/activate`
* Deactivate the `venv`: `deactivate`
* Add a package: `uv add <package>` (being inside `venv` no necessary)
* Remove a package: `uv remove <package>`
* Update state of dependencies after package edit: `uv sync`
* Check packages installed: `uv pip list`
* Dependency graph: `uv tree`
* Check the lock file: `uv lock --check`
