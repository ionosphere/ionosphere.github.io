# Site personnel — David Joulin — Conception

> Statut : **direction visuelle validée, architecture à revoir** (`/sc:design`, 2026-07-16).
> Ce document décrit **le comment**. Le **quoi et le pourquoi** sont dans **`SPEC.md`** ;
> la matière factuelle dans **`CONTENU.md`**.
>
> **Ce document ne contient pas de code d'implémentation** — il contient des schémas de
> données, des contrats de gabarit et un système de tokens. L'implémentation relève de
> `/sc:implement`.
>
> **Décisions validées par l'utilisateur le 2026-07-16** :
> 1. **Direction visuelle : « Assolement »** (§1).
> 2. **Bootstrap est abandonné** (§5) — il contredisait §6 de la spec.

---

## 0. Ce que le design doit tenir

Les exigences qui **commandent** la conception, par ordre de contrainte :

| Exigence | Ce qu'elle impose au design |
| --- | --- |
| **CV-7** | La timeline doit rendre des expériences **simultanées**. Toute forme qui *se lit* comme une succession ment. **C'est la contrainte structurante.** |
| **PROJ-3 / PROJ-4** | Ajouter un projet = **une entrée YAML**. Ajouter une étude de cas = **un fichier Markdown**, le lien apparaît seul. Zéro retouche de gabarit. |
| **ACT-8b** | Le schéma des publications doit porter `auteur` **et** `rôle` en **champs distincts** — sinon le gabarit ne *peut pas* dire « édité » plutôt que « écrit ». |
| **NFR-2** | Ne pas ressembler à un thème. L'identité passe par la **typo et la structure** (ID-3), pas par un logo. |
| **NFR-3** | Contraste, clavier, sémantique. **Jamais d'information portée par la couleur seule.** |
| **CV-4** | La feuille print est un **livrable**, et elle doit tenir le parallélisme. |
| **§5** | GitHub Pages `safe: true` → **plugins whitelistés uniquement**. Piège **libsass 1.5.2** sur `clamp()`. |
| **§6** | **Aucun script tiers.** → §5 de ce document. |

---

## 1. Direction visuelle — « Assolement »

### 1.1 La thèse

**Le problème posé par CV-7 — des bandes qui courent en parallèle sur des années — a
déjà un nom et une forme dans le métier de David Joulin : l'assolement.**

Un plan d'assolement, c'est des parcelles en lignes, des campagnes en colonnes, et des
bandes qui cohabitent. C'est exactement la forme dont CV-7 a besoin. Ce n'est pas une
métaphore plaquée :

- **C'est l'objet que rend son propre logiciel** — Ekylibre est un ERP agricole ;
- **OSFarm porte un dépôt `itineraire-technique`** dont la description est *« a
  visualisation tool to show agricultural technical itineraries »* ;
- **Le RPG** (Registre Parcellaire Graphique) code les parcelles **par couleur et par
  code**, ce qui règle NFR-3 au passage (§1.3).

**Structure = information.** Le dispositif n'illustre pas le parcours : il l'**encode**.
Et il fait du site une démonstration de POS-1 — le site est dessiné dans le langage du
métier qu'il raconte.

### 1.2 Le risque assumé

Rendre un CV comme un plan de culture peut virer au gadget. Ce qui l'en empêche :

- **La forme est fonctionnelle avant d'être expressive** — c'est un diagramme de Gantt,
  la façon canonique de montrer de la simultanéité. Sans référence agricole, ce serait
  *quand même* la bonne réponse à CV-7.
- **La boldness est dépensée là, et nulle part ailleurs.** Tout le reste est discipliné :
  pas d'illustration, pas de dégradé, pas de motif, pas d'animation décorative.
- **Une seule chose est retirée** *(règle de Chanel)* : les **engagements associatifs ne
  figurent pas** dans l'assolement de la home. Ils sont pourtant parallèles eux aussi —
  mais quinze bandes en accueil noient le signal. Ils ont leur propre plan sur `/activite`.

### 1.3 Couleur — dérivée du RPG, pas du « vert agriculture »

Les deux CV sont verts. « Agriculture → vert » est le réflexe, donc le template.
La palette vient d'ailleurs : **du codage des parcelles par usage du sol**.

**Neutres**

| Token | Hex | Emploi |
| --- | --- | --- |
| `--sol` | `#F7F8F5` | Fond. Blanc cassé **froid** — délibérément **pas** un crème (`#F4F1EA` est le défaut esthétique du moment). |
| `--encre` | `#14201A` | Texte. Noir **vert**, pas noir pur — l'encre des relevés. |
| `--trait` | `#CBD1C6` | Filets, séparateurs, grille de campagne. |

**Parcelles — la nature de l'engagement, pas la décoration**

La couleur **encode une catégorie réelle** du parcours :

