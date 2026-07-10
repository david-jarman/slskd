# slskd fork

This is my personal fork of slskd to goof around with changes and new features. No plans to move anything upstream.

## Building a Docker image

```powershell
$tag = git describe --tags --abbrev=0
$revision = git rev-parse --short HEAD
$version = "$tag.65534+$revision"
$buildDate = (Get-Date).ToUniversalTime().ToString('yyyy-MM-ddTHH:mm:ssZ')

docker build `
  --build-arg "TAG=$tag" `
  --build-arg "VERSION=$version" `
  --build-arg "REVISION=$revision" `
  --build-arg "BUILD_DATE=$buildDate" `
  --tag "slskd:local" `
  .
```

Confirm that the image exists and reports the expected application version:

```powershell
docker image inspect slskd:local
docker run --rm slskd:local ./slskd --version
```

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
