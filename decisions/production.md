This issue covers the following:

* Proper `pyproject.toml` edits.
  * Project description.
  * Authors.
  * Version.
  * Dev and Test dependencies.
  * Package mode `false`.
* Updated CONTRIBUTING file.
* MVP README.
* Labels being synched.
* Milestones created.
* Issues and PRs labeled and milestoned.
* Presence of paper in assets.
* Correct tagging on GitHub.
* Correct description on GitHub.
* Ensure `poetry.lock` is not tracked.
* Updated `pre-commit` workflow.
* Updated `pre-commit-config` file.
* Updated `_typos.toml`.
* Updated `.gitignore`.
* Branch protections to `main`.
  * Require a pull request before merging & (Require approvals & Require review from Code Owners)
  * Require status checks to pass before merging
  * Require conversation resolution before merging
* Updated CODEOWNERS.
* Correct LICENSE.
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
poetry env use /Library/Frameworks/Python.framework/Versions/3.12/bin/python3.12
poetry install
poetry env info
```

Note, some tasks in this issue have already been completed.
