# 🖥️ Monitor System Resources Using Netdata for DevOps

This project demonstrates how to install and run **Netdata**, a real-time monitoring tool, to visualize system and Docker container performance metrics using Docker.

---

## 🎯 Objective
To monitor system resources (CPU, memory, disk I/O, network, and Docker containers) in real-time using **Netdata**, and to save logs for analysis.

---

## 🛠 Tools & Technologies Used

- 🐳 Docker
- 📊 Netdata (Official Docker Image)
- 🐧 Ubuntu (hosted on AWS EC2)
- 📂 Linux CLI Tools

---

## ⚙️ Steps to Run Netdata via Docker

### ✅ 1. Install Docker (if not already installed)
```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER
newgrp docker
```

### ✅ 2. Run Netdata Container
```bash
docker run -d --name=netdata -p 19999:19999   --cap-add SYS_PTRACE   --security-opt apparmor=unconfined   netdata/netdata
```

---

## 🌐 Access the Netdata Dashboard

- On your local system: `http://localhost:19999`
- On a remote server: `http://<your-ec2-ip>:19999`

> Make sure port `19999` is open in your security group.

---

## 📊 Features Explored

- CPU, Memory, Disk I/O, Network Monitoring
- Real-time monitoring of Docker containers
- Netdata alert thresholds
- Dashboard panels with detailed graphs

---

## 📝 Logs

### ✅ Saved Logs:
I accessed the container logs using:
```bash
docker logs netdata > Netdata_logs.txt
```

- The file `Netdata_logs.txt` contains captured logs from the Netdata container.
- Logs were also explored inside the container at `/var/log/netdata`.

To view logs:
```bash
docker exec -it netdata bash
cd /var/log/netdata
ls
cat error.log
```

---

## 🧪 Output Screenshots

Screenshots added to the GitHub repo include:

- ✅ Netdata dashboard (overview and resource graphs)
- ✅ Running container (`docker ps`)
- ✅ Logs and service behavior

---

## 📁 Folder Structure

```bash
netdata-monitoring/
├── Netdata_logs.txt
├── screenshots/
├── README.md
```

---

## 📌 Learnings

- How to deploy Netdata using Docker
- Accessing real-time system health data
- Saving and reading logs
- Basic Docker and Linux admin operations

---

Thanks for reading! 📈🧠
