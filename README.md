# ionosphere.github.io

Site personnel de **David Joulin** — *Directeur technique, vingt ans de systèmes
d'information pour l'agriculture, en logiciel libre.*

→ **[ionosphere.github.io](https://ionosphere.github.io)**

Jekyll statique, français, servi par le **build GitHub Pages classique**. Pas de
framework, **aucune ressource tierce**, aucun analytics, aucun cookie. ~16 ko de CSS,
trois fontes libres auto-hébergées.

## Le geste

Le CV est dessiné comme un **plan d'assolement** : parcelles en lignes, campagnes en
colonnes. Ce n'est pas une coquetterie agricole — c'est la seule forme qui rend un
parcours **parallèle**, où plusieurs expériences courent en même temps et où deux postes
peuvent être en cours ensemble. Un CV de recrutement lisse cette simultanéité ; celui-ci
la montre. Grille CSS pure, zéro JavaScript, et le même plan tient à l'impression.

## Ajouter du contenu

Tout vit dans `_data/`. **Aucun gabarit à toucher.**

| Geste | Coût |
| --- | --- |
| Ajouter un projet | **une entrée** dans `_data/projects.yml` |
| Ajouter une étude de cas | **un fichier** `_projects/<id>.md` avec `ref: <id>` — le lien apparaît seul |
| Ajouter une ligne de CV | **une entrée** dans `_data/parcours.yml` |

⚠️ **Piège YAML** — une puce contenant « mot **:** mot » est lue comme un dictionnaire et
s'imprime sur le site en `{"Élevage"=>"…"}`, sans faire échouer le build. Mettre la
phrase entre guillemets simples. Voir `CLAUDE.md`.

## Développer

```bash
JEKYLL_NO_BUNDLER_REQUIRE=true jekyll serve --port 4321
```

⚠️ **Un build local qui passe ne prouve rien** : le local tourne sous Jekyll 4 + Dart
Sass, GitHub Pages épingle Jekyll 3.10 + libsass + `safe: true`. La seule preuve est le
site en ligne.

## Documentation

| Fichier | Contenu |
| --- | --- |
| **`CLAUDE.md`** | Les pièges qui échouent **en silence** et les règles non négociables. **À lire en premier.** |
| `docs/SPEC.md` | Le **quoi** et le **pourquoi** — exigences numérotées, décisions et leurs raisons |
| `docs/DESIGN.md` | Le **comment** — direction visuelle, tokens, architecture |
| `docs/CONTENU.md` | La **matière factuelle** et ses conflits — trace des sources |
| `docs/ressources/` | Les CV d'origine |
| `_sources/` | Images originales, non déployées |
