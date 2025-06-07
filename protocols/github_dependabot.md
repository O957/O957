# Dependabot

_This document covers my usage of Dependabot on GitHub. Dependabot seems to help reduce latency in updating packages, especially in cases where there is an issue with their security._

<details markdown=1>

<summary> Environments & Machine </summary>

```
OS Version: ProductName: macOS
Product Version:	13.3.1
Build Version: 22E261
Kernel: arm64
Architecture: 22.4.0
CPU Brand: Apple M1
Python Version: Python 3.13.1
UV Version: uv 0.7.3 (3c413f74b 2025-05-07)
Ruby Version: ruby 3.2.3 (2024-01-18 revision 52bb2ac0a6) [arm64-darwin22]
Quarto Version: 1.6.40
Rscript Version: Rscript (R) version 4.4.2 (2024-10-31)
Git Version: git version 2.40.0
```

</details>

Description from the [quickstart guide](https://docs.github.com/en/code-security/getting-started/dependabot-quickstart-guide):

> Dependabot consists of three different features that help you manage your dependencies:
>
> * Dependabot alerts: Inform you about vulnerabilities in the dependencies that you use in your repository.
> * Dependabot security updates: Automatically raise pull requests to update the dependencies you use that have known security vulnerabilities.
> * Dependabot version updates: Automatically raise pull requests to keep your dependencies up-to-date.

Some Relevant Links:

* Dependabot Quickstart Guide: <https://docs.github.com/en/code-security/getting-started/dependabot-quickstart-guide>
* Working With Dependabot: <https://docs.github.com/en/code-security/dependabot/working-with-dependabot>
* How Dependabot Empowers You To Keep Your Projects Secure: <https://github.blog/security/supply-chain-security/how-dependabot-empowers-you-to-keep-your-projects-secure/>
* How To Use Dependabot For Automated Updates In 2025: <https://toxigon.com/how-to-use-dependabot-for-automated-updates>
* Automating Dependabot With GitHub Actions: <https://docs.github.com/en/code-security/dependabot/working-with-dependabot/automating-dependabot-with-github-actions>
* Dependabot Options Reference: <https://docs.github.com/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference>
* Configuring Dependabot Alerts: <https://docs.github.com/en/code-security/dependabot/dependabot-alerts/configuring-dependabot-alerts>
* Configuring Dependabot Security Updates: <https://docs.github.com/en/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates>
* Configuring Dependabot Version Updates: <https://docs.github.com/en/code-security/dependabot/dependabot-version-updates/configuring-dependabot-version-updates>
* Example File: <https://github.com/dependabot/dependabot-core/blob/main/.github/dependabot.yml>
* Customizing Dependabot Pull Requests To Fit Your Processes: <https://docs.github.com/en/code-security/dependabot/dependabot-version-updates/customizing-dependabot-prs>

Enabling Dependabot:

* Head to Settings on GitHub within the target repository.
* Head to Advanced Security within Settings.
* Enable (if desired): Dependabot for alerts, security updates, and version updates, along with grouped updates.
  * Dependabot will create for you `./github/dependabot.yml` if Dependabot is enable for version updates (wait to commit until later sections).
  * Updates will be in the Security section of the repository.

(on grouped updates; see [here](https://docs.github.com/en/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates))

> You can enable grouped pull requests for Dependabot security updates in one, or both, of the following ways.
>
> * To group as many available security updates together as possible, across directories and per ecosystem, enable grouping in the "Advanced Security" settings for your repository, or in "Global settings" under Advanced Security for your organization.
> * For more granular control of grouping, such as grouping by package name, development/production dependencies, SemVer level, or across multiple directories per ecosystem, add configuration options to the dependabot.yml configuration file in your repository.

* Use the following for the `dependabot.yml` file (the below file captures the author's preferences):

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

For the sake of using Dependabot, the current state of this protocol file suffices, though there may be future updates (2025-05-20).

* Since pull requests made by Dependabot fail `pre-commit`, the CI for `pre-commit` (see [here](https://pre-commit.ci/)) can be used to automatically fix the PRs; some benefits:

> auto fixing pull requests: if tools make changes to files during a pull request, pre-commit.ci will automatically fix the pull request.
> caching: tool caching is baked in and shared across all users. this means that the more users there are of pre-commit.ci, the more likely you will get faster builds!
> automatic updates: pre-commit.ci will periodically autoupdate your configuration ensuring that your hook versions are kept up to date. this autoupdate is currently scheduled weekly at approximately 16:00 UTC Monday.

Two notes:

> re-running a pull request: you can trigger a re-run on a pull request by commenting pre-commit.ci run (must appear on a line by itself). alternatively, one can attach a pre-commit.ci run label to the pull request.
> skipping push runs: skip a run by putting [skip ci], [ci skip], [skip pre-commit.ci], or [pre-commit.ci skip] in the commit message.

```yaml
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
```
