SSH Honeypot Project with Cowrie on Kali Linux

Introduction

This project focuses on the deployment and configuration of an SSH honeypot using Cowrie Honeypot￼ on Kali Linux. The purpose of the project was to simulate a vulnerable SSH server in a controlled lab environment in order to observe, monitor, and analyze attacker behavior.

A honeypot is a cybersecurity defense mechanism intentionally designed to appear vulnerable or attractive to attackers. Instead of protecting real assets directly, the honeypot acts as a decoy system that gathers intelligence about malicious activities. In this project, Cowrie was used to emulate an SSH service and record attacker interactions such as login attempts, executed commands, and malware download attempts.

This project provided practical experience in Linux system administration, network security monitoring, cybersecurity analysis, and log investigation.



Objectives of the Project

The main objectives of this project were:

* Understand how honeypots work in cybersecurity
* Deploy and configure a Cowrie SSH honeypot
* Monitor brute-force SSH attacks
* Capture attacker commands and login attempts
* Analyze logs generated from malicious activity
* Gain hands-on experience with Linux command-line operations
* Understand attacker reconnaissance behavior



What is a Honeypot?

A honeypot is a fake system or service intentionally exposed to attackers for monitoring and research purposes.

Its functions include:

* detecting unauthorized access attempts
* collecting threat intelligence
* studying attacker behavior
* identifying attack techniques
* improving defensive security measures

Instead of blocking attackers immediately, a honeypot allows defenders to observe how attackers behave after gaining access.

In cybersecurity, honeypots are valuable because they provide real-world attack data.



Why SSH Honeypots are Common

SSH (Secure Shell) is one of the most targeted services on the internet because system administrators use it to remotely manage Linux servers.

Attackers frequently attempt:

* brute-force attacks
* password guessing
* credential stuffing
* automated scanning

Because SSH is constantly targeted, it is ideal for honeypot deployment and attack observation.



What is SSH?

SSH stands for:

Secure Shell

It is a secure network protocol used for:

* remote login
* remote command execution
* secure communication between systems
* server management

SSH encrypts traffic between devices, making it safer than older remote access protocols like Telnet.

Example uses include:

* managing cloud servers
* accessing remote Linux machines
* transferring files securely



Why Kali Linux Was Used

Kali Linux was selected because it is a specialized Linux distribution built for cybersecurity professionals.

Kali Linux contains tools for:

* penetration testing
* ethical hacking
* digital forensics
* vulnerability assessment
* network analysis

Advantages of Kali Linux include:

* pre installed cybersecurity utilities
* strong Linux package support
* compatibility with Python tools
* simplified software installation

It is commonly used by ethical hackers, researchers, and security analysts.



Tools Used in the Project

1. Cowrie Honeypot

Cowrie Honeypot￼ is an open source SSH and Telnet honeypot.

Cowrie simulates:

* fake SSH login systems
* fake Linux file systems
* shell environments

Its purpose is to trick attackers into believing they have accessed a real Linux server.

Cowrie records:

* usernames
* passwords
* attacker IP addresses
* executed commands
* downloaded files
* session activity



2. Python3

Python is widely used in cybersecurity because it supports:

* automation
* scripting
* networking
* malware analysis
* penetration testing

Cowrie itself is built primarily using Python.



3. Git

Git is used to:

* download repositories
* manage project versions
* track code changes

Git allows cybersecurity professionals to install tools directly from GitHub repositories.



4. GitHub

GitHub￼ is a cloud platform used for hosting and sharing software repositories.

Cowrie’s source code is hosted there.



Installation and Deployment Process



Step 1 Updating the System

The first step was updating Kali Linux:

sudo apt update && sudo apt upgrade -y



Deep Explanation of the Command

sudo

sudo means:

Super User DO

It temporarily gives administrator privileges required for system-level modifications.

Without sudo, package installations and updates may fail due to permission restrictions.



apt

APT means:

Advanced Package Tool

It is the package manager used in Debian based Linux systems.

APT helps users:

* install software
* remove software
* update packages
* manage dependencies


update

This refreshes package information from online repositories.

It does NOT install upgrades directly.

It simply updates the system’s software database.



upgrade

This installs newer versions of installed packages.

Benefits include:

* security patches
* bug fixes
* improved stability



-y

Automatically answers “yes” to installation prompts.

This allows automated installation without manual confirmation.



Why Updating Was Important

Updating ensured:

* latest package compatibility
* reduced software vulnerabilities
* stable dependency installation
* proper Cowrie deployment

Outdated systems can create compatibility issues and security risks.



Step 2 Installing Dependencies

Command used:

sudo apt install git python3 python3-pip python3-venv libssl-dev libffi-dev build-essential authbind -y



