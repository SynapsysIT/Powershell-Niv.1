# Exercices 3

## Function

Écrivez une fonction `Convert-Octects` qui prend en paramètre une taille en octets et une unité cible, et retourne un objet contenant la valeur convertie.

La fonction doit :

- Accepter un paramètre $Octets de type `[long]`, obligatoire, en position 0
- Accepter un paramètre $Unite de type `[string]`, obligatoire, limité aux valeurs KB, MB, GB via `[ValidateSet]`
- Retourner un PSCustomObject avec les propriétés Octets, Unite et Resultat (arrondi à 2 décimales)

!!!tip
- Pour arrondir un nombre : [math]::Round( *valeur*, *nb_apres_virgule*)
- Pour convertir, vous pouvez utiliser les opérateurs spéciaux: `/1GB`, `/1MB`, `/1KB`
!!!

## Script

Ecrivez un script qui renverra des informations sur votre poste de travail sous forme d'objet:

- Nom de la machine
- La Version de Windows (Caption)
- Le numéro de build Windows
- RAM Totale en GB
- Espace disque libre sur le disque C: en GB

Bonus: Permettre de retourner la sortie sous forme de JSON en fonction d'un paramètre `[switch]`

⚠️ **Votre script devra utiliser la fonction précédemment crée**

!!!tip
La commande `Get-CimInstance -Class win32_OperatingSystem` vous permez de récupérer une partie des informations demandées.
!!!

[!button variant="danger" icon=":angry:" text="Solution"](soluce_exercice3.md)