---
icon: command-palette
order: 999
---

# Exécuter des commandes

## Syntaxe des commandes
![Syntax](../assets/syntax.png)
Toutes les commandes PowerShell, appelés **CmdLets** se composent d’un verbe et d’un nom séparé par un tiret. Le résultat de la commande peut être influencer par l'ajout de paramètres.


Par exemple, la commande `Get-Service` exécutée telle quelle, renverra l'ensemble des services.

Tandis que la commande `Get-Service -Name *Net*` ne renverra que les services contenant *net* dans leur nom.

Chaque **verbe** correspond à un type d'action précis :

| Verb                                      | Action                                 |
| ----------------------------------------- | -------------------------------------- |
| [!badge variant="contrast" text="Get"]    | :icon-arrow-right: Requeter            |
| [!badge variant="contrast" text="Set"]    | :icon-arrow-right: Configurer / Définir |
| [!badge variant="contrast" text="Import"] | :icon-arrow-right: Importer             |
| etc.                                   | ...                                    |


!!!
[!badge target="blank" text="Get-Verb"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.core/get-verb?view=powershell-5.1) permet d'obtenir la liste des **verbs** approuvés par les best-practices Powershell
!!!

## Les 3 commandes <span style="color:#be1212"> indispensables </span>

![](../assets/triforce.png)

### Get-Command
[!badge target="blank" text="Get-Command"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.core/get-command?view=powershell-5.1) permet de rechercher une commande en fonction de nom, de son **verb** ou de son module d'appartenance.

```powershell
Get-Command -Name "*process*"
```

```text Output :icon-chevron-right:

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      7.0.0.0    Microsoft.PowerShell.Management
Cmdlet          Enter-PSHostProcess                                7.3.4.500  Microsoft.PowerShell.Core
Cmdlet          Exit-PSHostProcess                                 7.3.4.500  Microsoft.PowerShell.Core
Cmdlet          Get-Process                                        7.0.0.0    Microsoft.PowerShell.Management
Cmdlet          Get-PSHostProcessInfo                              7.3.4.500  Microsoft.PowerShell.Core
Cmdlet          Start-Process                                      7.0.0.0    Microsoft.PowerShell.Management
Cmdlet          Stop-Process                                       7.0.0.0    Microsoft.PowerShell.Management
Cmdlet          Wait-Process                                       7.0.0.0    Microsoft.PowerShell.Management


```

### Get-Help

La commande [!badge target="blank" text="Get-Help"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.core/get-help?view=powershell-5.1)  permet d'obtenir une aide sur le fonctionnement d'une commande.

Elle vous permet d'identifier les paramètres attendues, lesquels sont obligatoires ou non, le type de valeurs à leur envoyer, etc ...

```powershell
Get-Help -Name "Get-Service"
```

```text Output :icon-chevron-right:

NAME
    Get-Service
    
SYNTAX
    Get-Service [[-Name] <string[]>] [-DependentServices] [-RequiredServices] [-Include <string[]>] [-Exclude <string[]>] [<CommonParameters>]
    
    Get-Service -DisplayName <string[]> [-DependentServices] [-RequiredServices] [-Include <string[]>] [-Exclude <string[]>] [<CommonParameters>]
    
    Get-Service [-DependentServices] [-RequiredServices] [-Include <string[]>] [-Exclude <string[]>] [-InputObject <ServiceController[]>] [<CommonParameters>]
    

ALIASES
    gsv
    

REMARKS
    Get-Help cannot find the Help files for this cmdlet on this computer. It is displaying only partial help.
        -- To download and install Help files for the module that includes this cmdlet, use Update-Help.
        -- To view the Help topic for this cmdlet online, type: "Get-Help Get-Service -Online" or
           go to https://go.microsoft.com/fwlink/?LinkID=2096496.



```

!!!
L'ajout du paramètre **-Online** à la commande `Get-Help` vous envoie sur la page **Microsoft Docs** correspondante.
!!!

### Get-Member

[!badge target="blank" text="Get-Member"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/get-member?view=powershell-7.3)  vous permet d'obtenir *"la carte d'identité"* d'un objet obtenu par l'éxécution d'une commande ou stockée dans une variable.
Elle vous permettra de connaitre:

- Son **type**
- Ses **propriétés**
- Ses **méthodes**


```powershell
Get-Process | Get-Member
```

```text Output :icon-chevron-right:
   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Disposed                   Event          System.EventHandler Disposed(System.Object, System.EventArgs)
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ErrorDataReceived(System.Object, System.Diagnostics.…
Exited                     Event          System.EventHandler Exited(System.Object, System.EventArgs)
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler OutputDataReceived(System.Object, System.Diagnostics…
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill(), void Kill(bool entireProcessTree)
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
```


___

| Commande                                                                                                                                                       | Description                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| [!badge target="blank" text="Get-Command"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.core/get-command?view=powershell-5.1)  | :icon-arrow-right: Lister et chercher des commandes                             |
| [!badge target="blank" text="Get-Help"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.core/get-help?view=powershell-5.1)        | :icon-arrow-right: Obtenir l'aide d'une commande                                |
| [!badge target="blank" text="Get-Member"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/get-member?view=powershell-7.3) | :icon-arrow-right: Connaitre le type, les propriétés et les méthodes d’un objet |