Deep Explanation of Dependencies

git

Used to download the Cowrie repository from GitHub.



python3

Installs Python 3 interpreter required to run Cowrie.



python3-pip

PIP is Python’s package manager.

It installs Python libraries and modules needed by Cowrie.

Example:

pip install package-name



python3-venv

Used to create virtual environments.

A virtual environment isolates project dependencies from the main operating system.

This prevents:

* dependency conflicts
* version mismatches
* system-wide package corruption



libssl-dev

Provides SSL/TLS encryption libraries.

SSL helps secure network communication.

Cowrie requires these cryptographic libraries for secure protocol handling.



libffi-dev

Provides Foreign Function Interface libraries.

These help Python communicate with lower level system libraries.



build-essential

Installs core Linux development tools including:

* GCC compiler
* make utility
* build libraries

Some Python packages require compilation during installation.



authbind

Allows non-root applications to bind to privileged ports like:

* port 22 for SSH

Normally, only root users can use ports below 1024.

Authbind safely bypasses that limitation.



Step 3 Cloning the Cowrie Repository

Command used:

git clone https://github.com/cowrie/cowrie.git



What This Command Does

git clone

Downloads a complete copy of the repository from GitHub.

This includes:

* source code
* scripts
* configuration files
* directories

The project folder is created locally on the system.



Step 4 Creating a Virtual Environment

Command used:

python3 -m venv cowrie-env



Deep Explanation

python3

Runs Python interpreter.



-m

Tells Python to run a module.



venv

Python module for creating virtual environments.



cowrie-env

Name of the virtual environment folder.



Why Virtual Environments Matter

Virtual environments isolate project dependencies.

Benefits include:

* cleaner system management
* dependency separation
* safer package installation
* easier troubleshooting

This is considered best practice in Python based cybersecurity projects.



Step 5 — Starting Cowrie

Command used:

bin/cowrie start



What Happens When Cowrie Starts

Cowrie begins:

* emulating an SSH service
* listening for incoming connections
* logging attacker activity
* simulating fake shell environments

Attackers connecting to the server believe it is a legitimate Linux machine.



How the Honeypot Works

When attackers scan the network and find the open SSH service:

1. They attempt login attacks
2. Cowrie accepts fake credentials
3. Attackers gain access to a simulated shell
4. Every action is logged
5. Commands are monitored
6. Download attempts are captured

The attacker thinks the system is real, while the defender safely observes.


Common Attacker Commands Observed

Attackers often execute reconnaissance commands such as:

ls
pwd
whoami
uname -a



Meaning of These Commands

ls

Lists files and folders.

Used to inspect the system.



pwd

Displays current directory location.



whoami

Shows current logged in username.

Used to identify privilege level.



uname -a

Displays operating system and kernel information.

Attackers use this for system reconnaissance.



Step 6 — Monitoring Logs

Command used:

tail -f var/log/cowrie/cowrie.log



Deep Explanation

tail

Displays the last lines of a file.



-f

Means:

Follow continuously

The log updates in real time as new events occur.



What the Logs Contain

Cowrie logs include:

* attacker IP addresses
* usernames entered
* passwords attempted
* executed commands
* session timestamps
* malware download attempts

These logs are extremely useful for cybersecurity analysis.



Security Considerations

This project was deployed only in a controlled lab environment for educational purposes.

Important considerations include:

* avoiding deployment on production systems
* preventing unauthorized access to real infrastructure
* isolating the honeypot from sensitive networks
* monitoring outbound attacker activity

Honeypots should be carefully controlled to prevent misuse.



Skills Demonstrated in the Project

This project demonstrated practical skills in:

* Linux administration
* cybersecurity monitoring
* network analysis
* SSH security
* Python environment setup
* GitHub repository management
* log analysis
* attacker behavior analysis



Challenges Encountered

Some common issues during deployment included:

* dependency installation errors
* permission issues
* Python version conflicts
* port binding problems
* virtual environment configuration

These challenges improved troubleshooting and Linux command line skills.



Educational Value of the Project

This project provided hands on cybersecurity experience rather than only theoretical learning.

It demonstrated how attackers:

* probe systems
* attempt credential attacks
* gather system information
* interact with Linux environments

The project also improved understanding of defensive monitoring and threat intelligence collection.



Conclusion

The Cowrie SSH honeypot project successfully demonstrated the deployment and operation of a honeypot environment using Kali Linux.

Through this project, practical knowledge was gained in:

* Linux system administration
* honeypot deployment
* SSH monitoring
* cybersecurity analysis
* log investigation
* attacker behavior observation

The project highlighted the importance of proactive cybersecurity monitoring and showed how honeypots can provide valuable insight into real world attack techniques while safely isolating malicious activity in a controlled environment.