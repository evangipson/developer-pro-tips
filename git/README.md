## Git/github tips
- You can switch to the previous branch you were on by using the shortcut "git checkout -"
- You can reword your previous commit message by using the command "git commit -v --amend"
- Use "git stash" to save changes that aren't currently committed without committing.
  - "git stash list" will show you all current stashes saved.
  - "git stash apply <n>" will retreive the nth stash.
  - "git stash pop" apply the last stash, and remove it from the stash list.
  - "git stash clear" will remove all stashes.
- If a file is persisting to be modified even after a checkout, try to remove your git cache by running the command "git rm --cached -r ." in the root directory.
  - After the git rm you will have to reset your branch to the HEAD by running "git reset --hard"
