# GitHub Actions

> These are **NOT real questions** from the exam but quite close enough to what you can get to help you to prepare it and obtain the certification

## Skills measured

- [Author and maintain workflows](#author-and-maintain-actions) (40% of the exam)
- [Consume workflows](#consume-workflows) (20% of the exam)
- [Author and maintain actions](#manage-github-actions-for-the-enterprise) (25% of the exam)
- [Manage GitHub Actions for the enterprise](#manage-github-actions-for-the-enterprise) (15% of the exam)

## Author and maintain workflows

### How to trigger a workflow when a commit is done on the main branch ?

<details><summary>show</summary>
<p>

```yaml
on:
  push:
    branches:
      - main
```

</p>
</details>

### How to trigger a workflow when a pull request is done on the main branch ?

<details><summary>show</summary>
<p>

```yaml
on:
  pull_request:
    branches:
      - main
```

</p>
</details>

### What is the keyword to ensure a job must run after another successful job ?

<details><summary>show</summary>
<p>

**needs**

```yaml
jobs:
  job1:
  job2:
    needs: job1
  job3:
    needs: [job1, job2]
```

</p>
</details>

### In which folder must be placed your workflows's YAML files?

<details><summary>show</summary>
<p>

```
.github/workflows
```

</p>
</details>

### Suppose you have created a bug fix on a new branch and want it to become part of the next production build generated from the main branch. What should you do next? ?

<details><summary>show</summary>
<p>

Create a pull request to merge your new branch into the main branch.

</p>
</details>

### What is the keyword to specify the operating system on which the job will be executed ?

<details><summary>show</summary>
<p>

**runs-on**

```yaml
jobs:
  print-username:
    runs-on: ubuntu-latest
    steps:
```

</p>
</details>

## Consume workflows

### What are the two "secure" ways to call a specific version of an Action

<details><summary>show</summary>
<p>

- the version (semver)
- the commit hash

```yaml
steps:
  - uses: github/my-action@v1
  - uses: github/my-action@734713bc047d87bf7eac9674765ae793478c50d3
```

The branch name is not secure as it can change at anytime. The version (using semver) is most secure IF the developer never overwrite a previous version/tag
</p>
</details>

### How to create a manual approval step in a workflow ?

<details><summary>show</summary>
<p>

There are different steps. First you need to create an **Environment** (let's call it "dev").

Then, in this environment you need to define **protection rules** and especially the rule "Required reviewers"

Finally, you need for the job you want an approval for, to reference the newly created/configured environment :

```yaml
jobs:
  build-and-publish:
    runs-on: ubuntu-latest
    steps:

  deploy-dev:
    runs-on: 'ubuntu-latest'
    environment: 'dev'
```

</p>
</details>

### Which operating systems are supported to run GitHub Actions on hosted agents?

<details><summary>show</summary>
<p>

- Linux (ubuntu)
- Windows (windows server)
- Mac OS
  
</p>
</details>

### Which trigger allows to start a workflow manually ?

<details><summary>show</summary>
<p>

**workflow_dispatch**
  
</p>
</details>

### How many combinations are created with the following matrix  ?

```yaml
jobs:
  example_matrix:
    strategy:
      matrix:
        version: [10, 12, 14]
        os: [ubuntu-latest, windows-latest]
```

<details><summary>show</summary>
<p>

6 combinations
  
</p>
</details>

### Which variable contains the name of the repository and the name of the owner ?

<details><summary>show</summary>
<p>

**GITHUB_REPOSITORY**

</p>
</details>

### Which variable contains the name of the user who triggered the workflow ?

<details><summary>show</summary>
<p>

**GITHUB_ACTOR**

</p>
</details>

### Which variable contains the name of the branch or tag which triggered the current workflow ?

<details><summary>show</summary>
<p>

**GITHUB_REF_NAME**

/!\ GITHUB_REF will contains the full name (*refs/heads/<branch_name>*)

</p>
</details>

### Do the jobs of a workflow run on the same machine ?

<details><summary>show</summary>
<p>

No. Which means that a file/anything created by a job, cannot be retrieved by a second job automatically.

</p>
</details>

### What are the three different ways to call a version of an Action

<details><summary>show</summary>
<p>

- the branch name
- the version (semver)
- the commit hash

```yaml
steps:
  - uses: github/my-action@v1
  - uses: github/my-action@main
  - uses: github/my-action@734713bc047d87bf7eac9674765ae793478c50d3
```

</p>
</details>

### How do you enforce your workflow running on a specific self-hosted agent running on Linux with ARM ?

<details><summary>show</summary>
<p>

You need to use a "route" by specifying the labels you want to target:

```yaml
runs-on: [self-hosted, linux, ARM64]
```

</p>
</details>

### You have a workflow secret named MY_SECRET. What is the format to call it from the workflow ?

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

## Author and maintain actions

### What are the three types of custom Actions you can create ?

<details><summary>show</summary>
<p>

- Docker
- JavaScript
- Composite Actions

</p>
</details>

### Which file containing metadata is mandatory ?

<details><summary>show</summary>
<p>

The metadata filename must be either action.yml or action.yaml

</p>
</details>

### Which fields are mandatory in the metadata file ?

- [ ] name
- [ ] description
- [ ] version
- [ ] inputs
- [ ] author

<details><summary>show</summary>
<p>

**Name** and **description**. **Inputs** and **author** are optional. **Version** does not exist

</p>
</details>

### How do you return values from your GitHub Actions ?

<details><summary>show</summary>
<p>

By defining outputs variables:

```yaml
outputs:
  sum: # id of the output
    description: 'The sum of the inputs'
```

</p>
</details>

### How can you customize the icon and the background color of your custom GitHub Action ?

<details><summary>show</summary>
<p>

By defining a branding section in the metadata file:

```yaml
branding:
  icon: 'award'  
  color: 'green'
```

</p>
</details>

### You want to create a custom JavaScript Action. What is the name of the main JavaScript file ?

<details><summary>show</summary>
<p>

Whatever you want as long as the name is specified in the action.yaml file:

```yaml
name: 'Hello World by me' # name of the action (mandatory)
description: 'Says hello to someone' #  simple description (mandatory)
author: 'Louis-Guillaume MORAND' # author (optional)
runs:
  using: 'node12' 
  main: 'index.js'
```

</p>
</details>

### Which ones are prerequisites to publish an action in the marketplace ?

- [ ] The action must be in a public repository.
- [ ] Each repository must contain a single action.
- [ ] The action's metadata file (action.yml or action.yaml) must be in the root directory of the repository.
- [ ] The name in the action's metadata file must be unique.

<details><summary>show</summary>
<p>

ALL of them [see documentation](https://docs.github.com/en/actions/creating-actions/publishing-actions-in-github-marketplace#about-publishing-actions).
</p>
</details>

### Which is the first step to publish an action in the marketplace ?

<details><summary>show</summary>
<p>

To create a **Release**.
</p>
</details>

## Manage GitHub Actions for the enterprise

### Can you prevent users to use Actions from the marketplace ?

<details><summary>show</summary>
<p>

Yes, using **Policies** and restricting to local actions only.

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

### Which Action allows to upload an artifact ?

<details><summary>show</summary>
<p>

```yaml
- uses: actions/upload-artifact@v3
  with:
    name: my-artifact
    path: path/to/artifact/world.txt
```

</p>
</details>

### Which Actions allows to pass an file from one job to another ?

<details><summary>show</summary>
<p>

You can use **upload-artifact** and **download-artifact**

```yaml
jobs:
  job1:
    steps:
      - uses: actions/checkout@v2

      - run: mkdir -p path/to/artifact

      - run: echo hello > path/to/artifact/world.txt

      - uses: actions/upload-artifact@v2
        with:
          name: my-artifact
          path: path/to/artifact/world.txt
  job2:
    steps:
      - uses: actions/download-artifact@v2
        with:
          name: my-artifact
```

</p>
</details>
