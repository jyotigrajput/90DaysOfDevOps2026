# Day 24 – Advanced Git: Merge, Rebase, Stash & Cherry Pick


### Task 1: Git Merge 
- While merging first go to branch in which merge need to perform
- Ex . for while merging feature-login branch in master branch go to master then merge branch
    - ```
      git checkout master
      git merge devops
      ```
- What is a fast-forward merge?
      - No new commit created 
- When does Git create a merge commit instead?
      - new merge commit created when two branch have new commit
- What is a merge conflict? (try creating one intentionally by editing the same line in both branches)
      - When two developer on different branch committed in same file on same line and while merging git confused which line to keep and merge conflict occured
---

### Task 2: Git Rebase — Hands-On
1. Create a branch `feature-dashboard` from `main`, add 2-3 commits
    - `$ git checkout -b feature-dashboard`
2. While on `main`, add a new commit (so `main` moves ahead)
     ```
       $ git checkout master
        <<Added 3 commit>>
     ```
3. Switch to `feature-dashboard` and rebase it onto `main`
    ```
       $ git checkout feature-dashboard
       $ git rebase merge
    ```
4. Observe your `git log --oneline --graph --all` — how does the history look compared to a merge?
   - It shows visual history of all branches
   - What does rebase actually do to your commits?
      - timeline or sequence will be maintained from refernace branch 
   - How is the history different from a merge?
       -  rebase gives straight history while merge create new merge commit
   - Why should you **never rebase commits that have been pushed and shared** with others?
       - 
   - When would you use rebase vs merge?

---

### Task 3: Squash Commit vs Merge Commit
1. Create a branch `feature-profile`, add 4-5 small commits (typo fix, formatting, etc.)
2. Merge it into `main` using `--squash` — what happens?  
3. Check `git log` — how many commits were added to `main`?
4. Now create another branch `feature-settings`, add a few commits
5. Merge it into `main` **without** `--squash` (regular merge) — compare the history
6. Answer in your notes:
   - What does squash merging do?
   - When would you use squash merge vs regular merge?
   - What is the trade-off of squashing?

---

### Task 4: Git Stash — Hands-On
1. Start making changes to a file but **do not commit**
2. Now imagine you need to urgently switch to another branch — try switching. What happens?
3. Use `git stash` to save your work-in-progress
4. Switch to another branch, do some work, switch back
5. Apply your stashed changes using `git stash pop`
6. Try stashing multiple times and list all stashes
7. Try applying a specific stash from the list
8. Answer in your notes:
   - What is the difference between `git stash pop` and `git stash apply`? 
   - When would you use stash in a real-world workflow?

---

### Task 5: Cherry Picking
1. Create a branch `feature-hotfix`, make 3 commits with different changes
2. Switch to `main`
3. Cherry-pick **only the second commit** from `feature-hotfix` onto `main`
4. Verify with `git log` that only that one commit was applied
5. Answer in your notes:
   - What does cherry-pick do?
   - When would you use cherry-pick in a real project?
   - What can go wrong with cherry-picking?


Happy Learning!
**TrainWithShubham**
