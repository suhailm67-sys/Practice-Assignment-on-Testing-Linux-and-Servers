# Practice-Assignment-on-Testing-Linux-and-Servers
Practice Assignment on Testing, Linux and Servers

# Task 1: System Monitoring Setup
# 1. Install Monitoring Tools:
1. sudo apt update
2. sudo apt install htop -y
3. sudo apt install nmon -y
# 2. Disk Usage Monitoring:
1. Check overall disk usage: df -h
2. Check directory-level usage: du -sh /home/*
# 3. Process Monitoring
1. View running processes: ps aux
2. Find top CPU-consuming processes: ps aux --sort=-%cpu | head -10
3. Find top memory-consuming processes: ps aux --sort=-%mem | head -10
# 4. Create Monitoring Logs (Reporting System)
1. Create Script: sudo nano monitor.sh:   #!/bin/bash

  LOGFILE="/var/log/system_monitor.log"

  echo "===== System Monitoring Report =====" >> $LOGFILE
  date >> $LOGFILE

  echo "--- CPU & Memory Usage ---" >> $LOGFILE
  top -b -n1 | head -10 >> $LOGFILE

  echo "--- Disk Usage ---" >> $LOGFILE
  df -h >> $LOGFILE

  echo "--- Top Processes (CPU) ---" >> $LOGFILE
  ps aux --sort=-%cpu | head -5 >> $LOGFILE

  echo "--- Top Processes (Memory) ---" >> $LOGFILE
  ps aux --sort=-%mem | head -5 >> $LOGFILE
  echo "====================================" >> $LOGFILE
  echo "" >> $LOGFILE
  
2. Make Script Executable: chmod +x monitor.sh

3. Run Script: sudo ./monitor.sh

4. View Logs: cat /var/log/system_monitor.log
# 5. Automate Logging
Set up a cron job to run every 5 minutes: crontab -e; */5 * * * * /path/to/monitor.sh

# Task 2: User Management and Access Control
# 1. Create Users (Sarah & Mike)
1. sudo adduser sarah
2. sudo adduser mike
# 2. Set / Update Passwords
1. sudo passwd sarah
2. sudo passwd mike
# 3. Create Dedicated Workspaces
1. sudo mkdir -p /home/sarah/workspace
2. sudo mkdir -p /home/mike/workspace
# 4. Assign Ownership
1. sudo chown -R sarah:sarah /home/sarah/workspace
2. sudo chown -R mike:mike /home/mike/workspace
# 5. Set Permissions
1. sudo chmod 777 /home/sarah/workspace
2. sudo chmod 777 /home/mike/workspace
# 6. Set Password Expiration Policy
1. sudo chage -m 1 -M 30 -W 7 sarah
2. sudo chage -m 1 -M 30 -W 7 mike
# 7. Verify Password Policy
sudo chage -l sarah

