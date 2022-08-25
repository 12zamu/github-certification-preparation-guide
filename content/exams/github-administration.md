# GitHub Administration

> These are **NOT real questions** from the exam but quite close enough to what you can get to help you to prepare it and obtain the certification

## Skills measured

- [Support GitHub Enterprise for users and key stakeholders](#support-github-enterprise-for-users-and-key-stakeholders) (15% of the exam)
- [Manage user identities and GitHub authentication](#manage-user-identities-and-github-authentication) (20% of the exam)
- [Describe how GitHub is deployed, distributed, and licensed](#describe-how-github-is-deployed-distributed-and-licensed) (5% of the exam)
- [Manage access and permissions based on membership](#manage-access-and-permissions-based-on-membership) (20% of the exam)
- [Enable secure software development and ensure compliance](#enable-secure-software-development-and-ensure-compliance) (15% of the exam)
- [Manage GitHub Actions](#manage-github-actions) (20% of the exam)
- [Manage GitHub Packages](#manage-github-packages) (5% of the exam)

## Support GitHub Enterprise for users and key stakeholders

### What role is required to edit a team ?

<details><summary>show</summary>
<p>

**Maintainer** or **admin**

</p>
</details>

### Can you have nested teams in GitHub ?

<details><summary>show</summary>
<p>

Yes and it is a general pratice [to use them to reflect](https://docs.github.com/en/organizations/organizing-members-into-teams/about-teams#nested-teams) the current enterprise internal's organization.

</p>
</details>

### Which format are available when exporting audit logs ?

<details><summary>show</summary>
<p>

**JSON** and **CSV**

</p>
</details>

### Which roles can be used to manage billing information ?

<details><summary>show</summary>
<p>

**owner** and **billing manager**

</p>
</details>

### On GitHub Enterprise Server, which command lines allows to generate a logs package to communicate to the support ?

<details><summary>show</summary>
<p>

```bash
ssh -p 122 admin@hostname -- 'ghe-support-bundle -o' > support-bundle.tgz
```

</p>
</details>

## Manage user identities and GitHub authentication

### Can be GitHub synchronized with an identity provider ?

<details><summary>show</summary>
<p>

Yes, for instance, Azure Active Directory but other like ADFS, Okta, OneLogin, etc

</p>
</details>

### What are the different methods to authenticate against GitHub ?

<details><summary>show</summary>
<p>

- username/password
- PAT (Personal Access Token)
- SSH keys
- Deploy keys

</p>
</details>

### Which authentication mechanism allow user to connect using their company's credentials ?

<details><summary>show</summary>
<p>

**SAML SSO**

</p>
</details>

### What are the supported 2FA (multi factor authentication) methods ?

<details><summary>show</summary>
<p>

- SMS
- TOTP app
- security keys

</p>
</details>

### Which feature allow to synchronize exchange of user identity data between your Idp and GitHub ?

<details><summary>show</summary>
<p>

**SCIM**

</p>
</details>

### What is the limit number of user in one GitHub organization ?

<details><summary>show</summary>
<p>

**10000**

- Maximum number of members in a GitHub team: 5000
- Maximum number of members in a GitHub organization: 10000
- Maximum number of teams in a GitHub organization: 1500

</p>
</details>

## Describe how GitHub is deployed, distributed, and licensed

### Can an enterprise contain several organizations  ?

<details><summary>show</summary>
<p>

yes.

</p>
</details>

### Are the hosted agents totally free ?

<details><summary>show</summary>
<p>

Yes for public repositories. For private repositories, you have free minutes of usage offered per month

</p>
</details>

### You plan on using GitHub Actions to build, test, and deliver your cross-platform code. Which of the following platforms will be the most expensive to use?

<details><summary>show</summary>
<p>

macOS. It cost 10 times (in terms of minute of compute) the price of a linux minute

</p>
</details>

### What are the different types of support of Enterprise Support ?

<details><summary>show</summary>
<p>

- GitHub Enterprise Support (Included with Enterprise Cloud and Enterprise Server)
- GitHub Enterprise Premium support
- GitHub Enterprise Premium Plus support

</p>
</details>

### What kind of info can you find using Audit Log API ?

<details><summary>show</summary>
<p>

- Accesses your organization or repository settings.
- Changes permissions.
- Adds or removes users in an organization, repository, or team.
- Promotes users to admin.
- Changes permissions of a GitHub App.

</p>
</details>

### Does the support covers account, server, and security issues ?

<details><summary>show</summary>
<p>

No, it covers Account, Security, and Abuse issues

</p>
</details>

### Does GitHub Enterprise Server contains GitHub Actions feature ?

<details><summary>show</summary>
<p>

Yes. It is disabled by default but it's here and it contains already some built-in actions created by GitHub. It does NOT require acces to Internet to work because you can sync/download the Actions locally.

</p>
</details>

### Does GitHub Enterprise Server contains GitHub Packages feature?

<details><summary>show</summary>
<p>

yes

</p>
</details>

## Manage access and permissions based on membership

### What are the two roles available at team level  ?

<details><summary>show</summary>
<p>

- member
- maintainer

</p>
</details>

### What are the three roles available at organization level  ?

<details><summary>show</summary>
<p>

- owner
- member
- billing manager

</p>
</details>


### Which role access should you give to a contributor with full control on the repo except access to sensitive or destructive actions  ?

<details><summary>show</summary>
<p>

**maintainer** because **admin** role would for instance allow to delete a repo

</p>
</details>

### What is the appropriate repository permission level for contributors who will actively push changes to your repository

<details><summary>show</summary>
<p>

**write**

</p>
</details>

### By default, can all users of an organization see all repositories ?

<details><summary>show</summary>
<p>

Yes if the "Read" access is defined as default role in "base permissions" in the organization's settings

</p>
</details>

### Which role allows a person to manage issues of a repository without any write rights ?

<details><summary>show</summary>
<p>

**triage**

</p>
</details>

### What is a deploy key ?

<details><summary>show</summary>
<p>

You can launch projects from a repository on GitHub.com to your server by using a deploy key, which is an SSH key that grants access to a single repository. GitHub attaches the public part of the key directly to your repository instead of a personal account, and the private part of the key remains on your server.

</p>
</details>

## Enable secure software development and ensure compliance

### How can you exclude sensitive files from your repository ?

<details><summary>show</summary>
<p>

One technique to help avoid the majority of this risk is to build and maintain **.gitignore** files

</p>
</details>

### Once a sensitive data has been commited, can you erase the history to keep the data secret again ?

<details><summary>show</summary>
<p>

**No**. You can overwrite a commit but you must consider the data unsecure once it has been commited. If it's a secret/password, then you must renew it.

</p>
</details>

### What is the starting point to enforce certain workflows like passing security checks ?

<details><summary>show</summary>
<p>

You should use [branch protection rules](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/managing-a-branch-protection-rule).

</p>
</details>

### How can you automatically assign specific persons as reviewers when a part of the code is modified ?

<details><summary>show</summary>
<p>

You should use [CODEOWNERS](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners#codeowners-syntax) files.

</p>
</details>

### What is the simplest way to prevent the creation of public repository  ?

<details><summary>show</summary>
<p>

At the organization level, in "Member privileges" settings, disallow the creation of public repositories.

</p>
</details>

### If you plan to communicate about your security policy, like disclosing vulnerabilities, where should you store your policy publicly ?

<details><summary>show</summary>
<p>

In the root of your repository in a file named SECURITY.md.

</p>
</details>


### Using branch protection rule, which setting prevents merge commits ?

<details><summary>show</summary>
<p>

**Require linear history** ([see documentation](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/about-protected-branches#require-linear-history))

</p>
</details>

### In which part of your repository can you find the dependency graph listing all the packages your repo depends on ?

<details><summary>show</summary>
<p>

In the **Insights** tab and then **Dependency graph**.
</p>
</details>


### Which feature of GitHub scan your repo and alerts you in case of detected vulnerabilities in your dependencies ?

<details><summary>show</summary>
<p>

**GitHub Security Advisories**.
</p>
</details>


### Which feature of GitHub scan your repo and alerts you in case of detected vulnerabilities and automatically create a pull request to fix it ?

<details><summary>show</summary>
<p>

**Dependabot**.
</p>
</details>

### What is the feature which help to prevent to commit a secret ?

<details><summary>show</summary>
<p>

If you want to act **before** a commit, you must use pre-commit hook which allow to scan the code before the commit.

</p>
</details>

### Which tools can be used to tamper Git history and erase sensitive data ?

<details><summary>show</summary>
<p>

**git filter-repo** & **BFG Repo-Cleaner**

</p>
</details>

### Which two pieces of information should be included in a security advisory ?

<details><summary>show</summary>
<p>

**Product affected** and **severity**

</p>
</details>

### You have a workflow secret named MY_SECRET. What if the format to call it from the workflow ?

<details><summary>show</summary>
<p>

```yaml
steps:
  - name: Hello world action
    with: # Set the secret as an input
      super_secret: ${{ secrets.MY_SECRET }}
```

</p>
</details>

## Manage GitHub Actions

### Which two files are mandatory when create a workflow template ?

<details><summary>show</summary>
<p>

- a workflow file with a yml extension (**my-workflow**.yml)
- a propertires files with ".properties.json" extention (**my-workflow**.properties.json)

Both files must have the same name.

</p>
</details>

### Which placeholder keyword allow to inject the current default branch in a workflow template ?

<details><summary>show</summary>
<p>

**$default-branch**

```yaml
on:
  push:
    branches: [ $default-branch ]
```

</p>
</details>

### Can you prevent users to use Actions from the marketplace ?

<details><summary>show</summary>
<p>

Yes, using Policies and restricting to local actions only.

</p>
</details>

### Can you allow users to only used actions created by GitHub or verified creators ?

<details><summary>show</summary>
<p>

Yes, using Policies and restricting to specific actions (menu "Allow select actions").

</p>
</details>

### Are the Actions created by GitHub automatically present in GitHub Enterprise Server ?

<details><summary>show</summary>
<p>

Yes, but they may not be the last version of them.

</p>
</details>

### Which feature allow to provide already premade templaces to users when they want to create a workflow ?

<details><summary>show</summary>
<p>

It's called a **workflow template**

</p>
</details>

### What are the default labels applied to a self-hosted agent ?

<details><summary>show</summary>
<p>

- *self-hosted*
- the os: *linux*, *windows*, or *macOS*
- the CPU architecture: *x64* , *ARM*, or *ARM64*

</p>
</details>

### How do you enforce your workflow running on a specific self-hosted agent running on Linux with ARM ?

<details><summary>show</summary>
<p>

```yaml
runs-on: [self-hosted, linux, ARM64]
```

</p>
</details>

### In which folder of a self-hosted agent can you find logs to debug the behavior of the runner ?

<details><summary>show</summary>
<p>

In the *_diag* folder.

</p>
</details>

## Manage GitHub Packages

### Can you upload containers images in GitHub Packages ?

<details><summary>show</summary>
<p>

Yes.

</p>
</details>

### What is the docker command to publish a container image on GitHub Packages ?

<details><summary>show</summary>
<p>

```bash
docker push ghcr.io/OWNER/IMAGE_NAME:latest
```

</p>
</details>

### What are the (programming) package managers supported by GitHub Packages  ?

<details><summary>show</summary>
<p>

- npm, a NodeJS package manager
- NuGet, the .NET package manager
- RubyGems
- Maven and Gradle, two package managers for Java

</p>
</details>

### In which scenarios should you NOT use GitHub Packages ?

- [ ] When I want to share code between methods of my application.
- [ ] When I want to share container images among developers of your team.
- [ ] When I want to publish a small code library as an open-source project.

<details><summary>show</summary>
<p>

**When I want to share code between methods of my application**

</p>
</details>
