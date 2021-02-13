---
date: 2021-02-05
---

# Git Changed Files

You'd think this would be easy, but wtf git.

- <https://github.community/t/check-pushed-file-changes-with-git-diff-tree-in-github-actions/17220/10>
- <https://stackoverflow.com/questions/1527234/finding-a-branch-point-with-git/1527308#1527308>
- <https://forum.gitlab.com/t/ci-cd-pipeline-get-list-of-changed-files/26847/11>

```sh
files_since() {
  changed_since="$(git log -1 --before="@{$2}")"
  files="${changed_since:+"$(git diff-tree --no-commit-id --name-only -r "$1" | xargs)"}"
  echo "$files"
}
```

```sh
diff --old-line-format='' --new-line-format='' <(git rev-list --first-parent topic) <(git rev-list --first-parent master)|head -1
# or
git log -n1 --format=format:%H $(git log --reverse --format=format:%H master..topic | head -1)~
```
