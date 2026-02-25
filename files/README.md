# Files

One-liners for file and directory management.

## Commands

| Description | Command |
|-------------|---------|
| Find files by extension | `Get-ChildItem -Recurse -Filter *.log` |
| Find files larger than 100MB | `Get-ChildItem -Recurse | Where-Object { $_.Length -gt 100MB }` |
| Find files modified last 7 days | `Get-ChildItem -Recurse | Where-Object { $_.LastWriteTime -gt (Get-Date).AddDays(-7) }` |
| Find duplicate files | `Get-ChildItem -Recurse -File | Group-Object { (Get-FileHash $_.FullName).Hash } | Where-Object Count -gt 1` |
| Count files in folder | `(Get-ChildItem -Recurse -File).Count` |
| Get total folder size | `"{0:N2} MB" -f ((Get-ChildItem -Recurse | Measure-Object -Property Length -Sum).Sum / 1MB)` |
| Rename files to lowercase | `Get-ChildItem | Rename-Item -NewName { $_.Name.ToLower() }` |
| Delete files older than 30 days | `Get-ChildItem -Recurse | Where-Object { $_.LastWriteTime -lt (Get-Date).AddDays(-30) } | Remove-Item` |
