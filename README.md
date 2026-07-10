# DPL-TDAH — Les Makaras (UMAA, CH Valvert)

Site de présentation du Dispositif de Première Ligne TDAH adulte
et formulaire de demande associé.

## Structure

```
index.html                → page de présentation      (racine du domaine)
demande/index.html        → formulaire de demande     (/demande/)
```

Tous les liens internes sont **relatifs**. Le site fonctionne à l'identique :
- en ligne (Cloudflare Pages, GitHub Pages…)
- hors ligne, en ouvrant `index.html` par un double-clic

Le formulaire de demande génère son PDF entièrement dans le navigateur ;
aucune donnée patient n'est transmise ni stockée sur un serveur.

**Une seule dépendance réseau** : le mot de passe des téléchargements est lu
dans la cellule **B3** d'une feuille Google publiée en CSV. Le site doit donc
pouvoir joindre `docs.google.com` pour déverrouiller les téléchargements.
Le reste de la page fonctionne sans connexion.

## Déploiement (Cloudflare Pages)

Create application → Pages → Connect to Git → sélectionner ce dépôt
- Framework preset : **None**
- Build command : *(vide)*
- Build output directory : `/`

Puis Custom domains → `umaa-makaras.com` (racine).
Le formulaire sera automatiquement servi sur `umaa-makaras.com/demande/`.

⚠️ Désactiver GitHub Pages sur ce dépôt (Settings → Pages → Source : None)
pour éviter une URL `github.io` en doublon.

## Mise à jour

Modifier les fichiers, puis `git push`. Cloudflare redéploie automatiquement.

## Mot de passe des téléchargements

Lu dans la cellule **B3** de la feuille Google publiée (URL dans `index.html`).
Pour le changer : modifier B3. Aucun redéploiement nécessaire.

⚠️ Ce mécanisme **n'est pas une protection**. La feuille est publiée
publiquement et son URL figure dans `index.html` : n'importe qui peut lire B3.
Les fichiers restent par ailleurs accessibles directement par leur URL.
C'est un garde-fou contre un accès fortuit, pas une serrure.
Ne pas y placer de donnée confidentielle.
