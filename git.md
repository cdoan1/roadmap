# Useful GIT commands

1. Sometimes, you have pushed to GHE, and it takes time to go through the checks, and before you can create a PR, someone else had created a PR and their code was merged into MASTER. You branch is now out of sync, and behind MASTER. And, your PR cannot be merged without rebasing to master. The following instructions allows you to quickly rebase your branch.

   ```
   git checkout your-branch-name
   git fetch
   git rebase origin/master
   git push origin +HEAD
   ```

2. We also like commits to be squashed, before your code goes to code review. You can use the following sequence to squash and rebase your commit.

   ```
   # example merging 4 commits

   git checkout your-branch-name
   git rebase -i your-branch-name~4 your-branch-name

   # at the interactive screen
   # choose fixup for commit: 2 / 3 / 4
   
   git push -u origin +your-branch-name
   ```

3. To avoid having to squash right before you make a PR, you can commit your changes with `commit --amend`

   ```
   git checkout -b your-branch-name
   git add .
   git commit -m "commit message"
   git push origin HEAD
   
   # multi task on another task

   git checkout your-branch-name
   git fetch
   git add .
   git commit --amend
   git push origin +HEAD
   ```
