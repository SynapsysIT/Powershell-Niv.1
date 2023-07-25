---
order: 9
--- 

# Select-Object

[!badge target="blank" text="Select-Object"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.3) permet de ne sélectionner que certaines propriétés de l'objet ou d'en créer de nouvelles.

```powershell
Get-Service | Select-Object Name, Status, StartType,CanStop
```

___
## Afficher l'ensemble des propriétés

`Select-Object *` permettra de renvoyer l'intégralité des propriétés et leur valeurs d'un objet, même si la commande ne les renvoient pas de base.

```powershell
Get-Disk -Number 0
```

```text Output ❱ 

Number Friendly Name                      Serial Number                    HealthStatus         OperationalStatus      Total Size Partition
                                                                                                                                  Style
------ -------------                      -------------                    ------------         -----------------      ---------- ----------
0      Samsung SSD 860 EVO M.2 1TB        S5GENJ0N808902D                  Healthy              Online                  931.51 GB GPT


```


```powershell
Get-Disk -Number 0 | Select-Object *
```

```text Output ❱ 

DiskNumber            : 0
PartitionStyle        : GPT
ProvisioningType      : Fixed
OperationalStatus     : Online
HealthStatus          : Healthy
BusType               : RAID
UniqueIdFormat        : FCPH Name
OfflineReason         : 
ObjectId              : {1}\\HULK\root/Microsoft/Windows/Storage/Providers_v2\WSP_Disk.ObjectId="{52598d39-5131-11ed-9742-806e6f6e6963}:DI:\\?\scsi#disk&ven_samsung&prod_ssd#4&632e028&0&000000#{53f56307-b6bf-11d0-94f2-00a0c91efb8b}"
PassThroughClass      : 
PassThroughIds        : 
PassThroughNamespace  : 
PassThroughServer     : 
UniqueId              : 5002538E30834143
AdapterSerialNumber   : 
AllocatedSize         : 1000203837440
BootFromDisk          : False
FirmwareVersion       : RVT24B6Q
FriendlyName          : Samsung SSD 860 EVO M.2 1TB
Guid                  : {0a51a6af-cb23-42dc-895c-a765d01d9893}
IsBoot                : False
IsClustered           : False
IsHighlyAvailable     : False
IsOffline             : False
IsReadOnly            : False
IsScaleOut            : False
IsSystem              : False
LargestFreeExtent     : 1048576
Location              : Integrated : Bus 0 : Device 23 : Function 0 : Adapter 0 : Port 0 : Target 0 : LUN 0
LogicalSectorSize     : 512
Manufacturer          : 
Model                 : Samsung SSD 860 EVO M.2 1TB
Number                : 0
NumberOfPartitions    : 3
Path                  : \\?\scsi#disk&ven_samsung&prod_ssd#4&632e028&0&000000#{53f56307-b6bf-11d0-94f2-00a0c91efb8b}
PhysicalSectorSize    : 512
SerialNumber          : S5GENJ0N808902D
Signature             : 
Size                  : 1000204886016
PSComputerName        : 
CimClass              : ROOT/Microsoft/Windows/Storage┬á: MSFT_Disk
CimInstanceProperties : {ObjectId, PassThroughClass, PassThroughIds, PassThroughNamespaceÔÇª}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties

```


## Créer une propriétés custom

```powershell
Get-ChildItem | Select-Object Name,@{ Name = "Taille en MB" ; expression={ ($_.Length/1MB) } }
```

## Limiter un résultat

`Select-Object` possède des paramètres `-First` et -`-Last` pour ne récupérer qu'un certain nombres d'objets dans une collection.

```powershell
Get-Service | Select-Object -First 10
```

```powershell
Get-Service | Select-Object -Last 10
```

