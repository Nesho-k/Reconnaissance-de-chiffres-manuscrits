# Reconnaissance de chiffres manuscrits

## Sommaire

- [Introduction](#introduction)
- [Importation des données](#importation-des-données)
- [Transformation des données](#transformation-des-données)
- [Modèle](#modèle)
- [Entraînement du modèle](#entraînement-du-modèle)
- [Vérification](#vérification)
- [Vérification avec le test set](#vérification-avec-le-test-set)
- [Conclusion](#conclusion)


## Introduction

Dans ce projet, un modèle de reconnaissance de chiffres manuscrits est developpé, en utilisant PyTorch et des techniques de deep learning. L’objectif est de concevoir et d’entraîner un réseau de neurones capable d’identifier correctement les chiffres à partir d’images d’entrée.

Ce projet permet d’explorer les concepts fondamentaux du deep learning, tels que la manipulation des tenseurs, la construction de réseaux de neurones et l’optimisation des hyperparamètres pour améliorer les prédictions.


## Importation des données 

Le jeu de données a été importé depuis : www.di.ens.fr/~lelarge/MNIST.tar.gz

Il est composé de deux parties : un training set et un test set. Nous allons d'abord importer le training set sans transformer les données afin de voir à quoi ressemble le dataset, puis nous allons créer un dataset personnalisé pour le prétraitement.

Le jeu de données est composé de 60 000 images de 28 pixels par 28 pixels, accompagné de 60 000 labels correspondants.

![Capture d’écran 2025-02-10 190018](https://github.com/user-attachments/assets/1bf786fd-a784-4387-a316-b6b4fb5d9cc8)

## Transformation des données 

Tout d'abord nous devons normaliser les images. La normalisation des images consiste à ramener les valeurs des pixels dans une intervalle plus restreint, entre 0 et 1. C'est important, car des valeurs trop grandes peuvent rendre l’entraînement du modèle instable. En effet, sans normalisation, les poids des neurones subiront des mises à jour trop instables, car les grandes valeurs domineront l'apprentissage au détriment des plus petites.

Il faut également effectuer un One-Hot Encoding pour la variable à expliquer **y**. Le One-Hot Encoding est une méthode de représentation des labels sous forme de vecteurs binaires.
Nous effectuons cela car le One-Hot Encoding permet au modèle de calculer la perte plus précisément en comparant directement les probabilités prédites avec les labels.


## Modèle 

![Capture d’écran 2025-02-10 190504](https://github.com/user-attachments/assets/11228439-a2bb-4c50-b7c9-07b8bc7d9d71)

Le réseau de neurones est composé de trois couches contenant respectivement 100, 50 et 10 neurones. La dernière couche doit en comporter 10 afin d'estimer les probabilités. Les deux premières couches utilisent la fonction d'activation ReLU.


## Entraînement du modèle 

La fonction coût utilisée pour notre modèle est la Cross Entropy Loss ou encore appelée Log Loss. 

![Capture d’écran 2025-02-10 190851](https://github.com/user-attachments/assets/0fd4bfd1-0e89-4452-901c-2180254a14ba)

Nous constatons qu'au fur et à mesure de l'entraînement, les erreurs du modèle diminuent. Au début, l'erreur était de 0.44 pour atteindre 0.004 à la fin.

## Vérification 

Voici le résultat obtenu pour les 20 premières images du train set :

![Capture d’écran 2025-02-10 191213](https://github.com/user-attachments/assets/ae58b198-1cf2-4bbe-ae5d-3c3e48a8f07b)


## Vérification avec le test set

Il faut maintenant vérifier si le modèle souffre de surapprentissage ou de sous-apprentissage des données. C'est là qu'intervient le test set, car le modèle n'a jamais vu ces images.

Voici le résultat obtenu pour les 20 premières images du test set :

![Capture d’écran 2025-02-10 191435](https://github.com/user-attachments/assets/fc61e9de-8098-44ca-9e60-7d11bd73d046)

Le modèle est très bon car il n'y pas de surapprentissage.

## Conclusion 

En conclusion, notre modèle montre de très bonnes performances dans la reconnaissance des chiffres manuscrits. En effet, il est capable de prédire les chiffres avec précision, sans surapprentissage, comme l'indique l'évaluation sur le test set. Les erreurs du modèle diminuent significativement au fil des epochs, ce qui témoigne de l'efficacité de l'apprentissage. Ainsi, nous pouvons affirmer que le modèle est bien entraîné et qu'il généralise correctement sur de nouvelles données.
 
