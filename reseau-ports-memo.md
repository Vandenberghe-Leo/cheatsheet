# 🔌 Mémo : numéros de ports usuels

Table de référence des ports réseau les plus courants, regroupés par usage.

**Sources** : aucun document fourni. Contenu rédigé à partir de connaissances générales : **l'ensemble du mémo est `[Complément hors document]`**.
**Référence officielle** : registre IANA « Service Name and Transport Protocol Port Number Registry ».

## 📖 Sommaire

- [Notions clés](#-notions-clés)
- [Accès distant et transfert](#-accès-distant-et-transfert)
- [Web](#-web)
- [Messagerie](#-messagerie)
- [Infrastructure réseau](#-infrastructure-réseau)
- [Bases de données](#-bases-de-données)
- [Ports de développement](#-ports-de-développement)
- [Vérifier un port](#-vérifier-un-port)
- [Points à compléter](#-points-à-compléter)

---

## 🧠 Notions clés

| Plage | Nom | Usage |
| :--- | :--- | :--- |
| 0 – 1023 | Ports « bien connus » (*well-known*) | Services standards (SSH, HTTP…), privilégiés sous Linux |
| 1024 – 49151 | Ports enregistrés | Applications et services (bases de données…) |
| 49152 – 65535 | Ports dynamiques / éphémères | Attribués temporairement côté client |

Un port se combine toujours avec un protocole de transport : **TCP** (fiable) ou **UDP** (rapide, sans garantie). Voir [`reseau-abreviations-memo.md`](reseau-abreviations-memo.md).

## 🔐 Accès distant et transfert

| Port | Protocole | Transport | Rôle |
| ---: | :--- | :---: | :--- |
| 20 / 21 | FTP | TCP | Transfert de fichiers (20 : données, 21 : contrôle) |
| 22 | SSH / SFTP / SCP | TCP | Accès distant sécurisé et transfert chiffré |
| 23 | Telnet | TCP | Accès distant **non chiffré** (obsolète) |
| 3389 | RDP | TCP | Bureau à distance Windows |

> [!CAUTION]
> Telnet (23) et FTP (21) font circuler identifiants et données en clair : préférez SSH, SFTP ou SCP.

## 🌍 Web

| Port | Protocole | Transport | Rôle |
| ---: | :--- | :---: | :--- |
| 80 | HTTP | TCP | Web non chiffré |
| 443 | HTTPS | TCP | Web chiffré (TLS) |
| 8080 | HTTP alternatif | TCP | Serveurs de test, proxys |
| 8443 | HTTPS alternatif | TCP | Serveurs de test |

## ✉️ Messagerie

| Port | Protocole | Transport | Rôle |
| ---: | :--- | :---: | :--- |
| 25 | SMTP | TCP | Échange de mails entre serveurs |
| 587 | SMTP (soumission) | TCP | Envoi de mail par un client (STARTTLS) |
| 465 | SMTPS | TCP | SMTP sur TLS implicite |
| 110 | POP3 | TCP | Récupération de mails |
| 995 | POP3S | TCP | POP3 sur TLS |
| 143 | IMAP | TCP | Accès aux mails sur le serveur |
| 993 | IMAPS | TCP | IMAP sur TLS |

## 🧭 Infrastructure réseau

| Port | Protocole | Transport | Rôle |
| ---: | :--- | :---: | :--- |
| 53 | DNS | UDP / TCP | Résolution de noms (TCP pour les grosses réponses) |
| 67 / 68 | DHCP | UDP | Attribution d'adresses IP (67 : serveur, 68 : client) |
| 123 | NTP | UDP | Synchronisation de l'heure |
| 161 / 162 | SNMP | UDP | Supervision (162 : alertes / *traps*) |
| 179 | BGP | TCP | Routage entre réseaux |
| 520 | RIP | UDP | Routage interne |
| 389 | LDAP | TCP | Annuaire |
| 445 | SMB | TCP | Partage de fichiers Windows |

> [!NOTE]
> **ICMP** (`ping`) et **OSPF** n'utilisent pas de port : ce sont des protocoles IP à part entière (OSPF : protocole IP n° 89).

## 🗄️ Bases de données

| Port | Service | Transport |
| ---: | :--- | :---: |
| 3306 | MySQL / MariaDB | TCP |
| 5432 | PostgreSQL | TCP |
| 6379 | Redis | TCP |
| 27017 | MongoDB | TCP |

> [!WARNING]
> Ne jamais exposer ces ports directement sur Internet : limitez l'accès au réseau interne ou passez par un tunnel SSH.

## 🧪 Ports de développement

| Port | Usage courant |
| ---: | :--- |
| 3000 | Serveurs de dev (Node, React…) |
| 5000 | Serveurs de dev (Flask…) |
| 8000 | Serveurs de dev (Django, `python -m http.server`) |
| 2375 / 2376 | API Docker (2375 : non chiffrée, 2376 : TLS) |

> [!CAUTION]
> L'API Docker sur le port 2375 donne un contrôle total de la machine : ne l'exposez jamais.

## 🔎 Vérifier un port

```bash
ss -tuln                     # ports en écoute sur la machine locale
nc -zv 192.168.1.10 22       # tester si un port est ouvert sur une machine distante
nmap -p 22,80,443 <hôte>     # scanner quelques ports (voir reseau-nmap-memo.md)
grep -w ssh /etc/services    # retrouver le numéro d'un service
```

## ✅ Points à compléter

- Vérifier chaque numéro dans le registre IANA ou `/etc/services`.
- Ports spécifiques à Windows, VoIP et jeux : non traités.
- Voir aussi : [`linux-reseau-memo.md`](linux-reseau-memo.md), [`reseau-ssh-memo.md`](reseau-ssh-memo.md).
