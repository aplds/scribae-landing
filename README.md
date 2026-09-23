# doc.scribae.eu — vitrine et documentation de Scribae

Site **statique** : la page d'accueil (vitrine) et son annexe technique
(`#documentation`). C'est la version publiée du générateur Perchance « scribae »
— les gabarits Perchance ont été résolus ici en HTML pur, pour que le site
fonctionne tel quel sur n'importe quel hébergeur statique.

## Publier sur GitHub Pages (hébergement dans un dépôt)

1. Créer un dépôt (par ex. `scribae-site`), puis déposer **le contenu de ce
   zip à la racine du dépôt** (`index.html` doit être à la racine).
2. `Settings` → `Pages` → `Build and deployment` : source « Deploy from a
   branch », branche `main`, dossier `/`, puis `Save`.
3. Au bout d'une minute le site est en ligne.

Le fichier `.nojekyll` (vide) désactive Jekyll : sans lui, GitHub interprète
les accolades de la documentation comme des balises de gabarit et la
publication échoue. Ne pas le supprimer.

## Domaine personnalisé (doc.scribae.eu)

Le fichier `CNAME` contient `doc.scribae.eu`. Pour l'utiliser :

1. Chez le gestionnaire DNS de `scribae.eu`, créer un enregistrement
   `CNAME` : nom `doc`, valeur `<compte>.github.io` (ou, pour un domaine
   apex, des enregistrements `A` vers les IP de GitHub Pages).
2. Dans `Settings` → `Pages` → `Custom domain`, saisir `doc.scribae.eu` et
   cocher « Enforce HTTPS ».

Si le site est hébergé ailleurs, supprimer `CNAME`.

## Contenu du zip

| Fichier | Rôle |
| --- | --- |
| `index.html` | Toute la page : styles, icônes, illustrations, contenu, script (thème clair/sombre, menu mobile, apparition au défilement, routage vitrine ↔ documentation). |
| `favicon.svg` | Icône d'onglet (marque Scribae). |
| `src/illustrations/*.svg` | Les six illustrations unDraw recolorées (variante claire + sombre). |
| `.nojekyll` | Désactive Jekyll. |
| `CNAME` | Domaine personnalisé `doc.scribae.eu`. |

## Mettre à jour

Le contenu fait foi dans le générateur Perchance (source de vérité). Pour
régénérer ce zip : recopier `index.html`, remplacer les `[root.site.<clé>]`
par les valeurs de la liste `site` de `main.pjs`, dé-échapper les accolades
(\{ → {, \} → }), puis renvoyer le tout ici.

Les liens (dépôt, démonstration, licence) sont ceux du `main.pjs` d'origine :
dépôt <https://github.com/aplds/scribae>, démonstration
<https://demo.scribae.eu/>.
