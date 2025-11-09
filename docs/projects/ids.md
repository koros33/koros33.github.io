# Intrusion Detection System (IDS)

## 🧠 Project Overview
This project is a **lightweight Intrusion Detection System (IDS)** that I built as a proof-of-concept for real-time threat detection.  
It focuses on **network visibility, signature-based detection, and incident logging**, all implemented from scratch in Python.  

The goal was to understand how detection engines work under the hood — from packet capture to alert correlation — and to demonstrate practical skills in **threat analysis**, **network monitoring**, and **rule-driven security automation**.


## 🔍 Key Features
- **Rule-Based Detection:** YAML-driven rules make it easy to define new attack patterns (e.g., SQLi, XSS).  
- **Real-Time Alerts:** Suspicious packets trigger instant alerts stored in `ids_alerts.log`.  
- **Traffic Replay & Simulation:** Built-in tools for generating and replaying PCAP files for realistic testing.  
- **Modular Design:** Clear separation between the detection engine, utilities, and configuration files for scalability.



## 🧰 Tech Stack
- **Language:** Python  
- **Libraries:** Scapy / PyShark, YAML, Logging  
- **Environment:** Linux / macOS  
- **Testing Tools:** tcpreplay, custom PCAP generator  


## 💼 What I Learned
Building this IDS helped me:
- Understand **how intrusion detection engines work** internally.  
- Write **modular, testable Python code** for cybersecurity use cases.  
- Develop and tune **detection rules** to minimize false positives.  
- Gain experience with **packet analysis** and **log correlation** — critical for cyber analyst roles.  


## ⚡ Example Workflow
1. Define attack signatures in `config/rules.yaml`.  
2. Run the IDS on a live interface (`eth0` or `wlan0`).  
3. Replay traffic or monitor real packets.  
4. Review alerts in `logs/ids_alerts.log` to identify anomalies.

