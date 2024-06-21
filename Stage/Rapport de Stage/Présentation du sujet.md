Le stage s'articule autour d'un projet de recherche réalisé avec le
musée Guimet[^1].

Contexte général
----------------

En 2022, le ministère de la Culture lance un appel à projet
\"Numérisation du patrimoine et de l'architecture\" dans le cadre du
plan France Relance, France 2030[^2]. Le projet a pour but de \"soutenir
les initiatives de numérisation du patrimoine et de l'architecture, que
ce soit à des fins de préservation ou dans le but de proposer de
nouvelles offres culturelles innovantes pour un plus large public\".

Dans le cadre de cet appel à projet, le Musée national des Arts
asiatiques - Guimet (MNAAG) et Teklia se sont associés pour proposer un
projet visant à développer une plateforme basée sur l'intelligence
artificielle pour l'analyse et l'exploration des collections
photographiques patrimoniales. Le projet a été nommé Yokohama [^3].

Objectif du projet Yokohama 
---------------------------

Le musée Guimet rassemble une collection abondante d'images anciennes et
modernes. L'achat de la collection du Dr. Joseph Dubois en 2007 a été un
moment décisif. Cet ensemble remarquable de 280 albums, qui relate le
Japon de 1850 à 1920, propose une perspective captivante sur cette
période de l'histoire au Japon. Grâce à ses 15 000 clichés, la
collection Dubois constitue un véritable trésor. Chaque image relate une
histoire, que ce soit des paysages, des scènes de vie quotidienne ou des
portraits saisissants[^4]. Le musée Guimet collabore avec Teklia afin de
maximiser l'utilisation de ce trésor en exploitant la vision par
ordinateur et de l'apprentissage profond. Ce projet innovant s'engage à
bouleverser la recherche sur le Japon et à créer des outils d'étude et
de diffusion nouveaux pour exploiter pleinement ce trésor d'histoire.

Pour résumer, le Musée Guimet et la collection Dubois proposent une
opportunité exceptionnelle de faire un voyage dans le temps et de
découvrir le Japon d'autrefois.

Les objectifs du stage
----------------------

![Le modèle, LLaVA v1.6 34B, prend une image, ici l'imag
et une instruction de l'utilisateur en entrée, et génère un texte en
sortie. Ici, il génère une description de la
photographie.](images/Model.png)

Le but du projet est de faire de la description et de l'indexation
automatique d'images. Afin de réaliser cette tâche, nous nous
intéressons aux grands modèles de langages multimodaux. Dans la figure
[1](#fig:schema-explicatif)
reference="fig:schema-explicatif"}, nous pouvons observer le schéma
typique du modèle que nous allons utiliser. Nous testons différentes
combinaisons de modèles et de prompts pour obtenir la description la
plus précise possible de chaque image.

Il existe de nombreux modèles pour réaliser cette tâche, nous allons
voir plusieurs dans la suite du rapport. Chaque modèle est très sensible
au prompt d'entrée. Nous devons donc tester plusieurs prompts pour
chaque modèle, ce qui représente un nombre d'expériences très important.

Afin de réaliser cette tâche, je vais tester des outils de comparaison
de LLM, qui simplifieront cette tâche de comparaison. Par exemple,
l'outil Promptfoo[^5] qui permet de comparer les performances de
différents modèles de LLM.

L'idée à terme étant de l'intégrer dans les pipelines de Teklia.

[^1]: <https://www.guimet.fr/>

[^2]: [https://www.culture.gouv.fr/Presse/Communiques-de-presse/Plan-France-Relance-2030-lancement-de-l-appel-a-projets-Numérisation-du-patrimoine-et-de-l-architecture](https://www.culture.gouv.fr/Presse/Communiques-de-presse/Plan-France-Relance-2030-lancement-de-l-appel-a-projets-Numérisation-du-patrimoine-et-de-l-architecture)

[^3]: <https://Teklia.com/fr/blog/2023-guimet-Teklia/>

[^4]: Exemples de photographies de la collection Dubois en annexe : ...

[^5]: <https://github.com/promptfoo/promptfoo>