---
order: 4
--- 

# Exportation / Importation

## Fichier brut

### :icon-arrow-right: Out-File

[!badge target="blank" text="Out-File"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/out-file?view=powershell-7.3) permet d'exporter dans un fichier **brut** le contenu du pipeline.

```powershell
Get-EventLog -LogName Application -Newest 10 | Out-File Log.txt
```

### :icon-arrow-left: Get-Content

[!badge target="blank" text="Get-Content"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.3) permet de faire l'action inverse et d'importer le contenu d'un fichier brut

```powershell
Get-Content C:\Windows\System32\drivers\etc\hosts
```

---

## JSON

### :icon-arrow-right: ConvertTo-Json

[!badge target="blank" text="ConvertTo-Json"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.3) permet de convertir le contenu du pipeline au format JSON

```powershell
Get-Service | ConvertTo-Json | Out-File services.json
```

### :icon-arrow-left: ConvertFrom-Json

[!badge target="blank" text="ConvertFrom-Json"](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-7.3) permet de faire l'action inverse et de convertir la syntaxe Json en objet powershell.

!!!warning
[!badge target="blank" text="ConvertFrom-Json"](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-7.3) ne prend pas de fichier en entrée mais un objet de type `string` respectant la syntaxe Json. Cet objet pourra être obtenu depuis un fichier (`Get-Content`), une RestAPI (`Invoke-WebRequest`), ...
!!!

---
## CSV

### :icon-arrow-right: Export-CSV

[!badge target="blank" text="Export-CSV"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-7.3) permet d'exporter le contenu du pipeline dans un fichier CSV

```powershell
Get-Process | Export-Csv -Path .\Processes.csv 
```

!!!
Le paramètre `-IncludeTypeInformation` permet de rajouter un entête au fichier pour conserver le type de l'objet lors de son importation
!!!

!!!
Le paramètre `-Delimiter` permet précisier le caractère de séparation `,` , `;`... Le même devra être choisi lors de l'importation.
!!!

### :icon-arrow-left: Import CSV

[!badge target="blank" text="Import-Csv"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/import-csv?view=powershell-7.3) permet de faire l'action inverse et d'importe le contenu d'un fichier CSV

```powershell
Import-CSV -Path .\Processes.csv 
```

---

## XML 

### :icon-arrow-right: Export-CliXML

[!badge target="blank" text="Export-XML"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-7.3) pPermet d’exporter le contenu du pipeline dans un fichier XML. En concervant le type, les propriétés et les méthodes de l’objet.

```powershell
Get-Process | Export-Clixml .\Processes.xml
```

### :icon-arrow-left: Import-CliXML

[!badge target="blank" text="Import-CliXML"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-7.3) permet de faire l'action inverse et d'importe le contenu d'un fichier XML

```powershell
Import-Clixml .\Processes.xml
```
