# Exercice  - Script bash (Solutionnaire)

## Réaliser les scripts suivants

** Attention : n'oublier pas de donner les droits d'exécution sur les script (chmod a+x)**

1- De quelle manière peut-on écrire un code qui permette d'afficher à l'écran :

```bash
#!/bin/bash
echo "Bonjour à tous, je m'appelle {Votre prénom}"
echo "Je me pratique pour bash"
```

2- Quelle est la commande à taper pour demander à l'utilisateur de rentrer son nom et de le stocker dans la variable NAME ?

```bash
#!/bin/bash
read -p "Taper votre nom svp ?" NAME
```

3- Quelle est la commande à taper pour afficher à l'écran : "Bonjour NOM, tu as AGE ans." en remplaçant NOM et AGE par les valeurs entrées par l'utilisateur ?

```bash
#!/bin/bash
read -p "Quel est ton nom : " NOM
read -p "Donne-nous ton age : " AGE
echo "Bonjour  ${NOM}, tu as $AGE ans!"
```

4- Réalisation un compteur  qui commencer au chiffre rentré par l'utilisateur et qui descend jusqu'à 1.

```bash
#!/bin/bash
#Établissement du compteur

read  -p "Entrez le nombre de départ : " NOMBRE

echo "Vous avez choisit $NOMBRE comme valeur de départ."

while [ $NOMBRE -gt 0 ]
do
echo $NOMBRE
NOMBRE=$(($NOMBRE-1))

done
echo "Voici, votre compteur à terminé son travail"
```

5- Crer un jeu qui permet à l'utilisateur de deviner un chiffre généré par le script entre 1 et 50. A chaque fois que l'utilisateur entre un chiffre, le script lui indique si le chiffre à trouver est supérieur ou inférieur à celui qu'il a entré, etc…

```bash
#!/bin/bash

MIN=1
MAX=50

NOMBRE=$[($RANDOM % ($[$MAX - $MIN] +1)) + $MIN]
#Compexité des nombres. Présence de la fonction RANDOM.
CHIFFRE=0 
#En initialisant la variable è 0, on fait en sorte
# que bash interprête  CHIFFRE comme une valeur numérique.


read -r CHIFFRE;

while [ $CHIFFRE -ne $NOMBRE ]
do
    echo "Le chiffre a trouver est compris entre $MIN et $MAX, Trouvez-le !"
    read CHIFFRE
    if [ $CHIFFRE -lt $NOMBRE ]
    then
        echo "Le chiffre est plus grand"
        
    elif [ $CHIFFRE -gt $NOMBRE ]
    then
        echo "Le chiffre est plus petit"
    fi
done
echo "Trouvé !! le chiffre etait: $NOMBRE"
```

6- Réaliser un script bash qui permet de vérifier si l'utilisateur a bien saisi des arguments, et si les fichiers placés en arguments existent bien.

```bash
#!/bin/bash
#Recuperation des noms des fichiers
FICHIERS=$@
NOMBRE_ARGUMENTS=$#

#Verification que l'utilisateur a bien saisi des arguments
function verif_arguments(){
        if [ $NOMBRE_ARGUMENTS -eq 0 ]
        then
                echo "Attention, vous n'avez pas saisi les noms des fichiers"
                exit 2
        fi
}
#Verification que le fichier n'existe pas déjà
function verif_fichier_existe(){
        for FICHIER in $FICHIERS
        do

                ls $FICHIER 2> /dev/null

                if [ $? -eq 0 ]
                then
                        echo "Le fichier $FICHIER existe"
                else
                        echo "Le fichier $FICHIER n'existe pas"
                fi
        done
}

verif_arguments
verif_fichier_existe $FICHIERS
```

7- Réaliser un script faisant appel a une fonction qui prend comme paramètre un login d'un user et vérifie si l'utilisateur existe déjà.

```bash
#!/bin/bash
function saisirUser { 
    echo "Saisir l'utilisateur" 
    read -r util 
} 
#Au sein de la commande grep, l'accent circonflexe ^ et le symbole dollar $ sont des méta-caractères correspondant respectivement à une chaîne vide au début et en fin de ligne. 
function verifyUser { 
    if grep "^$util:" /etc/passwd > /dev/null; 
    then 
        echo "L'utilisateur existe" 
    else 
        echo "L'utilisateur n'existe pas" 
    fi 
    
} 


 saisirUSer
 verifyUser 
 
```


**Fin de l'exercice **
