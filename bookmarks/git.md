# git

## Shallow

1st lesson learned: don't clone forks. Do git init, then config remote refspec and alias shallow fetch, _then_ fetch from remote.

- [How to Update a Shallow Clone - Torek](https://stackoverflow.com/questions/41075972/how-to-update-a-git-shallow-clone)
- In summary:
  - Make a fork, delete stale branches in github, clone it with `--depth=100`
  - Add a remote upstream and edit .git/config refspec to only fetch important branches
  - `git config git config remote.upstream.tagopt --no-tags`
  - Run git fetch --all --depth=100

- [prune-packed](https://git-scm.com/docs/git-prune-packed)
- [refspec](https://git-scm.com/book/en/v2/Git-Internals-The-Refspec)
- [various prunes](https://stackoverflow.com/questions/20106712/what-are-the-differences-between-git-remote-prune-git-prune-git-fetch-prune)
  - [prune after change refspec](https://stackoverflow.com/questions/35937839/prune-remote-branches-after-fetch-refspec-changes)
  - [aggressive pruning](https://stackoverflow.com/questions/1904860/how-to-remove-unreferenced-blobs-from-my-git-repo)

```sh
# to convert to shallow after cloning deep:
git reflog expire --expire=all --all
git tag -d $(git tag -l)
git fetch --all --prune --depth=1
git gc --prune=all
```