Core Scenarios & Technical Execution
1. Layer 1–4 Network Stack Diagnostics
Physical & Data Link (Layers 1 & 2): Diagnosed link flap issues, verified physical NIC status, and validated ARP table mappings (arp -a) to resolve IP conflict flags.

Network Layer (Layer 3): Isolated gateway routing drops and DHCP lease exhaustion using ipconfig /all, ping -t, and tracert.

Transport Layer (Layer 4): Verified open socket communication between client endpoints and backend database services using PowerShell:

SQL Server Port Check: Test-NetConnection 192.168.10.50 -Port 1433

SYSPRO Service Check: Test-NetConnection 192.168.10.50 -Port 3000

2. DNS & TCP/IP Stack Remediation
Hostname Resolution: Verified DNS A-record mappings using nslookup and resolved client caching failures using ipconfig /flushdns.

Socket Stack Resets: Executed full TCP/IP socket rebuilds for isolated workstations encountering corrupt network profiles:

```powershell
  netsh winsock reset
  netsh int ip reset
  ipconfig /release
  ipconfig /renew
3. SYSPRO ERP & SQL Database Administration
ODBC / DSN Configuration: Configured 32-bit and 64-bit System DSN drivers using SQL Server Native Client to establish persistent client-to-database connections.

SQL Session Triage: Executed read-only diagnostic queries in SQL Server Management Studio (SSMS) to clear locked SYSPRO operator sessions:

Check Active Connections: EXEC sp_who2

Identify Blocked Sessions: SELECT * FROM sys.sysprocesses WHERE blocked > 0

INI File Configuration: Re-pointed client-side syspro.ini configuration paths directly to host IPs when netBIOS/DNS resolution failed across VLAN boundaries.

4. Remote Support Operations (TeamViewer & RDP)
Unattended Access Setup: Managed remote user sessions using TeamViewer and RDP (MSTSC) for silent software deployments and background CLI troubleshooting.

Firewall Port Verification: Confirmed outbound firewall rules allowed pass-through traffic over TeamViewer communication ports (TCP/UDP 5938 and 443).

Technical Skills Summary
Networking Tools: TCP/IP, Subnetting, DNS, DHCP, ping, tracert, nslookup, netstat, Test-NetConnection.

ERP & Database Systems: SYSPRO ERP, Microsoft SQL Server, SSMS, System DSN / ODBC Management.

Remote Admin & OS: TeamViewer, RDP, Windows PowerShell, CMD, Services.msc, Windows Registry.
