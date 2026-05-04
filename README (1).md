# 🌐 Network Traffic Monitor

**A real-time network packet sniffing and analysis platform**  
built with Python · Flask · Scapy · HTML/CSS/JS

---

## 📌 Overview

**Network Traffic Monitor** is a web-based platform that captures and analyzes live network packets in real time. It provides a clean dashboard to monitor protocols, filter traffic, view statistics, and export data — all accessible through a browser.

> 🎓 Developed as a **Computer Networks course project** at university level.  
> ⚡ Implements **real-time packet sniffing** using Scapy for extra credit.

---

## ✨ Features

- 🔴 **Live Packet Capture** — Real-time sniffing via Scapy on all network interfaces
- 🔍 **Protocol Detection** — Identifies TCP, UDP, and ICMP packets
- 🗂️ **Port-to-Service Mapping** — Maps 15+ well-known ports (HTTP, HTTPS, DNS, SSH, FTP, etc.)
- 📊 **Live Statistics** — Total packets, per-protocol counts, avg/min/max sizes, top source IPs
- 🔎 **Advanced Filtering** — Filter by Protocol, Source IP, Destination IP, and Service name
- 📋 **Activity Logs** — Timestamped log panel with last 100 entries
- 📥 **CSV Export** — Download all captured packets as a `.csv` file
- 🔐 **Secure Login** — Session-based authentication with UUID token validation
- 🎨 **Dark UI** — Cyberpunk-themed interface with animated gradient borders

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend Language | Python 3.x |
| Web Framework | Flask |
| Packet Capture | Scapy (`sniff`, `IP`, `TCP`, `UDP`, `ICMP`) |
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| Data Export | Python `csv.DictWriter` |
| Authentication | Flask Sessions + UUID Tokens |

---

## 📁 Project Structure

```
network-traffic-monitor/
│
├── app.py               # Main Flask application & packet handler
├── login.html           # Login page (served via Flask templates)
├── index.html           # Main dashboard UI
├── users.json           # Credential store (auto-created on first login)
└── README.md            # This file
```

> **Note:** `login.html` and `index.html` should be placed inside a `templates/` folder for Flask to serve them correctly.

```
network-traffic-monitor/
│
├── app.py
├── templates/
│   ├── login.html
│   └── index.html
└── users.json
```

---

## ⚙️ Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/network-traffic-monitor.git
cd network-traffic-monitor
```

### 2. Install Dependencies

```bash
pip install flask scapy
```

### 3. Run the Application

> ⚠️ **Administrator/root privileges are required** for Scapy to capture live packets.

**Windows (run as Administrator):**
```bash
python app.py
```

**Linux / macOS (run with sudo):**
```bash
sudo python app.py
```

### 4. Open in Browser

```
http://127.0.0.1:5000
```

---

## 🔑 Default Login Credentials

| Field | Value |
|-------|-------|
| Username | `admin` |
| Password | `admin` |

> Credentials are stored in `users.json` and can be changed from within the dashboard settings.

---

## 🖥️ How to Use

1. **Login** — Open the app in your browser and sign in with the default credentials.
2. **Start Monitoring** — Click the **Start** button to begin live packet capture.
3. **View Packets** — The packet table updates in real time with all captured traffic.
4. **Apply Filters** — Use the filter bar to narrow results by Protocol, Source IP, Destination IP, or Service.
5. **Check Stats** — View the statistics panel for traffic breakdown and summaries.
6. **Export Data** — Click **Download CSV** to save all captured packets locally.
7. **Stop Monitoring** — Click the **Stop** button to halt packet capture.

---

## 📡 Captured Packet Fields

Each captured packet contains the following information:

| Field | Description |
|-------|-------------|
| `No` | Packet sequence number |
| `Time` | Capture timestamp (HH:MM:SS) |
| `Source IP` | Sender's IP address |
| `Destination IP` | Receiver's IP address |
| `Protocol` | TCP / UDP / ICMP |
| `Packet Size` | Size in bytes |
| `Source Port` | Sender's port number |
| `Destination Port` | Receiver's port number |
| `Service` | Derived service name (e.g. HTTP, DNS, SSH) |

---

## 🗺️ Port-to-Service Mapping

| Port | Service | Port | Service |
|------|---------|------|---------|
| 80 | HTTP | 443 | HTTPS |
| 53 | DNS | 21 | FTP |
| 22 | SSH | 25 | SMTP |
| 110 | POP3 | 143 | IMAP |
| 3306 | MySQL | 8080 | HTTP-Alt |
| 23 | Telnet | 3389 | RDP |
| 67/68 | DHCP | 123 | NTP |

---

## 📊 Statistics Provided

The `/stats` endpoint returns:

- **Total Packets** captured
- **TCP / UDP / ICMP** packet counts
- **HTTP traffic** count (ports 80, 443, 8080)
- **Average / Max / Min** packet size (bytes)
- **Top 5 Source IPs** by traffic volume
- **Service breakdown** dictionary

---

## 🔐 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/` | Main dashboard (login required) |
| `GET/POST` | `/login` | Login page |
| `GET` | `/logout` | Logout and clear session |
| `POST` | `/start` | Start packet capture |
| `POST` | `/stop` | Stop packet capture |
| `POST` | `/clear` | Clear all captured data |
| `GET` | `/data` | Get packets + logs (supports filter params) |
| `GET` | `/stats` | Get traffic statistics |
| `GET` | `/download` | Download packets as CSV |

### Filter Parameters for `/data`

```
/data?protocol=TCP&src_ip=192.168.1.1&dst_ip=8.8.8.8&service=DNS
```

---

## ⚠️ Requirements & Notes

- Python **3.8 or higher**
- Must be run with **administrator / root** privileges for Scapy packet capture
- Tested on **Windows 10/11** and **Ubuntu 22.04**
- Scapy on Windows may require **Npcap** or **WinPcap** to be installed

### Install Npcap (Windows only)
Download from: [https://npcap.com/#download](https://npcap.com/#download)

---

## 📄 License

This project is licensed under the **MIT License**.  
Feel free to use, modify, and distribute for educational purposes.

---

<div align="center">

Made with ❤️ for Computer Networks

</div>
