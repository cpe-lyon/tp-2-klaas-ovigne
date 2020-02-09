OVIGNE Adrien

KLAAS Guillaume

equipe 15


VAR ENVIRONNEMENT

1 printenv PATH

2 HOME

3 **LANG**: langue utilisée pr communiquer avec l'utilisateur. **PWD**: affiche le repertoire courant **OLDPWD**: affiche l'ancien repertoire courant **SHELL**:  montre le chemin de l'interpreteur shell utilisé par defaut **_**:

4 MY_VAR="test"
	echo $MY_VAR

5 **bash** nous place dans un nvx shell, la variable locale MY\_VAR n'y existe pas. un **echo $MY\_VAR** n'affiche donc rien apres avoir fait **exit** on revien dans le shell où MY\_VAR existe

6 **export MY_VAR="test_env"** et ca marche même ds l'autre shell

7 **export NOMS="KLAAS OVIGNE" ; printenv NOMS**

8 **echo Bonjour à vous deux, $NOMS!**
 
9 **unset** supprime la variable.
 
10 **echo \$HOME = $HOME** le "\" permet d'afficher "HOME" au lieu du contenu de la variable d'environnement

EXOS:

pour ajouter script a la variable d'environnement PATH:**export PATH="$HOME/script:$PATH"**

pour executer : **./nomduscript.sh**

# testpwd.sh

#!/bin/bash
read -p 'Entre ton mdp:' -s mdp
if [ $mdp = "abcd" ]; then
	echo "Bon mot de passe"
else
	echo "Mauvais mot de passe"
fi

# isReal.sh

#!/bin/bash
function is_number()

{
re='^[+-]?[0-9]+([.][0-9]+)?$'
if ! [[ $1 =~ $re ]] ; then
	return 1
else
	return 0
fi
}

read -p 'entrez votre nombre' re

is_number $re
if [[ $? == 1 ]] ; then
echo non
else
echo oui
fi



# test_utilisateur.sh
#!/bin/bash
if [ $# = 0 ]; then
	echo "utilisation: $0 nom_utilisateur"
else
	id -u $1
	if [[$? = 1]]; then
		echo "utilisateur inexistant"
	else
		echo "utilisateur existant"
	fi
fi


# factorielle.sh
#!/bin/bash
i=0
read -p 'nb:' a
resultat=1
while [[ $i<$a ]]
	do
		i=$(($i + 1))
		resultat=$(($resultat*$i))
	done
echo $resultat

# leJustePrix.sh
#!/bin/bash
echo "BIENVENUE DANS LE JUSTE PRIX!!!!!"
echo "C'EST PARTIIIIIII !!!!!!"

read -p 'Quelle est votre proposition' proposition
MAX=1000
reel=$((RANDOM*(1+MAX)/32767))
while [[ $reel != $proposition ]]
	do
		if [[ $reel > $proposition ]]
			echo "Plus haut!"
		else
			echo "Plus bas!"
		fi
	read -p 'Quelle est votre proposition' proposition
	done
echo "ET C'EST GAGNÉ!!!"




# stats.sh

#!/bin/bash
function is_entier() {
	if [ $(($1%1)) -eq 0 ]; then
		return 1
	else
		return 0
	fi
}
min=$1
max=$1
total=$#
while (("$#")); do
	if [ $1 -lt 100 -a $1 -gt -100 ];then
		is_entier $1
		
		if [ $? -eq 1 ]; then
			somme=$((somme+$1))
			
	
			if [ $1 -gt $max ]
			then
				max=$1
			elif [ $1 -lt $min ]
			then
				min=$1
			fi
		else
			echo "non"
			
		
		fi
	else
		echo "Nombre pas conforme, veuillez recommencer"
		exit
	fi
	shift
done

moyenne=$(($somme/$total))

echo "moyenne : $moyenne"

echo " min : $min"
echo " max : $max"

