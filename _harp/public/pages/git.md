<h1 class="page-title">
  Git & GitHub
</h1>

## Introduction

Cuberis uses Git for version control and GitHub for a number of development tasks, i.e. project development documentation, project issues and development specific discussion. The goal is to keep all documentation and discussion in context and provide a central location for all information related to  projects.

## Cheat Sheet of Git Commands

https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf

The following provides a High Level over of the most common operations and Cuberis standard practices. Additionally, you can use once of server GUI applications including GitHub for Mac/Windows or SourceTree

## Introduction to Basic Methods

The most common methods required for Git are:

* `git init`
* `git status`
* `git branch <branch name>`
* `git checkout <branch name>`
* `git add -A`
* `git commit -a`
* `git push / git push -u origin <branch name>`

### git init

Initializes a Git repository so that you can begin tracking files.

Example Response:

```shell
Initialized empty Git repository in /Users/name/Cuberis/example-project/.git/
```

### git status

Provides current status, providing details of current branch, Files untracked, changed and deleted.

```shell
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	index.html

nothing added to commit but untracked files present (use "git add" to track)
```

### git branch &lt;branch name&gt;

This command is used to create a new branch off of your current branch

### git checkout &lt;branch name&gt;

Swaps your current branch

### git add -A / git add path/to/file

Add files to be tracked in a Git project. Tracked files will be pushed to GitHub and have a history from the time that they are added forward.

### git commit -a

A commit represents a point in the files history that can be referenced. Commits should be main frequently in order to provide adequate references to changes and progress. Commits should take place whenever new functionality is working, or if a developer is breaking from the work for any reason. Commits that take place mid work should be marked as such.

### git push / git push -u origin &lt;branch name&gt;

A push stores your local code on GitHub where it can be accessed by the rest of the team. To push your current branch, if it is already available on GitHub, is simpley <code>git push</code>. In order to add your local branch to GitHub a <code>git push -u origin &lt;branch name&gt;</code> is required

Example Response:

```shell
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 255 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/cuberis/example.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
```


## .gitignore Files

Using an appropriate .gitignore file is critical.

Cuberis' default .gitignore files are include in project baselines but may also be found on the  [Cuberis Gists Page](https://gist.github.com/cuberis).

## Branches

Cuberis has a specific branching structure for developing, staging and shipping code.

The primary primary branch for Development is the 'dev' branch. This branch should only ever have working code and should be the primary branch that work is merged into.

The 'dev' branch as sub branches labeled to indicate purpose.
- **bug/branch-name** : These branches are specifically for dealing with a collection of smaller bug, they may be ended with the day the work is being done or the type of work, ie. jan26, css-updates, js-errors.
- **issue/issue-number** : Branches prepended with issue/ are for specific larger scale issues reported in Github.
- **feature/feature-name** : These branches are used in primary production as well as for ongoing development of new features. There may be more than one of these branches to a feature as one may include backend or functional code while the other contains frontend.
- **styles/general** : This branch and associated branches are for the creation and implementation of general purpose CSS/JS that are not directly associate with specific components.

## Committing

When working with Git it is important to commit regularly and to include concise and descriptive commit messages. The goal of commit messages is to provide information about what the commit involved.

https://robots.thoughtbot.com/5-useful-tips-for-a-better-commit-message

1. First line should include less than 50 characters and act as a title.
2. Never use the <code>-m</code> flag (It encourages abbreviated messages)
3. Messages Should be in present tense (Fix bug vs Fixed Bug)
4. Answer the Following:
  * Why is the change necessary?
  * How does it address the issue?
  * What side effects does this change have?
  * If related to an issue provide a link to that issue

Example:

```shell
clear errors on modal close

- clear JS errors when user closes login or registration modals.
- change in behavior requested by client.
- listen to .close class and empty() .js-errors and removeClass('error') from .required

original issue: https://github.com/cuberis/greenspon/issues/209

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch bug/clear-errors
# Your branch is ahead of 'origin/bug/clear-errors' by 1 commit.
#   (use "git push" to publish your local commits)
#
# Changes to be committed:
#       modified:   example/file/path.less
#
```
