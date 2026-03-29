# Bloc Recherche Opérationnelle — A3 2025-2026

Ce dépôt centralise les travaux et ressources du bloc d'apprentissage dédié à la Recherche Opérationnelle. Ce bloc se déroule sur quatre semaines et s'articule autour d'un projet fil rouge (ADEME) nécessitant la mise en œuvre de concepts d'optimisation, de théorie des graphes et d'algorithmique avancée.

## Structure du dépôt

```
├── 00_Preparation/                         Remise à niveau Python, graphes, algorithmique
│   ├── sequence_0_fondamentaux_python.ipynb
│   ��── sequence_1_bases_theorie_graphes.ipynb
│   └── sequence_2_algorithmique.ipynb
│
├── 00_MiniProjet/                          Mini-projet d'entraînement (livraison de pizzas)
��   ├── Sujet.md
│   ├── Squelette.py
│   └── quartier_pizzeria.json
│
├── 00_Slides/                              Supports de cours magistral (PDF)
│
��── 01_Projet_ADEME/                        Projet fil rouge
│   ├── Presentation_Projet.md
│   └── Présentation_Projet.pptx
│
├── 02_Boucle_1_Theorie_Graphe/             Semaine 1 — Théorie des graphes
│   ├── 00_workshop_euleriens_etudiant.ipynb
│   ├── 01_cycle_eulerien.ipynb
│   └── 02_exercices_networkx.ipynb
│
├── 03_Boucle_2_Complexite/                 Semaine 2 — Complexité algorithmique
│   ├── 00_workshop_hamiltonien_np_completude.docx
│   ├── 01_classes_de_complexite.ipynb
│   ├── 02_reductions_polynomiales.ipynb
│   ├── 03_np_complet.ipynb
│   └── 04_exercices_corriges.ipynb
│
├── 04_Boucle_3_Programmation_Lineaire/     Semaine 3 — Programmation linéaire
│   └── 01_programmation_lineaire.ipynb
│
├── 05_Boucle_4_Metaheuristiques/           Semaine 4 — Méthodes de résolution
│   ├── 01_algorithmes_probabilistes.ipynb
│   ├── 02_algorithmes_genetiques.ipynb
│   ├── 03_bin_packing_problem.ipynb
│   ├── 04_backtracking.ipynb
│   ├── 05_programmation_dynamique.ipynb
│   └── 06_algorithmes_gloutons_et_bruteforce.ipynb
│
└── Tableau_des_AAV_A3_RO_2025-26.xlsx      Acquis d'apprentissage visés
```

## Parcours étudiant recommandé

### Phase 0 — Préparation (avant le bloc)

1. **Séquence 0** : Fondamentaux Python (variables, listes, dictionnaires, fonctions, modules)
2. **Séquence 1** : Bases de la théorie des graphes (représentations, BFS/DFS, Dijkstra)
3. **Séquence 2** : Fondamentaux d'algorithmique (complexité, récursivité, stratégies de résolution)
4. **Mini-projet pizzas** : À réaliser en autonomie tout au long du bloc pour s'entraîner

### Semaine 1 — Boucle 1 : Théorie des graphes

- Workshop sur les cycles eulériens et la représentation de graphes
- Implémentation et étude expérimentale de l'algorithme de Hierholzer
- Exercices pratiques avec NetworkX

### Semaine 2 — Boucle 2 : Complexité

- Workshop sur les problèmes hamiltoniens et la NP-Complétude
- Classes de complexité (P, NP, NP-Complet, NP-Difficile)
- Réductions polynomiales et preuves de NP-Complétude
- Exercices corrigés d'analyse de complexité

### Semaine 3 — Boucle 3 : Programmation linéaire

- Formulation de problèmes d'optimisation (variables, contraintes, objectif)
- Résolution avec le solveur PuLP (PL et PLNE)
- Application au TSP avec contraintes MTZ

### Semaine 4 �� Boucle 4 : Méthodes de résolution

- Algorithmes exacts : backtracking, programmation dynamique, force brute
- Algorithmes approchés : glouton, algorithmes probabilistes
- Métaheuristiques : algorithmes génétiques, recuit simulé
- Application au Bin Packing Problem

### Tout au long — Projet ADEME

Les compétences acquises dans chaque boucle sont mobilisées pour construire progressivement les deux livrables du projet fil rouge.

## Contexte du projet fil rouge

L'ADEME a lancé un appel à manifestation d'intérêt pour promouvoir de nouvelles solutions de mobilité. La mission consiste à concevoir un programme calculant une **tournée optimale** sur un réseau routier, avec au moins **deux contraintes supplémentaires** (fenêtres temporelles, multi-véhicules, capacités...).

**Livrables attendus :**
- **Livrable 1 — Modélisation** : Représentation formelle, démonstration de NP-Complétude
- **Livrable 2 — Implémentation** : Générateur d'instances, deux méthodes de résolution, étude expérimentale

Voir [`01_Projet_ADEME/Presentation_Projet.md`](01_Projet_ADEME/Presentation_Projet.md) pour les détails complets.

## Installation

L'exécution du code nécessite :

```bash
# Environnement Python (Anaconda recommandé)
pip install networkx matplotlib numpy pulp
```

Les notebooks sont conçus pour être exécutés dans Jupyter Notebook ou JupyterLab.