| Token | Hex | Code | Ce que ça désigne |
| --- | --- | --- | --- |
| `--p-entreprise` | `#C8A64B` | `ENT` | Entreprise fondée — Ekylibre |
| `--p-salariat` | `#6E8F55` | `SAL` | Emploi salarié — COBAS, Bordeaux Sciences Agro, Ergolis, bziiit |
| `--p-independant` | `#7A5570` | `IND` | Indépendant — Ionosphere Consulting |
| `--p-agricole` | `#A8785A` | `AGR` | Agricole — GAEC Joulin |
| `--p-stage` | `#8A8F6B` | `STG` | Stage — Charentes Alliance *(ajouté le 2026-07-16)* |

> **Pourquoi `STG` mérite sa propre catégorie** plutôt que d'être rangé en `SAL` :
> un stage n'est pas un emploi. Le coder « salariat » **surévaluerait** l'expérience —
> exactement le genre d'imprécision que NFR-1 fait payer. Le système l'a encaissé en
> deux lignes : un token, un cas dans `parcelle.html`.

**Accent**

| Token | Hex | Emploi |
| --- | --- | --- |
| `--releve` | `#2E5A8C` | Liens, focus. **Bleu de relevé** — l'hydrographie des cartes IGN. Choisi contre le rouge cadastral, trop proche du terracotta ambiant, et distinct des quatre remplissages. ~5,9:1 sur `--sol`. |

> **NFR-3 — jamais la couleur seule.** Chaque parcelle porte **son code** (`ENT`, `SAL`,
> `IND`, `AGR`) en mono, à côté de sa couleur. Ce n'est pas une béquille
> d'accessibilité ajoutée après coup : **c'est ainsi que le RPG fonctionne**. La
> contrainte et le référentiel disent la même chose.
>
> **Contraste des bandes** : le remplissage est une **teinte à ~30 %**, l'arête gauche
> est à pleine intensité. Les libellés sont en `--encre` sur la teinte → contraste large.

### 1.4 Typographie — le mono porte ce qui ne se traduit pas

**LANG-4 est un cadeau au design.** La spec dit : *les jetons techniques restent tels
quels — `Ruby`, `PostGIS`, `AGPL-3.0`, les handles ; seule la prose est en français.*

**Cette règle devient le système typographique** :

| Rôle | Fonte | Licence | Emploi |
| --- | --- | --- | --- |
| **Display** | **Bricolage Grotesque** | SIL OFL | `h1`, `h2`. **Avec retenue.** Axe *Wonky* **désactivé**, `opsz` respecté. |
| **Prose** | **Source Sans 3** | SIL OFL | Corps de texte. Diacritiques françaises solides, ne lutte pas avec le display. |
| **Jeton** | **IBM Plex Mono** | SIL OFL | **Les jetons LANG-4**, les campagnes, les codes RPG, les coordonnées. |

- **Mono = l'intraduisible et le machine-readable. Sans = la voix française.**
  La distinction est **lisible sans légende** et elle est **vraie**.
- **Les trois fontes sont libres et auto-hébergées** dans le repo. C'est cohérent avec le
  sujet (un site sur le logiciel libre servi par des fontes libres), et **exigé par §6** :
  Google Fonts est un tiers.
- **Pourquoi Bricolage Grotesque** : ce n'est ni Inter, ni Geist, ni Playfair, ni Space
  Grotesk — c'est-à-dire aucun des défauts. C'est une grotesque à caractère, avec des
  partis pris assumés. ⚠️ **Risque** : son axe *Wonky* la rend joueuse ; pour un lectorat
  DSI, il est **désactivé** et la fonte reste cantonnée aux titres.

### 1.5 Le geste unique

> **L'assolement.** Le reste de la page est délibérément silencieux.

### 1.6 Images et marques — ajouté le 2026-07-16

Le site était intégralement textuel. Trois familles d'images sont entrées, chacune
avec une règle. **Toutes sont auto-hébergées** : §6 interdit le moindre tiers.

| Famille | Où | Règle |
| --- | --- | --- |
| **Visuels de projet** (PROJ-5 `visuel`) | cartes du book | Captures **des sites réels**, 16∶9, WebP, ~12 ko pièce. C'est du **contenu encadré**, pas une marque — d'où sa légitimité. |
| **Marques** d'organisation | CV, engagements | **Logo réel si on l'a, monogramme typographique sinon.** Voir ci-dessous. |
| **Portrait** | `/cv` **uniquement** | Convention du CV français. **Pas dans le hero** : celui-ci porte la thèse, pas un visage — et 320 px ne tiendraient pas un grand format (NFR-1). |

#### Le système de marques — pourquoi un monogramme

Les logos fournis sont un **arc-en-ciel sans rapport avec la palette RPG** : vert LFD,
cyan GAIA, bordeaux Ocealia, jaune/bleu bziiit, scène dessinée Piloterra. **Alignés tels
quels, ils produisent le bandeau LinkedIn — c'est-à-dire NFR-2.** Et la couverture est
trouée : **trois postes sur huit** ont un logo.

D'où la règle : **logo réel quand il existe, monogramme dans la fonte de titre sinon**,
à la couleur RPG de sa parcelle. Ce n'est pas un pis-aller :

