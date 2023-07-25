
# Opérateur de type

| Commande   |  Exemple   | Description         |
| ---------- | --- | ------------------- |
| `-is`  | `99 -is "int"`    | Compare le type de l'objet founi et retourne `true` si égal                |
| `-isnot`  | `99 -isnot "int"`    | Compare le type de l'objet founi et retourne `false` si égal               |
| `-as`  |   `"01/09/23" -as [datetime]`  | Converti la valeur fourni dans un type donnée. Renvoie une erreur si la conversion est impossible    |


L'opérateur `-as` peut aussi permettre de vérifier qu'une donnée est correctement formatée:

```powershell
"192.168.1.10" -as [ipaddress]
```

```text Output ❱
AddressFamily      : InterNetwork
ScopeId            : 
IsIPv6Multicast    : False
IsIPv6LinkLocal    : False
IsIPv6SiteLocal    : False
IsIPv6Teredo       : False
IsIPv6UniqueLocal  : False
IsIPv4MappedToIPv6 : False
Address            : 167880896
IPAddressToString  : 192.168.1.10
```

!!!success
Cette commande renvoie un objet de type `ipaddress` 
!!!

```powershell
"192.168.1.300" -as [ipaddress]
```

!!!danger
Cette commande ne renverra rien, permettant d'en déduire que le format d'entrée est incorrect.
!!!