---
tags:
  - review
---
 [Papier](https://cloud.teklia.com/index.php/apps/onlyoffice/s/YFq4mDGy54ZcGLi?fileId=476136)

Neurips : prestigieuse conférence de deeplearning 

# Abstract 
#ATR
Reconnaissance de ligne du #Latin, #Chinoix " #ciphered " #scene-texte 
Fonctionnement du modèle : Traitement parallèle de ligne 
# introduction
Contribution : 
 - transformer base character detection approach for line recogningtion
# Related work
Text line recognition for latin
1. model de markov caché
2. #CTC loss
	1. #CNN & #RNN
		1. #LSTM
		2. Multimodal LSTM
3. transformers
	1. could be complement to CTC
	2. #Cross-Attention
	3. #Autoregressive decoders : different token scale : car -> sub word

Text line recognition for chinese :
1. #YOLO inspiration 

Text line for cipher :
1. LSTM
2. Transformer based method 
3. Segmented symbol
4. K means
5. Probleme peut de donnée pour chaque langage

Language Model :
like TrOCR, DtrOCR
1. Probleme : grand nombre de ligne necessaire pour 

# Methods
## Synthetic data pre-trained
Création des données synthetics, + maskage vertical (toute la ligne) & horizontal (partiel) utilisation de plusieurs font
> placement des figure je trouves pas toujours pertinent : figure 2 par rapport à la citation
> le text de préentrainement ne soit que du laitn pas de chinoix
> Mais ca semble bien marché pour la suite
> Précision dans la création du dataset

Utilisation de l'algorithme hongrois

> Ils sont précis dans la structure du model
> 


### Inference speed :
> seams to be fast
> Dans les résultats manque peut etre d'un tableau de comparaison global : (Faster DANS )