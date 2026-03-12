# User Management

One-liners for user management tasks.

---

## Get all local users
```powershell
Get-LocalUser | Select-Object Name, Enabled, LastLogon, PasswordLastSet
```

## Create new local user
```powershell
New-LocalUser -Name "username" -Password (ConvertTo-SecureString "Password123!" -AsPlainText -Force) -FullName "Full Name"
```

## Delete local user
```powershell
Remove-LocalUser -Name "username"
```

## Add user to local group
```powershell
Add-LocalGroupMember -Group "Administrators" -Member "username"
```

## Remove user from local group
```powershell
Remove-LocalGroupMember -Group "Administrators" -Member "username"
```

## Get all local groups
```powershell
Get-LocalGroup | Select-Object Name, Description
```

## Get members of a group
```powershell
Get-LocalGroupMember -Group "Administrators" | Select-Object Name, ObjectClass
```

## Disable local user
```powershell
Disable-LocalUser -Name "username"
```

## Enable local user
```powershell
Enable-LocalUser -Name "username"
```

## Reset local user password
```powershell
Set-LocalUser -Name "username" -Password (ConvertTo-SecureString "NewPassword123!" -AsPlainText -Force)
```
