# Files

One-liners for file-related tasks.

---

## Find large files
```powershell
Get-ChildItem -Path C:\ -Recurse -ErrorAction SilentlyContinue | Where-Object { $_.Length -gt 100MB } | Select-Object FullName, @{n='Size(MB)';e={[math]::Round($_.Length/1MB,2)}} | Sort-Object 'Size(MB)' -Descending
```

## Find files modified in the last 24 hours
```powershell
Get-ChildItem -Path C:\ -Recurse -ErrorAction SilentlyContinue | Where-Object { $_.LastWriteTime -gt (Get-Date).AddHours(-24) } | Select-Object FullName, LastWriteTime
```

## Get file hash
```powershell
Get-FileHash -Path C:\path\to\file -Algorithm SHA256
```

## Search for text in files
```powershell
Select-String -Path C:\path\*.txt -Pattern "searchterm"
```

## Get folder size
```powershell
Get-ChildItem -Path C:\path -Recurse | Measure-Object -Property Length -Sum | Select-Object @{n='Size(GB)';e={[math]::Round($_.Sum/1GB,2)}}
```

## Copy files older than 30 days
```powershell
Get-ChildItem -Path C:\source | Where-Object { $_.LastWriteTime -lt (Get-Date).AddDays(-30) } | Copy-Item -Destination C:\destination
```

## Delete files older than 30 days
```powershell
Get-ChildItem -Path C:\path -Recurse | Where-Object { $_.LastWriteTime -lt (Get-Date).AddDays(-30) } | Remove-Item -Force
```

## List hidden files
```powershell
Get-ChildItem -Path C:\ -Force | Where-Object { $_.Attributes -match 'Hidden' } | Select-Object FullName
```

## Get file permissions
```powershell
Get-Acl -Path C:\path\to\file | Select-Object -ExpandProperty Access
```

## Count files in folder
```powershell
(Get-ChildItem -Path C:\path -Recurse -File).Count
```
