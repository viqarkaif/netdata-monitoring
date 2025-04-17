# netdata-monitoring
# DevOps Internship – Task 7: System Monitoring with Netdata

## ✅ Objective
Monitor system resources (CPU, RAM, Disk, Docker containers) using **Netdata** and visualize the data in real-time.

---

## 🚀 What Was Done

1. **Docker Setup**:
   - Installed Docker on the EC2 instance.
   - Ran **Netdata** container with additional permissions to monitor Docker.

2. **Netdata Configuration**:
   - Configured custom alerts for system resources:
     - CPU usage > 80%
     - RAM usage > 85%
     - Disk space < 15%
   - Triggered alerts using the `stress` tool to simulate high CPU and memory usage.

3. **Docker Container Monitoring**:
   - Monitored Docker container performance: CPU, memory, disk I/O, network stats.
   - Ensured that Netdata was able to track app container performance (`viqarkaif/nodejs-demo-app`).

4. **Netdata Logs**:
   - Checked and documented logs at `/var/log/netdata/`.
   - Verified that there were no errors in the `error.log` file.

---

## 🔧 Commands Used

```bash
# Docker Install & Run Netdata
docker run -d --name=netdata -p 19999:19999 --cap-add=SYS_PTRACE --security-opt apparmor=unconfined netdata/netdata

# Entering the Netdata container for configuration
docker exec -it netdata bash

# Creating Custom Alerts
vi /etc/netdata/health.d/my-custom-alerts.conf

# Restarting the Netdata container
docker restart netdata

# Stress Test for triggering alerts (CPU/Memory)
sudo apt install stress -y
stress --cpu 2 --timeout 60

📸 Screenshots
Netdata Dashboard showing resource metrics.

Alarms section showing active alerts for CPU, RAM, and Disk.

Error Log from /var/log/netdata/ showing no issues.

Access Log for verifying dashboard access.

📋 Learnings & Key Takeaways
Gained hands-on experience with real-time system monitoring.

Configured custom alerts for resource usage thresholds.

Explored Netdata logs for system diagnostics.

Strengthened skills in Docker container monitoring.

