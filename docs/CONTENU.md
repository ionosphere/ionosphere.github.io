# Matière disponible — dépouillement des CV

> Annexe de `SPEC.md` (rév. 3, 2026-07-16). **Ce document n'est pas le contenu du site** :
> c'est la matière brute extraite des deux CV de `docs/ressources/`, avant arbitrage
> éditorial. Il alimentera les `_data/` une fois §7 de la spec fermée.
>
> **Règle de lecture** : ⚠️ marque un **écart entre les deux sources** ou une
> **information non attestée**. Rien de marqué ⚠️ ne doit être publié sans vérification.
>
> **Le parcours est parallèle** (CV-7, rév. 4) : plusieurs expériences se déroulent en
> même temps. Un chevauchement de dates **n'est donc jamais, en soi, l'indice d'une
> erreur** — c'est la forme normale de ce parcours. Le CV DSI, destiné au recrutement,
> a **lissé** cette simultanéité ; le site n'a pas à le suivre sur ce point.

## Sources

### Documents (`docs/ressources/`)

| Fichier | Nature | Positionnement affiché |
| --- | --- | --- |
| `CV-david-joulin (3).pdf` | 4 p., généré par DoYouBuzz | **« Expert AgTech »** |
| `CV_David_JOULIN_DSI.pdf` | 2 p., mise en page soignée | **« Directeur des Systèmes d'Information »** |

Le CV DSI est **plus récent** (il porte le poste chez bziiit démarré en 01/2026) et
paraît avoir corrigé des approximations du DoYouBuzz. **En cas de doute il fait foi** —
sauf pour ce qu'il a **volontairement coupé** (voir « Entrées absentes du CV récent »),
et sauf sur le **rôle chez Ekylibre**, qu'il recadre en « directeur technique » alors que
la bio GitHub de l'intéressé dit **« CEO »**.

### En ligne (dépouillé le 2026-07-16, rév. 6)

| Source | Apport principal |
| --- | --- |
| **`github.com/ionosphere`** | ⚠️ **Compte personnel de David Joulin** — bio, rôles, dépôts épinglés. Renverse la prémisse de la spec. |
| `github.com/ekylibre` | `ekylibre/ekylibre` : **486 ★**, AGPL-3.0, actif juil. 2026 |
| `github.com/osfarm` | 9 dépôts — héberge **Lexicon** et **GAIA** |
| `ekylibre.org` | Projet libre : stack, licences, communauté |
| `ekylibre.com` | ⚠️ **« Fin de notre offre SAAS, Evolution en 2026 »** (17/01/2026) |
| `lexicon.osfarm.org` | 7 catégories, v1.3.3, dépôt REST |
| `gaia-ia.org` | 8 hackathons, 30 sujets, 17 coachs, presse |
| `osfarm.org` | Stack, écosystème, © 2023–2026 |
| `piloterra.fr` *(via recherche)* | Né du hackathon **GAIA au SIA 2024** ; équipe |
| **`ia-des-champs.lovable.app`** | ⚠️ **Le livre** — Éditions France Agricole, 251 termes |
| **`sci-chenes-verts.github.io`** | ⚠️ **La Vauzelle** — le tiers-lieu familial |
| ~~`linkedin.com/in/david-joulin-9b629790`~~ | ❌ **HTTP 999 — non dépouillable** |

> **Ce que la rév. 6 apprend sur la méthode** : les CV **omettaient** plus qu'ils ne se
> trompaient. Un livre, un tiers-lieu, un handle GitHub et 486 étoiles n'y figurent pas.
> Deux conclusions de la rév. 3 — « supprimer ACT-2 faute de matière » et « écart URL /
> identité assumé » — étaient des **artefacts d'une source incomplète**.

---

## Identité

- **Nom** : David JOULIN
- **Titres portés** : « Expert AgTech » (DoYouBuzz) / « Directeur des Systèmes
  d'Information » (CV DSI). ⚠️ **Aucun n'est le one-liner du site** — à rédiger (POS-3).
- **Âge** : 42 ans (DoYouBuzz). Bac en 1999 → naissance vers 1983-1984.
- **Permis de conduire** (DoYouBuzz).

### Contact

