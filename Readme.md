### Git Commands

- **`git log`**: To check the log of updates made in the repository.
- **`git status`**: To check the status of files that are yet to be committed.
- **`git commit -m 'message'`**: To commit the changes of files to the branch with a message describing the update.
- **`git add ./`**: To add all the files. Alternatively, you can specify the file name instead of `./` to add specific files to the staging area.
- **`git init`**: To initialize an empty repository.

---

### Checkout Commands

- **`git checkout <commit-hash>`**: You first need to copy the commit hash from `git log`, then use this command to revert back to the state of the specific commit.
- **`git checkout main`**: Switches back to the main branch. For example, if you made changes to a `readme.md` file and a `test.js` file, but something went wrong and you want to revert to the previous commit, you use `git log`, get the commit hash, and use `git checkout <commit-hash>`. If you later want to switch back to the main branch (which contains both files), you use `git checkout main`.
- **`git checkout -f main`**: Forces a switch to the previous state, discarding any local changes.

---

### Branching

- **`git branch -M main`**: Renames the current branch to `main`.
- To create a remote repository, go to GitHub, create a repository, copy the link, and use the following command:
  - **`git remote add origin <link>`**: Adds the remote repository. You can create multiple remote repositories by changing the link.
- **`git push -u origin main`**: Pushes your local repository to the GitHub main repository.
- **`git branch <branch-name>`**: Creates a new branch.
- **`git checkout <branch-name>`**: Switches to the specified branch.
- **`git checkout -b <branch-name>`**: A shortcut to create and switch to a new branch in one step.

---

### Branching and Merging

- **`git push --set-upstream origin feature-branch`**: Pushes the changes in the feature branch to the remote repository.
- **`git push -u origin <branch-name>`**: Similar to the above command, it sets up the upstream branch and pushes changes.
- **`git pull`**: Merges changes from the remote repository to your local repository.
- To sync the main branch with the feature branch on GitHub, go to GitHub and create a pull request. After the merge is complete, you can choose to delete the feature branch.

To sync your local repository with the updated main branch:

- **`git checkout main`**, then
- **`git pull`** (or **`git pull -u origin main`**).

This will sync your local main branch with the remote repository.

To delete a branch locally:

- **`git branch -d <branch-name>`**.

---

### Resolving Merge Conflicts

Merge conflicts occur when two branches modify the same file and one branch is already merged into the main branch. When trying to merge the second branch, you'll encounter a merge conflict.

To resolve:

1. **`git pull`** the changes of the branch that merged first.
2. Go to your code editor, which will highlight the conflicts.
3. You can either discard or keep changes.
4. After resolving, click the option to complete the merge.
5. In the terminal, run:
   - **`git add ./`**
   - **`git commit -m "Resolved merge conflict"`**
   - **`git push`**.

Go to your GitHub repository to verify that the merge conflict is resolved, and complete the pull request.

---

### Resetting Commits

Suppose you've made 6 commits, but the last 2 were wrong. If you want to delete the last 2 commits, take the ID of the 4th commit and run:

- **`git reset <id>`**: This will completely delete the unwanted commits.

Additional reset commands:

- **`git reset --soft <id>`**: Resets the commits, but keeps the changes staged.
- **`git reset --hard <id>`**: Resets the commits and discards all changes.
- **`git revert --continue`**: Continues reverting after conflict resolution.

---

### Stashing Changes

If you're working on some code but a bug needs immediate attention, you can use `git stash` to save your current work without committing it. After fixing the issue, retrieve your stashed work:

1. **`git stash list`**: Lists all stashed changes.
2. **`git stash apply <id>`**: Applies the stashed changes back to your working directory.
