# Preparing Repository for Production

_This document contains the contents of a common issue that the author makes on his repositories called Prepare Repository For Production._

This issue covers the following:

* Proper `poetry` file `pyproject.toml` exists:
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
* (possible) Dependabot enabled.
  * Fork <https://github.com/dependabot/demo>.
  * Select current repository.
  * Go to Advanced Security in Security in Settings.
  * Enable the bot.
* Proper `CONTRIBUTING` file.
* MVP `README`.
  * Title of repositories.
  * Description from GitHub.
  * Note of Work In Progress.
* Labels being synched (see end).
* Milestones created.
  * Backlog: Backlog of issues and PRs that have no due date.
* Issues and PRs labeled and milestoned.
* (possible) Presence of paper in assets.
* (possible) Presence of `repo-notes.md` in `assets/misc`.
* (possible) Presence of `dev-notes.md` in `assets/misc`.
* (possible) presence of `mypy.ini` file, if using Python.
* (possible) presence of `lintr` file, if using R.
* Between 2-5 tags on GitHub.
* Description on GitHub.
* If `poetry`, ensure `poetry.lock` is not tracked.
* Proper `pre-commit` workflow.
* Proper `pre-commit-config` file.
* Proper `_typos.toml`.
* Proper `.gitignore`.
* Blank issue in `ISSUE_TEMPLATE`.
* Branch protections to `main`.
  * Require a pull request before merging & (Require approvals & Require review from Code Owners).
  * Require status checks to pass before merging.
  * Require conversation resolution before merging.
* Proper `CODEOWNERS`.
* If CDC repository, proper Statements.
* Proper `LICENSE`.
* No Discussions or Wiki enabled.
* (possible) Sponsorships enable.
* Python environment change to Python 3.13

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
