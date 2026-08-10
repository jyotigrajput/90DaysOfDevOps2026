## Basic commands
1. git init - intialization git repository 
2. git log  - show commit history/log
3. git status - show current working directory status  from untracked and staging area
4. git config --global user.email 'jyotigrajput@gmail.com' & git config --global user.name 'jyotigrajput' - set git global variables
5. git add <filename> - Adding files in staging area
6. git commit -m "Commit- msg" -Creates a commit from the staged changes and records a snapshot in Git history.
7. git remote add  origin https://<token>@github.com/jyotigrajput/Github-practice.git  - Setting origin value


## Branch commands
1. git branch -  list local branches
2. git checkout <branch_name> - switching to branch
3. git checkout -b <branch_name> - Creating and switching to new branch
4. git switch <branch_name> -switching to another branch
5. git branch -d <branch_name> - deleting branch

## Push and Pull command
1. git push -u origin <branch> -  push changes to github in mentioned branch
2. git pull origin master - pulling changes from `origin/master` and merge them into current branch
3. git fetch origin - fetching changes from all the repositories along with different branches
4. git fetch upstream  - Get the latest changes from the original repository.
   
