# Windows Log Parser & Threat Hunter (`log_hunter.py`)

## 🧠 Project Overview
This project  **Log Hunter**  is an enterprise-grade **Windows Event Log & Threat Hunting tool** I developed to support Security Operations Center (SOC) workflows.  
It automates the process of **collecting, parsing, and analyzing Windows event logs**, detects suspicious activity (such as brute-force attempts or privilege escalation), and integrates with **VirusTotal** and **YARA** for file reputation and malware signature scanning.

The goal was to simulate what a **cyber analyst** does in an enterprise environment: **collect data, hunt anomalies, correlate threats, and validate findings** using multiple threat intelligence sources.


## 🔍 Key Features
- 🪟 **Windows Log Parsing** — Supports both live log collection via `pywin32` and offline `.evtx` file analysis.  
- 🔎 **Threat Detection Rules** — Built-in SOC logic to flag brute-force attacks, privilege escalation, PowerShell misuse, and more.  
- 🧬 **YARA Scanning** — Identifies malware artifacts using built-in or custom YARA rules.  
- 🧠 **VirusTotal Integration** — Automatically checks file hashes (SHA256) against VirusTotal’s database with API rate-limiting.  
- 📊 **CSV Reporting & Summaries** — Exports findings and statistics for easy review or SIEM ingestion.  
- ⚙️ **Extensible Design** — Modular architecture allows analysts to add new detection logic or integrations easily.


## ⚙️ Tech Stack
| Component | Technology Used |
|------------|----------------|
| **Language** | Python |
| **Log Sources** | Windows Event Viewer (live & EVTX) |
| **Threat Intelligence** | VirusTotal API |
| **Malware Analysis** | YARA (built-in + custom rules) |
| **Libraries** | `pywin32`, `python-evtx`, `requests`, `yara-python`, `hashlib`, `argparse` |
| **Output Formats** | CSV reports & console summaries |


## 🧩 Detection Logic Example
**Brute-force Detection (Event ID 4625)**  
Tracks multiple failed logins within a time window:
```python
THREAT_RULES = {
    "brute_force": {"event_id": 4625, "threshold": 5, "window_min": 5},
    "privilege_escalation": {"event_id": 4672, "suspicious_accounts": ["Guest", "DefaultAccount"]},
    "account_lockout": {"event_id": 4740, "threshold": 3},
    "powershell_exec": {"event_id": 4104, "keywords": ["downloadstring", "invoke-expression", "base64"]},
    "new_service": {"event_id": 7045, "suspicious_paths": ["temp", "appdata", "programdata"]}
}
````

**Sample Alert Output:**

```
⚠️  BRUTE_FORCE - Severity: HIGH
   User: admin
   Attempts: 8
   Timeframe: 2025-11-09 09:10:23 to 2025-11-09 09:14:55
```


## 🧪 Example Workflow

1. **Live Log Monitoring**

   ```bash
   python log_hunter.py log Security --detect --summary
   ```

2. **Offline EVTX Analysis**

   ```bash
   python log_hunter.py evtx Security.evtx --ids 4625,4672 --summary
   ```

3. **Directory Malware Scan (with VirusTotal + YARA)**

   ```bash
   python log_hunter.py scan C:\Users\Public --hash --yara --vt-key YOUR_API_KEY
   ```


## 📈 Example Output (CSV)

| Time                | ID   | Type | Source                              | Message                          | YARA_Match | VT_Status     |
| ------------------- | ---- | ---- | ----------------------------------- | -------------------------------- | ---------- | ------------- |
| 2025-11-09 09:12:34 | 4625 | WARN | Microsoft-Windows-Security-Auditing | Failed login attempt             | clean      | clean/unknown |
| 2025-11-09 09:14:55 | 4625 | WARN | Microsoft-Windows-Security-Auditing | Failed login attempt             | clean      | clean/unknown |
| 2025-11-09 09:16:12 | 4672 | INFO | Microsoft-Windows-Security-Auditing | Privilege assigned to user Guest | clean      | MALWARE       |


## 💼 What I Learned

* Parsing and analyzing **Windows Event Logs** at scale (Security, System, Application).
* Applying **threat detection logic** similar to what SIEM and SOC systems use.
* Integrating **multiple threat intelligence sources** into one workflow (YARA + VirusTotal).
* Building **efficient, analyst-friendly CLI tools** for data triage and incident response.
* Handling **rate limits, error cases, and large data sets** programmatically.


## 🚀 Future Improvements

* Add correlation between different log sources (System + Security).
* Integrate with **Elastic Stack (ELK)** for visualization.
* Introduce **real-time alert notifications** (Slack / email).
* Extend YARA library for **specific APT and ransomware families**.


> 💡 This project demonstrates my ability to combine **threat intelligence, malware analysis, and log forensics** into a unified SOC workflow  the kind of analytical mindset essential for a **Cybersecurity Analyst**.


