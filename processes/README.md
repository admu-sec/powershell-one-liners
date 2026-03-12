# Processes

One-liners for process-related tasks.

---

## Get all running processes
```powershell
Get-Process | Select-Object Name, Id, CPU, @{n='Memory(MB)';e={[math]::Round($_.WorkingSet/1MB,2)}} | Sort-Object 'Memory(MB)' -Descending
```

## Get process by name
```powershell
Get-Process -Name "chrome" | Select-Object Name, Id, CPU, @{n='Memory(MB)';e={[math]::Round($_.WorkingSet/1MB,2)}}
```

## Kill process by name
```powershell
Stop-Process -Name "processname" -Force
```

## Kill process by ID
```powershell
Stop-Process -Id 1234 -Force
```

## Get process and its parent
```powershell
Get-CimInstance Win32_Process | Select-Object Name, ProcessId, ParentProcessId, CommandLine | Sort-Object ProcessId
```

## Get processes with network connections
```powershell
Get-NetTCPConnection | Where-Object State -eq 'Established' | Select-Object LocalPort, RemoteAddress, RemotePort, @{n='Process';e={(Get-Process -Id $_.OwningProcess).Name}}
```

## Get top 10 CPU-consuming processes
```powershell
Get-Process | Sort-Object CPU -Descending | Select-Object -First 10 Name, Id, CPU
```

## Get top 10 memory-consuming processes
```powershell
Get-Process | Sort-Object WorkingSet -Descending | Select-Object -First 10 Name, Id, @{n='Memory(MB)';e={[math]::Round($_.WorkingSet/1MB,2)}}
```

## Check if a specific process is running
```powershell
if (Get-Process -Name "processname" -ErrorAction SilentlyContinue) { "Running" } else { "Not running" }
```

## Get process start time
```powershell
Get-Process | Select-Object Name, Id, StartTime | Sort-Object StartTime -Descending
```
