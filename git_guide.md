###### Shortcuts
```
git init
git add .
git status
git commit -m "Commit message"
git remote add origin https://github.com/zorbax/cc.git
git push -u origin master
```

###### Change the URI (URL) for a remote Git repository

```
git remote set-url origin https://github.com/zorbax/scripts.git
```

###### Set git to use the credential memory cache

```
git config --global credential.helper cache
```
###### Set the cache to timeout after 1 hour (setting is in seconds)

```
git config --global credential.helper 'cache --timeout=3600'
```
###### Update local repository to the newest commit

```
git pull
```
##### Running Jekyll in localhost
```
# bundle update #Update site
bundle exec jekyll serve
```

##### Delete local branch

```
git branch -d gh-pages
```
##### Delete remote branch
```
git push origin :gh-pages
```
##### Push local master *into* gh-pages branch on github
```i
git checkout gh-pages
git merge master
git push -u origin gh-pages
```

###### CC

* Basic

|      |     |
|:--- | --- |
|`git init`| creates a new Git repository.|
|`git status` | inspects the contents of the working directory and staging area.|
|`git add`| adds files from the working directory to the staging area.|
|`git diff` | shows the difference between the working directory and the staging area.|
|`git commit` | permanently stores file changes from the staging area in the repository.|
|`git log` | shows a list of all previous commits.|

* Backtrack

|      |     |
|:--- | --- |
|`git checkout HEAD filename` | Discards changes in the working directory.|
|`git reset HEAD filename` | Unstages file changes in the staging area.|
|`git reset SHA` | Can be used to reset to a previous commit in your commit history.|

* Branching

|      |     |
|:--- | --- |
|`git branch` | Lists all a Git project's branches.|
|`git branch branch_name` | Creates a new branch.|
|`git checkout branch_name` | Used to switch from one branch to another.|
|`git merge branch_name` | Used to join file changes from one branch to another.|
|`git branch -d branch_name` | Deletes the branch specified.|

* Teamwork

|      |     |
|:--- | --- |
|`git clone`| Creates a local copy of a remote.|
|`git remote -v`| Lists a Git project's remotes.|
|`git fetch`| Fetches work from the remote into the local copy.|
|`git merge origin/master`| Merges origin/master into your local branch.|
|`git push origin <branch_name>`| Pushes a local branch to the origin remote.|


### Fetch all changes

```
git fetch --all
```

### Reset the master

```
git reset --hard origin/master
```

### Pull

```
git pull
```

### Global gitignore

```
git config --global core.excludesfile '~/.gitignore'

echo '.ipynb_checkpoints' >> ~/.gitignore
```

### Git commit to the past
```
git commit --amend --no-edit --date="Thu Mar 21 20:00:00 2019 -0600"
```
