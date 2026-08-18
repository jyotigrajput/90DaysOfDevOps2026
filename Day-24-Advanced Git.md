# Day 24 – Advanced Git: Merge, Rebase, Stash & Cherry Pick

## Challenge Tasks

### Task 1: Git Merge — Hands-On
1. Created a new branch `feature-login` from `main`, added a couple of commits to it
     
           $ git checkout -b feature-login
              < 3 commits added on feature-login>
   
            ubuntu@ip-172-31-24-48:~/git-practice$ git log --oneline
            0013b8c (HEAD -> feature-login) 2 login commit
            a1c0925 2 login commit
            b658919 1 login commit
            302928f (master) thirs login commit
            9b7456d second commit
            3e28972 first login commit
            12d602a added commit on main branch
  
2. Switch back to `main` and merge `feature-login` into `main`
   
           ubuntu@ip-172-31-24-48:~/git-practice$ git checkout master
            Switched to branch 'master'
            ubuntu@ip-172-31-24-48:~/git-practice$ git merge feature-login
            Updating 302928f..0013b8c
            **Fast-forward**
             feature-login-new.txt | 5 +++++
             1 file changed, 5 insertions(+)
             create mode 100644 feature-login-new.txt
   
3. Now created another branch `feature-signup`, added commits to it — but also added a commit to `main` before merging
   
         $ git checkout -b feature-signup
             204227d (HEAD -> feature-signup) feature-signup commit
            0013b8c (feature-login) 2 login commit
            a1c0925 2 login commit
            b658919 1 login commit
            302928f thirs login commit
            9b7456d second commit
            3e28972 first login commit
            12d602a added commit on main branch

            - commit added to main as well
     
5. Merge `feature-signup` into `main`
    
       ` $git  merge feature-signup`
       - This time merge commit created
       ```
           ubuntu@ip-172-31-24-48:~/git-practice$ git log --oneline
            c23830a (HEAD -> master) Merge branch 'feature-signup'//Merge commit> 
            d264706 4th  commit
            204227d (feature-signup) feature-signup commit
            0013b8c (feature-login) 2 login commit
            a1c0925 2 login commit
            b658919 1 login commit
            302928f thirs login commit
            9b7456d second commit
            3e28972 first login commit
            12d602a added commit on main branch
       ```
   - What is a fast-forward merge?
       - `When targeted branch has no new commit since feature branch created`
   - When does Git create a merge commit instead?
       - `Merge commit created when targeted branch also have new commit along with feature branch`
   - What is a merge conflict?
        - Two developer changed same line contents on different branch and when trying to merge git get confused which code to keep so developer have to resolve the conflict manually
        - After removing merge conflict commit is required
---

### Task 2: Git Rebase — Hands-On
1. Created a branch `feature-dashboard` from `main`, added 3 commits
   ```
       $ git checkout -b feature-dashboard
       $ git log --oneline
        b0b0cd1 (HEAD -> feature-dashboard) dashboard added 3
        e7af053 dashboard added 2
        5acb0cf dashboard added
   ```
2. While on `main`, add a new commit (so `main` moves ahead)
   ```
     ubuntu@ip-172-31-24-48:~/git-practice$ git log --oneline
        94a727e (HEAD -> master) main branch 6
        9909c6b main branch 5
        5d6a52e main branch 5
   ```
3. Switch to `feature-dashboard` and rebase it onto `main`
4. Observe your `git log --oneline --graph --all` — how does the history look compared to a merge?
   Notes:
   - What does rebase actually do to your commits?
       - arrange commits in sequential timeline 
   - How is the history different from a merge?
      -  rewrite project history and merge join two history lines together and saved special as merge step 
   - When would you use rebase vs merge?
      - `merge` to add changes from branch to another
      - `rebase` in case you branch get behind from main branch
---

### Task 3: Squash Commit vs Merge Commit
1. Created a branch `feature-profile`, added 4-5 small commits
   
           $ git checkout -b feature-profile
           ubuntu@ip-172-31-24-48:~/git-practice$ git log --oneline
            9406fae (HEAD -> feature-profile) profile commit 4
            2aa75b7 profile commit 3
            b82c54b profile commit 2
            81b9194 profile commit 1
2. Merge it into `main` using `--squash` — what happens?
    ```
        git merge --squash feature-profile
        --- Updating 94a727e..9406fae
            Fast-forward
            Squash commit -- not updating HEAD
             feature-profile.txt | 7 +++++++
             1 file changed, 7 insertions(+)
             create mode 100644 feature-profile.txt
       $ git commit -m "squash commit"
    ```
4. Checking with `git log` 
    - single squash commit added to main for 3 commit in feature-profile
5. Now created another branch `feature-settings`, added a few commits
6. Merge it into `main` **without** `--squash` (regular merge) — comparing the history
    - In squash merge single commit added after merge but in regular merge 3 commits added in main

   - When would you use squash merge vs regular merge?
         - when there is long commit history and we want to keep simple history in main then squash otherwise regular
    
---

### Task 4: Git Stash — Hands-On
1. Made the changes to a file but **did not commit**
2. If I urgently switch to another branch  -`local changes will be overwritten by checkout and ask to either commit or stash`
3. Use `git stash` to save your work-in-progress
    ```
        ubuntu@ip-172-31-24-48:~/git-practice$ git stash 
        Saved working directory and index state WIP on master: cabc007 feature 3wq commit
    ``` 
4. Apply your stashed changes using `git stash pop`
    ```
        ubuntu@ip-172-31-24-48:~/git-practice$ git stash pop
        On branch feature-settings
        Changes not staged for commit:
          (use "git add <file>..." to update what will be committed)
          (use "git restore <file>..." to discard changes in working directory)
                modified:   merge-commit-test.txt
        
        no changes added to commit (use "git add" and/or "git commit -a")
        Dropped refs/stash@{0} (9a7041f5ad5143d034306f168c5bd5ed215797bf)
    ```
5. Notes:
   - What is the difference between `git stash pop` and `git stash apply`?
      - `git stash pop ` - add all stash files in untracked area
      - `git stash apply <stash_id>` - select specific stash file with id
   - When would you use stash in a real-world workflow?
     - I am working on branch and don't want to discard changes and suddenly I need to do switch to another branch then
---

### Task 5: Cherry Picking
1. Created a branch `feature-hotfix`, made 3 commits with different changes

        $ git checkout feature-hotfix
        ubuntu@ip-172-31-24-48:~/git-practice$ git log --oneline
        d7245f0 (HEAD -> feature-hotfix) hotfix 3 commit
        38480e7 hotfix 2 commit
        8ea5418 hotfix 1 commit

2. Cherry-pick **only the second commit** from `feature-hotfix` onto `main`
    - Only 1 commit merge in master from `feature-hotfix` branch
    - `$ git cherry-pick 489ff29` 
3. notes:
   - What does cherry-pick do?
         - merge single commit to targeted branch(for ex. main)
   - When would you use cherry-pick in a real project?
        - when we want to merge single commit from one branch to current branch without branch merging and rebasing entire branch


