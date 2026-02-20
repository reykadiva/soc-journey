# SOC Journey Log Englih Version

---

## Day 1 - Ubuntu Installation & Linux Permission Fundamentals
Date: 2026-02-20  
Duration: ~3-4 hours  
Focus Area: Linux Basics & Privilege Management  

---

### 🎯 Objective
- Install Ubuntu in VirtualBox
- Understand Linux file system structure
- Learn file and directory permissions
- Understand SetUID and privilege escalation concept

---

### 🛠 Practical Activities

#### 1. Virtual Lab Setup
- Installed VirtualBox
- Created Ubuntu-SOC-Lab VM (4GB RAM, 2 CPU, 40GB disk)
- Installed Ubuntu Desktop LTS manually (interactive mode)
- Updated system packages
- Installed basic tools (curl, wget, git, net-tools, htop, vim) (by gpt ask)

---

#### 2. Linux File System Exploration
Commands practiced:

- ```bash
- pwd 
- ls
- ls -la /
- cd ~
- touch testfile
- ls -l testfile

Learned 
- / is the root directory
- /home is equivalent to C:\Users\ in Windows
- Directory permissions control deletion capability

---

#### 3. Linux Permission Model

Studied permission format:
-rw-r--r--

Understood:
First character indicates file type
Owner / Group / Others structure
r = read
w = write
x = execute

Key Insight:
To delete a file, write permission is required on the directory, not the file. 

---

#### 4. SetUID Concept

Explored:
ls -l /usr/bin/passwd
find / -perm -4000 2>/dev/null

Learned:
- s in permission indicates SetUID
- SetUID makes a program run with the file owner's effective UID
- /usr/bin/passwd runs with root privilege
- User does not become root; the process runs as root

Understood difference between:
Real UID (Real UID status)
Effective UID (The UID that work now)

---

#### 5. Privilege Escalation Awareness

Compared risk levels of:
- 777 permission
- SetUID root
- SetUID root + world writable

Key Understanding:
- SetUID root binaries are high risk if vulnerable
- World-writable root files can allow privilege escalation through tampering
- Combination of both is critical misconfiguration

---

### 🔎 Key Security Insights Today

- Linux security is heavily permission-based
- Privilege separation is fundamental
- SetUID misconfiguration can lead to root compromise
- Effective UID determines actual process privilege
- Not all privilege escalation involves sudo

---

### ❓ Confusions / Open Questions

- How does Linux internally switch between real UID and effective UID?
- How are SetUID vulnerabilities exploited in real-world attacks?

---

### 📈 Progress Reflection

- Today was foundational but intensive.
- Moved from basic Linux commands to understanding privilege mechanics and
escalation risks.
- Began thinking from a defender perspective rather than just user perspective.

---

### 🗓 Plan for Tomorrow

- Deep dive into sudo and /etc/sudoers
- Learn about Linux logging (/var/log/auth.log)
- Begin basic log analysis