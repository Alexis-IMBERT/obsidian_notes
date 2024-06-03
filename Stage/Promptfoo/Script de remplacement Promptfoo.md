---
tags:
  - promptfoo
  - 6108
---
https://redmine.teklia.com/issues/6108#note-37
## Rappel des objectif :

Pouvoir tester ensemble de model LLM multimodaux, prompt et image de manière efficace et simple.

## Proposition de workflow :

En entrée :
* Dans un dossier avoir un prompt par fichier
* La liste des modèles à tester, qui peut être sous la forme de plusieurs script à executer
* La liste des images à traiter, avec (ou pas) les tags correspondant à la vérité terrain
* entrée possible pour les images :
	* ID d'un dossier arkindex 
	  > le script, s'occuperait de télécharger les images et les tags
	* Fichier (json/csv) contenant : 
		* l'url
		* (un identifiant unique de l'image,) 
		* la liste des tags de la vérité terrain
	* Fichier pour la vérité terrain (idantifiant de l'image / chemin vers l'image) + vérité terrain + dossier des images préalablement téléchargé
* La liste et les fonction permettant d'évaluer le résultat de chaque experience

  

En sortie :
* un fichier (json/csv) qui contient pour chaque expérience
	* l'identifiant de l'image
	* chemin / url de l'image
	* le prompt utilisé
	* le modèle utilisé
	* la réponse du modèle
	* Le / les score obtenue
A réfléchir : 
* 1 fichier de sortie total :
	* Inconvéniant multiple :
		* on ne voit pas les résultat avant la fin du process
		* Stock de plus en plus de mémoire RAM
* 1 fichier de sortie par inférence 
	* Avantage :
		* on peut voir l'avancé du process rapidement
	* inconvéniant
		* Génère beaucoup de fichier => stock plus de mémoire HDD 
* 1 fichier de sortie par modèle:
	* Compromis ?

## D'un point de vue technique
* On peut faire un script python par modèle qui admet en entrée :
	* la liste des images / le dossier ou elle sont stocké
	* la liste des prompt / le dossier ou ils sont stocké
	* la méthode d'évaluation ? 
		* ce qui implique d'avoir aussi la ground truth
* Pour chaque modèle on peut essayer de les lancer dans un subprocess différent
	* Avantage : 
		* avoir des environnement python différent => éviter des problème de compatibilité de librairie
	* inconvénient :
		* Les entrée et les sorties du script
		  > Pour contourner ce problème on pourrait load les images et les prompts dans ces scripts, puis éventuellement faire l'évalation et directement générer le fichier de sortie
		  * Question : est ce que l'évaluation se fait à la sortie du modèle (juste après l'inférence) ou dans un second temps ?
choix dans [[2024-05-27]]