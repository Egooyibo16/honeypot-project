SSH Honeypot Project with Cowrie on Kali Linux

Introduction
This project demonstrates the deploymentv and configuration of a cowrie SSH honeypot on Kali Linux for cybersecurity monitoring and attacker analysis.

Obgjectives
1. Understand how honeypots work
2. Deploy an SSH honeypot
3. Monitor brute-force login attempts
4. Capture attacker commands and logs

TOOLS USED
A. Kali Linux
B. Cowrie Honeypot
C. Python3
D. Git
E. Github

INSTALLATION STEPS UPDATE SYSTEM
1. Update sytem
   Bash
   sudo apt update && sudo apt upgrade -y
2. Install Dependencies
  Bash
sudo apt install git python3 python3-pip python3-venv libssl-dev libffi-dev build-essential authbind -y
3. Clone Cowrie
 Bash
git clone https://github.com/cowrie/cowie.git
cd cowrie
4. Create Virtual Environment
 Bash
python3 -m venv cowrie-env
source cowrie-env/bin/activate
5. Install Requirements
 Bash
pip install --upgrade pip
pip install -r requirements.txt
6. Configure Cowrie 
 Bash
cp etc/cowrie.cgc.dist etc/cowrie.cfg
7. Start Cowrie
 Bash
bin/cowrie start
8. Monitor Logs
 Bash
tail -f var/log/cowrie/cowrie.log


SECURITY CONSIDERATIONS
This project was deployed in a controlled lab environment for educational
and defensive cybersecurity purposes only.

CONCLUSION
This project demonstrates practical cybersecurity skills involving honeypot
deployment, monitoring and log analysis using Kali Linux and Cowrie.
