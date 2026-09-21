# Scribae — page d'accueil

Version **statique** de la page d'accueil, exportée depuis le générateur Perchance.
Toutes les interpolations `[root.site.*]` ont été remplacées par leurs valeurs :
le fichier `index.html` est autonome et ne dépend d'aucun moteur de gabarit.

## Héberger sur GitHub Pages

1. Créez un dépôt (ou utilisez `aplds.github.io` pour la racine du domaine).
2. Déposez à la racine : `index.html`, `favicon.svg`, `.nojekyll`.
3. Commit, puis **Settings → Pages → Source : Deploy from a branch**, branche `main`, dossier `/`, **Save**.
4. La page est en ligne à `https://<utilisateur>.github.io/<depot>/` en une minute.

Le fichier `.nojekyll` évite le traitement Jekyll (inutile ici, et source de lenteurs).

## Contenu

| Fichier | Rôle |
| --- | --- |
| `index.html` | La page complète (styles, icônes SVG, contenu, script thème clair/sombre + menu mobile). |
| `favicon.svg` | La marque Scribae (document + chevron), en SVG. |
| `.nojekyll` | Désactive Jekyll sur GitHub Pages. |

## Liens

| | |
| --- | --- |
| Démonstration | https://aplds.github.io/scribae |
| Code source | https://github.com/aplds/scribae |
| Retours | https://github.com/aplds/scribae/issues |
| Licence | https://www.gnu.org/licenses/gpl-3.0.fr.html (GNU General Public License v3.0) |

## Mise à jour

Cette copie est un export : pour modifier le texte ou la mise en page, repartez du
générateur Perchance (`main.pjs` + `index.html`) puis réexportez.
