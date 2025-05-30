
---

#### **Reflection Questions**  
```markdown
## 💡 Reflection Questions  

### 1. Role of SIEM in modern cybersecurity  
SIEMs provide centralized visibility into security events across hybrid environments, enabling:  
- Real-time threat detection via correlation rules  
- Compliance auditing (GDPR, HIPAA)  
- Automated incident response workflows  

### 2. Lab setup challenges  
- **Network Segmentation**: VMs initially couldn't communicate until switching to bridged networking.  
- **Winlogbeat SSL Errors**: Resolved by disabling SSL verification in test environment (`ssl.verification_mode: none`).  

### 3. Sysmon vs. Windows Security Logs  
| **Feature**          | **Sysmon**                          | **Windows Logs**               |  
|----------------------|-------------------------------------|--------------------------------|  
| **Granularity**      | Process trees, file hashes          | Authentication events          |  
| **Event Volume**     | High (requires filtering)           | Lower                          |  
| **Key for Detection**| TTP-based threats (e.g., malware)   | Account compromise             |  

### 4. Brute Force Log Indicators  
- **Event ID 4625**: `Status 0xC000006A` (wrong password) with repeated `SubjectUserName`  
- **Pattern**: >5 attempts/minute from single IP  

### 5. Detecting After-Hours Logins  
```kql
event.code:4624 AND user.name: "Administrator" 
AND NOT (@timestamp >= "09:00:00" AND @timestamp <= "19:00:00")
