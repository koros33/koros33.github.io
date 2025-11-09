# Purple Team Zero

## 🧠 Project Overview
**PurpleTeamZero** is my ongoing, production-ready framework for **purple-team exercises**  combining offensive emulation (Red Team) with defensive validation (Blue Team).  
It’s designed to test how well security controls, detections, and analysts respond to simulated attacks such as **PowerShell abuse, brute-force attempts, and credential misuse**.

The project bridges the gap between **attack simulation** and **defense evaluation**, allowing me to model real adversarial behavior and verify whether detection systems (like my `log_hunter.py` or IDS) trigger properly.

> 🟣 **Status:** In Production  actively maintained and evolving with new attack modules and detection validators.





## 🔍 Key Capabilities
- **Attack Emulation (Red Team)**  
  Simulates real adversarial behaviors using MITRE ATT&CK-aligned YAML definitions and PowerShell payloads.  
  Each attack is safely contained and logged for replay and tuning.

- **Detection Validation (Blue Team)**  
  Uses `log_hunter.py` to verify detection triggers, confirm alert quality, and measure defensive visibility.

- **Automated Validation (Purple Integration)**  
  `validator.py` checks logs, correlates alert IDs, and produces a pass/fail matrix per technique.

- **Safe Sandbox Execution**  
  The `emulator.py` component runs all scripts in a controlled environment to avoid real damage.



## 🧰 Tech Stack
- **Language:** Python + PowerShell  
- **Frameworks:** MITRE ATT&CK mapping  
- **Tools:** VirusTotal, YARA, Windows Event Viewer, IDS_NEW integration  
- **OS:** Windows / Linux hybrid testing lab  


## ⚔️ Example Workflow
1. **Run an emulation** (e.g., PowerShell abuse)

    ``` python
    run_purple.py --attack T1059_powershell.yaml
    ````


3. **Monitor with detection tools**

 `log_hunter.py` for event logs
 `IDS_NEW` for network triggers


4. **Validate results**

   ```bash python
   validator.py --attack T1059_powershell.yaml --logs logs/ids_alerts.log
   ````

5. **Generate a detection report**

   ```
   ✅ Detection: PowerShell Command & Control
   🧩 Technique: T1059
   🔥 Triggered Rules: 3
   📊 Detection Confidence: HIGH
   ```


## 💼 What I Learned

* Designing **safe red-team simulations** that replicate real MITRE ATT&CK behaviors.
* Automating **blue-team validation** and correlating multiple log sources.
* Building a **feedback loop** between attacks and detections to strengthen defenses.
* Understanding how **purple-team collaboration** improves SOC maturity.



## 🚀 Future Plans

* Add new emulations for **phishing**, **lateral movement**, and **exfiltration**.
* Integrate with **ELK Stack dashboards** for visual reporting.
* Expand YAML schemas to include **adversary metadata** (group names, TTPs, impact).


> 💡 *PurpleTeamZero* represents my drive to master both **attack simulation** and **defensive engineering**, closing the loop between red and blue into a unified, data-driven purple-team workflow.

