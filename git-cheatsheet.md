# Git CheatSheet


| Sr. No. | Topic Name | Description |
| :--------: | :--------: | :--------: |
| 1 | [Basic Commands](#basic-command) | Simple commands like add, commit, etc. |
| 2 | [Branch Commands](#branch-command) | Commands related to branches. |
| 3 | [Git Diff](#diff) | Checking difference between branches, commits, etc. |
| 4 | [Git Stash](#stash) | Stash changes to avoid making bad commits to save progress. |
| 5 | [Time Travel](#time-travel) | Go back in git commit history. |
| 6 | [Deleting Commits](#delete-stuff) | Resetting the commit history. |
| 7 | [Git Remote](#remote) | Working with basic remote commands. |
| 8 | [Git Remote Branches](#remote-branch) | Working with remote branches. |
| 9 | [Git Rebase](#rebase) | Rebasing branches to clean up commit history. |
| 10 | [Git Tags](#tags) | Add release versions to important commits. |
| 11 | [Git Hash Objects](#hash-obj) | Working with hash objects. |
| 12 | [Git Reference Logs](#reflog) | Check reference logs to keep track of history locally. |
| 13 | [Git Alias](#alias) | Create alias for Git commands. |
| 14 | [SSH Key Setup](#ssh) | SSH Setup for Git and GitHub. |
| 15 | [Git GNUPG Setup (Sign your commits)](#sign-commit-setup) | Setup signed commits for Git and GitHub. |

---

<span id="basic-command"></span>
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

<span id="branch-command"></span>
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

<span id="diff"></span>
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

<span id="stash"></span>
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

---

<span id="time-travel"></span>
## Time Travel in Git Repository

### *Checkout old commits*
- `git checkout <commit-hash>`
- Checkout old commits. This will put the HEAD in a detached state.

---

### *Travel back to current time/HEAD*
- `git switch master`
- To reattach the HEAD from detached state just switch to the branch back.

---

### *Go back in time using HEAD*
- `git checkout HEAD~(number)`
- This will checkout to the number of commits before the current head.
- For HEAD~1, git will checkout 1 commit before current HEAD and so on.

---

### *Travel back in present using switch*
- `git switch -`
- Use this to go back to the last position the HEAD was on before time travel.

---

### *Remove unstaged changes using checkout*
- `git checkout HEAD <file-name>`
- This will remove all the changes made to a particular file that was not staged.

- `git checkout -- <file-name> ...`
- multiple files can be reverted.

- `git checkout .`
- Revert all changes to the last commit.

---

<span id="delete-stuff"></span>
## *Delete or go back to a certain commit permanently*

- `git restore <file-name>`
- This restores the file to its previous commit removing the unstaged changes.

---

- `git restore --source HEAD~<number> <file-name>`
- number : number of commits to go back from HEAD. and which file we want to.
- restore to a previous commit.

---

- `git restore --staged <file-name>`
- This will remove the mentioned file from the staging area.

---

- `git reset <commit-hash>`
- Reset the repo to an old commit
- This will remove the commits from the git history but the changes will still be there. 
- It will put the changes that were reset in an unstaged state so we can still use the changes maybe in another branch or simply remove it. 
- It will give a chance to us to see if there is anything useful in the commits we just reset.

---

- `git reset --hard <commit-hash>`
- This will undo the commits and the changes. Every change made after the commit hash we mentioned in the command will be removed completely with the commits by git.

---

- `git revert <commit-hash>`
- This will undo the commits till the mentioned commit hash. revert will create a new commit in which the changes will be undone. This will preserve the history of the commits we reverted so it can be restored in an unlikely scenario.

---

<span id="remote"></span>
## *Basic Commands for Remote Repository* 

- `ls -al ~/.ssh`
- Check if SSH is configured

---

- `git remote -v`
- Check if we have a remote for our local repo

---

- `git remote add <remote-name> <remote-url>`
- Add remote using url to a local git repo
- Remote name should be origin by convention, and URL is the url of the GitHub remote repo that we create. 
- This command will link the remote to our local repo.

---

- `git remote rename <old-name> <new-name>`
- Rename remote name

---

- `git remote remove <remote-name>`
- Remove remote from local repo

---

<span id="remote-branch"></span>
## *Basic Push, Pull and Fetch remote branches*

### Push

- `git push <remote-name> <branch-name>`
- Push changes to remote
- Remote is usually origin, branch name is the one branch that we wish to push. When we push for the first time, usually the branch won't be present on remote so git push will create the branch at remote and connect the local branch to the remote branch. 
- So the next time we push, it would push it to the remote branch that we created with the first push.	

---

- `git push <remote> <local-branch-name>:<remote-branch-name>`
- Push a local branch to a remote branch with different name

---

- `git push -u origin <branch-name>`
- `git push --set-upstream origin <branch-name>`
- Create a link between local and remote branch using -u
- This sets an upstream to a branch we are pushing. Think of this as linking our local branch to a branch on GitHub. 
- Once branched are linked, Git will remember this link and it will allow us to use just "git push" from next time instead of specifying branch name everytime. 

---

- `git push -u origin <local-branch>:<remote-branch>`
- Set upstream to a branch remotely with different name
- This again links the local branch to the remote branch but with different name.

---

### Check link of branch to remote branch

- `git branch -r`
- Check remote branch tracking reference

---

### Checkout from remote branch

- To add a branch that is available on remote repo but not locally simply use:-
- `git switch <remote-branch-name>`
- New way
- `git checkout --track <remote-name>/<remote-branch-name>`
- Old way 

---

### Fetch

- Fetch changes others have made on remote without merging it to our local repo
- `git fetch <remote-name>`
- `git fetch <remote-name> <branch-name>`
- If we want to fetch just a single branch
- After fetch we can checkout the remote branch like git checkout origin/master but our local master will remain untouched.

---

### Pull

- `git pull <remote> <branch-name>`
- Pull changes from remote
- Pulls/downloads the changes from remote and gets merged into our local.
- `git pull`
- Shorter command that works if origin is our remote name which is default and our current branch tracking is configured to a remote branch.
- E.G. if we are on master branch, then using "git pull" will be like "git pull origin master", it will use the remote branch that is linked to our current branch where our HEAD is.

---

<span id="rebase"></span>
## *Git Rebase*

- `git switch <feature-name>`
- `git rebase <master-branch>`
- Always switch to the feature branch that we want to rebase and then use rebase using the main/master branch so the current HEAD of master becomes the base of the feature.

---

- Merge conflict can occur while rebasing and we can either abort or fix the conflicts and continue to rebase.

---

- Abort rebase
- `git rebase --abort`
- Goes back to the original branch before rebase

---

- Continue rebase
- `git add .`
- Add the fixed conflicts before continuing the rebase
- `git rebase --continue`
- After fixing the conflicts and staging it, use continue to finish the rebase.

---

- `git rebase -i HEAD~<number of commits to go back>`
- Interactive Rebase											
- After this command, in the editor use the commands provided to make changes to the commit and project history according to our liking.
- Check notes for the various options to choose from.

---

<span id="tags"></span>
## *Git Tags*

- `git tag`
- View tags
- List all the tags in the current repository
- `git tag -l`
- Implicit way to do the same as above

- `git tag -l "some wildcard pattern"`
- Use some pattern to find the type of tags you are searching for E.g "v2*". 
- Here pattern means start with v2 and * means 0 or more of any characters following after v2.

---

- `git checkout <tag>`
- Checkout a tag
- Tag refers to a particular commit in the past so it is the same as using a commit hash to checkout a past commit. Puts us in detached HEAD state.

---

- `git tag <tag-name>`
- Create a lightweight tag

- `git tag -a <tag-name>`
- Create an annotated tag
- Opens an editor for us to provide additional details about the release.

---

- `git show <tag-name>`
- View details of the annotated tag

---

- `git tag <tag-name> <commit-hash>`
- For lightweight, tagging previous commits

- `git tag -a <tag-name> <commit-hash>`
- For annotated, tagging previous commits

- `git tag -f <existing-tag-name> <new-commit-hash>`
- Forcefully point an already existing tag to a different commit

---

- `git tag -d <tag-name>`
- Delete a tag

---

- `git push origin <tag-name>`
- Pushing tags to remote
- Push a single tag.

- `git push --tags`
- Push all tags in local. Specify a remote if multiple remotes are configured.

---

<span id="hash-obj"></span>
## *Working with Hash Objects*

- `git hash-object <file-name>`
- Get hash of files/texts
- Get hash of file (SHA-1)

- `echo "text" | git hash-object --stdin`
- Get hash of text. --stdin tells git to hash the input provided instead of hashing a file.

- use -w flag with the above 2 commands to make GIT to store the hash and its value.

---

- `git cat-file -p <hash-value>`
- -p tells git to pretty print the output.
- Retrieve the data stored in git objects folder, view the hash-value object contents.

---

- `git cat-file -p <hash-value> > <file.txt>`
- To add contents of a value stored in a hash to a file use

---

- `git cat-file -p master^{tree}`
- To view a tree
- gives the tree for the most recent commit.

- `git cat-file -t <hash-value>`
- -t stands for type of the hash value object.
- To view a type of git object based on hash value

---

<span id="reflog"></span>
## *Git Reference log*

- `git reflog show HEAD`
- will show the logs of HEAD similar to git log command for commits.	
- Every log will have a relative name that can be used in another command the name would be like HEAD@{0}, it keeps changing after every log where the latest change becomes 0 and all past changes get incremented by 1.
- Similar to prepending an item in a linked list or array.

---

- `git checkout HEAD@{2}`
- This will checkout to the point when the reference was logged.
- This may keep us on the same commit if we didn't commit anything but just did something like switching branches and stuff

---

- `git reflog master@{one.week.ago}`
- Timed References in Reflog
- View repo from 1 week ago.

- `git checkout bugfix@{2.days.ago}`
- Checkout the repo from 2 days ago

- `git diff main@{0} main@{yesterday}`
- Check difference between the latest log and yesterday

---

<span id="alias"></span>
## *Configure alias using cmd*

- `git config --global alias.alias-name git-command`
- alias name is the shortcut and git-command is the command we want to make a shortcut for.

---

<span id="ssh"></span>
## *SSH Key Setup*

1. Generate key using `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`. It will create a .ssh folder in your working directory and will ask to setup a passphrase while using SSH. Set it up.

2. After the first step, our private and public keys will be created in .ssh folder (default names id_rsa and id_rsa.pub). 

3. Now start the ssh agent using `start-ssh-agent` and adding passphrase for verification.

4. Ensure that the OpenSSH Authentication Agent is running for this to work (check services.msc for this).

5. Add your SSH Key to the SSH agent using `ssh-add "ssh-private-key-path"`

6. Finally add the public key i.e. **id_rsa.pub** in our GitHub SSH and GPG keys.

7. After these steps, SSH configuration is done. 


<span id="sign-commit-setup"></span>
## *Git Sign Commits using GNUPG*

1. Install GIT and GnuPG (we also get gpg.exe installed with GIT so GnuPG installation is not mandatory)

---

2. Generate a new private-public key pair using the following command `gpg --full-generate-key`

---

3. Use the default settings it should be fine, just add your name and email address correctly.

---

4. Export your public key using the following command `gpg --armor --export your_email@example.com > publickey.asc`. It will save our public key in this file. Private key is handled by GPG don't need to do anything to save it.

---

5. Add this public key contents to your GitHub by going to settings, SSH and GPG keys and create a new GPG key and paste the public key there and save it.

---

6. All that is left is to tell GIT to use GPG key to sign your commits which is done by modifying .gitconfig file that should be placed in your user folder.

---

7. First grab hold of the key ID of the GPG we generated using the command `gpg --list-keys`. Your ID will be something in the combination of numbers and capital letters. Copy it.

---

8. Now we have to change 2 things in .gitconfig file:-
    
    i. mention key id of GPG key in file using the command `git config 
    --global user.signingkey your_key_id`

    ii. Specify path to the gpg.exe file that will help to sign the commits using the command `git config --global gpg.program "C:\\path\\to\\gpg.exe"` 

---


9. After this, git will automatically sign your commits using GPG key.

---
