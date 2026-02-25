# Text Processing

One-liners for working with text and files.

## Commands

| Description | Command |
|-------------|---------|
| Search for string in files | `Get-ChildItem -Recurse | Select-String -Pattern "searchterm"` |
| Count lines in file | `(Get-Content file.txt).Count` |
| Find and replace in file | `(Get-Content file.txt) -replace "old", "new" | Set-Content file.txt` |
| Get unique lines | `Get-Content file.txt | Sort-Object -Unique` |
| Sort lines in file | `Get-Content file.txt | Sort-Object | Set-Content sorted.txt` |
| Count word occurrences | `(Get-Content file.txt | Select-String -Pattern "word" -AllMatches).Matches.Count` |
