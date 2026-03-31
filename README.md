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
