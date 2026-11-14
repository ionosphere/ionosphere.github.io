# ionosphere.github.io — site personnel de David Joulin

Site Jekyll statique, **en français uniquement**, servi par le **build GitHub Pages
classique** sur `https://ionosphere.github.io` (pas de domaine personnalisé).

> `ionosphere` est le **compte utilisateur GitHub personnel** de David Joulin — pas une
> organisation, et pas une marque. C'était son nom d'activité freelance (2008–2014).

## Où lire quoi

| Document | Contient | À lire avant de… |
| --- | --- | --- |
| **`docs/SPEC.md`** | **Le quoi et le pourquoi.** Exigences numérotées (`CV-7`, `PROJ-3`, `ACT-8`…), décisions et leurs raisons, questions ouvertes. | toucher au **comportement** ou au contenu |
| **`docs/DESIGN.md`** | **Le comment.** Direction visuelle, tokens, architecture, contrats de gabarit. | toucher à la **structure** ou au CSS |
| **`docs/BRIEF-GORT.md`** | La mise à jour pour l'appel d'offres Gort (nov. 2026) : exigences `GORT-n`, sources, questions ouvertes. | toucher à Gort, Fourmy, Aiffel ou à la chaîne |
| **`docs/CONTENU.md`** | **La matière factuelle** dépouillée des CV et de neuf sources en ligne, avec ses ⚠️ conflits. | écrire quoi que ce soit dans `_data/` |
| `docs/ressources/` | Les deux CV PDF d'origine. |  |
| `_sources/` | Images originales, **non déployées**. |  |

**Les exigences sont citées par leur code dans tout le code source.** Un commentaire qui
dit « CV-7 » renvoie à `SPEC.md` — la raison y est écrite. Ne pas défaire une règle sans
l'avoir lue.

## Commandes

```bash
# Le Gemfile fait échouer jekyll (gems github-pages non installées) → contourner :
JEKYLL_NO_BUNDLER_REQUIRE=true jekyll build
JEKYLL_NO_BUNDLER_REQUIRE=true jekyll serve --port 4321
```

⚠️ **Un build local qui passe ne prouve rien.** Le local tourne sous Jekyll 4 + Dart
Sass ; GitHub Pages épingle **Jekyll 3.10 + libsass + `safe: true`**. La seule preuve est
le site en ligne.

## Les trois pièges qui échouent EN SILENCE

Aucun des trois ne fait échouer le build. Tous se voient sur le site publié.

### 1. `clamp()` sans `calc()` → CSS cassé en production

libsass 1.5.2 **échoue** sur un terme additif nu dans `clamp()`.

```scss
font-size: clamp(2rem, 1.6rem + 4vw, 5rem);        // ❌ casse le build distant
font-size: clamp(2rem, calc(1.6rem + 4vw), 5rem);  // ✅
```

*Dart Sass, en local, **retire** le `calc()` du CSS compilé — c'est valide en CSS et sans
conséquence. Vérifier la **source** `_sass/`, jamais `_site/`.*

### 2. Piège YAML : `mot : mot` devient un dictionnaire

Une puce contenant un deux-points entouré d'espaces est lue comme un **Hash**. La page
affiche alors `{"Élevage"=>"alimentation, soin"}` en clair. **C'est déjà arrivé, en
production, sur dix faits du CV.**

```yaml
- Élevage : alimentation, soin.        # ❌ → Hash
- 'Élevage : alimentation, soin.'      # ✅
```

Contrôle : `ruby -ryaml -e 'YAML.load_file("_data/parcours.yml").each{|p| (p["faits"]||[]).each{|f| puts f.inspect unless f.is_a?(String)}}'`

### 3. `safe: true` ignore les plugins sans rien dire

Seuls les plugins **whitelistés** GitHub Pages tournent (`jekyll-seo-tag`,
`jekyll-sitemap`). Un plugin non whitelisté est ignoré **sans erreur**. Ne jamais
compter sur un plugin sans avoir vérifié qu'il est whitelisté.

## Règles non négociables

### ACT-8 — l'attribution des publications

**Le point le plus sensible du site.** `_data/publications.yml` porte `auteurs` **et**
`role` en champs **distincts**, et `_includes/publication.html` affiche **toujours les
deux**, visuellement séparés.

> **« La Vauzelle — Deux siècles de son histoire » est de FRANCIS JOULIN**, pas de David
> Joulin, qui en est l'**éditeur**. Ne jamais ajouter « David Joulin » à ses `auteurs`.
> Ne jamais rendre les deux publications à l'identique : s'attribuer le témoignage d'un
> tiers **par simple placement** est le seul type d'erreur que ce site ne peut pas se
> permettre — l'auteur est une personne réelle, identifiable, de sa famille.

### CV-7 — le parcours est PARALLÈLE

Plusieurs expériences se déroulent **en même temps**, et plusieurs postes peuvent être
« en cours » simultanément (`fin:` vide). **Les chevauchements ne sont pas des erreurs** :
c'est la forme réelle du parcours, et c'est ce que l'assolement démontre.

