# User Management

One-liners for managing users and groups.

## Commands

| Description | Command |
|-------------|---------|
| Get current user | `$env:USERNAME` |
| Get current user details | `Get-LocalUser $env:USERNAME` |
| List all local groups | `Get-LocalGroup` |
| Add user to group | `Add-LocalGroupMember -Group "Administrators" -Member "username"` |
| Get logged in users | `query user` |
