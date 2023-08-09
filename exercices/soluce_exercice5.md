---
visibility: hidden
---

# Solution Exercice 5

```powershell
1..10 | ForEach-Object {New-Item -Type File -Name "File_$_.txt"}
```

[!button variant="success" icon="arrow-left" text="Retourner à l'exercice"](exercice5.md)