SSH Honeypot Project with Cowrie on Kali Linux

Introduction
This project demonstrates how to deploy and configure a Cowrie SSH honeypot on Kali Linux for cybersecurity monitoring and attacker analysis.

Objectives
- Understand honeypot deployment
- Monitor brute-force attacks
- Capture attacker activity
- Analyze SSH login attempts

Tools Used
- Kali Linux
- Cowrie Honeypot
- Python3
- Git
- GitHub

Installation Steps

Update System
sudo apt update && sudo apt upgrade -y

Install Dependencies
sudo apt install git python3 python3-pip python3-venv libssl-dev libffi-dev build-essential authbind -y

Clone Cowrie
git clone https://github.com/cowrie/cowrie.git

Create Virtual Environment
python3 -m venv cowrie-env

Start Cowrie
bin/cowrie start

Monitoring Logs
tail -f var/log/cowrie/cowrie.log

Security Considerations
This project was deployed in a controlled lab environment for educational cybersecurity purposes only

Conclusion
This project demonstrates practical cybersecurity skills involving honeypot deployment, monitoring, and log analysis.
