# SIEM Internship - Phase 1: Foundation Setup  
**Lab Implementation for Suspicious Activity Detection**  

## 🔧 Lab Architecture  
- **Attacker VM**: Kali Linux 
- **Target VM**: Windows 10 
- **SIEM**: ELK Stack

## 🛠️ Tools Used  
| Category       | Tools                          |  
|----------------|--------------------------------|  
| SIEM           | ELK Stack (Elasticsearch, Kibana)|  
| Log Forwarder  | Winlogbeat                     |  
| Monitoring     | Sysmon                         |  
| Attack Simulation | Nmap, Hydra, Windows RDP     |  

## 📂 Use Case Reports  
1. [Brute Force Login Detection](writeups/use-case-1-brute-force.md)  
2. [After-Hours Admin Login](writeups/use-case-2-after-hours.md)  
3. [RDP Lateral Movement](writeups/use-case-3-rdp-lateral.md)  
4. [Log Tampering Detection](writeups/use-case-4-log-tampering.md)  
5. [Hidden User Account Creation](writeups/use-case-5-hidden-user.md)  

## 💡 Reflection Questions  
1. **Role of SIEM**: Centralized log analysis for real-time threat detection...  
2. **Lab Challenges**: Network misconfigurations between VMs...  
> [Full Answers Here](writeups/reflection-questions.md)
