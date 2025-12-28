# Incident Response Playbook  
## Unauthorized SSH Access Attempts

---

## 1. Purpose

This playbook describes the detection, investigation, and mitigation process
for unauthorized SSH authentication attempts against a Windows host.

The objective is to provide a clear, repeatable response workflow for
security incidents involving SSH brute-force or repeated failed logins.

---

## 2. Scenario Description

A Windows system running an SSH server receives multiple failed authentication
attempts from a remote host.

The activity indicates a possible unauthorized access attempt and requires
investigation and containment.

---

## 3. Environment

- **Attacker Simulation**: Kali Linux
- **Target System**: Windows 10 with OpenSSH Server enabled
- **Network**: Internal host-only network
- **Monitoring Tools**:
  - Windows Event Viewer
  - OpenSSH operational logs
  - Wireshark
- **Mitigation Tools**:
  - Windows Firewall
  - PowerShell

---

## 4. Detection

### 4.1 Indicators of Suspicious Activity

- Multiple failed SSH authentication attempts
- Repeated login failures within a short time frame
- Unknown or unauthorized user accounts

### 4.2 Log Sources

- **Windows Security Logs**
  - Event ID: `4625` (An account failed to log on)
- **OpenSSH Logs**
  - Messages indicating failed authentication attempts
  - Source IP address recorded in SSH logs

---

## 5. Investigation

### 5.1 Log Analysis

Steps performed:

1. Open **Event Viewer**
2. Navigate to: Windows Logs -> Security
3. Filter for: Event ID: 4625
4. Identify:
- Account name
- Logon failure reason
- Timestamp correlation

### 5.2 Source Identification

- SSH operational logs reveal:
- Source IP address
- Invalid username attempts
- Source port

Example indicator: Connection closed by invalid user from 192.168.56.101


---

## 6. Network Traffic Analysis

- Wireshark used to capture SSH traffic (TCP port 22)
- Observed:
  - Repeated TCP connection attempts
  - Failed authentication sequences
- Traffic correlated with timestamps from system logs

---

## 7. Mitigation

### 7.1 Immediate Containment

Block the identified malicious source IP using Windows Firewall.

### 7.2 Firewall Rule (PowerShell)

```powershell
New-NetFirewallRule `
  -DisplayName "Block SSH Unauthorized Source" `
  -Direction Inbound `
  -Protocol TCP `
  -LocalPort 22 `
  -RemoteAddress 192.168.56.101 `
  -Action Block

### 7.3 Verification
-Confirm firewall rule is active
-Attempt SSH connection from blocked IP
-Validate connection is denied

---

### 8. Post-Incident Actions
-Review SSH exposure and access policies
-Ensure strong authentication methods
-Monitor for additional suspicious activity
-Document incident and response actions

---

### 9. Outcome
The unauthorized SSH access attempts were successfully:
-Detected through log analysis
-Investigated using host and network evidence
-Mitigated via firewall enforcement
The system returnd to a secure operational state.

---

### 10. Lessons Learned
-Event correlation is critical for SSH incident detection
-Host logs and network traffic provide complementary visibility
-Simple firewall actions can effectively stop active threats
