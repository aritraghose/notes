#git #github #commands #cli 

---

## Git

### git init, add, diff

- Lets first create a repository on GitHub. Also add a readme file there. Make sure the repo is public.
- Install Git and Git Bash
- Open Git Bash and navigate to the folder where we will be working
- `mkdir test-123`  --> lets us create a folder name *test-123*
- now lets create a *index.js* file using the command  --> `touch index.js`
- `git init`  --> Initialize empty Git Repository
- `git status`  --> to check the status of the files in the local repo
- lets write some code in *index.js* file
- `git add index.js`  --> Git starts tracking this file and adds to the stage // `git add file_path`
- now lets update the *index.js* file with some more code
- `git diff`   --> shows the changes made to the files Git is tracking
- `git add .`  --> lets Git track all the files and folders and adds to the stage

### git commit and revert

- `git commit -m "added first commit"`  --> commit files or folders
- `git commit -a -m "commit message"`  --> add and commit together
- `git log`  --> to check the commit history
- `q`   --> press *q* to quit 
- `git log --oneline`  --> shorter commit history
- `git blame index.js`  --> show each line is changed by whom, at what time
- `git status` --> shows which files have changed that Git is tracking
> `HEAD` points to the latest commit
- `git log --oneline`
- `git reset --hard <commit_hash>`
> But `Git Reset` deletes all commit history after the `HEAD`. So if we reset back to the 3rd last commit, 2nd and current commit is deleted
> But sometimes we want a new commit to be created instead, which should have the states from the commit we want, without deleting the prior commit history
- `git revert <comnmit hash>`  --> creates a new commit changing the codebase based on a prev commit
- 



## GitHub

> Use **GitHub** documentation to create and set up the SSH Key. 

### Push and Pull from Remote

- `git remote -v`  --> to check if any remote repo is added
- `git remote add origin git@github.com:aritraghose/test-123.git`   --> adds the remote repo (Using SSH)
- `git branch`  --> check the current branch
- `git branch -m main`  --> change the current branch name from *master* to *main*
- `git push --force origin main`  --> force push to the remote, if you are sure enough
- `git push -u origin main`  --> 
- `git push`  --> push to remote
- `git pull`  --> pull from the remote
- `git push -f`  --> force push


### Branching, Merging and Rebasing

- `git branch`  --> check which branch we are currently working in
- `git branch "new-branch"` --> creates a new branch // `git branch <"BRANCH_NAME">`
- `git checkout new-branch` --> switch to a branch
- `git branch -b "new-branch"`  --> create a new branch and switch to it

> - Make some some changes and then commit the changes to the newly created branch. The new created branch will be ahead of the main branch. 
> - Now, when we do `git push`, it will not work since the remote repository does not have the branch we are working in. So,
- `git push --set-upstream origin new-branch`  -->  this creates the new branch in the remote repo and pushes the code to it.

>Now when we want to merge this newly created branch with the `main`:
- `git merge origin/new-branch`
- `git push`

> - Now say, we created the new branch in the remote repo, we will have an option showing up on GitHub that asks us to do "**Compare and pull request**"
> - Click on it and add a title to the request and hit the "Create a pull request"
> - Now the owner/collaborators of the repo can review and merge the pull request
> - Note that, once merged, it will merge with the remote repo. We must `git pull` it to our local.

> When merging a branch with the main, the entire commit history of that new branch is packed into a new commit added to the main. So that branch history is lost. *Rebase* solves this.
> What rebase does is that, all the commit history is added linearly with the current head of the main and the new head now points to the last commit.
> But using rebase can make the commit history huge, so we tend to avoid it.

- `git rebase branch-3`  --> rebase `branch-3`


### Stashing

> - There are times when the remote codebase is updated with some code from other developers, and local repo is also updated by us. But we are not going to stage or commit our local code.
> - In that case, without doing commit, we will not be able to pull the remote changes.
> - Stashing temporarily stores the local unsaved codes so that we can pull right away.

- `git stash` --> stores temporarily the unsaved local changes
- `git pull`  --> pull the remote changes
- `git stash apply` --> now paste back the unsaved local changes
