# Detection Use Case: Brute Force Login Detection  
_MITRE ATT&CK: [T1110](https://attack.mitre.org/techniques/T1110/)_  

## 🎯 Scenario Description  
Simulated brute-force attack on Windows RDP using Hydra, followed by a successful login.  

## 🛠️ Tools Used  
- **SIEM**: ELK Stack  
- **Log Sources**: Windows Security Logs (Event ID 4625, 4624)  
- **Attack Tool**: Hydra  

## 🔍 Detection Logic  
```kql
event.code:4625 | 
STATS COUNT() AS failed_attempts BY source.ip, user.name | 
WHERE failed_attempts > 5
