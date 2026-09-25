# Machine-Learning-for-Computer-vision
# Machine Learning for Computer Vision — Projets pratiques

Projets réalisés dans le cadre du cours **Machine Learning for Computer Vision** (Coursera / MathWorks), couvrant la classification d'images et la détection d'objets avec MATLAB.

## Sommaire
- [Projet 1 — Classification de panneaux de signalisation](#projet-1--classification-de-panneaux-de-signalisation)
- [Projet 2 — Détection de nœuds de bois](#projet-2--détection-de-nœuds-de-bois)
- [Compétences mobilisées](#compétences-mobilisées)

---

## Projet 1 — Classification de panneaux de signalisation

### Objectif
Entraîner un modèle de classification capable de distinguer plusieurs catégories de panneaux de signalisation (Cédez le passage, Ne pas entrer, Route fermée, Fin de toutes restrictions) à partir d'images, avec un objectif de précision de test d'au moins 90 %.

### Démarche
1. **Préparation des données**
   - Import des images sous forme d'`imageDatastore`, labellisées par sous-dossier.
   - Séparation en ensembles d'apprentissage (80 %) et de test (20 %) via `splitEachLabel`.

2. **Extraction des caractéristiques**
   - Construction d'un sac de mots visuels (`bagOfFeatures`) à partir des images d'apprentissage.
   - Encodage des images d'apprentissage et de test en vecteurs de caractéristiques (`encode`).

3. **Entraînement et évaluation**
   - Entraînement de plusieurs modèles de classification via l'app **Classification Learner** (SVM, arbre de décision, k-NN, méthodes d'ensemble).
   - Sélection du modèle le plus performant par validation croisée.
   - Évaluation finale sur l'ensemble de test : précision, matrice de confusion, courbes ROC et AUC par classe.


## Projet 2 — Détection de nœuds de bois

### Objectif
Développer et évaluer un détecteur d'objets basé sur la méthode **ACF (Aggregate Channel Features)** pour identifier automatiquement la présence et la localisation de nœuds sur des images de bois.

### Démarche
1. **Préparation des données**
   - Utilisation d'une vérité terrain fournie pour l'ensemble d'apprentissage (90 images).
   - Labellisation manuelle de l'ensemble de test (10 images) via l'app **Image Labeler**, avec des boîtes englobantes serrées autour des nœuds.

2. **Entraînement du détecteur**
   - Conversion de la vérité terrain en table d'entraînement (`objectDetectorTrainingData`).
   - Entraînement d'un détecteur ACF (`trainACFObjectDetector`) avec les paramètres par défaut.

3. **Détection et évaluation**
   - Application du détecteur sur l'ensemble de test.
   - Évaluation de la qualité des détections via l'**IoU (Intersection over Union)** entre boîtes détectées et vérité terrain.
   - Identification et comptage des nœuds non détectés (faux négatifs).

4. **Amélioration du détecteur**
   - Ajustement du seuil de détection (`Threshold`) pour réduire le nombre de faux négatifs.
   - Suppression des détections redondantes (plusieurs boîtes sur un même nœud) via `selectStrongestBbox`, avec `RatioType = "Min"` pour gérer correctement les boîtes imbriquées.



## Compétences mobilisées
- MATLAB & Computer Vision Toolbox
- Préparation de données et extraction de caractéristiques (`bagOfFeatures`) pour la classification d'images
- Entraînement et évaluation de modèles de classification (Classification Learner, matrice de confusion, courbes ROC/AUC)
- Entraînement et évaluation de détecteurs d'objets (ACF)
- Évaluation de détections : IoU, seuils de détection, Non-Maximum Suppression (NMS)
