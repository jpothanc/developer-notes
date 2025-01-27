# Cron Cheat Sheet

## 1. Cron Basics
Cron is a time-based job scheduler that runs tasks (commands or scripts) at specified times or intervals.

### Crontab Syntax
* * * * * command_to_execute
- - - - -
| | | | |
| | | | +---- Day of the week (0 - 7) [Sunday = 0 or 7]
| | | +------ Month (1 - 12)
| | +-------- Day of the month (1 - 31)
| +---------- Hour (0 - 23)
+------------ Minute (0 - 59)

### Special Symbols
- *: Every value (e.g., every minute, every hour)
- ,: List of values (e.g., 1,15,30 = at minutes 1, 15, and 30)
- -: Range of values (e.g., 1-5 = from minute 1 to 5)
- /: Step values (e.g., */5 = every 5 minutes)

## 2. Managing Crontabs
# View current user's crontab
crontab -l

# Edit the crontab
crontab -e

# Remove the crontab
crontab -r

# View system-wide crontabs
cat /etc/crontab

## 3. Predefined Schedules
# Use special strings for common schedules
@reboot          # Runs once at system startup
@yearly          # Runs once a year (0 0 1 1 *)
@monthly         # Runs once a month (0 0 1 * *)
@weekly          # Runs once a week (0 0 * * 0)
@daily           # Runs once a day (0 0 * * *)
@hourly          # Runs once an hour (0 * * * *)

## 4. Examples of Cron Jobs
# Run a script every day at midnight
0 0 * * * /path/to/script.sh

# Run a command every 5 minutes
*/5 * * * * /path/to/command

# Run a script at 8 AM every Monday
0 8 * * 1 /path/to/script.sh

# Run a script on the 1st and 15th of every month
0 0 1,15 * * /path/to/script.sh

# Run a script every 2 hours
0 */2 * * * /path/to/script.sh

## 5. Environment Variables
# Set variables like SHELL and PATH at the top of the crontab
SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

## 6. Logging and Debugging
# Check cron logs
grep CRON /var/log/syslog   # (Most systems)

# Redirect output to a file
* * * * * /path/to/script.sh >> /var/log/script.log 2>&1

## 7. System-Wide Cron Directories
/etc/crontab            # System-wide cron jobs
/etc/cron.d/            # Additional system-wide crontabs
/etc/cron.hourly/       # Scripts run hourly
/etc/cron.daily/        # Scripts run daily
/etc/cron.weekly/       # Scripts run weekly
/etc/cron.monthly/      # Scripts run monthly

## 8. Permissions
# Only users in /etc/cron.allow can use cron.
# Users in /etc/cron.deny are blocked from using cron.

## 9. Troubleshooting Tips
# Ensure cron is running
sudo systemctl status cron

# Check script permissions
chmod +x /path/to/script.sh

# Debug a specific job by adding logging
*/5 * * * * /path/to/script.sh >> /var/log/script_debug.log 2>&1
