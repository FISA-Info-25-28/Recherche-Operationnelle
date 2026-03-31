# Projet Fil Rouge : Optimisation de Tournées de Véhicules (ADEME / CesiCDP)

## 1. Contexte

L'ADEME (Agence de l'Environnement et de la Maîtrise de l'Énergie) a lancé un appel à manifestation d'intérêt pour promouvoir de nouvelles solutions de mobilité pour les personnes et les marchandises.

Votre structure **CesiCDP**, déjà implantée dans le domaine de la Mobilité Multimodale Intelligente, souhaite répondre à cet appel. Les applications sont nombreuses : distribution du courrier, livraison de produits, traitement du réseau routier, ramassage des ordures. Leur impact environnemental peut être significatif.

## 2. Problème à résoudre

**Objectif** : sur un réseau routier, calculer une tournée reliant un sous-ensemble de villes et revenant au point de départ, en **minimisant la durée totale du trajet**.

## 3. Contraintes supplémentaires

Le problème de base doit **obligatoirement** intégrer **au moins deux contraintes supplémentaires** : une contrainte temporelle et une contrainte véhicule. Vous pouvez en ajouter d'autres pour enrichir votre modélisation.

### 3.1 Contraintes temporelles (au moins une obligatoire)

Ces contraintes ajoutent une dimension **temps** au problème : les visites et les trajets ne peuvent plus se faire à n'importe quel moment.

| Contrainte | Description | Exemple concret |
| --- | --- | --- |
| **Fenêtres temporelles** | Chaque ville doit être visitée dans un intervalle de temps donné. | La ville A n'accepte les livraisons qu'entre 8h et 10h. |
| **Dépendances entre visites** | Une ville ne peut être visitée qu'après une autre (relation de précédence). | On doit charger au dépôt B avant de livrer au client C. |
| **Routes dynamiques** | Les coûts ou la disponibilité des routes changent au cours du temps. | Un embouteillage double le temps de trajet sur la route X à partir de 17h. |

**Comment les modéliser concrètement ?**

- **Fenêtres temporelles** : chaque ville `i` est associée à un couple `(ouverture_i, fermeture_i)`. Le véhicule doit arriver avant `fermeture_i`. S'il arrive avant `ouverture_i`, il attend sur place (temps d'attente à intégrer dans le coût). La variable `t_i` représente l'heure d'arrivée à la ville `i` et doit vérifier : `ouverture_i <= t_i <= fermeture_i`. Les temps de trajet entre villes doivent être additionnés au fur et à mesure du parcours.
- **Dépendances entre visites** : définir une liste de couples `(i, j)` signifiant "la ville `i` doit être visitée avant la ville `j`". Cela se traduit par une contrainte de précédence : `position(i) < position(j)` dans la tournée, ou `t_i + durée_trajet <= t_j` en formulation temporelle.
- **Routes dynamiques** : définir des créneaux sur les arêtes. Par exemple, l'arête `(i, j)` a un coût `c1` entre 8h et 17h et un coût `c2` après 17h. Le coût utilisé dépend de l'heure à laquelle le véhicule emprunte la route. Cela rend la matrice des coûts dépendante du temps.

### 3.2 Contraintes véhicules (au moins une obligatoire)

Ces contraintes portent sur les **ressources physiques** : nombre de véhicules, ce qu'ils peuvent transporter, comment répartir le travail.

| Contrainte | Description | Exemple concret |
| --- | --- | --- |
| **Multi-véhicules** | Plusieurs véhicules effectuent des sous-tournées au lieu d'une seule grande tournée. | Une flotte de 3 camions se répartit 20 villes à livrer. |
| **Capacités de chargement** | Chaque véhicule a une limite de poids ou de volume. Nécessite la contrainte multi-véhicules. | Un camion ne peut transporter que 500 kg ; au-delà, il faut un autre véhicule. |
| **Équilibrage de charge** | Répartir équitablement les villes ou la distance entre les véhicules. Nécessite la contrainte multi-véhicules. | Aucun camion ne doit faire plus du double du trajet d'un autre. |
| **Coûts/restrictions sur les arêtes** | Certaines routes sont plus coûteuses ou interdites selon le type de véhicule. | Les poids lourds ne peuvent pas emprunter les routes de montagne. |

