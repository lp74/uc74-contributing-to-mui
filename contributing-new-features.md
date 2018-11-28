[contributing](contributing.md)

---

# Contributing to new features

You should know ```git```

- [Here you can find the git book](https://git-scm.com/book/en/v2)

## 1. Checkout master branch

> We use the master branch as the development branch

```shell
$ git checkout master
```

## 2. Incorporate changes from the origin/master branch

```shell
$ git pull origin/master
```
## 3. Create a new branch 

named **feature-n-short-description** where:
- n is the redmine issue-id,
- short-description is the redmine issue-title (whenever applicable).

```shell
$ git checkout -b feature-n-short-description
```

## 4. Develop the new feature

- using:
	- MUI CSS classes,
	- MUI HTML tags,
	- MUI (AngularJS) components,
- using our [coding rules](coding-rules.md),
- developing and running unit-test and e2e tests (whenever applicable),
- complying with the Common UX principles and the provided mock-up (if available),

## 5. Commit your work 

following the [Commit message guidlelines](commit-message.md)

> Please, checkout our [definition of done](definition-of-done.md)

```shell
$ git add . # it depends on your feature, pay attention to the files that you add
$ git commit -m "feature(scope): succint description of the feature (issue-id)"
```

> Please, to keep history clean, squash your commits.

```shell
$ git rebase -i HEAD~n
```

## 6.a Rebase your work on to master (preferred)

If your are the unique developer of your local feature branch, you cand rebase your work on to master.

```shell
$ git fetch --all
$ git rebase origin/master
```
> rebasing your work on to origin/master is very important:
> - to keep your work aligned with the master branch, 
> - to keep the git log clean and more easy, and
> - to avoid conflicts and failures.  

After rebasing your work, fix conflicts (if needed) and keep tests successful.

## 6.b Merge your work on to master

```shell
$ git fetch --all
$ git merge origin/master
```
After merging your work, fix conflicts (if needed) and keep tests successful.

## 7. Push your work upstream

```shell
$ git push origin feature-n-short-description
```

## 8. Make a pull request

Checkout [Pull request (PR)](pull-request.md)

---

[contributing](contributing.md)