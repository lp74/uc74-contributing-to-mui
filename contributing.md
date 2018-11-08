# Contributing to MUI #

Here are the guidelines we would like you to follow

> This work is in progress!!!
> The interaction with Webpack should be investigated

## <a name="summary"></a> Summary

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
- [Architecture](#arch)

## <a name="repository"></a> MUI repository

To clone the repository locally

```shell
$ git clone git@itteb-s-git0001.it.abb.com:FeasibilityStudy/MultiplatformUI
```

> To clone the repository, you need your authorised credentials.
> Please, ask the administrator.

We are going to partition the project in three repositories:

- ui-components,
- ui-composites, and
- connectivity.

currently we have created a new folder **front-end-2** that contains the three sub-directories.
The files contained in these folders should follow our naming conventions and folder structures.
Just to show an example, the component **cux-notification-message**, that is a core UI component, is inside the sub-folder:

**../ui-components/core/cux/notifications/message**

and it's AngularJS module is

**ui.components.core.cux.notifications.message**

Every components should deliver at least the following files:

- component.directive.js: directive
- component.html: html template
- component.less: the style
- component.spec.js: unit test
- readme.md: general documentation
- javascript.md: an example about how to use the component (js)
- html.md: an example about how to use the component (html)

Before to code the component, we should define:

- if there exists a developed Common UX component [here](https://commonux.abb.com/),
- the name of the component, it's module and it's attributes,
- how to use it as pure HTML tag or class.

We believe in the principles of software developement (at least):

- [SOLID](https://en.wikipedia.org/wiki/SOLID)
- [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
- [KISS](https://en.wikipedia.org/wiki/KISS_principle)

and a strong understanding of [GOF Design Patterns](https://en.wikipedia.org/wiki/Design_Patterns) is recommended.

The review of the component will be done following these principles and software engineering good practises.

## <a name="catalogue"></a> MUI catalogue

> **TODO** Deploy MUI catalogue

## <a name="specification"></a> Specification and guidelines

We provide you with a set of documents and tools to complete your work and to successfully contribute to MUI:

- User stories (if applicable),
- Mock-ups and prototypes (if applicable),
- [The MUI catalog of patterns, CSS classes and components](http://...),
- [Common UX principles](https://softwareui.abb.com/) **obsolete**
- [Common UX principles](https://commonux.abb.com/) **new**

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

> Before to commit 

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
* **chore**: a small task (i.e. moving a file)

### Scope
The scope should be the name of the affected module (lowerCamelCase)

The following are examples:

* **ui.components.core.cux.controls.button**
* **ui.components.core.cux.controls.input**
* **ui.components.opt.cux.charts.lineChart**

### Subject
The subject contains a succint description of the change:

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

## <a name="arch"></a> Architecture

```
  /dist (here goes the build)
    img/
      ..
    fonts/
      ..
    mui.core.css (stylesheet) <= CSS can be used without a framework
    mui.js (utilities) <= Vanilla js
  /front-end-2
    /ui-layout
      /core/cux
        /fonts
        /style
          ...
          _breackpoints.less
          _font-faces.less
          ...
          _utilities.less
          _variables.less
          layout.less (import core ui-components)
        /..
    /ui-components
      /core/cux (i.e. buttons, inputs, tabs, navigator)
        /component-nane
        /components-group
          /component-name
        /notifications
          /message
            message.directive.js
            message.html
            message.less
            message.spec.js
            readme.md
            /doc
              html.md
              javascript.md
       /opt/cux
         ... (i.e. gauges, charts ...)
    /ui-composites
      /cux
    /connectivity
  
  /app
    /www
      /bower_components
      /ui-components
      /ui-composites
      /connectivity
      /dashboard
        dashboard.controller.js (module: app.dashboard)
        dashboard.html
        ..
      /login
        login.controller.js (module: app.login)
        login.html
      /status-summary
      /style
        app.less (only application classes)
        mui.opt.less (imported from mui optional ui-components ad other ui-composites)
      /services
      /sessions
      /...
    /...
    ...
```

[Back to top](#summary)

## <a name="links"></a>Links

ABB
- [ABB MUI online catalogue]() ... to be done
- [ABB Redmine](http://monitoring-helpdesk.it.abb.com)
- [ABB VersionOne](https://versionone.abb.com)
- [ABB Common UX style guide](https://stsint.abb.com)

Other
- [Git book](https://git-scm.com/book/en/v2)
- [Contributing to angular](https://github.com/angular/angular/blob/master/CONTRIBUTING.md)
- [Angular style guide](https://github.com/johnpapa/angular-styleguide)
- [CSS BEM naming convention](https://medium.freecodecamp.org/css-naming-conventions-that-will-save-you-hours-of-debugging-35cea737d849)
