# ♞ Promenade Aléatoire du Cavalier

> Projet de **modèles aléatoires markoviens** consacré à l’étude de la promenade aléatoire d’un cavalier sur un échiquier \(8 \times 8\), avec **analyse théorique**, **simulations Python** et **rapport scientifique rédigé en LaTeX**.

## ✨ Aperçu

Ce projet étudie le déplacement aléatoire d’un cavalier sur un échiquier standard à travers le cadre mathématique des **chaînes de Markov homogènes**.

À chaque instant, le cavalier choisit de manière équiprobable l’un des mouvements autorisés par les règles du jeu d’échecs.  
L’objectif est d’analyser ce processus stochastique à la fois :

- théoriquement ;
- numériquement ;
- graphiquement.

## 🎯 Objectifs

Le projet répond à trois grandes questions :

- **Caractériser mathématiquement** la chaîne de Markov associée à la promenade du cavalier
- **Calculer et valider** le temps moyen de retour à certaines cases, notamment les coins
- **Étudier le comportement asymptotique** de la sous-chaîne aux instants pairs

## 🧠 Contenu scientifique

Le rapport traite notamment des notions suivantes :

- chaîne de Markov homogène
- matrice de transition
- irréductibilité
- récurrence positive
- périodicité
- structure bipartite
- mesure stationnaire
- temps moyen de retour
- convergence en distribution
- validation par simulation

## 🛠️ Technologies utilisées

- **Python**
- **NumPy**
- **Matplotlib**
- **NetworkX**
- **Seaborn**
- **SciPy**
- **LaTeX**

## 📂 Structure attendue du projet

```bash
.
├── code/
│   ├── simulation_markov.py
│   ├── graphe_transition.py
│   └── visualisations.py
├── figures/
│   ├── graphe_transition.png
│   ├── temps_retour_case27.png
│   ├── chaine_pairs_case0.png
│   └── ...
├── rapport/
│   ├── projet_MARKOV_version_finale.pdf
│   ├── main.tex
│   └── annexes/
└── README.md
