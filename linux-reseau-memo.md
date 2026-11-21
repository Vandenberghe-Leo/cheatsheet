# 🌐 Mémo Linux : commandes réseau

Référence rapide pour diagnostiquer la connectivité, interroger un service et télécharger.

**Sources** : image « Linux Commands – Important » (@logic_launchpoint), `LINUXCMD.md`.
**Légende** : `*` = `[Complément hors document]`.

## ⌨️ Commandes

| Commande | Rôle | Exemple |
| :--- | :--- | :--- |
| `ip a` | Afficher les informations d'adresses IP | `ip a` |
| `ping <host>` | Vérifier la connectivité | `ping 8.8.8.8` * |
| `curl <URL>` | Envoyer une requête HTTP | `curl https://example.com` * |
| `ss -tuln` | Afficher les ports en écoute | `ss -tuln` |
| `wget` * | Télécharger un fichier | `wget https://example.com/fichier.zip` * |

## 🧩 Lien avec les sigles réseau

| Commande | Sigle associé |
| :--- | :--- |
| `ip a` | IP, MAC * |
| `ping` | ICMP * |
| `curl` | HTTP / HTTPS * |
| `ss -tuln` | TCP, UDP * |

Voir [`reseau-abreviations-memo.md`](reseau-abreviations-memo.md) (à venir).

## ✅ Points à compléter

- Signification des options `-t`, `-u`, `-l`, `-n` de `ss` : absente des sources. [À vérifier dans le document source]