- **ID-3 fait reposer l'identité sur la typo** — un monogramme est un signe de plein droit ;
- il **comble le trou de couverture** : plus de colonne à moitié vide ;
- **la moitié des marques du site sont des lettres**, ce qui casse net l'effet
  « mur de logos » ;
- les logos réels restent **petits, sur fond neutre** : des repères, pas des taches qui
  se disputeraient l'assolement.

#### Ce qui a été retiré

- **Pas de marque sur les cartes projet** : la capture porte **déjà** le logo, en grand.
  Un second exemplaire à 38 px n'ajoutait rien — et celui de Piloterra, une scène
  dessinée, s'y réduisait à un pâté illisible. *(La règle de Chanel appliquée : l'accessoire
  en trop.)*
- **Pas de visuel de projet à l'impression** : quatre captures couleur mangeraient une
  page pour une information déjà écrite. Le portrait et les marques, eux, s'impriment.

---

## 2. L'assolement — spécification du composant

### 2.1 Forme

Grille CSS. **Colonnes = campagnes** (années). **Lignes = parcelles** (postes, projets).

```
                     '06   '08   '10   '12   '14   '16   '18   '20   '22   '24   '26
                      │     │     │     │     │     │     │     │     │     │     │
POSTES
 bziiit          SAL                                                          ▐████  CTO
 Ekylibre        ENT                          ▐███████████████████████████████████  Co-fondateur & CEO
 Ionosphere      IND        ▐███████████████████                                     Consultant AgroTIC
 Ergolis         SAL                    ▐███████                                     Chef de projet MOA
 Bordeaux Sc.Agro SAL       ▐███████████████                                         Ingénieur / Enseignant
 COBAS           SAL  ▐███████                                                       Ingénieur NTIC
 GAEC Joulin     AGR   ▐████████████████████████████████                             Agriculteur

TRAVAUX
 Ekylibre                                     ▐███████████████████████████████████  AGPL-3.0 · 486 ★
 Lexicon                                                                ▐██████████  MIT
 GAIA                                                                   ▐████████    MIT
 Piloterra                                                              ▐██████████
```

**Ce que la forme rend visible, et qu'aucune liste ne rendrait** :

- **Ionosphere Consulting chevauche Bordeaux Sciences Agro et Ergolis** — trois bandes,
  une seule période. C'est le fait que le CV DSI avait effacé, confirmé en rév. 7.
- **Deux postes en cours** (Ekylibre, bziiit) — CV-7 l'exige, la forme l'absorbe.
- **Les travaux courent sous les postes** — POS-1 rendu littéral : *le book est la preuve
  du CV*, parce que les bandes se superposent aux mêmes années.

### 2.2 Pourquoi postes **et** travaux sur le même plan

**HOME-2** exige un accès de **rang égal** au parcours et aux projets. Deux sections
côte à côte créent toujours une hiérarchie de lecture. **Un seul assolement, deux familles
de bandes, n'en crée aucune** — et c'est *vrai* : Ekylibre est à la fois un poste et un
projet, et PROJ-12 établit que les projets, les emplois et les associations sont le même
écosystème.

> **HOME-2 est satisfaite par la structure, pas par un arbitrage de mise en page.**

### 2.3 Mécanique — grille CSS, zéro JS

- **Origine** : `2006` par défaut (`--origine`), **2002 sur `/cv`** si le GAEC est
  réintégré (CV-6, §7.2 ouvert).
- Chaque bande reçoit ses colonnes en **propriétés personnalisées inline**, calculées en
  Liquid :
  ```
  style="--c1: {{ colonne_debut }}; --c2: {{ colonne_fin }}"
  ```
  → `grid-column: var(--c1) / var(--c2);`
- **`fin: null` = en cours** → la bande court jusqu'à la campagne courante.
  ⚠️ **Le build classique ne rebuild que sur push** : une bande « en cours » se fige à la
  date du dernier push. Acceptable — mais **ce n'est pas un affichage de fraîcheur** au
  sens d'ACT-4 : la campagne décrit le parcours, elle ne date pas le site.
- **Aucun JS.** La grille est statique ; les bandes sont des liens.

### 2.4 Sémantique et accessibilité (NFR-3)

- Le plan est une **`<ol>`** — chaque parcelle une `<li>`. La grille est de la **mise en
  forme**, la liste est la **structure**.
- **La grille visuelle n'est jamais la seule source** : chaque parcelle porte ses dates
  en clair (`<time datetime>`), lisibles par lecteur d'écran et **visibles à l'impression**.
