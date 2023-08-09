---
order: 6
---

# Manipuler des chaînes de caractères

## Remplacer (-replace)

```powershell
"Le héros s'appelle Zelda !" -replace "Zelda","Link" 
```

```text Output :icon-chevron-right:
Le héros s'appelle Link !
```

## Séparer (-split)

```powershell
"nom.prenom@societe.com" -split "@" 
```

```text Output :icon-chevron-right:
nom.prenom
societe.com
```

!!!
Le résulat obtenu est une `array` (liste) d'objet de type **string**
!!!

## Joindre (-join)

```powershell
"nom.prenom","societe.com" -join "@"
```

```text Output :icon-chevron-right:
nom.prenom@societe.com
```