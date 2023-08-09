---
icon: issue-reopened
order: 7
---

Même si l'habitude rends l'utilisation des commandes DOS native plus rapide, il est important de noter que l'utilisation de leur équivalent Powershell, comme toutes les commandes Powershell renvoie un objet permettant une utilisation plus fine du résultat. 

## ipconfig

```powershell
Get-NetIPConfiguration
```

```text Output :icon-chevron-right:
InterfaceAlias       : Ethernet
InterfaceIndex       : 9
InterfaceDescription : Intel(R) Ethernet Connection (2) I219-V
NetProfile.Name      : Réseau
IPv6Address          : fd80:9f3e:68ad:4519:4942:3f1a:d05f:e390
IPv4Address          : 192.168.1.2
IPv6DefaultGateway   : 
IPv4DefaultGateway   : 192.168.1.1
DNSServer            : 192.168.1.102
                       1.1.1.1
```

## ping

```powershell
Test-Connection  google.fr
```

```text Output :icon-chevron-right:

   Destination: google.fr

Ping Source           Address                   Latency BufferSize Status
                                                   (ms)        (B)
---- ------           -------                   ------- ---------- ------
   1 HULK             142.250.75.227                  3         32 Success
   2 HULK             142.250.75.227                  3         32 Success
   3 HULK             142.250.75.227                 15         32 Success
   4 HULK             142.250.75.227                  3         32 Success
```

## telnet

```powershell
Test-NetConnection google.fr -Port 80
```

```text Output :icon-chevron-right:

ComputerName     : google.fr
RemoteAddress    : 142.250.75.227
RemotePort       : 80
InterfaceAlias   : Ethernet
SourceAddress    : 192.168.1.2
TcpTestSucceeded : True
```


## tracert


```powershell
Test-NetConnection google.fr -TraceRoute
```

```text Output :icon-chevron-right:
ComputerName           : google.fr
RemoteAddress          : 142.250.75.227
InterfaceAlias         : Ethernet
SourceAddress          : 192.168.1.2
PingSucceeded          : True
PingReplyDetails (RTT) : 3 ms
TraceRoute             : 192.168.1.1
                         0.0.0.0
                         194.149.166.62
                         72.14.211.26
                         72.14.233.77
                         216.239.48.45
                         142.250.75.227
```


## nslookup

```powershell
Resolve-DnsName synapsys-it.com
```


```text Output :icon-chevron-right:
Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
synapsys-it.com                                A      1183  Answer     217.70.184.38
```

## nslookup

```powershell
Get-NetTCPConnection -State Established
```


```text Output :icon-chevron-right:

LocalAddress                        LocalPort RemoteAddress                       RemotePort State       AppliedSetting OwningProcess
------------                        --------- -------------                       ---------- -----       -------------- -------------
fe80::c4b1:e773:9f4b:88f5%9         54321     fe80::f967:9cb8:e251:931a%9         8123       Established Internet       16216
::1                                 54103     ::1                                 5000       Established Internet       16132
::1                                 53944     ::1                                 5000       Established Internet       16132
::1                                 49967     ::1                                 49962      Established Internet       18972
::1                                 49962     ::1                                 49967      Established Internet       16232
::1                                 49957     ::1                                 4699       Established Internet       16232
fe80::c4b1:e773:9f4b:88f5%9         49893     fe80::f967:9cb8:e251:931a%9         1883       Established Internet       16216
fe80::c4b1:e773:9f4b:88f5%9         49681     fe80::f967:9cb8:e251:931a%9         1883       Established Internet       3536
::1                                 5000      ::1                                 54103      Established Internet       24116
::1                                 5000      ::1                                 53944      Established Internet       24116
::1                                 4699      ::1                                 49957      Established Internet       17624
127.0.0.1                           65001     127.0.0.1                           49716      Established Internet       3544
192.168.1.2                         54437     20.111.1.3                          443        Established Internet       17660
192.168.1.2                         54408     82.65.239.230                       443        Established Internet       20360
192.168.1.2                         54395     13.69.106.90                        443        Established Internet       18776
```

## net share

```powershell
Get-SmbShare
```


```text Output :icon-chevron-right:

Name   ScopeName Path       Description
----   --------- ----       -----------
ADMIN$ *         C:\Windows Administration ├á distance
C$     *         C:\        Partage par défaut
D$     *         D:\        Partage par défaut
E$     *         E:\        Partage par défaut
F$     *         F:\        Partage par défaut
IPC$   *                    IPC distant
```

