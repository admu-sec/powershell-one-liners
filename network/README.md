# Network

One-liners for network-related tasks.

## Commands

| Description | Command |
|-------------|---------|
| Get local IP | `(Get-NetIPAddress -AddressFamily IPv4 | Where-Object { $_.InterfaceAlias -notlike "*Loopback*" }).IPAddress` |
| Get DNS servers | `Get-DnsClientServerAddress | Select-Object InterfaceAlias, ServerAddresses` |
| Flush DNS cache | `Clear-DnsClientCache` |
| Test connection | `Test-NetConnection -ComputerName google.com` |
| Get listening ports | `Get-NetTCPConnection | Where-Object State -eq 'Listen' | Select-Object LocalPort, @{n='Process';e={(Get-Process -Id $_.OwningProcess).Name}} | Sort-Object LocalPort` |
| Get MAC address | `Get-NetAdapter | Select-Object Name, MacAddress` |
| Show routing table | `Get-NetRoute | Select-Object DestinationPrefix, NextHop, RouteMetric` |
| Get Wi-Fi speed | `(Get-NetAdapter | Where-Object { $_.Name -like "*Wi-Fi*" }).LinkSpeed` |
