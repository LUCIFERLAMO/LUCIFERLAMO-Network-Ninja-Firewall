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

