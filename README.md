# slskd fork

This is my personal fork of slskd to goof around with changes and new features. No plans to move anything upstream.

## Syncing with upstream

The `origin` remote points to this fork. The `upstream` remote is fetch-only and points to the original repository.

```powershell
git fetch upstream
git switch master
git merge upstream/master
```

If the merge has conflicts, resolve them in an editor, then complete and push the merge:

```powershell
git add .
git merge --continue
git push origin master
```

To abandon an unresolved merge instead:

```powershell
git merge --abort
```