> **Aucun code ne doit « corriger » un chevauchement.** C'est exactement la faute que le
> CV de recrutement avait commise en lissant le parcours.

### §6 — zéro tiers dans le chargement

Pas de CDN, pas de Google Fonts, pas d'analytics, pas de script exécutable. Les trois
fontes (libres) et toutes les images sont **auto-hébergées**. Bootstrap a été
**abandonné** pour cette raison (`DESIGN.md` §5) — CSS Grid et `<details>` natif suffisent.

### ID-3 / ID-5 — pas de marque « Ionosphere »

Le site s'appelle **« David Joulin »**. « ionosphere » n'a le droit d'apparaître que là
où c'est une **donnée technique vraie** : l'URL, `_config.yml`, le lien de profil GitHub,
les liens de dépôts. **Jamais** en logo, filigrane, `og:site_name` ou favicon siglée —
le handle est une adresse, pas une identité.

### GORT-2 — un consortium n'est pas un projet

**Gort** (porté par **XLIM**, ANR France 2030) vit dans `_data/consortiums.yml`, **jamais**
dans `projects.yml`, et se rend par `_includes/consortium.html` : le porteur dans le
titre, le rôle de David Joulin comme une étiquette posée sur l'objet. C'est la faute
d'ACT-8 appliquée à un projet de recherche. Le détail est dans `docs/BRIEF-GORT.md`.

### CONT-3 — jamais le numéro de téléphone

Il figure dans les CV sources. Il n'est dans **aucune** donnée et ne doit apparaître
nulle part, **impression comprise**. Pas d'âge non plus (celui du CV est déjà périmé).

## Ce qu'il ne faut PAS publier

Trois chiffres du CV **ne sont attestés par aucune source publique**. Ils sont
délibérément absents du site (NFR-1 : un pair vérifie en un clic) :

- GAIA « **80 projets** » — `gaia-ia.org` dit *30 sujets, 8 hackathons, 17 coachs* ;
- Lexicon « **80 sources** » — le site affiche *7 catégories* ;
- « sélectionné parmi **750 projets** internationaux à l'IA Summit 2025 » — **faux**. La
  source (`osfarm.org/collective`) dit **770 projets, 111 pays** : c'est ce chiffre-là
  qui est publié sur la carte GAIA, avec son lien (PROJ-8, GORT-7).

Un **rôle** ne s'écrit que si une source publique le porte. GAIA : *« Co-créateur &
animateur »*, mot pour mot d'`osfarm.org/collective`. Fourmy et Aiffel : « Créateur »,
prouvé par les dépôts publics, dont `ionosphere` est le seul contributeur.

## Architecture

```
_data/         la source de vérité — TOUT le contenu (NFR-6)
_projects/     études de cas ; le front matter ne porte que `ref:`
_includes/     assolement.html (signature) · parcelle.html · marque.html
               publication.html (ACT-8) · projet-carte.html · jeton.html
               chaine.html (GORT-5, piloté par chaine.yml) · consortium.html (GORT-2)
_sass/         _tokens (palette RPG) · _assolement (le geste) · _print (CV-4)
```

- **`_includes/assolement.html`** est le **geste du site** : le CV dessiné comme un plan
  d'assolement agricole — parcelles en lignes, campagnes en colonnes. Grille CSS, **zéro
  JS**. Son origine est **calculée** sur les données : retirer une entrée la remonte toute
  seule.
- **PROJ-3 / PROJ-4** : ajouter un projet = **une entrée dans `projects.yml`**. Ajouter
  une étude de cas = **un fichier `_projects/<id>.md`** avec `ref: <id>` ; le lien
  apparaît seul. **Aucun gabarit à toucher, jamais.**
- **LANG-4/5** : les jetons techniques (`Ruby`, `PostGIS`, `AGPL-3.0`) ne se traduisent
  pas et passent tous par `_includes/jeton.html` (rendu mono). **Aucun libellé français
  en dur dans un gabarit** quand la donnée existe en `_data`.
- **`marque.html`** : logo réel si `logo:` existe, **monogramme typographique sinon**.
  Trois postes sur huit ont un logo — un système à trous ferait pire que rien.

## Conventions

- **Français** partout dans la prose et les commentaires ; **anglais** pour les
  identifiants techniques, clés YAML, classes CSS et URL de structure (LANG-6).
- Les noms d'organisation sont ceux **de l'époque** ; le nom actuel va dans `devenu:`
  (ex. *Charentes Alliance · aujourd'hui Ocealia* — Ocealia n'existe que depuis 2015).
- **ACT-4** : aucune date de fraîcheur (« dernière mise à jour »), aucune année de
  copyright. Le site ne doit pas exhiber son propre vieillissement. *(Une période de
  poste ou de projet, elle, est licite : elle décrit le contenu, pas le site.)*
