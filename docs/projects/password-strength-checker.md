# Password Strength Checker

## 🧠 Project Overview
A simple, analyst-friendly utility that estimates password strength using **entropy-based scoring**, provides a human-readable verdict, and visualizes estimated brute-force crack time.  
This tool demonstrates practical knowledge of password security, threat modeling, and communicating technical risk to non-technical stakeholders all useful skills for a Cybersecurity Analyst.


## ⚙️ What it Does
- Estimates **entropy (bits)** based on character classes present (lowercase, uppercase, digits, symbols).  
- Converts entropy into an **estimated brute-force crack time** assuming a baseline attacker speed (10 billion guesses/sec).  
- Prints a SHA-256 hash of the candidate password (useful for safe reporting without storing plaintext).  
- Produces a simple visualization comparing entropy vs. estimated crack time.


## 🔎 Key Design Decisions
- **Entropy model:** Counts character sets (a–z, A–Z, 0–9, symbols) and computes `log2(charset^length)`. This is a practical approximation that highlights the value of length + variety.  
- **Crack-time assumption:** Uses `10_000_000_000` guesses/second as a conservative attacker baseline (configurable in future versions).  
- **User-first output:** Provides a short verdict (`Weak` / `Moderate` / `Strong`) to make the result actionable for end-users or SOC reports.


## 🧰 Tech Stack
- **Language:** Python  
- **Libraries:** `math`, `re`, `hashlib`, `matplotlib` (for visualization)  
- **Output:** Console summary + PNG/interactive chart (when run locally)


## ▶️ How to Run
```bash
# (optionally create venv) 
pip install matplotlib

python password_checker.py
# Enter password at prompt
