# Preparing Repository For Production

_This document contains the contents of a common issue, called Prepare Repository For Production, that I make in my repositories to ensure everything is set up properly._

This issue covers the following:

* [ ] Use of `uv` for projects with Python.
  * [ ] `uv python pin 3.13`.
  * [ ] Dependencies, with groups (`dev`, `test`).
    * [ ] `uv add pytest --group test`
  * [ ] `uv sync`.
  * [ ] Proper `pyproject.toml` file:

```
[project]
name = ""
version = "0.0.1"
authors = [
  {name = "", email = ""},
]
description = "<repository description>"
license = "Apache-2.0"
readme = "README.md"
keywords = [<repository tags>]
requires-python = ">=3.13"

[project.urls]
Repository = ""
Issues = ""
"Author GitHub" = "https://github.com/AFg6K7h4fhy2"

[tool.ruff.lint.mccabe]
max-complexity = 15
```

* [ ] Proper `pre-commit` workflow (see below).
* [ ] Proper `pre-commit` configuration file (see below).
* [ ] Dependabot enabled.
  * [ ] Proper `dependabot.yaml` file (see below).
* [ ] Proper `CONTRIBUTING` file (see below).
* [ ] Proper `CODEOWNERS` file (see below).
* [ ] Proper `_typos.toml` (see below).
* [ ] Proper `.gitignore` (see below).
* [ ] Proper `LICENSE` (usually Apache-2.0) (see below).
* [ ] Proper minimum viable `README` (see below).
* [ ] Blank issue in `ISSUE_TEMPLATE` (see below).
* [ ] GitHub issue labels synched (see below).
* [ ] GitHub milestones created.
  * [ ] Backlog: Backlog of issues and PRs that have no due date.
* [ ] Open issues and pull requests labeled and milestoned.
* [ ] GitHub tags (2-5) in repository description.
* [ ] GitHub description on repository.
* [ ] Proper "General" settings:
  * [ ] Default branch `main`.
  * [ ] Wikis (disabled).
  * [ ] Issues (enabled).
  * [ ] Allow forking (choose based on repository).
  * [ ] Sponsorships (choose based on repository).
  * [ ] Discussions (choose based on repository).
  * [ ] Projects (enabled).
  * [ ] Allow merge commits.
  * [ ] Allow squash merging.
  * [ ] Allow rebase merging.
* [ ] Proper "Branches" settings:
  * [ ] Classic branch protection rule:
    * [ ] To `main`.
    * [ ] Require a pull request before merging.
    * [ ] Require approvals.
    * [ ] Require review from Code Owners.
    * [ ] Require status checks to pass before merging.
    * [ ] Require conversation resolution before merging.
* [ ] Proper "Actions" (general) settings:
  * [ ] Allow enterprise, and select non-enterprise, actions and reusable workflows.
  * [ ] Artifact / logs saved for 30 days.
  * [ ] Read and write permissions (in workflow permissions).
  * [ ] Allow GitHub Actions to create and approve pull requests.
  * [ ] Not accessible (workflows in other repositories cannot access this repository).
* [ ] Proper "Advanced Security" settings:
  * [ ] Dependency graph (enabled).
  * [ ] Automatic dependency submission (disabled).
  * [ ] Dependabot alerts (enabled).
  * [ ] Dependabot security updates (enabled).
  * [ ] Grouped security updates (enabled).
  * [ ] Dependabot on Actions runners (enabled).


For the label synching:

```
export LABELS_USERNAME="<YOUR USERNAME>"
export LABELS_TOKEN="<YOUR TOKEN>"
labels fetch -o <OWNER OF REPOSITORY WITH LABELS> -r <REPOSITORY WITH LABELS>
labels sync -o <OWNER OF REPOSITORY TO RECEIVE LABELS> -r <REPOSITORY TO RECEIVE LABELS> -f <LABELS FILE NAME>
```

Note, some tasks in this issue have already been completed.
