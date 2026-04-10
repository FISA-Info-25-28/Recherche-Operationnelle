# Glossaire - Recherche Opérationnelle

Ce glossaire regroupe les notions abordées dans les quatre boucles du module de Recherche Opérationnelle (théorie des graphes, complexité, programmation linéaire, métaheuristiques), ainsi que les prérequis des séquences de préparation.

---

## 1. Fondamentaux des graphes

**Graphe.** Structure mathématique composée d'un ensemble de sommets et d'un ensemble d'arêtes reliant ces sommets.

**Sommet (ou nœud).** Élément de base d'un graphe. Représente une entité : une ville, une tâche, un individu, un état.

**Arête.** Lien non orienté entre deux sommets. Une arête `{u,v}` est identique à `{v,u}`.

**Arc.** Lien orienté entre deux sommets. Un arc `(u,v)` est distinct de `(v,u)`.

**Graphe non orienté.** Graphe dont les liens n'ont pas de direction.

**Graphe orienté (digraphe).** Graphe dont les liens ont une direction définie.

**Graphe pondéré.** Graphe dont chaque arête porte une valeur numérique : distance, coût, durée, capacité.

**Graphe simple.** Graphe sans boucle ni arête multiple entre deux mêmes sommets.

**Graphe complet.** Graphe dans lequel chaque paire de sommets est reliée par une arête.

**Degré d'un sommet.** Nombre d'arêtes incidentes à ce sommet.

**Degré entrant / sortant.** Dans un graphe orienté, nombre d'arcs arrivant au sommet (entrant) ou partant du sommet (sortant).

**Lemme des poignées de main.** Dans tout graphe non orienté, la somme des degrés des sommets est égale au double du nombre d'arêtes.

**Chemin.** Suite de sommets reliés successivement par des arêtes.

**Cycle.** Chemin dont le sommet de départ et le sommet d'arrivée sont identiques.

**Voisinage.** Ensemble des sommets directement reliés à un sommet donné.

**Graphe connexe.** Graphe dans lequel il existe un chemin entre toute paire de sommets.

**Composante connexe.** Sous-ensemble maximal de sommets deux à deux reliés par un chemin.

---

## 2. Représentations informatiques

**Matrice d'adjacence.** Tableau carré `n × n` où la case `[i][j]` contient le poids de l'arête entre les sommets `i` et `j`, ou 0 en son absence. Pour un graphe non orienté, la matrice est symétrique. Complexité mémoire en `O(S²)`.

**Liste d'adjacence.** Structure associant à chaque sommet la liste de ses voisins. Plus compacte pour les graphes creux. Complexité mémoire en `O(S + A)`.

**Matrice de distances.** Matrice indiquant, pour chaque paire de sommets, la distance (ou le coût) du plus court chemin entre ces deux sommets.

**Graphe creux.** Graphe dont le nombre d'arêtes est faible devant le nombre de paires de sommets possibles. Favorise la liste d'adjacence.

**Graphe dense.** Graphe dont le nombre d'arêtes est proche du maximum. Favorise la matrice d'adjacence.

---

## 3. Parcours de graphes

**Parcours en largeur (BFS).** Exploration couche par couche à partir d'un sommet de départ. Visite d'abord les voisins directs, puis les voisins des voisins. Utilise une file (FIFO). Utile pour calculer le plus court chemin en nombre d'arêtes dans un graphe non pondéré.

**Parcours en profondeur (DFS).** Exploration en s'enfonçant le plus loin possible dans une branche avant de remonter. Utilise une pile (LIFO) ou la récursion. Utile pour détecter les cycles, les composantes connexes, ou effectuer un tri topologique.

**Sommet visité.** Sommet déjà rencontré au cours d'un parcours, généralement marqué pour éviter de le traiter plusieurs fois.

**Test de connexité.** Vérification qu'un parcours (BFS ou DFS) depuis un sommet atteint bien tous les autres sommets du graphe.

**Détection de cycle (DFS).** Lors d'un parcours en profondeur d'un graphe non orienté, la rencontre d'un sommet déjà visité qui n'est pas le parent direct révèle la présence d'un cycle.

---

## 4. Plus courts chemins

