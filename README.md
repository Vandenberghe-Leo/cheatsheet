<div align="center">

# 📚 Cheatsheet

**Mémos techniques rapides, classés par thème : terminal Linux, réseau et plus à venir.**

[![Licence](https://img.shields.io/github/license/Vandenberghe-Leo/cheatsheet?style=flat-square)](LICENSE)
[![Mémos](https://img.shields.io/badge/mémos-10-blue?style=flat-square)](#-index-des-mémos)
[![Issues](https://img.shields.io/github/issues/Vandenberghe-Leo/cheatsheet?style=flat-square)](https://github.com/Vandenberghe-Leo/cheatsheet/issues)

</div>

---

## 📖 Sommaire

- [Aperçu](#-aperçu)
- [Index des mémos](#-index-des-mémos)
- [Conventions](#-conventions)
- [Ajouter un mémo](#-ajouter-un-mémo)
- [Structure du dépôt](#-structure-du-dépôt)
- [Roadmap](#️-roadmap)
- [Contribution](#-contribution)
- [Auteur et licence](#-auteur-et-licence)

---

## 🧐 Aperçu

Ce dépôt rassemble des fiches mémo courtes et scannables, construites à partir de documents sources (cours, schémas, notes personnelles). Chaque fiche est un fichier Markdown indépendant, pensé pour être lu directement sur GitHub.

> [!NOTE]
> Les mémos sont fidèles à leurs sources. Tout ce qui est ajouté en plus est marqué `*` ou `[Complément hors document]`, et les points douteux `[À vérifier dans le document source]`.

---

## 🗂️ Index des mémos

### 🐧 Linux

| Mémo | Contenu | Statut |
| :--- | :--- | :---: |
| [`linux-fichiers-recherche-memo.md`](cheatsheets/linux-fichiers-recherche-memo.md) | Navigation, gestion, lecture, recherche, archives, éditeurs | ✅ |
| [`linux-permissions-memo.md`](cheatsheets/linux-permissions-memo.md) | `chmod`, `chown`, valeurs r/w/x, exemple `755` | ✅ |
| [`linux-systeme-processus-memo.md`](cheatsheets/linux-systeme-processus-memo.md) | Processus, disques, informations système | ✅ |
| [`linux-reseau-memo.md`](cheatsheets/linux-reseau-memo.md) | `ip`, `ping`, `curl`, `ss`, `wget` | ✅ |
| [`linux-shell-alias-aide-memo.md`](cheatsheets/linux-shell-alias-aide-memo.md) | Aide, historique, alias, `~/.bashrc` | ✅ |

### 🌐 Réseau

| Mémo | Contenu | Statut |
| :--- | :--- | :---: |
| [`reseau-abreviations-memo.md`](cheatsheets/reseau-abreviations-memo.md) | Glossaire de 30 sigles réseau, par thème | ✅ |
| [`reseau-ports-memo.md`](cheatsheets/reseau-ports-memo.md) | Numéros de ports usuels par usage | ✅ |
| [`reseau-codes-http-memo.md`](cheatsheets/reseau-codes-http-memo.md) | Codes de retour HTTP 1xx à 5xx | ✅ |
| [`reseau-ssh-memo.md`](cheatsheets/reseau-ssh-memo.md) | SSH : clés, config, tunnels, erreurs | ✅ |
| [`reseau-scp-memo.md`](cheatsheets/reseau-scp-memo.md) | SCP : syntaxe complète et pièges | ✅ |
| `reseau-nmap-memo.md` | Scans de ports et de services | 🚧 |

### ➕ À venir

| Thème | Mémo prévu | Statut |
| :--- | :--- | :---: |
| [À COMPLÉTER : ex. Git] | [À COMPLÉTER : `git-commandes-memo.md`] | 🚧 |

**Légende des statuts** : ✅ prêt · 🚧 en cours · 💡 idée

---

## 📐 Conventions

| Règle | Détail |
| :--- | :--- |
| **Nommage** | `kebab-case`, sans accents ni espaces, suffixe `-memo.md` (`theme-sujet-memo.md`) |
| **Dossier** | Tous les mémos dans `cheatsheets/` |
| **Préfixe de thème** | Le thème en premier (`linux-`, `reseau-`, `git-`…) pour regrouper les fichiers dans l'explorateur |
| **Sources** | Chaque mémo cite ses sources en en-tête |
| **Compléments** | `*` ou `[Complément hors document]` pour ce qui n'est pas dans les sources |
| **Doutes** | `[À vérifier dans le document source]` plutôt que deviner |
| **Sommaire** | Obligatoire au-delà de ~100 lignes |
| **Blocs de code** | Langage toujours indiqué (`bash`, `json`, `text`…) |

### Alertes GitHub utilisables

Seules ces cinq alertes sont valides (`INFO`, `SUCCESS`, `BUG`, etc. ne s'affichent pas) :

> [!NOTE]
> Information utile, même en lecture rapide.

> [!TIP]
> Conseil pour mieux faire.

> [!IMPORTANT]
> Information indispensable pour réussir.

> [!WARNING]
> Risque potentiel : à lire avant d'agir.

> [!CAUTION]
> Danger : conséquences négatives graves possibles.

---

## ➕ Ajouter un mémo

1. Créer `cheatsheets/<theme>-<sujet>-memo.md` à partir du squelette ci-dessous.
2. Ajouter une ligne dans le tableau du thème de l'[index](#-index-des-mémos) (ou créer une section si le thème est nouveau).
3. Mettre à jour le badge « mémos » en haut de ce fichier.
4. Ajouter des liens croisés vers les mémos voisins (ex. `ping` ↔ ICMP).

<details>
<summary><b>📋 Squelette d'un mémo</b></summary>

````markdown
# 🔧 Mémo : [À COMPLÉTER : sujet]

[À COMPLÉTER : objectif de la fiche en 1 à 2 phrases.]

**Sources** : [À COMPLÉTER : documents utilisés].
**Légende** : `*` = `[Complément hors document]`.

## 📖 Sommaire

*(si le mémo dépasse ~100 lignes)*

## 🧠 Notions clés

| Terme | Définition |
| :--- | :--- |
| [À COMPLÉTER] | [À COMPLÉTER] |

## ⌨️ Commandes / Syntaxe

| Commande | Rôle | Exemple |
| :--- | :--- | :--- |
| `[commande]` | [rôle] | `[exemple]` |

## ⚖️ Bonnes pratiques et pièges

> [!WARNING]
> [À COMPLÉTER : piège fréquent.]

## ✅ Points à compléter

- [À COMPLÉTER : éléments à vérifier dans les sources.]
````

</details>

---

## 📁 Structure du dépôt

````text
.
├── cheatsheets/
│   ├── linux-fichiers-recherche-memo.md
│   ├── linux-permissions-memo.md
│   ├── linux-systeme-processus-memo.md
│   ├── linux-reseau-memo.md
│   ├── linux-shell-alias-aide-memo.md
│   └── reseau-abreviations-memo.md
├── templates/
│   └── readme-template.md       # template de README de projet
├── LICENSE
└── README.md                    # ce fichier (index)
````

---

## 🗺️ Roadmap

- [x] Mémos Linux (fichiers, permissions, système, réseau, shell)
- [x] Glossaire des sigles réseau
- [ ] [À COMPLÉTER : prochain thème]
- [ ] Supprimer l'ancien `LINUXCMD.md` et l'ancien `TEMPLATE.md` (remplacés)
- [ ] [À COMPLÉTER : vérifier les points `[À vérifier dans le document source]`]

---

## 🤝 Contribution

Les suggestions et corrections sont les bienvenues.

1. **Forkez** le projet.
2. Créez votre branche (`git checkout -b memo/nom-du-sujet`).
3. **Committez** (`git commit -m "docs: ajoute le mémo nom-du-sujet"`).
4. **Poussez** la branche (`git push origin memo/nom-du-sujet`).
5. Ouvrez une **Pull Request**.

---

## 👤 Auteur et licence

Créé par [Léo Vandenberghe](https://github.com/PhantomSKZT)

Distribué sous licence **MIT**. Voir le fichier [`LICENSE`](LICENSE).
