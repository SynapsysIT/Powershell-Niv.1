---
icon: project
order: 1
---
# PSCustomObject

Le **PSCustomObject** permet la création d'un objet personnalisé dans lequel on pourra définire l'ensemble de ses propriétés

```powershell
$Computer= [PSCustomObject]@{
    Name= "HAL9000"
    OS = "Windows 3.11"
    Disks = "256Mo"
}

```

Il est possible de compléter l'objet via l'utilisation de la commande `Add-Member`

```powershell
$Computer | Add-Member -MemberType NoteProperty -Name RAM -Value "512Mo"
```

Les **propriétés** peuvent alors être appelés comme n'importe quel autre objet

```powershell
$Computer.Name
```

```text Output ❱
"HAL9000"
```
