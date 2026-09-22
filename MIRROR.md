# Miroir de 418.extension

Ce dépôt est un miroir de la branche `main` de
[418.extension](https://github.com/aliae2425/418.extension), avec **un seul
commit** posé par-dessus (`chore: rebranding PDA`) qui change le nom, le logo et
retire l'onglet Manage.

Tout le reste doit rester identique. Ne développe pas de fonctionnalité ici :
elle irait dans 418.extension, puis descendrait par resynchro.

## Resynchroniser

`git rebase upstream/main` **ne marche pas** : le commit de marque renomme tout
`418.tab/` en `PDA.tab/`, et dès qu'`upstream` déplace ou supprime un fichier
dans l'intervalle, git rend la main sur une quinzaine de conflits
rename/rename et rename/delete. Le commit de marque n'est pas de l'historique à
préserver, c'est une recette à rejouer :

```bash
git fetch upstream
git reset --hard upstream/main      # on repart de zéro sur le nouvel upstream
# rejouer la recette ci-dessous, puis :
git commit -am "chore: rebranding PDA (miroir de 418.extension/main)"
git push --force-with-lease
```

Le force-push est normal. Personne ne doit brancher depuis ce dépôt.

## La recette de marque

| Fichier | Changement |
|---|---|
| `PDA.tab/` (ex-`418.tab/`) | `git mv 418.tab PDA.tab` — nom de l'onglet du ruban : pyRevit le lit sur le **nom du dossier**, pas sur `title:` (`uimaker.py`, `_produce_ui_tab`) |
| `PDA.tab/Manage.panel/` | **supprimé** — l'outil Matériaux ne part pas chez PDA. Retirer aussi la ligne `- Manage` du `layout:` de `PDA.tab/bundle.yaml`, et l'entrée `Materiaux.pushbutton` de `BOUTONS` dans `lib/ui/tests/test_rail_window.py` |
| `PDA.tab/418.panel/bundle.yaml` | fichier à créer : `title: PDA` — les panels, eux, respectent `title:` |
| titres de fenêtres | `418 ·` → `PDA ·` : la propriété `Titre` des `MainViewModel.py` des 4 outils à rail, et le `TextBlock` de `PDA.tab/Export.panel/BatchExport.pushbutton/GUI/Views/MainWindow.xaml` |
| `lib/core/align.py` | titre des deux `TaskDialog.Show('418', …)` |
| `Infos.pushbutton/` | `AboutViewModel.py` + `tests/test_about_viewmodel.py` : nom `PDA.archi`. Le lien du dépôt reste volontairement sur `418.extension` : c'est là que vit le code. |
| `README.md` | **entièrement réécrit** : celui du miroir est un README de déploiement, pas une copie patchée de l'amont. À la resynchro, le reprendre tel quel du commit de marque précédent (`git checkout <ancien-commit> -- README.md`) et ignorer la version amont. |
| icônes | voir plus bas |
| `MIRROR.md` | ce fichier |

Le dossier d'installation doit s'appeler `PDA.extension` (minuscule) : pyRevit
compare le suffixe `.extension` littéralement.

## Icônes

Quatre fichiers portent la marque, tous dérivés du wordmark P&DA
(`…\AgencePDA - Documents\05_Logo PDA\pda-logo-picto-png.png`, 2044×750, noir
sur transparent) :

| Fichier | Taille | Encre |
|---|---|---|
| `lib/ui/GUI/resources/logo.png` | 512×512 | noire |
| `lib/ui/GUI/resources/logo.dark.png` | 512×512 | blanche |
| `PDA.tab/418.panel/Infos.pushbutton/icon.png` | 90×90 | noire |
| `PDA.tab/418.panel/Infos.pushbutton/icon.dark.png` | 90×90 | blanche |

Le wordmark est centré dans un carré transparent avec 8 % de marge. La variante
`.dark` est la même silhouette, encre forcée en blanc, alpha inchangé — c'est la
convention du dépôt : `.png` pour le thème clair, `.dark.png` pour le sombre.

À la resynchro ces quatre fichiers se recopient tels quels depuis le commit de
marque précédent (`git checkout <ancien-commit> -- lib/ui/GUI/resources/logo.png …`) :
rien à régénérer tant que le logo de l'agence ne change pas.
