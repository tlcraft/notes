# Git

This page lists notes on various `git` commands.

## Contents

- [Change Branches](#change-branches)
- [Set upstream branch](#set-upstream-branch)
- [Checkout a Tag](#checkout-a-tag)
- [Empty Commits](#empty-commits)
- [Get Remote URL](#get-remote-url)
- [Precommit Hooks](#precommit-hooks)
- [Rebase Onto](#rebase-onto)
- [Soft Undo Commits](#soft-undo-commits)

### Change Branches

You can swap back to the last branch you were on by using a dash with `checkout`. In the following example you will end back on `branch-name`.

```shell
git checkout branch-name
git checkout main
git checkout -
```

### Set upstream branch

When pushing up a new branch for the first time you will want to link the branch to an upstream branch. Using the `-u` flag is shorthand for doing this. It configures the local branch to track the remote branch as its upstream. This allows future `git push` and `git pull` commands to work without specifying the remote and branch names. Your local branch will track changes to `origin/feature/branch`.

```shell
git checkout main # whichever your main branch is
git checkout -b feature/branch
# commits are made
git push -u origin feature/branch
```

### Checkout a Tag

You can checkout git tags if you need a specific version of your code (if you're tagging commits).

For example, you can follow this pattern to fetch the tags and checkout a new branch.

```bash
git fetch --all --tags --prune
git checkout -b branch/name tags/<tag_name>
```

### Empty Commits

You can make commits with no changes or message if needed.

```shell
git commit --allow-empty -m "Empty commit"
git commit --allow-empty --allow-empty-message # will be asked to enter a message
git commit --allow-empty --allow-empty-message -m ""
```

- [How to commit no change and new message?](https://stackoverflow.com/questions/12470029/how-to-commit-no-change-and-new-message)

### Get Remote URL

The following command will list your repo's remote origin URL.

```shell
git config --get remote.origin.url
```

### Precommit Hooks

Precommit hooks are useful to ensure standard checks are performed before allowing a commit to be made. For example, you may want to run a linter and unit tests, or perform formatting, or even require a commit message in a specific format. There are a number of tools, like `husky` and `lefthook`, that can help. It can also be good to prevent commits to the `main` branch.

- [Prevent commits in master branch](https://stackoverflow.com/questions/40462111/prevent-commits-in-master-branch)
- [lefthook](https://github.com/evilmartians/lefthook)
- [husky](https://typicode.github.io/husky/get-started.html)
- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0-beta.2/)
- [pre-commit](https://pre-commit.com/)

### Rebase Onto

Rebasing a branch with your `main` branch will preserve a linear history of commits. In some cases we branch from a branch while we're in the middle of changes. If the parent branch is merged back to `main` while we are still working on the child branch we can `rebase --onto` to essentially update the child's parent branch to `main`.

```shell
git checkout main
git checkout -b feature/parent
# commits are made to parent
git checkout -b feature/child
# commits are made to child
# parent is squash merged into main
git checkout main
git pull
git checkout feature/child
git rebase feature/parent --onto main
```

- [Git rebase --onto an overview](https://womanonrails.com/git-rebase-onto)
- [How to git rebase a branch with the onto command?](https://stackoverflow.com/questions/29914052/how-to-git-rebase-a-branch-with-the-onto-command)

### Soft Undo Commits

When you have accidentally committed changes to a branch you can undo them and restage the changes using `git reset HEAD^ --soft`. You can run this multiple times to continue undoing changes as needed. `git reset HEAD~` will also work.
