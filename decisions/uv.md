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

Useful Links:

* Project Setup & Structure: <https://docs.astral.sh/uv/guides/projects/>
* Scripting Setup & Running: <https://docs.astral.sh/uv/guides/scripts/>
* Tooling: <https://docs.astral.sh/uv/guides/tools/>
* Notes On Using Precommit: <https://docs.astral.sh/uv/guides/integration/pre-commit/>

In a project with `poetry`,


Tasks related to the issue "Prepare Repository for production:

* Pin `uv` to appropriate Python version (`uv python pin 3.13`)
