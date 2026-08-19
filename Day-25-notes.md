# Day 25 – Git Reset vs Revert & Branching Strategies

   - What is the difference between `--soft`, `--mixed`, and `--hard`?
      
      - `--soft` = `git reset --soft <commit-id>` Undo the commited changes in staged area and head will point to given commit id
      - `--mixed` = `git reset --mixed <commit-id>`  Undo the committed changes in untracked area but keep them in working directory and  head will point to given commit id
      - `--hard` =  `git reset --hard <commit-id> ` deleted changes permenantly above mentioned commit-id 
   - Which one is destructive and why?
       - ` git reset --hard <commit_id>` is destructive because it deleted the changes permanantely
   - When would you use each one?
   - Should you ever use `git reset` on commits that are already pushed?
     - No 
---

### Task 2: Git Revert — Hands-On
1. Made  3 commits (commit X, Y, Z)
  ```
    ubuntu@ip-172-31-24-48:~/git-practice$ git log --oneline
    82ce21d (HEAD -> master) Z commit revert
    d0d0b49 y commit revert
    38d76a3 X commit revert
  ```
2. Revert commit Y (the middle one) — what happens?
    - New commit added after `git revert d0d0b49`
3. Check `git log` — is commit Y still in the history?
   - Yes it is present in history
4. Answer in your notes:
   - How is `git revert` different from `git reset`?
       - `git reset` moved branch pointer to another commit and rewrite history
       - `git revert ` - undo changes of commit and create new revert commit
   - Why is revert considered **safer** than reset for shared branches?
       - reset removes history but in revert changes present in history
   - When would you use revert vs reset?
      - revert for changes that already pushed to shared branch 
      - reset for local/unshared work 
---

### Task 3: Reset vs Revert — Summary
Create a comparison in your notes:

| | `git reset` | `git revert` |
|---|---|---|
| What it does | undo changes & remove commit and rewrite history | undo the change and create the new commit by removing changes |
| Removes commit from history? | yes | No |
| Safe for shared/pushed branches? | No | yes |
| When to use | for local/unshared work | working with already pushed/shared |

---

### Task 4: Branching Strategies
1. **GitFlow** — develop, feature, release, hotfix branches
      - Traditional strategy with several long-lived branches
      -  main
           │
           └── develop
                 ├── feature/login
                 ├── feature/payment
                 └── feature/profile
        - **Good for** - large project with scheduled releases and multiple environments
        - More branches so more complexity
2. **GitHub Flow** — simple, single main branch + feature branches
     - new feature branch created from main branch
     - main
        │
        ├── feature/login
        │
        └── feature/payment
       - Create branch -> Make changes ->Push branch ->create pull request -> code review ->Merge into main ->deploy
       - **Good for**  - For frequent deployment
         
3. **Trunk-Based Development** — everyone commits to main, short-lived branches
      -               feature A
                          │
         main ────────────┼───────────────
                          │
                       merge quickly
       - Developer frequently add changes to main
       - **Good for** -  CI/CD, frequent deployments
       - Important: Feature flags are often used when a feature isn't ready for users but the code needs to be merged.
5. Answer:
   - Which strategy would you use for a startup shipping fast? -- `Github Flow`
   - Which strategy would you use for a large team with scheduled releases? -- `Git Flow`
   - Which one does your favorite open-source project use? (check any repo on GitHub) -- `Github Flow`

---

---
