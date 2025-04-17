# netdata-monitoring
# DevOps Internship – Task 7: System Monitoring with Netdata

## ✅ Objective
Monitor system resources (CPU, RAM, Disk, Docker containers) using **Netdata** and visualize the data in real-time.

---

## 🚀 What Was Done

1. **Docker Setup**:
   - Installed Docker on the EC2 instance.
   - ![Screenshot 2025-04-18 023427](https://github.com/user-attachments/assets/62d06275-22f0-4cf7-bc2f-2cd0145a7e34)
   - 
   - Ran **Netdata** container with additional permissions to monitor Docker.
   - ![Screenshot 2025-04-18 024558](https://github.com/user-attachments/assets/581f7e8f-4b98-40b9-a874-2f55d9e45b07)
   - ![Screenshot 2025-04-18 025232](https://github.com/user-attachments/assets/99863fb6-b7bd-4379-9e48-1bd05ba72a65)



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
   - ![Screenshot 2025-04-18 034106](https://github.com/user-attachments/assets/474220ba-2c55-4968-b18b-51f879752f8e)


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
![Screenshot 2025-04-18 030231](https://github.com/user-attachments/assets/d62e91ed-9089-4242-8078-13edc8a65a01)
![Screenshot 2025-04-18 031053](https://github.com/user-attachments/assets/99c91b33-9e93-409d-9624-3f4a741cc2f6)
![Screenshot 2025-04-18 031053](https://github.com/user-attachments/assets/5e43b6d6-3e1e-4f77-bbd5-8352b0c26046)
![Screenshot 2025-04-18 031100](https://github.com/user-attachments/assets/cf4f1771-15b0-4b87-8020-04710b3519f8)
![Screenshot 2025-04-18 031106](https://github.com/user-attachments/assets/30631f9d-c8d3-4232-95b2-5124f99628e1)
![Screenshot 2025-04-18 031120](https://github.com/user-attachments/assets/432a0eab-9ab8-4a92-909b-529fd7d16d02)
![Screenshot 2025-04-18 031125](https://github.com/user-attachments/assets/41501a99-cfc5-4ae0-b6e3-a3312f88205b)
![Screenshot 2025-04-18 031153](https://github.com/user-attachments/assets/34067b32-689d-41e5-a897-47b5759a6e3a)


Alarms section showing active alerts for CPU, RAM, and Disk.
![Screenshot 2025-04-18 032310](https://github.com/user-attachments/assets/6789810a-4267-4852-9bf5-03340e86f9f1)


Error Log from /var/log/netdata/ showing no issues.
![Screenshot 2025-04-18 034106](https://github.com/user-attachments/assets/5dfd73cf-1961-4b78-bf29-0aee0c4b7183)


Access Log for verifying dashboard access.
![Screenshot 2025-04-18 025232](https://github.com/user-attachments/assets/bc5d4ced-7743-4a84-a60f-c075bbd5fe97)


📋 Learnings & Key Takeaways
Gained hands-on experience with real-time system monitoring.

Configured custom alerts for resource usage thresholds.

Explored Netdata logs for system diagnostics.

Strengthened skills in Docker container monitoring.

