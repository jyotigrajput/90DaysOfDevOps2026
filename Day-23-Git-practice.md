### Task 1: Branching Commands — Hands-On
In your `devops-git-practice` repo, perform the following:
1. List all branches in your repo
   -  `git branch`
2. Create a new branch called `feature-1` and Switch to `feature-1`
    - ` git checkout -b feature-1 `
3. Create a new branch and switch to it in a single command — call it `feature-2`
   - `git checkout -b feature-2 `
4. Try using `git switch` to move between branches — how is it different from `git checkout`?
    - ` git switch main ` - modern way for switching branch
    - ` git checkout master ` - used to restore the files also
   
5. Make a commit on `feature-1` that does **not** exist on `main`
      ```
      ubuntu@ip-172-31-25-135:~/devops-git-practice$ git checkout feature-1
      Switched to branch 'feature-1'
      ubuntu@ip-172-31-25-135:~/devops-git-practice$ vim feature-1.txt
      ubuntu@ip-172-31-25-135:~/devops-git-practice$ git add feature-1.txt 
      ubuntu@ip-172-31-25-135:~/devops-git-practice$ git commit -m  "feature added to branch"
      [feature-1 a2cb091] feature added to branch
       1 file changed, 2 insertions(+)
       create mode 100644 feature-1.txt
      ```
6. Switch back to `main` — verify that the commit from `feature-1` is not there
      ```
      $ git switch master
      Already on 'master'
      $ git log
      commit 22b473c0620fd4bc819301eeaeb7aae70bb11e0f (HEAD -> master, feature-2)
      Author: Ubuntu <jyotigrajput@gmail.com>
      Date:   Mon Aug 10 12:39:15 2026 +0000
      
          first commit
      
      ```
7. Delete a branch you no longer need
    ```
    ubuntu@ip-172-31-25-135:~/devops-git-practice$ git branch -d feature-2
    Deleted branch feature-2 (was 22b473c)
    ```


### Task 2: Push to GitHub
1. **new repository** created on GitHub with name "Github-practice"
2. Connecting `devops-git-practice` repo to the GitHub remote
      -  `git remote add  origin https://<token>@github.com/jyotigrajput/Github-practice.git`
3. Push your `main` branch to GitHub
     - `git push -u origin master`
4. Push `feature-1` branch to GitHub
     -  - `git push -u origin feature-1 `
5.What is the difference between `origin` and `upstream`?
    - `original` - remote repo clone from own github
    - `upstream` - origin repo from fork repo coming 
 ---

### Task 3: Pull from GitHub
```
    $ git pull origin master
    remote: Enumerating objects: 5, done.
    remote: Counting objects: 100% (5/5), done.
    remote: Compressing objects: 100% (2/2), done.
    remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
    Unpacking objects: 100% (3/3), 956 bytes | 956.00 KiB/s, done.
    From https://github.com/jyotigrajput/Github-practice
    * branch            master     -> FETCH_HEAD
     22b473c..c28818f  master     -> origin/master
    Updating 22b473c..c28818f
    Fast-forward
    demo.txt | 2 ++
    1 file changed, 2 insertions(+)

```
1. What is the difference between `git fetch` and `git pull`?
    - `git fetch` - fetch all changes from whole repo including other branches
    - `git pull` - pulling changes locally from particular branch

---

### Task 4: Clone vs Fork
1. What is the difference between clone and fork?
    -  `git clone ` - getting code locally from github
    - `git fork` - cloning repository in github

2. After forking, how do you keep your fork in sync with the original repo?
     - `git fetch upstream`
    
