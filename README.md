# Machine-Learning-for-Computer-vision
# Détection de nœuds de bois par apprentissage automatique

Projet réalisé dans le cadre du cours **Computer Vision for Science and Engineering** (Coursera / MathWorks), visant à entraîner un détecteur d'objets capable de repérer automatiquement les nœuds sur des images de bois.

## Objectif

Développer et évaluer un détecteur d'objets basé sur la méthode **ACF (Aggregate Channel Features)** pour identifier la présence et la localisation de nœuds de bois sur des images, avec une évaluation quantitative de sa performance.

## Démarche

1. **Préparation des données**
   - Utilisation d'une vérité terrain fournie pour l'ensemble d'apprentissage (90 images).
   - Labellisation manuelle de l'ensemble de test (10 images) via l'app **Image Labeler** de MATLAB, avec des boîtes englobantes serrées autour des nœuds.

2. **Entraînement du détecteur**
   - Conversion de la vérité terrain en table d'entraînement (`objectDetectorTrainingData`).
   - Entraînement d'un détecteur ACF (`trainACFObjectDetector`) avec les paramètres par défaut.

3. **Détection et évaluation**
   - Application du détecteur sur l'ensemble de test.
   - Évaluation de la qualité des détections via l'**IoU (Intersection over Union)** entre boîtes détectées et vérité terrain.
   - Identification des nœuds non détectés (faux négatifs).

4. **Amélioration du détecteur**
   - Ajustement du seuil de détection (`Threshold`) pour réduire le nombre de faux négatifs.
   - Suppression des détections redondantes (boîtes multiples sur un même nœud) avec `selectStrongestBbox`, en utilisant `RatioType = "Min"` pour bien gérer les boîtes imbriquées.

## Résultats

| Étape | Nœuds non détectés | Détections redondantes |
|---|---|---|
| Détection initiale (seuil par défaut) | X | Y |
| Après ajustement du seuil | X' | Y' |
| Après suppression des redondances (NMS) | — | 0 |

*(Remplace X, Y, X', Y' par tes valeurs réelles.)*

### Exemple de détection
![Exemple de détection](images/example_detection.png)

*Boîte verte : vérité terrain — Boîte jaune : détection du modèle, avec score de confiance.*

### Avant / après suppression des doublons
![Avant après NMS](images/before_after_nms.png)

## Compétences mobilisées

- MATLAB & Computer Vision Toolbox
- Détection d'objets (ACF)
- Labellisation d'images (Image Labeler)
- Évaluation de modèles : IoU, seuils de détection, Non-Maximum Suppression (NMS)

## Remarque

Le dataset d'images (nœuds de bois) provient du matériel pédagogique du cours et n'est pas inclus dans ce dépôt pour des raisons de droits d'usage. Seuls le code et les résultats sont partagés.
