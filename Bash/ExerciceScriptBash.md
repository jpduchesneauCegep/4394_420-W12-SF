# Exercice - Script Bash


## Exercices pas-à-pas

### Espace disque


1- Nous allons d'abord faire un script  Bash qui va nous permettre de vérifier l'espace de chacune des partitions de votre disque dur.

- Nous allons d'abord vérifier le nom des partitions à partir de la commande df -H que vous avons déjà utilisé dans le travail pratique d'installation de Linux. 
```bash
$df -H
```
- Prenez en note, le nom du disque par exemple : /dev/sd
- Maintenant, créer le script Bash suivant à la racine de votre répertoire usager à l'aide de l'éditeur de texte de votre choix. Si vous ne savez pas lequel utilisé, utilisez nano : 
```bash
$nano espace.sh
```

    Nous donnons ici l'extension  .sh au fichier. On le fait par convention pour indiquer que c'est un script Shell, mais ce n'est pas une obligation. 

    à la première ligne du script, n'oubliez pas de préciser le shebang: 

```bash
#!/bin/bash
Fichier="espaceDisque.txt"

date >> $Fichier
df -H | grep /dev/sd >> $Fichier

cat $Fichier
```
- Sauvegardez votre fichier en tapant sur Crtl+X et répondez Yes
- Faite la commande suivante pour rendre le script Bash exécutable : 

```bash
$chmod u+x espace.sh
#Vérifier les droits d'exécution sur le fichier :
$ls -l
# et maintenant, pour exécuter votre script Bash :
./espace.sh
# Vérifier la présence du nouveau fichier "espaceDisque.txt":
ls -l
```
Question 1 : Expliquer chaque ligne de votre script.

Question 2 : Qu'est-ce qui arrive si vous exécutez plusieurs fois le script ?

Question 3 : Qu'elle est l'intérêt d'utiliser ce script plutôt que la commande df -H régulièrement ?




### read : demander une saisie


Vous pouvez demander à l'utilisateur de saisir du texte avec la commande read. Ce texte sera immédiatement stocké dans une variable.

La commande read propose plusieurs options intéressantes. La façon la plus simple de l'utiliser est d'indiquer le nom de la variable dans laquelle le message saisi sera stocké :
```bash
read nomvariable
```
Exemple en ligne de commande, à modifier avec vos informations : 
```bash
jpduches@DFCSAE-95871-JPDUCHESNEAU:~$ read nom
"Jean-Pierre Duchesneau"
jpduches@DFCSAE-95871-JPDUCHESNEAU:~$ echo "Bonjour $nom !"
Bonjour "Jean-Pierre Duchesneau" !
jpduches@DFCSAE-95871-JPDUCHESNEAU:~$
```
Créons un script bonjour.sh pour qu'il nous demande notre nom puis qu’il nous l'affiche :
```bash
nano bonjour.sh
```
Contenu du script : 
```bash
#!/bin/bash

read nom
echo "Bonjour $nom !"
```
***Attention, suivez les étapes vues au point précédent pour les droits et lancez le script.***

Lorsque vous lancez ce script, rien ne s'affiche, mais si vous tapez du texte (votre nom, par exemple) le résultat va s'afficher.

![Exécution du script par le professeur](images/script2.jpg)


On peut demander de saisir autant de variables d'affilée que l'on souhaite. Voici un exemple de ce qu'il est possible de faire :


```bash
#!/bin/bash

read nom prenom
echo "Bonjour $nom $prenom !"
```


On est d'accord, ça manque d'informatique c'est ce que vas permettre l'option -p : afficher un message de prompt : 
```bash
#!/bin/bash


read -p 'Entrez votre nom : " nom 
echo "Bonjour $nom !"
```


**Exécution de débogage**


Plus tard, vous ferez probablement de gros scripts et risquerez de rencontrer des bogues. Il faut donc dès à présent que vous sachiez comment déboguer un script.


Il faut l'exécuter comme ceci :


```bash
$bash -x espace.sh
```
On appelle en fait directement le programme bas et on lui ajoute en paramètre un -x (pour lancer le mode débogage) ainsi que le nom de notre script à déboguer.


Le Shell affiche alors le détail de l'exécution de notre script, ce qui peut nous aider à retrouver la cause de nos erreurs.



## A vous de jouer, réaliser les scripts suivants

Référez-vous à la théorie présentée par le professeur.

**Attention : n'oubliez pas de donner les droits d'exécution sur les scripts 
(chmod a+x)**


1- De quelle manière peut-on écrire un code qui permette d'afficher à l'écran : 


    Bonjour à tous, je m'appelle {Votre prénom}


     Je me pratique pour Bash




2- Quelle est la commande à taper pour demander à l'utilisateur de rentrer 
son nom et de le stocker dans la variable NAME ?




3- Quelle est la commande à taper pour afficher à l'écran : "Bonjour NOM, tu 
as AGE ans." en remplaçant NOM et AGE par les valeurs entrées par l'utilisateur 
?




4- Réalisation un compteur qui commencer au chiffre rentré par l'utilisateur 
et qui descend jusqu'à 1.




6- Créer un jeu qui permet à l'utilisateur de deviner un chiffre généré par le 
script entre 1 et 50. À chaque fois que l'utilisateur entre un chiffre, le 
script lui indique si le chiffre à trouver est supérieur ou inférieur à celui 
qu'il a entré, etc.




7- Réaliser un script bas qui permet de vérifier si l'utilisateur a bien 
saisi des arguments, et si les fichiers placés en arguments existent bien.




8- Réaliser un script faisant appel à une fonction qui prend comme paramètre 
un login d'un user et vérifie si l'utilisateur existe déjà.




**Fin de l'exercice**

