# Toutes les rues à pied

Page publique de @attends.je.texplique : le parcours le plus court pour passer dans toutes les rues d'une ville,
découpé en étapes d'environ 4 h (20 km à 5 km/h), en fichiers GPX. Site statique, sans dépendance à installer :
`index.html` lit `villes.json` et `<ville>/carte.json` ; Leaflet vient de cdnjs, le fond de carte d'OpenStreetMap.

```
index.html          la page
villes.json         villes, chiffres et étapes (départ, arrivée, stations, km, durée, lien GPX)
<ville>/carte.json  tracé simplifié de chaque étape pour la carte (0 = rue nouvelle, 1 = rue refaite)
<ville>/gpx/        un GPX par étape + <ville>-complet.gpx
```

Lien direct vers une étape : `…/#lyon/12` (pratique pour répondre à un commentaire).

## Régénérer ou ajouter une ville

Tout est produit par `outils/parcours/generer.py` dans le dépôt de production du compte (non public), à partir du
circuit calculé pour la vidéo (`videos/<NN>/calculations/donnees/parcours.json`) :

```
cd ~/Projects/tiktok/outils/parcours && python3 generer.py ~/Projects/parcours-a-pied
```

Nouvelle ville : ajouter une entrée dans `VILLES` (generer.py) et un fichier `donnees/stations_<ville>.json`
(métro, tram et gares, requête Overpass sur OpenStreetMap).

## Mise en ligne (GitHub Pages), une seule fois

1. Compte GitHub de la chaîne : `attendsjetexplique` (créé le 15/11/2026).
2. Créer un dépôt **public** nommé `attendsjetexplique.github.io` : la page sera à `https://attendsjetexplique.github.io/`.
3. Pousser ce dossier sur ce dépôt (branche `main`).
4. Dépôt → Settings → Pages → Source : *Deploy from a branch*, branche `main`, dossier `/ (root)`.
5. Attendre 1-2 minutes, ouvrir l'adresse, tester un téléchargement.

## Licences (à vérifier avant publication)

- Paris : filaire des voies, opendata.paris.fr. Si le jeu est sous ODbL, les GPX en sont un dérivé : garder la
  mention de la source et redistribuer les GPX sous ODbL.
- Lyon : voies de la Métropole de Lyon, data.grandlyon.com : vérifier la licence sur la fiche du jeu.
- Stations et fond de carte : © contributeurs OpenStreetMap, ODbL (mention présente en pied de page et sur la carte).
- Fond de carte : serveur de tuiles d'OpenStreetMap, prévu pour un usage modéré. Si la page devient très
  fréquentée, passer à un fournisseur de tuiles dédié.
