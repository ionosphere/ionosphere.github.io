---
# PROJ-4 — la SEULE chose à écrire pour que le lien apparaisse sur la carte.
# Toutes les métadonnées (rôle, stack, licence, dépôt, traction) viennent de
# _data/projects.yml : source unique, rien à re-déclarer ici (NFR-6).
ref: ekylibre
---

## Le problème

Une exploitation agricole est une PME industrielle qui s'ignore : elle produit,
transforme, stocke, vend, emploie, investit et rend des comptes — avec, en plus,
le vivant, la météo et vingt ans de réglementation empilée. Les outils qu'on lui
proposait en 2014 traitaient chacun un bout du problème, sans se parler, et
gardaient les données captives.

## Ce qu'on a construit

Un ERP agricole complet, sous licence AGPL-3.0. Plus de trois cents modèles de
données, une base PostgreSQL/PostGIS parce que l'agriculture est
irréductiblement géographique — une parcelle est une géométrie avant d'être une
ligne de tableau.

Le pari de départ était l'**interopérabilité** plutôt que la captivité : des
nomenclatures normalisées (Onoma, puis Lexicon) qui agrègent plus de vingt
millions de références, et une API ouverte. Un agriculteur qui part doit pouvoir
partir avec ses données.

## Mon rôle

Cofondateur et CEO. Concrètement, sur dix ans : le schéma directeur produit et
technique, les standards d'architecture et d'interopérabilité, le management
d'une équipe pluridisciplinaire, la sécurité du SI et la conformité RGPD — et la
direction de l'entreprise, du financement au support client.

## Ce que ça a donné

Le dépôt porte aujourd'hui près de cinq cents étoiles et cent soixante-dix forks.
C'est modeste à l'échelle de GitHub, considérable à l'échelle de l'AgTech
francophone — où les ERP libres se comptent sur les doigts d'une main.

En janvier 2026, nous avons arrêté l'offre SaaS commerciale. Le projet libre,
lui, continue : c'était précisément l'intérêt de le publier sous AGPL dès le
premier commit. Le code ne dépend pas de la survie du modèle économique qui l'a
financé.
