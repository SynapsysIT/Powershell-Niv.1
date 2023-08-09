---
order: 7
--- 

# Group-Object

[!badge target="blank" text="Group-Object"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/group-object?view=powershell-7.3) permet de regrouper les objets d'une collection en fonction de la valeur d'une de leur propriétés. Cette commande renvoie un nouvel objet de type `groupinfo`


```powershell
Get-Service | Group-Object Status
```

```text Output :icon-chevron-right: 
Count Name                      Group
----- ----                      -----
  173 Stopped                   {AarSvc_3267b5, AESMService, AJRouter,...}
  122 Running                   {AdobeARMservice, Appinfo, AppXSvc,...}
```

___ 

```powershell
$names = @( "Aaron", "Albert", "Alphonse","Julien", "Mathieu", "Lucile", "Cédric", "Sébastien")
$names | Group-Object -Property Length
```

```text Output :icon-chevron-right: 
Count Name                      Group
----- ----                      -----
    1 5                         {Aaron}
    4 6                         {Albert, Julien, Lucile, Cédric}
    1 7                         {Mathieu}
    1 8                         {Alphonse}
    1 9                         {S├®bastien}
```