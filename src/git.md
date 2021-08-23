# How to share local codes with remote codes on github

## Case 1

[A project has already been created in local folder](https://docs.github.com/en/github/importing-your-projects-to-github/importing-source-code-to-github/adding-an-existing-project-to-github-using-the-command-line) 

1. Create a new repo on github

2. Input command line in terminal:

    `git initial -b main`
    `git remote add origin url`
    `git fetch`
    `git checkout main`
    `git merge master`
    `git git push`

## Case 2 - start from the begining

[Advanced Git Tutorial | Google IT Automation with Python](https://www.youtube.com/watch?v=TwVuFwyztEE)

**Git is a visual control system (VCS), which can save code, configrations, histories, etc.**

1. After installing git, the first thing to do is to tell Git who you are by execute command line `git config --global "me@email.com"`

2. Add new project and repo

    `mkdir project`

    `cd project`

    `git init` /create a new repo

3. Stage changes and commit

    `git status`

    `git add`


    `git commit -m "comments"`

    `git commit -a -m"message"` // A shortcut to stage any changes to tracked files and commit them in one step, only for small changes

4. Show changes in commit

    `git log` - only show logs, change author and dates

    `git log -p` or `git diff -u` - show changes with details

    `git show gitlog_id`

    `git log --stat`

    `git add -p` - review changes before staging them

    `git diff` - shows only unstaged changes by default

    `git diff --staged` - to show the changes that are staged but not commited

5. Remove or rename the file in the repo

    `git rm filename.py` - remove files from repo, stop the file from being tracked by git

    `ls -l` - check out the files in the repo

    `ls -la` - check out all files including hidden files

    `git mv new_file_name old_file_name` - rename the file 

    .gitigore - inside this file, we can specify rules to tell git which files to skip for the current repo. For example, `echo .DS_STORE > .gitignore`

6. Undo changes before committing

    `git checkout filename` - change the file back to previous state has not been staged

    `git reset HAD filename` - change the file has been staged but not commited, counterpart to `git add`

7. Amend commit

    `git commit --amend` -overwrite previous commit. only for local commit, not for public commit

    `touch filename` - create files

8. Rollbacks

    `git revert HEAD` - HEAD is regarded as a point to a snapshot

    `git revert commit_id`

    `git log -p -2`

    Identify a commit by **Commit ID**

### Branch - a point to a particular commit

*default branch - master*

`git branch` - check up the current branch

`git branch new_branch` - create a new branch

`git checkout new_branch`- **check out the latest snapshot for both files and for branches**
   
`git checkout -b another_branch` - create a new branch and swtich to it

When branch was changed, the working directory also changed.

`git branch -d new_branch` - delete the branch

`git merge new_branch` - merge a branch to another

**merge conflict**

`git log --graph --oneline`

`git merge -abort` - stop merging and back to previous status


## Case 2 Return to previous commit 

- `git lg` to check out the history and find out which version I want to return back (commit_ID)

- `git reset commit_ID` Be causious of using `git reset -hard commit_ID`

- Then add, commit, push. If leaving a new commit message after `git reset` operation, it will combine the last few commits that you do not want into a single commint.