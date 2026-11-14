# Vidéos de projet (GORT-14 à 18)

Les projets vidéo HyperFrames vivent **dans le dépôt de leur projet** : ils y ont
leurs captures, leurs polices et leurs bruitages. Ici, seulement ce qu'il faut pour
refaire le fichier publié.

## Fourmy : `assets/video/fourmy.mp4` (55 s, 1280×720, 2,4 Mo)

- **Source** : `github.com/ekylibre/fourmy`, dossier `videos/journee-semis-mais`
  (film de 81 s, relu le 12/11/2026, voir son `REVIEW.md`).
- **Montage court** : `fourmy-court/index.html` remplace l'`index.html` du film.
  Plans retirés : `plan` (formulaire), `depart` (9 h 15), `cahier`. Bruitages
  décalés avec leurs scènes. Les scènes elles-mêmes ne changent pas.
- **Accord** : Pierre Haurigot (ses parcelles sont à l'écran), acquis selon
  l'utilisateur le 2026-11-14.
- **Refaire** :

  ```bash
  cp fourmy-court/index.html <fourmy>/videos/journee-semis-mais/index.html
  cd <fourmy>/videos/journee-semis-mais && npx hyperframes render -o renders/master.mp4 --video-frame-format png
  ffmpeg -i renders/master.mp4 -vf scale=1280:720:flags=lanczos -c:v libx264 -preset slow \
    -crf 26 -pix_fmt yuv420p -movflags +faststart -c:a aac -b:a 64k -ac 1 fourmy.mp4
  ffmpeg -ss 9 -i renders/master.mp4 -frames:v 1 -vf scale=1280:720 affiche.png   # → fourmy.webp
  ```
