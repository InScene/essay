# Git Guide

 - [Branching](#branch)
 - [Issues and Bugs](#issue)
 - [Feature Requests](#feature)
 - [Submission Guidelines](#submit)
   * [Submitting Issue](#submit-issue)
   * [Submitting Pull Request](#submit-pr)
 - [Commit Message Format](#commit)
 - [CI/CD](#cicd)
   * [Continuous Integration](#ci)
   * [Continuous Deployment](#cd)
     - [Semantic Release](#sr)

## <a name="branch"></a> Branching
Inspired by [Couchcamote](https://dev.to/couchcamote/git-branching-name-convention-cch) and [vtenq](https://gist.github.com/vtenq/7a93687108cb876f884c3ce75a8a8023#file-git-workflow-md).

|   Instance  | Branch |   Description |
|:-----------:|:------:|:-------------:|
| Main      | main | The production branch, if the repository is published, this is the default branch being presented. |
| Fix     | fix/ | If there is a need to fix a blocker, do a temporary patch, apply a critical framework or configuration change that should be handled immediately, it should be created as a fix. It does not follow the scheduled integration of code and could be merged directly to the production branch, then on the development branch later. |
| Release     | release/ |  Branch for tagging a specific release version. Git also supports tagging a specific commit history of the repository. A release branch is used if there is a need to make the code available for checkout or use. |
| Development | develop/   | All new features and bug fixes should be brought to the development branch. Resolving developer codes conflicts should be done as early as here. |
| Feature     | feat/  | Any code changes for a new module or use case should be done on a feature branch. This branch is created based on the current development branch. When all changes are Done, a Pull Request/Merge Request is needed to put all of these to the development branch. |

[Link](https://backlog.com/git-tutorial/branching-workflows/) to the image reference.
![Branching](https://github.com/Sentenz/general/blob/main/image/branching_workflows.png)

The central repo holds two main branches with an infinite lifetime:

- main
- develop

We consider **origin/main** to be the main branch where the
source code of HEAD always reflects a _production-ready_ state.

We consider **origin/develop** to be the main branch where the 
source code of HEAD always reflects a state with the latest
delivered development changes for the next release. Some would
call this the "integration branch".

Direct push to **main** and **develop** branches is forbidden.

Every push to **develop** branch will deploy to staging.

Every push to **main** will create a new release and deploy to production.

Pull requests of **feature** branches ONLY into **develop** branch.

Before merging a PR into **develop** branch the CI should pass (merge button disabled untill it's done).

### Feature branch

- May branch off from: **develop**
- Must merge back into: **develop**
- Branch naming convention: **feat/ISSUETYPE-ID-short_describe**

#### Creating of a feature branch

When starting work on a new feature, branch off from the develop branch.

```
$ git checkout -b feat/ISSUE-ID-short_name develop
Switched to a new branch "feat/ISSUE-ID-short_name"
```

#### Merging a finished feature into develop

To merge feature branch into **develop** you should push your local branch
to origin and then create a PR into **develop**. This is done to user power
of CI and do all checks automatically before merging.

```
# Push to origin
git push -u origin feat/ISSUE-ID-short_name
```

When PR is created CI must run. In most cases it will have the following jobs _lint_ _test_ _build_.

Merge button should be disabled until all checks pass.
(Optinally) Merge button can also be disabled until PR gets two approves or it can be just an agreement in a team.

##### Squash or Merge or Rebase

###### Squash

Tracking how feature was developed is good thing, but only in the
ideal world where it includes just a few commits and every one is meaningful.

Feature branches are frequently considered as "fat" branches that contain a lot
of commit sthat make history unclean and unconcise, for example:

- feat: add new feture
- fix: something I forgot to do
- fix: and again
- chore: adopt review changes
- chore: adopt review changes 2
- chore: final commit, I promise

In this case no real need to see these commits in **develop** branch.
Squashing will combine all your commits into one.

To sqush changes select "Squash and merge" option on PR merge button in github.

TBD: how to squash changes locally?

###### Rebase

It's possible to rebase commits from feature (or fix) branch into develop if **ALL** of them are self-descriptive (have meaningful commit comment and are responsible for their purpose).

###### Merge

It's not allowed to merge feature/fix/whatever branch into develop so that git history will be clean and without merge commits.

### Release

In most cases release will be done in the following way:

- create PR from **develop** into **main**
- merge it with merge commit (TBD: commit message) (NO squash and rebase)
- ci should pass
- new release created and deloyed to production (TBD: auto vs manual deploy)

Sometimes release should be done in a few days with the _current_ state, but we do not want to block other developers from merging new features into **develop** branch. In this case we can borrow idea of a release branch from git flow.

- create new branch from **develop** (TBD: naming convention, i.e. release-v1.2.x)
- now we can continue merging into develop branch
- when we want release the stuff we create a PR from this **release** branch into **main**
- then the flow as described above when merging develop into main

#### Fix

When develop branch already has new features and a _fix_ is needed in production then:

- create a fix branch from **main**
- commit fix with commit message like `fix: what was fixed`
- create PR into main (after merging release process will be triggered)
- create PR into develop (CI will run on PR and after merge deployed to staging)
- delete fix branch

**NOTE:** merging a fix branch into develop and main should be done with _merge commit_.

## <a name="issue"></a> Found a Bug?

If you find a bug in the source code, you can help us by [submitting an issue](#submit-issue) to our [GitHub Repository][github].
Even better, you can [submit a Pull Request](#submit-pr) with a fix.


## <a name="feature"></a> Missing a Feature?
You can *request* a new feature by [submitting an issue](#submit-issue) to our GitHub Repository.
If you would like to *implement* a new feature, please consider the size of the change in order to determine the right steps to proceed:

* For a **Major Feature**, first open an issue and outline your proposal so that it can be discussed.
  This process allows us to better coordinate our efforts, prevent duplication of work, and help you to craft the change so that it is successfully accepted into the project.

  **Note**: Adding a new topic to the documentation, or significantly re-writing a topic, counts as a major feature.

* **Small Features** can be crafted and directly [submitted as a Pull Request](#submit-pr).


## <a name="submit"></a> Submission Guidelines


### <a name="submit-issue"></a> Submitting an Issue

Before you submit an issue, please search the issue tracker, maybe an issue for your problem already exists and the discussion might inform you of workarounds readily available.

We want to fix all the issues as soon as possible, but before fixing a bug we need to reproduce and confirm it.
In order to reproduce bugs, we require that you provide a minimal reproduction.
Having a minimal reproducible scenario gives us a wealth of important information without going back and forth to you with additional questions.

A minimal reproduction allows us to quickly confirm a bug (or point out a coding problem) as well as confirm that we are fixing the right problem.

We require a minimal reproduction to save maintainers' time and ultimately be able to fix more bugs.
Often, developers find coding problems themselves while preparing a minimal reproduction.
We understand that sometimes it might be hard to extract essential bits of code from a larger codebase but we really need to isolate the problem before we can fix it.

Unfortunately, we are not able to investigate / fix bugs without a minimal reproduction, so if we don't hear back from you, we are going to close an issue that doesn't have enough info to be reproduced.

You can file new issues by selecting from our [new issue templates](https://github.com/angular/angular/issues/new/choose) and filling out the issue template.


### <a name="submit-pr"></a> Submitting a Pull Request (PR)

Before you submit your Pull Request (PR) consider the following guidelines:

1. Search [GitHub](https://github.com/angular/angular/pulls) for an open or closed PR that relates to your submission.
   You don't want to duplicate existing efforts.

2. Be sure that an issue describes the problem you're fixing, or documents the design for the feature you'd like to add.
   Discussing the design upfront helps to ensure that we're ready to accept your work.

3. Please sign our [Contributor License Agreement (CLA)](#cla) before sending PRs.
   We cannot accept code without a signed CLA.
   Make sure you author all contributed Git commits with email address associated with your CLA signature.

4. Fork the angular/angular repo.

5. Make your changes in a new git branch:

     ```shell
     git checkout -b my-fix-branch master
     ```

6. Create your patch, **including appropriate test cases**.

7. Follow our [Coding Rules](#rules).

8. Run the full Angular test suite, as described in the [developer documentation][dev-doc], and ensure that all tests pass.

9. Commit your changes using a descriptive commit message that follows our [commit message conventions](#commit).
   Adherence to these conventions is necessary because release notes are automatically generated from these messages.

     ```shell
     git commit --all
     ```
    Note: the optional commit `-a` command line option will automatically "add" and "rm" edited files.

10. Push your branch to GitHub:

    ```shell
    git push origin my-fix-branch
    ```

11. In GitHub, send a pull request to `angular:master`.


#### Addressing review feedback

If we ask for changes via code reviews then:

1. Make the required updates to the code.

2. Re-run the Angular test suites to ensure tests are still passing.

3. Create a fixup commit and push to your GitHub repository (this will update your Pull Request):

    ```shell
    git commit --all --fixup HEAD
    git push
    ```

    For more info on working with fixup commits see [here](docs/FIXUP_COMMITS.md).

That's it! Thank you for your contribution!


##### Updating the commit message

A reviewer might often suggest changes to a commit message (for example, to add more context for a change or adhere to our [commit message guidelines](#commit)).
In order to update the commit message of the last commit on your branch:

1. Check out your branch:

    ```shell
    git checkout my-fix-branch
    ```

2. Amend the last commit and modify the commit message:

    ```shell
    git commit --amend
    ```

3. Push to your GitHub repository:

    ```shell
    git push --force-with-lease
    ```

> NOTE:<br />
> If you need to update the commit message of an earlier commit, you can use `git rebase` in interactive mode.
> See the [git docs](https://git-scm.com/docs/git-rebase#_interactive_mode) for more details.


#### After your pull request is merged

After your pull request is merged, you can safely delete your branch and pull the changes from the main (upstream) repository:

* Delete the remote branch on GitHub either through the GitHub web UI or your local shell as follows:

    ```shell
    git push origin --delete my-fix-branch
    ```

* Check out the master branch:

    ```shell
    git checkout master -f
    ```

* Delete the local branch:

    ```shell
    git branch -D my-fix-branch
    ```

* Update your master with the latest upstream version:

    ```shell
    git pull --ff upstream master
    ```
    

## <a name="commit"></a> Commit Message Format

This specification is inspired by
 * the [Angular](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#-commit-message-format) github project
 * the [AngularJS](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit#heading=h.uyo6cb12dt6w) commit message format
 * this specifications are identical to Conventional Commits from [STYLE_GUIDE.md](STYLE_GUIDE.md).

We have very precise rules over how our Git commit messages must be formatted.
This format leads to **easier to read commit history**.

Each commit message consists of a **header**, a **body**, and a **footer**.

```
<header>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

The `header` is mandatory and must conform to the [Commit Message Header](#commit-header) format.

The `body` is mandatory for all commits except for those of scope "docs".
When the body is required it must be at least 20 characters long.

The `footer` is optional.

Any line of the commit message cannot be longer than 100 characters.


#### <a href="commit-header"></a>Commit Message Header

```
<type>(<scope>): <short summary>
  │       │             │
  │       │             └─> Summary in present tense. Not capitalized. No period at the end.
  │       │
  │       └─> Commit Scope: app|config|generated|interface|utility|tools|guide|external|
  │                          education|elements|forms|platform|upgrade|packaging|changelog|
  │                          migrations
  │
  └─> Commit Type: build|ci|docs|feat|fix|perf|refactor|test
```

The `<type>` and `<summary>` fields are mandatory, the `(<scope>)` field is optional.


##### Type

Must be one of the following:

* **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
* **ci**: Changes to our CI configuration files and scripts (example scopes: Circle, BrowserStack, SauceLabs)
* **docs**: Documentation only changes
* **feat**: A new feature
* **fix**: A bug fix
* **perf**: A code change that improves performance
* **refactor**: A code change that neither fixes a bug nor adds a feature
* **test**: Adding missing tests or correcting existing tests


##### Scope
The scope should be the name of the npm package affected (as perceived by the person reading the changelog generated from commit messages).

The following is the list of supported scopes:

* `animations`
* `bazel`
* `benchpress`
* `common`
* `compiler`
* `compiler-cli`
* `core`
* `elements`
* `forms`
* `http`
* `language-service`
* `localize`
* `platform-browser`
* `platform-browser-dynamic`
* `platform-server`
* `router`
* `service-worker`
* `upgrade`
* `zone.js`

There are currently a few exceptions to the "use package name" rule:

* `packaging`: used for changes that change the npm package layout in all of our packages, e.g. public path changes, package.json changes done to all packages, d.ts file/format changes, changes to bundles, etc.

* `changelog`: used for updating the release notes in CHANGELOG.md

* `dev-infra`: used for dev-infra related changes within the directories /scripts, /tools and /dev-infra

* `docs-infra`: used for docs-app (angular.io) related changes within the /aio directory of the repo

* `migrations`: used for changes to the `ng update` migrations.

* `ngcc`: used for changes to the [Angular Compatibility Compiler](./packages/compiler-cli/ngcc/README.md)

* `ve`: used for changes specific to ViewEngine (legacy compiler/renderer).

* none/empty string: useful for `test` and `refactor` changes that are done across all packages (e.g. `test: add missing unit tests`) and for docs changes that are not related to a specific package (e.g. `docs: fix typo in tutorial`).


##### Summary

Use the summary field to provide a succinct description of the change:

* use the imperative, present tense: "change" not "changed" nor "changes"
* don't capitalize the first letter
* no dot (.) at the end


#### Commit Message Body

Just as in the summary, use the imperative, present tense: "fix" not "fixed" nor "fixes".

Explain the motivation for the change in the commit message body. This commit message should explain _why_ you are making the change.
You can include a comparison of the previous behavior with the new behavior in order to illustrate the impact of the change.


#### Commit Message Footer

The footer can contain information about breaking changes and is also the place to reference GitHub issues, Jira tickets, and other PRs that this commit closes or is related to.

```
BREAKING CHANGE: <breaking change summary>
<BLANK LINE>
<breaking change description + migration instructions>
<BLANK LINE>
<BLANK LINE>
Fixes #<issue number>
```

Breaking Change section should start with the phrase "BREAKING CHANGE: " followed by a summary of the breaking change, a blank line, and a detailed description of the breaking change that also includes migration instructions.


### Revert commits

If the commit reverts a previous commit, it should begin with `revert: `, followed by the header of the reverted commit.

The content of the commit message body should contain:

- information about the SHA of the commit being reverted in the following format: `This reverts commit <SHA>`,
- a clear description of the reason for reverting the commit message.


## <a name="cla"></a> Signing the CLA

Please sign our Contributor License Agreement (CLA) before sending pull requests. For any code
changes to be accepted, the CLA must be signed. It's a quick process, we promise!

* For individuals, we have a [simple click-through form][individual-cla].
* For corporations, we'll need you to
  [print, sign and one of scan+email, fax or mail the form][corporate-cla].

If you have more than one GitHub accounts, or multiple email addresses associated with a single GitHub account, you must sign the CLA using the primary email address of the GitHub account used to author Git commits and send pull requests.

The following documents can help you sort out issues with GitHub accounts and multiple email addresses:

  * https://help.github.com/articles/setting-your-commit-email-address-in-git/
  * https://stackoverflow.com/questions/37245303/what-does-usera-committed-with-userb-13-days-ago-on-github-mean
  * https://help.github.com/articles/about-commit-email-addresses/
  * https://help.github.com/articles/blocking-command-line-pushes-that-expose-your-personal-email-address/

    
## <a name="cicd"></a> CI/CD
 > TODO
 
### <a name="ci"></a> Continuous Integration (CI)
 - Inspired by [Commitizen for contributors](https://github.com/commitizen/cz-cli)

### <a name="cd"></a> Continuous Deployment (CD)
 - Inspired by [Semantic release](https://github.com/semantic-release/semantic-release)

### <a name="sr"></a> Semantic Release
[semantic-release](https://github.com/semantic-release/semantic-release) is meant to be executed on the CI environment after every successful build on the release branch.

[FAQ](https://github.com/semantic-release/semantic-release/blob/master/docs/support/FAQ.md)

<strong>Triggering a release</strong> for each new commits added to one of the release branches (for example main, develop, feature), with git push or by merging a pull request or merging from another branch, a CI build is triggered and runs the semantic-release command to make a release if there are codebase changes since the last release that affect the package functionalities.
semantic-release offers various ways to control the timing, the content and the audience of published releases. See example workflows in the following recipes:
* [Using distribution channels](https://github.com/semantic-release/semantic-release/blob/master/docs/recipes/distribution-channels.md)
* [Maintenance releases](https://github.com/semantic-release/semantic-release/blob/master/docs/recipes/maintenance-releases.md)
* [Pre-releases](https://github.com/semantic-release/semantic-release/blob/master/docs/recipes/pre-releases.md)

Lint commit messages with [commitlint](https://github.com/conventional-changelog/commitlint). Alternatively, you can run [Commitlint Github Action](https://github.com/wagoid/commitlint-github-action) in the CI workflow.

Links to implement semantic release into github workflow
 * [How to Automate Project Versioning and Releases with Continuous Deployment](https://css-tricks.com/how-to-automate-project-versioning-and-releases-with-continuous-deployment/).
 * [Continuous Deployment with Semantic Release and GitHub Actions](https://www.wizeline.com/blog-continuous-deployment-with-semantic-release-and-github-actions/).
