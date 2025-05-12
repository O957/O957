# UV Python Package And Project Management

_This document covers my usage of the Python package and project manager UV._

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
Ruby Version: ruby 3.2.3 (2024-01-18 revision 52bb2ac0a6) [arm64-darwin22]
```

</details>

Installation, MacOS & Linux:

```
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Description:

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

Given speed upgrade and centralization of capabilities, I've decided (2025-05-12) that I will use `uv` over `poetry` for Python package and project management.

Useful Links:

* Project Setup & Structure: <https://docs.astral.sh/uv/guides/projects/>
* Scripting Setup & Running: <https://docs.astral.sh/uv/guides/scripts/>
* Tooling: <https://docs.astral.sh/uv/guides/tools/>
* Notes On Using Precommit: <https://docs.astral.sh/uv/guides/integration/pre-commit/>



<details markdown=1>

<summary> Example Pyproject File </summary>

```yaml
[tool.poetry]
name = "afg6k7h4fhy2"
version = "0.0.1"
description = "The author's personal GitHub profile. Contained therein are some resources the author makes use of and decisions that the author has made concerning his use of GitHub. This repository also exists as a place for onlookers to provide the author with feedback. "
authors = ["AFg6K7h4fhy2 <127630341+AFg6K7h4fhy2@users.noreply.github.com>"]
license = "MIT"
readme = "README.md"
package-mode = false

[tool.poetry.dependencies]
python = "^3.12"
pre-commit = "^3.7.0"

[tool.poetry.group.dev.dependencies]
pygments = "^2.18.0"

[build-system]
requires = ["poetry-core"]
build-backend = "poetry.core.masonry.api"
```

</details>



Tasks related to the issue "Prepare Repository for production:

* Pin `uv` to appropriate Python version (`uv python pin 3.13`)
