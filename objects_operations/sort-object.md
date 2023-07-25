---
order: 8
--- 

# Sort-Object

[!badge target="blank" text="Sort-Object"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7.3) permet de trier une collection d'objet en fonction de la valeur de ses propriétés

```powershell
$names = @( "Aaron", "Albert", "Alphonse","Julien", "Mathieu", "Lucile", "Cédric", "Sébastien")
$names | Sort-Object
```

```text Output ❱ 
Aaron
Albert
Alphonse
C├®dric
Julien
Lucile
Mathieu
Sébastien
```

Pour inverser l'ordre:

```powershell
$names = @( "Aaron", "Albert", "Alphonse","Julien", "Mathieu", "Lucile", "Cédric", "Sébastien")
$names | Sort-Object -Descending
```


```powershell
Get-Process | Sort-Object CPU -Descending
```

```powershell
Get-Service | Sort-Object Status
```