**Algorithme de Dijkstra.** Algorithme de recherche du plus court chemin depuis un sommet source vers tous les autres sommets d'un graphe pondéré à poids positifs. Sélectionne à chaque étape le sommet non visité le plus proche. Son implémentation optimisée repose sur une file de priorité (tas binaire).

**File de priorité.** Structure de données dans laquelle les éléments sont extraits selon une clé de priorité. Centrale dans l'implémentation efficace de Dijkstra.

**Distance.** Poids total d'un chemin ; pour Dijkstra, distance minimale accumulée depuis la source.

**Prédécesseur.** Sommet qui précède un sommet donné sur le plus court chemin. Permet de reconstruire le chemin une fois les distances calculées.

**Reconstruction de chemin.** Procédé qui remonte, à partir du sommet d'arrivée, la chaîne des prédécesseurs jusqu'à la source.

---

## 5. Cycles particuliers

**Cycle eulérien.** Cycle qui emprunte chaque arête du graphe exactement une fois et revient au sommet de départ.

**Chemin eulérien.** Chemin qui emprunte chaque arête exactement une fois, sans nécessairement revenir au point de départ.

**Théorème d'Euler.** Un graphe connexe non orienté possède un cycle eulérien si et seulement si tous ses sommets sont de degré pair. Il possède un chemin eulérien si et seulement si exactement deux sommets sont de degré impair.

**Algorithme de Hierholzer.** Algorithme linéaire en nombre d'arêtes permettant de construire un cycle eulérien. Il parcourt le graphe à l'aide d'une pile en supprimant les arêtes utilisées, puis inverse le chemin obtenu.

**Cycle hamiltonien.** Cycle qui passe par chaque sommet du graphe exactement une fois et revient au point de départ. À ne pas confondre avec le cycle eulérien (qui concerne les arêtes).

**Chemin hamiltonien.** Chemin qui passe par chaque sommet exactement une fois sans nécessairement former un cycle.

**Problème hamiltonien.** Problème consistant à déterminer si un graphe donné admet un cycle hamiltonien. Il est NP-complet.

---

## 6. Complexité algorithmique

**Problème algorithmique.** Couple constitué d'un format d'entrée et d'une question précise posée sur ces données.

**Instance.** Ensemble de valeurs concrètes respectant le format d'entrée d'un problème.

**Problème de décision.** Problème dont la réponse attendue est « oui » ou « non ».

**Problème d'optimisation.** Problème consistant à maximiser ou minimiser une fonction objectif sous contraintes.

**Notation de Landau.** Notation asymptotique utilisée pour décrire le comportement d'un algorithme : `O(·)` pour une borne supérieure, `Ω(·)` pour une borne inférieure, `Θ(·)` pour un encadrement.

**Complexité temporelle.** Mesure du nombre d'opérations élémentaires exécutées par un algorithme en fonction de la taille de l'entrée.

**Complexité spatiale.** Mesure de la quantité de mémoire utilisée par un algorithme en fonction de la taille de l'entrée.

**Temps polynomial.** Temps d'exécution borné par un polynôme en la taille de l'entrée : `O(n^k)`.

**Temps exponentiel.** Temps d'exécution de la forme `O(k^n)` ou `O(n!)`, généralement prohibitif dès que `n` dépasse quelques dizaines.

**Machine de Turing.** Modèle théorique de calcul défini par un ensemble d'états, un alphabet, une fonction de transition, un état initial et un ensemble d'états acceptants. Sert de référence pour définir les classes de complexité.

---

## 7. Classes de complexité

**Classe P.** Ensemble des problèmes de décision résolubles en temps polynomial par une machine de Turing déterministe. Exemples : tri, recherche dichotomique, plus court chemin avec Dijkstra.

**Classe NP.** Ensemble des problèmes de décision pour lesquels une solution candidate (certificat) peut être vérifiée en temps polynomial. Exemples : SAT, TSP (version décision), clique.

**Classe co-NP.** Ensemble des problèmes dont le complément appartient à NP : on peut vérifier en temps polynomial qu'une solution n'existe pas.

**NP-complet.** Problème appartenant à NP auquel tout autre problème de NP peut être réduit en temps polynomial. Les problèmes NP-complets sont les plus difficiles de NP.

**NP-difficile.** Problème au moins aussi difficile que n'importe quel problème de NP, sans être nécessairement lui-même dans NP.

