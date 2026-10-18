# Notus

Masque les visages d'une photo, directement dans le navigateur. Rien n'est envoyé : la détection et le rendu tournent sur l'appareil.

**Utiliser :** ouvrir la page sur le téléphone, choisir une photo, régler, enregistrer. « Ajouter à l'écran d'accueil » pour l'avoir comme une app.

## Gestes

- Glisser verticalement (photo ou zone du bas) : choisir l'option.
- Glisser horizontalement ou tourner la molette : régler. Un coup sec lance la molette.
- Tap sur la photo : plein écran (pincer pour zoomer). Appui long : voir l'original.
- Réglages › Manuel › Sélection : toucher un visage pour retirer ou ajouter son masque.

## Réglages et rendus

- **Seuil** : nombre de visages masqués, du plus évident au moins sûr.
- **Marge** : taille du masque autour du contour (0 à 1).
- **Affichage** : cadres, contours, points et scores du détecteur (jamais exportés).
- **Rendus** : Couleur, Bruit, Emoji, Lumière (−100 ténèbres · +100 lumière), Néon.

Export JPEG ou PNG, sans métadonnées EXIF.

## Technique

Une seule page statique, aucune dépendance de build.

- Détection : SCRFD-2.5G (InsightFace), deux passes pour les foules.
- Contour : 106 points (InsightFace 2d106det).
- Inférence : [onnxruntime-web](https://github.com/microsoft/onnxruntime) 1.22, WebAssembly.

```
index.html   l'app
vendor/      onnxruntime-web (MIT)
models/      modèles ONNX (voir licences)
```

Servir le dossier tel quel (GitHub Pages, ou `python3 -m http.server`).

## Licences

- **Code** : MIT, voir [LICENSE](LICENSE).
- **onnxruntime-web** : MIT, © Microsoft.
- **Modèles `models/*.onnx`** : publiés par [InsightFace](https://github.com/deepinsight/insightface) **pour un usage non commercial et de recherche uniquement**. Ils seront remplacés par des modèles sous licence libre avant toute version stable.
