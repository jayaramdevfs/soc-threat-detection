# 🚀 SOC Threat Detection Project: Student Walkthrough & Demo Guide

Hi! This guide will help you understand, run, and present your **SOC Threat Detection Log Analyzer** project to your college lecturers. 

It's designed to be short, structured, and easy to explain.

---

## 💡 1. Project Overview (What is this?)
This project simulates a **Security Operations Center (SOC)** tool. It acts like a mini-SIEM (Security Information and Event Management) system.
- **Goal:** Read authentication logs (like Linux server login attempts), analyze them, and find hackers trying to guess passwords (Brute Force) or suspicious logins.
- **Inputs:** A text file containing sample Linux login logs (`logs/sample_auth.log`).
- **Process:** The Python script parses the logs and runs them through a "Detection Engine" containing security rules.
- **Outputs:** It prints **Security Alerts** in the terminal and saves a report to `incident_report.json`.

---

## 🛠️ 2. Prerequisites (What do you need?)
Before you showcase this project, install the following on your laptop:
1. **Python 3.9+**: Required to run the main code. [Download here](https://www.python.org/downloads/).
2. **VS Code (Recommended)**: A good code editor to show the code to your lecturers.
3. **Docker Desktop (Optional but Impressive)**: Shows you know how to containerize applications. [Download here](https://www.docker.com/products/docker-desktop/).

---

## ▶️ 3. How to Run & Demo the Project

### **Method A: The Standard Python Way (Easiest)**
1. Open your terminal (Command Prompt / PowerShell / VS Code Terminal).
2. Go to your project folder:
   ```bash
   cd path/to/soc-threat-detection
   ```
3. Install the required Python packages (only needs to be done once):
   ```bash
   pip install -r requirements.txt
   ```
4. Run the threat analyzer against the sample logs:
   ```bash
   python src/main.py logs/sample_auth.log
   ```
5. **Boom!** You will see the security alerts pop up in your terminal. You can show this output directly to your lecturer.

### **Method B: The Docker Way (Advanced/Pro level)**
1. Make sure **Docker Desktop** is open and running in the background.
2. In your terminal, build the container image:
   ```bash
   docker build -t soc-analyzer .
   ```
3. Run the container:
   ```bash
   docker run soc-analyzer
   ```
*(This proves to your lecturer that your project is ready for modern Cloud/DevOps environments!)*

---

## 🕵️ 4. How to Explain the Features (For Your Presentation)

When demonstrating the code, here is what you should point out:

*   **The Log Parser (`src/log_parser.py`):** Show them how it uses Regular Expressions (Regex) to extract the Time, User, and IP address from messy log text.
*   **The Detection Engine (`src/detection_engine.py`):** This is the core "brain". Show them the 3 rules you built:
    1.  **Brute Force:** If an IP fails to login 10 times in 5 minutes.
    2.  **Suspicious Login:** If a user logs in from an IP they have never used before.
    3.  **Abnormal Time:** If someone logs in successfully outside of normal working hours (8 AM to 6 PM).
*   **The Test File (`tests/test_detection.py`):** Show them you wrote "Unit Tests." Run `pytest tests/` in the terminal to prove your security rules actually work without errors.

---

## 🧪 5. How to Live-Test it (Show off!)
You can trick the system live during your demo!
1. Open up `logs/sample_auth.log`.
2. Add 10 new "Failed password" lines for a fake user (e.g., `hacker`) from a fake IP (e.g., `9.9.9.9`).
3. Run `python src/main.py logs/sample_auth.log` again.
4. Watch the new **Brute Force Alert** catch the fake hacker you just added! 

Good luck with your presentation! 🎓
