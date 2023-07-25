# Pipeline & Objets

## Language Objet

* Contrairement à **Batch** ou **Bash** qui sont des langages dit « textes », **Powershell est un langage objet**.

* Sous PowerShell, chaque commande renverra un objet d’un type précis possédant ses **propriétés** et ses **méthodes**.

![](../assets/objets.png)

## Le Pipeline

* Le pipeline, symbolisée par le caractère **|** ( ++altgr+6++ ) permet de **chainer** plusieurs commandes entre elles.

* Autrement dit, la **sortie** d'une commande correspond à l'**entrée** de la suivante.

* Les valeurs des paramètres de la deuxième commande lui sont fourni par la première commande.


```powershell
Get-Process  -Name notepad
Stop-Process -Name notepad
```

```powershell
Get-Process  -Name notepad | Stop-Process
```

