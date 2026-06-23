# Projet Data Mining - Auto MPG Dataset

> Prédiction de la consommation de carburant automobile à partir des caractéristiques techniques des véhicules

![Python](https://img.shields.io/badge/Python-3.11-blue.svg)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-orange.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)

---

## 📋 Table des matières

- [Présentation du projet](#-présentation-du-projet)
- [Objectifs](#-objectifs)
- [Dataset](#-dataset)
- [Structure du projet](#-structure-du-projet)
- [Installation](#-installation)
- [Exécution](#-exécution)
- [Résultats](#-résultats)
- [Visualisations](#-visualisations)
- [Auteurs & encadrants](#-auteurs)

---

## 📖 Présentation du projet

Ce projet s'inscrit dans le cadre du module **Exploration de données** et porte sur la prédiction de la consommation de carburant des véhicules automobiles à partir de leurs caractéristiques techniques.

### Problématique

**Peut-on prédire la consommation de carburant d'une voiture (en miles per gallon) à partir de ses caractéristiques techniques ?**

### Type de problème

- **Régression supervisée**
- Variable cible : `mpg` (miles per gallon) - continue
- Variables explicatives : caractéristiques techniques du véhicule

### Modèles comparés

| Modèle | Description |
|--------|-------------|
| Linear Regression | Régression linéaire standard |
| Ridge | Régularisation L2 |
| Lasso | Régularisation L1 |
| **Random Forest** | Forêt aléatoire **(Meilleur modèle)** |

---

## 🎯 Objectifs

1. Comprendre le dataset et sa source (UCI Machine Learning Repository)
2. Analyser les variables et la cible
3. Nettoyer et préparer les données
4. Réaliser une analyse exploratoire commentée
5. Construire plusieurs modèles de régression adaptés
6. Évaluer les performances avec des métriques pertinentes
7. Interpréter les résultats et discuter les limites

---

## 📊 Dataset

### Source

- **Nom** : Auto MPG Dataset
- **Source** : UCI Machine Learning Repository
- **URL** : [https://archive.ics.uci.edu/ml/datasets/Auto+MPG](https://archive.ics.uci.edu/ml/datasets/Auto+MPG)
- **Fichier** : `auto-mpg.data`

### Description

| Caractéristique | Valeur |
|-----------------|--------|
| Nombre de lignes | 398 |
| Nombre de colonnes | 9 |
| Période | 1970 - 1982 |
| Type de tâche | Régression |

### Variables

| Variable | Type | Description |
|----------|------|-------------|
| `mpg` | Numérique | Consommation (miles per gallon) - **CIBLE** |
| `cylinders` | Numérique | Nombre de cylindres (3-8) |
| `displacement` | Numérique | Cylindrée (cubic inches) |
| `horsepower` | Numérique | Puissance (horsepower) |
| `weight` | Numérique | Poids (lbs) |
| `acceleration` | Numérique | Accélération 0-60 mph (secondes) |
| `model_year` | Numérique | Année du modèle (70-82) |
| `origin` | Catégoriel | Origine : 1=USA, 2=Europe, 3=Japon |
| `car_name` | Identifiant | Nom du modèle (exclu) |

---

## 📁 Structure du projet
notebook/
│
├── notebook.ipynb # Notebook Jupyter principal
├── auto-mpg.data # Dataset
├── requirements.txt # Dépendances Python
├── README.md # Ce fichier
│
├── images/ # Dossier des figures générées
│ ├── eda_visualizations.png # Visualisations EDA
│ ├── correlation_matrix.png # Matrice de corrélation
│ ├── outliers_boxplots.png # Boxplots des outliers
│ ├── predictions_vs_actual.png # Prédictions vs valeurs réelles
│ ├── residuals_analysis.png # Analyse des résidus
│ └── feature_importance.png # Importance des variables
│
├── rapport/ # Rapport LaTeX
│ ├── main.tex # Fichier LaTeX
│ └── rapport.pdf # PDF généré
│
└── outputs/ # Résultats
└── results_summary.json # Résumé des résultats


## 🔧 Installation

### Prérequis

- Python 3.8 ou supérieur
- pip (gestionnaire de paquets Python)

### Étapes d'installation

**1. Cloner le dépôt**

git clone https://github.com/votre-username/notebook.git
cd notebook
2. Créer un environnement virtuel (recommandé)

# Windows
python -m venv venv
venv\Scripts\activate

# Linux/Mac
python3 -m venv venv
source venv/bin/activate

3. Installer les dépendances
pip install -r requirements.txt

Dépendances

pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=1.0.0
jupyter>=1.0.0

🚀 Exécution

1. Télécharger le dataset
Le dataset est inclus dans le projet (auto-mpg.data). Si vous souhaitez le télécharger :

# Télécharger depuis l'UCI
wget https://archive.ics.uci.edu/static/public/9/auto+mpg.zip
unzip auto+mpg.zip

2. Lancer Jupyter Notebook
jupyter notebook

3. Ouvrir le notebook
Dans Jupyter, ouvrez notebook.ipynb et exécutez les cellules dans l'ordre.

4. Exécuter en mode headless (sans interface)
jupyter nbconvert --to notebook --execute notebook.ipynb --output notebook_executed.ipynb

📈 Résultats
Performance des modèles
Modèle	Train RMSE	Test RMSE	Train R²	Test R²
Linear Regression	3.370	2.888	0.819	0.845
Ridge (L2)	3.371	2.889	0.819	0.845
Lasso (L1)	3.438	2.955	0.811	0.838
Random Forest	1.088	2.180	0.981	0.912

Meilleur modèle
Random Forest a été sélectionné avec :

R² = 0.912 sur le test set

RMSE = 2.18 mpg

Erreur moyenne d'environ 1.62 mpg (MAE)

Importance des variables
Variable	Importance
weight	51.2%
model_year	20.8%
origin_3 (Japon)	11.0%
origin_2 (Europe)	5.5%
horsepower	5.5%
displacement	4.6%
cylinders	1.0%
acceleration	0.4%
Principales relations identifiées
Poids vs consommation : Corrélation de -0.83 (très forte)

Année vs consommation : Corrélation de +0.58 (modérée à forte)

4 cylindres : moyenne 29 mpg vs 15 mpg pour 8 cylindres

Voitures japonaises : moyenne 30 mpg vs 20 mpg pour américaines

📊 Visualisations
Les figures suivantes sont générées automatiquement par le notebook :

Figure	Description
eda_visualizations.png	6 visualisations de l'analyse exploratoire
correlation_matrix.png	Matrice de corrélation des variables numériques
outliers_boxplots.png	Boxplots pour l'analyse des outliers
predictions_vs_actual.png	Prédictions vs valeurs réelles
residuals_analysis.png	Analyse des résidus du modèle
feature_importance.png	Importance des variables dans Random Forest

Annexes

Compiler le rapport
bash
cd rapport
pdflatex main.tex
pdflatex main.tex  # Deux fois pour la table des matières

👥 Auteurs & encadrants
Étudiants : Mr. Omar Tazi & Mlle. Meriam Erragragui

Encadrement académique : EMSI – Pr. Younes Nadir

📩 Contact
📧 Email : omart4437@gmail.com | merragragui3@gmail.com

🔗 LinkedIn : www.linkedin.com/in/omar-tazi-b0a131284 | www.linkedin.com/in/meryem-erragragui-23b02929a

💻 GitHub : https://github.com/OTazi95 | https://github.com/merragragui
