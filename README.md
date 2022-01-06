# Git Basics

## Create a new git repository
`git init`

## Git config
- `git config --global --edit` edits global config file
- `git config --local --edit` edits local config file

## Git areas
- Working Area
- Staging Area
- Stash Area

## Git add
Add file(s) from working area to staging area
```
git add file
git add file1 file2 filen
git add .
git add -a
```

## Git commit
Create a commit with the staged file(s)
```
    git commit // opens an editor to write the commit message
    git commit -m "Commit Message goes here" // commit with the provided inline commit message
```

## Working with remote repository
- Create a github account if you don't have one
- Create a github repository
- Add that github repository as a remote repo to your local repo
    ```
        git remote add <remote_name> <remote_repo_url>
   ```

    ### Publish your changes
        We use `git push` command for publishing our local changes to the remote repo
        `git push <remote_name> <local_branch/source_branch>:<remote_branch/target_branch>`
        `git push origin master:master`
        `git push origin master`

    ### Receive remote changes
        - We use `git pull` command for receiving latest changes from the remote repo into local repo.
        `git pull <remote_name> <remote_branch_name>`
        `git pull origin master`
        - Git pull command first fetches the changes from the remote then merge these changes into local branch.

## Git stash
- Creates a temporary commit
- Move files from the working tree to the stash tree/area. Making working tree clean.
- Commands
    `git stash` to create a new stash
    `git stash apply [<stash_id>]` to apply the stash to the current working tree
    `git stash pop [<stash_id>]` to apply the stash to the current working tree then drop it
    `git stash show <stash_id>` to show the summary of changes/files saved in the stash
    `git stash drop <stash_id>` to drop the stash

## gitignore file
    gitignore file helps in ignoring some file, folders or patterns that git should not track.

## git restore
    Git restore commands discard the changes from the working tree.
    eg. `git restore <file>` `git restore README.md`
    Git restore with staged option remove file(s) from the staging area and put it back in working tree.
    eg. `git restore --staged <file>` `git restore --staged README.md`

## Git reset
Git reset command is used for dropping one or more commit from the history. 
Note: Use git reset when the commits are still in your local repo.
There are three options for doing git reset.
--soft
--mixed (default)
--hard
eg. `git reset HEAD~1` drops the last commit and keep the changes in working tree
`git reset --soft HEAD~1` drops the last commit and keep the changes in staging area
`git reset --hard HEAD~1` drops the last commit and the changes as well.

## QA Branch changes
I am making changes in qa branch.

## Development branch changes
this could result in a conflic

## Git revert
Git revert command is used for dropping changes from a commit. It retains the changes done after the dropped commit. Also, it creates a new commit with the revert commit information.

eg. `git revert HEAD~1` drops the changes from last commit and create a new revert commit.

## Working with branch
- Create a new branch `git branch <new_branch_name>`
- Swith to new branch `git checkout <new_branch_name>`
- Create a new branch using checkout command `git checkout -b <new_branch_name>`. This will create a new branch and swith to it as well.
- Create a new branch using checkout command with respect to a remote branch. `git checkout <remote_branch_name>`
- List local branches `git branch`
- List remote branches `git branch -r`
- List all branches `git branch -a`

## Working with remote
- Add a remote repo `git remote add <remote_name> <remote_repo_address>`
- Remove a remote `git remote remove <remote_name>`
- View remote details `git remote -v`

## Combine changes from branches
- Merge: merge changes from development branch to master branch eg
`git checkout master`
`git merge development`

- Rebase: rebase branch development with master branch eg.
`git checkout development`
`git rebase master`

### Further reading
- Reset vs Rervert vs Checkout [here](https://sillevl.gitbooks.io/git/content/advanced/reset-checkout-revert/)
- Merge vs Rebase [here](https://sillevl.gitbooks.io/git/content/advanced/merging-vs-rebasing/)
- Git tutorial [here](https://www.atlassian.com/git/tutorials/what-is-version-control)