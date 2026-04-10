# Bloc Recherche Opérationnelle - A3 2025-2026

Ce dépôt rassemble l'ensemble des ressources du bloc Recherche Opérationnelle. Le bloc dure quatre semaines et tourne autour d'un projet fil rouge pour l'ADEME : optimiser des tournées de véhicules sur un réseau routier. Pour y arriver, on monte progressivement en compétences sur la théorie des graphes, la complexité, la programmation linéaire et les métaheuristiques.

## Avant de commencer

Trois notebooks de préparation sont disponibles dans le dossier `00_Preparation`. Ils permettent de se remettre à niveau sur Python, la théorie des graphes et les bases de l'algorithmique. Prenez le temps de les parcourir avant le début du bloc, surtout si vous n'avez pas codé depuis un moment.

Un mini-projet d'entraînement est également disponible dans `00_MiniProjet` : il s'agit d'optimiser les tournées de livraison d'une pizzeria. C'est un bon moyen de pratiquer en autonomie tout au long du bloc, sur un problème plus petit et plus ludique que le projet principal.

Les slides de cours magistral sont dans `00_Slides` au format PDF.

## Déroulement du bloc

**Semaine 1 - Théorie des graphes** (`02_Boucle_1_Theorie_Graphe`). On apprend à modéliser un réseau sous forme de graphe, à le représenter en mémoire et à le parcourir. Le workshop porte sur les cycles eulériens et le problème des 7 ponts de Königsberg. On implémente l'algorithme de Hierholzer et on découvre la bibliothèque NetworkX.

**Semaine 2 - Complexité** (`03_Boucle_2_Complexite`). On comprend pourquoi certains problèmes sont difficiles. Le workshop porte sur les problèmes hamiltoniens et la NP-Complétude. On étudie les classes P, NP, NP-Complet et NP-Difficile, les réductions polynomiales, et on s'entraîne sur des exercices d'analyse de complexité.

**Semaine 3 - Programmation linéaire** (`04_Boucle_3_Programmation_Lineaire`). On apprend à formuler un problème d'optimisation comme un programme linéaire (variables de décision, contraintes, fonction objectif) et à le résoudre avec le solveur PuLP en Python. On passe à la programmation linéaire en nombres entiers et on formule le TSP avec les contraintes MTZ.

**Semaine 4 - Méthodes de résolution** (`05_Boucle_4_Metaheuristiques`). On explore l'ensemble des stratégies de résolution : méthodes exactes (backtracking, programmation dynamique, force brute), heuristiques gloutonnes, algorithmes probabilistes, et métaheuristiques (algorithmes génétiques, recuit simulé). On applique ces méthodes au Bin Packing Problem.

## Le projet fil rouge ADEME

Tout au long du bloc, les compétences acquises dans chaque boucle alimentent le projet principal. L'ADEME cherche des solutions de mobilité intelligente : la mission est de concevoir un programme calculant une tournée optimale sur un réseau routier, avec au moins deux contraintes supplémentaires (fenêtres temporelles, multi-véhicules, capacités de chargement...).

Deux livrables sont attendus sous forme de Notebooks Jupyter. Le premier porte sur la modélisation du problème et la preuve de sa NP-Complétude. Le second inclut un générateur d'instances, l'implémentation d'au moins deux méthodes de résolution, et une étude expérimentale comparant leurs performances.

Tous les détails du projet sont dans le fichier [`01_Projet_ADEME/Presentation_Projet.md`](01_Projet_ADEME/Presentation_Projet.md).

## Installation

L'exécution des notebooks nécessite Python 3 (Anaconda recommandé). Toutes les dépendances sont listées dans le fichier `requirements.txt` et s'installent en une commande :

```bash
pip install -r requirements.txt
```

## Liens des kahoots

- [Kahoot Entrainement Graphe - Les base](https://create.kahoot.it/share/ro-base-graphe/56bc7058-12b3-447a-b7aa-34313aa638c7)
- [Kahoot Prosit Retour 1 - Théorie des graphes](https://create.kahoot.it/share/ro-pr1/c00a20ca-b4d3-43b0-884e-7c6f48d33637)
- [Kahoot Prosit Retour 2 - Complexité et Réduction](https://create.kahoot.it/share/ro-pr2/53270ab4-240e-4cf9-8028-8459210c310d)
- [Kahoot Prosit Retour 3 - Problèmes d'optimisation difficiles](https://create.kahoot.it/share/ro-pr3/621a274d-6a1b-42f2-8b65-0cc54058bd59)
