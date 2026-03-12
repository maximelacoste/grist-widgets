# Grist Widgets

Widgets personnalisés pour [Grist](https://www.getgrist.com/), librement réutilisables et adaptables.

---

## 📡 widget_radar.html — Graphes radar multi-catégories

Visualise des scores sur plusieurs axes sous forme de graphes radar (toile d'araignée), directement dans Grist. Idéal pour analyser des profils d'élèves, des évaluations multi-critères, ou tout autre jeu de données à plusieurs dimensions.

### Aperçu

![Capture d'écran du widget radar](screenshot.png)

### Fonctionnalités

- Affichage de **N graphes radar** (sans limite) organisés en grille 2 colonnes
- **Configuration persistante** via les options du widget Grist (sauvegardée entre les sessions)
- Pour chaque graphe, réglage de :
  - Titre et emoji
  - Couleur du contour de l'étoile
  - Couleur du repère de fond (grille)
  - Échelle maximale (ex : 0–5, 0–10…)
  - Colonnes à inclure (cochées parmi toutes les colonnes de la table)
- Ajout, suppression et réorganisation des graphes depuis le panneau ⚙️
- Mise à jour automatique au clic sur un enregistrement

### Installation

#### 1. Héberger le fichier

Le widget doit être servi depuis un hébergeur qui autorise l'intégration en iframe. [Netlify](https://netlify.com) fonctionne parfaitement et est gratuit :

1. Télécharge `widget_radar.html`
2. Sur Netlify : **Add new site → Deploy manually** → glisse-dépose le fichier
3. Netlify te fournit une URL du type `https://ton-site.netlify.app/widget_radar.html`

> ⚠️ GitHub Pages et jsDelivr ne fonctionnent pas car ils bloquent l'intégration en iframe.

#### 2. Ajouter le widget dans Grist

1. Dans ton document Grist, ajoute un **widget personnalisé** (Custom Widget)
2. Colle l'URL Netlify dans le champ URL
3. Configure le **"Sélectionner par"** sur ta table de données
4. Règle l'**accès aux données** sur **"Lire la table"**
5. Clique sur un enregistrement → les graphes s'affichent

#### 3. Configurer les graphes

Clique sur **⚙️** en haut à droite du widget pour ouvrir le panneau de configuration.

### Structure attendue des données

Une ligne = un enregistrement (ex. un élève). Les scores sont dans des colonnes numériques, idéalement préfixées par catégorie :

| Colonne | Description |
|---|---|
| `lang_comprehension` | Score de compréhension (Langage) |
| `math_calcul` | Score de calcul (Mathématiques) |
| `compor_attention` | Score d'attention (Comportement) |
| … | … |

Les noms de colonnes sont entièrement configurables depuis le panneau ⚙️.

### Dépendances

- [Chart.js 4.4](https://www.chartjs.org/) — chargé via CDN
- [Grist Plugin API](https://support.getgrist.com/widget-custom/) — chargé via CDN

---

## 🔧 widget_debug.html

Widget utilitaire pour diagnostiquer la communication entre Grist et un widget personnalisé. Affiche le contenu brut de l'enregistrement sélectionné au format JSON. Utile pour vérifier que le "Sélectionner par" et l'accès aux données sont bien configurés.

---

## Licence

[MIT](LICENSE) — libre d'utilisation, de modification et de redistribution, avec mention de l'auteur original.

---

## Contribuer

Les contributions sont bienvenues ! N'hésite pas à ouvrir une *issue* ou une *pull request* pour proposer des améliorations ou de nouveaux widgets.
