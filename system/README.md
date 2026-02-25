# System

One-liners for system information and management.

## Commands

| Description | Command |
|-------------|---------|
| Get CPU usage | `(Get-WmiObject Win32_Processor).LoadPercentage` |
| Get RAM usage | `Get-WmiObject Win32_OperatingSystem | Select-Object @{n='FreeGB';e={[math]::Round($_.FreePhysicalMemory/1MB,2)}}, @{n='TotalGB';e={[math]::Round($_.TotalVisibleMemorySize/1MB,2)}}` |
| Get uptime | `(Get-Date) - (Get-CimInstance Win32_OperatingSystem).LastBootUpTime` |
| Get disk usage | `Get-PSDrive -PSProvider FileSystem | Select-Object Name, @{n='Used(GB)';e={[math]::Round($_.Used/1GB,2)}}, @{n='Free(GB)';e={[math]::Round($_.Free/1GB,2)}}` |
| Get battery status | `(Get-WmiObject Win32_Battery).EstimatedChargeRemaining` |
| Get Windows version | `(Get-WmiObject Win32_OperatingSystem).Caption` |
| Get installed RAM | `(Get-WmiObject Win32_ComputerSystem).TotalPhysicalMemory / 1GB` |
