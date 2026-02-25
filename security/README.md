# Security

One-liners for security and permissions.

## Commands

| Description | Command |
|-------------|---------|
| Generate random password | `-join ((33..126) | Get-Random -Count 16 | % {[char]$_})` |
| Check user privileges | `[Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()` |
| List local users | `Get-LocalUser | Select-Object Name, Enabled, LastLogon` |
| List local admins | `Get-LocalGroupMember -Group "Administrators"` |
| Check file permissions | `Get-Acl C:\path\to\file | Format-List` |
| Lock computer | `rundll32.exe user32.dll,LockWorkStation` |
| List firewall rules | `Get-NetFirewallRule | Where-Object Enabled -eq True | Select-Object DisplayName, Direction, Action` |
