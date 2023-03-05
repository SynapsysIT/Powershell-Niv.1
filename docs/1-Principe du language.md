# Principe du language

## Syntaxe des commandes
___

Toutes les commandes PowerShell, appelés CmdLets se composent d’un verbe et d’un nom séparé par un tiret. Le résultat de la commande peut être influencer par l'ajout de paramètres.

![Syntax](assets/syntax.png)

Chaque verbe correspond à un type d'action précis :

| Verb     | Action               |
| -------- | -------------------- |
| `Get`    | Requeter             |
| `Set`    | Configurer / Définir |
| `Import` | Importer             |
| etc ...  | ...                  | 


!!! note " "
	**`#!powershell Get-Verb`** permet d'obtenir la liste des verbs "approuvés" par les best-practices Powershell



## Les 3 commandes indispensables
___

**`#!powershell Get-Command`** *Lister et chercher des commandes*

**`#!powershell Get-Help`**  *Obtenir l'aide d'une commande*

**`#!powershell Get-Member`**  *Connaitre le type, les propriétés et les méthodes d’un objet*


