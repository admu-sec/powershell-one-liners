# Security

One-liners for security and permissions.

## Commands

| Description | Command |
| :--- | :--- |
| **Generate random password** | `-join ((33..126) | Get-Random -Count 16 | % {[char]$_})` |
| **Check user privileges** | `[Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()` |
| **List local users** | `Get-LocalUser | Select-Object Name, Enabled, LastLogon` |
| **List local admins** | `Get-LocalGroupMember -Group "Administrators"` |
| **Check file permissions** | `Get-Acl C:\path\to\file | Format-List` |
| **Lock computer** | `rundll32.exe user32.dll,LockWorkStation` |
| **List active firewall rules** | `Get-NetFirewallRule | Where-Object Enabled -eq True | Select-Object DisplayName, Direction, Action` |
| **List listening ports & PIDs** | `Get-NetTCPConnection -State Listen | Select-Object LocalAddress, LocalPort, OwningProcess` |
| **Find unsigned auto-start services** | `Get-WmiObject win32_service | Where-Object {$_.StartMode -eq "Auto" -and $_.PathName -notlike "*Microsoft*"} | Select-Object Name, PathName` |
| **Check execution policy (all scopes)** | `Get-ExecutionPolicy -List` |
| **Find files in System32 modified < 24h** | `Get-ChildItem C:\Windows\System32 -File | Where-Object {$_.LastWriteTime -gt (Get-Date).AddDays(-1)}` |
| **Find processes without a Window title** | `Get-Process | Where-Object {$_.MainWindowTitle -eq ""} | Select-Object ProcessName, Id` |
| **Search Event Log for failed logins** | `Get-EventLog -LogName Security -InstanceId 4625 -Newest 10` |
| **Find hidden files in C:** | `Get-ChildItem -Path C:\ -Recurse -Hidden -File -ErrorAction SilentlyContinue` |
| **List scheduled tasks (Ready)** | `Get-ScheduledTask | Where-Object {$_.State -ne "Disabled"} | Select-Object TaskName, TaskPath` |