**Réduction polynomiale.** Transformation d'une instance d'un problème A en une instance d'un problème B, effectuée en temps polynomial, qui préserve la réponse. Outil fondamental pour prouver qu'un problème est NP-complet.

**Théorème de Cook-Levin.** Résultat fondateur établissant que SAT est NP-complet. Premier problème démontré comme tel, il sert de point d'ancrage pour les autres preuves de NP-complétude.

**Problème SAT.** Problème de la satisfiabilité d'une formule booléenne : existe-t-il une assignation des variables rendant la formule vraie ?

**Hypothèse P = NP.** Question ouverte majeure de l'informatique théorique. Sa résolution positive impliquerait qu'un algorithme polynomial existe pour tous les problèmes NP-complets.

---

## 8. Problèmes classiques

**Problème du voyageur de commerce (TSP).** Étant donné un ensemble de villes et les distances entre elles, trouver la tournée passant une fois par chaque ville et de distance totale minimale. NP-difficile.

**Problème du sac à dos.** Sélectionner parmi un ensemble d'objets, chacun ayant un poids et une valeur, un sous-ensemble maximisant la valeur totale sans dépasser une capacité fixée. NP-complet dans sa version 0/1.

**Problème de la clique.** Déterminer s'il existe dans un graphe un sous-graphe complet de taille `k`.

**Couverture de sommets (Vertex Cover).** Trouver un ensemble de sommets de taille minimale tel que chaque arête ait au moins une extrémité dans cet ensemble.

**Coloration de graphe.** Attribuer une couleur à chaque sommet de telle sorte que deux sommets adjacents aient des couleurs différentes, en minimisant le nombre de couleurs utilisées.

**Bin packing.** Répartir un ensemble d'objets dans le minimum possible de contenants de capacité fixe.

**Problème des N reines.** Placer `N` reines sur un échiquier `N × N` sans qu'aucune ne puisse en attaquer une autre.

---

## 9. Programmation linéaire

**Programme linéaire (PL).** Problème d'optimisation dont la fonction objectif et les contraintes sont des expressions linéaires des variables de décision.

**Variables de décision.** Quantités inconnues dont on cherche les valeurs optimales.

**Fonction objectif.** Expression linéaire à maximiser ou minimiser.

**Contraintes.** Inégalités ou égalités linéaires que doivent respecter les variables.

**Domaine admissible.** Ensemble des solutions satisfaisant toutes les contraintes. Géométriquement, il forme un polyèdre convexe.

**Solution optimale.** Point du domaine admissible qui maximise ou minimise la fonction objectif. Elle se trouve toujours sur un sommet du polyèdre.

**Résolution graphique.** Méthode visuelle applicable aux problèmes à deux variables : on trace le domaine admissible et on fait glisser la droite de la fonction objectif.

**Algorithme du simplexe.** Méthode classique de résolution des programmes linéaires. Parcourt les sommets du polyèdre admissible en améliorant l'objectif à chaque étape.

**Programmation linéaire en nombres entiers (PLNE).** Variante où tout ou partie des variables doivent prendre des valeurs entières. Résolution beaucoup plus coûteuse : problème NP-difficile en général.

**Relaxation linéaire.** Technique consistant à ignorer la contrainte d'intégrité pour obtenir rapidement une borne sur la solution optimale entière.

**Formulation MTZ.** Formulation de Miller-Tucker-Zemlin utilisée pour éliminer les sous-tours dans une modélisation PLNE du TSP.

**PuLP.** Bibliothèque Python de modélisation et de résolution de programmes linéaires.

---

## 10. Paradigmes algorithmiques

**Force brute (brute force).** Approche consistant à énumérer toutes les solutions possibles pour retenir la meilleure. Garantit l'optimum mais devient impraticable dès que la taille du problème augmente.

**Algorithme glouton (greedy).** Construit une solution étape par étape en faisant à chaque étape le choix localement optimal, sans revenir en arrière. Rapide mais ne garantit pas l'optimum global.

**Backtracking (retour sur trace).** Exploration systématique de l'espace des solutions sous forme d'arbre, avec abandon des branches dès qu'elles deviennent incompatibles avec les contraintes (élagage).

