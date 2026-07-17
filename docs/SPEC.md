# Site personnel — David Joulin — Spécification des besoins

> Statut : **✅ SITE EN LIGNE** — `https://ionosphere.github.io` (2026-07-17).
> Découverte close (rév. 7), design fait, implémentation faite et déployée. Restent des
> **faits à vérifier** (§7.2) qui n'ont **pas** empêché la mise en ligne mais qu'il faut
> fermer.
>
> Ce document décrit **le quoi et le pourquoi**. Le **comment** est dans
> **`docs/DESIGN.md`** ; la matière factuelle dans **`docs/CONTENU.md`** ; les sources
> dans **`docs/ressources/`** ; les pièges de maintenance dans **`CLAUDE.md`**.
>
> **Le design a amendé deux points de cette spec** — §5 (Bootstrap abandonné : il
> contredisait §6) et PROJ-7 (filtres : non implémentés). Voir `DESIGN.md` §7.
>
> **Ce que l'implémentation a appris** *(le détail est en `DESIGN.md` §8.1)* :
> - **CV-7 tient partout** — écran, mobile 390 px **et** impression A4. Le design
>   proposait d'y renoncer sous 600 px : c'était un repli inutile, la grille tient.
> - **CV-4 est acquis** — le PDF sort en A4, bandes contourées lisibles en noir et blanc,
>   URL en toutes lettres, aucun téléphone.
> - **PROJ-3 / PROJ-4 sont prouvés** par test réel, pas supposés.
> - ⚠️ **Un piège YAML a publié `{"Élevage"=>"…"}` sur le CV en production.** Dix faits
>   touchés, aucun échec de build. Voir `CLAUDE.md`.
>
> **Révision 1 du 2026-07-16** — arbitrage utilisateur : **site en français uniquement**
> pour l'instant. Le bilingue FR/EN et toute sa mécanique sortent du périmètre ; la
> tension I18N-4 (études de cas en prose longue vs. chaînes en `_data`) est **résolue par
> disparition**. Voir §3.6.
>
> **Révision 2 du 2026-07-16** — quatre arbitrages utilisateur ferment les questions
> ouvertes 3, 4 et 5, et fixent la méthode de collecte du contenu (question 1) :
> identité **« David Joulin », site personnel** (§1) ; PDF du CV = **rendu print de la
> page**, source unique (§3.2) ; **aucun analytics** (§2) ; le contenu factuel sera
> **extrait d'un CV existant fourni par l'utilisateur** (§7). Reste bloquant : le
> **nom de domaine**, et la fourniture effective du CV.
>
> **Révision 3 du 2026-07-16** — les **deux dernières questions bloquantes tombent**.
> Domaine : **pas de domaine personnalisé**, l'URL est `https://ionosphere.github.io`
> (§5). Contenu : **deux CV fournis** et dépouillés (`docs/ressources/`), matière
> reportée dans **`docs/CONTENU.md`**. Positionnement retenu : **synthèse « CTO open
> source, agriculture & données »** (§1). Book amorcé avec **quatre projets** (§3.3).
> Contact : **email + LinkedIn, sans téléphone** (§3.5).
>
> **Le document n'est plus bloqué sur des décisions, mais sur des faits** : les deux CV
> se contredisent sur des dates et un intitulé de poste, et le handle GitHub manque.
> Voir §7 — ces trous se comblent par vérification, pas par arbitrage.
>
> **Révision 4 du 2026-07-16** — deux précisions utilisateur, dont une **structurante** :
> 1. **Les expériences se déroulent en parallèle.** Ce n'est pas une exception à gérer
>    mais une **caractéristique du parcours** : elle annule la lecture « contradiction de
>    dates » de la rév. 3 et impose une exigence nouvelle et forte sur la timeline
>    (**CV-7**, §3.2). Un rendu séquentiel serait un **contresens**, pas un choix
>    esthétique.
> 2. **Les URL GitHub des projets seront fournies.** CONT-5 cesse d'être bloquant ;
>    l'architecture peut compter sur des liens repo (§3.5).
> 3. L'écart URL / identité d'**ID-4 est confirmé par l'utilisateur** — « c'est normal ».
>    Le point est **clos**.
>
> **Révision 5 du 2026-07-16** — **le one-liner est validé** (POS-3, §1.0) :
> *« Directeur technique — vingt ans de systèmes d'information pour l'agriculture, en
> logiciel libre. »* C'était le dernier point bloquant.
>
> ### ✅ La découverte est close. `/sc:design` peut démarrer.
>
> **Révision 6 du 2026-07-16** — **neuf sources en ligne** dépouillées (LinkedIn bloqué).
> La rév. 6 ne modifie **aucune décision** ; elle **corrige des faits**, dont deux
> fondateurs :
> 1. ⚠️ **`ionosphere` est le compte GitHub personnel de David Joulin** — profil
>    « ionosphere (David JOULIN) », bio *« Focusing on open source agtech »*. **Pas une
>    organisation** : la prémisse de la découverte initiale était fausse, et l'« écart
>    URL / identité » de la rév. 3 **n'existait pas**. ID-4 réécrit, **ID-5 amendé**
>    (il était inapplicable : tout lien GitHub affiche le mot).
> 2. ⚠️ **Il existe un livre** — *L'IA des Champs*, Éditions France Agricole, dont David
>    Joulin est l'un des trois experts. **Absent des deux CV.** ACT-2, que la rév. 3
>    proposait de supprimer faute de matière, **est sauvée**.
> 3. **Ekylibre : 486 ★, AGPL-3.0, actif au 6 juillet 2026** — statut tranché, rôle
>    tranché (**CEO**, d'après sa propre bio GitHub).
> 4. **La Vauzelle** (`sci-chenes-verts.github.io`) : le tiers-lieu né de la ferme
>    familiale, que le CV rangeait en « centres d'intérêt ». Voir ACT-7.
>
> **Leçon de méthode** : les CV **omettaient** plus qu'ils ne se trompaient. Deux
> conclusions de la rév. 3 — « supprimer ACT-2 », « écart URL assumé » — étaient des
> **artefacts d'une source incomplète**, pas des arbitrages.
>
> **Révision 7 du 2026-07-16** — l'utilisateur tranche les rôles et les derniers faits.
> **§7.2 passe de 11 points ouverts à 5.**
> - **Rôles** : GAIA **créateur** · Lexicon **créateur** · Piloterra **CTO** · Ekylibre
>   **co-fondateur & CEO**. ⚠️ *Les sources publiques ne portent pas ces rôles* — écart à
>   traiter (§7.2 point 10).
> - **Ergolis : 2012–2014** — le DoYouBuzz avait raison. **Le chevauchement avec Bordeaux
>   Sciences Agro est réel** : **CV-7 est confirmé par les faits**, et le CV DSI avait
>   bien effacé la simultanéité.
> - **Trésorier de Seconde Nature : confirmé**, et attesté par `seconde-nature.net/faq`.
>   La découverte initiale avait raison ; les deux CV omettaient.
> - **Deux livres, pas un** — ACT-2 est la section la plus riche du dossier, alors que la
>   rév. 3 proposait de la supprimer.
> - ⚠️ **« La Vauzelle » n'est pas de David Joulin** : c'est un **témoignage de Francis
>   Joulin** (209 p.), qu'il a **édité**. Crédit d'auteur exigé — **ACT-8**, avec une
>   conséquence de **structure** sur `_data` (ACT-8b).

---

## 1. Objectif

Un site personnel qui sert **deux publics à parts égales** :

| Public | Ce qu'il cherche | Ce qu'il doit trouver en < 10 s |
| --- | --- | --- |
| Recruteur / client | « Ce type est-il crédible et disponible ? » | Titre, pitch, parcours, CV emportable (§3.2) |
| Pair technique / communauté OSS | « Sur quoi il travaille, et est-ce sérieux ? » | Le book de projets, la stack, les liens repo |

**Positionnement retenu** : équilibré CV + projets. La home donne un accès de rang égal
aux deux univers, sans hiérarchie forte entre eux.

### 1.0 Récit retenu — « CTO open source, agriculture & données »

**Décision (2026-07-16, rév. 3)**. Les deux CV fournis défendaient deux personnes
différentes : un **« Expert AgTech »** (CV DoYouBuzz) et un **« Directeur des Systèmes
d'Information »** (CV récent, orienté gouvernance / sécurité / RGPD). Le site tient
**les deux à la fois** : vingt ans de direction technique **dont la matière est
l'agriculture et les communs numériques**.

- **POS-1** — Le récit est un **seul** fil, pas deux rubriques juxtaposées : la
  compétence de direction SI et le corpus open source agricole s'expliquent l'un
  l'autre. GAIA, Piloterra, Lexicon et Ekylibre sont **tous** agri **et** libres — le
  book *est* la preuve du CV, pas une annexe.
- **POS-2** — C'est le **seul** récit compatible avec §1 : « Expert AgTech » seul
  n'adresse pas le recruteur DSI ; « Directeur SI » seul relègue le pair technique et
  viderait le book de son sens, ce qui contredirait §3.3.
- **POS-3** — **Le one-liner — validé (2026-07-16, rév. 5)** :

  > ### Directeur technique — vingt ans de systèmes d'information pour l'agriculture, en logiciel libre.

  Aucun des deux CV n'en fournissait un réutilisable : « Expert AgTech » est trop étroit,
  « Directeur des Systèmes d'Information » est un intitulé, pas une proposition. Cette
  formule porte les **quatre** éléments de la synthèse, et c'est ce qui la fait tenir :

  | Segment | Ce qu'il fait | Pour qui |
  | --- | --- | --- |
  | « Directeur technique » | le rôle, en clair | recruteur / client (§1) |
  | « vingt ans » | l'ancrage de crédibilité | recruteur — NFR-1 |
  | « systèmes d'information » | le métier | recruteur / DSI |
  | « pour l'agriculture » | **le fil qui unifie** | les deux — POS-1 |
  | « en logiciel libre » | l'engagement | pair technique / OSS (§1) |

  - **POS-3a** — `<title>` retenu : **« David Joulin — Directeur technique, systèmes
    d'information agricoles libres »** (forme courte, cf. ID-1). Le one-liner complet
    reste à la home (HOME-1) ; le `<title>` en est la contraction, pas une variante
    libre.
  - **POS-3b** — « logiciel libre » est délibéré, contre « open source » : le site est en
    français (LANG-1) et la prose n'a pas à angliciser ce qui a un mot courant. **Les
    jetons techniques, eux, restent tels quels** (LANG-4) — une licence reste `AGPL-3.0`.
  - **POS-3c** — La formule **ne mentionne pas l'IA**, alors que trois des quatre projets
    du book et le poste en cours en relèvent. C'est un choix : une accroche à l'IA
    vieillit vite (tension directe avec ACT-4) et rétrécirait vingt ans de parcours à sa
    phase récente. **L'IA se démontre dans le book, elle ne s'annonce pas dans le
    titre.**
- **POS-4** — Le **profil du CV récent** est la meilleure base de pitch existante
  (« 20 ans […] co-fondateur d'un éditeur de logiciels de gestion […] attaché à une
  culture associative et de service ») mais devra être réécrit pour ne pas viser
  uniquement le poste de DSI.

### 1.1 Identité — « David Joulin », site personnel

**Décision (2026-07-16, rév. 2)** : le site est le **portfolio personnel de David Joulin**.
`ionosphere` n'est qu'un **hébergement GitHub** : le nom n'apparaît nulle part côté
visiteur, ni dans le `<title>`, ni dans un logo, ni dans le pied de page.

- **ID-1** — Le `<title>` et le `title` de `_config.yml` portent « David Joulin »,
  suivi du one-liner une fois celui-ci rédigé (POS-3, §7.1).
- **ID-2** — Le ton de la prose est à la **première personne**. Cohérent avec §1 : les
  deux publics cherchent une personne, pas une structure.
- **ID-3** — Aucune identité de marque à construire : pas de logo d'entité. L'identité
  visuelle repose sur la typo et la mise en page (cf. NFR-2, non-templaté).
- **ID-4** — **Réécrit (rév. 6) — la prémisse d'origine était fausse, deux fois.**
  La découverte initiale posait : *« `ionosphere` est une **organisation** GitHub, pas un
  compte personnel »*. **Les deux moitiés sont fausses.** Vérification faite sur les
  sources primaires :

  1. **`ionosphere` est un compte UTILISATEUR**, pas une organisation — il figure comme
     **membre** de l'org `ekylibre`, ce que seul un utilisateur peut être.
  2. **C'est le handle GitHub personnel de David Joulin.** Le profil s'affiche
     littéralement **« ionosphere (David JOULIN) »**, bio *« Focusing on open source
     agtech »*, localisation Bordeaux, 29 abonnés, 8 dépôts.
  3. **C'était déjà son nom d'activité freelance** (Ionosphere Consulting, 2008–2014).

  **Conséquence** : `ionosphere.github.io` n'est **pas** un site d'organisation qui
  porterait un nom d'emprunt — c'est le **site utilisateur personnel** de David Joulin,
  à son URL canonique GitHub. L'« écart URL / identité » que la rév. 3 dramatisait
  **n'existe pas** : `ionosphere` **est** David Joulin sur GitHub, et l'est depuis 2008.
  L'utilisateur avait raison de répondre « c'est normal » (rév. 4).

  **La décision de §1.1 tient sans changement** — titrage « David Joulin », pas
  d'identité de marque à construire — mais **pour une autre raison** : ce n'est plus un
  écart assumé à contrecœur, c'est simplement qu'un **handle** et un **nom affiché**
  sont deux choses différentes, ce qui n'étonne aucun visiteur. Rien à rattraper.
- **ID-6** — **Portrait — page `/cv` uniquement** (décidé le 2026-07-16, rév. 8). La
  découverte n'avait jamais évoqué de photo.
  - **Pas dans le hero** : celui-ci porte la **thèse** — one-liner + assolement, soit
    « vingt ans, plusieurs choses à la fois ». Un visage y prendrait la place de
    l'argument.
  - **Sur `/cv`**, c'est la convention française et l'endroit où le recruteur l'attend.
    Il s'imprime (CV-4).
  - **Contenu à 7 rem** : le fichier fait 320 px ; au-delà il piquerait, et NFR-1 dit que
    ce site est lui-même une pièce du portfolio.
  - Un portrait **n'est pas un logo** : ID-3 n'est pas en cause.
- **ID-5** — **Amendé (rév. 6) — il se contredisait.** La rév. 3 écrivait : *« le seul
  endroit où ionosphere a le droit d'apparaître est l'URL et `_config.yml` »*. Or le
  handle étant `ionosphere`, **tout lien vers GitHub affiche le mot** :
  `github.com/ionosphere` (CONT-1), et chaque lien repo de PROJ-5 mène à un compte qui
  le porte. La règle était donc **inapplicable**.

  **Règle corrigée** : « ionosphere » apparaît **partout où c'est une donnée technique
  vraie** — URL du site, `_config.yml`, lien de profil GitHub, liens de dépôts. Ce qui
  reste proscrit, c'est de le traiter comme une **marque** : pas de logo, pas de
  filigrane, pas d'`og:site_name`, pas de favicon siglée, pas de « Ionosphere » en
  en-tête ou en pied de page. **Le handle est une adresse, pas une identité de marque.**

### 1.2 Registre visuel

**Registre visuel demandé** : « très pro et technologique, orienté open source ».
La direction précise est à proposer et à faire valider avant écriture du SCSS
(skill `frontend-design`), avec une exigence explicite : **ne pas ressembler à un
template**.

---

## 2. Périmètre

### Dans le périmètre

- Home équilibrée (pitch → parcours + projets → activité → contact).
- Page **CV** (parcours, compétences), **emportable en PDF via le rendu print** (§3.2).
- **Book de projets** : grille pilotée par YAML + pages d'étude de cas détaillées.
  **Quatre projets au lancement** : GAIA, Piloterra, Lexicon, Ekylibre (§3.3).
- Section **Activité** : contributions open source, talks/confs/publications,
  engagements associatifs. ⚠️ Deux de ces trois volets sont **conditionnels** —
  les contributions dépendent du handle GitHub (CONT-5) et les talks n'ont pour
  l'instant **aucune matière** (ACT-2).
- **Site en français uniquement.**
- Déploiement GitHub Pages sur **`https://ionosphere.github.io`** (décidé rév. 3).

### Hors périmètre (décidé)

- **Pas de blog** (`_posts`, RSS). Écarté sciemment : un blog non alimenté fait
  vieillir un site plus vite qu'une absence de blog.
- **Pas de version anglaise, pas de sélecteur de langue, pas de couche i18n.**
  Arbitrage du 2026-07-16. Le « pour l'instant » est noté : §3.6 précise ce qu'on
  s'interdit pour ne pas rendre une version EN coûteuse plus tard — sans pour autant
  la préconstruire.
- Pas de formulaire de contact (pas de FormSubmit). Liens directs uniquement.
- Pas de remplissage automatique depuis l'API GitHub (voir §5, contrainte de build).
- **Aucun analytics** — décidé le 2026-07-16 (rév. 2), plus « à confirmer ». Aucun script
  de mesure, donc aucun cookie, aucun bandeau de consentement, aucune obligation RGPD, et
  aucun tiers dans le chargement de la page. Cohérent avec NFR-4 (pas de JS) et avec le
  positionnement open source de §1. **Conséquence assumée** : on ne saura pas si le book
  de projets est consulté. Décision réversible à tout moment et sans coût de structure.
- Pas de fichier PDF versionné dans le repo (cf. CV-3 : le PDF est un rendu print).

---

## 3. Exigences fonctionnelles

### 3.1 Home

- **HOME-1** — Identité immédiate : nom, titre/one-liner, pitch court.
- **HOME-2** — Accès de rang égal au parcours et aux projets (aucun des deux
  n'est relégué en pied de page).
- **HOME-3** — Aperçu des projets `featured` (sous-ensemble du book, piloté par un
  drapeau dans les données — pas une liste dupliquée à la main).
- **HOME-4** — Aperçu du parcours condensé, renvoyant vers `/cv`.
- **HOME-5** — Section activité + points de contact.

### 3.2 CV

- **CV-1** — Parcours (timeline) et compétences, pilotés par données (pas de HTML
  en dur, cf. convention `_data/` du repo de référence). **Matière disponible (rév. 3)** :
  six postes, quatre diplômes, cinq formations complémentaires et six domaines
  d'expertise, dépouillés dans `docs/CONTENU.md`. **Ne pas recopier un CV tel quel** :
  les deux sources divergent (§7) et l'arbitrage POS-1 impose de raconter la direction
  technique *et* l'open source agricole d'un seul fil.
- **CV-7** — ⚠️ **La timeline doit rendre des expériences parallèles.** Exigence
  ajoutée en rév. 4 sur précision utilisateur : *« certaines de mes expériences se font
  en parallèle »*. Ce n'est **pas** un cas limite — c'est la forme normale de ce parcours :

  | Période | Ce qui tourne en même temps |
  | --- | --- |
  | 2008–2013 | Bordeaux Sciences Agro **+** Ionosphere Consulting (freelance) **+** GAEC Joulin |
  | 2012/13–2014 | Ergolis **+** Ionosphere Consulting **+** GAEC Joulin |
  | 2014–2020 | Ekylibre **+** GAEC Joulin **+** La Ferme Digitale |
  | **2026 →** | **Ekylibre + bziiit** (⚠️ à confirmer, §7.2) |

  Conséquences, **non négociables** :
  - Le gabarit **ne peut pas** supposer une succession de périodes disjointes. Toute
    forme qui **se lit** comme une séquence (une colonne, un point par poste, une ligne
    continue) **ment sur le parcours** — même si les données sont exactes.
  - **Plusieurs postes peuvent être « en cours » simultanément.** Le rendu doit pouvoir
    en afficher deux sans que l'un paraisse erroné.
  - Un chevauchement **n'est pas un défaut à masquer** : c'est de l'information. Il
    étaye directement POS-1 — diriger la technique *et* entretenir un corpus libre
    n'est pas une succession de phases, c'est une simultanéité tenue vingt ans.
  - **Le CV DSI a précisément gommé cette simultanéité** (voir CV-6) : il coupe le
    freelance et le GAEC, et aligne Ergolis derrière Bordeaux Sciences Agro. C'est
    l'usage d'un CV de recrutement. **Le site n'a pas cette contrainte** — et §1 lui
    demande justement de servir aussi le pair technique.
  - **CV-4 s'applique aussi** : la feuille print doit tenir le parallélisme. C'est le
    cas où une mise en page à colonnes résiste le moins bien à la pagination.
- **CV-6** — **Le parcours à publier n'est pas l'union des deux CV.** Le CV DoYouBuzz
  porte trois entrées que le CV récent a **délibérément coupées** — Ionosphere Consulting
  (freelance 2008–2014), GAEC Joulin (agriculteur à temps partiel, bénévolat 2002–2020),
  Charentes Alliance (stage QSE 2004–2005). Les réintégrer par défaut serait un choix
  éditorial déguisé en exhaustivité. Chaque entrée est à décider explicitement (§7) —
  celle d'Ionosphere Consulting ayant en outre un lien direct avec ID-4.
- **CV-2** — Le CV doit être **récupérable en PDF**.
- **CV-3** — **Résolu (2026-07-16, rév. 2)** : le PDF est le **rendu print de la page**,
  via une feuille de style `@media print`. Il n'existe **aucun fichier PDF dans le repo**.
  La source de vérité unique reste les `_data` — la dérive HTML/PDF est rendue
  structurellement impossible, conformément à NFR-6.
- **CV-4** — La feuille print est une **exigence de premier plan, pas une finition** :
  c'est l'artefact que le recruteur emporte. Elle doit masquer navigation, liens de
  contact décoratifs et pied de page ; garantir une pagination propre (pas de coupure au
  milieu d'une expérience) ; et **faire apparaître les URL des liens** en toutes lettres,
  puisqu'un lien n'est pas cliquable sur papier.
- **CV-5** — L'appel à l'action sur `/cv` doit **dire au visiteur quoi faire** (« Imprimer
  / enregistrer en PDF ») plutôt que de mimer un lien de téléchargement qui n'existe pas.
  Le libellé exact relève du design.

### 3.3 Book de projets — **exigence centrale**

**Amorcé (rév. 3)** : le book n'est plus vide. **Quatre projets** au lancement, retenus
par l'utilisateur dans la rubrique « Projets & distinctions » du CV récent. La matière
détaillée est en `docs/CONTENU.md` ; les métadonnées PROJ-5 restent à compléter par
projet (§7).

**Métadonnées PROJ-5 — vérifiées sur sources primaires (rév. 6)** :

| | **Ekylibre** | **Lexicon** | **GAIA** | **Piloterra** |
| --- | --- | --- | --- | --- |
| **Tagline** | ERP agricole open source — gestion, traçabilité, comptabilité | Open data agricole normalisé | Démocratiser l'IA dans le monde agricole | Portail IA agricole open source |
| **Période** | 2015–2026 | 2024–2026 | 2024–2026 | 2024–2026 |
| **Repo** | `github.com/ekylibre/ekylibre` | `github.com/osfarm/lexicon` + `lexicon-rest-api` | `github.com/osfarm/GAIA-AGRI-IA-QUALIFICATION` | ⚠️ non trouvé |
| **Licence** | **AGPL-3.0** | **MIT** | **MIT** | ⚠️ « agents open source » revendiqué |
| **Stack** | Ruby, PostgreSQL, **PostGIS** | Ruby ; TypeScript (API) | — | Mistral AI, Supabase, n8n |
| **Site** | ekylibre.com · ekylibre.org | lexicon.osfarm.org | gaia-ia.org | piloterra.fr |
| **Statut** | **actif** — MAJ 6 juil. 2026 | **actif** — MAJ 26 juin 2026 | **maintenu** — MAJ 30 juil. 2025 | **actif** |
| **Traction** | **486 ★ · 170 forks** | v1.3.3 | 8 hackathons · 17 coachs | — |
| **Porté par** | Ekylibre SAS | OSFarm | La Ferme Digitale **+** OSFarm | bziiit |
| **Rôle de DJ** ✅ | **Co-fondateur & CEO** | **Créateur** | **Créateur** | **CTO** |

- **PROJ-11** — **Ekylibre est la pièce maîtresse, et de loin.** **486 étoiles, 170
  forks, dernière mise à jour le 6 juillet 2026**, en **AGPL-3.0** : c'est la seule
  preuve de traction open source réelle du dossier, et elle est vérifiable en un clic.
  Le design doit lui donner le poids qu'elle a — c'est ce qui distingue ce site d'un
  portfolio d'intentions.
- **PROJ-12** — **Les quatre projets forment une chaîne, pas une liste.** À faire
  apparaître, c'est la démonstration de POS-1 :
  - **Lexicon alimente Ekylibre** — Ekylibre normalise ses données via les nomenclatures
    Onoma et Lexicon, *« plus de 20 millions de références »*.
  - **GAIA a engendré Piloterra** — Piloterra est né du **premier hackathon IA & agri**
    organisé par Comexposium, La Ferme Digitale et GAIA au **SIA 2024**.
  - **GAIA est né de La Ferme Digitale + OSFarm** — les deux associations de §3.4.
  - Autrement dit : les projets, les associations et l'emploi **sont le même
    écosystème**. Le book n'illustre pas le CV, il **est** le CV.
- **PROJ-13** — ⚠️ **Chiffres à corriger avant publication** — les CV divergent des
  sources officielles :

  | | CV | Source officielle |
  | --- | --- | --- |
  | GAIA | « **80 projets**, 8 sessions » | « **8 hackathons, 30 sujets**, 17 coachs » (gaia-ia.org) |
  | Lexicon | « **80 sources** » | « **7 catégories** de jeux de données » (lexicon.osfarm.org) |
  | Ekylibre | « **2015–2025** » | dépôt **actif en juillet 2026**, © **2014–2026** |

  **Publier le chiffre du CV quand le site officiel en affiche un autre est
  exactement le risque NFR-1** : un pair vérifie en un clic.

- **PROJ-0** — Ces quatre projets **valident POS-1** : tous agri **et** libres, ils
  démontrent le récit au lieu de l'illustrer. C'est ce qui autorise l'accès de rang égal
  CV / projets exigé en HOME-2.
- **PROJ-8** — **GAIA porte une distinction datée et vérifiable** (IA Summit 2025).
  C'est le seul élément du dossier de cette nature : il mérite mieux qu'une ligne de
  carte. Candidat prioritaire à l'étude de cas détaillée (PROJ-2).
- **PROJ-9** — **Tension avec ACT-4** : les quatre projets portent des périodes, dont
  trois se terminent en 2026 et une en 2025. ACT-4 interdit d'**afficher de la
  fraîcheur** — mais une **période de projet** n'est pas une date de mise à jour : elle
  décrit le projet, elle ne date pas le site. La distinction est à tenir en design ;
  ce qui est proscrit reste « dernière mise à jour le … », pas « 2024–2026 ».
- **PROJ-10** — Quatre projets, c'est **le cas nominal de PROJ-6**, pas le cas
  dégradé : la grille doit être conçue pour bien rendre à **quatre**, sans supposer
  qu'elle se remplira.

La qualité du site se juge autant sur **la facilité d'ajout** des suivants que sur le
rendu des quatre premiers.

- **PROJ-1** — Grille de projets pilotée par `_data/projects.yml` (une entrée = une carte).
- **PROJ-2** — Un projet peut avoir **en plus** une page d'étude de cas détaillée
  (Markdown long : contexte, problème, rôle, résultats, images, extraits de code).
  Tous les projets n'en ont pas.
- **PROJ-3** — Ajouter un projet **sans page détail** doit coûter *une entrée YAML et
  rien d'autre* : pas de retouche de gabarit, pas de lien à câbler à la main.
- **PROJ-4** — Ajouter une **page détail** doit coûter *un fichier Markdown* ; le lien
  depuis la carte doit apparaître automatiquement.
- **PROJ-5** — Métadonnées à porter par carte : nom, tagline, rôle, stack, lien repo,
  lien site, licence, statut (actif / maintenu / archivé), période, visuel, `featured`.
  ✅ **Renseignées et en ligne** — voir `DESIGN.md` §3.4.
  - **`visuel` (2026-07-16)** : une **capture du site réel** du projet, 16∶9, WebP,
    ~12 ko, auto-hébergée (§6). C'est du **contenu encadré**, pas une marque — d'où sa
    légitimité là où un logo aurait fait décoration. Le site était jusque-là
    **intégralement textuel**.
  - **Pas de logo sur les cartes** : la capture porte **déjà** le logo, en grand.
- **PROJ-14 — Le système de marques** (`_includes/marque.html`, 2026-07-16). Les logos
  fournis forment un **arc-en-ciel** sans rapport avec la palette RPG (vert, cyan,
  bordeaux, jaune, scène dessinée), et **trois postes sur huit** seulement en ont un.
  Alignés tels quels → **bandeau LinkedIn, c'est-à-dire NFR-2**.
  → **Logo réel s'il existe, monogramme typographique sinon.** Ce n'est pas un pis-aller :
  **ID-3 fait reposer l'identité sur la typo**. La moitié des marques du site étant des
  lettres, l'effet « mur de logos » ne prend jamais.
- **PROJ-6** — La grille doit rester **digne** avec 1 à 3 projets comme avec 20.
  Un book vide ou quasi vide ne doit pas donner l'impression d'un site inachevé.
- **PROJ-7** — Filtrage / regroupement par stack ou statut : *souhaitable, non requis*.
  À arbitrer selon le volume réel de projets.
  → ❌ **Arbitré (design, 2026-07-16) : non implémenté.** Quatre projets ne justifient pas
  un filtre — à ce volume, c'est un ornement qui **signale que le book est trop court pour
  lui**. À rouvrir si le book dépasse ~10 entrées. Voir `DESIGN.md` §4.3.

### 3.4 Activité

- **ACT-1** — Contributions open source : repos, rôle, contributions notables.
  **Dépend de CONT-5** : sans handle GitHub, cette section n'a aucune matière.
- **ACT-2** — Talks, confs, publications (liste courte pilotée par YAML).
  **La section est sauvée (rév. 6)** : la rév. 3 concluait « aucune matière → supprimer ».
  **Faux — les CV étaient muets, pas la réalité.** Matière trouvée :
  - 📕 **« L'IA des Champs — une autre culture de l'IA »**, **Éditions France Agricole**.
    David Joulin en est **co-auteur** ✅ (rév. 7), avec Hervé Pillaud et Karine
    Cailleaux-Breton. Plateforme associée : **251 termes** illustrés en vidéo, assistant
    Mistral AI. Présentation au **SIA le 21 février 2026**, stand La Ferme Digitale.
    → `ia-des-champs.lovable.app`
  - 📗 **« La Vauzelle — Deux siècles de son histoire »** — témoignage de **Francis
    Joulin** ; David Joulin **éditeur** (mise en page, numérisation, travail documentaire,
    mise en ligne). 209 p. → `sci-chenes-verts.github.io`. **Voir ACT-8 : le crédit
    d'auteur est une exigence, pas une politesse.**
  - 🎤 **Intervention publique sur le hackathon GAIA du SIA 2024** — David Joulin est
    **cité comme intervenant** sur `gaia-ia.org`.
  - 📰 **Couverture presse de GAIA** : Plein Champ, BPI France, La France Agricole,
    Terre Net, Réussir, Ouest-France, **BFM TV**.
  - **Un livre chez un éditeur national est l'actif le plus fort après les 486 étoiles
    d'Ekylibre.** Qu'il soit absent des deux CV est l'angle mort le plus coûteux du
    dossier.
- **ACT-6** — ✅ **Tranché (rév. 7)** : **« L'IA des Champs » est une publication**
  (ACT-2), **pas** un cinquième projet. David Joulin y est **co-auteur**. Le book reste
  à **quatre** projets (§3.3).
- **ACT-8** — ⚠️ **« La Vauzelle — Deux siècles de son histoire » : publication d'un
  AUTRE auteur.** Décision rév. 7 : le livre figure en publications, **crédité à son
  auteur**.
  - **Auteur : Francis JOULIN** — page de titre : *« Un témoignage de Francis Joulin » ;*
    préface signée, *« né le 03 mars 1933 à La Vauzelle »*, agriculteur éleveur retraité.
    **209 pages**, 64 chapitres, de 1822 à nos jours. `sci-chenes-verts.github.io`.
  - **Rôle de David Joulin : éditeur** — mise en page et numérisation, travail
    documentaire, mise en ligne. **Pas auteur.** Il n'apparaît dans l'ouvrage qu'à une
    ligne, comme enfant qui naît (*« le 02 mars 1981 naît un fils prénommé David »*).
  - **ACT-8a — Règle de rendu, non négociable** : l'entrée doit nommer **Francis Joulin
    comme auteur** et David Joulin **comme éditeur**. Une liste « Publications » qui
    ferait figurer ce titre à côté de *L'IA des Champs* (où il est co-auteur) **sans
    distinguer les deux rôles** s'attribuerait le témoignage d'un tiers **par simple
    placement**. L'auteur est une personne réelle et identifiable.
  - **ACT-8b** — Conséquence pour `_data` : le schéma des publications doit porter un
    champ **`auteur`** et un champ **`rôle`** distincts, sinon le gabarit **ne peut pas**
    exprimer la différence. C'est une contrainte de **structure**, à intégrer en design,
    pas une nuance de rédaction.
- **ACT-3** — **Corrigé et enrichi (rév. 3)**. Quatre engagements, tirés du CV récent :
  - **La Ferme Digitale** (depuis 2015) — **VP Data & IA** depuis 2022 ; auparavant
    responsable adhésion (2020–2022) et **trésorier** (2015–2020).
  - **OSFarm** (⚠️ CV : depuis 2024 ; site : **© 2023–2026**) — création de l'association
    et d'un **fablab de 350 m²**, hackathons autour des **communs numériques agricoles**.
    **Porte une organisation GitHub active** (`github.com/osfarm`, 9 dépôts, MIT) qui
    héberge **Lexicon** et **GAIA** — deux des quatre projets du book. OSFarm n'est donc
    pas seulement associatif : c'est **l'infrastructure** de la moitié du book.
  - **Seconde Nature** (depuis 2025) — recyclerie de **2 200 m²** (⚠️ surface non
    confirmée par le site) en tiers-lieu, **8 rue du Bouil Bleu, 17250 Saint-Porchaire**.
    ⚠️ **Fermée pour travaux jusqu'au 30 septembre 2026** — fait à connaître avant de la
    présenter, et **tension avec ACT-4** : une réouverture datée est précisément le genre
    d'information qui périme.
  - **NAOS — Nouvelle-Aquitaine Open Source** (2021–2024) — pôle de compétences régional
    en logiciels libres.

  ✅ **Seconde Nature — trésorier : CONFIRMÉ (rév. 7)**, par l'utilisateur **et** par une
  source publique. `seconde-nature.net/faq` publie le bureau : *« **David — Trésorier**
  (Finance, Achats, **Informatique, IA**, Matériel, Jardin) »*, aux côtés de Julien
  (président), Alexandra, Thomas et Amandine. La découverte initiale avait donc **raison**,
  et les deux CV avaient **tort par omission** — une fois de plus (§7.3).
  À noter : le portefeuille recoupe **informatique et IA**, ce qui rattache l'engagement
  à POS-1 plutôt qu'au bénévolat de bon voisinage.
  *(Le site ne donne que les prénoms — l'identification repose sur la confirmation
  utilisateur, ce qui suffit.)*
- **ACT-5** — Ces engagements **ne sont pas décoratifs** : OSFarm (communs numériques)
  et NAOS (logiciel libre) sont de la **matière open source**, cohérente avec POS-1.
  Ils appartiennent au récit, pas à une rubrique « divers » en bas de page.
- **ACT-7** — ⚠️ **La Vauzelle / SCI des Chênes Verts — la pièce manquante, absente des
  deux CV.** Le lien `sci-chenes-verts.github.io` révèle un **tiers-lieu né d'une ferme
  familiale de 1917**, en Charente-Maritime, où **six structures indépendantes** partagent
  bâtiments et réseaux : agriculture bio, innovation agricole, économie sociale et
  solidaire, recyclerie.

  **Ce que ça recoupe** — et le recoupement est le fait le plus fort de tout le
  dépouillement :
  - Le CV range **« Ferme de la Vauzelle »** dans les *centres d'intérêt*, à côté du
    potager et du bricolage.
  - **Seconde Nature** (recyclerie, ACT-3) est décrite « au sein d'un tiers-lieu » et
    siège **à Saint-Porchaire**.
  - Le **GAEC Joulin** (agriculteur 2002–2020, entrée coupée par CV-6) est à
    **Saint-Porchaire**.
  - **Ekylibre** est domicilié « Bègles / **Saint-Porchaire** ».
  - David Joulin habite « **Saint-Porchaire** (17) / Bordeaux ».
  - Sa bio GitHub commence par **« Farmer son »**.

  **Conclusion** : la ferme familiale n'est pas un loisir, c'est **le lieu physique où
  son écosystème est installé** — et elle a, elle aussi, son site GitHub Pages. Le
  « fils d'agriculteur » de POS-1 n'est pas une figure de style : c'est une **adresse**.
  Classer ça en « centres d'intérêt » est un contresens que le CV commet et que le site
  ne doit pas répéter. **Statut à décider** (§7) : le tiers-lieu appartient-il au récit ?
- **ACT-4** — Aucune de ces sections ne doit **afficher de fraîcheur** (« dernière mise
  à jour le … », dates de flux) : sans blog, le site ne doit pas exhiber son propre
  vieillissement.

### 3.5 Contact

- **CONT-1** — **Révisé (rév. 3)**. Points de contact retenus : **email
  `djoulin@gmail.com`** et **LinkedIn** (`linkedin.com/in/david-joulin`).
  L'adresse `gmail` est préférée à `djoulin@ekylibre.com` : elle est personnelle et
  pérenne, alors qu'Ekylibre est justement une structure au statut à clarifier (§7).
- **CONT-2** — *Toujours ouvert* : email en clair (scraping) ou obfusqué ? Arbitrage
  simplicité / spam. À trancher en design.
- **CONT-3** — **Pas de numéro de téléphone.** Les deux CV portent un portable ; il
  **ne va pas sur le site**. Une page publique indexable est aspirée en quelques jours
  et le retrait est illusoire. Un CV transmis en direct n'engage pas la même exposition
  qu'une URL permanente — la feuille print (CV-4) **ne doit pas** le réintroduire.
- **CONT-4** — **Pas d'adresse postale ni de localisation précise.** Le CV récent porte
  « Saint-Porchaire (17) / Bordeaux » : une mention de zone géographique est utile au
  recruteur, mais relève du même arbitrage que CONT-3 et n'a pas été tranchée. *Ouvert.*
- **CONT-5** — **Résolu (rév. 4)**. L'utilisateur fournira les **URL GitHub de tous ses
  projets**. La contradiction relevée en rév. 3 — un site open source sans lien vers le
  moindre dépôt — **n'a plus lieu d'être** : POS-1, PROJ-5 et ACT-1 tiennent, et
  l'architecture peut compter sur des liens repo.
  - *En attente de la fourniture effective des URL.* Non bloquant pour le design : la
    **structure** est confirmée, seules les **valeurs** manquent.
- **CONT-6** — **Résolu (rév. 6)** : le profil GitHub personnel est
  **`github.com/ionosphere`** — le même nom que le site. **À afficher en contact.**
  - Bio : *« Focusing on open source agtech »* · Bordeaux · 29 abonnés · 8 dépôts.
  - Auto-description : *« Farmer son, AgroTIC Data engineer, Ekylibre CEO / bziiit
    CTO »* — **elle valide POS-1 mot pour mot** : le fils d'agriculteur, l'ingénieur
    data agri et le dirigeant, dans une seule ligne, écrite par l'intéressé avant qu'on
    ne rédige POS-3.
  - **Le profil tient debout seul** — la crainte formulée en rév. 4 (un profil vide parce
    que le travail vit sous des orgs) est levée : les dépôts épinglés portent
    `ekylibre/ekylibre` (**486 ★**), `osfarm/osfarm.github.io`, `osfarm/lexicon` et
    `ekylibre/zero-mobile`.
  - ⚠️ **Conséquence sur ID-5** : ce lien fait apparaître « ionosphere » dans le contenu.
    ID-5 a été amendé en conséquence — le handle est **une adresse**, pas une marque.

### 3.6 Langue — français uniquement

**Décision (2026-07-16)** : le site est **intégralement en français**. Aucune couche i18n
n'est construite. Le repo de référence est lui-même 100 % français : l'écart de
complexité avec `seconde-nature.github.io` **disparaît**, et le principal poste de
travail de la spec initiale s'annule.

- **LANG-1** — Tout le contenu visible est en français. `lang="fr"` sur `<html>`.
- **LANG-2** — Aucun sélecteur de langue, aucun `hreflang`, aucun arbre `/fr` ou `/en`.
  Les URL sont à la racine, sans préfixe de langue.
- **LANG-3** — Pas de `_data/i18n/`. Les données (`projects.yml`, CV, talks…) portent
  directement leurs libellés en français, en une seule chaîne par champ — conformément
  à la convention `_data/` du repo de référence.
- **LANG-4** — Les **jetons techniques restent tels quels**, ils ne se traduisent pas :
  noms de stack (`Ruby`, `PostGIS`), licences (`AGPL-3.0`), noms de repo, handles.
  Seule la prose est en français.

#### Ce qu'on s'interdit pour ne pas se fermer la porte

Le « pour l'instant » est pris au sérieux **sans rien préconstruire** : bâtir une
mécanique bilingue pour un anglais hypothétique coûte tout de suite et ne rapporte
peut-être jamais. La couverture se limite à trois règles d'hygiène, gratuites :

- **LANG-5** — Pas de français en dur dans les gabarits (`_layouts`, `_includes`) là où
  la donnée existe déjà : les libellés viennent des `_data/` ou du front matter. C'est
  déjà l'exigence NFR-6 ; elle suffit à rendre une passe EN mécanique plus tard.
- **LANG-6** — Pas de français dans les **URL de structure** ni dans les identifiants
  techniques (slugs de collection, clés YAML, noms de classes CSS). Renommer une URL
  après indexation coûte du SEO ; une clé YAML en anglais ne coûte rien.
- **LANG-7** — `url` et le titre du site restent centralisés dans `_config.yml`
  (déjà exigé par §5 pour le domaine).

**Conséquence assumée** : la partie open source du site n'est pas lisible par un pair
non francophone, alors que l'anglais est la langue par défaut de l'écosystème. Le
compromis est acté ; il est réversible via une passe EN ultérieure, dont LANG-5/6/7
gardent le coût raisonnable.

---

## 4. Exigences non fonctionnelles

- **NFR-1 — Crédibilité technique** : le site est lui-même une pièce du portfolio.
  Un site perso de dev mal fichu décrédibilise le CV qu'il porte.
- **NFR-2 — Non-templaté** : le rendu ne doit pas être reconnaissable comme un thème
  sur étagère (exigence explicite de l'utilisateur).
- **NFR-3 — Accessibilité** : contrastes, navigation clavier, sémantique. Non
  négociable sur un site qui se réclame du sérieux technique.
- **NFR-4 — Performance** : site statique, pas de framework JS. Attention au poids des
  polices et des visuels de projets.
- **NFR-5 — Responsive** : desktop et mobile.
- **NFR-6 — Maintenabilité** : ajouter un projet ou une ligne de CV ne doit pas demander
  de relire le CSS. C'est la règle `_data/` du repo de référence, à préserver.
- **NFR-7 — SEO** : `jekyll-seo-tag` + `jekyll-sitemap`, URL canonique stable
  (cf. domaine, §5).

---

## 5. Contraintes techniques

Héritées de la stack `seconde-nature.github.io`, validées par l'utilisateur :

- **Jekyll** + **build GitHub Pages classique** (pas de GitHub Actions).
- `safe: true` → **seuls les plugins whitelistés GitHub Pages tournent**. Un plugin non
  supporté est ignoré **silencieusement** (pas d'erreur), ce qui rend le diagnostic
  pénible : vérifier qu'un plugin est whitelisté *avant* de compter dessus.
  *Note pour une éventuelle version EN* : les plugins i18n usuels (ex. `jekyll-polyglot`)
  ne sont **pas** whitelistés — une passe bilingue devrait être faite à la main ou en
  sortant du build classique. Sans objet tant que §3.6 tient.
- Les **collections Jekyll** (`_projects`) sont du Jekyll natif : disponibles sans plugin.
- ~~**Bootstrap 5 via CDN**~~ — ❌ **abandonné (design, 2026-07-16)**. Cette contrainte,
  héritée de `seconde-nature.github.io`, **contredisait §2 et §6** : un CDN **est** un
  tiers, et §6 exige « aucun script tiers ». *(L'écart datait de la rév. 2 : la clause
  « aucun analytics… aucun tiers dans le chargement » a été écrite sans voir que Bootstrap
  tombait dedans.)*
  → **Aucun framework CSS.** CSS Grid pour la mise en page — c'est elle qui porte la
  signature du design ; menu et accordéons en **`<details>`/`<summary>`** natifs, sans JS.
  Sert §6, **NFR-2** (le rendu Bootstrap *est* le rendu template) et **NFR-4**.
  Voir `DESIGN.md` §5.
- **Aucune fonte tierce** — Google Fonts est un tiers (§6). Les fontes sont **libres et
  auto-hébergées** dans le repo. Contrainte non prévue par la découverte, ajoutée au
  design.
- **Piège SCSS connu** : GitHub Pages épingle `jekyll-sass-converter 1.5.2` (libsass), qui
  échoue sur `clamp(<rem> + <vw>, …)`. Tout terme additif doit être enveloppé dans
  `calc()` — ex. `clamp(2rem, calc(1.6rem + 4vw), 5rem)`.
- `Gemfile`/`Gemfile.lock` ne servent qu'au `bundle exec` local ; le builder classique
  utilise son propre environnement épinglé.
- **Pas d'appel à l'API GitHub au build** (sandbox) : toute donnée GitHub dynamique
  impliquerait du JS client ou une Action, donc de sortir du build classique.
- **Domaine — résolu (rév. 3)** : **pas de domaine personnalisé**. Le site vit sur
  `https://ionosphere.github.io`.
  - **Pas de fichier `CNAME`.**
  - `url: https://ionosphere.github.io` et **`baseurl: ""`** dans `_config.yml` — c'est
    un site d'**organisation** (`<org>.github.io`), donc servi à la racine ; un `baseurl`
    non vide casserait tous les liens.
  - HTTPS et certificat sont fournis par GitHub Pages, sans réglage DNS.
  - **Le risque de migration SEO ne disparaît pas, il est reporté** : le jour où un
    domaine sera pris, l'URL canonique changera. Le coût reste faible tant que `url`
    est **centralisé** dans `_config.yml` (LANG-7) et qu'aucune URL absolue n'est écrite
    en dur dans les gabarits ou le contenu — à tenir dès le premier commit.

---

## 6. Critères d'acceptation

- [ ] Un visiteur identifie qui est David et ce qu'il fait sans scroller.
- [ ] Recruteur et pair technique atteignent chacun leur cible en un clic depuis la home.
- [ ] **Ajouter un projet sans page détail = une entrée YAML, zéro autre fichier touché.**
- [ ] **Ajouter une étude de cas = un fichier Markdown ; la carte s'y lie toute seule.**
- [ ] Le book reste présentable avec 2 projets, et **rend bien avec les 4 du lancement**.
- [ ] Aucun chiffre, date ou intitulé publié n'est en contradiction avec les CV sources
      (§7.2 fermée) — en particulier le statut d'Ekylibre et le rôle chez Seconde Nature.
- [ ] Le numéro de téléphone n'apparaît **nulle part**, y compris à l'impression (CONT-3).
- [ ] Tout le contenu visible est en français ; `lang="fr"` ; aucun reliquat de sélecteur
      de langue ni d'anglais résiduel dans les gabarits.
- [ ] Aucun libellé français codé en dur dans `_layouts`/`_includes` quand la donnée
      existe en `_data` (LANG-5).
- [ ] Le CV est consultable en ligne et récupérable en PDF **par impression de la page**,
      sans qu'aucun PDF ne soit versionné.
- [ ] L'aperçu d'impression de `/cv` tient la route : navigation et pied de page masqués,
      aucune expérience coupée entre deux pages, URL des liens visibles en toutes lettres.
- [ ] Le site est celui de « David Joulin » : le mot « ionosphere » n'apparaît nulle part
      côté visiteur (`<title>`, en-tête, pied de page).
- [ ] Aucun script tiers, aucun cookie, aucun bandeau de consentement.
- [ ] Le site est correct au clavier et lisible en contraste.
- [ ] `bundle exec jekyll build` passe ; `htmlproofer` ne signale aucun lien mort.
- [ ] Le rendu ne se lit pas comme un thème par défaut (validation utilisateur).
- [ ] Aucune section n'affiche de date de fraîcheur susceptible de vieillir.

---

## 7. Questions ouvertes

**Plus aucune décision ne bloque.** Ce qui reste sont des **faits à vérifier** : deux CV
qui se contredisent, et des trous qu'aucun des deux ne comble. Un site perso qui publie
une date fausse ou un intitulé périmé décrédibilise le CV qu'il porte (NFR-1) — ces
points **doivent** être fermés avant publication, mais **ne bloquent pas `/sc:design`**,
qui travaille sur la structure et non sur les valeurs.

### 7.1 Bloquant pour le design

**Néant.** ✅ Le dernier point (POS-3, le one-liner) est validé en rév. 5.

### 7.2 Bloquant pour la publication, pas pour le design

2. **Écarts de dates entre les deux CV** — ⚠️ **reformulé en rév. 4**. La rév. 3 les
   lisait comme des **contradictions** dont l'une des deux versions serait fausse. La
   précision *« certaines de mes expériences se font en parallèle »* **annule cette
   lecture** : un chevauchement n'est pas l'indice d'une erreur. Restent de simples
   **valeurs à confirmer**, sans enjeu de cohérence :

   | Sujet | CV DoYouBuzz | CV récent (DSI) | Lecture |
   | --- | --- | --- | --- |
   | ~~**Début Ergolis**~~ | ~~juin 2012~~ | ~~juillet 2013~~ | ✅ **Tranché (rév. 7) : 2012–2014.** Le **DoYouBuzz avait raison**. Ergolis **chevauche donc bien** Bordeaux Sciences Agro (jusqu'en 2013) : **le chevauchement est réel**, et c'est le CV DSI qui l'a **effacé**. **CV-7 est confirmé par les faits**, pas seulement par une déclaration. |
   | ~~Rôle chez Ekylibre~~ | ~~Co-fondateur & CEO~~ | ~~Directeur technique~~ | ✅ **Tranché (rév. 6) : CEO.** Sa **bio GitHub** dit *« **Ekylibre CEO** / bziiit CTO »*. Le CV DSI **recadrait** le mandat en « directeur technique » pour viser un poste de DSI. Le site n'a pas cette contrainte : **co-fondateur & CEO**. |
   | Début / fin Bordeaux Sciences Agro | sept. 2008 – mai 2013 | oct. 2008 – juin 2013 | Écart d'un mois — sans conséquence de rendu. |
   | Début Ekylibre | octobre 2014 | novembre 2014 | Idem. |
   | Début La Ferme Digitale | mars 2016 | 2015 | ⚠️ Un an d'écart, **non expliqué par le parallélisme**. |
   | Trésorier La Ferme Digitale | 2016–2020 | 2015–2020 | Idem. |
   | **Début OSFarm** | — | depuis **2024** | ⚠️ Le site porte **« © 2023 – 2026 »**. |

3. ✅ **Statut d'Ekylibre — tranché (rév. 6).** Trois sources primaires concordent :
   - la **bio GitHub** de David Joulin dit **« Ekylibre CEO »** — au présent, en 2026 ;
   - le dépôt `ekylibre/ekylibre` est **actif au 6 juillet 2026** (486 ★), © 2014–2026 ;
   - `ekylibre.com` annonce le **17 janvier 2026** : *« Fin de notre offre SAAS, Evolution
     en 2026 »*.

   **Lecture** : ce qui s'arrête est **l'offre commerciale SaaS**, pas le projet libre ni
   le mandat. Le « 2015–2025 » du CV décrit vraisemblablement la **fenêtre du produit
   commercial**, pas une fin. → carte projet **« actif »** ; parcours à **deux postes en
   cours** (Ekylibre CEO + bziiit CTO), ce que CV-7 rend rendable. *Formulation exacte
   du « depuis 2026 » chez Ekylibre à confirmer par l'utilisateur.*

4. ✅ ~~**ACT-3 — rôle chez Seconde Nature**~~ — **confirmé (rév. 7) : trésorier**,
   attesté par `seconde-nature.net/faq`. ⚠️ *Subsiste* : la **surface de 2 200 m²** reste
   non attestée par le site, et la recyclerie est **fermée pour travaux jusqu'au
   30/09/2026** (tension ACT-4).

5. ✅ **ACT-2 — talks / publications : la section est sauvée (rév. 6).** La rév. 3
   concluait « supprimer, faute de matière » sur la foi des seuls CV. **Il existe un
   livre** — *L'IA des Champs*, Éditions France Agricole — plus une intervention SIA 2024
   et une couverture presse jusqu'à BFM TV. **Leçon** : l'absence dans les CV n'est pas
   une absence de matière. Voir ACT-2 et ACT-6.

6. ✅ ~~**CV-6 — les trois entrées coupées**~~ — **toutes réintégrées** (rév. 8).
   C'étaient précisément les **parallèles** que le CV de recrutement avait effacés : les
   remettre ne « alourdit » pas le parcours, ça **restitue sa forme réelle** (CV-7).
   - **Ionosphere Consulting** (2008–2014) — porte le nom du handle GitHub et du site (ID-4).
   - **GAEC Joulin** (2002–2020) — la plus longue bande, et le lieu de La Vauzelle (ACT-7).
   - **Charentes Alliance** (stage) — je l'avais écartée en jugeant qu'un stage de vingt
     ans n'apportait rien ; **arbitrage utilisateur contraire**, elle est en ligne.
     ⚠️ **Elle a imposé deux choses** — voir points 13 et 14.

7. ✅ ~~**CONT-6 — profil GitHub personnel**~~ — **résolu (rév. 6)** :
   **`github.com/ionosphere`**, et il tient debout seul. Voir §3.5.

8. ✅ ~~**ACT-6 — « L'IA des Champs » : publication ou projet ?**~~ — **publication**,
   en **co-auteur** (rév. 7). Le book reste à quatre projets.

9. ✅ ~~**ACT-7 — La Vauzelle**~~ — entre **par les publications** (rév. 7), via le livre
   de **Francis Joulin** que David Joulin a **édité**. Voir **ACT-8** : le crédit
   d'auteur est une exigence de structure (**ACT-8b**), pas de rédaction.
   ⚠️ *Subsiste* : le **tiers-lieu lui-même** (les six structures, le lieu) entre-t-il au
   récit **au-delà** du livre ? La réponse rév. 7 ne portait que sur la publication. Si
   non, la ligne « centres d'intérêt : Ferme de la Vauzelle » du CV reste un contresens
   à ne pas reproduire (ACT-7).

10. ✅ ~~**Rôles sur les projets**~~ — **tranchés (rév. 7)** : **GAIA — créateur** ·
    **Lexicon — créateur** · **Piloterra — CTO** · **Ekylibre — co-fondateur & CEO**.
    ⚠️ *Subsiste, et c'est sérieux* : **les sources publiques ne portent pas ces rôles.**
    `gaia-ia.org` attribue GAIA à La Ferme Digitale + OSFarm et ne cite David Joulin que
    comme **intervenant** ; l'équipe publiée de **Piloterra** ne le mentionne pas.
    Écrire « créateur de GAIA » sur son site quand le site de GAIA ne le dit pas est
    **exactement le claim qu'un pair vérifie** (NFR-1). Deux issues : **formuler
    précisément** ce qui est vérifiable (« créateur, via La Ferme Digitale et OSFarm »),
    ou **faire corriger les sources**. Ne pas laisser l'écart en l'état.

11. **CONT-2** — email en clair ou obfusqué ?
    **CONT-4** — ⚠️ **recadré (rév. 6)** : « Saint-Porchaire » n'est plus une simple
    zone de mobilité. C'est là que sont **le GAEC, La Vauzelle, Seconde Nature et le
    siège d'Ekylibre**. La question n'est plus « faut-il donner sa localisation ? » mais
    « le site peut-il raconter cet écosystème sans le situer ? ».

12. ✅ **Ne pas publier d'âge** — appliqué, aucun âge sur le site. Le CV DoYouBuzz affiche
    « 42 ans » ; le livre de Francis Joulin date la naissance au **2 mars 1981** (cohérent
    avec le bac en 1999), soit **45 ans**. Le CV est **périmé** — illustration littérale
    de ce que proscrit ACT-4 : une donnée qui vieillit toute seule.

13. ⚠️ **Dates du stage Charentes Alliance — CONFLIT OUVERT.** L'utilisateur dit
    **2002–2004** ; le CV DoYouBuzz dit **juin 2004 – juin 2005**. Deux ans d'écart, mais
    contenu **identique** (HACCP / « certification Sécurité alimentaire » + audit ATEX) :
    c'est le même stage. **2002–2004 est en ligne** — parole de l'intéressé, et cohérent
    avec l'IUP Génie des procédés (2002–2004) qu'il chevauche exactement. **À confirmer.**

14. ✅ **Anachronisme évité — « Ocealia » n'existait pas en 2002.** La coopérative naît en
    **décembre 2015**, de la fusion de **Charentes Alliance** et de Coréa Poitou-Charentes.
    David Joulin n'a **jamais** travaillé chez Ocealia : il a fait son stage chez Charentes
    Alliance, absorbée depuis. Le site affiche donc le **nom d'époque** en titre et le nom
    actuel en mention (`devenu:`) — vérité historique **et** reconnaissance d'aujourd'hui.
    *Un lecteur du monde agricole charentais aurait vu l'erreur (NFR-1).*

15. **CV-8 — nouvelle nature `stage` (code RPG `STG`).** Un stage **n'est pas** un emploi :
    le coder `salariat` l'aurait surévalué. Cinquième catégorie de parcelle, ajoutée pour
    une seule entrée — et c'est justifié, parce qu'elle **dit quelque chose de vrai**.

### 7.3 Résolues

- ~~I18N-4 (études de cas en bilingue)~~ — sans objet, site français uniquement (§3.6).
- ~~Question 3 (identité)~~ — **David Joulin, site personnel** ; `ionosphere` invisible
  côté visiteur. Reconfirmée en rév. 3 malgré la découverte qu'Ionosphere était le nom de
  freelance de David Joulin, puis **close en rév. 4** : l'utilisateur juge l'écart URL /
  identité normal. **Ne pas rouvrir.** Voir §1.1 et ID-4.
- ~~CONT-5 (GitHub : accident ou choix ?)~~ — **accident** : les URL GitHub des projets
  seront fournies (rév. 4). POS-1, PROJ-5 et ACT-1 tiennent. Voir §3.5.
- ~~« Contradictions de dates »~~ — **mal qualifiées** : le parcours est parallèle par
  nature (CV-7), les chevauchements ne sont pas des erreurs. Ce qui subsiste est une
  liste de **valeurs à confirmer**, pas un conflit à arbitrer. Voir §7.2 point 2.
- ~~Question 4 (CV-3 : PDF à la main ou rendu print ?)~~ — **rendu print** de la page,
  source unique, aucun PDF versionné. Voir §3.2.
- ~~Question 5 (analytics ?)~~ — **aucun analytics**. Voir §2.
- ~~Question 2 (nom de domaine)~~ — **pas de domaine personnalisé** :
  `https://ionosphere.github.io`. Voir §5.
- ~~Question 1 (le contenu)~~ — **deux CV fournis et dépouillés** (`docs/ressources/`,
  reportés dans `docs/CONTENU.md`). Positionnement (§1.0), projets (§3.3), engagements
  (ACT-3) et contact (CONT-1) sont désormais renseignés. Ne subsistent que les
  vérifications ci-dessus.

---

## 8. Étape suivante

`/sc:design` — direction visuelle argumentée (typo, couleurs, grille, tokens) soumise à
validation, puis architecture Jekyll (arborescence, collection `_projects`, schéma de
`projects.yml`). Le volet i18n de cette étape **tombe**. La **feuille print du CV**
(CV-4) entre au périmètre du design : c'est un livrable, pas une finition.

✅ **§7.1 est vide : `/sc:design` peut démarrer.** Le design travaille sur la structure
et la direction visuelle ; il n'a pas besoin que la date exacte du poste chez Ergolis
soit tranchée.

Ce que les rév. 3 à 5 apportent au design, concrètement :

- Le **one-liner est écrit** (POS-3) : la home a sa première ligne, le `<title>` sa
  forme (POS-3a).

- Il ne se fera **pas sur du faux texte** : le pitch, six postes, quatre diplômes,
  quatre projets et quatre engagements sont réels et disponibles (`docs/CONTENU.md`).
- La grille projets se dessine pour **quatre cartes réelles** (PROJ-10), pas pour un
  book vide, et peut compter sur des **liens repo** (CONT-5).
- **CV-7 est la contrainte majeure de l'étape** : la timeline doit rendre des
  **expériences simultanées**, à l'écran comme à l'impression. C'est le point où les
  gabarits de CV tout faits échouent — et, incidemment, une occasion de tenir NFR-2
  (non-templaté) par la **structure** plutôt que par la décoration.
- La **feuille print du CV** (CV-4) est un livrable de cette étape, pas une finition.
- Le volet i18n **tombe** (§3.6) ; le volet domaine **tombe** (§5).

**Ne pas publier avant** d'avoir fermé §7.2 : une date fausse ou un intitulé périmé sur
un site qui se réclame du sérieux technique coûte plus cher que l'absence de site
(NFR-1).
