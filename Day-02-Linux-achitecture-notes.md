#Core components of Linux 
1. **Kernal space** - Highly priviledge space , directly communicate with OS 
2. **User space** - It is for applications like bash, ediror,  Un priviledge space , can not directly communicate with OS, required systemcall to communicate with kernal space
3. **init/systemd** - 

init -tradition linux initalization system & first process start during boot using runlevel

systemd - Modern linux init system 
        - manage sytem services,dependencies & system resource
        - Manage proccess manually using **systemctl** 

#What systemd does and why it matters
- PID 1/first process
- Service and system manager
- Manage services after kernal reboots
- Auto restart failed services


How process are created and managed ?


