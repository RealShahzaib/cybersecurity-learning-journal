# 📨 Moniker Link (CVE-2024-21413) – Outlook NTLM Credential Leak

## 🧠 Overview

In this lab, I learned about a critical Microsoft Outlook vulnerability:

**CVE-2024-21413**, also known as the **Moniker Link vulnerability**.

This vulnerability allows attackers to bypass Outlook’s Protected View mechanism by sending a specially crafted hyperlink. When clicked, it can cause the victim’s system to leak NTLM credentials.

---

## ⚠️ What the Vulnerability Does

The attack works as follows:

- An attacker sends an email containing a malicious **Moniker Link**
- When the victim clicks the link, Outlook attempts to access a remote file
- This forces the victim’s machine to authenticate over SMB
- The victim’s **NetNTLM hash** is sent to the attacker

Instead of directly executing malicious code, the vulnerability abuses Outlook’s handling of specific hyperlinks to trigger credential leakage.

---

## 🔬 How the Exploit Works

The crafted link:

- Uses special characters
- Instructs Outlook to attempt loading a file from a network share
- Bypasses Protected View restrictions

Once clicked:

- Outlook tries to access an attacker-controlled machine
- SMB authentication occurs
- The attacker captures the NetNTLM hash

---

## 🛠️ Practical Lab – Proof of Concept

During the lab, I:

1. Crafted a malicious email containing a Moniker link  
2. Sent it to the victim machine  
3. Used **Responder** on the attacker machine  
4. Captured the victim’s NetNTLM hash  

I also analyzed the SMB authentication traffic using **Wireshark**, where I observed:

- SMB request packets  
- NTLM negotiation process  
- Truncated NTLM hash in the capture  

This helped me understand how credential leakage occurs at the protocol level.

---

## 🛡️ Mitigation & Best Practices

To prevent exploitation:

- Keep Microsoft Office/Outlook updated  
- Avoid clicking unknown or suspicious links  
- Preview links before clicking  
- Forward suspicious emails to the security team  
- Restrict outbound NTLM authentication where possible  

This lab reinforced how simple user interaction can lead to serious credential compromise.

---

# 💣 Metasploit – Introduction to the Exploitation Framework

## 🧠 What is Metasploit?

Metasploit is one of the most widely used exploitation frameworks in cybersecurity.

It supports multiple phases of penetration testing:

- Information gathering  
- Scanning  
- Exploitation  
- Post-exploitation  
- Vulnerability research  

---

## 🧩 Versions of Metasploit

### Metasploit Pro
- Commercial version  
- GUI-based  
- Automation-focused  

### Metasploit Framework
- Open-source  
- Command-line based  
- Commonly used in Kali Linux  

In this lab, I worked with **msfconsole** (Metasploit Framework CLI).

---

## 🏗️ Core Components

### msfconsole
The main CLI interface used to interact with Metasploit.

### Modules
Modules perform specific functions such as:

- Exploits  
- Scanners  
- Payloads  
- Auxiliary modules  

### Standalone Tools
Examples include:

- `msfvenom`  
- `pattern_create`  
- `pattern_offset`  

These tools assist in exploit development and payload generation.

---

## 📚 Key Concepts

### Vulnerability
A flaw in system design, code, or logic.

### Exploit
Code that takes advantage of a vulnerability.

### Payload
The code executed after successful exploitation (e.g., reverse shell, Meterpreter).

An exploit gains access — a payload gives control.

---

## 🔧 Module & Payload Types

### Auxiliary
Used for scanning, brute forcing, and information gathering.

### Encoders
Modify payloads to evade detection.

### NOPs
Used in buffer overflow exploitation.

### Payload Categories

- **Adapters** – Convert payloads into different formats  
- **Singles** – Self-contained payloads  
- **Stagers** – Establish connection to the target  
- **Stages** – Downloaded by stagers for extended functionality  

Understanding this structure helped me see how real-world exploitation chains are built.

---

# 🚀 Metasploit Exploitation – Practical Use

After learning the basics, I practiced:

- Scanning target systems  
- Using the Metasploit database feature  
- Conducting vulnerability scans  
- Exploiting vulnerable services  
- Generating payloads with `msfvenom`  
- Obtaining a Meterpreter session  

This connected theory with real attack workflows.

---

# 🕵️ Meterpreter – Post Exploitation & System Control

After exploitation, I worked with **Meterpreter**, a powerful post-exploitation payload.

---

## 🛠️ Useful Commands Practiced

- `sysinfo`  
- `shell`  
- `search`  
- `hashdump`  
- `migrate`  

---

## 🔌 Extensions & Credential Harvesting

I loaded extensions like:
`load kiwi`


The **Kiwi** extension allows:

- Dumping NTLM hashes  
- Extracting credentials  
- Advanced post-exploitation actions  

---

## 🧪 Practical Tasks Performed

In the lab, I simulated:

- Initial compromise over SMB  
- Retrieved computer name and domain using `sysinfo`  
- Used `net share` inside a shell to view shared resources  
- Dumped NTLM hashes using Kiwi  
- Cracked hashes using Hashcat  
- Searched for sensitive files  
- Viewed file contents  

This demonstrated how attackers move from:

Initial access → Credential harvesting → Potential lateral movement

---

# 🧠 Final Reflection

These labs significantly improved my understanding of:

- Real-world credential leaks (Moniker Link)  
- Exploitation frameworks (Metasploit)  
- Post-exploitation techniques (Meterpreter)  
- Credential dumping and offline hash cracking  

Performing hands-on tasks helped me develop an attacker mindset, which is essential for improving defensive strategies.

Understanding these techniques strengthens my ability to:

- Detect attacks  
- Respond to incidents  
- Harden systems  
- Improve password and authentication security  
