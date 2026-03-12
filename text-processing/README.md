# Text Processing

One-liners for text processing tasks.

---

## Search for string in file
```powershell
Select-String -Path C:\path\to\file.txt -Pattern "searchterm"
```

## Search recursively in multiple files
```powershell
Select-String -Path C:\path\*.log -Pattern "searchterm" -Recurse
```

## Count lines in file
```powershell
(Get-Content C:\path\to\file.txt).Count
```

## Get specific line from file
```powershell
(Get-Content C:\path\to\file.txt)[9]
```

## Replace text in file
```powershell
(Get-Content C:\path\to\file.txt) -replace "oldtext", "newtext" | Set-Content C:\path\to\file.txt
```

## Get last 20 lines of file
```powershell
Get-Content C:\path\to\file.txt -Tail 20
```

## Get first 20 lines of file
```powershell
Get-Content C:\path\to\file.txt -TotalCount 20
```

## Convert CSV to JSON
```powershell
Import-Csv C:\path\to\file.csv | ConvertTo-Json | Out-File C:\path\to\file.json
```

## Sort lines in file
```powershell
Get-Content C:\path\to\file.txt | Sort-Object | Set-Content C:\path\to\sorted.txt
```

## Remove duplicate lines
```powershell
Get-Content C:\path\to\file.txt | Sort-Object -Unique | Set-Content C:\path\to\file.txt
```
