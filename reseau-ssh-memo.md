# 🔐 Mémo : SSH

Connexion distante sécurisée : syntaxe, clés, configuration, tunnels, durcissement et erreurs courantes.

**Sources** : aucun document fourni. Contenu rédigé à partir de connaissances générales : **l'ensemble du mémo est `[Complément hors document]`**.
**Référence officielle** : `man ssh`, `man ssh_config`, `man sshd_config`, documentation OpenSSH.

## 📖 Sommaire

- [Notions clés](#-notions-clés)
- [Connexion](#-connexion)
- [Options courantes](#️-options-courantes)
- [Clés SSH](#-clés-ssh)
- [Fichier de configuration client](#-fichier-de-configuration-client)
- [Tunnels et rebonds](#-tunnels-et-rebonds)
- [Configuration du serveur](#️-configuration-du-serveur)
- [Fichiers et permissions](#-fichiers-et-permissions)
- [Erreurs courantes](#-erreurs-courantes)
- [Points à compléter](#-points-à-compléter)

---

## 🧠 Notions clés

| Terme | Définition |
| :--- | :--- |
| **SSH** | Secure Shell : accès distant chiffré, port **22** par défaut |
| **Clé privée** | Reste sur votre machine, ne se partage jamais |
| **Clé publique** | Se copie sur le serveur (`authorized_keys`) |
| **`known_hosts`** | Empreintes des serveurs déjà rencontrés (protège contre l'usurpation) |
| **`sshd`** | Le service serveur SSH |

## ⌨️ Connexion

```bash
ssh utilisateur@hôte                      # connexion de base
ssh -p 2222 utilisateur@hôte              # port personnalisé (p minuscule)
ssh -i ~/.ssh/ma_cle utilisateur@hôte     # clé précise
ssh utilisateur@hôte 'uptime'             # exécuter une commande puis quitter
ssh utilisateur@hôte 'sudo systemctl status nginx'
exit                                      # quitter (ou Ctrl+D)
```

> [!TIP]
> Session figée ? Tapez `Entrée`, puis `~` puis `.` pour fermer la connexion.

## 🎛️ Options courantes

| Option | Rôle |
| :--- | :--- |
| `-p <port>` | Port du serveur |
| `-i <clé>` | Fichier de clé privée |
| `-v` / `-vv` / `-vvv` | Mode verbeux (diagnostic) |
| `-L <local>:<hôte>:<port>` | Redirection de port locale |
| `-R <distant>:<hôte>:<port>` | Redirection de port distante |
| `-D <port>` | Proxy SOCKS dynamique |
| `-N` | Pas de commande distante (tunnel seul) |
| `-f` | Passer en arrière-plan |
| `-J <hôte>` | Passer par un hôte de rebond |
| `-A` | Transférer l'agent SSH (à utiliser avec prudence) |
| `-X` | Transférer l'affichage graphique (X11) |
| `-o <option>=<valeur>` | Option de configuration ponctuelle |
| `-q` | Mode silencieux |

> [!NOTE]
> Attention : `ssh` utilise **`-p`** (minuscule) pour le port, alors que `scp` utilise **`-P`** (majuscule). Voir [`reseau-scp-memo.md`](reseau-scp-memo.md).

## 🔑 Clés SSH

```bash
ssh-keygen -t ed25519 -C "mon-email@exemple.fr"        # créer une paire de clés
ssh-copy-id -i ~/.ssh/id_ed25519.pub utilisateur@hôte  # installer la clé publique sur le serveur
eval "$(ssh-agent -s)"                                 # démarrer l'agent
ssh-add ~/.ssh/id_ed25519                              # charger la clé dans l'agent
ssh-add -l                                             # lister les clés chargées
ssh-keygen -R hôte                                     # oublier l'empreinte d'un hôte
```

| Fichier | Contenu |
| :--- | :--- |
| `~/.ssh/id_ed25519` | Clé **privée** |
| `~/.ssh/id_ed25519.pub` | Clé **publique** |

> [!IMPORTANT]
> Protégez votre clé privée par une **passphrase** lors de `ssh-keygen`.

## 🗒️ Fichier de configuration client

Fichier `~/.ssh/config` : évite de retaper les options.

```text
Host prod
    HostName 203.0.113.10
    User deploy
    Port 2222
    IdentityFile ~/.ssh/id_ed25519

Host bastion
    HostName bastion.exemple.fr
    User admin

Host interne
    HostName 10.0.0.5
    User admin
    ProxyJump bastion
```

```bash
ssh prod         # équivaut à ssh -p 2222 -i ~/.ssh/id_ed25519 deploy@203.0.113.10
ssh interne      # passe automatiquement par le bastion
```

## 🚇 Tunnels et rebonds

```bash
# Accéder à un service distant (ex. base de données) depuis sa machine
ssh -L 5433:localhost:5432 utilisateur@hôte -N
# puis : psql -h localhost -p 5433

# Exposer un service local sur le serveur distant
ssh -R 8080:localhost:3000 utilisateur@hôte -N

# Proxy SOCKS (navigation via le serveur)
ssh -D 1080 utilisateur@hôte -N

# Rebond via un bastion
ssh -J admin@bastion.exemple.fr utilisateur@10.0.0.5
```

## 🛡️ Configuration du serveur

Fichier `/etc/ssh/sshd_config` (côté serveur, droits `sudo` requis) :

| Directive | Valeur recommandée | Effet |
| :--- | :---: | :--- |
| `PasswordAuthentication` | `no` | Interdit les mots de passe (clés uniquement) |
| `PermitRootLogin` | `no` | Interdit la connexion directe en `root` |
| `PubkeyAuthentication` | `yes` | Autorise les clés |
| `Port` | personnalisé | Réduit le bruit des scans automatiques |
| `AllowUsers` | liste | Restreint les comptes autorisés |

```bash
sudo sshd -t                       # vérifier la syntaxe avant de recharger
sudo systemctl restart ssh         # Debian / Ubuntu (le service s'appelle sshd sur d'autres distributions)
```

> [!WARNING]
> Avant de désactiver les mots de passe, vérifiez que votre clé fonctionne **dans une seconde session ouverte**, sinon vous risquez de vous verrouiller dehors.

## 📏 Fichiers et permissions

| Fichier / dossier | Droits | Commande |
| :--- | :---: | :--- |
| `~/.ssh/` | `700` | `chmod 700 ~/.ssh` |
| Clé privée | `600` | `chmod 600 ~/.ssh/id_ed25519` |
| `~/.ssh/authorized_keys` | `600` | `chmod 600 ~/.ssh/authorized_keys` |
| `~/.ssh/config` | `600` | `chmod 600 ~/.ssh/config` |

Voir [`linux-permissions-memo.md`](linux-permissions-memo.md).

## 🩹 Erreurs courantes

| Message | Cause probable | Piste |
| :--- | :--- | :--- |
| `Connection refused` | Service arrêté, mauvais port ou pare-feu | Vérifier `ss -tuln`, le port et `sshd` |
| `Connection timed out` | Pare-feu ou réseau injoignable | Tester `ping`, `nc -zv hôte 22` |
| `Permission denied (publickey)` | Clé non installée ou mauvais utilisateur | `ssh -v`, vérifier `authorized_keys` |
| `UNPROTECTED PRIVATE KEY FILE` | Droits trop larges sur la clé | `chmod 600` sur la clé |
| `Host key verification failed` / `REMOTE HOST IDENTIFICATION HAS CHANGED` | Empreinte différente (serveur réinstallé, ou usurpation) | Vérifier d'abord la légitimité, puis `ssh-keygen -R hôte` |
| `Too many authentication failures` | Trop de clés tentées par l'agent | `ssh -o IdentitiesOnly=yes -i <clé> ...` |

> [!CAUTION]
> Ne supprimez jamais une empreinte (`ssh-keygen -R`) sans comprendre pourquoi elle a changé : c'est la protection contre les attaques de l'homme du milieu.

## ✅ Points à compléter

- Nom du service (`ssh` ou `sshd`) selon la distribution : à vérifier sur votre système.
- `ssh-agent` et gestion des clés sous Windows et macOS : non traités.
- Voir aussi : [`reseau-scp-memo.md`](reseau-scp-memo.md), [`reseau-ports-memo.md`](reseau-ports-memo.md).
