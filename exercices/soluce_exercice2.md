---
visibility: hidden
---

# Solution Exercice 2

## Solution Exercice 2.1

```powershell
$process = Get-Process | Sort-Object CPU -Descending | Select-Object ProcessName,Id,CPU -First 5
$process | Export-Csv -Path "rapport_process.csv" -NoTypeInformation
```

## Solution Exercice 2.2

```powershell
Get-Service |
    Where-Object { $_.StartType -eq "Automatic" } |
    Select-Object Name, Status, StartType |
    Group-Object Status
```



[!button variant="success" icon="arrow-left" text="Retourner à l'exercice"](exercice2.md)