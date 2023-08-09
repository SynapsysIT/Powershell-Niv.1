---
icon: code
order: 9
---
# Fonctions

Une fonction est un morceau de code nommé.

Une fois exécutée, la fonction est chargée en mémoire **dans la session Powershell en cours**. Elle devient une commande disponible comme les autres.

Une fonction est définie par le mot clé `function`, un nom et optionnellement, des paramètres.

!!!danger
Si vous répétez au moins deux fois un ensemble de commande pour une même opération. C'est que vous devez en faire une fonction.
!!!

## Les paramètres


### Quick and dirty :poop:

```powershell
function Write-Presentation ($name, $age)
{

  "Bonjour $name, Tu as $age ans"

}
```

Cette syntaxe de base ne permet pas le contrôle des valeurs de paramètres entrés, de leur **type**, il ne permet pas non plus de les rendre **obligatoires**.

L'ordre des paramètres lors du lancement de la commandes sera le même que l'ordre dans lequel ils ont étés déclarés dans la fonction.

Cette fonction pourra donc être appelés de ces deux façons:

```powershell
Write-Presentation "Julien" "38"
```

```powershell
Write-Presentation -Name "Julien" -Age "38"
```

### Advanced and clean :+1:

```powershell #5-6,8-9
function Write-Presentation
{
    [CmdletBinding()] 
	param
    (
        [Parameter(Mandatory=$true,Position=0)]
        [String]$name,

        [Parameter(Mandatory=$true,Position=1)]
        [int]$age
    )
    
   Write-host "Bonjour $name, Tu as $age ans"

}
```

Nous ajoutons ici à nos déclarations de paramètres plusieurs élements:

#### Attributs de paramètres

Ils permettent d'ajuster le comportement du paramètres. Par exemple ici, le paramètres sera **obligatoire** `mandatory=$true`, et dans le cas ou le nom du paramètres ne sera pas spécifié lors de l'appel de la fonction, il devra se trouver en première position `Position=0`.

```powershell Liste des attributs de paramètres disponibles
[Parameter(Mandatory=$Boolean,
Position=Int,
ParameterSetName="String",
ValueFromPipeline=$Boolean,
ValueFromPipelineByPropertyName=$Boolean,
ValueFromRemainingArguments=Boolean)]
[Alias("String")]
[ValidateNotNull()]
[ValidateNotNullOrEmpty()]
[ValidateSet("String1", "String2")]
[ValidateCount(Int_min, Int_max)]
[ValidateLength(Int_min, Int_max)]
[ValidateRange(Int_min, Int_max)]
[ValidatePattern("RegexPattern")]
[ValidateScript({Expression})]
[AllowNull()]
[AllowEmptyString()]
[AllowEmptyCollection()]
[Type[]]
$Name
```

#### CmdLetBinding

```powershell #3
function Write-Presentation
{
    [CmdletBinding()] 
	param
    (
        [Parameter(Mandatory=$true,Position=0)]
        [String]$name,

        [Parameter(Mandatory=$true,Position=1)]
        [int]$age
    )
    
   Write-host "Bonjour $name, Tu as $age ans"

}
```

Le mot clé `CmdLetBinding()` permet l'ajout à votre fonction des paramètres communs à toute les commandes Powershell

| Paramètres     | Description                                                                |
| -------------- | -------------------------------------------------------------------------- |
| `-Verbose  `   | Permet d'afficher le retour `Verbose` de la commande                       |
| `-ErrorAction` | Permet de définir le comportement attendu en cas d'erreur dans la commande |

!!!
D'autres common parameters sont disponibles pour une utilisation plus avancée:
https://learn.microsoft.com/en-us/powershell/scripting/developer/cmdlet/common-parameter-names?view=powershell-7.3
!!!

## Fonctions avancées : Intégration au pipeline


Une fonction avancée qui pourra recevoir les objets avec lesquels interagir depuis le pipeline


```powershell
Function Ping-IP
{
    [CmdletBinding()]
    param(
        [Parameter(Mandatory = $True, ValueFromPipeline = $True, ValueFromPipelineByPropertyName = $true)]
        [Alias("Name")]
        [Alias("ServerName")]
        [string[]]$computername
    )
    
    BEGIN 
    {
	    Write-Verbose "Ping de $($computername.count) hostname"
    }

    PROCESS
    {
        Write-Verbose "Ping de l'ordinateur $ComputerName"
        Test-Connection -ComputerName $computername -Count 1 -ErrorAction SilentlyContinue
    }

    END 
    {
	     Write-Verbose "Fin du traitement"
    }
}
```

- `ValueFromPipeline = $true` permet à la commande d'être appelé à la droite du pipeline
- `ValueFromPipelineByPropertyName = $true` permet à la commande de prendre comme valeur de paramètre, la propriété des objets reçu possédant le même nom (ou alias)

- Le bloc `begin` sera exécuté **une fois** au début
- Le bloc `process` sera exécuté autant de fois qu'il y a d'objets dans la collection envoyé dans le pipeline.
- Le bloc `end` sera exécuté **une fois** à la fin

## Retour de la fonction

Une fonction (ou un script) retournera indifférement:

- Tout objet qui sera pas enregistré dans une variable.
- Tout objet renvoyé par la commande [!badge target="blank" text="Write-Output"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/write-output?view=powershell-7.3).
- Tout objets renvoyé par le mot clé `return`

!!!warning
Le mot clé `return` mettra fin immédiatement à l'éxécution du script ou de la fonction dans lequel il est appelé.
!!!