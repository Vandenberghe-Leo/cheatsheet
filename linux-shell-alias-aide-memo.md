# 🐚 Mémo Linux : shell, alias et aide

Référence rapide pour l'aide en ligne, l'historique et la gestion des alias.

**Sources** : `LINUXCMD.md`, image « Linux Commands – Important » (@logic_launchpoint).
**Légende** : `*` = `[Complément hors document]`.

## ❓ Aide et historique

| Commande | Rôle | Exemple |
| :--- | :--- | :--- |
| `man` * | Afficher le manuel d'une commande | `man ls` * |
| `tldr` | Résumé simplifié d'une commande | `tldr mv` |
| `history` | Afficher l'historique des commandes | `history` |
| `echo` * | Afficher un texte | `echo "bonjour"` * |
| `date` * | Afficher la date et l'heure | `date` * |

> [!NOTE]
> `tldr` ne fonctionne pas chez moi. [À vérifier dans le document source]
> Piste : l'outil n'est peut-être pas installé. *

## 🔗 Alias

Un alias est un raccourci pour une commande.

```bash
alias gs='git status'     # créer l'alias gs
```

### Où sont stockés les alias

Dans le fichier `~/.bashrc` :

```bash
nano ~/.bashrc
```

### Afficher les alias

```bash
alias -p        # liste les alias avec leur définition *
compgen -a      # liste les noms d'alias
```

> [!IMPORTANT]
> Ta note indique que `compgen -a` « n'indique pas les commandes configurées pour les alias ». [À vérifier dans le document source]

## ✅ Points à compléter

- Recharger la configuration après modification de `~/.bashrc` : `source ~/.bashrc`. *
