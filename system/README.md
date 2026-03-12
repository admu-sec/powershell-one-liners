# System

One-liners for system-related tasks.

---

## Get system information
```powershell
Get-ComputerInfo | Select-Object CsName, OsName, OsVersion, CsProcessors, CsTotalPhysicalMemory
```

## Get uptime
```powershell
(Get-Date) - (gcim Win32_OperatingSystem).LastBootUpTime
```

## Get disk usage
```powershell
Get-PSDrive -PSProvider FileSystem | Select-Object Name, @{n='Used(GB)';e={[math]::Round($_.Used/1GB,2)}}, @{n='Free(GB)';e={[math]::Round($_.Free/1GB,2)}}
```

## Get running services
```powershell
Get-Service | Where-Object Status -eq 'Running' | Select-Object Name, DisplayName
```

## Get installed software
```powershell
Get-ItemProperty HKLM:\Software\Microsoft\Windows\CurrentVersion\Uninstall\* | Select-Object DisplayName, DisplayVersion, Publisher
```

## Get environment variables
```powershell
Get-ChildItem Env: | Select-Object Name, Value
```

## Get scheduled tasks
```powershell
Get-ScheduledTask | Where-Object State -eq 'Ready' | Select-Object TaskName, TaskPath
```

## Get Windows version
```powershell
(Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion").ProductName
```

## Get CPU usage
```powershell
Get-Counter '\Processor(_Total)\% Processor Time' | Select-Object -ExpandProperty CounterSamples | Select-Object CookedValue
```

## Get memory usage
```powershell
Get-CimInstance Win32_OperatingSystem | Select-Object @{n='TotalRAM(GB)';e={[math]::Round($_.TotalVisibleMemorySize/1MB,2)}}, @{n='FreeRAM(GB)';e={[math]::Round($_.FreePhysicalMemory/1MB,2)}}
```
