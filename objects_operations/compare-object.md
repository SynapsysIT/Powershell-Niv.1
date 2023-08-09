---
order: 5
--- 

# Compare-Object

[!badge target="blank" text="Compare-Object"](https://learn.microsoft.com/fr-fr/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7.3) permet de comparer deux collections d'objets.


```powershell
$ProcessPreExecution = Get-Process
Start-Process Notepad
$ProcesPostExecution = Get-Process
Compare-Object -ReferenceObject $ProcessPreExecution -DifferenceObject $ProcesPostExecution
```

```text Output :icon-chevron-right:
InputObject                          SideIndicator
-----------                          -------------
System.Diagnostics.Process (Notepad) =>
```

Lorsque vous utilisez le paramètre `-PassThru` , le **type** de l’objet n’est pas modifié

```powershell
$ProcessPreExecution = Get-Process
Start-Process Notepad
$ProcesPostExecution = Get-Process
Compare-Object -ReferenceObject $ProcessPreExecution -DifferenceObject $ProcesPostExecution -Passthru
```

```text Output :icon-chevron-right: 
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     23     9,55      31,03       0,19   20268   1 Notepad
```