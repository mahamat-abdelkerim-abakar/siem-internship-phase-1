
---

#### **Reflection Questions**  
```markdown
## 💡 Reflection Questions  

 1. Role of SIEM in modern cybersecurity  
SIEMs provide centralized visibility into security events across hybrid environments, enabling:  
- Real-time threat detection via correlation rules  
- Compliance auditing (GDPR, HIPAA)  
- Automated incident response workflows  

 2. Lab setup challenges  
- Network Segmentation: VMs initially couldn't communicate until switching to bridged networking.  
- Winlogbeat SSL Errors: Resolved by disabling SSL verification in test environment (`ssl.verification_mode: none`).  

3. Sysmon vs. Windows Security Logs  
| **Feature**          | **Sysmon**                          | **Windows Logs**               |  
|----------------------|-------------------------------------|--------------------------------|  
| **Granularity**      | Process trees, file hashes          | Authentication events          |  
| **Event Volume**     | High (requires filtering)           | Lower                          |  
| **Key for Detection**| TTP-based threats (e.g., malware)   | Account compromise             |  

 4. Brute Force Log Indicators  
- Event ID 4625: `Status 0xC000006A` (wrong password) with repeated `SubjectUserName`  
- Pattern: >5 attempts/minute from single IP  

5. Detecting After-Hours Logins  
```kql
event.code:4624 AND user.name: "Administrator" 
AND NOT (@timestamp >= "09:00:00" AND @timestamp <= "19:00:00")



6. Tracking RDP Lateral Movement
Key Event: 4624 with LogonType 10 (RDP)

Suspicion Indicators:

Source IP not in allowed subnets

Preceded by failed attempts (4625)

7. Log Tampering Risks & Detection
Risk: Attackers erase evidence of compromise

Detection: Sysmon Event ID 1 for wevtutil.exe or auditpol.exe with suspicious args

8. Lab Improvements
Add Linux VM for multi-OS detection

Implement firewall (pfSense) for network-level alerts

Enable Elastic Security's prebuilt rules

9. Real-World Relevance
Interview Talking Points:

"Built SIEM lab detecting 5 MITRE ATT&CK techniques, reducing false positives by 70% through threshold tuning"

Job Skills: Log analysis, alert triage, KQL/Python automation

10. Key Takeaway
Defense-in-Depth: SIEM is one layer - combine with endpoint protection, network monitoring, and user training for robust security.

