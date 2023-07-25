---
icon: hash
order: 3
---
# Hashtable

Une **Hashtable** est un tableau de correspondance clé/valeur

```powershell
$Environemment= @{PROD= "SERVER-PROD"; DEV = "SERVER-DEV"; HOM = "SERVER-HOM"}
```

Les valeurs peuvent alors être appelés en utilisant leur clé

```powershell
$Environemment["PROD"]
```


```text Output ❱
"SERVER-PROD"
```

Ou comme pour appelé la propriété d'un objet

```powershell
$Environemment.PROD
```

```text Output ❱
"SERVER-PROD"
```
