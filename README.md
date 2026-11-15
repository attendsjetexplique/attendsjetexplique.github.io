# attendsjetexplique.github.io

Site public de @attends.je.texplique, hébergé par GitHub Pages sur le
compte GitHub de la chaîne `attendsjetexplique`. Site statique : pas de compilation, pas de dépendance à installer.

## Rangement : un dossier par projet

```
index.html        accueil : présentation, lien Instagram, liste des projets
parcours/         « Toutes les rues à pied » → https://attendsjetexplique.github.io/parcours/
<projet>/         tout futur projet, dans son propre dossier, avec sa propre page index.html
```

Ajouter un projet : créer son dossier, y mettre sa page et ses fichiers, puis l'ajouter à la liste « Projets » de
`index.html` à la racine. Rien d'un projet ne se pose à la racine.

Les anciens liens directs vers une étape (`…/#lyon/12`, avant le rangement du 15/11/2026) sont redirigés par
l'accueil vers `parcours/#lyon/12`.

## Projet « parcours »

```
parcours/index.html          la page (carte, étapes, téléchargements)
parcours/villes.json         villes, chiffres et étapes (départ, arrivée, stations, km, durée, lien GPX)
parcours/<ville>/carte.json  tracé simplifié de chaque étape pour la carte (0 = rue nouvelle, 1 = rue refaite)
parcours/<ville>/gpx/        un GPX par étape + <ville>-complet.gpx
```

Lien direct vers une étape : `https://attendsjetexplique.github.io/parcours/#lyon/12`.

Tout le dossier est produit par `outils/parcours/generer.py` dans le dépôt de production du compte (privé), à partir
du circuit calculé pour la vidéo :

```
cd outils/parcours && python3 generer.py      (depuis le dépôt de production)
```

Nouvelle ville : ajouter une entrée dans `VILLES` (generer.py) et un fichier `donnees/stations_<ville>.json`
(métro, tram et gares, requête Overpass sur OpenStreetMap), relancer, vérifier, pousser.

## Mise en ligne

Pousser sur `main` suffit : GitHub Pages republie en une à deux minutes. Les commits portent le nom de la chaîne et
son adresse noreply GitHub (réglage local du dépôt), jamais une adresse personnelle. Si plusieurs comptes GitHub sont connectés
sur le Mac, activer celui de la chaîne avant de pousser (`gh auth switch --user attendsjetexplique`).

## Licences (à vérifier)

- Paris : filaire des voies, opendata.paris.fr. Si le jeu est sous ODbL, les GPX en sont un dérivé : garder la
  mention de la source et redistribuer les GPX sous ODbL.
- Lyon : voies de la Métropole de Lyon, data.grandlyon.com : vérifier la licence sur la fiche du jeu.
- Stations et fond de carte : © contributeurs OpenStreetMap, ODbL (mention en pied de page et sur la carte).
- Fond de carte : serveur de tuiles d'OpenStreetMap, prévu pour un usage modéré. Si la page devient très
  fréquentée, passer à un fournisseur de tuiles dédié.
