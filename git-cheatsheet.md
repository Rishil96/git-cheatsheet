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

