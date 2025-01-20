# Git

## Contents

- [Change Branches](#change-branches)
- [Rebase Onto](#rebase-onto)

### Change Branches

You can swap back to the last branch you were on by using a dash with `checkout`. In the following example you will end back on `branch-name`.

```shell
git checkout branch-name
git checkout main
git checkout -
```

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
git rebase --onto main feature/parent
```
