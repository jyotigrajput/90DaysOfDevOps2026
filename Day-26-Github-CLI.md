# Day 26 – GitHub CLI: Manage GitHub from Your Terminal


### Task 1: Install and Authenticate
1. Install the GitHub CLI on your machine --> `sudo apt install gh`
2. Authenticate with your GitHub account --> `gh auth login`
     ```
       ubuntu@ip-172-31-24-48:~$ gh auth login
        ? What account do you want to log into? GitHub.com
        ? What is your preferred protocol for Git operations on this host? HTTPS
        ? Authenticate Git with your GitHub credentials? Yes
        ? How would you like to authenticate GitHub CLI? Login with a web browser
        
        ! First copy your one-time code: 2062-D77E
        Press Enter to open github.com in your browser... 
        ! Failed opening a web browser at https://github.com/login/device
          exec: "xdg-open,x-www-browser,www-browser,wslview": executable file not found in $PATH
          Please try entering the URL in your browser manually
        ✓ Authentication complete.
        - gh config set -h github.com git_protocol https
        ✓ Configured git protocol
        ! Authentication credentials saved in plain text
        ✓ Logged in as jyotigrajput
     ```
4. Verify you're logged in and check which account is active
    `gh auth status`
   
     ```
       ubuntu@ip-172-31-24-48:~$ gh auth status
          github.com
        ✓ Logged in to github.com account jyotigrajput (/home/ubuntu/.config/gh/hosts.yml)
        - Active account: true
        - Git operations protocol: https
        - Token: gho_************************************
        - Token scopes: 'gist', 'read:org', 'repo', 'workflow'
     ```
6. Answer in your notes: What authentication methods does `gh` support?
      1. Webrowser Device code  (8 digit OTP)
      2. Personal access token (PAT)
---

### Task 2: Working with Repositories
1. Create a **new GitHub repo** directly from the terminal — make it public with a README
     - `gh repo create githubcli-demo --public  --clone --add-readme`
     ```
       ubuntu@ip-172-31-24-48:~$ gh repo create githubcli-demo --public  --clone --add-readme
      ✓ Created repository jyotigrajput/githubcli-demo on GitHub
        https://github.com/jyotigrajput/githubcli-demo
        Cloning into 'githubcli-demo'...
     ```
3. Clone a repo using `gh` instead of `git clone`
   - `gh repo clone <reponame> `
5. View details of one of your repos from the terminal
     ```
       ubuntu@ip-172-31-24-48:~/githubcli-demo$ gh repo view
        jyotigrajput/githubcli-demo
        No description provided
           githubcli-demo                                                                                                     
        View this repository on GitHub: https://github.com/jyotigrajput/githubcli-demo
     ```
7. List all your repositories
     - `gh repo list`
9. Open a repo in your browser directly from the terminal
      - ` gh repo view https://github.com/jyotigrajput/githubcli-demo  --web `
11. Delete the test repo you created (be careful!)
    -  
---

### Task 3: Issues
1. Create an issue on one of your repos from the terminal — give it a title, body, and a label
    - First clone the repo and go inside repo locally and run below command
    - `gh issue create --title "Bug in login" --body "issue in login functionality" --label "bug"`
       
3. List all open issues on that repo
     ```
       ubuntu@ip-172-31-24-48:~/github-demo/Github-practice$ gh issue list
      Showing 1 of 1 open issue in jyotigrajput/Github-practice
      
      ID  TITLE         LABELS  UPDATED            
      #1  Bug in login  bug     about 7 minutes ago
     ```
5. View a specific issue by its number
    - `gh issue view 1 --repo https://github.com/jyotigrajput/Github-practice.git`
7. Close an issue from the terminal
    - ` gh issue close <issue no>`
9. Answer in your notes: How could you use `gh issue` in a script or automation?
    - 
---

### Task 4: Pull Requests
1. Create a branch, make a change, push it, and create a **pull request** entirely from the terminal
   -   gh pr create --title "CLI-pr" --body "Testing for CLI"
     
3. List all open PRs on a repo
```
       ubuntu@ip-172-31-24-48:~/github-demo/Github-practice$ gh pr list

Showing 1 of 1 open pull request in jyotigrajput/Github-practice

ID  TITLE   BRANCH    CREATED AT        
#2  CLI-pr  cli-demo  about 1 minute ago
     ```
5. View the details of your PR — check its status, reviewers, and checks
    ` gh pr view <PR No>`
6. Merge your PR from the terminal
    ```
      buntu@ip-172-31-24-48:~/github-demo/Github-practice$ gh pr merge
      Merging pull request jyotigrajput/Github-practice#2 (CLI-pr)
      ? What merge method would you like to use? Create a merge commit
      ? Delete the branch locally and on GitHub? No
      ? What's next? Edit commit message
      ? What's next? Submit
      ✓ Merged pull request jyotigrajput/Github-practice#2 (CLI-pr)
    ```
7. Answer in your notes:
   - What merge methods does `gh pr merge` support?
        - Close the Pull request and merge the code
   - How would you review someone else's PR using `gh`?
        1. `gh pr list`
        2. `gh pr view <PR_Number>`
---

### Task 5: GitHub Actions & Workflows (Preview)
1. List the workflow runs on any public repo that uses GitHub Actions
      - `gh workflow list --repo https://github.com/LondheShubham153/devboard `
2. View the status of a specific workflow run
    - ` gh run view`
3. Answer in your notes: How could `gh run` and `gh workflow` be useful in a CI/CD pipeline?
    - `gh run` - monitor and debugging specific workflow run
    - `gh workflow` - managing and triggring workflow 

### Task 6: Useful `gh` Tricks
Explore and try these — add the ones you find useful to your `git-commands.md`:
1. `gh api` — make raw GitHub API calls from the terminal
2. `gh gist` — create and manage GitHub Gists
3. `gh release` — create and manage releases
4. `gh alias` — create shortcuts for commands you use often
5. `gh search repos` — search GitHub repos from the terminal
