# Introduction to Git

## Install and configure git
1. Verify Git is installed on your machine
  `git version`
2. Set up your Git identity — name and email
   
   `git config --global user.email 'jyotigrajput@gmail.com'`
   
   `git config --global user.name 'jyotigrajput'`
    
3. Verify your configuration
```
ubuntu@ip-172-31-25-135:~$ git config --list
user.email=jyotigrajput@gmail.com
user.username=jyotigrajput

```

## Create Git project 
1. Create a new folder called devops-git-practice - `mkdir devops-git-practice`
2. Initialize it as a Git repository - `cd devops-git-practice && git init` 
3. Check the status — read and understand what Git is telling you -` git status`
     - git status show which file are in untracked, stage and track area
4. Explore the hidden .git/ directory — look at what's inside
      - in .git folder files ex.  HEAD, config  description. etc and folders like hooks, info,logs,objects,refs present

## Stage and commit changes
1. Stage your file

`ubuntu@ip-172-31-25-135:~/devops-git-practice$ git add . `

2. Check what's staged
```
ubuntu@ip-172-31-25-135:~/devops-git-practice$ git status 
On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   demo.txt
```

3. Commit with a meaningful message
```
ubuntu@ip-172-31-25-135:~/devops-git-practice$ git commit -m "Adding demo.txt"
[master (root-commit) 50c6e6f] Adding demo.txt
 1 file changed, 2 insertions(+)
 create mode 100644 demo.txt
```
   
5. View your commit history
```
ubuntu@ip-172-31-25-135:~/devops-git-practice$ git log
commit 50c6e6ff9cc3f61a9f973e530cd1464626bde2c8 (HEAD -> master)
Author: Ubuntu <jyotigrajput@gmail.com>
Date:   Thu Aug 6 06:51:05 2026 +0000
Adding demo.txt
```

## Understand the Git Workflow
1. What is the difference between `git add` and `git commit`?
     - `git add` - add the files from untracked to staged area
     - `git commit ` - add the files from staged area to tracked area
     
2. What does the staging area do? Why doesn't Git just commit directly?
     - preparing/keeping the file before commit
     - 
3. What information does git log show you?
       - it show commit history
4. What is the .git/ folder and what happens if you delete it?
       -  .git folder contain git repo information as commit history,index,head information and by deleting it will erase history
    
5. What is the difference between a working directory, staging area, and repository?
        1. working directory - in which we can modified the file
        2. staging area - buffer area before commit (files created for commit)
        3. repository - local directory with .git folder
