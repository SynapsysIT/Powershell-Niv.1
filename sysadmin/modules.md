---
icon: apps
order: 8
---

# Les Modules

Un **module** Powershell est une bibliothèque de commandes (fonctions) dédié à la gestion ou l'administration d'un élément précis (Application / Api / Rôle Windows Server / ...).

La liste des modules installés sur la machine s'obtient grâce à la commande [!badge target="blank" text="Get-Module"](https://go.microsoft.com/fwlink/?LinkID=2096696)


```powershell
Get-Module -ListAvailable
```

Depuis Powershell v.3, le chargement d'un module est automatique lorsque l'on appelle une commande qu'il contient. Mais le chargement peut-être forcé grâce à la commande [!badge target="blank" text="Import-Module"](https://go.microsoft.com/fwlink/?LinkID=2096585)

```powershell
Import-Module ActiveDirectory
```

La liste des commandes d'un module s'obtient via un paramètre de la commande [!badge target="blank" text="Get-Command"](https://go.microsoft.com/fwlink/?LinkID=2096579)

```powershell
Get-Command -Module ActiveDirectory
```


## Rechercher des modules

Microsoft met à disposition un repository public permettant aux particulier comme au professionnels de mettre à disposition des modules Powershell.

[!badge target="blank" text="Find-Module"](https://go.microsoft.com/fwlink/?LinkID=398574) permet de rechercher des modules ( par defaut dans le repository Microsoft)

```powershell
Find-Module -Name PowerShell*
```

```text Output :icon-chevron-right:
Version              Name                                Repository           Description
-------              ----                                ----------           -----------
0.4.7                powershell-yaml                     PSGallery            Powershell module for serializing and deserializing YAML
2.2.5                PowerShellGet                       PSGallery            PowerShell module with commands for discovering, installing, ÔÇª
1.0.0                powershell-devops                   PSGallery            PowerShell module for dealing with commands in Azure DevOps PÔÇª
1.2.5                PowerShell-Beautifier               PSGallery            PowerShell beautifier / code cleaner / pretty printer.  For mÔÇª
0.16.1               PowerShellForGitHub                 PSGallery            PowerShell wrapper for GitHub API
```

## Installer des modules

[!badge target="blank" text="Install-Module"](https://go.microsoft.com/fwlink/?LinkID=398573) permet d'installer des modules

```powershell
Install-Module powershell-yaml
```


!!!
Le repository Microsoft peut être parcouru depuis un navigateur sur [PowerShell Gallery](https://www.powershellgallery.com/)
!!!