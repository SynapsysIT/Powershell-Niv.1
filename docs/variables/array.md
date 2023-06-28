Une array est une **liste** de valeur

```powershell
$ArrayOfInts = 1,2,3,4 
$ArrayOfStrings = "Un","Deux","Trois","Quatre"
```

## Indexage dans une liste

```powershell title="Sélectionner le premier élément de la liste"
$ArrayOfInts [0]
```

```powershell title="Sélectionner le dernier élément de la liste"
$ArrayOfInts [-1]
```

```powershell title="Utiliser une variable comme index"
$int = 1
$ArrayOfInts [$int]
```

```powershell title="Sélectionner une plage dans la liste"
$ArrayOfInts [0..2]
```