| Donnée | Valeur | Décision |
| --- | --- | --- |
| Email | `djoulin@gmail.com` | **Retenu** (CONT-1) |
| LinkedIn | `linkedin.com/in/david-joulin` | **Retenu** (CONT-1) |
| Téléphone | `06 18 60 03 27` | **Écarté** (CONT-3) |
| Localisation | Saint-Porchaire (17) / Bordeaux | ⚠️ Ouvert (CONT-4) |
| GitHub — profil personnel | **`github.com/ionosphere`** ✅ | **Retenu** (CONT-6, rév. 6) |
| GitHub — dépôts projets | `ekylibre/ekylibre` · `osfarm/lexicon` · `osfarm/GAIA-AGRI-IA-QUALIFICATION` | **Acquis** (PROJ-5) — ⚠️ Piloterra manquant |
| LinkedIn | `linkedin.com/in/david-joulin-9b629790` | ⚠️ **Deux URL** — voir ci-dessous |
| Email pro | `djoulin@ekylibre.com` | Écarté au profit du gmail (CONT-1) |

> ⚠️ **Deux URL LinkedIn en circulation** — le **CV DSI** imprime
> `linkedin.com/in/david-joulin` ; l'utilisateur a fourni (rév. 6)
> `linkedin.com/in/david-joulin-9b629790`. La seconde est la forme **par défaut**
> (suffixe généré) ; la première serait une **URL personnalisée**. Si la vanity URL
> n'existe pas, **le CV imprime un lien mort** — à vérifier, et à ne pas reporter tel
> quel sur le site (critère `htmlproofer`, §6).
>
> ⚠️ **LinkedIn n'a pas pu être dépouillé** : le profil renvoie **HTTP 999** (blocage
> anti-robot). Tout ce qu'il contiendrait de plus que les CV — dates réelles, intitulés,
> publications — **reste non collecté**. C'est la seule des neuf sources non exploitée.

### Pitch — base de travail (CV DSI, à réécrire pour POS-4)

> Directeur SI / CTO, 20 ans d'expérience dans la conception, le déploiement et la
> gouvernance de systèmes d'information. Co-fondateur d'un éditeur de logiciels de
> gestion, j'allie vision stratégique, pilotage d'équipes techniques pluridisciplinaires
> et expertise en architecture, sécurité, conformité (RGPD) et valorisation de la donnée.
> Attaché à une culture associative et de service, j'accompagne les métiers et la
> direction dans leur transformation numérique.

Le DoYouBuzz porte une autre présentation, plus personnelle et plus AgTech — utile pour
la synthèse POS-1 :

> Issu du monde agricole, j'ai commencé ma carrière dans l'enseignement professionnel &
> les nouvelles technologies numériques puis me suis dirigé vers le développement
> d'applications, les systèmes d'informations et les données appliqués aux entreprises
> agricoles. La création d'outils de gestion agricole au sens large basée sur des
> technologies libres est mon domaine d'expertise.

---

## Parcours

Ordre antéchronologique. Les colonnes divergentes sont marquées ⚠️.

### bziiit — Piloterra · Bordeaux
**Directeur Technique (CTO)** · 01/2026 → aujourd'hui *(CV DSI uniquement)*
- Direction technique : gestion des projets et des environnements de production numériques.
- Veille technologique IA & Data ; audit, expertise et formation des organisations.

### Ekylibre · Bègles / Saint-Porchaire
⚠️ **Rôle** : « Co-fondateur & **CEO** » (DoYouBuzz) vs « Co-fondateur & **Directeur
technique** » (CV DSI).
⚠️ **Début** : octobre 2014 (DoYouBuzz) vs novembre 2014 (CV DSI).
⚠️ **Fin** : « Aujourd'hui » dans l'expérience du CV DSI, mais « **2015–2025** » dans sa
propre rubrique projets — alors que le poste chez bziiit démarre en 01/2026. **Statut à
clarifier** (§7.2).

Contenu (CV DSI) :
- Définition du schéma directeur produit & technique, des standards d'architecture,
  d'urbanisation et d'interopérabilité.
- Management d'une équipe pluridisciplinaire (développement, support, infrastructure) et
  pilotage des éditeurs & prestataires.
- Gouvernance SI : méthodes, procédures et indicateurs de qualité de service garantissant
  la « déliverabilité » des projets.
- Sécurité du SI : gestion des environnements, sauvegardes, centralisation des logs,
  supervision, incidents, conformité RGPD.
- Pilotage du portefeuille : roadmap produit, sprints, arbitrages budgétaires et mises en
  production.
