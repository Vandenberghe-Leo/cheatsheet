# 🛠️ Mémo Linux : système, processus et disques

Référence rapide pour surveiller les processus, l'espace disque et l'état de la machine.

**Sources** : image « Linux Commands – Important » (@logic_launchpoint), `LINUXCMD.md`.
**Légende** : `*` = `[Complément hors document]`.

## ⚙️ Processus

| Commande | Rôle | Exemple |
| :--- | :--- | :--- |
| `ps` | Afficher les processus en cours | `ps` |
| `top` | Visualiseur de processus en temps réel | `top` |
| `htop` * | Version interactive de `top` | `htop` * |
| `kill <PID>` | Terminer un processus | `kill 1234` * |

## 💾 Disques

| Commande | Rôle | Exemple |
| :--- | :--- | :--- |
| `df -h` | Utilisation du disque (lisible) | `df -h` |
| `du -sh` | Taille d'un dossier | `du -sh ~/projects` * |
| `lsblk` | Lister les périphériques de stockage | `lsblk` |

## 🖥️ Informations système

| Commande | Rôle | Exemple |
| :--- | :--- | :--- |
| `whoami` | Utilisateur courant | `whoami` |
| `uname -a` | Informations système | `uname -a` |
| `hostname` | Nom du système | `hostname` |
| `uptime` | Durée de fonctionnement | `uptime` |
| `neofetch` * | Résumé visuel du système | `neofetch` * |
| `sudo reboot` | Redémarrer le système | `sudo reboot` |

> [!CAUTION]
> `sudo reboot` redémarre la machine : enregistrez votre travail avant. *

## ✅ Points à compléter

- `neofetch` figure dans `LINUXCMD.md` sans description : rôle ajouté à titre indicatif. *
- Voir aussi : [`linux-reseau-memo.md`](linux-reseau-memo.md).
