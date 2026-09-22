<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="lib/ui/GUI/resources/logo.dark.png">
    <img src="lib/ui/GUI/resources/logo.png" alt="P&amp;DA" width="140">
  </picture>
</p>

<h1 align="center">PDA.extension</h1>

<p align="center">
  Le déploiement agence de
  <a href="https://github.com/aliae2425/418.extension">418.extension</a> —
  boîte à outils Revit pour la production de documents.
</p>

<p align="center">
  <a href="LICENSE"><img alt="Licence MIT" src="https://img.shields.io/badge/licence-MIT-black"></a>
  <a href="https://github.com/aliae2425/418.extension/tags"><img alt="Dernier tag" src="https://img.shields.io/github/v/tag/aliae2425/418.extension?label=amont&color=black"></a>
  <a href="https://github.com/aliae2425/418.extension/releases"><img alt="Releases" src="https://img.shields.io/github/v/release/aliae2425/418.extension?label=release&color=black&display_name=tag"></a>
  <img alt="Revit 2026+" src="https://img.shields.io/badge/Revit-2026%2B-black">
  <a href="MIRROR.md"><img alt="Miroir" src="https://img.shields.io/badge/miroir-418.extension%2Fmain-black"></a>
</p>

---

## Ce dépôt

C'est un **miroir** de la branche `main` de
[418.extension](https://github.com/aliae2425/418.extension), à la marque de
l'agence : même code, onglet **PDA**, logo P&DA. Deux écarts avec l'amont, et
c'est tout — l'outil **Matériaux** n'est pas embarqué, et les icônes portent le
logo de l'agence.

**Le développement se fait sur [418.extension](https://github.com/aliae2425/418.extension)**,
pas ici. Ce dépôt ne reçoit que des resynchronisations — voir
[`MIRROR.md`](MIRROR.md). Ne pas en brancher, ne pas y ouvrir de PR.

## Installation

1. Installer [pyRevit](https://github.com/eirannejad/pyRevit).
2. Cloner ce dépôt sous le nom exact `PDA.extension` :

   ```bash
   git clone https://github.com/aliae2425/PDA.Extension.git "%APPDATA%\pyRevit\Extensions\PDA.extension"
   ```

3. Dans Revit : onglet **pyRevit → Reload** (ou `Ctrl+F5`).

L'onglet **PDA** apparaît dans le ruban. Pour mettre à jour : `git pull`, puis
**Reload**.

## L'onglet PDA

| Panneau | Bouton | Ce que ça fait |
|---|---|---|
| Export | **Export** | Export PDF/DWG en lot, par jeu de feuilles ou feuille par feuille, avec profils |
| Tools | **Dupliquer feuilles / vues** | Duplication en N copies, renommage à la volée |
| Tools | **Renommer feuilles / vues** | Rechercher-remplacer, préfixe, suffixe |
| Tools | **ImageCrop**, **SvgImport** | Découpe d'images importées, import de SVG |
| Align | 9 boutons | Aligner, centrer, répartir les éléments d'une vue |
| PDA | **À propos** | Version, dépôt, licence |

Tous les outils affichent un **aperçu avant validation** : rien n'est modifié
dans le modèle avant le clic sur le bouton d'action.

La documentation complète des outils est dans le
[README de l'amont](https://github.com/aliae2425/418.extension#readme).

## Problème ?

- **L'onglet PDA n'apparaît pas** : vérifier que le dossier s'appelle bien
  `PDA.extension` et qu'il est dans `%APPDATA%\pyRevit\Extensions`, puis **Reload**.
- **Un bouton reste grisé** : Revit 2026 minimum.
- **Autre** : [ouvrir une issue sur l'amont](https://github.com/aliae2425/418.extension/issues).

## Licence

[MIT](LICENSE) © 2025 — code sous licence MIT, logo P&DA propriété de l'agence.
