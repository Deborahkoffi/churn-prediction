# churn-prediction
Modèle de prédiction du départ client avec visualisation des résultats


Objectif
Développer un modèle prédictif permettant d’anticiper le **départ des clients (churn = 0/1)** afin d’aider l’entreprise à renforcer ses actions de fidélisation.

---

## Données & préparation
- Importation du jeu de données.
- Contrôles qualité :
  - Dimensions du dataset.
  - Valeurs manquantes (nombre et %).
  - Doublons.
- Nettoyage :
  - Recodage de la variable `genre` (*Male = 1, Female = 0*).

---

## 🔎 Analyse exploratoire pour comprendre les donnees 
- Statistiques descriptives : `age`, `anciennete`, `solde_bank`, `produit_souscrit`, `salaire_estime`.


![Resultat de l'analyse descriptive](description.png)

Interpreatation

- Tests de normalité (**Anderson–Darling**).
- Visualisations : histogrammes et courbes de densité.
- Matrice de corrélation (multicolinéarité).
- Recherche de valeurs aberrantes (méthode IQR et z-score).
- Étude du lien entre variables et churn (corrélation de Kendall + test de Wilcoxon).

### 📊 Visualisations
#### Histogramme d’âge
![Histogramme âge](images/hist_age.png)

#### Matrice de corrélation
![Corrplot](images/corrplot.png)

#### Distribution du solde bancaire
![Histogramme solde](images/hist_solde.png)

---

## Partitionnement & rééquilibrage
- Séparation des données en **train/test (70/30)**.
- Constats : `churn=1` est minoritaire.
- Application de **SMOTE** pour rééquilibrer les classes sur l’échantillon d’entraînement.

---

## Modélisation
- Modèle utilisé : **régression logistique**.
- Variables explicatives : `age`, `statut_active`, `produit_souscrit`, `credit_score`, `solde_bank`, `genre`.
- Qualité validée avec l’indice de **Nagelkerke**.

---

## Évaluation
- Prédictions sur l’échantillon test (non-SMOTE).
- Seuil de décision ajusté : **0,40**.
- **Matrice de confusion** : précision, rappel, accuracy.
- **Courbe ROC & AUC** : bonne capacité discriminante.

### 📊 Visualisations d’évaluation
#### Courbe ROC
![Courbe ROC](images/roc_curve.png)

#### Matrice de confusion
![Matrice de confusion](images/confusion_matrix.png)

---

## 📤 Restitution
- Export des prédictions (`proba`, `churn_predict`) pour analyse.
- Création d’un **dashboard Power BI** avec :
  - Taux de churn,
  - Variables explicatives clés,
  - Liste des clients à risque.

---

## Résultats & impact
- Mise en place d’un pipeline complet **Data → Analyse → Modèle → Évaluation → Restitution**.
- Amélioration de la détection des clients susceptibles de quitter.
- Outil de support à la **fidélisation client** grâce à des insights exploitables.

---

## 🧰 Packages R utilisés
`readxl`, `dplyr`, `nortest`, `corrplot`, `caret`, `smotefamily`, `pROC`, `rcompanion`.