**Comment les modéliser concrètement ?**

- **Multi-véhicules** : on dispose de `K` véhicules, chacun partant et revenant au dépôt (ville 0). Le problème revient à trouver `K` sous-tournées qui, ensemble, couvrent toutes les villes exactement une fois. Chaque ville est assignée à exactement un véhicule.
- **Capacités de chargement** : chaque ville `i` a une demande `d_i` (poids ou volume à livrer). Chaque véhicule `k` a une capacité maximale `Q_k`. La somme des demandes des villes assignées à un véhicule ne doit pas dépasser sa capacité : `somme(d_i) <= Q_k`.
- **Équilibrage de charge** : ajouter une contrainte limitant l'écart entre véhicules. Par exemple : la distance totale du véhicule le plus chargé ne doit pas dépasser `alpha` fois celle du moins chargé (avec `alpha` un facteur choisi, ex : 1.5 ou 2.0).
- **Coûts/restrictions sur les arêtes** : définir une matrice de coûts par type de véhicule, ou une liste d'arêtes interdites pour certains types. Par exemple, `interdit[k][(i,j)] = True` si le véhicule `k` ne peut pas emprunter la route `(i,j)`.

### 3.3 Contraintes libres (optionnelles)

Vous pouvez proposer vos propres contraintes supplémentaires, **en concertation avec votre tuteur**. Quelques pistes :

- Véhicules hétérogènes (vitesses ou capacités différentes)
- Points de recharge ou de ravitaillement obligatoires
- Livraisons avec collecte simultanée (pickup and delivery)
- Pénalités en cas de retard (soft time windows)

> **Attention aux dépendances** : "Capacités de chargement" et "Équilibrage de charge" nécessitent d'avoir choisi "Multi-véhicules". Elles comptent chacune comme une contrainte à part entière.

## 4. Données et instances

### 4.1 Générateur d'instances aléatoires

Votre générateur doit produire des instances paramétrables. Voici les paramètres à définir et justifier :

| Paramètre | Description | Exemple de valeurs |
| --- | --- | --- |
| `n` | Nombre de villes (hors dépôt) | 5 à 200 |
| `K` | Nombre de véhicules (si multi-véhicules) | 2 à 10 |
| Type de graphe | Complet (toutes les villes reliées) ou partiel (certaines routes manquantes) | Complet pour les petites instances, partiel pour le réalisme |
| Positions des villes | Coordonnées (x, y) générées aléatoirement dans un espace 2D | Uniforme dans un carré [0, 100] x [0, 100] |
| Coûts des arêtes | Distance euclidienne entre les villes, ou temps de trajet | `cout(i,j) = sqrt((xi-xj)^2 + (yi-yj)^2)` |
| Demandes | Poids/volume à livrer par ville (si capacités) | Uniforme entre 1 et 20 |
| Capacité véhicule | Charge maximale par véhicule (si capacités) | Ajustée pour que tous les véhicules soient nécessaires |
| Fenêtres temporelles | Intervalle `[ouverture, fermeture]` par ville (si fenêtres) | Générées pour qu'au moins une solution faisable existe |

**Point important** : vos instances doivent être **faisables** (il existe au moins une solution qui respecte toutes les contraintes). Vérifiez-le lors de la génération, notamment pour les fenêtres temporelles et les capacités.

