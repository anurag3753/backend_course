# Lecture: <br>
    - https://www.youtube.com/watch?v=NPi2Dr3OdrI&list=PLN4aKSfpk8TTD3g83qIK4PiNsImxWK-6x&index=7

# Popular git commands
- Convert a directory into a git repository
    - git init
- We can not create a repository in command line in git and push it to github ?
    - git and github both are different things
    - we need to manually create repository in github
    - Do not add/create any files(not even README and LICENSE)
- Connect local repository to github repository ?
    - in local repository run the following commands
    - git add .
    - git commit -m "Initial Files"
    - Connect it to remote repo
        - git remote -v :- Came out empty
        - git remote add origin <path_of_remote_git_repo>
        - git push origin master
- Remove commits but keep file changes
    - There are 3 types of resets in git
        - hard reset, soft reset, default reset
    - git reset HEAD~2                    [ Remove commits but keep the changes]    [Also known as default reset]
        - It does not remove the changes. 
        - It justs removes the commit and unstages the changes.
    - git reset --soft HEAD~2            [Remove commits but keep changes]           [Also known as soft reset]
        - It does not remove the changes. 
        - It justs removes the commit but keeps the changes in staging area
    - git reset --hard HEAD~2            [Removes commits and corresponding changes] [Also known as hard reset]
        - It removes the commit and the changes as well
        - Now, if you want to push the changes, then you need to force push it.
        - git push --force origin main    [Remove the hard reset commit from github]

Note: `origin` is nothing but the alias name of the github repository

## Failing git push
- changes present in remote and are not present in local
- For simple cases(the ones which do not end up in merge conflicts)
    - git pull (do it first, so that remote changes comes into your local repository)
    - git push (send local changes to remote)

## Merge Conflicts
- when same file has gone through some changes and its remote and local version are different.
- In those scenarios, also `git pull` fails. We need to manually resolve these conflicts.

## Branches
- We generally create branches to work on separate features.
- Create a new branch
    - git checkout -b feature
- Go back to existing branch
    - git checkout master

## Creating a pull request
- Usually we create pull request from `feature` branch to `main` branch
- Leave your review comments in the `files changed` section
- Can mark which all files you have viewed
- If suppose your pull request has 2 commits, and you make 1 more commit. 
    - Then the pull request will automatically get updated to 3 commits
    - It is applicable as long as the pull request is not merged OR the pull request is not closed.

## Merge Pull Request
- There are various options to merge pull requests
    - Create a merge commit : All commits from this branch will be added to the base branch via a merge commit
        - After merge it is recommended that you delete the branch
        - When we do a normal merge, a new merge commit is created
    - Squash and Merge : 
        - Combine  multiple commits into 1 commit and merge it. 
        - Using this the git history, will have lesser number of commits to be shown to other user.

## git revert Vs git reset
- with `git reset` we can only remove the latest commits (like latest 1, latest 2, latest 3 etc.)
- suppose we want to remove the arbitrary commit in between.
- git revert <commit_id> (to revert an arbitrary commit)
- Inside `git revert` a new commit is created where it resets changes from a particular commit
- Inside `git revert` no force push is needed
    - Reason is : History is not modified. Hence for github it is just a new commit, where we are undoing some older changes. That is the reason `--force` is not needed.
- **Interesting** : If we do `git reset --hard HEAD~1` , then last commit will be deleted and if the revert commit has `deleted` some file. `git reset` will bring it back.
- We can even do `revert` of a `revert`, to bring back the changes.
- It is always safe to do a `revert` instead of a `reset`. And is always the recommended practice.
- One side effect is : revert creates too many commits. (git history becomes dirty)
    - If you are very-very sure, then only go for `git reset` and never reset on a master/main branch. Because others might also have cloned that branch and working on their own feature development.
    - Otherwise always go for `git revert`

## Abort any git command
- git revert --abort

## Merging and Rebasing
- merging creates a new commit, i.e the merge commit(similar to revert)
- one thing we need to take care during the merging process is that of <src> <dest> for the merge process.
- Merge Process:
    - Goto the branch where you want to merge. 
        - `git checkout main`
        - `git merge new-branch` (this will merge new-branch contents to main branch)
        - This creates a new merge commit. Along with this the history of the commits is also preserved once merge is done.
        - The commitID used in individual branch remains the same post merge as well.
- Rebase Process:
    - Same as merge. Below is the command
    - `git rebase new-branch`
    - In rebase, no additional commits gets created. But the history of commits is not preserved.
    - The commitID used in individual branch gets changed post merge.
    - So, order of commits is not preserved and individual commit id is also not preserved.
    - How does it works?
        - the changes in branch `main` are removed first. All the changes of `new-branch` are brought in and on the top of that branch `main` changes are pushed back.
        - hence, the order of commits and the commit hashes do not get preserved.
        - side effect : it modifies the history as well.
    - usability of rebase ?
        - we should not use rebase on main/master branch.
        - you can use rebase on your local branch where you are working on.
        - you should not use rebase on branches where lot of people are working, because it modifies the history
        - we have to force push changes after doing rebase.
    - Rebase is used a lot for personal branches or branches where you are working on
        - you have created your commits in `feature branch`
        - meanwhile `main` branch gets updated.
        - then, first thing that you do is goto `main` branch and do `git pull`
        - then, checkout `feature` branch again, and then you do `git rebase main` . i.e. rebasing the feature branch with `main` branch.
        - this way, my `feature` branch will be in sync with the `main` branch. And then I can merge `feature` branch to `main` branch.

## Merge Conflicts
- Process for resolving merge conflicts
    - Get the list of files which is causing merge conflicts
    - open the files one-by-one
    - Inside files take decision according to the data inside <<<<<< AND >>>>>> and remove additional things
    - Then add these files (git add <file1> etc)
    - then do, `git commit -m <msg>`
    - `git push origin master`
    - So, we basically create a new commit in which merge conflicts are resolved.
- Tools available for easy resolution of merge conflicts:
    - sublime merge

