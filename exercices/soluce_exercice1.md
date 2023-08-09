---
visibility: hidden
---
# Solution Exercice 1

```powershell
Get-Command -Verb Get -Noun *disk*
Get-Help Get-Disk -Online

$Disk = Get-Disk -Number O
$Disk | Get-Member

$Disk.IsSystem
```


[!button variant="success" icon="arrow-left" text="Retourner à l'exercice"](exercice1.md)