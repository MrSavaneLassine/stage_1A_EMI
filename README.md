# stage_1A_EMI
Ici se trouve les details du stage de fin de première année d'ingénierie que j'ai effectué.

# Détection du glaucome à partir d’images du fond d’œil par apprentissage profond

Étude comparative de ResNet50 et de ViT-B/16 sur deux jeux de données de rétinographie.

## Contexte

Le glaucome est une neuropathie optique chronique et progressive constituant l'une des principales causes de cécité irréversible dans le monde. Son dépistage précoce est essentiel afin de ralentir son évolution par une prise en charge adaptée. 【1-2f3413】

Dans le cadre de mon stage de fin de première année à l'École Mohammadia d’Ingénieurs (EMI), effectué au Centre Hospitalier Ibn Sina de Rabat, j'ai réalisé une étude comparative de modèles de Deep Learning pour la détection automatique du glaucome à partir d'images du fond d’œil. 【1-2f3413】


## Objectifs

L'objectif principal du projet est de comparer les performances de deux architectures d'apprentissage profond :

- ResNet50 (réseau convolutif)
- ViT-B/16 (Vision Transformer)

L'étude vise également à :

- Évaluer l'impact du prétraitement des images.
- Comparer les performances sur deux jeux de données différents.
- Analyser les métriques adaptées au dépistage médical.
- Étudier la robustesse des modèles face à la variabilité des images rétiniennes. 【1-2f3413】

## Datasets utilisés

### ACRIMA

- 705 images de fond d’œil
- 396 cas de glaucome
- 309 cas sains
- Dataset relativement équilibré

### AI Glaucoma Dataset for AI Diagnosis

- 3160 images
- 2678 cas de glaucome
- 482 cas sains
- Dataset fortement déséquilibré et multi-source

Les données ont été réparties selon une stratégie stratifiée :

- 70 % entraînement
- 15 % validation
- 15 % test

【1-2f3413】

## Architecture expérimentale

Le protocole expérimental repose sur huit entraînements indépendants :

- 2 modèles : ResNet50 et ViT-B/16
- 2 datasets
- 2 pipelines :
  - Images brutes
  - Images prétraitées

Schéma de la démarche expérimentale : ![EMBEDDEDIMAGE](placeholder-1)

## Prétraitement des images

Deux approches ont été comparées :

### Pipeline brut

- Lecture de l'image RGB
- Redimensionnement à 224 × 224

### Pipeline prétraité

- CLAHE (Contrast Limited Adaptive Histogram Equalization)
- Recadrage central (90 %)
- Redimensionnement à 224 × 224
- Normalisation adaptée au modèle

Exemple de prétraitement : ![EMBEDDEDIMAGE](placeholder-2)

【1-2f3413】

## Modèles étudiés

### ResNet50

- Pré-entraîné sur ImageNet
- Backbone entièrement gelé
- Extraction de caractéristiques
- Tête de classification personnalisée

### ViT-B/16

- Pré-entraîné sur ImageNet
- Fine-tuning partiel
- Dernier bloc Transformer dégelé
- Couche de classification adaptée

Comparaison des architectures : ![EMBEDDEDIMAGE](placeholder-3)

【1-2f3413】

## Technologies utilisées

- Python
- TensorFlow / Keras
- PyTorch
- timm
- OpenCV
- Scikit-learn
- Jupyter Notebook
- Google Colaboratory

【1-2f3413】

## Résultats obtenus

### Dataset ACRIMA

#### Meilleur résultat de classification

ResNet50 avec prétraitement :

| Métrique | Valeur |
|-----------|---------|
| Accuracy | 98.11 % |
| Sensibilité | 98.31 % |
| Spécificité | 97.87 % |
| F1-Score | 98.31 % |
| AUC | 99.60 % |

#### Meilleure AUC

ViT-B/16 avec prétraitement :

- AUC = 99.82 %

【1-2f3413】

Matrices de confusion obtenues : ![EMBEDDEDIMAGE](placeholder-4)  
![EMBEDDEDIMAGE](placeholder-5)

### Second dataset

Les deux architectures ont obtenu :

- Accuracy ≈ 94–95 %
- AUC > 0.97

Malgré l'hétérogénéité des données et le fort déséquilibre des classes. 【1-2f3413】

Résultats du second dataset : ![EMBEDDEDIMAGE](placeholder-6)

## Principales conclusions

- Le prétraitement améliore significativement les performances du ResNet50.
- Le Vision Transformer atteint les meilleures performances de classement (AUC).
- Les deux modèles présentent d'excellentes capacités de détection du glaucome.
- La qualité des étiquettes des datasets reste un enjeu majeur pour les applications cliniques.
- Les modèles de fondation spécialisés comme RETFound constituent une piste prometteuse pour de futurs travaux. 【1-2f3413】

## Perspectives

Les améliorations envisagées incluent :

- Utilisation de RETFound pré-entraîné sur des images rétiniennes.
- Vérification clinique des annotations.
- Entraînements sur des bases de données plus larges.
- Validation multi-centres.
- Développement d'un système d'aide au diagnostic pour les ophtalmologues. 【1-2f3413】

## Structure du projet

```text
project/
│
├── notebooks/
├── datasets/
├── models/
├── results/
├── figures/
├── requirements.txt
└── README.md
```

## Auteur

Lassine SAVANE

Élève ingénieur en Informatique et Management des Systèmes

École Mohammadia d’Ingénieurs (EMI)

GitHub : https://github.com/MrSavaneLassine

## Encadrement

- Pr. Laila BENHLIMA (EMI)
- Pr. Rim EL HACHEMI (Centre Hospitalier Ibn Sina)

## Remerciements

Je remercie le Centre Hospitalier Ibn Sina et l'École Mohammadia d’Ingénieurs pour leur accompagnement durant ce stage de recherche consacré à l'application de l'intelligence artificielle à l'imagerie médicale.