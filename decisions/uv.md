# UV Python Package And Project Management

_This document covers my usage of the Python package and project manager UV._


Installation:

```
curl -LsSf https://astral.sh/uv/install.sh | sh
```



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


Tasks related to the issue "Prepare Repository for production:

* Pin `uv` to appropriate Python version (`uv python pin 3.13`)
