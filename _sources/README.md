# Sources d'images

Les **originaux** fournis par David Joulin. Ils ne sont **pas déployés** : Jekyll
ignore les dossiers préfixés `_`.

Les fichiers réellement servis sont dans `assets/img/`, dérivés de ceux-ci :
optimisés, détourés et redimensionnés. 909 ko d'originaux pour ~116 ko servis —
NFR-4 (performance) ne tolérait pas de déployer les deux.

| Original | Dérivé servi | Traitement |
| --- | --- | --- |
| `david_photo.jpeg` | `assets/img/david.webp` | 400→320 px, WebP |
| `bziiit_logo.png` | `assets/img/logos/bziiit.webp` | **fond blanc détouré**, 96 px |
| `ocealia.png` | `assets/img/logos/ocealia.webp` | **fond blanc détouré**, 96 px |
| `lfd.png` | `assets/img/logos/lfd.webp` | 96 px |
| `osfarm.png` | `assets/img/logos/osfarm.webp` | 3600→222 px |
| `ekylibre.svg` | `assets/img/logos/ekylibre.svg` | copié tel quel (vectoriel) |

Le détourage est un remplissage par diffusion **depuis les bords** : il n'efface que
le fond connecté au cadre, et préserve les blancs *intérieurs* au logo (le creux du
« b » de bziiit, la vague d'Ocealia). Un simple blanc→transparent les aurait troués.
