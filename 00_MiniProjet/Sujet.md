# Mini-Projet d'Entrainement : Optimisation de Tournees de Livraison de Pizzas

## Contexte

Vous etes le gerant d'une pizzeria et vous devez livrer des commandes a plusieurs clients repartis dans votre quartier. Votre livreur part de la pizzeria, doit passer chez chaque client exactement une fois, puis revenir a la pizzeria. L'objectif est de **minimiser la distance totale parcourue** pour economiser du temps et du carburant.

Ce probleme est une version simplifiee du **Probleme du Voyageur de Commerce (TSP)**, qui est au coeur du bloc de Recherche Operationnelle.

Le plan du quartier est fourni dans le fichier `quartier_pizzeria.json`.

## Objectifs du Projet

1. **Modelisation du Probleme** : Representer le quartier sous forme de graphe (sommets = pizzeria + clients, aretes = rues avec distances en minutes).
2. **Implementation de trois algorithmes** :
   - **Force brute** : tester toutes les tournees possibles pour trouver la tournee optimale.
   - **Algorithme glouton (plus proche voisin)** : a chaque etape, livrer le client non visite le plus proche.
   - **Dijkstra + tournee** : utiliser les plus courts chemins pour ameliorer la tournee.
3. **Analyse de Complexite** : comparer les trois approches en termes de complexite theorique, temps d'execution et qualite de la solution.

## Instructions Detaillees

### Etape 1 : Preparation

- Installez Python et la librairie NetworkX : `pip install networkx`.
- Remplissez le fichier `Squelette.py` avec les fonctions à realiser pour chaque algorithme. Les signatures des fonctions sont deja definies, il vous suffit de les implementer.

### Etape 2 : Modelisation du Graphe

- Chargez les donnees depuis `quartier_pizzeria.json`.
- Construisez le graphe avec NetworkX.
- Affichez les proprietes du graphe : nombre de sommets, nombre d'aretes, degre de chaque sommet.

### Etape 3 : Implementation des Algorithmes

1. **Force brute** : Explorez toutes les permutations possibles des clients pour trouver la tournee la plus courte. Attention : cette approche n'est viable que pour un petit nombre de clients.
2. **Algorithme glouton** : A chaque etape, le livreur se rend chez le client non visite le plus proche. Cette heuristique est rapide mais ne garantit pas l'optimalite.
3. **Dijkstra + tournee** : Calculez les plus courts chemins entre tous les points, puis utilisez ces distances pour construire une tournee amelioree.

### Etape 4 : Analyse de Complexite

- Determinez la complexite theorique de chaque algorithme (en notation grand-O).
- Mesurez le temps d'execution de chaque algorithme sur le graphe fourni.
- Comparez la longueur des tournees obtenues.
- Discutez des avantages et limites de chaque approche.

### Etape 5 : Experimentation (bonus)

- Generez des instances aleatoires de tailles croissantes (5, 8, 10, 12 clients).
- Tracez l'evolution du temps de calcul en fonction du nombre de clients.
- Observez a partir de combien de clients la force brute devient impraticable.
- Que se passe-t-il un soir de match ou les commandes doublent ?

## Complexite Theorique Attendue

| Algorithme                   | Complexite temporelle | Qualite de la solution |
| ---------------------------- | --------------------- | ---------------------- |
| Force brute                  | $O(n!)$               | Optimale (garantie)    |
| Glouton (plus proche voisin) | $O(n^2)$              | Approchee              |
| Dijkstra + tournee           | $O(n^2 \log n)$       | Approchee (amelioree)  |

## Livrables

- **Code Python** : Implementation complete et commentee des trois algorithmes.
- **Rapport d'analyse** (1 a 2 pages) :
  - Description du probleme et du modele de graphe.
  - Explication de chaque algorithme.
  - Analyse de complexite theorique et experimentale.
  - Comparaison des resultats (tableau de synthese).
  - Conclusion : quel algorithme recommanderiez-vous au livreur et pourquoi ?

## Ressources

- [Documentation NetworkX](https://networkx.org/documentation/stable/index.html)
- [Complexite algorithmique](https://fr.wikipedia.org/wiki/Analyse_de_la_complexit%C3%A9_des_algorithmes)
- [Algorithme de Dijkstra](https://fr.wikipedia.org/wiki/Algorithme_de_Dijkstra)
- [Probleme du voyageur de commerce](https://fr.wikipedia.org/wiki/Probl%C3%A8me_du_voyageur_de_commerce)
