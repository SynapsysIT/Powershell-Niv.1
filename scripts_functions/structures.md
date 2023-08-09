---
icon: quote
order: 8
---
# Les structures

## IF-ELSE-ELSEIF

Le bloc [!badge variant="secondary" text="IF"] permet l'éxécution d'un bloc de code uniquement dans le cas où une condition est remplie.

```powershell
$Texte = "Condition"

if ($Texte -eq "Condition")
{
    Write-Host "Condition remplie" 
}
else
{
    Write-Host "Condition NON-remplie"
}
```
Le bloc [!badge variant="secondary" text="ELSEIF"] permet de rajouter une condition.

```powershell
$Texte = "Condition"

if ($Texte -eq "Condition")
{
    Write-Host "Condition remplie" 
}
elseif ( $Texte -is [string] )
{
    Write-Host "Condition NON-remplie mais la valeur est bien une châine de caractère"
}
```

Les blocs [!badge variant="secondary" text="ELSE"] et [!badge variant="secondary" text="ELSEIF"] ne sont pas obligatoire à la suite d'un bloc [!badge variant="secondary" text="IF"]

## FOREACH

A l'instar de la commande 
[!badge target="blank" text="Foreach-Object"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.3) . [!badge variant="secondary" text="foreach"] permet de répéter une action pour chaque éléments d'une collection d'objets.

```powershell
$Names = @('Mathieu', 'Julien', 'Sylvain', 'Romain')

ForEach ($Name in $Names) 
{ 
    Write-Host "Hello $Name!" 
}
```

```text Output :icon-chevron-right:
Hello Mathieu!
Hello Julien!
Hello Sylvain!
Hello Romain!
```

Ici [!badge variant="danger" text="$Names"] est la variable contenant la collection à parcourir, tandis que [!badge variant="danger" text="$Name"] représente l'élément unique de cette collection, dont la valeur changera à chaque itération de la boucle.

La boucle Foreach est trés utile pour générer rapidement une collection d'objets de type `pscustomobject`

```powershell
$Tablede10 = foreach ($Number in 1..10)
{
    [PSCustomObject]@{
        Calcul = "$Number x 10"
        Résultat = $Number*10
    }
}

$Tablede10
```

```text Output :icon-chevron-right:
Calcul  Egal
------  ----
1 x 10    10
2 x 10    20
3 x 10    30
4 x 10    40
5 x 10    50
6 x 10    60
7 x 10    70
8 x 10    80
9 x 10    90
10 x 10  100
```

## WHILE

Le bloc [!badge variant="secondary" text="WHILE"] permet d'éxécuter le bloc de code **tant qu'une** condition est remplie.

```powershell
$i = 10

While($i -ge 0)
{ 
    $i
    $i --
}
```

## DO-WHILE

Le bloc [!badge variant="secondary" text="DO-WHILE"] est identique au bloc [!badge variant="secondary" text="WHILE"] mais vérifie la condition à la fin, le bloc de code s'éxécutera donc au mininum une fois.

```powershell
$i = 10 

do 
{
    $i
    $i --
} while ($i -ge 0)
```

## DO-UNTIL

Le bloc [!badge variant="secondary" text="DO-UNTIL"] est identique au bloc [!badge variant="secondary" text="DO-WHILE"] mais s'éxécutera **jusqu'à ce que la condition soit vraie**. Elle s'éxécutera donc **tant que** la condition est fausse.

```powershell
$i = 10 

do 
{
    $i
    $i --
} while ($i -ge 0)
```

## SWITCH

Le bloc [!badge variant="secondary" text="SWITCH"] permet d'éxécuter un bloc de code en fonction de plusieurs cas de figure.

```powershell
$Value = "Condition"

switch($Value) 
{ 
	'Condition' { Write-Host 'Condition n°1 remplie' } 
	'Fondition' { Write-Host 'Condition n°2 remplie' } 
}
```

```powershell
$Value = 15

switch($Value) 
{ 
	$_ -gt 0    { Write-Host 'La valeur est supérieure à 0' } 
	$_ -lt 20    { Write-Host 'La valeur est inférieur à 20' } 
}
```

En ajoutant le paramètre `-WildCard` Le bloc [!badge variant="secondary" text="SWITCH"] permet d'accepter des caractères wildcard et regex dans la condition

```powershell
$Value = "Condition"
Switch –Wildcard ($Value) 
{ 
    'Condition' { Write-Host 'Condition n°1 remplie' } 
    'Condi*' { Write-Host 'Condition n°2 remplie' } 
    'C[aoc]ndition' {Write-Host 'Condition n°3 remplie' }
    'C?ndition' {Write-Host 'Condition n°4 remplie' } 
}
```

## Les Opérateurs Break / Continue

### continue

L'opérateur [!badge variant="secondary" text="continue"]  fonctionne à l'intérieur d'une boucle (for, foreach, while and do). Il permet de passer l'itération en cours de la boucle sans l'arrêter.

```powershell
$i = 0
while ($i -lt 20)
{
    $i++
    if ($i -eq 7) { continue }
    Write-Host $I
}
```

```text Output :icon-chevron-right:
Hello Mathieu!
Hello Julien!
Hello Sylvain!
Hello Romain!
```

### break

L'opérateur [!badge variant="secondary" text="break"]  fonctionne à l'intérieur d'une boucle (for, foreach, while and do). Il permet d'arrêter immédiatement le fonctionnement de la boucle.

```powershell
$i = 0
while ($i -lt 15)
{
    $i++
    if ($i -eq 7) { break }
    Write-Host $i
}
```

Ce code va compter les chiffres de 1 à 15 mais va s'arrêter arrivé au chiffre 7.

!!!
[!badge variant="secondary" text="break"] peut aussi être appelé à n'importe quel endroit d'un fichier de script. Il arrêtera alors l'exécution du script en lui même.
!!!