---
visibility: hidden
---

# Solution Exercice 5

```powershell
Get-Process | Where-Object {$_.id -lt 1000}
```

[!button variant="success" icon="arrow-left" text="Retourner à l'exercice"](exercice6.md)