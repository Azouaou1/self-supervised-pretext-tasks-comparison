# Comparaison de tâches prétextes auto-supervisées

TP de Master 2 Informatique (parcours VMI, module Image) : **apprentissage de représentations d'images par approches auto-supervisées**.

Le projet compare plusieurs tâches prétextes en évaluant la qualité des représentations apprises par **évaluation linéaire** (encodeur gelé + classifieur linéaire).

## Contenu

| Partie | Description |
| --- | --- |
| Q1–Q2 | Démos des trois tâches prétextes fournies : Context Encoder, Rotation, SimCLR |
| Q3 | Comparaison des trois modèles sur CIFAR-10 (graphique + matrice de confusion) |
| Q4 | Comparaison sur un autre jeu de données : CIFAR-100 |
| Q5 | Implémentation d'une nouvelle tâche prétexte : prédiction de la **position relative d'un patch** (Doersch et al., 2015) |
| Q6 | Évaluation de cette tâche face aux autres sur CIFAR-100 |

## Résultats (accuracy top-1 en test, évaluation linéaire)

| Modèle | CIFAR-10 | CIFAR-100 |
| --- | --- | --- |
| SimCLR | 92,8 % | 55,0 % |
| Rotation | 79,9 % | 47,3 % |
| Position relative (notre implémentation) | – | 33,3 % |
| Context Encoder | 45,8 % | 19,1 % |

La tâche prétexte « position relative » atteint 56,8 % d'accuracy (8 positions possibles) sur les paires de test.

## Exécution

Le notebook est prévu pour **Google Colab avec GPU** (Exécution → Modifier le type d'exécution → GPU).

1. Ouvrir le notebook dans Colab.
2. Exécuter les cellules d'installation : clonage de la librairie [`cs294-158-ssl`](https://github.com/ckurtz/cs294-158-ssl) et téléchargement des modèles pré-entraînés (`results.zip`).
3. Exécuter les cellules dans l'ordre. CIFAR-10 et CIFAR-100 sont téléchargés automatiquement par `torchvision`.

## Dépendances

- Python 3, PyTorch, torchvision
- scikit-learn, numpy, matplotlib
- Librairie `deepul_helper` (installée depuis [`cs294-158-ssl`](https://github.com/ckurtz/cs294-158-ssl))

## Références

- Code de départ : [teaching_UPC_UFRMI / selfsupervised_demos.ipynb](https://github.com/ckurtz/teaching_UPC_UFRMI/blob/main/selfsupervised_demos.ipynb)
- Pathak et al., *Context Encoders: Feature Learning by Inpainting*, CVPR 2016
- Gidaris et al., *Unsupervised Representation Learning by Predicting Image Rotations*, ICLR 2018
- Chen et al., *A Simple Framework for Contrastive Learning of Visual Representations*, ICML 2020
- Doersch et al., *Unsupervised Visual Representation Learning by Context Prediction*, ICCV 2015
