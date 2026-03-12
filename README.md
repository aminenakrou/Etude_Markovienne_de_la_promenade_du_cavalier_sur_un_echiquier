<p align="center">
  <img src="https://img.shields.io/badge/Langage-Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Chaînes_de-Markov-d4a843?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Polytech-Lille-d46a6a?style=for-the-badge" />
  <img src="https://img.shields.io/badge/IS4-2026-5ab8a0?style=for-the-badge" />
</p>

<h1 align="center">♞ Promenade du Cavalier sur un Échiquier</h1>

<p align="center">
  <strong>Étude Markovienne</strong> de la marche aléatoire d'un cavalier d'échecs<br>
  sur un échiquier 8×8 — Chaînes de Markov, irréductibilité, périodicité et convergence.
</p>

<p align="center">
  <a href="https://aminenakrou.github.io/Etude_Markovienne_de_la_promenade_du_cavalier_sur_un_echiquier">♞ Site interactif</a> &nbsp;·&nbsp;
  <a href="https://github.com/aminenakrou/Etude_Markovienne_de_la_promenade_du_cavalier_sur_un_echiquier/blob/main/projet_MARKOV_version_finale.pdf">📄 Rapport PDF</a>
</p>

---

## ♟️ À propos

Un cavalier se promène aléatoirement sur un échiquier 8×8 : à chaque instant, il choisit **uniformément** parmi ses déplacements possibles. Ce processus forme une **chaîne de Markov homogène** sur 64 états.

Ce projet étudie trois questions fondamentales :

1. **Caractérisation** — Démontrer que (X_n) est une chaîne de Markov, étudier son irréductibilité, sa récurrence et sa périodicité
2. **Temps de retour** — Calculer et simuler le temps moyen de retour aux coins de l'échiquier
3. **Comportement asymptotique** — Analyser la sous-chaîne Y_n = X_{2n} aux instants pairs

> ♞ **[Testez la simulation interactive →](https://aminenakrou.github.io/Etude_Markovienne_de_la_promenade_du_cavalier_sur_un_echiquier)** — Déplacez le cavalier sur un vrai échiquier, observez les degrés et les cases visitées en temps réel.

---

## ⚡ Résultats clés

| Case | Type | Degré D(x) | π(x) | E[T] théorique | E[T] simulé | Erreur |
|:-----|:----:|:----------:|:-----:|:--------------:|:-----------:|:------:|
| **0** | Coin | 2 | 1/168 | **168.00** | 167.19 | 0.48% |
| **9** | Bord | 4 | 1/84 | **84.00** | 83.76 | 0.29% |
| **18** | Milieu | 6 | 1/56 | **56.00** | 55.92 | 0.14% |
| **27** | Centre | 8 | 1/42 | **42.00** | 42.08 | 0.19% |

> Toutes les simulations (3 000+ runs) confirment les prédictions théoriques avec une erreur inférieure à **0.5%**.

---

## 🧠 Propriétés de la chaîne

| Propriété | Valeur |
|:----------|:-------|
| Espace d'états | E = {0, 1, …, 63}, \|E\| = 64 |
| Transition | p(x,y) = 1/D(x) si mouvement possible |
| Irréductible | ✅ Tous les états communiquent |
| Récurrente positive | ✅ Espace fini + irréductible |
| Période | **d = 2** (structure bipartite blanc/noir) |
| Mesure stationnaire | **π(x) = D(x) / 336** |
| Somme des degrés | Σ D(x) = 336 |

---

## 📊 Matrice des degrés

Le nombre de mouvements possibles varie selon la position sur l'échiquier :

```
  2  3  4  4  4  4  3  2
  3  4  6  6  6  6  4  3
  4  6  8  8  8  8  6  4
  4  6  8  8  8  8  6  4
  4  6  8  8  8  8  6  4
  4  6  8  8  8  8  6  4
  3  4  6  6  6  6  4  3
  2  3  4  4  4  4  3  2
```

Les coins (D=2) sont visités **4× moins souvent** que les cases centrales (D=8).

---

## 🔄 Sous-chaîne Y_n = X_{2n}

En ne considérant que les instants pairs, on obtient une chaîne **apériodique** qui converge :

| Propriété | Détail |
|:----------|:-------|
| Apériodique | ✅ (contrairement à X_n) |
| Cases accessibles | **32 sur 64** (même couleur que le départ) |
| Mesure stationnaire | π'(x) = 2D(x)/336 sur sa moitié |
| Vitesse de convergence | O(1/√n) |

La bipartition stricte de l'échiquier (cases blanches/noires) explique ce confinement.

---

## 📁 Structure du projet

```
├── index.html                          # Site web interactif (GitHub Pages)
├── projet_MARKOV_version_finale.pdf    # Rapport complet
├── code_simulation.py                  # Code Python des simulations
└── README.md
```

---

## 🛠 Prérequis

```bash
pip install numpy matplotlib networkx seaborn scipy
```

---

## 🚀 Lancer les simulations

```bash
python code_simulation.py
```

Le script génère :
- Le graphe de transition du cavalier (couleurs = probabilités)
- L'histogramme des temps de retour + QQ-plot exponentiel
- Les 4 heatmaps de la sous-chaîne Y_n (cases 0, 1, 18, 27)

---

## 🎮 Site interactif

Le [site web](https://aminenakrou.github.io/Etude_Markovienne_de_la_promenade_du_cavalier_sur_un_echiquier) propose :

- **♞ Échiquier jouable** — Déplacez le cavalier manuellement ou en mode automatique
- **🟡 Cases accessibles** — Les mouvements possibles pulsent en or
- **📊 Compteur temps réel** — Nombre de coups et cases visitées (x/64)
- **🎨 Heatmap des degrés** — Visualisation interactive avec π(x) au survol
- **📐 Formules** — Transitions, mesure stationnaire, temps de retour
- **📋 Tableaux comparatifs** — Théorie vs simulation avec erreurs

---

## 📐 Formules principales

**Probabilité de transition :**
```
p(x,y) = 1/D(x)  si x → y possible, 0 sinon
```

**Mesure stationnaire :**
```
π(x) = D(x) / 336
```

**Temps moyen de retour :**
```
E[Ti | X0 = i] = 1/π(i) = 336/D(i)
```

**Coin (D=2) → E[T₀] = 168 coups** &nbsp;|&nbsp; **Centre (D=8) → E[T₂₇] = 42 coups**

---

## 👥 Auteurs

| | Nom |
|:-:|:----|
| 🟡 | **Soufiane Derouich** | 
| 🟢 | **Amine Nakrou** | 

**Encadrant** : Prof. Louckx Christophe — Polytech Lille, IS4 — Janvier 2026

---

<p align="center">
  <em>« Le cavalier erre aléatoirement, mais sa marche obéit à des lois probabilistes rigoureuses. »</em>
</p>

<p align="center">
  <sub>Polytech Lille · IS4 · Modèles Aléatoires Markoviens · 2026</sub>
</p>
