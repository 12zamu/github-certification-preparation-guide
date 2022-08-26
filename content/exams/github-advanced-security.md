# GitHub Advanced Security

> These are **NOT real questions** from the exam but quite close enough to what you can get to help you to prepare it and obtain the certification

## Skills measured

- [Describe the GitHub Advanced Security features and functionality](#describe-github-advanced-security-best-practices-results-and-how-to-take-corrective-measures)  (10% of the exam)
- [Configure and use secret scanning](#configure-and-use-code-scanning) (10% of the exam)
- [Configure and use dependency management](#configure-and-use-dependency-management) (15% of the exam)
- [Configure and use code scanning](#configure-and-use-code-scanning) (15% of the exam)
- [Use code scanning with CodeQL](#use-code-scanning-with-codeql) (20% of the exam)
- [Describe GitHub Advanced Security best practices, results, and how to take corrective measures](#describe-github-advanced-security-best-practices-results-and-how-to-take-corrective-measures) (18% of the exam)
- [Configure GitHub Advanced Security tools in GitHub Enterprise](#configure-github-advanced-security-tools-in-github-enterprise) (12% of the exam)

## Describe the GitHub Advanced Security features and functionality

### GitHub Advanced Security focuses on protecting your organization in three primary areas. Which are?

<details><summary>show</summary>
<p>

- Supply chain
- Code
- Environments

</p>
</details>

### Which area of focus does GitHub dependency management belong to?

- [ ] Code scanning
- [ ] Policies
- [ ] Supply chain

<details><summary>show</summary>
<p>

Supply chain

</p>
</details>

### What is the name of the feature which provides Code Scanning on GitHub?

<details><summary>show</summary>
<p>

CodeQL

</p>
</details>

### What does the term 'shifting left' mean?

<details><summary>show</summary>
<p>

Incorporating security principles early in the software development lifecycle

</p>
</details>

### What is the features which provides a safe space for code maintainers to discuss how to best address errors and vulnerabilities found in the codebase ?

<details><summary>show</summary>
<p>

security advisories
</p>
</details>

### What are the main security features availables with GitHub Advanced Security ?

<details><summary>show</summary>
<p>

- Dependabot
- Code scanning (CodeQL or 3rd party)
- Secret scanning

</p>
</details>

## Configure and use secret scanning

### Can secret scanning detect a specific connection string for a Cloud provider such as Azure or AWS ?

<details><summary>show</summary>
<p>

Yes. A lot of [providers formats](https://docs.github.com/en/code-security/secret-scanning/secret-scanning-patterns) can be detected within the source code.

</p>
</details>

### Which branch(s) is (are) scanned to detect the secrets ?

- [ ] the main/master branch
- [ ] the default branch
- [ ] the active branch (last 30 days)
- [ ] all the branchs

<details><summary>show</summary>
<p>

All the branchs

</p>
</details>

### How many days in Git history are scanned ?

<details><summary>show</summary>
<p>

ALL history is scanned.

</p>
</details>

### In which tab of the repository can you find the detected secrets  ?

<details><summary>show</summary>
<p>

In the **Security** > **Secret scanning** screen.

</p>
</details>

### Can you add custom patterns to detect specific secrets ?

<details><summary>show</summary>
<p>

Yes, you can add up to 100 custom patterns for a private repository and 500 for an organization.

</p>
</details>

### Can you prevent a user to commit a secret ?

<details><summary>show</summary>
<p>

No, or you need a local software to scan the code before the commit (pre-commit).

</p>
</details>

### Can you prevent to push a commit which contain a secret ?

<details><summary>show</summary>
<p>

Yes, you can enable [**push protection**](https://docs.github.com/en/enterprise-cloud@latest/code-security/secret-scanning/protecting-pushes-with-secret-scanning) which scans the content of the commit before allowing it on the server.

</p>
</details>

### Can a user bypass push protection?

<details><summary>show</summary>
<p>

Yes, but then it generates an alert in the Security tab, a bypass even is added to the audit log and an email is sent to org owners, security managers and repo administrators.

</p>
</details>

### Can secret scanning rotate your detected secret automatically for you ?

<details><summary>show</summary>
<p>

No but in some cases, GitHub also notifies the service provider who issued the secret. The service provider can then take any appropriate action like revoking the secret, issuing a new secret or reaching out to you directly depending on the associated risks to you or them.

</p>
</details>

### Can you have secret scanning for free ?

<details><summary>show</summary>
<p>

Yes, it is enabled by default on all public repositories. It **cannot be configured or turned off**. Secret scanning **must be enabled manually** on private repositories but it then a paid option.

</p>
</details>

### What is the best way to enable secrets scanning at scale ?

<details><summary>show</summary>
<p>

You can enable it at organization level to enable it by default on all private repositories.

Follow the steps below to enable secret scanning for an organization:

- In your organization, navigate to Settings > Security & analysis.
- Under Configure security and analysis features, click the Enable all button next to GitHub Advanced Security.
- Review the impact of enabling Advanced Security on all repositories and click Enable all.
- Click the Enable all button next to Secret scanning.
- Optionally enable the feature by default for new repositories in your organization, and click Enable for eligible repositories.


</p>
</details>

### What is the name of the file to list paths/files to exclude from secret scanning ?

<details><summary>show</summary>
<p>

The file **.github/secret_scanning.yml** and then using the keyword **paths-ignore**

```yaml
paths-ignore:
  - "foo/bar/*.js"
```

> If there are more than 1,000 entries in paths-ignore, secret scanning will only exclude the first 1,000 directories from scans.
  If secret_scanning.yml is larger than 1 MB, secret scanning will ignore the entire file.

</p>
</details>

## Configure and use dependency management

### What is the name of the dependency scanning feature of GitHub ?

<details><summary>show</summary>
<p>

Dependency graph (which is different from Dependabot!)

</p>
</details>

### Does Dependency graph scan your source code ?

<details><summary>show</summary>
<p>

Not really. It scans the files of your repository and is looking for dependencies/packages files (package.json, package.config, pom.xml, etc) but the code your wrote yourself is not scanned by this tool.

</p>
</details>

### What are the dependencies checked by Dependency graph ?

<details><summary>show</summary>
<p>

- The direct dependencies explicitly defined in a manifest or lock file.
- The indirect dependencies, also known as transitive dependencies or subdependencies, which are dependencies used by packages that are dependencies of your project.
- The vendored dependencies that are checked into a specific directory in your repository but aren't referenced in your manifest file (only available for some package managers).

</p>
</details>

### What is the goal of Dependabot ?

<details><summary>show</summary>
<p>

Dependabot keeps your dependencies up to date by informing you of any security vulnerabilities in your dependencies, and automatically opens pull requests to upgrade your dependencies to the next available secure version when a Dependabot alert is triggered, or to the latest version when a release is published.

</p>
</details>

### What are the supported packages managers (list at least 5) ?

<details><summary>show</summary>
<p>

- composer (PHP)
- nuget (.Net)
- maven (Java/Scala)
- npm (JavaScript)
- PIP (Python)
- yarn (JavaScript)
- RubyGems (Ruby)
- Go modules (Go) - ONLY for GitHub Enterprise Security versions above 3.2
- Python Poetry (Python) - ONLY for GitHub Enterprise Security versions above 3.3

</p>
</details>

### Where can you find the list of last known vulnerabilities in the world ?

<details><summary>show</summary>
<p>

You can use the [GitHub Advisory Database](https://github.com/advisories)

</p>
</details>

### Can the contributors of a repository access to Dependabot alerts ?

<details><summary>show</summary>
<p>

No, by default only repo owners and administrators can access them. But administrators and owners can also grant other teams and users with access to the repository, permissions to view and dismiss Dependabot alerts by adding them in **Access to alerts**"** section.

</p>
</details>

### Which file allow to configure Dependabot behavior such as interval scanning or version control  ?

<details><summary>show</summary>
<p>

dependabot.yml

</p>
</details>

### Which channels can be used for Dependabot notifications ?

<details><summary>show</summary>
<p>

- By email, an email is sent when Dependabot is enabled for a repository, when a new manifest file is committed to the repository, and when a new vulnerability with a critical or high severity is found.
- In the user interface, a warning is shown in your repository's file and code views if there are any vulnerable dependencies.
- On the command line, warnings are displayed as callbacks when you push to repositories with any vulnerable dependencies.
- In your inbox, as web notifications. A web notification is sent when Dependabot is enabled for a repository, when a new manifest file is committed to the repository, and when a new vulnerability with a critical or high severity is found.
- On GitHub for mobile, as web notifications.

</p>
</details>

### How can you retrieve detected vulnerabilities programmatically ?

<details><summary>show</summary>
<p>

Using GitHub GraphQL

```graphql
query {
  repository(name: "${repo}", owner: "${org}") { 
    vulnerabilityAlerts(first: 100) {
      nodes { 
        createdAt 
        dismissedAt 
        securityVulnerability { 
          package { 
            name 
          } 
          severity 
          vulnerableVersionRange 
          advisory { 
            ghsaId 
            publishedAt 
            identifiers { 
              type 
              value 
            } 
          } 
        } 
      } 
    } 
  }
}
```

</p>
</details>

## Configure and use code scanning

### What are the supported langages of code scanning ?

<details><summary>show</summary>
<p>

- C/C++
- C#
- Go
- Java
- JavaScript/TypeScript
- Python
- Ruby

</p>
</details>

### Which file format permits to integrate results for a 3rd party scanning tool ?

<details><summary>show</summary>
<p>

The **SARIF** format (Static Analysis Results Interchange Format)

</p>
</details>

### Which GitHub action allow to upload a SARIF file ?

<details><summary>show</summary>
<p>

**codeql-action/upload-sarif**

```yaml
  steps:
    - name: Upload SARIF file
      uses: github/codeql-action/upload-sarif@v1
      with:
        sarif_file: results.sarif 
```

</p>
</details>

### What is the difference between dismiss and delete a code scanning alert ?

<details><summary>show</summary>
<p>

When dismissing an alert:

- It's dismissed in all branches
- The alert is removed from the number of current alerts for your project
- The alert is moved to the "Closed" list in the summary of alerts. You can reopen it from here, if required
- The reason why you closed the alert is recorded
- Next time code scanning runs, the same code won't generate an alert

When deleting an alert:

- It's deleted in all branches
- The alert is removed from the number of current alerts for your project
- It is not added to the "Closed" list in the summary of alerts
- If the code that generated the alert stays the same, and the same code scanning tool runs again without any configuration changes, the alert will be shown again in your analysis results

</p>
</details>

## Use code scanning with CodeQL

### What are the two ways of running CodeQL on GitHub ?

<details><summary>show</summary>
<p>

- Add the CodeQL workflow to your repository. This uses the github/codeql-action to run the CodeQL CLI.
- Run the CodeQL CLI directly in an external CI system and upload the results to GitHub.

</p>
</details>

## Describe GitHub Advanced Security best practices, results, and how to take corrective measures

### What is the name of the file to declare the security policy of a repository ?

<details><summary>show</summary>
<p>

SECURITY.md

</p>
</details>

### Which screen allows you to have a clear vision of all security issues in your organization ?

<details><summary>show</summary>
<p>

the **Security Overview** screen.
</p>
</details>

### Is security overview available for public repositories ?

<details><summary>show</summary>
<p>

The Security Overview is only available on private repositories with GitHub Advanced Security

</p>
</details>

### How can you give specific rights to GITHUB_TOKEN to automate security workflows ?

<details><summary>show</summary>
<p>

You have to add a **permissions** section in your workflow YAML file.

```yaml
name: Create issue on commit

on: [ push ]

jobs:
  create_commit:
    runs-on: ubuntu-latest
    permissions:
      issues: write
    steps:
      - name: Create issue using REST API
        run: |
```

</p>
</details>

## Configure GitHub Advanced Security tools in GitHub Enterprise

### What are the 3(+1) main features of GitHub Advanced Security ?

<details><summary>show</summary>
<p>

- **Code scanning**: Automatically detect common vulnerabilities and coding errors.
- **Secret scanning**: Receive alerts when secrets or keys are checked in, exclude files from scanning, and define up to 100 custom patterns.
- **Dependency review**: Show the full impact of changes to dependencies and see details of any vulnerable versions before you merge a pull request.
- **Security Overview**: Review the security configuration and alerts for an organization and identify the repositories at greatest risk.

</p>
</details>

### What is the pricing model for GitHub Advanced Security ?

<details><summary>show</summary>
<p>

Your pay one license (seat) for each active commiter in private/internal repositories.

</p>
</details>

### How enable GitHub Advanced Security for GitHub Enterprise Server ?

<details><summary>show</summary>
<p>

This can be done two ways: via the GitHub user interface or via the administrative shell (SSH). You need to ensure that your license for GitHub Enterprise Server has been upgraded to include GitHub Advanced Security and you have uploaded it to your GitHub Enterprise Server instance and you need to check for the technical prerequisites.

</p>
</details>