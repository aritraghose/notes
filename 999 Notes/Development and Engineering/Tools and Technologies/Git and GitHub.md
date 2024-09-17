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