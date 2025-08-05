# Simulateur de cadrage projet IA 🚀

Un simulateur léger et autonome (HTML/CSS/JS) pour estimer rapidement l’effort et le coût d’un projet intégrant de l’IA. Il permet de définir des phases, ajuster un TJM, appliquer une remise et une marge, puis d’exporter les résultats au format JSON.

Démo locale en un clic : ouvrez `index.html` dans votre navigateur.

## Fonctionnalités ✨

- Gestion des phases de projet
  - ➕ Ajouter, ✏️ Renommer, 🗑️ Supprimer des phases
  - ⌨️ Jours par phase avec validation optimiste
- Paramétrage des coûts
  - 💶 TJM (Taux Journalier Moyen)
  - 🏷️ Remise (%) et 📈 Marge (%) appliquées au total HT
- Résumé clair
  - 🕒 Total jours et 💰 coût estimé
  - 📋 Détail par phase
  - ✅ Valeurs après remise et avec marge
- Presets pratiques
  - ⚡ Lean : cadrage rapide, prototype express, dev noyau, tests essentiels
  - 🧩 Complet : cadrage, UX/recherche, prototype haute fidélité, dev, intégration IA, sécurité/observabilité, tests, formation/support
- Export JSON intégré
  - 🧾 Téléchargement d’un fichier récapitulatif prêt à partager
- Export PDF (devis) via impression native
  - 🖨️ Bouton « Exporter PDF (Devis) » qui prépare un en‑tête (date, référence) et ouvre la boîte de dialogue d’impression
  - 📄 Mise en page optimisée A4 (@media print) pour un rendu type devis
- UI soignée et accessible
  - 🧱 Composants “cards / buttons / inputs”, labels ARIA, focus states, responsive

## Prise en main ⚙️

1. Ouvrir `index.html` dans un navigateur moderne (Chrome, Edge, Firefox).
2. Ajuster les phases et les jours dans le panneau gauche.
3. Saisir le TJM, la remise (%) et la marge (%) dans le panneau de droite.
4. Consulter le résumé et le détail des coûts.
5. Exporter en JSON via le bouton « Exporter ».
6. Générer un PDF (devis) via le bouton « Exporter PDF (Devis) » puis choisir « Enregistrer en PDF » dans la boîte de dialogue d’impression.

Aucune installation requise. Le projet est 100% front-end et fonctionne hors-ligne.

## Fichier principal 📁

- `index.html` : contient le HTML, le CSS et le JavaScript du simulateur dans un seul fichier.

## Données exportées 🧾

Le JSON exporté inclut :
- `generatedAt` : horodatage ISO
- `tjm` : valeur du TJM
- `phases` : liste des phases `{ name, days }`
- `totals` :
  - `days` : total jours
  - `costHT` : coût total HT avant remise
  - `remisePct` : remise appliquée (%)
  - `afterRemiseHT` : total HT après remise
  - `margePct` : marge appliquée (%)
  - `totalWithMargeHT` : total HT avec marge

Exemple abrégé :
```json
{
  "generatedAt": "2025-08-05T13:20:40.000Z",
  "tjm": 800,
  "phases": [{ "name": "Développement app", "days": 10 }],
  "totals": {
    "days": 10,
    "costHT": 8000,
    "remisePct": 0,
    "afterRemiseHT": 8000,
    "margePct": 20,
    "totalWithMargeHT": 9600
  }
}
```

## Accessibilité et UX ♿

- Champs numériques avec `inputmode="decimal"` et validation visuelle
- Libellés ARIA pour lecteurs d’écran
- Composants responsives, utilisables au clavier
- Design inspiré des patterns modernes (cards, toolbars, metrics)

## Architecture technique 🧠

- Autonome : aucun framework requis
- Formatage et calculs côté client
- `Intl.NumberFormat` pour les formats monétaires et numériques
- Export via `Blob` et `URL.createObjectURL`
- Export PDF: impression native (`window.print`) avec styles `@media print` (A4) et métadonnées dynamiques (date, référence)
- Identifiants phases générés via `crypto.randomUUID()`

## Roadmap 🗺️

Idées d’améliorations possibles :
- 💾 Persistance locale (localStorage)
- 🧷 Export CSV
- 🧾 Gabarit de devis personnalisable (en-tête société/client, logo, conditions, signature)
- 🧮 Option TVA et totaux TTC dans le PDF
- 🌗 Thème clair pour l’impression dédiée
- 🧮 TVA et devis TTC
- 👥 Multi-profils (TJM par rôle)
- 📊 Courbe d’effort par phase
- 📥 Import de presets personnalisés

## Contribution 🤝

1. Forker le repo
2. Créer une branche : `feature/ma-fonctionnalite`
3. Commits clairs et atomiques
4. Ouvrir une Pull Request avec une description détaillée

Recommandations :
- Garder l’app autonome et simple
- Soigner l’accessibilité
- Maintenir la cohérence visuelle

## Licence 📄

MIT — Utilisation libre, sans garantie. Inclure la notice de licence dans les redistributions.

## Références et remerciements 🙌

UI/UX inspirée par des patterns courants (cards, boutons, inputs) popularisés dans des tutoriels et dashboards modernes, en particulier des références mentionnées dans `index.html` (dev.to, Medium, etc.).
