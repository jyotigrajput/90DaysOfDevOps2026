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
    - New commit added after `git rever d0d0b49`
3. Check `git log` — is commit Y still in the history?
   - Yes it is present in history
4. Answer in your notes:
   - How is `git revert` different from `git reset`?
       - `git reset` moved branch pointer to another commit and rewrite history
       - `git revert ` - undo changes of commit and create new revert commit
   - Why is revert considered **safer** than reset for shared branches?
       - reset removes history but in revert it is maintained 
   - When would you use revert vs reset?
      - revert for changes that already pushed to shared branch 
      - reset for local/unshared work 
---

### Task 3: Reset vs Revert — Summary
Create a comparison in your notes:

| | `git reset` | `git revert` |
|---|---|---|
| What it does | ? | ? |
| Removes commit from history? | ? | ? |
| Safe for shared/pushed branches? | ? | ? |
| When to use | ? | ? |

---

### Task 4: Branching Strategies
Research the following branching strategies and document each in your notes with:
- How it works (short description)
- A simple diagram or flow (text-based is fine)
- When/where it's used
- Pros and cons

1. **GitFlow** — develop, feature, release, hotfix branches
2. **GitHub Flow** — simple, single main branch + feature branches
3. **Trunk-Based Development** — everyone commits to main, short-lived branches
4. Answer:
   - Which strategy would you use for a startup shipping fast?
   - Which strategy would you use for a large team with scheduled releases?
   - Which one does your favorite open-source project use? (check any repo on GitHub)

---

### Task 5: Git Commands Reference Update
Update your `git-commands.md` to cover everything from Days 22–25:
- Setup & Config
- Basic Workflow (add, commit, status, log, diff)
- Branching (branch, checkout, switch)
- Remote (push, pull, fetch, clone, fork)
- Merging & Rebasing
- Stash & Cherry Pick
- Reset & Revert

---
