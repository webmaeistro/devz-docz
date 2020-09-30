# [Source Control](./README.md) / Tools

This page provides a summary of tools I commonly use for source control
at I.

## Git

[Git](https://git-scm.com/) is a free and open source distributed version
control system designed to handle everything from small to very large
projects with speed and efficiency.

## pre-commit

I use [pre-commit](https://pre-commit.com/) at I to easily add git
hooks to my Git repos. This allows me to automate things like checking
for merge conflicts or mistakenly adding secret keys in my code. See
[this example](https://gitlab.com/webmaeistro/circleci-docker-primary/blob/master/.pre-commit-config.yaml)
pre-commit config file from one of my projects.

Since git does not distribute hooks when a repository is cloned, you will
have to install pre-commit in each cloned repo manually using `pre-commit
install --install-hooks` or pre-commit will not run in that repo.  To assist
with automating this step, pre-commit has a [feature] to exploit the
[template directory] setting in git:

```console
git config --global init.templateDir ~/.git-template
pre-commit init-templatedir ~/.git-template
```

From now on, each new repository you create or clone will have pre-commit
installed automatically.

[feature]: https://pre-commit.com/#pre-commit-init-templatedir
[template directory]: https://git-scm.com/docs/git-init#_template_directory

## pre-reqs

I use [pre-reqs](https://gitlab.com/webmaeistro/prereqs) to bootstrap
system pre-requisites that are required to run the code I push to gitlab.
