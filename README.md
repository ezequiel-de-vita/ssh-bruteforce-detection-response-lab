# SSH Unauthorized Access Detection & Response Lab

## Overview
This project simulates unauthorized SSH login attempts against a Windows host
and demonstrates detection, investigation, and mitigation from a blue team perspective.

## Scenario
A Windows system exposed to SSH receives multiple failed authentication attempts
from an internal host simulating an attacker.

## Tools Used
- Kali Linux
- Windows 10
- OpenSSH Server
- Wireshark
- Windows Event Viewer
- Windows Firewall (PowerShell)

## Detection
- Windows Security Event ID 4625
- SSH operational logs identifying source IP

## Mitigation
- Firewall rule blocking malicious source IP
- Verification of blocked traffic

## Outcome
Unauthorized access attempts were detected, investigated, and successfully mitigated.
