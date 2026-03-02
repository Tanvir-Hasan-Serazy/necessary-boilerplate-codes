# Git commands

## To change case sensetive folder

```
git rm -r --cached public/Images
mv public/Images public/images
git add public/images
git commit -m "Rename folder from Images to images"
git push
```

## Rolling back to previous commit (deleting current code)

```
git reset --hard <commit ID>
git push --force
```
