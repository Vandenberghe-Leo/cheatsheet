# 🔐 Mémo Linux : permissions de fichiers

Référence rapide pour lire et modifier les droits d'accès et le propriétaire d'un fichier.

**Sources** : image « Linux Commands – Important » (@logic_launchpoint).
**Légende** : `*` = `[Complément hors document]`.

## 🧠 Notions clés

| Droit | Lettre | Valeur |
| :--- | :---: | :---: |
| Lecture | `r` | 4 |
| Écriture | `w` | 2 |
| Exécution | `x` | 1 |

Les droits sont définis pour trois populations : propriétaire (*owner*), groupe (*group*) et autres (*others*). *

## ⌨️ Commandes

| Commande | Rôle |
| :--- | :--- |
| `ls -l` | Afficher les permissions |
| `chmod` | Modifier les permissions |
| `chown` | Changer le propriétaire |

```bash
ls -l                      # voir les permissions
chmod 755 script.sh        # rwxr-xr-x
chown utilisateur fichier  # changer le propriétaire *
```

## 🧮 Exemple : `chmod 755 script.sh`

`755` correspond à `rwxr-xr-x` :

| Population | Chiffre | Droits |
| :--- | :---: | :--- |
| Propriétaire | 7 | accès complet (lecture, écriture, exécution) |
| Groupe | 5 | lecture et exécution |
| Autres | 5 | lecture et exécution |

Les chiffres s'obtiennent en additionnant les valeurs : 7 = 4 + 2 + 1, 5 = 4 + 1. *

> [!CAUTION]
> `chmod 777` donne tous les droits à tout le monde : à éviter. *

## ✅ Points à compléter

- Syntaxe symbolique de `chmod` (`u+x`, etc.) : absente des sources. *