Il est attendu de générer des instances de **tailles variées** (petites pour la validation, grandes pour l'étude expérimentale) afin de pouvoir étudier le passage à l'échelle de vos algorithmes.

### 4.2 Utilisation de données réelles (optionnel, bonus)

En complément du générateur, vous pouvez utiliser des **données réelles** pour tester vos algorithmes dans un contexte plus réaliste. Quelques sources possibles :

- **TSPLIB** : bibliothèque de référence contenant des instances classiques du TSP et du VRP (Vehicle Routing Problem). Disponible à l'adresse : `http://comopt.ifi.uni-heidelberg.de/software/TSPLIB95/`
- **CVRPLIB** : instances spécifiques au VRP avec capacités. Disponible à l'adresse : `http://vrp.atd-lab.inf.puc-rio.br/`
- **OpenStreetMap** (via la bibliothèque `osmnx` en Python) : extraction de réseaux routiers réels avec distances et temps de trajet

L'utilisation de données réelles n'est **pas obligatoire**, mais c'est un plus appréciable pour la soutenance et l'étude expérimentale. Si vous utilisez des données réelles, documentez leur provenance et le traitement appliqué pour les adapter à votre modélisation.

## 5. Livrables

Tous les livrables prennent la forme de **Notebooks Jupyter** avec un storytelling soigné. Le code doit être lisible, commenté, performant et respecter les [recommandations PEP 8](https://openclassrooms.com/fr/courses/235344-apprenez-a-programmer-en-python/235263-de-bonnes-pratiques).

### Livrable 1 - Modélisation (check, non évalué)

Point d'avancement avec le tuteur pour valider la modélisation. **Ne pas aborder les méthodes de résolution.**

Contenu attendu :

- Présentation du problème et de son contexte
- **Représentation formelle** des données, du problème et de la fonction objectif
- **Preuve de NP-Complétude** du problème (avec les contraintes choisies, pas juste la version de base)
- Justification des choix de modélisation
- Références bibliographiques (articles, ouvrages scientifiques)

### Livrable 2 - Final (évalué)

Se compose de **deux parties** :

#### Partie 1 - Modélisation (mise à jour)

- Reprise et mise à jour de la modélisation du livrable 1
- Description détaillée des méthodes de résolution choisies (algorithmes, justifications)

#### Partie 2 - Implémentation et exploitation

| Volet | Contenu |
| --- | --- |
| **Générateur d'instances** | Génération aléatoire d'instances avec paramètres justifiés (graphes complets ou non, taille des liens, nombre de villes, etc.) |
| **Résolution** | Implémentation d'**au moins deux méthodes de résolution différentes** |
| **Démonstration** | Tests sur différents cas montrant que le code fonctionne |
| **Étude expérimentale** | Plan d'expérience complet : performances, limitations, comparaisons entre méthodes, et propositions d'améliorations. Le tout doit être justifié de manière détaillée. |

### Soutenance (évaluée)

**Format** : 15 minutes de présentation + 15 minutes de questions avec le jury.

**Support** : slides obligatoires + démonstration live du notebook. Les slides doivent être claires, synthétiques, et visuellement attrayantes. La démonstration doit être fluide, avec des instances suffisamment petites pour éviter les temps de calcul trop longs.

**Posture attendue** : la soutenance se place dans le contexte du projet ADEME. Vous êtes un ingénieur technico-commercial qui présente la solution de CesiCDP à un client. L'objectif est de **convaincre** que votre approche est la bonne, sans noyer l'audience dans les détails techniques. Le jury doit comprendre pourquoi votre solution fonctionne, pas comment elle est codée ligne par ligne.

**Contenu attendu** :

- Rappel du contexte ADEME et du problème traité (bref, 2-3 min max)
- Présentation des contraintes choisies et pourquoi elles sont pertinentes pour le cas d'usage
- Présentation des méthodes de résolution retenues, vulgarisées pour un public non technique
- Démonstration live sur le notebook (sur des instances suffisamment petites pour que ce soit fluide)
- Résultats obtenus : graphiques, comparaisons, chiffres clés
- Limites identifiées et pistes d'amélioration

**Ce qui sera évalué lors des questions** :

- Votre compréhension du problème et des choix effectués
- Votre capacité à justifier vos décisions (pourquoi cette méthode plutôt qu'une autre ?)
- Votre recul critique sur les résultats (qu'est-ce qui marche, qu'est-ce qui ne marche pas, pourquoi ?)

> **Bonus** : vous pouvez créer une interface interactive avec **Streamlit** pour présenter vos résultats. Cela permet de visualiser les tournées sur une carte, d'ajuster les paramètres en temps réel (nombre de véhicules, capacités, taille de l'instance...) et de comparer visuellement les méthodes de résolution. C'est un plus apprécié lors de la soutenance, mais ce n'est pas obligatoire.
