---
order: 10
--- 

# Where-Object

[!badge target="blank" text="Where-Object"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.3) permet de trier une collection pour n'afficher que ceux répondant à des conditions précises.


```powershell
$names = @( "Aaron", "Albert", "Alphonse","Julien", "Mathieu", "Lucile", "Cédric", "Sébastien")
$names | Where-Object { $_ -like "A*" }
```

```text Output ❱ 
Aaron
Albert
Alphonse
```


```powershell
Get-HotFix | Where-Object { $_.Description -eq "Update"}
```

```powershell
Get-ChildItem | Where-Object { $_.LastWriteTime -gt (Get-Date "01/09/2023") }
```
