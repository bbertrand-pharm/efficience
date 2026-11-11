# Le pharmacien clinicien au service de l'efficience

Tableaux de bord des consommations de médicaments, solutés et DMS par service de soins (CHG, unité de pharmacie clinique).

- `index.html` : accueil, liste des services.
- `service.html?s=<identifiant>` : tableau de bord d'un service et dépôt de ses extractions « Analyse_conso », protégés par le mot de passe du service.
- `admin.html` : mise en place (référentiels hors GHS / LPPR / UF, services et regroupements d'UF, mots de passe, jeton GitHub) et vue d'ensemble.

Toutes les données de `data/` sont chiffrées dans le navigateur (AES-GCM 256, clé dérivée du mot de passe par PBKDF2-SHA256, 310 000 itérations). Les fichiers Excel ne sont jamais déposés dans le dépôt. Seul `data/manifest.json` (noms des services et dates de mise à jour) est en clair.

Publication : un jeton GitHub « fine-grained » limité à ce dépôt (Contents : read and write, avec expiration), saisi dans l'administration et transmis chiffré aux pages de service. L'historique Git permet de restaurer une version antérieure en cas d'erreur.
