---
tags:
  - MLBrief
  - ENS
  - Softmax
  - self-Training
  - sample-selection-bias
  - workshop
  - article
---
## Résumé :
Quand nous possédons un grand nombre de données, il est compliqué de pouvoir labelliser l'ensemble des données. On peut alors appliquer des algorithmes d'auto-entrainement qui vont donner des pseudo-labels aux données non labellisées quand le modèle a une confiance suffisante.

Le problème, c'est que le score de confiance actuellement utilisé est la softmax qui a tendance à être trop confiante (même avec des faux positifs). L'article propose donc un nouveau score de confiance : la T-similiraté. 

Le problème vient principalement du fait de la pertinence des données labellisé de base : des biais que les données présentent, en effet, les données labellisées ne représentent pas forcément l'ensemble des données labellisé, il peut exister une différence de loi de distribution entre les données labellisées et les données non labellisées. Pour prouver l'efficacité de ce nouveau score de confiance, plusieurs expériences vont être réalisées sur plusieurs jeux de données (répétés avec 9 seeds différente) avec des données Indépendante et Identiquement Distribué (IID) et des données biaisées (SSB).

L'idée est de donner le score de similarité d'un exemple non étiqueté à partir de plusieurs résultats de classifieurs divers. Si les classifieurs sont d'accord dans l'ensemble, alors le score de similarité sera élevé. Si les classifieurs ne sont pas d'accord, alors le score de similarité sera faible.

Les résultats montrent bien que quand les données sont IID parmi toutes les données, la T-similiraté n'a pas beaucoup d'utilité par rapport à la softmax. Les résultats entre la softmax et la T-sim sont proches, la softmax peut être légèrement meilleure. Par contre, quand les données sont biaisées, alors la softmax admet des résultats d'apprentissage bien inférieurs par rapport à la T-similarité.

![[2310.14814v4.pdf]]

https://arxiv.org/html/2310.14814v4

Self trainning : semi supervised learning (SSL)
-> assigner des pseudo label aux valeur non labélisé dans lesquelle le modèles donne une confiance suffisante
-> le sueil peut etre fixe OU changé à chaque itération -> **curriculum learning**
=> problème quand le classifier est biaisé ou quand la loi de distribution change entre les données labéllisé et non labélisé


Softmax often use but known to be overconfident (even for wrong prediction)

So creation of a T-similarity
	- comme un ensemble de plusieurs prédiction et si la majorité est d'accord alors c'est bon
[Lien du code](https://github.com/ambroiseodt/tsim)


(1) How to rank unlabeled data to reflect their difficulty for classification? 
 * less documented
(2) How to select the threshold for pseudo-labeling at each iteration?
 - well documented : (Feofanov et al.,, [2019](https://arxiv.org/html/2310.14814v4#bib.bib19); Cascante-Bonilla et al.,, [2021](https://arxiv.org/html/2310.14814v4#bib.bib9); Zhang et al.,, [2021](https://arxiv.org/html/2310.14814v4#bib.bib63))
 
sample selection bias (SSB)
disparité de distribution entre les données étiquetée et les données non étiqueté 
 Formalisé par Heckman (1974), 
 Dans le contexte de la classification, la SSB a été correctement définie par Zadrozny (2004)
 
We denote this challenging scenario by SSL + SSB.

Diversité de l'ensemble 
	dans les année précédente la diversité a été créer par le bagging
	>To this end, Liu and Yao, (1999), introduced a mixture of expert that are diversified through the negative correlation loss that forces a trade-off between specialization and cooperation of the experts
	
#### Datasets.

We consider 13 publicly available SSL datasets with various data modalities: 
* biological data for 
	* Cod-RNA (Chang and Lin,, [2011](https://arxiv.org/html/2310.14814v4#bib.bib10)), 
	* DNA (Chang and Lin,, [2011](https://arxiv.org/html/2310.14814v4#bib.bib10)), 
	* Protein (Dua and Graff,, [2017](https://arxiv.org/html/2310.14814v4#bib.bib17)), 
	* Splice (Dua and Graff,, [2017](https://arxiv.org/html/2310.14814v4#bib.bib17)); 
* images for 
	* COIL-20 (Nene et al.,, [1996](https://arxiv.org/html/2310.14814v4#bib.bib49)), 
	* Digits (Pedregosa et al.,, [2011](https://arxiv.org/html/2310.14814v4#bib.bib52)), 
	* Mnist (Lecun et al.,, [1998](https://arxiv.org/html/2310.14814v4#bib.bib41)); 
* tabular data for 
	* DryBean (Dua and Graff,, [2017](https://arxiv.org/html/2310.14814v4#bib.bib17)), 
	* Mushrooms (Dua and Graff,, [2017](https://arxiv.org/html/2310.14814v4#bib.bib17)), 
	* Phishing (Chang and Lin,, [2011](https://arxiv.org/html/2310.14814v4#bib.bib10)), 
	* Rice (Dua and Graff,, [2017](https://arxiv.org/html/2310.14814v4#bib.bib17)), 
	* Svmguide1 (Chang and Lin,, [2011](https://arxiv.org/html/2310.14814v4#bib.bib10)); t
* ime series for 
	* HAR (Dua and Graff,, [2017](https://arxiv.org/html/2310.14814v4#bib.bib17)). 
* More details can be found in Appendix [B.1](https://arxiv.org/html/2310.14814v4#A2.SS1 "B.1 Datasets ‣ Appendix B Experimental Setup"). All experimental results reported below are obtained over 9 different seeds.

#### Labeling procedure.

To generate SSL data, we consider the two following labeling strategies and compare the studied baselines in both cases (see more details in Appendix [B.2](https://arxiv.org/html/2310.14814v4#A2.SS2 "B.2 More details on the labeling procedure ‣ Appendix B Experimental Setup")):

1. IID: this is the case usually considered in classification tasks and that verifies the i.i.d. assumption. The selection variable s is completely random, i.e., independent of 𝐱 and y. In this case, we have P⁢(s=1|𝐱,y)=P⁢(s=1) and thus Plab⁢(𝐱,y)=P⁢(𝐱,y).
IID Par opposition à SSB

3. SSB: in this case, s is dependent of 𝐱 and y. For each class c and each data 𝐱 with label y=c, we impose:

| P⁢(s=1\|𝐱,y=c)=1β⁢exp⁡(r×\|proj1⁢(𝐱)\|), |
| ------------------------------------------ |
where r>0 is a hyperparameter, proj1⁢(𝐱) is the projection value of 𝐱 on the first principal component of the training data in class c and β=∑𝐱exp⁡(r×|proj1⁢(𝐱)|) is a normalizing constant to ensure that P(s=1|𝐱∈𝐗ℓ,y=c)=1. The impact of the strength of the bias is studied in Appendix [C.5](https://arxiv.org/html/2310.14814v4#A3.SS5 "C.5 Robustness to the strength of the bias ‣ Appendix C Additional Experiments").

#### Architecture and training parameters.

In all of our experiments, we train a 3-layer MLP, with the Adam optimizer (Kingma and Ba,, [2015](https://arxiv.org/html/2310.14814v4#bib.bib38)) and a learning rate of 0.001. Unless specified otherwise, we consider M=5 linear heads and a diversity strength parameter γ=1. In our experiments, we take ℓsup as the cross-entropy loss. Training is performed during 5 epochs with 100 training iterations per epoch. We evaluate the model on a test set of size 25% of the dataset. For each dataset, we run our experiments with 9 different seeds and display the average and the standard deviation of the test accuracy (both in %) over the 9 trials.


