# Rapport de fin de chantier — RENE CUISINES

Application web installable (PWA) pour remplir sur téléphone le rapport de fin de chantier et produire un PDF signé.

## Fonctionnement
1. **Chantier** : client, adresse, type de travaux, équipe
2. **Contrôles** : points à vérifier selon le type de travaux
3. **Réception** : sans réserve / avec réserves, appréciation du client
4. **Photos & croquis** : photos annotables, documents scannés, croquis au doigt
5. **Signatures** : installateur et client, puis génération du PDF

Les données restent sur le téléphone (IndexedDB) jusqu'au clic sur « Nouveau ». Rien n'est envoyé sur Internet.

## Fichiers
| Fichier | Rôle |
|---|---|
| `index.html` | Application complète (interface, logique, génération du PDF) |
| `jspdf.umd.min.js` | Bibliothèque jsPDF (génération du PDF) |
| `fonts/` | Police Inter hébergée localement (licence OFL, voir `fonts/LICENSE-Inter.txt`) |
| `sw.js` | Service worker : fonctionnement hors connexion |
| `manifest.webmanifest`, `icon-*.png` | Installation sur l'écran d'accueil |

## Mise à jour
Après toute modification d'un fichier, incrémenter la version du cache dans `sw.js` (`const C="rfc-vN"`) pour que les téléphones récupèrent la nouvelle version.

## Envoi par email (désactivé)
`MAIL_ENDPOINT` est vide dans `index.html`. Avant de l'activer : l'adresse du service sera visible publiquement si le dépôt reste public ; le service doit vérifier le code équipe, limiter le nombre d'envois et journaliser les envois.
