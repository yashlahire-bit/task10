# task10-EL-
🛠 Tools Used
 Primary Tool: UFW (Uncomplicated Firewall) on Ubuntu/Linux
 Testing Tools: nmap (for port scanning), curl (connectivity testing) 
 Logging: /var/log/ufw.log 
🚀 Configuration Steps
  1. Hardening the Baseline
     The first step was to ensure a secure posture by denying all unsolicited incoming traffic.
     Bash
     sudo ufw default deny incoming
     sudo ufw default allow outgoing
2. Allowing Essential Services
   Specific ports were opened to allow for remote management and web traffic.
     SSH (Port 22): sudo ufw allow 22/tcp
     HTTP (Port 80): sudo ufw allow 80/tcp
     HTTPS (Port 443): sudo ufw allow 443/tcp
3. Mitigating Attacks
   To simulate blocking a malicious actor identified in the logs, a specific IP block was implemented:
   Bash
     sudo ufw deny from 192.168.1.100
📊 Firewall Rules DocumentationPriorityActionPortProtocolPurpose1DENYALLALLBlocked Malicious IP (192.168.1.100)2ALLOW22TCPRemote SSH Access3ALLOW80TCPWeb Traffic (HTTP)4ALLOW443TCPSecure Web Traffic (HTTPS)5DENYALLALLDefault Incoming Deny🔍 Testing & VerificationTo verify the configuration, I performed an external port scan using nmap:Result: Only ports 22, 80, and 443 showed as open. All other ports appeared as filtered, confirming the firewall was successfully dropping unauthorized packets.
