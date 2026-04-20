---
visibility: hidden
---

# Solution Fonction

```powershell
function Convert-Taille
{
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true, Position=0)]
        [long]$Octets,

        [Parameter(Mandatory=$true, Position=1)]
        [ValidateSet("KB","MB","GB")]
        [string]$Unite
    )

    $resultat = switch ($Unite)
    {
        "KB" { [math]::Round($Octets / 1KB, 2) }
        "MB" { [math]::Round($Octets / 1MB, 2) }
        "GB" { [math]::Round($Octets / 1GB, 2) }
    }

    [PSCustomObject]@{
        ValeurOriginale = $Octets
        Unite           = $Unite
        Resultat        = $resultat
    }
}
```

# Solution Script

```powershell
param
(
    [Parameter(Mandatory = $false)]
    [switch]$JSON
)

Write-Verbose "Querying computer: $computer"
$OSInfo = Get-CimInstance -ComputerName $computer -Class win32_OperatingSystem

$DiskInfo = Get-Volume -DriveLetter C

$Output = [PSCustomObject]@{
    ComputerName         = $OSInfo.CSName
    OSVersion            = $OSInfo.Caption
    BuildOS              = $OSInfo.BuildNumber
    RamMemory            = $OSInfo.TotalVisibleMemorySize
    SystemDriveFreeSpace = (Convert-Octets -Octets $DiskInfo.SizeRemaining -Unite GB).Resultat
}

if ($JSON)
{
    $Output | ConvertTo-Json
}
else
{
    $Output
}
```

[!button variant="success" icon="arrow-left" text="Retourner à l'exercice"](exercice3.md)