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
- [Rebase Commits to a Branch](#rebase-commits-to-a-branch)
- [Interactive Rebase](#interactive-rebase)
- [Soft Undo Commits](#soft-undo-commits)
- [Prune Branches](#prune-branches)
- [Stashing Changes](#stashing-changes)
- [Branching Strategy](#branching-strategy)

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

### Rebase Commits to a Branch

As you work in a feature branch you'll want to periodically pull in changes from `main`. To preserve a clean history use `rebase` to pull in the latest changes and replay your local commits on top of them (placing them at the top of your history). Typically, you'll want to do this often, before you push your local branch to your remote server. Once you've pushed to your remote you'll want to merge changes in case others are working from your feature branch as well. Rebasing changes the commit history so it can cause issues when others use the remote branch. Coordinating with your team is important in those situations and you can force push a branch to rewrite the history of the remote when needed.

```shell
git checkout main
git fetch origin
git checkout feature/branch
git rebase main
# Then work through resolving conflicts and committing changes
```

- [Learn Git Rebase in 6 minutes ](https://www.youtube.com/watch?v=f1wnYdLEpgI)
- [Merging vs. rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)

### Interactive Rebase

You can perform an interactive rebase when pulling in changes from `main`. This allows you review and alter commits. This can let you clean up the commit history by allowing you to edit, squash, reorder, or delete commits before they get merged in. Ultimately this can clean up the commit log and history. Since the history will change it's best to only rebase on local branches before pushing to the remote (and then to start using `merge` to keep the history in place for others).

```shell
git checkout main
git pull
git checkout feature/branch
git rebase -i main
```

As you review and make changes you can commit them using `git commit --amend`. You can always exit a rebase with `git rebase --abort` if needed and start over or go another route.

- [Beginner’s Guide to Interactive Rebasing](https://hackernoon.com/beginners-guide-to-interactive-rebasing-346a3f9c3a6d)
- [Git Rebase --interactive: EXPLAINED](https://www.youtube.com/watch?v=H7RFt0Pxxp8)
- [How to keep your Git history clean with interactive rebase](https://about.gitlab.com/blog/keep-git-history-clean-with-interactive-rebase/)

### Soft Undo Commits

When you have accidentally committed changes to a branch you can undo them and restage the changes using `git reset HEAD^ --soft`. You can run this multiple times to continue undoing changes as needed. `git reset HEAD~` will also work.

### Prune Branches

To remove local remote-tracking branches that are no longer on the remote server run `git fetch --prune` (this won't delete the local branch itself). Separately, the `git prune` command will delete locally detached commits.

### Stashing Changes

You can stash uncommitted changes and later reapply them in case you need to work on something else before committing. You can stage newly created files and they will be stashed with your changes. Otherwise modified files will be stashed and newly created files won't be. Stash files using the `git stash` command. You can include a message if needed like so, `git stash push -m "work in progress on feature A"`.

To retrieve the stash you can use `git stash apply` or `git stash pop`. Apply will retain your stash in the stash list for later use whereas pop will remove the stash. You can target specific stashes with both commands using the `stash@{X}` option (where X is replaced with the stash index). Stashes are stored with the most recent on top (last-in, first-out).

### Branching Strategy

I prefer trunk-based development, using short-lived feature branches (not committing directly to `main`, which is more like the GitHub flow process).

I typically use `main` and `develop` branches. Work is done against `develop` and then merged to `main` periodically for production releases. Hot fixes can be done against `main` as necessary and merged back to `develop` (or even done in `develop` and cherry picked to `main` depending on the issue). Feature branches should be squash merged into `develop` and `develop` should be merged into `main` to keep the development and production histories intact.

If the `main` and `develop` histories conflict preventing a merge, we need to create a branch from `main`, merge `develop` into that branch and resolve any conflicts and merge it into `main`. Then merge `main` back to `develop` to resync them.

- [Trunk-based development](https://www.atlassian.com/continuous-delivery/continuous-integration/trunk-based-development)
- [Gitflow - A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)
- [The origins of Trunk-Based Development](https://paulhammant.com/2015/04/23/the-origins-of-trunk-based-development)
- [Is GitHub Flow the same as Trunk-based development?](https://www.reddit.com/r/git/comments/1oft3lq/is_github_flow_the_same_as_trunkbased_development/)
