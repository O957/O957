# Preparing Repository For Production

_This document contains the contents of a common issue, called Prepare Repository For Production, that I make in my repositories to ensure everything is set up properly._

This issue covers the following:

* [ ] Use of `uv` for projects with Python.
  * [ ] `uv python pin 3.13`.
  * [ ] Dependencies, with groups (`dev`, `test`).
    * [ ] `uv add pytest --group test`
  * [ ] `uv sync`.
  * [ ] Proper `pyproject.toml` file (see below).
* [ ] Proper `pre-commit` settings.
  * [ ] `pre-commit install`.
  * [ ] Proper `pre-commit` workflow (see below).
  * [ ] Proper `pre-commit` configuration file (see below).
  * [ ] `detect-secrets scan > .secrets.baseline`.
  * [ ] CI enabled (choose based on repository).
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

<details markdown=1>

<summary> Blank Issue Template </summary>

```md
---
name: Blank Issue
about: A blank issue template, for minimal overhead in issue creation.
title: ""
labels: ["basic issue"]
assignees: ""
---
```

</details>

<details markdown=1>

<summary> Apache-2.0 LICENSE </summary>

```
                                 Apache License
                           Version 2.0, January 2004
                        http://www.apache.org/licenses/

   TERMS AND CONDITIONS FOR USE, REPRODUCTION, AND DISTRIBUTION

   1. Definitions.

      "License" shall mean the terms and conditions for use, reproduction,
      and distribution as defined by Sections 1 through 9 of this document.

      "Licensor" shall mean the copyright owner or entity authorized by
      the copyright owner that is granting the License.

      "Legal Entity" shall mean the union of the acting entity and all
      other entities that control, are controlled by, or are under common
      control with that entity. For the purposes of this definition,
      "control" means (i) the power, direct or indirect, to cause the
      direction or management of such entity, whether by contract or
      otherwise, or (ii) ownership of fifty percent (50%) or more of the
      outstanding shares, or (iii) beneficial ownership of such entity.

      "You" (or "Your") shall mean an individual or Legal Entity
      exercising permissions granted by this License.

      "Source" form shall mean the preferred form for making modifications,
      including but not limited to software source code, documentation
      source, and configuration files.

      "Object" form shall mean any form resulting from mechanical
      transformation or translation of a Source form, including but
      not limited to compiled object code, generated documentation,
      and conversions to other media types.

      "Work" shall mean the work of authorship, whether in Source or
      Object form, made available under the License, as indicated by a
      copyright notice that is included in or attached to the work
      (an example is provided in the Appendix below).

      "Derivative Works" shall mean any work, whether in Source or Object
      form, that is based on (or derived from) the Work and for which the
      editorial revisions, annotations, elaborations, or other modifications
      represent, as a whole, an original work of authorship. For the purposes
      of this License, Derivative Works shall not include works that remain
      separable from, or merely link (or bind by name) to the interfaces of,
      the Work and Derivative Works thereof.

      "Contribution" shall mean any work of authorship, including
      the original version of the Work and any modifications or additions
      to that Work or Derivative Works thereof, that is intentionally
      submitted to Licensor for inclusion in the Work by the copyright owner
      or by an individual or Legal Entity authorized to submit on behalf of
      the copyright owner. For the purposes of this definition, "submitted"
      means any form of electronic, verbal, or written communication sent
      to the Licensor or its representatives, including but not limited to
      communication on electronic mailing lists, source code control systems,
      and issue tracking systems that are managed by, or on behalf of, the
      Licensor for the purpose of discussing and improving the Work, but
      excluding communication that is conspicuously marked or otherwise
      designated in writing by the copyright owner as "Not a Contribution."

      "Contributor" shall mean Licensor and any individual or Legal Entity
      on behalf of whom a Contribution has been received by Licensor and
      subsequently incorporated within the Work.

   2. Grant of Copyright License. Subject to the terms and conditions of
      this License, each Contributor hereby grants to You a perpetual,
      worldwide, non-exclusive, no-charge, royalty-free, irrevocable
      copyright license to reproduce, prepare Derivative Works of,
      publicly display, publicly perform, sublicense, and distribute the
      Work and such Derivative Works in Source or Object form.

   3. Grant of Patent License. Subject to the terms and conditions of
      this License, each Contributor hereby grants to You a perpetual,
      worldwide, non-exclusive, no-charge, royalty-free, irrevocable
      (except as stated in this section) patent license to make, have made,
      use, offer to sell, sell, import, and otherwise transfer the Work,
      where such license applies only to those patent claims licensable
      by such Contributor that are necessarily infringed by their
      Contribution(s) alone or by combination of their Contribution(s)
      with the Work to which such Contribution(s) was submitted. If You
      institute patent litigation against any entity (including a
      cross-claim or counterclaim in a lawsuit) alleging that the Work
      or a Contribution incorporated within the Work constitutes direct
      or contributory patent infringement, then any patent licenses
      granted to You under this License for that Work shall terminate
      as of the date such litigation is filed.

   4. Redistribution. You may reproduce and distribute copies of the
      Work or Derivative Works thereof in any medium, with or without
      modifications, and in Source or Object form, provided that You
      meet the following conditions:

      (a) You must give any other recipients of the Work or
          Derivative Works a copy of this License; and

      (b) You must cause any modified files to carry prominent notices
          stating that You changed the files; and

      (c) You must retain, in the Source form of any Derivative Works
          that You distribute, all copyright, patent, trademark, and
          attribution notices from the Source form of the Work,
          excluding those notices that do not pertain to any part of
          the Derivative Works; and

      (d) If the Work includes a "NOTICE" text file as part of its
          distribution, then any Derivative Works that You distribute must
          include a readable copy of the attribution notices contained
          within such NOTICE file, excluding those notices that do not
          pertain to any part of the Derivative Works, in at least one
          of the following places: within a NOTICE text file distributed
          as part of the Derivative Works; within the Source form or
          documentation, if provided along with the Derivative Works; or,
          within a display generated by the Derivative Works, if and
          wherever such third-party notices normally appear. The contents
          of the NOTICE file are for informational purposes only and
          do not modify the License. You may add Your own attribution
          notices within Derivative Works that You distribute, alongside
          or as an addendum to the NOTICE text from the Work, provided
          that such additional attribution notices cannot be construed
          as modifying the License.

      You may add Your own copyright statement to Your modifications and
      may provide additional or different license terms and conditions
      for use, reproduction, or distribution of Your modifications, or
      for any such Derivative Works as a whole, provided Your use,
      reproduction, and distribution of the Work otherwise complies with
      the conditions stated in this License.

   5. Submission of Contributions. Unless You explicitly state otherwise,
      any Contribution intentionally submitted for inclusion in the Work
      by You to the Licensor shall be under the terms and conditions of
      this License, without any additional terms or conditions.
      Notwithstanding the above, nothing herein shall supersede or modify
      the terms of any separate license agreement you may have executed
      with Licensor regarding such Contributions.

   6. Trademarks. This License does not grant permission to use the trade
      names, trademarks, service marks, or product names of the Licensor,
      except as required for reasonable and customary use in describing the
      origin of the Work and reproducing the content of the NOTICE file.

   7. Disclaimer of Warranty. Unless required by applicable law or
      agreed to in writing, Licensor provides the Work (and each
      Contributor provides its Contributions) on an "AS IS" BASIS,
      WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
      implied, including, without limitation, any warranties or conditions
      of TITLE, NON-INFRINGEMENT, MERCHANTABILITY, or FITNESS FOR A
      PARTICULAR PURPOSE. You are solely responsible for determining the
      appropriateness of using or redistributing the Work and assume any
      risks associated with Your exercise of permissions under this License.

   8. Limitation of Liability. In no event and under no legal theory,
      whether in tort (including negligence), contract, or otherwise,
      unless required by applicable law (such as deliberate and grossly
      negligent acts) or agreed to in writing, shall any Contributor be
      liable to You for damages, including any direct, indirect, special,
      incidental, or consequential damages of any character arising as a
      result of this License or out of the use or inability to use the
      Work (including but not limited to damages for loss of goodwill,
      work stoppage, computer failure or malfunction, or any and all
      other commercial damages or losses), even if such Contributor
      has been advised of the possibility of such damages.

   9. Accepting Warranty or Additional Liability. While redistributing
      the Work or Derivative Works thereof, You may choose to offer,
      and charge a fee for, acceptance of support, warranty, indemnity,
      or other liability obligations and/or rights consistent with this
      License. However, in accepting such obligations, You may act only
      on Your own behalf and on Your sole responsibility, not on behalf
      of any other Contributor, and only if You agree to indemnify,
      defend, and hold each Contributor harmless for any liability
      incurred by, or claims asserted against, such Contributor by reason
      of your accepting any such warranty or additional liability.

   END OF TERMS AND CONDITIONS

   APPENDIX: How to apply the Apache License to your work.

      To apply the Apache License to your work, attach the following
      boilerplate notice, with the fields enclosed by brackets "{}"
      replaced with your own identifying information. (Don't include
      the brackets!)  The text should be enclosed in the appropriate
      comment syntax for the file format. We also recommend that a
      file or class name and description of purpose be included on the
      same "printed page" as the copyright notice for easier
      identification within third-party archives.

   Copyright {yyyy} {name of copyright owner}

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```