**Élagage (pruning).** Technique d'optimisation du backtracking qui consiste à couper les branches de l'arbre de recherche ne pouvant mener à une solution valide ou meilleure que la meilleure déjà trouvée.

**Programmation dynamique.** Technique applicable aux problèmes présentant des sous-problèmes qui se recoupent et une structure optimale. Repose sur la mémorisation des résultats déjà calculés pour éviter les recalculs.

**Approche descendante (top-down).** Implémentation récursive de la programmation dynamique avec mémoïsation : on résout le problème principal et on mémorise les sous-problèmes au fur et à mesure.

**Approche ascendante (bottom-up).** Implémentation itérative : on résout d'abord les plus petits sous-problèmes et on combine leurs résultats pour construire la solution finale.

**Mémoïsation.** Technique consistant à stocker dans un cache les résultats des appels de fonction déjà effectués pour éviter de les recalculer.

**Structure optimale.** Propriété selon laquelle la solution optimale d'un problème peut être construite à partir des solutions optimales de ses sous-problèmes.

**Heuristique.** Méthode approchée qui fournit une solution de bonne qualité en un temps raisonnable, sans garantie d'optimalité.

**Heuristique du plus proche voisin.** Heuristique gloutonne pour le TSP consistant à toujours se rendre à la ville non visitée la plus proche.

---

## 11. Algorithmes probabilistes et métaheuristiques

**Algorithme probabiliste.** Algorithme qui utilise le hasard au cours de son exécution. Regroupe deux grandes familles : Las Vegas et Monte Carlo.

**Algorithme de Las Vegas.** Algorithme probabiliste qui fournit toujours un résultat exact, mais dont le temps d'exécution peut varier. Exemple : Quicksort randomisé.

**Algorithme de Monte Carlo.** Algorithme probabiliste dont le temps d'exécution est borné mais dont le résultat peut être erroné avec une probabilité faible et contrôlée. Exemple : test de primalité de Miller-Rabin.

**Méthode de Monte Carlo.** Technique d'estimation numérique par tirages aléatoires. Utilisée notamment pour l'estimation de π ou l'intégration numérique.

**Algorithme de Rabin-Karp.** Algorithme probabiliste de recherche de motif dans une chaîne, basé sur le hachage.

**Algorithme de Karger.** Algorithme probabiliste de recherche d'une coupe minimale dans un graphe par contraction aléatoire d'arêtes.

**Métaheuristique.** Méthode générique d'optimisation approchée applicable à une large classe de problèmes, sans exploiter la structure fine du problème traité.

**Algorithme génétique.** Métaheuristique inspirée de l'évolution biologique. Fait évoluer une population de solutions par sélection, croisement et mutation.

**Population.** Ensemble de solutions candidates manipulées par un algorithme génétique.

**Individu (ou chromosome).** Solution candidate unique au sein de la population.

**Gène.** Composante élémentaire d'un individu, correspondant à une variable de décision.

**Fitness (fonction d'évaluation).** Fonction qui mesure la qualité d'un individu au regard de l'objectif.

**Sélection.** Étape choisissant les individus qui vont se reproduire, typiquement par roulette, par tournoi ou par élitisme.

**Croisement (recombinaison).** Opérateur combinant deux individus parents pour produire un ou plusieurs individus enfants.

**Mutation.** Modification aléatoire et de faible amplitude d'un individu, destinée à maintenir la diversité et à éviter la convergence prématurée.

**Élitisme.** Stratégie conservant systématiquement les meilleurs individus d'une génération à la suivante.

**Convergence.** État dans lequel la population d'un algorithme évolutionnaire cesse de s'améliorer de façon significative.

---

## 12. Bibliothèques et outils utilisés

**NetworkX.** Bibliothèque Python dédiée à la manipulation, l'analyse et la visualisation de graphes.

**Matplotlib.** Bibliothèque Python de visualisation scientifique, utilisée pour tracer graphes, courbes et diagrammes.

**Seaborn.** Bibliothèque de visualisation statistique bâtie sur Matplotlib.

**heapq.** Module standard Python implémentant une file de priorité (tas binaire), utilisé notamment dans Dijkstra.

**PuLP.** Bibliothèque Python de modélisation de programmes linéaires et de programmes linéaires en nombres entiers.
