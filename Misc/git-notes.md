# GIT Notes

## git add & commit
```
// Does not add untracked files, only updated files

git commit -am "[commit message]"
```
<br>

## create support branch
```
git checkout -b [new branch name] [tag]
ex: git checkout -b support/4.1 4.1
```
<br>

## rename branch
```
git branch -m new-name
```
<br>

## download remote branches
```
git fetch
```
<br>

## download a specific remote branch to local

```
git checkout -b newlocalbranchname origin/branch-name
```
<br>

## remove deleted branches from local
```
git remote update origin --prune
```
<br>

## download all tags from remote
```
git fetch --tags
```
<br>

## add tag to commit
```
git tag -a <tag> <commit> -m "<message>"
ex: git tag -a 3.1 15857998c7e9f78c1da7f0fc90439e0c85d8e4d2 -m "3.1"
```
<br>

## delete tag
```
git tag -d <tag>
```
<br>

## push tag to remote
```
git push --tags
```
<br>

## stash
```
// use when you want to revert back to the HEAD but still save your changes

git stash
```
<br>

## stash apply
```
// puts the changes you stashed back in

git stash apply
```
<br>

## stash list
```
// show list of saved stashes

git stash list
```
<br>

## applies changes from saved entry
```
git stash apply [index]
```
<br>


## show which untracked files will be deleted (dry run)
```
git clean -n
```
<br>

## deletes untracked files forced
```
git clean -f
```
<br>

## pull from submodules
```
git submodule update --init --recursive ## use for the first time
git submodule update --recursive --remote ## use after
```
<br>

## remove file from history
- useful if you accidentally commit a senstive file and want it removed
```
git filter-branch --force --index-filter "git rm --cached --ignore-unmatch <file path>" --prune-empty --tag-name-filter cat -- --all
git push origin --force --all
```
<br>

## Add Files To Previous Commit
- you can add more files to a previous commit with `--amend`
```
git add <files>
git commit --amend 
```
<br>
