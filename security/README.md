# Security

One-liners for security-related tasks.

---

## Check for open ports
```powershell
Get-NetTCPConnection | Where-Object State -eq 'Listen' | Select-Object LocalPort, @{n='Process';e={(Get-Process -Id $_.OwningProcess).Name}} | Sort-Object LocalPort
```

## Get failed login attempts
```powershell
Get-WinEvent -LogName Security | Where-Object { $_.Id -eq 4625 } | Select-Object TimeCreated, Message | Select-Object -First 20
```

## Get successful logins
```powershell
Get-WinEvent -LogName Security | Where-Object { $_.Id -eq 4624 } | Select-Object TimeCreated, Message | Select-Object -First 20
```

## Get account lockouts
```powershell
Get-WinEvent -LogName Security | Where-Object { $_.Id -eq 4740 } | Select-Object TimeCreated, Message
```

## Check Windows Firewall status
```powershell
Get-NetFirewallProfile | Select-Object Name, Enabled
```

## List firewall rules
```powershell
Get-NetFirewallRule | Where-Object Enabled -eq 'True' | Select-Object Name, Direction, Action | Sort-Object Direction
```

## Check for local admins
```powershell
Get-LocalGroupMember -Group "Administrators" | Select-Object Name, ObjectClass
```

## Get recently created local users
```powershell
Get-LocalUser | Select-Object Name, Enabled, LastLogon, PasswordLastSet | Sort-Object PasswordLastSet -Descending
```

## Check AutoRun registry keys
```powershell
Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" | Select-Object *
```

## Get Windows Defender status
```powershell
Get-MpComputerStatus | Select-Object AMServiceEnabled, AntispywareEnabled, AntivirusEnabled, RealTimeProtectionEnabled
```
