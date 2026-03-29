# Projet Fil Rouge : Mobilité Multimodale Intelligente (ADEME / CesiCDP)

Ce dépôt centralise les travaux et ressources du bloc d'apprentissage dédié à la Recherche Opérationnelle. La Recherche Opérationnelle est une discipline qui consiste à mieux comprendre et résoudre les problèmes de décision et d'optimisation, trouvant des applications dans des domaines variés tels que la logistique, la production ou l'ordonnancement. Ce bloc se déroule sur quatre semaines et s'articule autour d'un projet fil rouge nécessitant la mise en œuvre de ces concepts.

## Contexte du Projet

L'ADEME (Agence de l'Environnement et de la Maîtrise de l'Énergie) a lancé un appel à manifestation d'intérêt pour promouvoir de nouvelles solutions de mobilité pour les personnes et les marchandises. En tant que membre de l'équipe de développement de la structure CesiCDP, l'enjeu est de proposer une solution algorithmique d'optimisation logistique performante pour remporter de nouveaux marchés,. 

La mission consiste à concevoir un programme capable de calculer, sur un réseau routier, une tournée permettant de relier un sous-ensemble de villes puis de revenir au point de départ, de manière à minimiser la durée totale du trajet. Ce problème devra impérativement intégrer au moins deux contraintes supplémentaires, comme des fenêtres temporelles de passage, l'utilisation de plusieurs véhicules, des dépendances entre les visites ou encore des capacités de chargement limitées,.

## Livrables Attendus

Les différents rendus de ce projet prendront la forme de Notebooks Jupyter, au sein desquels l'aspect storytelling devra être privilégié pour expliquer la démarche d'analyse et de résolution. Le code source fourni devra être lisible, commenté, performant et respecter les recommandations de bonnes pratiques PEP8.

L'étude transmise à l'ADEME se décompose en deux grands livrables :
*   **Livrable 1 - Modélisation :** Ce document doit proposer une représentation formelle des données, du problème et de l'objectif à optimiser, accompagnée d'une démonstration de la complexité théorique (notamment la NP-Complétude).
*   **Livrable 2 - Implémentation et Exploitation :** Ce rendu final inclut un générateur d'instances aléatoires avec des paramètres justifiés, l'implémentation d'au moins deux méthodes de résolution différentes, ainsi qu'une étude statistique et expérimentale rigoureuse démontrant les performances et les limites des algorithmes proposés,.

## Déroulement des Séquences d'Apprentissage

Le développement de la solution s'appuie sur quatre séquences d'apprentissage (boucles PBL) qui permettent de monter en compétence sur les aspects théoriques et techniques nécessaires :
*   **Boucle 1 - Théorie des graphes :** Modélisation de problèmes et résolution d'itinéraires à l'aide des graphes,.
*   **Boucle 2 - Complexité :** Analyse de la complexité théorique des problèmes de décision et d'optimisation, preuves de NP-Complétude et limites des algorithmes optimaux,.
*   **Boucle 3 - Outils d'optimisation :** Introduction à la Recherche Opérationnelle et modélisation via la Programmation Linéaire,.
*   **Boucle 4 - Méta-heuristiques :** Étude, conception et implémentation de méthodes de résolution approchées (méta-heuristiques) pour faire face aux problèmes d'optimisation difficiles,.

## Préparation de l'environnement

Une séquence de préparation est prévue pour configurer l'espace de travail. L'exécution du code de ce dépôt nécessite l'installation préalable de la distribution Anaconda et la prise en main de l'environnement Jupyter pour lire et éditer les Notebooks.