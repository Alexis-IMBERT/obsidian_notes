[[2024-05-20]], [[2024-05-21]], [[2024-05-22]], [[2024-05-23]], [[2024-05-24]]

* Pour le workshop : lire https://redmine.teklia.com/issues/7172 1/2 journée
* Au cas ou :
	* reprendre la tache de mélodie de tester les modèles pour la reconnaissance de text https://redmine.teklia.com/issues/6378




# Bilan de la semaine :
 * Recherche de nouveaux modèles
 * Promptfoo :
	 * implémentation dans promptfoo
		 * LLaVA LLAMA 3
		 * Google Paligemma
		 * Idefics 2
		 * Moondream2
		 * LLavA 7B, 13B
		 * Clip
		 * Blip
	 * Lancement d'une nouvelle expérience
		 * 8800 inférence au total
			 * 4 prompt
			 * 275 images
			 * 8 modèles testé
		 * 68h => ~27s / inférence
	 * réflexion sur comment améliorer le temps d'execution 
		 * On abandonne promptfoo
		 * Creation d'un nouveau script qui permet de charge le modèle puis de faire toute les inférence d'un coup
 * Avancé sur le poster SIFED
 * préparation du workshop de la semaine prochaine
