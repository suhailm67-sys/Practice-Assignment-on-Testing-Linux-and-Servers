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