- **Code RPG + couleur** — jamais la couleur seule (§1.3).
- L'en-tête de campagnes est décoratif → `aria-hidden="true"`.
- Focus visible sur chaque bande cliquable.
- `prefers-reduced-motion` respecté (il n'y a de toute façon aucune animation de fond).

### 2.5 Responsive (NFR-5)

| Largeur | Rendu |
| --- | --- |
| ≥ 900 px | Identité · piste · rôle sur trois colonnes. Échelle des campagnes en tête. |
| 600–900 px | Identité · piste sur deux colonnes, rôle sous la piste. Échelle conservée. |
| < 600 px | **La grille reste.** Identité empilée au-dessus de sa piste, pleine largeur. Seule l'échelle des campagnes tombe. |

> ✅ **Révisé au montage (2026-07-16).** Ce document prévoyait de **masquer la grille**
> sous 600 px et de faire porter le parallélisme par la prose. **Renoncé** : à 390 px,
> 25 campagnes font encore ~14 px chacune — la grille tient, il suffit d'empiler
> l'identité au-dessus de la piste. Vérifié sur capture réelle en 390 px : les
> chevauchements Ergolis / Bordeaux Sciences Agro / Ionosphere **restent visibles**.
>
> Abandonner la démonstration de CV-7 sur mobile aurait été un **repli**, pas une
> adaptation — c'est là que la majorité des visiteurs arrivent. Les dates en clair
> portent l'absolu, les bandes portent le relatif, c'est-à-dire le parallélisme.

---

## 3. Architecture Jekyll

### 3.1 Arborescence

```
.
├── _config.yml
├── CNAME                        ← ❌ N'EXISTE PAS (§5 : pas de domaine personnalisé)
├── _data/
│   ├── identite.yml             identité, one-liner, pitch, contacts
│   ├── parcours.yml             postes — porte CV-7
│   ├── formation.yml
│   ├── competences.yml
│   ├── projects.yml             LE BOOK — PROJ-1
│   ├── engagements.yml          ACT-3
│   ├── publications.yml         ACT-2 — porte ACT-8b
│   └── interventions.yml        ACT-2 (talks)
├── _projects/                   PROJ-2 — collection native, sans plugin
│   └── ekylibre.md              une étude de cas = un fichier
├── _layouts/
│   ├── base.html
│   ├── page.html
│   └── projet.html
├── _includes/
│   ├── assolement.html          ← le composant signature
│   ├── parcelle.html
│   ├── projet-carte.html
│   ├── publication.html         ← porte ACT-8a
│   └── jeton.html               ← LANG-4 : rendu mono
├── _sass/
│   ├── _tokens.scss
│   ├── _type.scss
│   ├── _assolement.scss
│   ├── _cartes.scss
│   └── _print.scss              ← CV-4
├── assets/
│   ├── css/style.scss
│   └── fonts/                   3 fontes libres, auto-hébergées (§6)
├── index.html                   home
├── cv.html
├── projets.html
└── activite.html
```

> **LANG-6 tenu** : aucun français dans les noms de fichiers de structure, les clés YAML
> ou les classes CSS. Les URL restent `/cv`, `/projets`, `/activite` — *ces trois-là sont
> français mais ce sont des **URL publiques**, pas des identifiants techniques ; les
> renommer après indexation coûterait du SEO. Choix conscient, conforme à l'esprit de
> LANG-6.*

### 3.2 `_config.yml` — l'essentiel

```yaml
title: David Joulin
tagline: Directeur technique, systèmes d'information agricoles libres   # POS-3a
url: https://ionosphere.github.io      # §5 — centralisé (LANG-7)
baseurl: ""                            # site utilisateur → servi à la racine
lang: fr                               # LANG-1
plugins:
  - jekyll-seo-tag                     # NFR-7 — whitelisté
  - jekyll-sitemap                     # NFR-7 — whitelisté
collections:
  projects:
    output: true
    permalink: /projets/:name/
```

> ⚠️ **`baseurl` doit rester vide.** `ionosphere` est un **compte utilisateur**
> (ID-4) : `ionosphere.github.io` est servi **à la racine**. Un `baseurl` non vide
> casserait tous les liens.
>
> ⚠️ **Aucune URL absolue en dur** nulle part — ni gabarit, ni contenu. C'est ce qui
> garde le coût d'un futur domaine à zéro (§5).

### 3.3 `_data/parcours.yml` — le schéma qui porte CV-7

```yaml
- id: bziiit
  organisation: bziiit
  role: Directeur technique (CTO)
  debut: 2026-01
  fin:                      # vide = en cours
  nature: salariat          # → couleur + code RPG
  lieu: Bordeaux
  faits:
    - Direction technique : projets et environnements de production.
    - Veille IA & Data ; audit, expertise et formation.

- id: ekylibre
  organisation: Ekylibre
  role: Co-fondateur & CEO  # ✅ rév. 7 — pas « directeur technique »
  debut: 2014-11
  fin:                      # en cours — DEUXIÈME poste courant, CV-7
  nature: entreprise
  lieu: Bègles / Saint-Porchaire
```

**Ce que le schéma rend possible, et qui est non négociable** :

- **`fin:` vide = en cours.** Deux entrées sans `fin` → **deux postes courants**. Aucune
  logique de gabarit ne doit supposer qu'il n'y en a qu'un.
- **Rien n'ordonne, ni n'exclut, les chevauchements.** Le gabarit trie par `debut` et
  **dessine ce qu'on lui donne**. Il n'existe **aucun code** qui « corrige » un
  chevauchement — c'est précisément l'erreur que le CV DSI a commise.
- **`nature`** est une clé fermée : `entreprise | salariat | independant | agricole`.
  Elle pilote la couleur **et** le code RPG.

### 3.4 `_data/projects.yml` — PROJ-1, PROJ-5

```yaml
- id: ekylibre                          # ← la clé de PROJ-4
  nom: Ekylibre
  tagline: ERP agricole open source — gestion, traçabilité, comptabilité.
  role: Co-fondateur & CEO
  stack: [Ruby, PostgreSQL, PostGIS]    # jetons LANG-4 → mono
  licence: AGPL-3.0                     # jeton LANG-4 → mono
  repo: https://github.com/ekylibre/ekylibre
  site: https://ekylibre.org
  statut: actif                         # actif | maintenu | archivé
  debut: 2015
  fin:
  featured: true                        # ← HOME-3
  visuel: /assets/img/projets/ekylibre.png
```

### 3.5 PROJ-3 et PROJ-4 — le mécanisme

**C'est le cœur de l'exigence centrale.** Le lien entre une carte et son étude de cas
**ne se câble pas à la main** :

```liquid
{%- assign detail = site.projects | where: "ref", projet.id | first -%}
{%- if detail -%}
  <a href="{{ detail.url }}">Étude de cas</a>
{%- endif -%}
```

Et dans `_projects/ekylibre.md` :

```yaml
---
ref: ekylibre        # ← la seule chose à écrire pour que le lien apparaisse
layout: projet
---
```

| Geste | Coût | Exigence |
| --- | --- | --- |
| Ajouter un projet **sans** page détail | **1 entrée dans `projects.yml`.** Rien d'autre. | ✅ **PROJ-3** |
| Ajouter une **étude de cas** | **1 fichier `_projects/<id>.md`** avec `ref: <id>`. Le lien apparaît seul. | ✅ **PROJ-4** |
| Retirer une étude de cas | Supprimer le fichier. Le lien disparaît seul. | ✅ |

> **Aucun plugin** : les collections sont du Jekyll natif (§5).
> ⚠️ **Piège** : si `ref` ne correspond à aucun `id`, l'étude de cas devient orpheline —
> publiée mais liée depuis nulle part. **`htmlproofer` ne le verra pas** (le lien n'est
> pas mort, il est absent). À couvrir par une vérification au build.

### 3.6 `_data/publications.yml` — ACT-8b

**Le schéma est ce qui empêche une faute d'attribution.**

```yaml
- titre: L'IA des Champs — une autre culture de l'IA
  auteurs: [Hervé Pillaud, Karine Cailleaux-Breton, David Joulin]
  role: co-auteur                    # ← rôle de DJ, distinct des auteurs
  editeur: Éditions France Agricole
  annee: 2026
  url: https://ia-des-champs.lovable.app/

- titre: La Vauzelle — Deux siècles de son histoire
  auteurs: [Francis Joulin]          # ← DJ N'Y EST PAS
  role: éditeur                      # ← mise en page, numérisation, mise en ligne
  annee: 2026
  pages: 209
  poids: 24 Mo                       # NFR-4 — un lien qui pèse 24 Mo se signale
  url: https://sci-chenes-verts.github.io/assets/livre/la-vauzelle-deux-siecles.pdf
```

**Contrat de rendu — `_includes/publication.html`** :

- **`auteurs` s'affiche toujours**, avant le rôle. Une publication ne peut pas être rendue
  sans son auteur.
- **`role` s'affiche toujours**, et il est **visuellement distinct** — `role: éditeur` ne
  doit jamais pouvoir se lire comme une signature.
- Rendu attendu :
  ```
  La Vauzelle — Deux siècles de son histoire
  Francis Joulin · 209 p.
  [Édition et mise en ligne : David Joulin]      ← rôle, traité comme une mention
  ```
- ⚠️ **Interdit** : une liste de publications où les deux titres se présentent
  identiquement. **ACT-8a** : s'attribuer le témoignage d'un tiers **par simple
  placement** est le seul type d'erreur que ce site ne peut pas se permettre — l'auteur
  est une personne réelle, identifiable, et de sa famille.

### 3.7 `_includes/jeton.html` — LANG-4 rendu

```liquid
<code class="jeton">{{ include.valeur }}</code>
```

Trivial, et c'est le but : **les jetons ne sont jamais écrits en dur dans un gabarit**.
Ils viennent des `_data` et reçoivent tous le même traitement mono. La règle LANG-4
devient **mécanique**, pas une discipline de rédaction (LANG-5).

---

## 4. Pages

### 4.1 Home — `index.html`

```
┌──────────────────────────────────────────────────────┐
│  David Joulin                                        │  HOME-1
│  Directeur technique — vingt ans de systèmes         │  POS-3
│  d'information pour l'agriculture, en logiciel libre.│
│                                                      │
│  [pitch court, 2–3 lignes, première personne]        │  ID-2
├──────────────────────────────────────────────────────┤
│  L'ASSOLEMENT                                        │  ← le geste
│  postes + travaux, mêmes campagnes                   │  HOME-2, HOME-4, CV-7
│  → /cv          → /projets                           │
├──────────────────────────────────────────────────────┤
│  TRAVAUX EN AVANT     (featured: true)               │  HOME-3
│  [Ekylibre] [GAIA] [Lexicon] [Piloterra]             │
├──────────────────────────────────────────────────────┤
│  ACTIVITÉ  → /activite      CONTACT                  │  HOME-5
└──────────────────────────────────────────────────────┘
```

**Le hero est une thèse, pas une accroche** : l'assolement dit en une image ce que le
one-liner dit en une phrase — *vingt ans, plusieurs choses à la fois, toujours les mêmes
sujets*. C'est POS-1 rendu visible avant d'être lu.

> ⚠️ **HOME-3 est piloté par `featured: true`**, jamais par une liste écrite à la main
> (l'exigence le dit). **Les quatre projets du lancement sont tous `featured`** — donc la
> grille « en avant » et le book **affichent la même chose au lancement**. Ce n'est pas un
> bug, mais **la home et `/projets` risquent de faire doublon**. À trancher au montage :
> soit la home montre 2–3 projets, soit elle assume la redite tant que le book est court.

### 4.2 `/cv`

- **L'assolement complet** — origine 2002 si le GAEC est réintégré (CV-6, ouvert).
- Le détail de chaque poste : rôle, faits, lieu.
- Formation, compétences (groupées par famille, jetons en mono).
- **Appel à l'action print** — CV-5 : *« Imprimer / enregistrer en PDF »*, **pas** un
  faux bouton de téléchargement. **Aucun PDF n'existe** (CV-3).

### 4.3 `/projets` — le book

- Grille de cartes depuis `projects.yml`.
- **PROJ-10** : la grille est conçue pour **quatre cartes réelles**, pas pour un book
  vide ni pour vingt. À quatre, une grille 2×2 large tient mieux qu'un 4×1 étriqué.
- **PROJ-7** (filtres) : **non implémenté**. À quatre projets, un filtre est un ornement
  qui signale que le book est trop court pour lui. L'exigence le donnait « souhaitable,
  non requis, à arbitrer selon le volume réel ». **Arbitré : non.**
- **PROJ-11** : Ekylibre porte 486 ★ et une AGPL-3.0 vérifiables. Ces deux jetons
  s'affichent **sur la carte**, pas seulement dans l'étude de cas — c'est la seule preuve
  de traction du dossier, et elle se vérifie en un clic.

### 4.4 `/activite`

- **Contributions open source** (ACT-1) — profil `github.com/ionosphere`, dépôts épinglés.
- **Publications** (ACT-2) — deux livres, **rendus par `_includes/publication.html`**
  (§3.6). **C'est ici que se joue ACT-8.**
- **Interventions** (ACT-2).
- **Engagements** (ACT-3) — leur propre assolement, réduit : quatre bandes.

---

## 5. CSS — sans Bootstrap

**Décision validée** : Bootstrap est **abandonné**. Il venait de `seconde-nature.github.io`,
un site aux besoins différents, et il **contredisait §6** (« aucun script tiers »).

| Ce que Bootstrap apportait | Remplacement |
| --- | --- |
| Grille | **CSS Grid** — et c'est la grille qui *fait* la signature. Bootstrap ne sait pas dessiner un assolement. |
| Menu mobile | **`<details>` / `<summary>`** natif — accessible, clavier, **zéro JS**. |
| Accordéon | `<details>` idem. |
| Reset / normalisation | ~20 lignes maison. |
| Utilitaires | Tokens CSS + ~400 lignes de SCSS. |

**Ce que l'abandon gagne** : §6 satisfait (aucun tiers), **NFR-2** servi (le look Bootstrap
*est* le look template — le re-thémer revenait à lutter contre l'objectif), NFR-4 servi
(rien à charger).

**Ce qu'il coûte** : tout écrire. ~400 lignes de SCSS pour ce site. C'est le bon prix.

> ⚠️ **§5 de `SPEC.md` doit être amendé** — il impose encore « Bootstrap 5 via CDN ».
> Voir §7 ci-dessous.

### 5.1 Le piège libsass — non négociable

GitHub Pages épingle **`jekyll-sass-converter 1.5.2` (libsass)**, qui **échoue** sur un
terme additif dans `clamp()`. **Tout `clamp()` fluide doit envelopper l'addition dans
`calc()`** :

```scss
// ❌ casse le build GitHub Pages, silencieusement
font-size: clamp(2rem, 1.6rem + 4vw, 5rem);

// ✅
font-size: clamp(2rem, calc(1.6rem + 4vw), 5rem);
```

> **`safe: true` rend le diagnostic pénible** : un plugin non whitelisté est ignoré **sans
> erreur** (§5). Corollaire : **construire en local avec `bundle exec jekyll build` ne
> prouve rien** sur le build distant — l'environnement local n'est pas épinglé (§5).

---

## 6. Print — `_print.scss` (CV-4)

**La feuille print est un livrable, pas une finition.** C'est l'artefact que le recruteur
emporte, et il n'existe **aucun PDF** derrière (CV-3).

| Règle | Raison |
| --- | --- |
| Masquer nav, pied de page, appels à l'action | CV-4 |
| **URL des liens en toutes lettres** : `a[href^="http"]::after { content: " (" attr(href) ")" }` | CV-4 — un lien n'est pas cliquable sur papier |
| `break-inside: avoid` sur chaque poste | CV-4 — pas de coupure au milieu d'une expérience |
| **L'assolement s'imprime** — compact, en tête de feuille | **CV-7 s'applique au print.** C'est le cas où une mise en page en colonnes résiste le moins bien à la pagination. |
| Dates en clair sous chaque poste | Le plan seul ne suffit pas sur papier |
| **Jamais le numéro de téléphone** | **CONT-3** — y compris à l'impression |
| Jamais d'âge | §7.2 point 12 — le CV DoYouBuzz est déjà périmé |

> ⚠️ **À vérifier au montage** : l'assolement compte ~21 colonnes. Sur A4 portrait, la
> grille est serrée. Deux issues — réduire l'empan (origine 2006 plutôt que 2002), ou
> imprimer le plan en bandeau pleine largeur avec les campagnes tous les 4 ans.
> **Le rendu print n'est pas acquis : il est à éprouver, pas à supposer.**

---

## 7. Ce que ce design demande de changer dans `SPEC.md`

Le design a rencontré **une contradiction** et **un arbitrage** que la spec ne portait pas :

1. ⚠️ **§5 impose « Bootstrap 5 via CDN » — §2 et §6 interdisent tout tiers dans le
   chargement.** Les deux ne peuvent pas tenir. *(L'écart a été introduit en rév. 2, en
   rédigeant « aucun analytics… aucun tiers dans le chargement », sans voir que Bootstrap
   tombait dedans.)*
   → **Tranché par l'utilisateur : Bootstrap est abandonné.** §5 est à amender.

2. **PROJ-7 (filtres) — arbitré : non implémenté.** L'exigence renvoyait au volume réel :
   quatre projets ne justifient pas un filtre.

3. ⚠️ **Google Fonts est un tiers** → les trois fontes sont **auto-hébergées**. À noter
   en §5, qui n'évoquait pas les fontes.

---

## 8. Ce qui reste ouvert

**Le site est monté et le build passe.** État des points relevés en conception, après
confrontation au rendu réel :

| # | Point | Issue |
| --- | --- | --- |
| 1 | Sous 600 px, la démonstration de CV-7 disparaîtrait | ✅ **Résolu par la structure, pas par la prose.** La grille tient à 390 px. Voir §2.5. |
| 3 | L'assolement à l'impression « n'est pas acquis » | ✅ **Acquis.** Vérifié sur PDF A4 : bandes contourées lisibles en noir et blanc, chevauchements visibles, URL en clair, aucun téléphone. 4 pages. |
| 5 | Origine de l'assolement : 2002 ou 2006 | ✅ **Sans objet.** L'origine est **calculée** sur les données. Retirer le GAEC la remonte à 2006 tout seul — rien à toucher (NFR-6). |
| 2 | Home et `/projets` font doublon | ⚠️ **Subsiste**, assumé : les 4 projets sont tous `featured`. À quatre, en cacher deux appauvrirait l'accueil sans enrichir le book. *(Corrigé au passage : un projet `featured: false` fuitait dans l'assolement de la home — voir §5.1 ci-dessous.)* |
| 4 | Études de cas orphelines | ⚠️ **Subsiste.** Un `ref` erroné ne casse aucun lien, il en **supprime** un : `htmlproofer` est aveugle. À couvrir par une vérification de build. |
| 6 | Bricolage Grotesque à éprouver | ⚠️ **À valider par l'utilisateur** sur le rendu réel. L'axe *Wonky* est désactivé et la fonte est cantonnée aux titres, mais le caractère reste un choix à confirmer. |
| 7 | **Dates du stage Charentes Alliance** | ⚠️ **Conflit non résolu.** L'utilisateur dit **2002-2004** ; le CV DoYouBuzz dit **juin 2004 – juin 2005**. Contenu identique (HACCP + ATEX) : c'est le même stage. 2002-2004 retenu — parole de l'intéressé, et cohérent avec l'IUP Génie des procédés (2002-2004) qu'il chevauche exactement. **À confirmer.** |

### 8.3 `devenu` — le nom d'époque contre le nom actuel

Ajouté le 2026-07-16, à l'occasion du stage Charentes Alliance.

**« Ocealia » n'existe que depuis décembre 2015**, née de la fusion de *Charentes
Alliance* et de *Coréa Poitou-Charentes*. Écrire « Ocealia · 2002-2004 » serait un
**anachronisme** : David Joulin n'a jamais travaillé chez Ocealia — il a fait son stage
chez Charentes Alliance, que le groupe a ensuite absorbée.

**Règle** : le **nom d'époque** reste le titre ; le nom actuel est une **mention**
(`devenu:`), traitée en jeton discret. On garde la vérité historique **et** la
reconnaissance d'aujourd'hui — un lecteur du monde agricole charentais saurait
qu'Ocealia n'existait pas en 2002.

*(Le logo affiché est bien celui d'Ocealia : c'est la continuité de l'entité, et c'est
le seul fourni.)*

### 8.1 Bugs trouvés au montage — et ce qu'ils apprennent

Sept défauts, dont plusieurs invisibles à la lecture du code :

| Bug | Cause | Leçon |
| --- | --- | --- |
| **Nav invisible** | Un `<details>` fermé masque ses enfants : la CSS desktop ne pouvait pas les rouvrir. | Le `<details>` était **surdimensionné** : un menu déroulant pour **quatre liens courts** est un réflexe, pas un besoin. Supprimé. |
| **Arêtes de parcelle écrasées** | `opacity: .32` sur la bande s'appliquait **aussi** à l'arête à pleine intensité. | Le contraste voulu en §1.3 était annulé par l'implémentation. → tokens `--parcelle-clair` explicites. |
| **Ekylibre en doublon** | Il figure en poste **et** en travail (c'est le point de POS-1), mais les deux bandes disaient « Co-fondateur & CEO ». | Une superposition **vraie** se lisait comme un **bug**. Les bandes de travaux portent désormais la licence. |
| **Titre « Engagements » en double** | Titre de section + titre de groupe de l'assolement. | Les titres de groupe ne servent qu'à distinguer des groupes : conditionnés à `nb_groupes > 1`. |
| **Référence ARIA orpheline** | Corollaire du précédent : `aria-labelledby` pointait vers un id devenu absent. | Une correction visuelle a cassé l'accessibilité. → `aria-label`, toujours valide. |
| **PDF au format `letter`** | `@page` sans `size` → défaut du navigateur, américain. | Un CV **français** qui s'imprime en letter se coupe. → `size: A4`. |
| **`featured: false` fuitait en home** | La grille filtrait sur `featured`, **l'assolement non**. | Un projet apparaissait dans le plan sans carte en dessous. **Trouvé par un test, pas par relecture.** → `featured_only`. |
| **`{"Élevage"=>"alimentation…"}` affiché sur le CV** | Piège YAML : une puce contenant « mot **:** mot » est lue comme un **dictionnaire**, pas une phrase. **10 faits** touchés. | **Le build ne bronche pas — ça s'imprime sur le site.** Le défaut était **en ligne**. → guillemets simples, et l'avertissement est en tête de `parcours.yml`, là où on ajoute une ligne. |
| **Bande noire sous deux visuels** | Recadrage 3∶2 demandé sur une capture 1280×800 : 1280×⅔ = **853 > 800** → PIL a rempli en noir. | Un recadrage qui déborde ne lève aucune erreur. → 16∶9 (720 ≤ 800), avec une assertion. |

### 8.2 Ce qui a été vérifié, pas supposé

- **PROJ-3 / PROJ-4** — éprouvés en ajoutant réellement un projet puis une étude de cas :
  la carte apparaît sur une entrée YAML, le lien d'étude apparaît **seul** sur un fichier
  Markdown, et le retrait ne laisse aucune trace.
- **ACT-8** — les deux livres se rendent en deux objets **distincts à l'œil** : *L'IA des
  Champs* « David Joulin — co-auteur » en clair ; *La Vauzelle* nomme **Francis Joulin**
  auteur et **encadre** « Éditeur : David Joulin ».
- **CV-7** — chevauchements visibles en desktop, **en mobile 390 px**, et **à l'impression**.
- **Liens** — aucun lien interne mort, aucune ancre orpheline, 12 liens externes en 200
  (`lafermedigitale.fr` renvoie 403 aux robots, 200 à un navigateur).
- **CONT-3** — le téléphone n'apparaît nulle part, PDF compris.

**Rappel — bloquants de publication, hérités de `SPEC.md` §7.2, non résolus par le design** :
les **rôles non portés par les sources publiques** (« créateur de GAIA » quand
`gaia-ia.org` ne le dit pas), les **chiffres non attestés** (80 projets, 80 sources,
750 projets à l'IA Summit), et la **date de La Ferme Digitale**.

---

## 9. Étape suivante

`/sc:implement` — dans cet ordre, parce que chaque étape dérisque la suivante :

1. **Squelette Jekyll + `_config.yml` + tokens** — vérifier **tout de suite** que le build
   GitHub Pages distant passe (le local ne prouve rien, §5.1).
2. **`_data/` réels** — parcours, projets, publications. Le contenu existe (`CONTENU.md`).
3. **L'assolement** — le composant signature, et le plus risqué. **À faire tôt.**
4. **Cartes projets + mécanisme PROJ-3/4.**
5. **Publications + `publication.html`** — ACT-8, à ne pas expédier.
6. **Feuille print** — CV-4, un livrable.
7. **Passe accessibilité + `htmlproofer`.**
