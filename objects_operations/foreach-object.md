---
order: 6
--- 

# Foreach-Object

[!badge target="blank" text="Foreach-Object"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.3) permet de réaliser une opération pour chaque objet d'une collection

## Exemples

Créer un fichier `readme.txt` dans chaque sous-dossier du disque E
```powershell
Get-ChildItem E:\ -Directory | ForEach-Object { New-Item -Path $_.FullName -Name "Readme.txt" }
```

Pinger plusieurs hostname à la suite
```powershell
"google.com","1.1.1.1","nexistepas.com" | Foreach-Object { Test-Connection $_ -Count 1 }
```

