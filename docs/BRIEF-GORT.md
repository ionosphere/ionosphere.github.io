# Mise à jour « Gort » : exigences

> Statut : **découverte en cours** (`/sc:brainstorm`, 2026-11-14). Document de
> **besoins** uniquement. Le *comment* relève de `/sc:design`, puis de `DESIGN.md`.
> Les codes existants (`ACT-8`, `CV-7`, `NFR-1`, `PROJ-8`…) renvoient à `SPEC.md`.
> Une fois les questions de §6 fermées, ce document sera versé dans `SPEC.md` comme
> **révision 9**.

> ⏱️ **Échéance : dépôt de l'appel d'offres le lundi 16/11/2026.** Le site doit être
> **en ligne et vérifié sur `ionosphere.github.io`** avant ce dépôt. D'où l'ordre de
> priorité de §7.

## 1. Objectif

Le site sert désormais **un lecteur de plus** : la personne qui évalue la réponse de
David Joulin dans le cadre de **Gort**. Deux choses sont à faire, et l'utilisateur les
veut toutes les deux (arbitrage du 2026-11-14) :

1. **Ajouter** les activités récentes (Gort, Fourmy, Aiffel) et mettre à jour celles
   qui ont évolué (GAIA, Lexicon, OSFarm).
2. **Réorienter la mise en avant** pour que ce lecteur trouve en moins de 10 s ce qu'il
   cherche : **une chaîne de données agricoles interopérable et libre, déjà en
   service, sur laquelle des robots peuvent s'appuyer.**

| Public | Ce qu'il cherche | Ce qu'il doit trouver en < 10 s |
| --- | --- | --- |
| Évaluateur Gort *(nouveau)* | « Sait-il fournir et évaluer de la donnée de ferme exploitable par un robot ? » | Le rôle dans Gort, la chaîne Lexicon → Ekylibre/Fourmy → Aiffel → GAIA, des preuves qui se vérifient en un clic |
| Recruteur / client | inchangé (SPEC §1) | inchangé |
| Pair technique | inchangé (SPEC §1) | inchangé |

## 2. Ce que disent les sources (relevé du 2026-11-14)

| Sujet | Fait | Source |
| --- | --- | --- |
| **Gort** | « Generic, agnostic and interoperable robots for massive technological tranformations » [sic] | osfarm.org/collective |
| | **4,5 M€ ANR, France 2030** · **porté par XLIM** | idem |
| | Consortium : XLIM (porteur), Natuition, ELATEC (constructeurs de robots), LaBRI (conseil) | idem |
| | David : **« Ekylibre, Data consulting and evaluator »** | idem |
| | « Field trials of GORT, GAIA and AOG+, fed by the data of a **digital twin of the farm** » (REBUS) | idem |
| | Dates, n° d'appel, lien XLIM/ANR, dépôt : **absents** | — |
| **Fourmy** | « Jumeau numérique de la ferme » · AGPL · **édité par Ekylibre SAS** · « reprend Ekylibre » · 57 procédures | fourmy.org |
| | David Joulin : **non cité** | — |
| **Aiffel** | Assistant agricole voix/écrit (Telegram) · branché sur Ekylibre et Lexicon · « Phase 1 en construction » · gratuit pour les adhérents OSFarm | aiffel.org |
| | Porteur : **aucun nommé** · David Joulin : **non cité** · licence : « open source », sans précision · dépôt : absent | — |
| **GAIA** | David : **« Co-createur / animateur »** · « Led by Ekylibre » | osfarm.org/collective |
| | **« Winner among 770 projects from 111 countries »**, AI Action Summit, Paris 2025 | idem |
| | **9 hackathons, 7 défis, 11 projets, 18 coachs** · hackathon SAED en cours (nov. 2026, Laval) | gaia-ia.org (refondu) |
| | « Un projet collaboratif entre La Ferme Digitale et OSFarm » | gaia-ia.org |
| **Lexicon** | **624 M de données, 55 jeux de données** · MIT · « Un commun d'OSFarm » · « Led by Ekylibre » | lexicon.osfarm.org, osfarm.org |
| **OSFarm** | David : **« President »** · projets REBUS (218 700 €, FEADER), AOG+, *IA des champs* (lauréat INRAE / INRAE Transfert) | osfarm.org/collective |
| **Ekylibre** | « more than 300 models », « more than 20 Millions items references » · © 2014–2026 | ekylibre.org |
| **Fourmy (dépôt)** | `github.com/ekylibre/fourmy` : **dépôt public depuis le 2026-11-14** · AGPL-3.0 · un seul contributeur, `ionosphere` (262 commits) · TypeScript, React + Mantine, PostgreSQL, service Python, Docker · « réécriture complète d'Ekylibre » · en ligne depuis le 07/11/2026 | `gh` (accès authentifié) |
| **Aiffel (dépôt)** | `github.com/ekylibre/aiffel` : **public** · AGPL-3.0-or-later (fichier `LICENSE` ajouté le 2026-11-14) · un seul contributeur, `ionosphere` (90 commits) · Python, FastAPI, PostgreSQL, MCP, Claude, faster-whisper | GitHub |
| **Démo** | Tableau de bord production (carte, assolement 2019, 119,11 ha), « GAEC JOULIN » | demo.ekylibre-dev.com *(session connectée)* |

