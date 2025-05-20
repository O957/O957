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

Enabling Dependabot:

* Head to Settings on GitHub within the target repository.
* Head to Advanced Security within Settings.
* Enable (if desired): Dependabot for alerts, security updates, and version updates, along with grouped updates.
  * Dependabot will create for you `./github/dependabot.yml` if Dependabot is enable for version updates.
  * Updates will be in the Security section of the repository.

(on grouped updates; see [here](https://docs.github.com/en/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates))

> You can enable grouped pull requests for Dependabot security updates in one, or both, of the following ways.
>
> * To group as many available security updates together as possible, across directories and per ecosystem, enable grouping in the "Advanced Security" settings for your repository, or in "Global settings" under Advanced Security for your organization.
> * For more granular control of grouping, such as grouping by package name, development/production dependencies, SemVer level, or across multiple directories per ecosystem, add configuration options to the dependabot.yml configuration file in your repository.
