# Troubleshooting Drill

## Target Service / Process

---

## System Information Commands

1. **`uname -a`** - Shows kernel version
2. **`lsb_release -a`** / **`cat /etc/os-release`** - Shows Linux distribution
3. **`cat /etc/os-release`** - Shows Ubuntu version

### Service Status Check

```bash
systemctl status ssh --no-pager
```

Example:

```text
ubuntu@ip-172-31-19-72:~$ systemctl status ssh --no-pager
● ssh.service - OpenBSD Secure Shell server
  Loaded: loaded (/usr/lib/systemd/system/ssh.service; disabled; preset: enabled)
  Drop-In: /usr/lib/systemd/system/ssh.service.d
           └─ec2-instance-connect.conf
  Active: active (running) since Tue 2026-08-04 14:43:44 UTC; 1h 25min ago
```

---

## CPU / Memory

1. **`top` / `htop` / `ps`** - Process information
2. **`ps -o pid,pcpu,pmem,comm -p <PID>`** - Shows PID, CPU, memory, and command information
3. **`free -h`** - Check RAM and swap usage (low free memory can slow the system)

Example:

```bash
ubuntu@ip-172-31-19-72:~$ ps aux | grep ssh
root       26211  0.0  0.8  10716  7612 ?        Ss   14:43   0:00 sshd: /usr/sbin/sshd -D -o AuthorizedKeysCommand /usr/share/ec2-instance-connect/eic_run_authorized_keys %u %f -o AuthorizedKeysCommandUser ec2-instance-connect [listener] 0 of 10-100 startups

ubuntu@ip-172-31-19-72:~$ ps -o pid,pcpu,pmem,comm -p 26935
PID %CPU %MEM COMMAND
26935  0.0  0.8 sshd-session
```

---

## Disk & I/O

1. **`df -h`** - Check disk usage
2. **`du -sh /var/log`** - Check disk usage of a specific directory
3. **`iostat`** - Show input/output device statistics
4. **`vmstat`** - Show virtual memory statistics
5. **`dstat -cdnm`** - Show system resource statistics realtime

          -c- cpu usage
          -d - disk usage
          -n - network statics
          -m - memory usage
          
---

## Network

1. **`ss -tulpn`** / **`netstat -tulpn`** - Show listening ports
2. **`curl -I <endpoint>`** / **`ping <endpoint>`** - Check endpoint connectivity

---

## Logs

1. **`journalctl -u <service> -n 50`** - Show the last 50 log entries for a service
2. **`tail -n 50 /var/log/<file>.log`** - Show the last 50 lines of a log file

---

## Quick Findings

- 
- 
- 
- 
- 
