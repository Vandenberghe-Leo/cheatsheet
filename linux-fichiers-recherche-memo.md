# 🗂️ Mémo Linux : fichiers, recherche et archives

Référence rapide pour naviguer, manipuler, chercher, archiver et éditer des fichiers dans le terminal.

**Sources** : image « Linux Commands – Important » (@logic_launchpoint), `LINUXCMD.md`.
**Légende** : `*` = `[Complément hors document]` (absent des sources).

## 📖 Sommaire

- [Navigation et gestion](#-navigation-et-gestion)
- [Lecture](#-lecture)
- [Recherche](#-recherche)
- [Archives](#-archives)
- [Éditeurs](#-éditeurs)
- [Points à compléter](#-points-à-compléter)

---

## 📂 Navigation et gestion

| Commande | Rôle | Exemple |
| :--- | :--- | :--- |
| `pwd` | Afficher le répertoire courant | `pwd` |
| `ls` | Lister fichiers et dossiers | `ls` |
| `ls -la` | Lister tous les fichiers (détaillé) | `ls -la` |
| `cd` | Changer de répertoire | `cd ~/projects` |
| `cd ..` | Remonter au répertoire parent | `cd ..` * |
| `mkdir` | Créer un nouveau dossier | `mkdir src` |
| `touch` | Créer un nouveau fichier | `touch README.md` |
| `cp` | Copier fichiers ou dossiers | `cp a.txt b.txt` * |
| `mv` | Déplacer ou renommer | `mv ancien.txt nouveau.txt` * |
| `rm` | Supprimer fichiers ou dossiers | `rm fichier.txt` * |
| `clear` | Effacer l'écran du terminal | `clear` |

> [!WARNING]
> `rm` supprime sans passer par une corbeille : vérifiez la cible avant de valider. *

## 👀 Lecture

| Commande | Rôle | Exemple |
| :--- | :--- | :--- |
| `cat` | Afficher le contenu d'un fichier | `cat README.md` * |
| `head` * | Afficher le début d'un fichier | `head -n 5 fichier.txt` * |
| `tail` * | Afficher la fin d'un fichier | `tail -n 5 fichier.txt` * |

## 🔍 Recherche

| Commande | Rôle | Exemple |
| :--- | :--- | :--- |
| `find` | Chercher des fichiers ou dossiers | `find . -name "*.md"` * |
| `grep` | Chercher du texte dans des fichiers | `grep "mot" fichier.txt` * |
| `which` | Afficher le chemin complet d'une commande | `which python3` * |

## 📦 Archives

| Commande | Rôle | Exemple |
| :--- | :--- | :--- |
| `tar -cvf` | Créer une archive tar | `tar -cvf archive.tar dossier/` * |
| `tar -xvf` | Extraire une archive tar | `tar -xvf archive.tar` * |
| `zip` | Créer une archive zip | `zip archive.zip fichier.txt` * |
| `unzip` | Extraire une archive zip | `unzip archive.zip` * |

## ✏️ Éditeurs

| Commande | Rôle | Exemple |
| :--- | :--- | :--- |
| `nano` * | Éditeur de texte simple en terminal | `nano fichier.txt` * |
| `vi` / `vim` * | Éditeurs de texte en terminal (modal) | `vim fichier.txt` * |
| `code .` * | Ouvrir le dossier courant dans VS Code | `code .` * |

---

## ✅ Points à compléter

- Les options `c`, `x`, `v`, `f` de `tar` ne sont pas détaillées dans les sources. À titre indicatif : `c` créer, `x` extraire, `v` mode verbeux, `f` fichier d'archive. *
- Voir aussi : [`linux-permissions-memo.md`](linux-permissions-memo.md).