**Deux conséquences sur les décisions passées :**
- **§7.2 point 10 se ferme pour GAIA.** Une source publique porte désormais un rôle :
  « co-créateur / animateur ». Voir GORT-7.
- **PROJ-8 devient publiable.** CLAUDE.md interdisait « 750 projets », introuvable. La
  source dit **770 projets, 111 pays**. On publie le chiffre **sourcé**, pas celui du CV.

## 3. Exigences fonctionnelles

### 3.1 Gort

- **GORT-1** : Gort apparaît sur le site, avec **trois faits visibles et séparés** :
  le **porteur** (XLIM), le **financement** (ANR, France 2030, 4,5 M€) et le **rôle**
  de David Joulin (*conseil data & évaluation, via Ekylibre*).
- **GORT-2** : **Gort n'est jamais présenté comme un projet de David Joulin.** C'est
  la même faute qu'ACT-8 : s'attribuer le travail d'un tiers par le seul placement.
  Gort ne prend pas la forme d'une carte du book identique à Ekylibre ou Lexicon, sauf
  si le porteur y est aussi visible que le rôle. *(Où le placer, et sous quelle forme,
  c'est à `/sc:design` de le décider. L'exigence porte sur l'attribution.)*
- **GORT-3** : les partenaires du consortium sont nommés tels que la source les nomme.
  Aucun logo tiers sans fichier auto-hébergé (§6).
- **GORT-4** : Gort renvoie à une source vérifiable (osfarm.org/collective, et la page
  XLIM ou ANR si l'utilisateur en fournit une). Pas de lien inventé.

### 3.2 Le récit d'interopérabilité (mise en avant)

- **GORT-5** : le site rend lisible **la chaîne** que Gort évalue, à partir des
  projets existants :
  *données publiques* (Lexicon) → *jumeau numérique de la ferme* (Ekylibre / Fourmy)
  → *saisie en langage naturel* (Aiffel) → *IA agricole* (GAIA) → *robots* (Gort).
  Chaque maillon renvoie à son projet. Ce n'est pas un nouveau contenu : c'est
  **POS-1 rendu explicite** (le book est la preuve du CV).
- **GORT-6** : cette chaîne est accessible **depuis la home**, au même rang que
  l'assolement, sans le remplacer. Le geste du site reste l'assolement (CV-7).

### 3.3 Projets nouveaux et mis à jour

- **GORT-7 : GAIA.** Le rôle passe à **« Co-créateur & animateur »**, que la source
  publique porte. Statut **actif** (hackathon en cours) : `fin:` vide. La distinction
  devient **« Lauréat parmi 770 projets de 111 pays — AI Action Summit, Paris 2025 »**
  (PROJ-8).
- **GORT-8 : Fourmy.** Nouvelle entrée du book. Rôle **« Créateur »**, d'après
  l'utilisateur. Le lien avec Ekylibre (« reprend Ekylibre », même éditeur) est
  visible : Fourmy est la suite d'Ekylibre, pas un projet sans rapport.
- **GORT-9 : Aiffel.** Nouvelle entrée du book. Rôle **« Créateur »**, d'après
  l'utilisateur. Statut **en construction**, sans formulation datée (ACT-4).
- **GORT-10 : NFR-1, écart en partie fermé.** Les sites fourmy.org et aiffel.org ne
  nomment pas David Joulin, mais **les dépôts le prouvent** : `ionosphere` est le seul
  contributeur des deux. Le **lien vers le dépôt** suffit donc comme preuve en un clic,
  à une condition : **le dépôt doit être public**.
  - **Aiffel** : public, la preuve tient. Le lien `repo:` est affiché.
  - **Fourmy** : public depuis le 2026-11-14, la preuve tient aussi. Lien `repo:` affiché.
- **GORT-10b : dates.** Fourmy et Aiffel : `debut: "2026-09"`. Gort : `debut: "2024"`,
  sans `fin:` (en cours).
- **GORT-10c : stack (jetons LANG-4).** Fourmy : `TypeScript`, `React`, `PostgreSQL`,
  licence `AGPL-3.0`. Aiffel : `Python`, `FastAPI`, `MCP`, licence
  `AGPL-3.0-or-later`.
- **GORT-10d : Ekylibre reste « actif »** (arbitrage du 2026-11-14). Sa carte renvoie à
  Fourmy comme à sa suite (« réécriture complète d'Ekylibre »), sans changer de
  statut.
- **GORT-11 : Lexicon.** Afficher **624 M de données, 55 jeux de données**, à la
  place de toute mention de « 7 catégories » ou de « 80 sources ».
- **GORT-12 : OSFarm.** Rôle « Fondateur & Président » maintenu, la source l'atteste.
  Le résumé cite **Gort, REBUS et AOG+** à la place de la formule vague « France 2030 /
  Horizon Europe ».
- **GORT-13** : ajouter un projet reste **une entrée dans `projects.yml`** (PROJ-3).
  Aucune de ces mises à jour ne doit demander de toucher un gabarit, à une exception
  près : la forme de Gort (GORT-2), qui peut demander un champ nouveau (par exemple
  `porteur:`).

### 3.4 Vidéos de projet (HyperFrames)

- **GORT-14** : **une vidéo par projet**, en commençant par Fourmy, Aiffel et Lexicon,
  insérée dans l'étude de cas (`_projects/<id>.md`).
- **GORT-15** : la vidéo est **produite hors ligne** avec HyperFrames et livrée en
  fichier **MP4/WebM auto-hébergé** dans `assets/`. Pas de YouTube, pas de lecteur
  tiers, aucun script (§6). Lecture native avec `<video controls>`.
- **GORT-16** : **pas de lecture automatique**, `preload="none"`, une **image d'affiche**
  et des **sous-titres** (`<track>`), ou à défaut une transcription. La vidéo doit se
  comprendre **sans le son**.
- **GORT-17** : à l'impression (CV-4), la vidéo cède la place à son affiche et à son URL
  en clair.
- **GORT-18** : poids contenu, à fixer en design. Repère : moins de 10 Mo par vidéo. Le
  dépôt GitHub Pages ne doit pas grossir de centaines de Mo.

### 3.5 Visuel de démonstration

- **GORT-19** : la capture du tableau de bord de production de la démo Ekylibre
  (carte, assolement, temps par activité) peut être publiée **telle quelle**, avec le
  nom « GAEC JOULIN » (arbitrage utilisateur). Elle est retravaillée en WebP, avec un
  texte alternatif descriptif. Elle sert au projet Ekylibre ou Fourmy (§6, question 4).

## 4. Exigences non fonctionnelles (rappel de ce qui reste vrai)

- **NFR-1** : chaque chiffre et chaque rôle se vérifie en un clic. Les chiffres
  interdits par CLAUDE.md restent interdits. **770 / 111** remplace « 750 », il ne
  s'y ajoute pas.
- **ACT-4** : pas de « mis à jour le… », pas de numéro de version (Fourmy 0.113.1,
  Lexicon 1.6.2) : ils vieillissent seuls.
- **§6** : zéro tiers au chargement, vidéos comprises.
- **Les trois pièges silencieux de CLAUDE.md** : à contrôler après chaque ajout dans
  `_data/` (YAML `mot : mot`) et dans `_sass/` (`clamp()` sans `calc()`).
- **CONT-3** : la démo et les vidéos ne montrent aucun numéro de téléphone.

## 5. Critères d'acceptation

- [ ] Un évaluateur Gort qui arrive sur la home atteint le rôle de David Joulin dans
      Gort **en un clic**, et voit XLIM comme porteur **sur le même écran**.
- [ ] Gort n'est nulle part rendu à l'identique d'un projet dont David Joulin est
      l'auteur (GORT-2).
- [ ] Fourmy et Aiffel ont une carte et sont ajoutés par `projects.yml` seul.
- [ ] GAIA affiche « Co-créateur & animateur » et « 770 projets, 111 pays », avec un
      lien vers la source.
- [ ] Chaque vidéo se lit sans requête tierce (onglet réseau vide hors
      `ionosphere.github.io`), sans lecture automatique, avec sous-titres.
- [ ] Vérifié **sur le site en ligne**. Un build local ne prouve rien (CLAUDE.md).

## 6. Questions ouvertes

**Fermées le 2026-11-14 :** Gort depuis 2024, dépôt de l'appel d'offres le 16/11/2026 ·
Fourmy et Aiffel depuis septembre 2026, dépôts `ekylibre/fourmy` et `ekylibre/aiffel`
(GORT-10 à 10c) · GAIA « Co-créateur & animateur » validé (GORT-7) · Ekylibre reste
« actif » (GORT-10d).

~~**A. Fourmy public**~~ ✅ **fait le 2026-11-14.** Historique vérifié avant : aucun
   secret (valeurs de test et `.env.example` uniquement). Les fixtures gardent les
   géométries des parcelles des fermes pilotes : ce sont les fermes de l'utilisateur,
   publication acceptée.
~~**B. LICENSE d'Aiffel**~~ ✅ **fait** (commit `41cb293`) : GitHub affiche
   maintenant AGPL-3.0.
**C. Gort : que recouvre « evaluator »** (évaluation des robots en champ, des données,
   des livrables) ? Y a-t-il une page XLIM ou ANR à citer ?
**D. Qui porte Aiffel** : Ekylibre SAS (le dépôt est sous `ekylibre/`), OSFarm (offre
   gratuite pour ses adhérents) ou bziiit ?
4. **La capture de la démo** : pour Ekylibre ou pour Fourmy ?
6. **Interventions 2026** : faut-il ajouter le 8e hackathon GAIA (SIA 2026), le
   hackathon SAED (novembre 2026), l'AG OSFarm (28 mai 2026) ou d'autres ?
   (`interventions.yml` se dit lui-même incomplet.)
7. **Vidéos** : quels projets après les trois premiers ? Une voix off, ou du texte
   seulement ? Quelle durée ? (Repère : 30 à 60 s.)
8. **REBUS et AOG+** : sont-ils des projets du book, ou une simple mention dans
   l'engagement OSFarm ?

## 7. Priorités, vu l'échéance du lundi 16/11

| Lot | Contenu | Pourquoi dans cet ordre |
| --- | --- | --- |
| **1. Données (indispensable)** | GORT-7 à 12 : GAIA, Lexicon, OSFarm corrigés ; Fourmy et Aiffel ajoutés | Ce ne sont que des entrées `_data/` (PROJ-3) : peu de risque, gain maximal. Rendre faux un rôle ou un chiffre est la seule erreur que l'évaluateur verra à coup sûr. |
| **2. Gort et la chaîne (indispensable)** | GORT-1 à 6 | C'est la raison de la mise à jour. Seul lot qui peut toucher un gabarit (GORT-2). |
| **3. Visuels** | GORT-19 (capture de la démo), visuels Fourmy et Aiffel | Rapide à faire, et ça se voit. |
| **4. Vidéos (si le temps le permet)** | GORT-14 à 18 | Le lot le plus coûteux et le moins nécessaire au dépôt. Une vidéo bâclée dessert plus qu'une étude de cas sans vidéo. Commencer par **Fourmy**. |

Chaque lot est **poussé et vérifié en ligne** avant de passer au suivant : un build
local ne prouve rien (CLAUDE.md).

## 8. Étape suivante

Les questions A et B sont fermées. Suite : `/sc:design` pour la forme de Gort
(GORT-2), le maillage de la chaîne (GORT-5/6) et l'intégration vidéo (GORT-14 à 18). La
production des vidéos (skill `hyperframes`) et le travail visuel (skill
`frontend-design`) viennent ensuite, au moment de l'implémentation.
