---
tags:
  - SIFED
  - promptfoo
  - Poster
  - publication
---
https://redmine.teklia.com/issues/7239

***
Poster à faire pour le 6 juin + temps d'impression

Sujet : 
> Le Musée national des Arts asiatiques - Guimet (MNAAG) et Teklia se sont associés dans le cadre du projet HikarIA pour la mise en valeur de photographies patrimoniales grâce à l’intelligence artificielle et le développement d’outils d’indexation automatisée de photographies anciennes. Au cœur du projet se trouve une collection exceptionnelle de plus de 20 000 photographies du Japon au XIXe et au début du XXe siècle, pour la plupart collectées par le Dr. Joseph Dubois et acquises par le Musée Guimet en 2007. Le but du projet est d’adapter des modèles d’IA à l’analyse de ces photographies et de les mettre en œuvre pour produire des données fiables sur l’iconographie du corpus. Images et métadonnées seront ensuite mises en ligne sur une plateforme d’exploration du corpus librement accessible.
Dans cette communication, nous comparons différents modèles de langage multimodaux afin de décrire automatiquement ces photographies anciennes. Ces modèles prennent une image et une instruction (prompt) en entrée, et génèrent une description de l'image en sortie. De nombreux modèles de ce type ont été proposés ces dernières années, tels que LLaVA, BackLLaVA, BLIP, CLIP et MobileCLIP.
Dans un premier temps, nous comparons différentes stratégies de prompt pour adapter ces modèles sans ré-entraînement. Puis, nous évaluons l'impact du fine-tuning sur les performances des modèles. Nous discutons également des besoins en ressources de calcul ainsi que de la quantité de données nécessaire. Enfin, nous présentons quelques bibliothèques d'évaluation automatisées de LLMs, telles que promptfoo et benchprompt, ainsi que les métriques d'évaluation pertinentes pour évaluer la sortie d'une combinaison modèle/prompt.

- Commencer le poster SIFED
	- Faire un plan (penser aux illustrations)
	- Faire le text & traduction en anglais
	- Mettre en page
	- Chercher un imprimeur

# Plan :
Pour l'intro la structure est ok

1. Intro
   1.1 Données: mettre une image d'une photographie (:warning: data sans s) 
   1.2. Objectif du projet: faire un schéma de l'inteface (utilisateur tape un mot clé, l'interface affiche les images qui contiennent ce mot clé)

Pour la partie centrale, je pense que tu devrais plutôt te concentrer sur les expés, pas sur Promptfoo (qui est juste un outil pour comparer efficacement des expés)

2. LLM prompt experiments for image description
   2.1 Task description (schéma: image + model + prompt = liste de tags)
   2.2 Models (liste + description rapide)
   2.3 Prompts (décire les stratégies de prompt: description libre ou liste des tags possible)
   2.3 Experiments with Promptfoo (décrire fonctionnement + exemple de l'interface)
   2.4 Results (un tableau)

Pour la conclusion:
* Limites des modèles actuels + solutions potentielles à explorer (c'est presque le plus important : l'intérêt de SIFED c'est d'échanger sur les limites actuelles, tu auras sûrement des retours/pistes intéressants)
* Lien vers le git (QR code)

Sur tout le poster : mettre plein de schéma/illustrations/table et peu de texte (ou alors des bullet points)
