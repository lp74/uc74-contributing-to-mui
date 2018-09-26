# Contributing to MUI #

Here are the guidelines we would like you to follow

> This work is in progress!!!

## Summary

- [MUI Repository](#repository)
- [MUI Catalogue](#catalogue)
- [Specification and guidelines](#specification)
- [New features](#new-features)
- [Bug fixes](#bug-fixes)
- [Commit message guidelines](#commit-message-guidelines)
- [Pull requests (PR)](#pull-requests)
- [Review](#review)
- [Coding rules](#coding-rules)
- [Definition of done](#definition-of-done)
- [Links](#links)

## <a name="repository"></a> MUI repository

To clone the repository locally

```shell
$ git clone git@itteb-s-git0001.it.abb.com:FeasibilityStudy/MultiplatformUI
```

> To clone the repository, you need your authorised credentials.
> Please, ask the administrator.

## <a name="catalogue"></a> MUI catalogue

> **TODO** Deploy MUI catalogue

## <a name="specification"></a> Specification and guidelines

We provide you with a set of documents and tools to complete your work and to successfully contribute to MUI:

- User stories (if applicable),
- Mock-ups and prototypes (if applicable),
- [The MUI catalog of patterns, CSS classes and componentes](http://...),
- [Common UX principles](https://softwareui.abb.com/)

## <a name="new-features"></a> New features

Here, we describe how to add new features to the MUI project.

1. Checkout master branch

```shell
$ git checkout master
```

2. incorporate changes from the origin/master branch

```shell
$ git pull origin/master
```
3. create a new branch named **feature-n-short-description** where:
    - n is the redmine issue-id,
    - short-description is the redmine issue-title (whenever applicable).

```shell
$ git checkout -b feature-n-short-description
```

4. develop the new feature
    - using:
        - MUI CSS classes,
        - MUI HTML tags,
        - MUI (AngularJS) components,
    - using our [coding rules](#coding-rules),
    - developing and running unit-test and e2e tests (whenever applicable),
    - complying with the Common UX principles and the provided mock-up (if available),

5. commit your work following the [Commit message guidlelines](#commit-message-guidelines)

> Please, checkout our [definition of done](#definition-of-done)

```shell
$ git add . # it depends on your feature, pay attention to the files that you add
$ git commit -m "feature(scope): succint description of the feature (issue-id)"
```

6. rebase your work on to master

```shell
$ git fetch --all
$ git rebase origin/master
```
> rebasing your work on to origin/master is very important:
> - to keep your work aligned with the master branch, 
> - to keep the git log clean and more easy, and
> - to avoid conflicts and failures.  

After rebasing your work, fix eventual conflicts (if needed) and keep tests successful.

7. Push your work upstream

```shell
$ git push origin feature-n-short-description
```

8. Make a pull request
Checkout [Pull requests (PR)](#pull-requests)

## <a name="bug-fixes"></a> Bug fixes

Bug fixing procedure is similar to the [New features](#new-features) procedure, but

3. create a new branch named **fix-n-short-description** where:
    - n is the redmine issue-id,
    - short-description is the redmine issue-title (whenever applicable).

5. commit your work following the [Commit message guidlelines](#commit-message-guidelines)

> Please, checkout our [definition of done](#definition-of-done)

```shell
$ git add . # it depends on your fix, pay attention to the files that you add
$ git commit -m "fix(scope): succint description of the fix (issue-id)"
```

## <a name="commit-message-guidelines"></a> Commit message guideline

### Commit Message Format
Each commit message consists of a **header**, a **body** and a **footer**.  The header has a special
format that includes a **type**, a **scope** and a **subject**:

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

The **header** is mandatory. The body and the footer are optional.

> Any line of the commit message cannot be longer 100 characters! This allows the message to be easier to read in various git tools.

### Type
Must be one of the following:

* **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
* **ci**: Changes to our CI configuration files and scripts (example scopes: grunt, packages, bower, bash script )
* **docs**: Documentation only changes
* **feat**: A new feature
* **fix**: A bug fix
* **perf**: A code change that improves performance
* **refactor**: A code change that neither fixes a bug nor adds a feature
* **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
* **test**: Adding missing tests or correcting existing tests

### Scope
The scope should be the name of the affected module

The following are examples:

* **abb.controls.cux-buttons**
* **abb.controls.cux-selectors**
* **abb.components.cux-charts**

### Subject
The subject contains a succinct description of the change:

* use the imperative, present tense: "change" not "changed" nor "changes"
* don't capitalize the first letter
* no dot (.) at the end

### Body
Just as in the **subject**, use the imperative, present tense: "change" not "changed" nor "changes".
The body should include the motivation for the change and contrast this with previous behavior.

### Footer
The footer should contain any information about **Breaking Changes** and is also the place to
reference redmine issues that this commit **Closes**.

**Breaking Changes** should start with the word `BREAKING CHANGE:` with a space or two newlines. The rest of the commit message is then used for this.

## <a name="pull-requests"></a> Pull requests (PR)

Submit your pull request by mail:

- to: luca.---@it.abb.com
- cc: francesca.--@it.abb.com
- subject and body: pull request {issued-id} - {issue-short-description}

you can add notes.

## <a name="review"></a> Review

After the pull request submission, our UI team will verify your work.

We'll check:

- the use of existing MUI patterns, CSS classes, components ... and so on,
- the compliance with the ABB common UX guidelines and the provided specifications (mock-up and specifications),
- the compliance with the coding guidelines (code format included),
- the unit tests (TDD) and end to end tests (E2E).

> Our goal is to develop new interesting feature and bug fixes; We hope that your code passes all tests. Good Luck!

If any of the checks fails, you will be notified soon. One ore more issues will be open in redmine and you will be request to work on them.
Our team might comment the code in the feature branch to highlight the issue or to show a suggested solution, or a common pattern.
Once you are done with all the issues you can submit another pull request.

## <a name="Coding rules"></a>Coding rules
[Coding rules](coding-rules.md)

## <a name="definition-of-done"></a>Definition of done

> **TODO** to be continued ...

## <a name="links"></a>Links
- [ABB MUI online catalogue]() ... to be done
- [ABB Redmine](http://monitoring-helpdesk.it.abb.com)
- [ABB VersionOne](https://versionone.abb.com)
- [ABB Common UX style guide](https://stsint.abb.com)
- [Contributing to angular](https://github.com/angular/angular/blob/master/CONTRIBUTING.md)
- [Angular style guide](https://github.com/johnpapa/angular-styleguide)