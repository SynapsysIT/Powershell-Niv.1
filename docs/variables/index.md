
# Les variables

- La variable est un emplacement mémoire. Elle se compose de 3 éléments :
    * Un nom
    * Un type 
    * Une valeur

Sous PowerShell, une variable est précédée du signe : **$** 

Le contenu d'une variable peut être une valeur unique, ou une **collection** d'objets
___
## Assignation de variables

L'assignation d'une variable se fait avec le symbole **=**

```powershell
$Variable = "ma variable"
```

Le résultat d'une commande peut être stocké dans une variable de la même manière

```powershell
$Process = Get-Process -name "Notepad"
```

Powershell détermine le type de la variable en fonction de la syntaxe avec laquelle elle est définie

```powershell
$Variable = 1
$Variable | Get-Member
```

```text title="Output ❱"

   TypeName: System.Int32

...
```


```powershell
$Variable = "1"
$Variable | Get-Member
```

```text title="Output ❱"
   TypeName: System.String

...
```

___
## Forcer le typage

Il peut être néccéssaire d'avoir à forcer le type d'une variable. Pour cela on précise le type voulu entre **[ ]** avant le nom de la variable.

```powershell
[string]$Variable = 1               # Int en string
[int]$Variable = "1"                # String en int
[char]$Char = 0201                  # Valeur ASCII en charactère
[datetime]$variable = "10/12/1984"  # String en Date
```

___
## Propriétés et méthodes

Les propriétés et les méthodes de l'objet stocké en variable pourront être appelé par un **.**

```powershell
$Variable = "Ceci est une phrase"
$Variable.Length
$Variable.ToUpper()
```

```powershell
$Process = Get-Process notepad 
$Process.ID
$Process.Kill()
```

___
## Utilisation dans une commande

Une variable ou seulement ses propriétés pourront être utilisés dans une commande

```powershell
$Date = Get-Date "28/09/2021"
Get-EventLog -LogName Application -After $Date
```

```powershell
$Service = Get-Service "Spooler"
"Spooler service is $($Service.Status)"
```
