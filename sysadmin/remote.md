---
icon: move-to-end
order: 10
---

# Remote Powershell

A l'instar de SSH sur un système Unix, Powershell permet l'ouverture de session distante et l'exécution sur des machines distantes.


### Activer Remote Powershell sur une machine cliente

```powershell
Enable-PSRemoting -Force
```
### Ouvrir une session interactive sur une machine cliente

```powershell
Enter-PSSession –ComputerName "Server01"
```

Il est possible d'ouvrir une session Remote Powershell et de l'enregistrer au sein d'une variable pour l'utiliser dans les commandes possédant un paramètre **-session**

```powershell
$Session = New-PSSession –computername  "Server01"
```

```powershell
Invoke-Command -Session $Session -ScriptBlock {Get-Process}
```

```powershell
Copy-Item -ToSession $Session -Path "C:\Users\Administrator\MonScript.ps1" -Destination "C:\chemin\MonScript.ps1"
```

```powershell
Invoke-Command -Session $session -ScriptBlock {. "C:\chemin\Monscript.ps1"}
```