- Direction d'entreprise : gestion financière, commerciale et RH ; mise en place du
  support clients et de la documentation.

Apports du DoYouBuzz : startup spécialisée dans l'édition d'**outil de gestion open
source pour le monde agricole** ; stratégie long terme **basée sur l'interopérabilité** ;
politique de communication ; stratégie commerciale BtoB / BtoC.

### Ergolis · Bordeaux
**Chef de projet MOA** · ⚠️ **juin 2012** (DoYouBuzz) vs **juillet 2013** (CV DSI) → octobre 2014
> ⚠️ **Un an d'écart, à confirmer.** À « juin 2012 », le poste **chevauche** Bordeaux
> Sciences Agro (qui court jusqu'à 2013) ; à « juillet 2013 », les deux s'enchaînent.
> **Le chevauchement n'est pas une erreur** : le parcours est parallèle par nature
> (CV-7). C'est vraisemblablement le CV DSI qui a **lissé** la simultanéité pour un usage
> de recrutement — pas le DoYouBuzz qui se serait trompé. La date réelle reste à donner.

- Recueil et formalisation des besoins métiers, rédaction des spécifications
  fonctionnelles et du cahier des charges.
- Définition de la méthodologie, du planning, des ressources et des livrables ;
  modélisation et tests fonctionnels.
- Apports DoYouBuzz : traduction FRA/ENG ; modélisation & implémentation (MVC) ;
  expertise métiers (comptabilité, gestion, productions agricoles).

### Bordeaux Sciences Agro (ex-ENITA de Bordeaux) · Gradignan
**Ingénieur applicatifs / Enseignant** · ⚠️ septembre (DoYouBuzz) vs octobre 2008 (CV DSI)
→ ⚠️ mai (DoYouBuzz) vs juin 2013 (CV DSI)
- Chef de projet sur le progiciel **ANAIS** (gestion prévisionnelle agricole) ; expertise
  et maintenance sur **ISTEA** (comptabilité agricole).
- Mise en place du suivi d'incidents, des tests unitaires & fonctionnels et d'un extranet
  client ; ingénieur système & réseau.
- Enseignant (cursus ingénieur & **Mastère Viticulture**).
- **Clients : 85 chambres d'agriculture & ADASEA, 15 centres de gestion.**
- Apports DoYouBuzz : intégration continue (SVN / Redmine) ; déploiement d'une solution
  libre de gestion de parc (OCS / GLPI) ; laboratoire informatique ;
  `http://laboinfonet.enitab.fr/` ⚠️ *(lien probablement mort — à vérifier avant
  publication, htmlproofer)*.

### COBAS · La Teste de Buch / Arcachon
**Ingénieur NTIC** · 09/2006 → 09/2008 *(les deux sources concordent)*
- Gestion du parc, des appels d'offres et du support pour **150 collaborateurs** ;
  documentation technique & applicatifs.
- Pilotage et suivi de projets, animation de réunions, suivi budgétaire et reporting.
- Apports DoYouBuzz : formateur en sciences alimentaires / hygiène ; Intranet / Web (Joomla).

### Entrées absentes du CV récent — ⚠️ à décider (CV-6)

Le CV DSI les a **coupées**. Les réintégrer est un choix éditorial, pas un rattrapage.

> **Elles ont un point commun** : ce sont **exactement les trois expériences parallèles**
> — un freelance mené par-dessus deux postes salariés, une activité agricole tenue
> dix-huit ans, un stage. Un CV de recrutement les coupe pour paraître linéaire ; c'est
> son métier. Le site, lui, doit rendre le parallélisme (CV-7) et sert aussi le pair
> technique (§1). **La question n'est donc pas « faut-il alourdir le parcours ? » mais
> « quelle forme a réellement ce parcours ? ».**

- **Ionosphere Consulting** · Freelance · Bordeaux · **janvier 2008 → décembre 2014**
  **Consultant AgroTIC**. Gestion de projet de réorganisation informatique et migration
  vers des systèmes de gestion **à base de briques libres** pour PMI-PME ; consultant
  AgroTIC « on-demand » ; gestion de projets transversaux.
  > **C'est l'origine du nom de domaine du site.** Voir ID-4 : la décision §1.1 maintient
  > « Ionosphere » invisible côté visiteur malgré cela.
- **GAEC JOULIN** · Bénévolat · Saint-Porchaire · janvier 2002 → décembre 2020
  **Agriculteur à temps partiel** : élevage (alimentation, soin, traite), production
  végétale, conducteur d'engins (presse, moissonneuse-batteuse).
- **Charentes Alliance** · Stage · Saintes · juin 2004 → juin 2005
  **Chargé de mission QSE** : certification « Sécurité Alimentaire », optimisation d'un
  procédé industriel de séchage du maïs pop-corn, audit ATEX de 3 sites.

---

## Formation

| Diplôme | Établissement | Période |
| --- | --- | --- |
| **Ingénieur des travaux agricoles** *(option Qualité et Gestion Agroalimentaire)* | VetAgro Sup (ex-ENITA de Clermont-Ferrand) | 2004–2006 |
| **Ingénieur-Maître en Génie des procédés** | IUP GEPI — Université de La Rochelle | 2002–2004 |
| **DUT Génie Biologique** | IUT de La Rochelle | 2000–2002 |
| **Bac S** ⚠️ *(DoYouBuzz uniquement — coupé du CV récent)* | Lycée Bellevue | 1996–1999 |

⚠️ Trou entre le Bac (juin 1999) et le DUT (septembre 2000) — non expliqué par les CV.

### Formations complémentaires *(DoYouBuzz uniquement)*

- **Ruby / Rails** — Ekylibre, depuis juillet 2012, niveau avancé.
  ⚠️ Antérieur à la fondation d'Ekylibre (fin 2014) — incohérence dans la source.
- **NME — Nouveau Modèle Économique** — CJD, septembre 2021 → juin 2022.
- **PNL niveau 1** — CJD, octobre 2021.
- **J2EE** (EJB3, EntityBean, SessionBean) — Bordeaux Sciences Agro, oct.–déc. 2012.
- **PHP niveau 1 et 2** — ENITA de Bordeaux, sept.–nov. 2010.

---

## Compétences

### Domaines d'expertise (CV DSI)

- **Pilotage & gouvernance SI** — schéma directeur, portefeuille projets, budget, KPI, qualité de service.
- **Architecture & urbanisation** — standards, interopérabilité, Cloud / SaaS, modernisation & simplification.
- **Sécurité & conformité** — PSSI, RGPD, gestion des risques, PCA / PRA, supervision & incidents.
- **Management & partenaires** — équipes pluridisciplinaires, pilotage éditeurs & prestataires.
- **Conduite du changement** — 15 ans de formation & accompagnement des métiers (coopératives agricoles & agroalimentaires).
- **Data & IA** — gouvernance et valorisation de la donnée, **IA frugale & souveraine**.

### Compétences techniques (CV DSI)

| Famille | Éléments |
| --- | --- |
| Langages | PHP, Python, Ruby, SQL |
| Plateforme & déploiement | GitHub, GitLab, CI/CD, Docker, Linux |
| Cloud & poste de travail | Cloud / SaaS, Microsoft 365 |
| Bases de données & ETL | PostgreSQL, PostGIS, BigQuery, Talend, Elastic, n8n |
| IA | Mistral, OpenAI, Anthropic, HuggingFace, Gradio, OpenWebUI, Ollama |
| Outils métiers | MesParcelles, Smag Farmer, Geofolia, QGIS |

> **LANG-4** s'applique : ces jetons ne se traduisent pas et restent tels quels.

Apports du DoYouBuzz, non repris par le CV DSI : Java, SQLite, MySQL, Sybase, CSS3,
HTML5 ; CRM-CMS-ERP open source, BI & reporting (suite Jasper) ; Labview, AutoCAD,
Solidworks, Ecotect ; ANAIS, ISTEA, Planete, STICS, Isamarge, Agreo ; Mailchimp, Slack,
Zendesk, Stripe, Shopify ; modélisation UML / Merise ; GLPI, Redmine, SVN, Git.

### Langues

- **Français** — langue maternelle.
- **Anglais** — courant, **TOEIC 755**.

> Rappel §3.6 : le site est en français uniquement. L'anglais reste une **ligne de CV**,
> pas une version du site.

---

## Projets *(retenus pour le book — §3.3)*

Les quatre sont **agri et open source** : c'est ce qui valide POS-1.
**Enrichis en rév. 6 depuis les sources officielles et GitHub.**

### Ekylibre · 2015–2026 — **la pièce maîtresse**

**ERP agricole open source** (FMIS) — *« Connecting farms to the world »*. Gestion,
traçabilité, comptabilité, interventions culturales, ventes, achats.

| | |
| --- | --- |
| Dépôt | **`github.com/ekylibre/ekylibre`** |
| Traction | **486 ★ · 170 forks · 9 PR ouvertes** |
| Licence | **AGPL-3.0** *(doc en CC-BY-4.0)* |
| Stack | **Ruby**, PostgreSQL, **PostGIS** — *« plus de 300 modèles »* |
| Données | nomenclatures **Onoma** et **Lexicon** — *« plus de 20 millions de références »* |
| Statut | ✅ **actif** — dépôt mis à jour le **6 juillet 2026**, © 2014–2026 |
| Sites | `ekylibre.com` (produit) · `ekylibre.org` (projet libre) · démo `demo.ekylibre-dev.com` |
| Communauté | Discord `discord.gg/BSpD6hq7qR` |
| Rôle de DJ | **Co-fondateur & CEO** ✅ *(sa bio GitHub : « Ekylibre CEO »)* |

Produits commerciaux : **Ekyagri** (gestion d'exploitation), **Ekyviti** (viticole),
**Eky-intégration** (SI agricoles sur mesure). Siège **Saint-Porchaire**. Membre fondateur
de La Ferme Digitale ; associé à OSFarm.

Autres dépôts de l'org : `zero-mobile` (TypeScript, MIT), **`duke`** (chatbot IA, Python,
MIT), `ekylibre-hve` (Ruby, MIT), `ekylibre.github.io`, `ekylibre-traccar`,
`ekylibre-agro-monitoring`, `ekylibre-hajimari`, `ekylibre-idea`.

> ⚠️ **`ekylibre.com`, 17 janvier 2026 : « Fin de notre offre SAAS, Evolution en 2026 ».**
> C'est **l'offre commerciale** qui s'arrête — pas le projet libre (dépôt actif) ni le
> mandat (bio « CEO » au présent). Le « 2015–2025 » du CV décrit vraisemblablement la
> **fenêtre du produit SaaS**. À confirmer.

### Lexicon · 2024–2026

**Open data agricole normalisé.** Explorer → filtrer → exporter en **JSON ou CSV**.

| | |
| --- | --- |
| Dépôts | **`github.com/osfarm/lexicon`** (Ruby, **MIT**, MAJ 26 juin 2026) · **`osfarm/lexicon-rest-api`** (TypeScript, ⚠️ *aucune licence déclarée*) · `osfarm/lexicon-cli` (Ruby, MIT) |
| Version | **v1.3.3** |
| Statut | ✅ **actif** — mais le site avertit : *« encore en cours de développement »* |
| Site | `lexicon.osfarm.org` |
| Porté par | **OSFarm** |
| Rôle de DJ | ⚠️ à préciser *(dépôt épinglé sur son profil)* |

**Sept catégories** de jeux de données : références géographiques, phytosanitaire,
production, entreprises, semences, viticulture, météo. Outil d'identification de parcelle.

> ⚠️ **Le CV annonce « 80 sources » ; le site affiche 7 catégories.** Pas forcément
> contradictoire — 7 catégories peuvent agréger 80 sources — mais **le chiffre 80 n'est
> attesté nulle part publiquement**. À vérifier (PROJ-13).
>
> 🔗 **Lexicon alimente Ekylibre** : c'est l'une de ses deux nomenclatures. Les deux
> projets ne sont pas côte à côte, ils sont **chaînés** (PROJ-12).

### GAIA · 2024–2026

*« Un projet collaboratif ouvert pour démocratiser l'intelligence artificielle dans le
monde agricole »* — **GAIA = Generative Artificial Intelligence for Agriculture**.

| | |
| --- | --- |
| Dépôt | **`github.com/osfarm/GAIA-AGRI-IA-QUALIFICATION`** — *« Détection de projets pour Hackathon Agricole »*, **MIT** |
| Statut | **maintenu** — dépôt figé au **30 juillet 2025** |
| Site | `gaia-ia.org` |
| Porté par | **La Ferme Digitale + OSFarm** — *les deux associations de DJ* |
| Rôle de DJ | ⚠️ **à préciser** — les sources publiques ne le citent **que comme intervenant** sur le hackathon du SIA 2024, **pas comme porteur** |

Chiffres officiels : **8 hackathons**, **30 sujets** proposés, **17 coachs**, 18+
organisations. Démonstrateurs hébergés sur **Hugging Face** : chatbot niveau 1, chatbot
niveau 2 (analyse de PDF), application ravageurs & élevage.
Presse : Plein Champ, BPI France, La France Agricole, Terre Net, Réussir, Ouest-France,
**BFM TV**.

> ⚠️ **Le CV annonce « 80 projets, 8 sessions ».** Le site officiel dit **8 hackathons,
> 30 sujets, 17 coachs**. Les « 8 » concordent ; **« 80 projets » n'est pas attesté**.
> ⚠️ **La distinction « sélectionné parmi 750 projets internationaux à l'IA Summit 2025 »
> — l'atout le plus fort du CV — n'apparaît sur aucune source consultée.** À étayer
> **impérativement** : c'est exactement le genre de claim qu'un pair vérifie (NFR-1).

### Piloterra · 2024–2026

**Portail IA agricole open source.** *« Simplifier le calcul des coûts de production
grâce à l'IA. »* Interrogeable en langage naturel : « Montre-moi mes coûts de
production », « mes coûts de fongicide sur blé ».

| | |
| --- | --- |
| Dépôt | ⚠️ **non trouvé** — les « agents open source » sont revendiqués, le dépôt n'est pas public |
| Stack | **Mistral AI**, **Supabase**, **n8n** |
| Sites | **`piloterra.fr`** · `bziiit.com` |
| Porté par | **bziiit** |
| Rôle de DJ | ⚠️ **à préciser** — voir ci-dessous |

Trois principes affichés : **souveraineté** (agents open source), **frugalité** (impact
carbone mesuré par agent), **collectivité** (catalogue mutualisé d'agents et de données).
bziiit est membre du **Hub France IA** et de l'**Institut du Numérique Responsable**.

> 🔗 **Piloterra est né du premier hackathon IA & agriculture** organisé par
> **Comexposium, La Ferme Digitale et GAIA au SIA 2024**. **GAIA a engendré Piloterra**
> (PROJ-12).
>
> ⚠️ **L'équipe publiée de Piloterra ne mentionne pas David Joulin** (Guillaume
> Chamouleau, Philippe Abram, Laurent Tripied, Cyril Dupland, Paul Arnon, Imad
> Ez-zejjari, Lucie Maurières). Il est **bziiit CTO depuis 01/2026** — donc arrivé après
> la création. Son rôle est **à formuler avec précision** : porter une carte projet sur
> un travail d'équipe antérieur demande de dire *quoi* exactement.

### Le profil GitHub de David Joulin — `github.com/ionosphere` ✅

**Compte utilisateur** (pas une organisation), affiché **« ionosphere (David JOULIN) »**.

- **Bio** : *« Focusing on open source agtech »*
- **Auto-description** : *« **Farmer son, AgroTIC Data engineer, Ekylibre CEO / bziiit
  CTO** »* — **POS-1 en une ligne, écrite par lui avant qu'on ne rédige POS-3.**
- Localisation **Bordeaux** · site `ekylibre.com` · **29 abonnés**, 26 abonnements ·
  **8 dépôts**
- **Épinglés** : `ekylibre/ekylibre` (486 ★) · `osfarm/osfarm.github.io` (3 ★) ·
  `osfarm/lexicon` (1 ★) · `ekylibre/zero-mobile`
- Membre visible de l'org **`ekylibre`**. L'org **`osfarm`** n'a **aucun membre public**.

### Métadonnées PROJ-5 encore manquantes

`tagline` définitive · **`rôle` de DJ sur Lexicon, GAIA et Piloterra** · `visuel` ·
`featured` · dépôt de **Piloterra** · licence de `lexicon-rest-api`.

---

## Engagement associatif *(ACT-3)*

- **La Ferme Digitale** — depuis ⚠️ **2015** (CV DSI) / **mars 2016** (DoYouBuzz)
  - **VP Data & IA** depuis 2022
  - Responsable adhésion 2020–2022 ⚠️ *(le DoYouBuzz dit « Responsable du pôle Synergie &
    Nouveaux membres depuis 2020 » — même poste, autre libellé)*
  - **Trésorier** ⚠️ 2015–2020 (CV DSI) / 2016–2020 (DoYouBuzz)
- **OSFarm** — ⚠️ CV : depuis **2024** · site : **© 2023 – 2026**
  Création de l'association et d'un **fablab de 350 m²** ; hackathons autour des **communs
  numériques agricoles**.
  - Devise : *« Building together a new innovative ecosystem for farms »* ; stack
    revendiquée **« Open source, Sustainable, Full, Affordable, Resilient, Merger »**.
  - **Rôle réel : c'est une infrastructure, pas un engagement décoratif.** L'org
    **`github.com/osfarm`** héberge **Lexicon** et **GAIA** — la moitié du book.
    9 dépôts, licence MIT dominante, **aucun membre public**.
  - Curation d'une stack interopérable : **Agopengps** (guidage tracteur), **Autoplant**,
    **Ecoterrabot** & **Natuition** (robots de désherbage), **E-tract** (binage
    autonome), **Farmbot**, **Ekylibre**.
  - 30+ organisations contributrices ; Discord ; `contact@osfarm.org`.
  - David Joulin **listé parmi les membres de l'équipe** — rôle non spécifié.
- **Seconde Nature** — depuis 2025 · **8 rue du Bouil Bleu, 17250 Saint-Porchaire**
  Recyclerie — *« Réemployer, Réparer, Réutiliser »*. SIRET **941 702 995 00015**.
  Collecte via les déchèteries de la **CDC Cœur de Saintonge** ; boutique **Vinted** ;
  interventions écoles, communes, professionnels. Objectif affiché :
  *« innover avec des technologies ouvertes et durables »*.
  - ✅ **Trésorier — CONFIRMÉ** (rév. 7), attesté par **`seconde-nature.net/faq`** :
    *« **David — Trésorier** (Finance, Achats, **Informatique, IA**, Matériel, Jardin) »*.
    Bureau : Julien (président), **David (trésorier)**, Alexandra et Thomas
    (administrateurs), Amandine (coordinatrice). *(Prénoms seuls sur le site.)*
    → Le portefeuille couvre **informatique et IA** : l'engagement relève de POS-1, pas
    du bénévolat de bon voisinage.
  - ⚠️ **Surface de 2 200 m² non confirmée** par le site.
  - ⚠️ **Fermée pour travaux jusqu'au 30 septembre 2026** — tension avec **ACT-4** :
    une date de réouverture est exactement le type d'information qui périme.
- **NAOS — Nouvelle-Aquitaine Open Source** — 2021–2024
  Pôle de compétences régional en logiciels et technologies libres.

### 🏡 La Vauzelle / SCI des Chênes Verts — **absent des deux CV** (ACT-7)

`sci-chenes-verts.github.io` — **une ferme familiale de 1917 devenue tiers-lieu**, en
Charente-Maritime. **Six structures indépendantes** y partagent bâtiments et réseaux :
agriculture bio, innovation agricole, ESS, recyclerie. *« Chaque structure garde son
indépendance ; toutes partagent bâtiments, réseaux et envie de coopération
transverse. »* © 2020–2026. Site statique, cartes OpenStreetMap.

> **Le recoupement le plus important du dépouillement.** Le CV range « Ferme de la
> Vauzelle » dans les **centres d'intérêt**, entre le potager et le bricolage. Or :
> **Seconde Nature** est une recyclerie « au sein d'un tiers-lieu » à **Saint-Porchaire** ;
> le **GAEC Joulin** est à **Saint-Porchaire** ; **Ekylibre** est domicilié à
> **Saint-Porchaire** ; David Joulin habite **Saint-Porchaire** ; sa bio GitHub commence
> par **« Farmer son »**.
>
> **La ferme familiale est le lieu physique de son écosystème** — et elle a son propre
> site GitHub Pages. Le « fils d'agriculteur » de POS-1 est **une adresse**, pas une
> figure de style. ⚠️ Rôle de DJ dans la SCI **à préciser** ; le site ne le nomme pas.

---

## Talks, conférences, publications *(ACT-2)* — ✅ **la section est sauvée**

La rév. 3 concluait « rien dans les CV → supprimer la section ». **Les CV étaient muets,
pas la réalité.**

### 📕 « L'IA des Champs — une autre culture de l'IA » · Éditions France Agricole

**Un livre chez un éditeur national**, dont **David Joulin est l'un des trois experts**
contributeurs, avec **Hervé Pillaud** et **Karine Cailleaux-Breton**.

- **Rôle de DJ : co-auteur** ✅ *(confirmé rév. 7)*.
- Plateforme associée : **`ia-des-champs.lovable.app`** — **251 termes** illustrés en
  vidéo, glossaire, assistant IA, espace presse.
- Stack : **Mistral AI** (assistant), **Supabase** (contenu), hébergé sur Lovable.
- **Présentation au SIA le 21 février 2026 à 15 h**, stand **La Ferme Digitale**.
- ✅ **Publication, pas cinquième projet** (ACT-6, rév. 7). Le book reste à quatre.

> **C'est l'actif le plus fort du dossier après les 486 ★ d'Ekylibre** — et il est
> **absent des deux CV**. L'angle mort le plus coûteux du dépouillement.

### 📗 « La Vauzelle — Deux siècles de son histoire » · **auteur : Francis JOULIN**

> ⚠️ **David Joulin n'est PAS l'auteur de ce livre.** Voir **ACT-8** — le crédit est une
> exigence de structure, pas une politesse.

| | |
| --- | --- |
| **Auteur** | **Francis JOULIN** — *« Un témoignage de Francis Joulin »* (page de titre) |
| **Rôle de DJ** | **Éditeur** — mise en page & numérisation, travail documentaire, mise en ligne ✅ |
| Sous-titre | *Deux siècles de son histoire* |
| Surtitre | *Tiers-lieu des Chênes Verts · Charente-Maritime* |
| Volume | **209 pages**, **64 chapitres**, de **1822** à nos jours |
| Lieu | **45.83° N · 0.78° O — Saint-Porchaire, Saintonge** |
| Fabrication | LibreOffice Writer, **27 juin 2026** ; métadonnée auteur : « Perso » |
| URL | `sci-chenes-verts.github.io/assets/livre/la-vauzelle-deux-siecles.pdf` (**24 Mo**) |

**Francis Joulin**, d'après sa préface signée : *« né le 03 mars 1933 à La Vauzelle »*,
agriculteur éleveur, retraité en 1993, **sept enfants**. Objectif déclaré : *« laisser un
témoignage pour les générations futures, du réel vécu d'une époque de vie paysanne […]
sans romancer »*. Rédigé aux Petites Séguineries, Saint-Simon de Pellouaille.

**David Joulin n'apparaît dans l'ouvrage qu'à une ligne**, comme enfant qui naît :
*« De leur union le 02 mars 1981 naît un fils prénommé David. »*

> 📌 **Date de naissance : 2 mars 1981** → **45 ans** en 2026. Cohérent avec le bac
> (1996–1999, sorti à 18 ans). ⚠️ **Le CV DoYouBuzz affiche « 42 ans » — il est périmé.**
> **Ne pas publier d'âge** : c'est le cas d'école de ce qu'ACT-4 proscrit.
>
> ⚠️ **Le PDF pèse 24 Mo.** S'il est lié depuis le site, le prévenir — NFR-4 vise la
> performance, et un lien qui déclenche 24 Mo sans avertissement est un piège en mobile.
> *(Le fichier est hébergé par `sci-chenes-verts.github.io`, pas par ce site.)*

### 🎤 Interventions

- **Hackathon GAIA au SIA 2024** — David Joulin **cité comme intervenant** sur
  `gaia-ia.org`.
- ⚠️ Liste probablement incomplète : **8 hackathons GAIA** ont eu lieu.

### 📰 Presse *(couverture de GAIA)*

Plein Champ · BPI France · La France Agricole · Terre Net · Réussir · Ouest-France ·
**BFM TV**.

> ⚠️ **À distinguer** : cette presse couvre **GAIA**, pas David Joulin nommément. Ne pas
> présenter une couverture de projet comme une couverture personnelle (NFR-1).

---

## Centres d'intérêt

Matière disponible, **usage non décidé** — un site « très pro et technologique » (§1) n'a
pas d'obligation d'en porter. À noter toutefois : l'agriculture n'est pas ici un loisir
mais **la racine du récit POS-1**.

- **Agriculture** — fils d'agriculteur, **Ferme de la Vauzelle** ; potager et élevage
  personnel ; ferme familiale polyculture-élevage.
- **Rénovation / DIY** — électricité, plomberie, mécanique ; rénovation de 2 maisons
  (menuiserie, toiture, sol).
- **Sports** — padel, tennis, rugby, VTT, sports de glisse *(DoYouBuzz : volley,
  badminton, hand-ball, wakeboard ; trésorier d'un club de tennis / padel)*.
- **Informatique** *(DoYouBuzz)* — veille technologique sur les outils de gestion open
  source & la domotique.
