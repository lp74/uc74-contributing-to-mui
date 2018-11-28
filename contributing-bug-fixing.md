[contributing](contributing.md)

---

# Bug Fixing

You should know ```git```

- [Here you can find the git book](https://git-scm.com/book/en/v2)

Bug fixing procedure is similar to the [New features](contributing-new-features.md) procedure, but

## 3. create a new branch named **fix-n-short-description** where:
    - n is the redmine issue-id,
    - short-description is the redmine issue-title (whenever applicable).

## 5. commit your work 

following the [Commit message guidlelines](commit-message.md)

> Before to commit 

> Please, checkout our [definition of done](definition-of-done.md)

```shell
$ git add . # it depends on your fix, pay attention to the files that you add
$ git commit -m "fix(scope): succint description of the fix (issue-id)"
```

---

[contributing](contributing.md)