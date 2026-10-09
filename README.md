# Base de données immobilière — SQL

Projet réalisé dans le cadre de ma **certification Data Analyst**.

## Présentation

Ce projet consiste à concevoir et exploiter une base de données relationnelle consacrée aux transactions immobilières afin de répondre à différentes problématiques métier à l'aide de requêtes SQL.

L'objectif était de structurer les données, construire le modèle relationnel puis produire des analyses sur les volumes de ventes, les prix immobiliers et les différences géographiques.

## Compétences mises en œuvre

- Conception et exploitation d'une base de données relationnelle
- Modélisation conceptuelle et relationnelle
- Création et utilisation de requêtes SQL
- Jointures entre plusieurs tables
- Agrégations avec `COUNT`, `AVG`, `SUM` et `GROUP BY`
- Utilisation de CTE avec `WITH`
- Filtres temporels et géographiques
- Calculs de pourcentages et d'évolutions
- Classement avec `RANK() OVER (PARTITION BY ...)`
- Traduction de problématiques métier en analyses SQL

## Analyses réalisées

Les requêtes développées permettent notamment de :

- analyser le volume de ventes d'appartements ;
- étudier la répartition des appartements selon le nombre de pièces ;
- identifier les départements présentant les prix au m² les plus élevés ;
- calculer le prix moyen au m² des maisons en Île-de-France ;
- identifier les appartements ayant les valeurs foncières les plus importantes ;
- comparer les volumes de ventes entre différentes périodes ;
- analyser l'évolution des ventes par commune ;
- comparer le prix moyen des appartements de 2 et 3 pièces ;
- identifier les communes présentant les valeurs foncières moyennes les plus élevées par département.

## Techniques SQL utilisées

```sql
SELECT code_dep,
       ROUND(AVG(valeur_fonciere / surface_m2), 2) AS prix_m2
FROM adresse
NATURAL JOIN logements
NATURAL JOIN valeur_fonciere
GROUP BY code_dep
ORDER BY prix_m2 DESC
LIMIT 10;
```
Le projet utilise également des fonctions de fenêtrage permettant d'effectuer des classements par groupe :

```sql
RANK() OVER (
    PARTITION BY code_dep
    ORDER BY moyenne DESC
)
```

## Contenu du dépôt

Le dépôt comprend :

- les scripts SQL utilisés pour répondre aux différentes problématiques ;
- le modèle conceptuel UML de la base de données ;
- le schéma relationnel ;
- une capture du SGBD ;
- une présentation du projet ;
- une documentation complémentaire des requêtes.

## Ce que ce projet démontre

Au-delà de l'écriture de requêtes SQL, ce projet montre ma capacité à partir d'une problématique métier, structurer les données dans un modèle relationnel puis produire des indicateurs et des analyses directement interprétables.

**Outils :** SQL · Base de données relationnelle · UML · Draw.io
