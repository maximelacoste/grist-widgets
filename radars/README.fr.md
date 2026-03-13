# Grist Widgets

> 🇬🇧 [Read in English](README.md)

Widgets personnalisés pour [Grist](https://www.getgrist.com/), librement réutilisables et adaptables.

---

## 📡 widget_radar.html — Graphes radar multi-catégories

Visualise des scores sur plusieurs axes sous forme de graphes radar (toile d'araignée), directement dans Grist. Idéal pour analyser des profils d'élèves, des évaluations multi-critères, ou tout jeu de données à plusieurs dimensions.

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
- **Mode présentation** : ouvre un nouvel onglet dédié (`presenter.html`) avec navigation clavier et plein écran
- **Bascule de langue intégrée** (FR / EN) : préférence enregistrée dans les options du widget Grist

### Fichiers

| Fichier | Rôle |
|---|---|
| `widget_radar.html` | Widget à intégrer dans Grist |
| `presenter.html` | Page de présentation plein écran (ouverte automatiquement) |

Les deux fichiers doivent être hébergés au **même endroit**.

### Installation

#### 1. Héberger les fichiers

Les widgets doivent être servis depuis un hébergeur qui autorise l'intégration en iframe. [Netlify](https://netlify.com) fonctionne parfaitement et est gratuit :

1. Télécharge `widget_radar.html` et `presenter.html`
2. Sur Netlify : **Add new site → Deploy manually** → glisse-dépose un dossier contenant les deux fichiers
3. Netlify te fournit une URL du type `https://ton-site.netlify.app/widget_radar.html`

> ⚠️ GitHub Pages et jsDelivr ne fonctionnent pas car ils bloquent l'intégration en iframe.

#### 2. Ajouter le widget dans Grist

1. Dans ton document Grist, ajoute un **widget personnalisé** (Custom Widget)
2. Colle l'URL Netlify de `widget_radar.html` dans le champ URL
3. Configure le **"Sélectionner par"** sur ta table de données
4. Règle l'**accès aux données** sur **"Lire la table"**
5. Clique sur un enregistrement → les graphes s'affichent

#### 3. Configurer les graphes

Clique sur **⚙️** en haut à droite du widget pour ouvrir le panneau de configuration.

#### 4. Changer de langue

Clique sur **FR/EN** pour basculer entre français et anglais. La préférence est enregistrée dans les options du widget Grist et persiste entre les sessions.

#### 5. Mode présentation

Clique sur **▶ Présentation** pour ouvrir `presenter.html` dans un nouvel onglet avec :

- Navigation **← →** au clavier entre les enregistrements
- Bouton **plein écran** natif
- Compteur de position (**3 / 7**)

### Structure attendue des données

Une ligne = un enregistrement (ex. un élève). Les scores sont dans des colonnes numériques, idéalement préfixées par catégorie :

| Colonne | Description |
|---|---|
| `lang_comprehension` | Score de compréhension (Langage) |
| `math_calcul` | Score de calcul (Mathématiques) |
| `compor_attention` | Score d'attention (Comportement) |
| … | … |

Les noms de colonnes sont entièrement configurables depuis le panneau ⚙️.

Un fichier CSV de démonstration (`eleves_scores.csv`) est disponible pour tester rapidement avec des données fictives.

### Accessibilité

Ce widget vise la conformité W3C/WCAG 2.1 AA :
- Tous les boutons icônes ont un attribut `aria-label` explicite
- Le panneau de configuration utilise `role="dialog"` avec piège de focus, fermeture à l'Échap et restauration du focus
- Les en-têtes d'accordéon sont navigables au clavier (Entrée / Espace)
- Les éléments `<canvas>` ont `role="img"` et `aria-label`
- Tous les éléments interactifs ont des styles `:focus-visible` visibles
- Les labels sont associés aux champs via `for`/`id`

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
