# Dédicaces

**Version stable 1.0.0 — 22 septembre 2026**

Agenda libre, autonome et bilingue français / anglais pour organiser ses dédicaces, festivals et déplacements. Conçu et développé par **Simon Léturgie**, dans le cadre d’**Eigrutel BD Academy** et d’**Eigrutel Lab — Atelier d’outils libres pour la bande dessinée**.

## Démarrer

Téléchargez le dépôt puis ouvrez `dedicaces.html` dans votre navigateur. Gardez le dossier `favicon/` à côté du HTML pour conserver l’icône. Aucun compte, aucune compilation et aucune dépendance externe ne sont nécessaires. L’interface démarre en français ; le sélecteur **FR / EN** permet de passer en anglais. Le contenu de vos fiches n’est pas traduit.

## Fonctions

- Fiches verticales en quatre colonnes sur grand écran, adaptées aux écrans plus petits ; couleurs pastel conservées d’une session à l’autre.
- Festival, dates, lieu, adresse, site web, statut et contact (e-mail, téléphone).
- Trajets, dates et heures de départ / arrivée, références de billets et de réservation.
- Hôtel, adresse, dates et référence de réservation.
- Créneaux de dédicace et emploi du temps hebdomadaire, avec gestion des chevauchements et des trajets de nuit.
- Petits calendriers mensuels à défilement continu, jours colorés comme les fiches ; un clic affiche la semaine correspondante.
- Post-it personnel, pièces jointes PDF ou images (10 Mo maximum par fichier), impression de la fiche.
- Sauvegarde locale, export et import JSON comprenant les documents joints.

## Vos données

## Partager une fiche / Share an event

Dans une fiche, **Exporter cette fiche** crée un fichier JSON à transmettre à un collègue. Le post-it et les pièces jointes sont facultatifs (décochés par défaut). Les contacts, trajets et informations d’hôtel sont inclus : vérifiez leur contenu avant de partager. **Importer une fiche**, en bas de la colonne, ajoute une copie indépendante sans remplacer les autres dédicaces. Une fiche similaire est signalée avant confirmation. Les deux personnes doivent utiliser cette version de l’application ou une version compatible.

**Export this event** creates a single-event JSON file to send to a colleague. Personal notes and attachments are opt-in; contacts, travel and hotel information are included, so check them first. **Import an event** adds an independent copy without replacing other events. Similar entries trigger a warning. Both users need this version or a compatible one.

## Stockage local

L’application fonctionne hors ligne et n’envoie pas vos données à un serveur. Les liens externes s’ouvrent uniquement à votre demande. Il n’y a pas de synchronisation entre appareils.

Les fiches et documents sont enregistrés dans IndexedDB, dans ce navigateur et pour cette adresse. La préférence de langue est enregistrée séparément dans localStorage. Si le stockage local est indisponible, un bandeau signale le fonctionnement temporaire en mémoire.

**« Sauvegarder » télécharge votre agenda JSON ; « Charger » remplace l’agenda actuel après confirmation.** Faites une sauvegarde avant de déplacer ou renommer le HTML, changer d’adresse d’hébergement, de navigateur, ou effacer les données du navigateur. Le HTML seul ne contient pas vos fiches.

Les sauvegardes des versions de travail précédentes restent compatibles : le schéma JSON conserve `version: 1`. `appVersion: "1.0.0"` indique la version du programme.

## Utilisation et hébergement

Le fichier peut être ouvert localement ou hébergé sur un serveur statique. `index.html` fournit une page d’entrée bilingue pour GitHub Pages. Le fonctionnement du stockage local, des téléchargements et des raccourcis d’écran d’accueil dépend du navigateur. Le favicon et l’icône Apple utilisent `favicon/favdedic.png`. Une icône de navigateur ne constitue pas une installation d’application native.

Voir [DEPOT_GITHUB.md](DEPOT_GITHUB.md) pour préparer le dépôt et la release, et [ARCHITECTURE.md](ARCHITECTURE.md) pour le fonctionnement du code.

## Licences

- Code : **GNU AGPL v3.0 ou version ultérieure** (`AGPL-3.0-or-later`).
- Documentation et modèles : **CC BY-SA 4.0**, sauf mention contraire.
- Marques, logos et signes distinctifs Eigrutel / Eigrutel Lab / Eigrutel BD Academy : **réservés**.

Voir [LICENSE.md](LICENSE.md) et [NOTICE.md](NOTICE.md). Les données et documents importés conservent leurs droits propres.

---

## English

**Dédicaces 1.0.0** is a free, standalone signing and festival planner by **Simon Léturgie**, developed within **Eigrutel BD Academy / Eigrutel Lab**.

Open `dedicaces.html` in a modern browser and choose **English** in the FR / EN selector. Keep the `favicon/` folder alongside the HTML. No account, build step or external library is required. User-entered content is never translated.

Features include pastel event cards, festival websites and contacts, travel and ticket details, hotels, signing sessions, a weekly timetable, continuously scrolling month calendars, personal sticky notes, attachments and printing. Cards use four columns on wide screens and adapt to smaller devices.

Your planner stays on your device, in the browser’s IndexedDB. The language preference uses localStorage. If storage is unavailable, the app displays a warning and works temporarily in memory. There is no cross-device synchronisation or data server.

**Back up** downloads a JSON file containing the planner and attachments. **Restore** replaces the current planner after confirmation. Keep a backup before moving the HTML, changing its hosting address, switching browsers or clearing browser data. The HTML is the application; the JSON contains your data. Earlier backups remain compatible (JSON schema version 1).

Code: **AGPL-3.0-or-later**. Documentation and templates: **CC BY-SA 4.0**, unless otherwise stated. Eigrutel trademarks, logos and distinctive signs are reserved. Imported content retains its own rights.
