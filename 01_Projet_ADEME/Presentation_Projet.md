# Projet Fil Rouge : Mobilite Multimodale Intelligente (ADEME / CesiCDP)

## Contexte

L'ADEME (Agence de l'Environnement et de la Maitrise de l'Energie) a lance un appel a manifestation d'interet pour promouvoir de nouvelles solutions de mobilite pour les personnes et les marchandises. En tant que membre de l'equipe de developpement de la structure CesiCDP, l'enjeu est de proposer une solution algorithmique d'optimisation logistique performante pour remporter de nouveaux marches.

## Mission

Concevoir un programme capable de calculer, sur un reseau routier, une **tournee permettant de relier un sous-ensemble de villes puis de revenir au point de depart**, de maniere a **minimiser la duree totale du trajet**.

Ce probleme devra imperativement integrer **au moins deux contraintes supplementaires**, par exemple :
- Fenetres temporelles de passage
- Utilisation de plusieurs vehicules
- Dependances entre les visites
- Capacites de chargement limitees

## Livrables

Les rendus prennent la forme de **Notebooks Jupyter** avec un storytelling soigne. Le code doit etre lisible, commente, performant et respecter les recommandations PEP 8.

### Livrable 1 : Modelisation

- Representation formelle des donnees, du probleme et de l'objectif a optimiser
- Demonstration de la complexite theorique (NP-Completude)
- Justification des choix de modelisation (graphe, contraintes, fonction objectif)

### Livrable 2 : Implementation et Exploitation

- Generateur d'instances aleatoires avec parametres justifies
- Implementation d'au moins **deux methodes de resolution differentes**
- Etude statistique et experimentale rigoureuse (performances, limites, comparaisons)

## Lien avec les boucles d'apprentissage

Le projet s'appuie sur les competences acquises dans les quatre boucles :

| Boucle | Apport pour le projet |
| ------ | --------------------- |
| **Boucle 1 - Theorie des graphes** | Modeliser le reseau routier, choisir la representation adaptee, parcourir le graphe |
| **Boucle 2 - Complexite** | Prouver que le probleme est NP-Complet, comprendre les limites des approches exactes |
| **Boucle 3 - Programmation Lineaire** | Formuler le probleme comme un programme lineaire, utiliser un solveur |
| **Boucle 4 - Methodes de resolution** | Implementer des heuristiques et metaheuristiques pour traiter de grandes instances |

## Organisation

- **Semaine 1** : Prise en main du probleme, modelisation du graphe (Boucle 1)
- **Semaine 2** : Analyse de complexite, preuve NP-C (Boucle 2)
- **Semaine 3** : Premiere resolution par programmation lineaire (Boucle 3)
- **Semaine 4** : Methodes approchees et experimentation (Boucle 4)
- **Rendu final** : Livrables 1 et 2 complets