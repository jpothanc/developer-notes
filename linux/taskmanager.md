# Check Task Manager in Linux

```bash

# 1. Using top (Real-time process viewer)
top
# - Press 'q' to quit.

# 2. Using htop (Interactive process viewer, more user-friendly)
# If not installed, install it first:
sudo apt install htop      # For Debian/Ubuntu
sudo yum install htop      # For RedHat/CentOS
# Launch htop:
htop
# - Use arrow keys to navigate, and press 'q' to quit.

# 3. Using ps (Snapshot of current processes)
ps -aux
# - a: Show processes for all users
# - u: Display user-oriented format
# - x: Show processes not attached to a terminal

# 4. Using top with specific sorting (CPU usage example)
top -o %CPU
# - Sort processes by CPU usage in descending order.

# 5. Using glances (Detailed real-time system monitoring tool)
# If not installed, install it first:
sudo apt install glances    # For Debian/Ubuntu
sudo yum install glances    # For RedHat/CentOS
# Launch glances:
glances
# - Press 'q' to quit.

# 6. Using system-monitor GUI (Desktop environment-specific)
# For GNOME-based systems:
gnome-system-monitor
# For KDE-based systems:
ksysguard
# For Xfce-based systems:
xfce4-taskmanager

# 7. Using kill to stop processes (Optional Task Management)
# Find a process by name:
ps -aux | grep process_name
# Kill a process by PID:
kill PID
# Force kill a process:
kill -9 PID
```

# Core Dump

```bash
# Create Crash and Hang Dumps in Linux

## 1. Enable Core Dumps (For Crashes)

# 1.1 Check current ulimit (core dump size limit)
ulimit -c
# If it shows "0", core dumps are disabled.

# 1.2 Enable core dumps for the current session
ulimit -c unlimited

# 1.3 Make this change permanent by editing the shell configuration file
# For bash:
echo "ulimit -c unlimited" >> ~/.bashrc
source ~/.bashrc

# 1.4 Set core dump file size in /etc/security/limits.conf
sudo nano /etc/security/limits.conf
# Add the following lines:
*    soft    core    unlimited
*    hard    core    unlimited

# 1.5 Define core dump file path and naming
sudo nano /etc/sysctl.conf
# Add or edit:
kernel.core_pattern=/tmp/core.%e.%p
# - %e: Executable name
# - %p: Process ID

# 1.6 Reload sysctl configuration
sudo sysctl -p

# 1.7 Generate a core dump (simulate a crash)
# Use a crashing application or run:
kill -SIGSEGV <PID>

---

## 2. Create Hang Dumps

# 2.1 Install gcore (from gdb package if not installed)
sudo apt install gdb         # For Debian/Ubuntu
sudo yum install gdb         # For RedHat/CentOS

# 2.2 Use gcore to generate a memory dump of a hanging process
gcore <PID>
# - <PID>: Process ID of the application
# The dump file will be saved as core.<PID> in the current directory.

# 2.3 Analyze the dump using gdb or other debugging tools
gdb /path/to/executable core.<PID>
# Example:
gdb ./myapp core.12345

---

## 3. Trigger Core Dumps on Signals (Optional)

# 3.1 Enable core dumps when a specific signal is sent
sudo nano /etc/systemd/system.conf
# Add or uncomment:
DefaultLimitCORE=infinity

# 3.2 Restart the systemd service to apply changes
sudo systemctl daemon-reexec

---

## 4. Automate Dumps for Java Applications (Optional)

# 4.1 Add JVM options for crash and hang dumps
java -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/tmp \
     -XX:+UseParallelGC -XX:+CrashOnOutOfMemoryError

# 4.2 Generate a thread dump manually for a Java process
kill -3 <PID>
# The thread dump will be logged to the Java process output (e.g., stdout).

---

## 5. Common Tools for Dump Creation and Analysis

# Debugging Tools:
# - gdb: Debugging and analyzing core dumps.
# - strace: Trace system calls and signals for hanging processes.
# - lsof: List open files by processes to diagnose hangs.
# - perf: Advanced performance monitoring.

# Example: Trace a process with strace
strace -p <PID> -o trace.log

# Example: Analyze open files for a hanging process
lsof -p <PID>

```
