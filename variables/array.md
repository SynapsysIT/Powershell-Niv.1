---
icon: list-unordered
order: 4
---
# Array
Une array est une **liste** de valeur

```powershell
$ArrayOfInts = 1,2,3,4 
$ArrayOfStrings = "Un","Deux","Trois","Quatre"
```

## Indexage dans une liste

```powershell Sélectionner le premier élément de la liste
$ArrayOfInts[0]
```

```powershell Sélectionner le dernier élément de la liste
$ArrayOfInts[-1]
```

```powershell Utiliser une variable comme index
$int = 1
$ArrayOfInts[$int]
```

```powershell Sélectionner une plage dans la liste
$ArrayOfInts[0..2]
```