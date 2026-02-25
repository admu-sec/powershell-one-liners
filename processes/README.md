# Processes

One-liners for managing processes.

## Commands

| Description | Command |
|-------------|---------|
| Top 10 CPU-hungry processes | `Get-Process | Sort-Object CPU -Descending | Select-Object -First 10 Name, CPU` |
| Top 10 memory-hungry processes | `Get-Process | Sort-Object WorkingSet -Descending | Select-Object -First 10 Name, @{n='RAM(MB)';e={[math]::Round($_.WorkingSet/1MB,2)}}` |
| Kill process by name | `Get-Process notepad | Stop-Process` |
| Kill process by ID | `Stop-Process -Id 1234` |
| Check if process is running | `Get-Process -Name "notepad" -ErrorAction SilentlyContinue` |
| Get process start time | `Get-Process | Select-Object Name, StartTime | Sort-Object StartTime` |
