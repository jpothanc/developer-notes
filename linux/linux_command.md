# 🧠 Linux Support & Troubleshooting Cheat Sheet

---

## 🧩 Basic Process Commands

| Task | Command |
|------|---------|
| View all processes | `ps -ef` |
| View process tree | `pstree -p` |
| Filter Java processes | `ps -ef | grep java` |
| Top live CPU/mem usage | `top` or `htop` |
| Kill a process by PID | `kill -9 <PID>` |
| Monitor command repeatedly | `watch -n 2 'ps -ef | grep java'` |
| Background a process | `command &` |
| Bring background job to foreground | `fg` |
| List background jobs | `jobs` |

---

## 🔬 Advanced Process Inspection

| Task | Command |
|------|---------|
| Detailed CPU/memory usage | `ps -eo pid,ppid,user,cmd,%mem,%cpu --sort=-%cpu | head` |
| Show process threads | `ps -Lp <PID>` or `top -H -p <PID>` |
| List open files by PID | `lsof -p <PID>` |
| Process env variables | `cat /proc/<PID>/environ | tr '\0' '\n'` |
| Current working dir | `ls -l /proc/<PID>/cwd` |
| Memory maps | `cat /proc/<PID>/maps` |
| Zombie process check | `ps aux | awk '$8=="Z"'` |
| Process limits | `cat /proc/<PID>/limits` |

---

## ☕ Java-Specific Tools

| Task | Command |
|------|---------|
| List Java processes | `jps -v` |
| Thread dump | `jstack <PID>` |
| Heap histogram | `jmap -histo <PID>` |
| Class histogram | `jcmd <PID> GC.class_histogram` |
| Dump heap | `jmap -dump:live,format=b,file=heapdump.hprof <PID>` |
| GC stats | `jstat -gcutil <PID> 1s 5` |

---

## 📜 Log Viewing & Tailing

| Task | Command |
|------|---------|
| Tail last 10 lines | `tail file.log` |
| Live tail log | `tail -f file.log` |
| Search logs for keyword | `grep "ERROR" file.log` |
| Count lines in log | `wc -l file.log` |
| View first N lines | `head -n 50 file.log` |
| Filter logs with timestamp | `grep "2025-05-01" file.log` |
| Combine tail + grep | `tail -f file.log | grep "Exception"` |

---

## 🌐 Network Diagnostics

| Task | Command |
|------|---------|
| List listening ports | `ss -ltnp` or `netstat -tulnp` |
| Check if port is bound | `ss -ltnp | grep :8080` |
| Find process using port | `lsof -i :8080` |
| Test URL reachability | `curl -I http://host:port` |
| Ping a host | `ping <host>` |
| DNS lookup | `nslookup <domain>` |
| Trace route | `traceroute <host>` |
| Show active connections | `ss -antp` or `netstat -antp` |
| Monitor per-process traffic | `sudo nethogs` |
| Check open sockets | `ss -s` |

---

## 💾 Disk Space & File Usage

| Task | Command |
|------|---------|
| Check mounted filesystem usage | `df -h` |
| Check directory size | `du -sh /path/to/dir` |
| Largest files (top 10) | `find . -type f -exec du -h {} + | sort -rh | head -n 10` |
| Disk inode usage | `df -i` |
| Check free space in `/tmp` | `df -h /tmp` |

---

## 📅 Cron Jobs

| Task | Command |
|------|---------|
| View user crontab | `crontab -l` |
| Edit user crontab | `crontab -e` |
| Cron schedule syntax | `* * * * * /path/to/script.sh` |
| Check if cron ran | `grep CRON /var/log/syslog` or `cat /var/log/cron` |
| Cron test logging | Add `>> /tmp/myscript.log 2>&1` to the script |

---

## 🧪 System Diagnostics

| Task | Command |
|------|---------|
| CPU info | `lscpu` |
| Memory usage | `free -h` |
| Uptime | `uptime` |
| Load average | `uptime` or `cat /proc/loadavg` |
| Top memory consumers | `ps -eo pid,ppid,cmd,%mem --sort=-%mem | head` |
| Top CPU consumers | `ps -eo pid,ppid,cmd,%cpu --sort=-%cpu | head` |
| Swap usage | `swapon --show` |
| Mounted filesystems | `mount` or `findmnt` |

---

## 🧠 Miscellaneous

| Task | Command |
|------|---------|
| Check current user | `whoami` |
| Show env variables | `printenv` |
| Find path of a command | `which java` |
| Search in current dir | `find . -name "*.log"` |
| Re-run last command | `!!` |
| Run as another user | `sudo -u <user> command` |
| List system users | `cut -d: -f1 /etc/passwd` |

