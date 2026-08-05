Linux Practice
--

Process check
--
1.**ps** - process information
```
PID TTY          TIME CMD
2953 pts/0    00:00:00 bash
4519 pts/0    00:00:00 ps
```
2. **top** - interactive process viewer

```
top - 11:30:35 up  4:23,  1 user,  load average: 0.09, 0.02, 0.01
Tasks: 115 total,   1 running, 114 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :    908.7 total,    174.1 free,    326.3 used,    524.6 buff/cache     
MiB Swap:      0.0 total,      0.0 free,      0.0 used.    582.4 avail Mem 
 PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                             
 1 root      20   0   25228  16044  10936 S   0.0   1.7   0:02.63 systemd                                                                                             
 2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd                                                                                            
 3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                                              
 4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp                                                                                    
 5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq
```

3. **pgrep systemd** - return proccesid with specific keyword
   
```
128
196
.
.
```
System check
--
4. **Systemctl status**
```
ubuntu@ip-172-31-19-72:~$ systemctl status
● ip-172-31-19-72
    State: running
    Units: 486 loaded (incl. loaded aliases)
     Jobs: 0 queued
   Failed: 0 units
    Since: Mon 2026-08-03 07:07:17 UTC; 4h 30min ago
  systemd: 259.5-0ubuntu3
  Tainted: unmerged-bin
   CGroup: /
           ├─init.scope
           │ └─1 /sbin/init
           ├─system.slice
           │ ├─ModemManager.service
           │ │ └─769 /usr/sbin/ModemManager
           │ ├─acpid.service
```

4. **systemctl list-units** - current state of syyetmd units active or loaded ins system memory

  1. UNIT - systemd unit name
  2. LOAD - services status loaded, error,stub
  3. ACTIVE -  activation state of unit (active, inactive,reloading,failed)
  4. SUB - (Running, exited,dead,mounted)

```
UNIT                                                                         LOAD   ACTIVE SUB       DESCRIPTION                                                        >
proc-sys-fs-binfmt_misc.automount                                            loaded active running   Arbitrary Executable File Formats File System Automount Point      >
sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p1.device      loaded active plugged   Amazon Elastic Block Store cloudimg-rootfs
```

Log check
--
1. **journalctl -u <service>**
```
ubuntu@ip-172-31-19-72:~$ journalctl -u ssh
Aug 03 07:07:29 ip-172-31-19-72 systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Aug 03 07:07:29 ip-172-31-19-72 sshd[1007]: Server listening on 0.0.0.0 port 22.
Aug 03 07:07:29 ip-172-31-19-72 sshd[1007]: Server listening on :: port 22.
Aug 03 07:07:29 ip-172-31-19-72 systemd[1]: Started ssh.service - OpenBSD Secure Shell server
.
.

```

Mini troubleshooting steps
--
**Inspecting ssh service**
--
1. Check status of service
     ***systemctl status ssh***- checking service active and running
2. Checking logs of service
     ***journalctl -u ssh -n 10*** --no-pager -> show top 10 lines of logs
3. ***ss -tulpn | grep <port_number>*** -> checking which port service is listening
