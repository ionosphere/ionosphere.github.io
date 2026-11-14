---
# PROJ-4 — la seule chose à écrire pour que le lien apparaisse sur la carte.
# Métadonnées ET vidéo : _data/projects.yml (NFR-6).
ref: fourmy
---

## Le problème

Ekylibre a dix ans de modèle de données, et ça se sent. Il fait tout, mais
l'agriculteur doit tout saisir, et chaque écran demande de connaître le logiciel
avant de connaître sa ferme. Les tracteurs savent pourtant déjà où ils sont
passés, les stations météo savent quel temps il faisait, et le ministère publie
l'usage autorisé de chaque produit.

## Ce que je construis

Fourmy est la **réécriture complète d'Ekylibre** : un jumeau numérique de la
ferme. Parcelles, interventions, stocks, cuves et matériels vivent dans un modèle
**daté** : on peut revoir la ferme à n'importe quelle date, sur la carte ou en 3D.

La saisie part de ce que la ferme sait déjà :

- les **boîtiers GPS** des tracteurs découpent la journée en parcours, et deux
  clics en font une intervention, avec ses heures et sa surface ;
- la **météo** de chaque intervention est gardée ;
- les **contrôles réglementaires** se font à la saisie (dose, usage autorisé, ZNT,
  délais), l'**IFT** est calculé par le service du ministère, et le registre
  phytosanitaire se remplit seul.

Les données d'Ekylibre sont reprises telles quelles : trois fermes pilotes ont été
migrées, avec un registre phyto identique à l'original.

## Pourquoi c'est un maillon

Fourmy est la mémoire de la ferme dans la chaîne qui va de la donnée publique au
robot : il lit Lexicon, et Aiffel y écrit à la voix. Un robot agricole a besoin
de la même chose qu'un agriculteur : savoir ce qui a été fait, où et quand.

## Mon rôle

Créateur : conception, architecture et développement. Le dépôt est public, sous
licence AGPL-3.0, et l'application est en ligne sur fourmy.org depuis novembre
2026.
