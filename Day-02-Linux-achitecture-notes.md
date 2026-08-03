Core components of Linux 
---
1. **Kernal space** - Highly priviledge space , directly communicate with OS 
2. **User space** - It is for applications like bash, ediror,  Un priviledge space , can not directly communicate with OS, required systemcall to communicate with kernal space
3. **init/systemd** - 

init - tradition linux initalization system & first process start during boot using runlevel

Systemd - Modern linux init system 
        - manage sytem services,dependencies & system resource
        - Manage proccess manually using **systemctl** 


What systemd does and why it matters
--
- PID 1/first process
- Service and system manager
- Manage services after kernal reboots
- Auto restart failed services

How process are created and managed ?
--
- Running active program/application
- for ex. executing script, run command
- Every process has PID, parent process, memory state

  ** Process creation proccess **
  ```
                  User runs command (for ex ls in Bash)
                            |
                  Parent shell create new [process (Fork)  --> Child process created for ls
                           |
                  new process load program (Exec) --> loas "ls" using exec
                          |
                  kernal will assign PID
                          |
                  process start running
```

**Process State**
1. Running- Currently in progress
2. Sleeping - waiting for event/input
3. Zombie -Finish executing but waiting for parent didn't acknowledge
4. Stopped - Stopped/pause for signal

**Process command**
--
1. ps - provide process information PID, timestamp, cmd
2. ps aux -detail description of process as PID, CPU Memory usage ,user
3. top - interactive process viewver - total process as per state running, zombies and other info
4. htop - give you option to monitor the system, use some keys like
          F1- open help menu,
          F3 '/' - search specific character
          F4 Search the process with keyword
          F6 - Sort process by columns CPI, memory usage
          F9 - kill the process
          F10/Q - Quit and exit program
5. pgrep <process name> - find process id with name / ps aux | grep 'cron'
6. pkill <process name> - send signal by process name
7. kill <PID> terminate the process by PID
8. nice - Setting priority of new process (use ps -l command to view priority column NI) 
9. renice -n 10 -p PID - adjust priority for running process
10. jobs - show active running jobs
11. bg %<jobid> - resume pause job and run it backgroun
12. fg %<jobid> - resume job in foreground 


