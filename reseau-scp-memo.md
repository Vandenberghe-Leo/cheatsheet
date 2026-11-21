# 📤 Mémo : SCP

Copier des fichiers et dossiers entre machines via SSH : syntaxe complète, options, cas d'usage et pièges.

**Sources** : aucun document fourni. Contenu rédigé à partir de connaissances générales : **l'ensemble du mémo est `[Complément hors document]`**.
**Référence officielle** : `man scp`.

## 📖 Sommaire

- [Syntaxe](#-syntaxe)
- [Cas d'usage](#-cas-dusage)
- [Options courantes](#️-options-courantes)
- [Avec le fichier `~/.ssh/config`](#-avec-le-fichier-sshconfig)
- [Pièges fréquents](#️-pièges-fréquents)
- [Alternatives](#-alternatives)
- [Points à compléter](#-points-à-compléter)

---

## 🧩 Syntaxe

```text
scp [options] <source> <destination>
```

Une cible distante s'écrit `utilisateur@hôte:chemin`. Sans chemin après le `:`, la destination est le dossier personnel distant.

| Forme | Sens |
| :--- | :--- |
| `fichier.txt` | Chemin **local** |
| `user@hôte:/chemin/fichier.txt` | Chemin **distant** (absolu) |
| `user@hôte:dossier/` | Chemin distant relatif au dossier personnel |
| `user@hôte:` | Dossier personnel distant |

## 🚚 Cas d'usage

```bash
# Local -> distant
scp fichier.txt user@hôte:/tmp/

# Distant -> local (le point = dossier courant)
scp user@hôte:/var/log/app.log .

# Dossier entier (récursif)
scp -r mon-dossier/ user@hôte:/home/user/

# Plusieurs fichiers
scp a.txt b.txt user@hôte:/tmp/

# Port personnalisé (P majuscule !)
scp -P 2222 fichier.txt user@hôte:/tmp/

# Clé précise
scp -i ~/.ssh/ma_cle fichier.txt user@hôte:/tmp/

# Plusieurs fichiers distants avec joker (guillemets obligatoires)
scp 'user@hôte:/var/log/*.log' ./logs/

# Distant -> distant (transite par votre machine avec -3)
scp -3 user1@hôte1:/tmp/f.txt user2@hôte2:/tmp/

# Via un hôte de rebond
scp -J admin@bastion user@10.0.0.5:/tmp/f.txt .

# Adresse IPv6 (crochets obligatoires)
scp fichier.txt user@[2001:db8::1]:/tmp/
```

## 🎛️ Options courantes

| Option | Rôle |
| :--- | :--- |
| `-r` | Copie récursive (dossiers) |
| `-P <port>` | Port SSH (**majuscule**) |
| `-i <clé>` | Fichier de clé privée |
| `-p` | Conserve dates et droits des fichiers |
| `-C` | Active la compression |
| `-l <kbit/s>` | Limite la bande passante |
| `-v` | Mode verbeux (diagnostic) |
| `-q` | Mode silencieux (sans barre de progression) |
| `-J <hôte>` | Hôte de rebond |
| `-3` | Copie distant -> distant via la machine locale |
| `-o <option>=<valeur>` | Option SSH ponctuelle |

> [!NOTE]
> **`scp -P`** (majuscule) vs **`ssh -p`** (minuscule) : source d'erreur classique. Voir [`reseau-ssh-memo.md`](reseau-ssh-memo.md).

## 🗒️ Avec le fichier `~/.ssh/config`

Les alias définis dans `~/.ssh/config` fonctionnent aussi avec `scp` (port, clé et utilisateur sont repris) :

```bash
scp fichier.txt prod:/tmp/       # prod = Host défini dans ~/.ssh/config
```

## ⚠️ Pièges fréquents

| Piège | Explication |
| :--- | :--- |
| **Écrasement silencieux** | Un fichier de même nom à destination est remplacé sans confirmation |
| **Jokers distants** | Sans guillemets, c'est votre shell local qui interprète `*` |
| **`:` dans un nom local** | `scp a:b.txt …` est lu comme un hôte `a` ; préfixer par `./` : `./a:b.txt` |
| **Dossier sans `-r`** | La copie échoue : `-r` est obligatoire |
| **Droits insuffisants** | Écrire dans `/etc` ou `/var` exige un compte autorisé sur le serveur |

> [!WARNING]
> `scp` écrase sans prévenir. Pour de grosses ou fréquentes synchronisations, préférez `rsync`.

## 🔄 Alternatives

| Outil | Intérêt | Exemple |
| :--- | :--- | :--- |
| `sftp` | Session interactive de transfert | `sftp user@hôte` |
| `rsync` | Ne transfère que les différences, reprise possible | `rsync -avz -e ssh dossier/ user@hôte:/chemin/` |

> [!NOTE]
> Le protocole SCP historique est considéré comme vieillissant par le projet OpenSSH. Les versions récentes de la commande `scp` utilisent le protocole SFTP en interne, mais la syntaxe reste la même.

## ✅ Points à compléter

- Comportement exact de `scp` selon la version d'OpenSSH installée : [À vérifier dans le document source] (`man scp`).
- Voir aussi : [`reseau-ssh-memo.md`](reseau-ssh-memo.md), [`reseau-ports-memo.md`](reseau-ports-memo.md), [`linux-fichiers-recherche-memo.md`](linux-fichiers-recherche-memo.md).
