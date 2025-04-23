# Preparing Repository for Production

_This document contains the contents of a common issue that the author makes on his repositories call Prepare Repository For Production._

This issue covers the following:

* Proper `pyproject.toml` edits.
  * `name`
  * `version`
  * `description`
  * `authors`
  * `license`
  * `readme`
  * `repository`
  * `keywords`
  * Dependencies groups.
  * URLs (`[tool.poetry.urls]`).
* Updated `CONTRIBUTING` file.
* MVP `README`.
* Labels being synched.
* Milestones created.
* Issues and PRs labeled and milestoned.
* (possible) presence of paper in assets.
* Presence of `repo-notes.md` in `assets/misc`.
* Presence of `dev-notes.md` in `assets/misc`.
* (possible) presence of `mypy.ini` file if Python.
* (possible) presence of `lintr` file if R.
* Correct tagging on GitHub.
* Correct description on GitHub.
* Ensure `poetry.lock` is not tracked.
* Updated `pre-commit` workflow.
* Updated `pre-commit-config` file.
* Updated `_typos.toml`.
* Updated `.gitignore`.
* Blank issue in `ISSUE_TEMPLATE`.
* Branch protections to `main`.
  * Require a pull request before merging & (Require approvals & Require review from Code Owners)
  * Require status checks to pass before merging
  * Require conversation resolution before merging
* Updated `CODEOWNERS`.
* If "work" repository, proper Statements.
* Correct `LICENSE`.
* Choices for Discussions, Wiki, and Sponsorships.
* Python environment change to Python 3.12.5

For the label synching:

```
export LABELS_USERNAME="<YOUR USERNAME>"
export LABELS_TOKEN="<YOUR TOKEN>"
labels fetch -o <OWNER OF REPOSITORY WITH LABELS> -r <REPOSITORY WITH LABELS>
labels sync -o <OWNER OF REPOSITORY TO RECEIVE LABELS> -r <REPOSITORY TO RECEIVE LABELS> -f <LABELS FILE NAME>
```

For the proper `poetry` environment on the author's system:

```
poetry env info
poetry env remove python3
poetry env use /Library/Frameworks/Python.framework/Versions/3.13/bin/python3.13
poetry install
poetry env info
```

Note, some tasks in this issue have already been completed.
