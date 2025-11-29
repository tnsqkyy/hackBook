# Wireshark

> "The packets never lie."

---

## 🧐 What it is

**Wireshark** is the world's foremost and widely-used network protocol analyzer. It lets you see what's happening on your network at a microscopic level. It is the de facto (and often de jure) standard across many commercial and non-profit enterprises, government agencies, and educational institutions.

---

## 🧠 Why it Matters

In pentesting, visibility is everything. Wireshark provides the ground truth of network communications. You can't trust what a machine *says* it's doing; you can only trust the packets it actually sends.

*   **Debugging:** Find out why network applications are not working.
*   **Security Analysis:** Detect suspicious network activity, analyze malware traffic, and identify intrusion attempts.
*   **Protocol Learning:** Understand how protocols like TCP/IP, DNS, and HTTP actually work by observing them in action.

---

## ⚙️ Internal Mechanics: How Wireshark Captures

Wireshark itself doesn't capture packets; it uses a capture library to do so.

1.  **Capture Library:** On Linux/macOS, it uses `libpcap`. On Windows, it uses `Npcap` (formerly `WinPcap`).
2.  **Promiscuous Mode:** The network interface card (NIC) is put into promiscuous mode. Normally, a NIC ignores all traffic that isn't addressed to its MAC address. In promiscuous mode, it grabs every packet it sees on the wire.
3.  **Packet Buffering:** The capture library copies these packets into a buffer in the kernel.
4.  **Hand-off to Wireshark:** Wireshark pulls packets from this buffer, dissects them according to its vast library of protocol dissectors, and displays them in a human-readable format.

---

## 🕵️ Real Attacker Use-Cases

*   **Credential Sniffing:** On an unencrypted network (e.g., open Wi-Fi), an attacker can capture login credentials sent in cleartext by protocols like FTP, Telnet, or old HTTP sites.
*   **Analyzing Malware C2 Traffic:** Capture traffic from a sandboxed machine infected with malware to understand its Command & Control (C2) communication patterns, heartbeat, and data exfiltration methods.
*   **Session Hijacking:** By capturing session cookies sent over unencrypted HTTP, an attacker can impersonate a legitimate user.
*   **VoIP Eavesdropping:** Capture and reconstruct RTP streams to listen to VoIP phone calls.

---

## 📊 Practical Display Filters (The "Commands" of Wireshark)

The filter bar is the most powerful feature in Wireshark. Here are concrete examples you can use to find exactly what you're looking for.

| Goal                                       | Filter Example                                     |
| ------------------------------------------ | -------------------------------------------------- |
| **See all traffic from/to an IP**          | `ip.addr == 8.8.8.8`                               |
| **See traffic from a source IP**           | `ip.src == 192.168.1.104`                          |
| **See traffic to a destination IP**        | `ip.dst == 1.1.1.1`                                |
| **Filter for specific protocols**          | `http` or `dns` or `smb` or `ftp`                  |
| **Find traffic on a specific port**        | `tcp.port == 443` or `udp.port == 53`              |
| **Find HTTP POST requests (often logins)** | `http.request.method == "POST"`                    |
| **Find DNS queries containing a name**     | `dns.qry.name contains "google"`                   |
| **Find packets with a specific string**    | `tcp contains "password"`                          |
| **Isolate problematic TCP packets**        | `tcp.flags.reset == 1` or `tcp.analysis.retransmission` |
| **Combine filters (AND / OR)**             | `ip.addr == 192.168.1.1 and http`                  |
|                                            | `dns or icmp`                                      |

