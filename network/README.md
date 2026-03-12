# Network

One-liners for network-related tasks.

---

## Get local IP
```powershell
(Get-NetIPAddress -AddressFamily IPv4 | Where-Object { $_.InterfaceAlias -notlike "*Loopback*" }).IPAddress
```

## Get DNS servers
```powershell
Get-DnsClientServerAddress | Select-Object InterfaceAlias, ServerAddresses
```

## Flush DNS cache
```powershell
Clear-DnsClientCache
```

## Test connection
```powershell
Test-NetConnection -ComputerName google.com
```

## Get listening ports
```powershell
Get-NetTCPConnection | Where-Object State -eq 'Listen' | Select-Object LocalPort, @{n='Process';e={(Get-Process -Id $_.OwningProcess).Name}} | Sort-Object LocalPort
```

## Get MAC address
```powershell
Get-NetAdapter | Select-Object Name, MacAddress
```

## Show routing table
```powershell
Get-NetRoute | Select-Object DestinationPrefix, NextHop, RouteMetric
```

## Get Wi-Fi speed
```powershell
(Get-NetAdapter | Where-Object { $_.Name -like "*Wi-Fi*" }).LinkSpeed
```

## Show established connections
```powershell
Get-NetTCPConnection -State Established | Select-Object RemoteAddress, RemotePort, OwningProcess
```

## Show active DNS servers
```powershell
Get-DnsClientServerAddress -AddressFamily IPv4 | Select-Object InterfaceAlias, ServerAddresses
```
