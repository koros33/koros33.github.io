## 🔍 Threat Hunting Notebook — Parent/Child Process Anomalies

This notebook demonstrates how to hunt for suspicious **parent–child process relationships** using Windows event logs (Sysmon Event ID 1).  
It’s a practical, analyst-focused investigation that shows how attackers abuse normal processes to hide activity.

### 🔧 Techniques Covered
- Parsing Sysmon process creation logs  
- Building parent–child process trees with Python  
- Identifying abnormal process behavior  
- Detecting suspicious chains like:
  - `winword.exe → powershell.exe`
  - `cmd.exe → certutil.exe`
  - `explorer.exe → unknown.exe`

### 📊 What You’ll See in the Notebook
- Clean code for loading & analyzing logs  
- Markdown explanations of each step  
- A simple detection logic example  
- A real-world hunting scenario  
- Clear output showing suspicious process paths  

Thank you.
