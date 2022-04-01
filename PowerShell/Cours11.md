# Système d'exploitation Cours 11 :

## 4 avril 2022

## Retour sur les Provider
```PowerShell
Get-PSProvider
Set-Location Env:
dir
Set-Location c:
```

## PSDrive
```PowerShell
Get-PSdrive
New-PSDrive SE filesystem 'C:\Users\usager\OneDrive - Cégep de Sainte-Foy\Cours\420-W12-SF-4394\Demo'
cd SE:
# dir or get-childitem or ls 
cd c:	
remove-psdrive SE
```
Voir : [New-PSDrive](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-7.2)
## Déclaration variable :
```PowerShell
$test = "PowerShell"
Write-Host $test
$nom = "Duchesneau"
$prenom = "Jean-Pierre"
Write-Host $prenom $nom
echo "$prenom $nom écrit du $test"
```
Voir : [about_Variables](https://docs.microsoft.com/fr-fr/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-7.2)

## Création d'une fonction :
```PowerShell
Get-Date  | Get-Member
function MaDate
{
    (Get-Date).ToShortDateString()
}
# Appelé la fonction MaDate
MaDate
$LaDate= MaDate
Write-Host $LaDate
Set-Location function:
#ls ou dir ou gci ou Get-ChildItem
gci
```
Voir : [Get-Member](https://docs.microsoft.com/fr-fr/powershell/scripting/samples/viewing-object-structure--get-member-?view=powershell-7.2) - [Fonctions](https://docs.microsoft.com/fr-fr/powershell/scripting/learn/ps101/09-functions?view=powershell-7.2)

## Écrire dans un fichier

```PowerShell
gci | Out-File ".\Monfichier.txt"
Get-Process | Export-csv -path ./export.csv 
Get-ChildItem
Get-Content Monfichier.txt
Get-Content export.csv
```
Voir : [Export-CSV](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-7.2)
## Lire un fichier exemple 1

```PowerShell
Clear-Host

$EmplacementFichier = [string]
$EmplacementFichier = "Demo:\export.csv"
$MonFichier = Get-Content $EmplacementFichier

foreach ($UneLigne in $MonFichire) {
    Write-Host $UneLigne
}
```
Voir : [about-Foreach](https://docs.microsoft.com/fr-fr/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-7.2)

## Lire un fichier exemple 2

```PowerShell
Clear-Host


$MonFichier = Get-Content nom.csv

foreach ($UneLigne in $MonFichire) {
    Write-Host $UneLigne
}
```
## Exemple jouer avec le contenu
```PowerShell
Clear-Host

$MonFichier = Get-Content nom.csv
$MonFichier | Get-Member
foreach ($UneLigne in $MonFichier) {
    Write-Host $UneLigne.split(';')[0]
    Write-Host $UneLigne.split(';')[1]
    Write-Host $UneLigne.split(';')[2]
    Write-Host "============"
}
```
Voir : [about_split](https://docs.microsoft.com/fr-fr/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-7.2)
