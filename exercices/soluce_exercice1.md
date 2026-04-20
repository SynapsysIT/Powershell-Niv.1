---
visibility: hidden
---
# Solution Exercice 1

___

# Solution Exercice 1.1
```powershell
Get-Command -Verb Get -Noun *disk*
Get-Help Get-Disk -Online

$Disk = Get-Disk -Number O
$Disk | Get-Member

$Disk.IsSystem
```

___

# Solution Exercice 1.2

```powershell
$services = Get-Service
$services.Count
$services[0].Name
$services[-1].Status
```

___

# Solution Exercice 1.3

```powershell
$srv1 = [PSCustomObject]@{
    Nom     = "SRV-WEB01"
    IP      = "192.168.1.10"
    OS      = "Windows Server 2022"
    Statut  = "Online"
}

# Etape 2
"Information Serveur 1: $($srv1.Nom) - $($srv1.IP)"

# Étape 3
$srv1.Statut = "Offline"

```

[!button variant="success" icon="arrow-left" text="Retourner à l'exercice"](exercice1.md)