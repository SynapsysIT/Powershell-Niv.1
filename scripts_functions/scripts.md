---
icon: log
order: 10
---

# Scripts

- Un **script** est un fichier texte au format **.ps1** contenant un enchaînement de commande, de structures et de fonctions.

Un script peut accepter des paramètres en entrée:

```powershell
Param
(
    [string]$computerName,
    [string]$filePath
)
```

## Éxécution

#### Depuis l'explorateur:

[!badge variant="contrast" text="Clic Droit"] [!badge variant="contrast" text=">"] [!badge variant="contrast" text="Exécuter avec Powershell"]

#### Depuis la console ou depuis un autre script:

`.\nomduscript.ps1`

#### Depuis un autre script:

```powershell 
& "C:\chemin\vers\monscript\script.ps1
```

```powershell Methode "Dot Sourcing"
. "C:\chemin\vers\monscript\script.ps1
```

!!!
L'éxécution du script en **DotSourcing** (avec le .) permet de conserver le contexte du script dans le contexte d'exécution ( Les variables ne disparaitront pas à la fin de l'éxécution )
!!!

### Execution Policy

Powershell intègre une sécurité qui permet de contrôler l'éxécution des scripts sur la machine.

[!badge target="blank" text="Get-ExecutionPolicy"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-7.3&viewFallbackFrom=powershell-7) permet de connaitre les stratégies d'éxécution sur la machine.

```powershell
Get-ExecutionPolicy -List
```

```text Output :icon-chevron-right:
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```


| Execution Policy | Description                                                                          |
| ---------------- | ------------------------------------------------------------------------------------ |
| **Restricted**       | Aucune exécution de script possible                                                  |
| **All Signed**       | Tous les scripts doivent être signés par un certificat valide                        |
| **Remote Signed**    | Les scripts téléchargés depuis Internet doivent être signés par un certificat valide |
| **ByPass**           | Aucune restriction                                                                   |

```powershell
Set-ExecutionPolicy ByPass
```

```powershell
powershell.exe –ExecutionPolicy Bypass –File "C:\chemin\monscript.ps1"
```