#  Task 5: Network Traffic Capture and Analysis (Wireshark)

## Task Objective
The objective was to gain practical experience with **packet analysis** by capturing live network traffic and identifying the fundamental protocols, demonstrating an understanding of how data moves across a network.

## 🛠 Tool Used
* **Wireshark:** Used to capture, filter, and analyze packets on the local network interface.

## ⚙️ Capture Details

| Setting | Value |
| :--- | :--- |
| **Interface Captured** | [Insert your active interface, e.g., `eth0` or `wlan0`] |
| **Traffic Generated** | Web Browsing (HTTP/HTTPS), DNS Lookups, and `ping` commands (ICMP). |
| **Capture Duration** | [Insert your actual capture time, e.g., 60 seconds] |
| **Deliverable** | `task5_capture.pcap` (The raw packet capture file) |

---

## 🔎 Protocol Analysis Report

Using Wireshark's Display Filters, the following key protocols were identified and analyzed in the captured traffic:

### 1. ICMP (Internet Control Message Protocol)
* **Filter Used:** `icmp`
* **Observation:** Packets were captured during the execution of a `ping 8.8.8.8` command.
* **Function:** Used for diagnostic and error messages. The packets observed were **Echo Request** and **Echo Reply**, confirming connectivity to the target server.

### 2. DNS (Domain Name System)
* **Filter Used:** `dns`
* **Observation:** Numerous **Standard Query** requests were seen, typically originating from the local machine and sent to the router/ISP DNS server.
* **Function:** Translates human-readable domain names (e.g., `aihumanize.io`) into routable IP addresses.

### 3. TCP (Transmission Control Protocol)
* **Filter Used:** `tcp`
* **Observation:** The protocol was analyzed during the initial phase of web browsing. The packets clearly showed the **Three-Way Handshake**  (SYN, SYN-ACK, ACK) sequence required to establish a reliable connection before data transfer (like HTTP or HTTPS) begins.
* **Function:** Provides reliable, ordered, and error-checked delivery of a stream of bytes between applications.

### 4. ARP (Address Resolution Protocol)
* **Filter Used:** `arp`
* **Observation:** Packets were seen periodically asking, "Who has IP address X.X.X.X? Tell Y.Y.Y.Y."
* **Function:** Maps a known IP address to its corresponding physical MAC address on the local network segment, which is necessary for data to be delivered correctly at the Data Link Layer.

---

## 🎓 Key Findings

* **Layered Operation:** The capture clearly illustrated the layered nature of networking (OSI Model), where higher-level protocols like DNS and HTTP rely on underlying transport protocols like TCP and IP.
* **Protocol Visibility:** Simple filters can immediately isolate specific traffic types, which is essential for troubleshooting and security monitoring.
* **Unencrypted Data Risk:** [If you found HTTP traffic]: The packets demonstrated that when using unencrypted **HTTP**, all data, including URLs and content, is transmitted in **plaintext** and fully visible within Wireshark. This highlights the importance of using HTTPS.
