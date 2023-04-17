# Git CheatSheet

## Basic Commands

### *Configure Git Username and Password*

- `git config --global user.name "Rishil Ramesh"`
- `git config --global user.email "rishil.ramesh@outlook.com"`

---

### *Configure settings locally using --local*
- `git config --local user.name "Rishil Ramesh"`
- `git config --local user.email "rishil.ramesh@outlook.com"`

---

### *Check status of a git repo*
- `git status`

---

### *Initialize a folder to become a git repo (creates a .git folder that stores all history of the folder)*
- `git init`

---

### *Add files to the staging area (one or more files with spaces)*
- `git add file1 file2`

### *Add all files to the staging area*
- `git add .`

---

### *Commit the changes in the staging area*
- *opens the default editor (vim if not configured) to write a commit message*
- `git commit`
- *-m used to write an inline commit message instead of opening an editor (vim)*
- `git commit -m "Commit message"`

### *Commit and Stage files in a single line*
- Adds all unstaged items
- `git commit -a -m "Commit message"`

### *Amend commit (fix mistakes in the previous commit)*
- usually to add forgotten files by staging the file or just to edit the commit message
- `git commit --amend`

---

### *Get the logs of the past commits*
- `git log`
- Show a single line of each commit message
- `git log --oneline`

---

## Branch Commands

### *View all existing branches*
- `git branch`
- *Use -v to get (extra info)the tip of the branch i.e. last commit and its commit message.*

---

### *Create new branch*
- `git branch <branch_name>`

---

### *Switch to a different branch*
- `git switch <branch_name>`
- new way
- `git checkout <branch_name>`
- older way

---

### *Switch and create a branch in one command*
- `git switch -c <branch_name>`
- -c => creates the branch in switch
- `git checkout -b <branch_name>`
- -b => creates the branch in checkout

---

### *Delete branch  (head should not be at the branch we want to delete)*
- `git branch -d <branch_name>`
- `git branch -D <branch_name>`
- -D => force delete

---

### *Rename branch (head needs to be at the branch we want to rename)*
- `git branch -m <new_branch_name>`
- Be present in the branch we want to rename

---

### *Merge branch*
- `git merge <branch_name>`
- Be present in the branch where we want to merge and write the name of the branch to be merged to the current HEAD/branch

---

## Check Difference using diff

### *View Changes*
- `git diff`
- without additional options, lists all the changes in our working directory that are not staged for the next commit.
- basically compares current unstaged changes in the repo with latest commit.

---

### *View changes since last commit*
- `git diff HEAD`
-  without additional options, lists all the changes in our working directory since the last commit (staged or not staged).

---

### *View staged changes since last commit*
- `git diff --staged`
- `git diff --cached`
-  this will show the changes from the HEAD to the point where we added changes to the staging area.
- basically compares the last commit to the current staged state of the repo.

---

### *View changes in a single file*
- `git diff --staged <file_name> <file_name2> ...`
- This will work with all the above diff commands to target just a single file or multiple files to view changes.

---

### *View changes accross branches*
- `git diff branch1 branch2`
- `git diff branch1..branch2 <file_name>`
- Changes will be shown according to the order of the mentioned branched in the command. Can also specify file names at the end to check a specific file.

---

### *View changes between 2 commits*
- `git diff commit1..commit2`
- here commit 1 and 2 are hashes that uniquely identify a single commit.
- `git diff commit1 commit2 <file_name>`
- Can also specify file names at the end to check a specific file.

---

## Stash Changes to preserve history

### *Saving changes without using commit*
- `git stash`
- `git stash save`
- this will undo the changes made staged or unstaged after our last commit but it will remember it for us so we can revert back to them later.

---

### *Pop changes to working directory*
- `git stash pop`
- this will pop back the changes that we stashed to our working directory/repo.

---

### *Apply stashed changes without popping* 

- `git stash apply`
- this will pop back the changes but also keep the changes in the stash so we can pop/apply the changes in multiple branches.

---

### *View Stash Stack*

- `git stash list`
- View stash stack in case of multiple stashes are made.

---

### *Apply a specific stash*
- `git stash apply stash@{id_number}`
- To get a specific stash with its stash id.

---

### *Drop a specific stash*
- `git stash drop stash@{id_number}`
- To drop a stash from the stash stack.

---

### *Clear the whole stash*
- `git stash clear`
- Clear the whole stash stack.

