# 🦈 Wireshark: The Basics – TryHackMe Writeup

## 🎯 Room Overview
This room introduced the fundamentals of Wireshark and how it is used as a network traffic analysis tool. The focus was on understanding packet analysis, protocol inspection, filtering, and navigation through PCAP files.

---

## 🧠 Key Concepts Learned

### 🔍 What Wireshark Actually Is
One of the first and most important things I learned is that Wireshark is **not an Intrusion Detection System (IDS)**.  
It is a packet analysis tool that captures and displays network traffic. The responsibility of identifying issues, anomalies, or suspicious activity lies with the analyst, not the tool itself.

This helped me understand that:
- Wireshark shows raw packets
- Analysis and interpretation depend on the user
- It is mainly used for troubleshooting, traffic analysis, and forensic investigations

---

## 🖥️ Wireshark Interface & GUI Understanding
I explored the main components of the Wireshark interface, including:
- Toolbar
- Display Filter Bar
- Capture Filters
- Packet List Pane
- Packet Details Pane
- Packet Bytes Pane

Understanding the GUI made navigation much easier while analyzing PCAP files.

---

## 🎨 Packet Coloring System
I learned about Wireshark’s coloring rules, which visually highlight packet behavior:
- 🔴 Red packets often indicate errors or suspicious activity
- 🟡 Yellow packets indicate warnings or notable traffic

This feature helps analysts quickly identify unusual traffic patterns during analysis.

---

## 🌐 Packet Dissection & Layer Analysis
A major learning point was packet dissection and how Wireshark breaks down packets into layers:
- Frame layer (Physical layer information)
- Data Link layer (MAC source and destination)
- Network layer (IP addresses)
- Transport layer (TCP/UDP details)
- Application layer (Protocols and payload data)

This helped me understand how data travels across the network stack and how each layer provides crucial forensic information.

---

## 📊 Important Packet Analysis Indicators
While analyzing packets, I learned to focus on key fields such as:
- Arrival time and timestamps
- TTL (Time To Live)
- Source and destination IP addresses
- TCP payload size
- Protocol types

These indicators are essential when investigating network behavior and potential anomalies.

---

## 🧭 Navigation & Packet Searching
Wireshark provides powerful navigation tools that improve efficiency during investigations:
- Go to specific packet numbers
- Find packets using strings, hex values, or filters
- Mark suspicious packets for later review
- Add comments to important packets

I also learned that marks are temporary (lost after restart), while comments remain saved in the capture file.

---

## 📦 Exporting Data & Objects
Another useful feature I explored was exporting:
- Selected packets for focused analysis
- Objects/files extracted from packet streams
- Exporting packet summaries with marks and comments

This is extremely helpful when isolating suspicious traffic for deeper investigation.

---

## 🔗 Stream Following (Very Useful Feature)
The “Follow Stream” feature (TCP/HTTP streams) was particularly interesting.  
It allows analysts to reconstruct communication between a client and a server:
- Red = Client traffic
- Blue = Server traffic

This made it easier to visualize full conversations within captured traffic, especially in protocols like HTTP and Telnet.

---

## ⏱️ Time Display Customization
Adjusting the time display format to date and time improved readability and made packet timeline analysis much more convenient during investigations.

---

## 🧪 Practical Task Experience (Flag Analysis)
The room included hands-on investigative tasks, which I found very engaging.  
One task required:
- Navigating to a specific packet
- Reading packet comments as hints
- Inspecting packet bytes
- Using MD5 hashing to retrieve the final flag

This exercise reinforced real-world analysis skills such as:
- Following investigative clues
- Deep packet inspection
- Logical analysis workflow

---

## 📌 Key Takeaways
- Wireshark is a traffic analysis tool, not an IDS
- Effective packet analysis depends on the analyst’s observation skills
- Packet dissection provides deep insight into network communication
- Filtering and stream following are critical for traffic investigation
- Proper navigation and exporting features significantly improve analysis efficiency

---

## 🚀 Personal Reflection
This room strengthened my foundational understanding of network traffic analysis and packet inspection. As someone aiming to pursue a SOC Analyst role, learning Wireshark is highly valuable since traffic monitoring, PCAP analysis, and anomaly detection are core responsibilities in defensive security.
