# How to share local codes with remote codes on github

## 1. About adding existing projects to GitHub

*A project has already been created in local*  [*See docs here*](https://docs.github.com/en/github/importing-your-projects-to-github/importing-source-code-to-github/adding-an-existing-project-to-github-using-the-command-line) 

1. Create a new repo on github.
   To avoid errors, do not initialize the new repository with `README`, license, or `.gitignore files. 
You can add these files after your project has been pushed to GitHub.


2. Open Terminal and change your working directory to your local folder


3. Initialize the local directory as a Git repository.

    ```
   git init -b main
   ```


4. Add the files in your new local repository. 
This stages them for the first commit.

    ```
   git add .
   ```
   
   Commits the tracked changes and prepares them to be pushed to a remote repository.
   To remove this commit and modify the file, use `git reset --soft HEAD~1` and commit and add the file again.


5. In Terminal, add the URL for the remote repository where your local repository will be pushed.
   
   ```
   $ git remote add origin  <REMOTE_URL> 
   # Sets the new remote
   $ git remote -v
   # Verifies the new remote URL
   ```

6. Push the changes in your local repository to GitHub.com.

   ```
   git push origin main
   ```
   
   `origin` is usually used for your own remote by convention.


## 2. Forking workflow

*For working in the open source community or collaborating on your own projects*

*Resources*
- https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow 
- https://gist.github.com/Chaser324/ce0505fbed06b947d962


1. Fork 'official' repo to your own remote github


2. Clone the forked repo from remote to your local system by `git clone <url>`

   Origin is used for your personal remote forked repo by default while running git clone. 

3. Add a remote for the 'official' repo
   
   ```
   git remote add upstream <url>
   ```

   Upstream is used for the official repository by convention.


4. Working in a branch: making & pushing changes
   
   * Create a new branch for workflow `git checkout -b new-branch`
   
   * Checkout to an existing branch `git checkout some-branch`
   
   * keep your fork up to date to the latest 'official' repo `git pull (upstream main)`
   

5. Making a pull request

   * push changes to my own remote repo that is accessible to others `git push origin my-branch`

   * Cleaning work is probably needed before pull request.

     - Rebase your development branch to avoid conflict when new commits have been made to the upstream main branch. 
     
        ```
        git checkout my-branch
        git rebase my-main
        ```

     - Squash several small commits to a more compact one by `git rebase -i my-main`

     More about `git rebase` can be found [here](https://git-scm.com/docs/git-rebase).

   * Create a "pull request" on github to let project maintainers know and then merge to `upstream main`.
   


## 3. Start from the beginning

Notes from [Advanced Git Tutorial | Google IT Automation with Python](https://www.youtube.com/watch?v=TwVuFwyztEE)

Git is a visual control system (VCS), which can save code, configrations, histories, etc.

1. After installing git, the first thing to do is to tell Git who you are by execute command line `git config --global "me@email.com"`


2. Add new project and repo

   ```
   $ mkdir project
   $ cd project
   
   # Create a new repo in local
   $ git init 
   ```


3. Stage changes and commit

   ```
   $ git status
   $ git add .
   $ git commit -m "comments"
   
   # A shortcut to stage any changes to tracked files and commit them in one step 
   # only for small changes
   $ git commit -a -m"message"
   ```
 
4. Show changes in commit

   ```
   # to show change logs
   $ git log
   
   # to show changes with details
   $ git diff -u
   # or 
   $ git log -p
   
   # shows only unstaged changes by default
   $ git diff
   # show changes staged but not commited
   $ git diff --stanged
   
   # review changes before staging them
   git add -p
   
 
5. Remove or rename the file in the repo

   ```
   # remove files from repo, stop the file from being tracked by git
   $ git rm FILENAME
   
   # check out the files in the directory/repo
   $ ls -l
   $ ls -al
   
   # rename the file
   $ git rename new_name old_name
   
   # create .gitigore in root repo
   $ touch .gitignore
   # add files into .gitignore
   $ echo .idea > .gitignore
   ```
  

6. Undo changes before committing

     - Change the file back to previous state has not been staged: `git checkout filename`

     - Change the file has been staged but not commit, counterpart to `git add`: `git reset HEAD filename`


7. Amend commit

    - Overwrite previous commit (only works for local repo, not for remote repo): `git commit --amend`


8. Rollbacks
   
   ```
   $ git revert HEAD // HEAD is regarded as a point to a snapshot
   $ git revert commit_id
   
   # identify a commit by commit_id
   $ git log -p -2
   ```

### Branch - a pointer to a particular commit

*default branch - main (or master in old github)*

```
# check up the current branch 
$ git branch

# create a new branch
$ git branch new_branch

# check out the latest snapshot for both files in this branch
$ git checkout new_branch

# create a new branch and switch to it
$ git checkout -b another_branch

# delete the branch
$ git branch -d old_branch

# merge a branch to another
$ git merge another_branch

```

**merge conflict**

`git log --graph --oneline`

`git merge -abort` - stop merging and back to previous status


## 4. How to reset and go back to your previous commit 

1. First to check out the history change logs and find out which version I want to return back by commit_id: `git lg`


2. Then go to the log that I want to go by `git reset commit_id` 

   *Be cautious of using* `git reset -hard commit_id`


3. Lastly, add, commit, and push. If there is a new commit message after `git reset` operation, it will combine the last few commits that you do not want into a single commit.