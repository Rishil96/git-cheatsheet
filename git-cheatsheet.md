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

