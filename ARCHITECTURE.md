# Architecture — Dédicaces 1.0.0

## Organisation

`dedicaces.html` regroupe HTML, CSS, dictionnaire français / anglais et JavaScript. Aucune bibliothèque ni police externe n’est chargée. `index.html` est la page de présentation. `favicon/favdedic.png` est l’unique ressource graphique externe au HTML.

## Données et persistance

`events` contient les fiches. Chaque fiche conserve son `id`, ses dates `start` / `end`, son statut, son lieu, son site, ses contacts, son hôtel, ses `trips`, ses `slots`, ses `files`, ses `notes` et son indice `colorTone`.

- IndexedDB : base `eigrutel-dedicaces`, version 1, magasin `agenda`, clé `events`.
- `draft` est une copie séparée : Annuler ne modifie pas la fiche enregistrée.
- `persist()` attend la validation de la transaction avant de modifier l’état affiché.
- En cas d’échec d’ouverture du stockage, mode mémoire avec bandeau et avertissement à la fermeture si des données n’ont pas été exportées.
- Pièces jointes : PDF, JPEG, PNG ou WebP, encodées en URL de données ; limite d’ajout de 10 Mio par document.
- Langue : clé localStorage `eigrutel-dedicaces-language`, indépendante des fiches.

## Sauvegardes

Format : `{ "app": "eigrutel-dedicaces", "version": 1, "appVersion": "1.0.0", "events": [...] }`.

`version` désigne le schéma JSON, pas la version publique. `appVersion` est informatif. Les sauvegardes antérieures sans `appVersion` restent acceptées. Les éventuelles anciennes valeurs `rating` restent compatibles à l’import, sans interface d’étoiles.

`validateImport()` vérifie les dates, heures, tableaux, identifiants uniques et documents avant de demander le remplacement de l’agenda. Les valeurs canoniques des statuts et modes de transport restent en français afin de préserver la compatibilité.

## Interface et calendrier

`render()` dirige vers les cartes, la fiche ou l’emploi du temps. `withColors()` équilibre les couleurs de la palette et conserve les indices existants. Les mini-calendriers colorent tous les jours compris entre le premier et le dernier jour d’une fiche, sauf annulation ; plusieurs fiches partagent la case par un dégradé.

`schedule()` répartit les trajets et créneaux par jour, découpe les trajets de nuit et attribue des colonnes aux blocs qui se chevauchent. Les dates du calendrier sont construites en heure locale afin d’éviter les décalages de jour liés à UTC.

Les grilles de formulaire utilisent `minmax(0, 1fr)`, des éléments rétrécissables et des contraintes de largeur sur les champs natifs date/heure, notamment pour Safari.

## Traduction

Le dictionnaire `EN` associe les libellés français à leurs traductions. `translate()` sert aux textes générés et messages. Les marqueurs `data-i18n` identifient uniquement les textes d’interface dans le HTML. `applyLanguage()` traduit ces éléments et les attributs d’accessibilité / placeholders connus ; un observateur applique la traduction aux fragments ajoutés dynamiquement.

Les textes saisis, noms de fichiers et notes ne reçoivent jamais ces marqueurs. Les dates utilisent `fr-FR` ou `en-GB`, les calendriers commencent le lundi dans les deux langues. Les exemples sont créés dans la langue choisie et deviennent ensuite des fiches ordinaires.

## Sécurité et confidentialité

Les valeurs utilisateur sont échappées avant insertion dans le HTML. Les liens de festival sont limités à HTTP(S), sans identifiants intégrés. La politique CSP interdit les connexions de données et les objets incorporés. Les liens externes sont déclenchés par l’utilisateur. Les scripts et styles intégrés sont permis pour conserver l’autonomie du fichier.

## Maintenance

Modifier le HTML source, puis vérifier syntaxe JavaScript, création/modification/suppression, FR/EN, conservation des saisies, sauvegarde/rechargement, import JSON ancien et rejet de fichiers invalides, calendriers et rendu mobile/tablette. Aucun outil de compilation n’est nécessaire à l’utilisation.

## English overview

A dependency-free HTML application with embedded styles, translations and JavaScript. Event records and base64 attachments are stored in IndexedDB; language preference is stored separately. The editor uses a separate draft and commits only after validation. JSON schema version 1 is retained for backward compatibility. Interface markers and a dictionary provide localisation without translating user data. Calendar dates use local time, and overlapping timetable blocks are assigned separate lanes.
