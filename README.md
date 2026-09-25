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

Le fichier `CNAME` contient `doc.scribae.eu`. Pour l'utiliser : chez le
gestionnaire DNS de `scribae.eu`, créer un enregistrement `CNAME` (nom `doc`
vers `<compte>.github.io`), puis `Settings` → `Pages` → `Custom domain`, et
cocher « Enforce HTTPS ». Si le site est hébergé ailleurs, supprimer `CNAME`.

## Contenu du zip

| Fichier | Rôle |
| --- | --- |
| `index.html` | Toute la page : styles, icônes, illustrations, contenu, script (thème clair/sombre, menu mobile, apparition au défilement, routage vitrine ↔ documentation, bandeau d'annonce). |
| `src/bandeau.json` | Le **bandeau d'annonce** : présence, titre, texte et lien. C'est ce fichier qu'on modifie pour publier une annonce (voir plus bas). |
| `favicon.svg` | Icône d'onglet (marque Scribae). |
| `src/illustrations/*.svg` | Les six illustrations unDraw recolorées (variante claire + sombre). |
| `.nojekyll` | Désactive Jekyll. |
| `CNAME` | Domaine personnalisé `doc.scribae.eu`. |

## Bandeau d'annonce (`src/bandeau.json`)

Un bandeau peut s'afficher en tête de **toutes** les pages (présentation et
documentation). Son contenu ne vit pas dans la page mais dans
`src/bandeau.json`, un simple fichier de texte : **on l'ouvre sur GitHub, on
clique sur le crayon, on change ce qui suit, puis « Commit changes »**. GitHub
Pages republie le site en une minute environ, et le bandeau change alors pour
**tous les visiteurs** — sans rien recompiler, sans mot de passe.

    {
      "actif": false,
      "titre": "Scribae 1.6.1q est disponible",
      "texte": "Image Docker officielle, rangement par fichiers et annuaire OIDC côté service.",
      "lienLibelle": "Voir le journal des versions",
      "lienUrl": "https://github.com/aplds/scribae/releases",
      "fermable": true
    }

| Champ | Effet |
| --- | --- |
| `actif` | `true` affiche le bandeau, `false` le retire (la page redevient exactement ce qu'elle était). |
| `titre` | En gras, en bleu. Peut rester vide. |
| `texte` | Le corps du message, en gris. Peut rester vide (mais l'un des deux doit être rempli). |
| `lienLibelle`, `lienUrl` | Le bouton du bandeau : il n'apparaît que si **les deux** sont remplis. Un lien externe s'ouvre dans un nouvel onglet ; un lien interne (`#documentation`) reste dans la page. |
| `fermable` | `false` retire la croix : l'annonce reste alors visible par tous, quoi qu'ils fassent. |

Le bandeau est visible sans rechargement particulier : la page lit ce fichier à
chaque visite (avec un paramètre qui écarte les caches). Si le fichier est
absent ou mal formé (virgule oubliée, guillemet non fermé), le bandeau ne
s'affiche pas et la page reste intacte — il n'y a rien d'autre à surveiller.
Le champ `_aide` n'a aucun effet : c'est un rappel pour la personne qui édite.

La source de vérité reste le générateur Perchance : `src/bandeau.json` y est
identique, et la page y fonctionne de la même manière.

## Mettre à jour

Le contenu fait foi dans le générateur Perchance (source de vérité). Pour
régénérer ce zip : recopier `index.html`, remplacer les `[root.site.<clé>]`
par les valeurs de la liste `site` de `main.pjs`, dé-échapper les accolades
(\{ → {, \} → }), puis renvoyer le tout ici.

Le bandeau d'annonce fait exception : `src/bandeau.json` se modifie
**directement dans le dépôt**, sans régénérer quoi que ce soit (cf. la section
« Bandeau d'annonce » ci-dessus). Le recopier depuis le générateur n'est utile
que si la structure du fichier elle-même change.

Liens : dépôt <https://github.com/aplds/scribae>, démonstration
<https://demo.scribae.eu/>.

Documentation annexe relevée sur Scribae **1.6.1q** (23 septembre 2026) :
image officielle Docker Hub `docker.io/aplds/scribae:latest`, rangement par
fichiers, annuaire OIDC côté service.
