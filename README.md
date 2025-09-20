# System Health Monitoring Script

This project provides a **simple Linux system health monitoring script** that checks CPU usage, memory usage, disk usage, and process count. It logs the results and highlights any metric that exceeds predefined thresholds.

Features:

- Monitors:
  - CPU usage
  - Memory usage
  - Disk usage
  - Running processes
- Logs output to a file: `system_health.log`
- Alerts with `[ALERT]` if any metric exceeds thresholds:
  - CPU > 80%
  - Memory > 80%
  - Disk > 80%
  - Processes > 300
- Runs automatically **every 1 minute** using cron


Setup Instructions:

1. **Clone the repository** to your Ubuntu EC2 instance:
   ```bash
   git clone https://github.com/arjumandshafi/system-health-monitor.git
   cd system-health-monitor

Make the script executable:

chmod +x system_health_monitor.sh

Test the script manually:

./system_health_monitor.sh

cat /home/ubuntu/system-health-monitor/system_health.log


Set up cron for automation:

crontab -e

Add the following line at the bottom:

* * * * * /home/ubuntu/system-health-monitor/system_health_monitor.sh >> /home/ubuntu/system-health-monitor/system_health.log 2>&1

This runs the script every minute and appends output to the log file.

Verify cron is running:

systemctl status cron

View logs:

tail -f /home/ubuntu/system-health-monitor/system_health.log

then push the code to github with logs:

git add .

git commit -m " system health logs"

git push -u origin main
