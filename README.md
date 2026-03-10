# Maintenance Prédictive Aéronautique par Intelligence Artificielle

## Estimation de la Remaining Useful Life (RUL) des Turboréacteurs

**Auteur :** Ahmed Elyamini
**Établissement :** ENSA Safi – Université Cadi Ayyad
**Département :** IRT | GATE3
**Filière :** Smart Manufacturing / IoT / Cybersécurité

---

# 📌 Présentation du Projet

Ce projet vise à développer un modèle d’intelligence artificielle capable de prédire la **durée de vie restante (Remaining Useful Life – RUL)** d’un turboréacteur à partir de données issues de capteurs.

Dans l’industrie aéronautique la maintenance constitue un enjeu majeur. Elle doit garantir la sécurité des vols tout en maîtrisant les coûts opérationnels. La maintenance prédictive permet d’anticiper les défaillances avant qu’elles ne surviennent en exploitant les données générées par les systèmes embarqués.

L’objectif principal de ce projet est donc de construire un modèle de **Machine Learning capable d’estimer le nombre de cycles restants avant la panne d’un moteur**.

---

# ⚙️ Types de Maintenance dans l’Aéronautique

### Maintenance corrective

Intervention après une panne. Cette approche est interdite dans le domaine aéronautique en raison des risques critiques.

### Maintenance préventive

Maintenance programmée selon un calendrier ou un nombre de cycles. Elle garantit la sécurité mais peut entraîner des coûts élevés car certaines pièces sont remplacées trop tôt.

### Maintenance prédictive

Approche basée sur l’analyse des données capteurs afin de prévoir les défaillances avant leur apparition.
C’est l’approche étudiée dans ce projet.

---

# 📊 Dataset Utilisé

Le projet utilise le dataset **NASA C-MAPSS (Commercial Modular Aero-Propulsion System Simulation)**.

Ce dataset contient des simulations de fonctionnement de turboréacteurs avec :

* **100 moteurs simulés**
* des cycles de fonctionnement jusqu’à la panne
* **3 paramètres opérationnels**
* **21 capteurs**

Dataset utilisé dans ce projet :

```
FD001
```

Structure des fichiers :

```
data/
 ├── train_FD001.txt
 ├── test_FD001.txt
 └── RUL_FD001.txt
```

---

# 🧰 Technologies et Bibliothèques

Le projet est développé en **Python** avec les bibliothèques suivantes :

* pandas
* numpy
* matplotlib
* seaborn
* scikit-learn

Installation rapide :

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

---

# 🧪 Méthodologie

Le projet suit une démarche classique de **data science appliquée à la maintenance prédictive**.

## 1 Analyse Exploratoire des Données (EDA)

Objectifs :

* comprendre la structure des données
* analyser l’évolution des capteurs
* identifier les capteurs inutiles

Actions réalisées :

* visualisation de l’évolution des capteurs
* calcul des écarts types
* suppression des capteurs constants
* analyse des corrélations entre capteurs

Capteurs supprimés :

```
sensor_1
sensor_5
sensor_10
sensor_16
sensor_18
sensor_19
```

---

# ⚙️ Prétraitement des Données

## Génération de la variable cible

La variable cible est la **Remaining Useful Life (RUL)**.

Formule :

```
RUL = cycle_max - cycle_actuel
```

Cela permet d’indiquer au modèle combien de cycles il reste avant la panne.

---

## Nettoyage des données

Les colonnes suivantes sont supprimées :

* unit_nr
* time_cycles
* capteurs constants

---

## Normalisation

Les données sont normalisées avec **MinMaxScaler** afin de ramener toutes les variables dans l’intervalle :

```
[0 , 1]
```

Cela permet d’éviter que certaines variables dominent artificiellement l’apprentissage.

---

# 🤖 Modèles de Machine Learning

Deux modèles ont été testés.

## 1 Régression Linéaire (Baseline)

La régression linéaire sert de modèle de référence.

Principe :

```
RUL = β0 + β1x1 + β2x2 + ... + βnxn
```

Résultats :

* RMSE : 32.04
* MAE : 25.59
* R² : 0.40

---

## 2 Random Forest Regressor

Le Random Forest est un ensemble d’arbres de décision.

Avantages :

* capture les relations non linéaires
* robuste au bruit
* performant sur des données complexes

Paramètres utilisés :

```
n_estimators = 200
random_state = 42
```

Résultats :

* RMSE : 33.85
* MAE : 24.79
* R² : 0.33

---

# 📈 Évaluation des Modèles

L’évaluation suit la méthodologie recommandée pour le dataset NASA C-MAPSS :

1. utiliser le dataset **test_FD001**
2. conserver le **dernier cycle de chaque moteur**
3. prédire le RUL
4. comparer avec **RUL_FD001**

Métriques utilisées :

### RMSE

```
RMSE = √(1/N Σ (y - y_pred)^2)
```

### MAE

Erreur absolue moyenne.

### R²

Coefficient de détermination.

---

# 📊 Visualisation des Résultats

Le projet inclut plusieurs visualisations :

* évolution des capteurs
* matrice de corrélation
* comparaison RUL réel vs RUL prédit
* analyse des erreurs

Ces graphiques permettent de mieux comprendre le comportement des modèles.

---

# 📌 Résultats

| Modèle              | RMSE  | MAE   | R²   |
| ------------------- | ----- | ----- | ---- |
| Régression Linéaire | 32.04 | 25.59 | 0.40 |
| Random Forest       | 33.85 | 24.79 | 0.33 |

La régression linéaire sert de référence simple.
Le Random Forest permet de mieux modéliser les relations complexes entre capteurs.

---

# 🚀 Applications Industrielles

Ce type de modèle peut être appliqué à :

* moteurs d’avions
* turbines industrielles
* machines de production
* systèmes IoT industriels

Bénéfices :

* réduction des coûts de maintenance
* augmentation de la disponibilité des équipements
* amélioration de la sécurité

---

# 📂 Structure du Projet

```
predictive-maintenance-aircraft/

├── data/
│   ├── train_FD001.txt
│   ├── test_FD001.txt
│   └── RUL_FD001.txt
│
├── notebooks/
│   └── predictive_maintenance.ipynb
│
├── src/
│   └── model_training.py
│
├── README.md
└── requirements.txt
```

---

# 👨‍💻 Auteur

**Ahmed Elyamini**
ENSA Safi – Université Cadi Ayyad

Filière : Smart Manufacturing / IoT / Cybersécurité

---

# 📜 Licence

Projet académique à usage pédagogique et de recherche.
