# LUCIFERLAMO-Network-Ninja-Firewall
Network Topology  
- pfSense :192.168.1.1/24.
- Kali linux: 192.168.1.100/24.
- Metaspolitable2: 192.168.1.101/24


# Defense 1: Port Scan Mitigation

I implemented a firewall rule in pfSense to block and log TCP SYN scans.

Before: The nmap scan successfully identified numerous open ports on the victim machine.
<img width="711" height="668" alt="portscan_before" src="https://github.com/user-attachments/assets/ad86fbbd-31f4-4f43-bd45-73f44ad0caa2" />



After: The same scan was blocked by the new firewall rule. The logs clearly show the detection and block action.
<img width="711" height="668" alt="portscan_before" src="https://github.com/user-attachments/assets/31e92267-0546-4138-a348-d02e00f2385e" />
<img width="573" height="225" alt="Screenshot 2025-09-10 204223" src="https://github.com/user-attachments/assets/c4a36ad8-af76-4e4f-8b01-2014eef62f03" />

---

## Defense 2: SYN Flood / DDoS Detection

I installed and configured the Suricata Intrusion Detection System (IDS) on pfSense to perform deeper packet inspection. I wrote a custom rule to detect a potential SYN flood attack by counting a high number of SYN packets from a single source over a short period.

Evidence: The screenshot below shows the Suricata alerts that were triggered immediately after launching a SYN flood attack with `hping3` from the Kali machine.

<img width="885" height="825" alt="synflood_detection" src="https://github.com/user-attachments/assets/ab6c200b-d431-41ad-92b2-8bc71787c88c" />

---

 Defense 3: DNS Tunneling Detection & Segmentation

For the final challenge, the network was segmented into a `Trusted Zone` (OPT1) and an `Untrusted Zone` (LAN). Firewall rules were created to strictly control traffic between them. An advanced Suricata rule was written to inspect allowed DNS traffic and detect signs of DNS tunneling by identifying unusually long query labels.

**Evidence:** The screenshot below shows the custom Suricata alert that was triggered after simulating a DNS tunneling attack from the Untrusted Zone.

<img width="820" height="490" alt="dns_tunnel_alert" src="https://github.com/user-attachments/assets/679dd241-ad36-47db-8336-00f2beb3b763" />


---
