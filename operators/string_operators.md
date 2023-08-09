---
order: 9
---

# Comparer des chaînes de caractères

## Egalité (-eq)

```powershell
$Variable = "Powershell"
$Variable -eq "Powershell"
```

```text Output :icon-chevron-right:
True
```

## Wildcard (-like)

```powershell
$String = "Texte"
$String -like "Text*"
```

```powershell
$String -like "*ext*"
```

```text Output :icon-chevron-right:
True
```

## Match (-match)

```powershell
$String = "Chaine de charactère complexe"
$String -match "char"
```

```text Output :icon-chevron-right:
True
```

`-match` permet aussi d'utiliser le format **Regex** pour comparer un format de chaîne attendu avec une valeur:

```powershell
"192.168.0.10" -match "(?:(?:2(?:[0-4][0-9]|5[0-5])|[0-1]?[0-9]?[0-9])\.){3}(?:(?:2([0-4][0-9]|5[0-5])|[0-1]?[0-9]?[0-9]))"
```

```text Output :icon-chevron-right:
True
```

## Présence (-contains)

` -contains` permet de vérifier la présence d'une valeur dans une liste

```powershell
$Liste = @("Valeur1","Valeur2","Valeur3")
$Liste -contains "Valeur2"
```

```text Output :icon-chevron-right:
True
```

!!!
Ces opérateurs, précédés de la lettre [!badge variant="danger" text="C"] ( `-ceq` , `-clike`, … ) rend la comparaison sensible à la case
!!!

!!!
Ces opérateurs, précédés [!badge variant="danger" text="not"] ( `-notlike` , `-notmatch`, … ) inverse la comparaison
!!!