</details>

<details markdown=1>

<summary> Pyproject File </summary>

```yaml
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

</details>


<details markdown=1>

<summary> CONTRIBUTION File </summary>

```
# Contribution Guidelines

_This document contains some guidelines for external contributions in this repository. At present, I would (on average) rather have you contribute than not, and if following these guidelines would effectuate you not making a contribution, I would rather you ignore them and contribute._

Primarily, aim to follow GitHub's community guidelines:

[GitHub Community Guidelines](https://github.com/github/docs/blob/main/content/site-policy/github-terms/github-community-guidelines.md):

> The primary purpose of the GitHub community is to collaborate on software projects. We are committed to maintaining a community where users are free to express themselves and challenge one another's ideas, both technical and otherwise. At the same time, it's important that users remain respectful and allow space for others to contribute openly. In order to foster both a safe and productive environment, we encourage our community members to look to these guidelines to inform how they interact on our platform. Below, you’ll find some suggestions for how to have successful interactions as a valued member of the GitHub community.
>
> * __Be welcoming and open-minded__ - New users join our community each day. Some are well-established developers, while others are just beginning. Be open to other ideas and experience levels. Make room for opinions other than your own and be welcoming to new collaborators and those just getting started.
> * __Be respectful__ - Working in a collaborative environment means disagreements may happen. But remember to criticize ideas, not people. Share thoughtful, constructive criticism and be courteous to those you interact with. If you’re unable to engage respectfully, consider taking a step back or using some of our moderation tools to deescalate a tense situation.
> * __Be empathetic__ - GitHub is a global community with people from a wide variety of backgrounds and perspectives, many of which may not be your own. Try to put yourself in others’ shoes and understand their feelings before you address them. Do your best to help make GitHub a community where others feel safe to make contributions, participate in discussions, and share different ideas.

Secondarily, aim to follow these guidelines[^guidelines], as outlined by the author:

- **Use Evidence**: Please attempt to back suggestions, contributions, code changes, and feature requests with evidence, such as relevant documentation, benchmarks, research papers, or conversations, among other things.
- **Transparency**: Please attempt to maintain transparency in discussions by clearly stating your motivations and assumptions, along with any limitations in your contributions or suggestions. Be explicit about areas where you are uncertain or where you lack evidence, specifying the degree of uncertainty where possible.
- **Adherence To Standards**: Please attempt to follow existing standards or best practices relevant to the project, tools, or procedures to ensure consistency and readability.
- **Prioritize Impact**: Please attempt to consider how your contributions affect the project's broader goals, integration with other tools or workflows, and long-term implications. Focus on improving the project's quality, usability, and performance. Reflect on its role within the context of civilization and strive to minimize harm or wasted effort.
- **Maintain Integrity**: Do not intentionally misrepresent data, results, or contributions. Please always strive for epistemic rigor, accuracy, and honesty.

[^guidelines]: The author welcomes, as is the case with most (all?) of the author's work, comments from the audience on these guidelines. The author is open to revising these contribution guidelines with suggestions engendered via reasonable criticism and discussion.
```

</details>


<details markdown=1>

<summary> CODEOWNERS </details>

```
# For any changes to any facet of this repository reference:
* @AFg6K7h4fhy2
```

</details>


<details markdown=1>

<summary> Dependabot </summary>

```yaml
###############################################################################
# OVERVIEW
###############################################################################
# The following contains the Dependabot security and version updates
# configuration for this repository, which likely are derived from the author's
# (AFg6K7h4fhy2) repository template.
#
# Links:
#
# The author's template: https://github.com/AFg6K7h4fhy2/AFg6K7h4fhy2-Template
# UV dependency bots: https://docs.astral.sh/uv/guides/integration/
# dependency-bots/
#
# Some of the comments in this file were derived from:
# https://docs.github.com/en/code-security/dependabot/
# dependabot-version-updates/configuring-dependabot-version-updates
# and
# https://docs.github.com/en/code-security/dependabot/working-with-dependabot/
# dependabot-options-reference
#
# Please see the documentation for all configuration options:
# https://docs.github.com/code-security/dependabot/dependabot-version-updates/
# configuration-options-for-the-dependabot.yml-file
###############################################################################
# DEPENDABOT SETTINGS
###############################################################################
# dependabot configuration syntax to use; always 2.
version: 2
# section where you define each package-ecosystem to update.
updates:
  # enable version updates for GitHub actions
  - package-ecosystem: "github-actions"
    # workflow files stored in the default location of `.github/workflows`;
    # you don't need to specify `/.github/workflows` for `directory`; you can
    # use `directory: "/"`.
    directory: "/"
    schedule:
      interval: "weekly"
      day: "sunday"
      time: "10:00"
      timezone: "America/Denver"
    reviewers:
      - "AFg6K7h4fhy2"
    assignees:
      - "AFg6K7h4fhy2"
    # default separator (/) to hyphen (-)
    pull-request-branch-name:
      separator: "-"
    labels:
      - "Automation"
    # enable version updates for uv; wait until Dependabot adds uv support
    # (tracked at dependabot/dependabot-core#10478)
  - package-ecosystem: "uv"
    directory: "/"
    schedule:
      interval: "weekly"
      day: "sunday"
      time: "10:00"
      timezone: "America/Denver"
    reviewers:
      - "AFg6K7h4fhy2"
    assignees:
      - "AFg6K7h4fhy2"
    # default separator (/) to hyphen (-)
    pull-request-branch-name:
      separator: "-"
    labels:
      - "Dependencies"
###############################################################################
```

</details>


<details markdown=1>

<summary> Pre-Commit Config </summary>

```yaml
name: pre-commit

on:
  pull_request:
  push:
    branches: [main]

jobs:
  pre-commit:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - uses: actions/setup-python@v5
    - uses: pre-commit/action@v3.0.1
```

</details>


<details markdown=1>

<summary> Pre-Commit Config </summary>

```yaml
###############################################################################
# OVERVIEW
###############################################################################
# The following contains the pre-commit hooks for this repository, which are
# likely a modified version of the author's (AFg6K7h4fhy2) repository template.
#
# Links:
#
# Pre-commit: https://pre-commit.com/
# The author's template: https://github.com/AFg6K7h4fhy2/AFg6K7h4fhy2-Template
# Supported hooks: https://github.com/pre-commit/pre-commit-hooks
# Ruff rules: https://docs.astral.sh/ruff/rules/
###############################################################################
# CONTINUOUS INTEGRATION
###############################################################################
ci:
    # custom commit message for PR autofixes
    autofix_commit_msg: |
        [pre-commit.ci] auto fixes from pre-commit.com hooks
        for more information, see https://pre-commit.ci
    # whether to autofix pull requests. when disabled, comment / label
    # "pre-commit.ci autofix" to a pull request to manually trigger
    # auto-fixing.
    autofix_prs: true
    # branch to send autoupdate PRs to; by default, pre-commit.ci will update
    # the default branch of the repository.
    autoupdate_branch: ""
    # custom commit message for autoupdate PRs.
    autoupdate_commit_msg: "[pre-commit.ci] pre-commit autoupdate"
    # control when the autoupdate runs, possible values: 'weekly',
    # 'monthly', 'quarterly'.
    autoupdate_schedule: weekly
    # a list of hook ids to skip only in pre-commit.ci;
    skip: []
    #  whether to recursively check out submodules
    submodules: false
###############################################################################
# GENERAL
###############################################################################
repos:
-   repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v5.0.0
    hooks:
    # prevent giant files from being committed.
    -   id: check-added-large-files
        args: ["--maxkb=10000"]
    # simply check whether files parse as valid
    # python
    -   id: check-ast
    # check for files with names that would
    # conflict on a case-insensitive filesystem
    # like MacOS HFS+ or Windows FAT.
    -   id: check-case-conflict
    # checks for a common error of placing
    # code before the docstring.
    -   id: check-docstring-first
    # attempts to load all yaml files to
    # verify syntax.
    -   id: check-yaml
        # allow yaml files which use the
        # multi-document syntax
        args: ["--allow-multiple-documents"]
    # attempts to load all TOML files to
    # verify syntax.
    -   id: check-toml
    # makes sure files end in a newline and
    # only a newline.
    -   id: end-of-file-fixer
    # replaces or checks mixed line ending.
    -   id: mixed-line-ending
    # verifies that test files are named
    # correctly.
    -   id: name-tests-test
        # ensure tests match test_.*\.py
        args: ["--pytest-test-first"]
    # checks that all your JSON files are pretty.
    # "Pretty" here means that keys are sorted
    # and indented.
    -   id: pretty-format-json
        # automatically format json files;
        # when autofixing, retain the original
        # key ordering (instead of sorting
        # the keys)
        args: ["--autofix", "--no-sort-keys"]
    # trims trailing whitespace.
    -   id: trailing-whitespace
    # checks that non-binary executables have
    # a proper shebang.
    -   id: check-executables-have-shebangs
        files: \.sh$
    # checks for the existence of private keys.
    -   id: detect-private-key
###############################################################################
# PYTHON
###############################################################################
-   repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.9.4
    hooks:
    # "currently, the Ruff formatter does not sort imports.
    # In order to both sort imports and format, call
    # the Ruff linter and then the formatter:"
    -   id: ruff
        args: [
          "check",
          "--select",
          # isort
          "I",
          "--fix"]
    # run ruff linter; the Ruff Linter is an extremely fast Python linter
    # designed as a drop-in replacement for Flake8 (plus dozens of plugins),
    # isort, pydocstyle, pyupgrade, autoflake, and more
    -   id: ruff
        args: [
          # ambiguous variable name: {name}
          "--ignore=E741",
          # do not assign a lambda expression, use a def
          "--ignore=E731",
          # indentation contains tabs (sorry, I like tabs)
          "--ignore=W191",
          # found useless expression. ignore since .qmd displays
          "--ignore=B018",
          # {name} is too complex ({complexity} > {max_complexity})
          # note: ignored on select repositories
          "--ignore=C901",
          # E and W: pycodestyle, standard PEP8 errors and pycodestyle warnings.
          # F: pyflakes warnings (e.g., unused variables, undefined names).,
          # B: flake8-bugbear (useful best practices).
          # SIM: flake8-simplify
          # C90: McCabe complexity (cyclomatic complexity).
          # UP: pyupgrade, Python version compatibility
          "--select=E,W,F,B,C90,UP,SIM",
          # linter checks for lines, but doesn't fix, default is 88
          "--line-length=79",
          # lint all files in the current directory, and fix any fixable errors.
          "--fix"]
    # run the ruff-formatter; the Ruff formatter is an extremely fast
    # Python code formatter designed as a drop-in replacement for Black
    -   id: ruff-format
        args: [
          "--line-length=79",
        ]
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
###############################################################################
# UV PACKAGE AND DEPENDENCY MANAGEMENT
###############################################################################
-   repo: https://github.com/astral-sh/uv-pre-commit
    # uv version.
    rev: 0.7.3
    hooks:
    -   id: uv-lock
    -   id: uv-export
        args: ["--no-hashes", "--output-file=requirements.txt"]
###############################################################################
# MAKE FILES
###############################################################################
-   repo: https://github.com/mrtazz/checkmake.git
    rev: 0.2.2
    hooks:
    -   id: checkmake
###############################################################################
# SECURITY
###############################################################################
-   repo: https://github.com/Yelp/detect-secrets
    rev: v1.5.0
    hooks:
    # must first run
    # detect-secrets scan > .secrets.baseline
    -   id: detect-secrets
        args: ["--baseline", ".secrets.baseline"]
        exclude: package.lock.json
###############################################################################
# GITHUB ACTIONS
###############################################################################
-   repo: https://github.com/rhysd/actionlint
    rev: v1.7.7
    hooks:
    -   id: actionlint
###############################################################################
# SPELLING
###############################################################################
-   repo: https://github.com/crate-ci/typos
    rev: dictgen-v0.3.1
    hooks:
    -   id: typos
        args: ["--force-exclude"]
###############################################################################
# COMMIT MESSAGES
###############################################################################
-   repo: https://github.com/commitizen-tools/commitizen
    rev: v4.1.1
    hooks:
    -   id: commitizen
-   repo: https://github.com/jorisroovers/gitlint
    rev:  v0.19.1
    hooks:
    -   id: gitlint
###############################################################################
```

</details>


<details markdown=1>

<summary> Typos File </summary>

```yaml
[default]
extend-ignore-identifiers-re = [
    "AttributeID.*Supress.*",
]

[default.extend-identifiers]
AttributeIDSupressMenu = "AttributeIDSupressMenu"

[default.extend-words]
# words that should not be corrected
AFg6K7h4fhy2 = "AFg6K7h4fhy2"
dot_acn = ".acn"
dot_fot = ".fot"
dot_ist = ".ist"
Remane = "Remane"
aquaduct = "aquaduct"

[files]
extend-exclude = [
    ".gitignore",
    ".pre-commit-config.yaml",
    "./.github/ISSUE_TEMPLATE/general_issue.md",
    "*.bib"
]
```

</details>


<details markdown=1>

<summary> GitIgnore </summary>


```
################################################################################
# PYTHON GITIGNORE TEMPLATE
# (https://github.com/github/gitignore/blob/main/Python.gitignore) (2024-10-03)
################################################################################

# Byte-compiled / optimized / DLL files
__pycache__/
*.py[cod]
*$py.class

# C extensions
*.so

# Distribution / packaging
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/
share/python-wheels/
*.egg-info/
.installed.cfg
*.egg
MANIFEST

# PyInstaller
#  Usually these files are written by a python script from a template
#  before PyInstaller builds the exe, so as to inject date/other infos into it.
*.manifest
*.spec

# Installer logs
pip-log.txt
pip-delete-this-directory.txt

# Unit test / coverage reports
htmlcov/
.tox/
.nox/
.coverage
.coverage.*
.cache
nosetests.xml
coverage.xml
*.cover
*.py,cover
.hypothesis/
.pytest_cache/
cover/

# Translations
*.mo
*.pot

# Django stuff:
*.log
local_settings.py
db.sqlite3
db.sqlite3-journal

# Flask stuff:
instance/
.webassets-cache

# Scrapy stuff:
.scrapy

# Sphinx documentation
docs/_build/

# PyBuilder
.pybuilder/
target/

# Jupyter Notebook
.ipynb_checkpoints

# IPython
profile_default/
ipython_config.py

# pyenv
#   For a library or package, you might want to ignore these files since the code is
#   intended to run in multiple environments; otherwise, check them in:
# .python-version

# pipenv
#   According to pypa/pipenv#598, it is recommended to include Pipfile.lock in version control.
#   However, in case of collaboration, if having platform-specific dependencies or dependencies
#   having no cross-platform support, pipenv may install dependencies that don't work, or not
#   install all needed dependencies.
#Pipfile.lock

# poetry
#   Similar to Pipfile.lock, it is generally recommended to include poetry.lock in version control.
#   This is especially recommended for binary packages to ensure reproducibility, and is more
#   commonly ignored for libraries.
#   https://python-poetry.org/docs/basic-usage/#commit-your-poetrylock-file-to-version-control
#poetry.lock

# pdm
#   Similar to Pipfile.lock, it is generally recommended to include pdm.lock in version control.
#pdm.lock
#   pdm stores project-wide configurations in .pdm.toml, but it is recommended to not include it
#   in version control.
#   https://pdm.fming.dev/latest/usage/project/#working-with-version-control
.pdm.toml
.pdm-python
.pdm-build/

# PEP 582; used by e.g. github.com/David-OConnor/pyflow and github.com/pdm-project/pdm
__pypackages__/

# Celery stuff
celerybeat-schedule
celerybeat.pid

# SageMath parsed files
*.sage.py

# Environments
.env
.venv
env/
venv/
ENV/
env.bak/
venv.bak/

# Spyder project settings
.spyderproject
.spyproject

# Rope project settings
.ropeproject

# mkdocs documentation
/site

# mypy
.mypy_cache/
.dmypy.json
dmypy.json

# Pyre type checker
.pyre/

# pytype static type analyzer
.pytype/

# Cython debug symbols
cython_debug/

# PyCharm
#  JetBrains specific template is maintained in a separate JetBrains.gitignore that can
#  be found at https://github.com/github/gitignore/blob/main/Global/JetBrains.gitignore
#  and can be added to the global gitignore or merged into this file.  For a more nuclear
#  option (not recommended) you can uncomment the following to ignore the entire idea folder.
#.idea/


################################################################################
# TEX GITIGNORE TEMPLATE
# (https://github.com/github/gitignore/blob/main/TeX.gitignore) (2024-10-03)
################################################################################


## Core latex/pdflatex auxiliary files:
*.aux
*.lof
*.log
*.lot
*.fls
*.out
*.toc
*.fmt
*.fot
*.cb
*.cb2
.*.lb

## Intermediate documents:
*.dvi
*.xdv
*-converted-to.*
# these rules might exclude image files for figures etc.
# *.ps
# *.eps
# *.pdf

## Generated if empty string is given at "Please type another file name for output:"
.pdf

## Bibliography auxiliary files (bibtex/biblatex/biber):
*.bbl
*.bcf
*.blg
*-blx.aux
*-blx.bib
*.run.xml

## Build tool auxiliary files:
*.fdb_latexmk
*.synctex
*.synctex(busy)
*.synctex.gz
*.synctex.gz(busy)
*.pdfsync
*.rubbercache
rubber.cache

## Build tool directories for auxiliary files
# latexrun
latex.out/

## Auxiliary and intermediate files from other packages:
# algorithms
*.alg
*.loa

# achemso
acs-*.bib

# amsthm
*.thm

# beamer
*.nav
*.pre
*.snm
*.vrb

# changes
*.soc

# comment
*.cut

# cprotect
*.cpt

# elsarticle (documentclass of Elsevier journals)
*.spl

# endnotes
*.ent

# fixme
*.lox

# feynmf/feynmp
*.mf
*.mp
*.t[1-9]
*.t[1-9][0-9]
*.tfm

#(r)(e)ledmac/(r)(e)ledpar
*.end
*.?end
*.[1-9]
*.[1-9][0-9]
*.[1-9][0-9][0-9]
*.[1-9]R
*.[1-9][0-9]R
*.[1-9][0-9][0-9]R
*.eledsec[1-9]
*.eledsec[1-9]R
*.eledsec[1-9][0-9]
*.eledsec[1-9][0-9]R
*.eledsec[1-9][0-9][0-9]
*.eledsec[1-9][0-9][0-9]R

# glossaries
*.acn
*.acr
*.glg
*.glo
*.gls
*.glsdefs
*.lzo
*.lzs
*.slg
*.slo
*.sls

# uncomment this for glossaries-extra (will ignore makeindex's style files!)
# *.ist

# gnuplot
*.gnuplot
*.table

# gnuplottex
*-gnuplottex-*

# gregoriotex
*.gaux
*.glog
*.gtex

# htlatex
*.4ct
*.4tc
*.idv
*.lg
*.trc
*.xref

# hypdoc
*.hd

# hyperref
*.brf

# knitr
*-concordance.tex
# TODO Uncomment the next line if you use knitr and want to ignore its generated tikz files
# *.tikz
*-tikzDictionary

# listings
*.lol

# luatexja-ruby
*.ltjruby

# makeidx
*.idx
*.ilg
*.ind

# minitoc
*.maf
*.mlf
*.mlt
*.mtc[0-9]*
*.slf[0-9]*
*.slt[0-9]*
*.stc[0-9]*

# minted
_minted*
*.pyg

# morewrites
*.mw

# newpax
*.newpax

# nomencl
*.nlg
*.nlo
*.nls

# pax
*.pax

# pdfpcnotes
*.pdfpc

# sagetex
*.sagetex.sage
*.sagetex.py
*.sagetex.scmd

# scrwfile
*.wrt

# svg
svg-inkscape/

# sympy
*.sout
*.sympy
sympy-plots-for-*.tex/

# pdfcomment
*.upa
*.upb

# pythontex
*.pytxcode
pythontex-files-*/

# tcolorbox
*.listing

# thmtools
*.loe

# TikZ & PGF
*.dpth
*.md5
*.auxlock

# titletoc
*.ptc

# todonotes
*.tdo

# vhistory
*.hst
*.ver

# easy-todo
*.lod

# xcolor
*.xcp

# xmpincl
*.xmpi

# xindy
*.xdy

# xypic precompiled matrices and outlines
*.xyc
*.xyd

# endfloat
*.ttt
*.fff

# Latexian
TSWLatexianTemp*

## Editors:
# WinEdt
*.bak
*.sav

# Texpad
.texpadtmp

# LyX
*.lyx~

# Kile
*.backup

# gummi
.*.swp

# KBibTeX
*~[0-9]*

# TeXnicCenter
*.tps

# auto folder when using emacs and auctex
./auto/*
*.el

# expex forward references with \gathertags
*-tags.tex

# standalone packages
*.sta

# Makeindex log files
*.lpz

# xwatermark package
*.xwm

# REVTeX puts footnotes in the bibliography by default, unless the nofootinbib
# option is specified. Footnotes are the stored in a file with suffix Notes.bib.
# Uncomment the next line to have this generated file ignored.
#*Notes.bib


################################################################################
# R GITIGNORE TEMPLATE
# (https://github.com/github/gitignore/blob/main/R.gitignore) (2024-12-05)
################################################################################

# History files
.Rhistory
.Rapp.history

# Session Data files
.RData
.RDataTmp

# User-specific files
.Ruserdata

# Example code in package build process
*-Ex.R

# Output files from R CMD build
/*.tar.gz

# Output files from R CMD check
/*.Rcheck/

# RStudio files
.Rproj.user/

# produced vignettes
vignettes/*.html
vignettes/*.pdf

# OAuth2 token, see https://github.com/hadley/httr/releases/tag/v0.3
.httr-oauth

# knitr and R markdown default cache directories
*_cache/
/cache/

# Temporary files created by R markdown
*.utf8.md
*.knit.md

# R Environment Variables
.Renviron

# pkgdown site
docs/

# translation temp files
po/*~

# RStudio Connect folder
rsconnect/


################################################################################
# JULIA GITIGNORE TEMPLATE
# (https://github.com/github/gitignore/blob/main/Julia.gitignore) (2024-12-05)
################################################################################

# Files generated by invoking Julia with --code-coverage
*.jl.cov
*.jl.*.cov

# Files generated by invoking Julia with --track-allocation
*.jl.mem

# System-specific files and directories generated by the BinaryProvider and BinDeps packages
# They contain absolute paths specific to the host computer, and so should not be committed
deps/deps.jl
deps/build.log
deps/downloads/
deps/usr/
deps/src/

# Build artifacts for creating documentation generated by the Documenter package
docs/build/
docs/site/

# File generated by Pkg, the package manager, based on a corresponding Project.toml
# It records a fixed state of all packages used by the project. As such, it should not be
# committed for packages, but should be committed for applications that require a static
# environment.
Manifest.toml


################################################################################
# GITHUB PAGES GITIGNORE TEMPLATE
# (https://github.com/github/gitignore/blob/main/GitHubPages.gitignore) (2024-12-05)
################################################################################

# This .gitignore is appropriate for repositories deployed to GitHub Pages and using
# a Gemfile as specified at https://github.com/github/pages-gem#conventional

# Basic Jekyll gitignores (synchronize to Jekyll.gitignore)
_site/
.sass-cache/
.jekyll-cache/
.jekyll-metadata

# Additional Ruby/bundler ignore for when you run: bundle install
/vendor

# Specific ignore for GitHub Pages
# GitHub Pages will always use its own deployed version of pages-gem
# This means GitHub Pages will NOT use your Gemfile.lock and therefore it is
# counterproductive to check this file into the repository.
# Details at https://github.com/github/pages-gem/issues/768
Gemfile.lock

################################################################################
# SASS GITIGNORE TEMPLATE
# (https://github.com/github/gitignore/blob/main/Sass.gitignore) (2024-12-05)
################################################################################

.sass-cache/
*.css.map
*.sass.map
*.scss.map

################################################################################
# C++ GITIGNORE TEMPLATE
# (https://github.com/github/gitignore/blob/main/C%2B%2B.gitignore) (2024-12-05)
################################################################################

# Prerequisites
*.d

# Compiled Object files
*.slo
*.lo
*.o
*.obj

# Precompiled Headers
*.gch
*.pch

# Compiled Dynamic libraries
*.so
*.dylib
*.dll

# Fortran module files
*.mod
*.smod

# Compiled Static libraries
*.lai
*.la
*.a
*.lib

# Executables
*.exe
*.out
*.app

################################################################################
# MISCELLANEOUS
################################################################################

poetry.lock
/.quarto/
_site
/_site
/_freeze
_freeze
.DS_Store
DS_Store
_book/
_book
author_emails.txt
# csv files must be converted to parquet files
*.csv
env
```

</details>


<details markdown=1>

<summary> Label Synching </summary>

```
export LABELS_USERNAME="<YOUR USERNAME>"
export LABELS_TOKEN="<YOUR TOKEN>"
labels fetch -o <OWNER OF REPOSITORY WITH LABELS> -r <REPOSITORY WITH LABELS>
labels sync -o <OWNER OF REPOSITORY TO RECEIVE LABELS> -r <REPOSITORY TO RECEIVE LABELS> -f <LABELS FILE NAME>
```

</details>







Note, some tasks in this issue have already been completed.
