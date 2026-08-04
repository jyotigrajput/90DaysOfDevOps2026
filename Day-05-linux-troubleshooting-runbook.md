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
   ```bash
     ubuntu@ip-172-31-19-72:~$ df -h 
      Filesystem       Size  Used Avail Use% Mounted on
      /dev/root        6.7G  2.7G  4.0G  41% /
      tmpfs            455M     0  455M   0% /dev/shm
      tmpfs            182M  916K  181M   1% /run
      efivarfs         128K  3.3K  120K   3% /sys/firmware/efi/efivars
      tmpfs            455M     0  455M   0% /tmp
      /dev/nvme0n1p13  989M  164M  759M  18% /boot
      /dev/nvme0n1p15  105M  6.3M   99M   7% /boot/efi
      none             1.0M     0  1.0M   0% /run/credentials/getty@tty1.service
      none             1.0M     0  1.0M   0% /run/credentials/serial-getty@ttyS0.service
      none             1.0M     0  1.0M   0% /run/credentials/systemd-journald.service
      none             1.0M     0  1.0M   0% /run/credentials/systemd-resolved.service
      none             1.0M     0  1.0M   0% /run/credentials/systemd-networkd.service
      tmpfs             91M  8.0K   91M   1% /run/user/1000
   ```
3. **`du -sh /var/log`** - Check disk usage of a specific directory
4. **`iostat`** - Show input/output device statistics
5. **`vmstat`** - Show virtual memory statistics
6. **`dstat -cdnm`** - Show system resource statistics realtime

          -c- cpu usage
          -d - disk usage
          -n - network statics
          -m - memory usage
          
---

## Network

1. **`ss -tulpn`** / **`netstat -tulpn`** - Show listening ports
  ```bash
  ubuntu@ip-172-31-19-72:~$ ss -tulpn
  Netid           State            Recv-Q           Send-Q                           Local Address:Port                        Peer Address:Port           Process           
  udp             UNCONN           0                0                                   127.0.0.54:53                               0.0.0.0:*                                
  udp             UNCONN           0                0                                127.0.0.53%lo:53                               0.0.0.0:*                                                  
  tcp             LISTEN           0                5                                    127.0.0.1:4330                             0.0.0.0:*
```
3. **`curl -I <endpoint>`** / **`ping <endpoint>`** - Check endpoint connectivity
```bash
HTTP/1.1 301 Moved Permanently
Location: http://www.google.com/
Content-Type: text/html; charset=UTF-8
Content-Security-Policy-Report-Only: object-src 'none';base-uri 'self';script-src 'nonce-lt-T1bKLZ2tG7CSQmxO5rw' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
Date: Tue, 04 Aug 2026 17:01:59 GMT
Expires: Thu, 03 Sep 2026 17:01:59 GMT
Cache-Control: public, max-age=2592000
Server: gws
Content-Length: 219
X-XSS-Protection: 0
```
---

## Logs

1. **`journalctl -u <service> -n 50`** - Show the last 50 log entries for a service
2. **`tail -n 50 /var/log/<file>.log`** - Show the last 50 lines of a log file

---

## Quick Findings

- service is running
- CPU utlization is  0 % and memory utilization 1.2%

