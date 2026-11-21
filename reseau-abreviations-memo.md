# 🌐 Mémo : sigles et abréviations réseau

Glossaire de référence rapide des 30 sigles réseau courants, regroupés par thème.

**Sources** : image « Common Networking Abbreviations – Basic Networking Terms ».
**Légende** : `*` = `[Complément hors document]` (absent de la source).

## 📖 Sommaire

- [Adressage et identification](#-adressage-et-identification)
- [Portée et réseaux locaux](#-portée-et-réseaux-locaux)
- [Transport et web](#-transport-et-web)
- [Messagerie](#-messagerie)
- [Sécurité et qualité de service](#-sécurité-et-qualité-de-service)
- [Diagnostic et couche physique](#-diagnostic-et-couche-physique)
- [Routage et commutation](#-routage-et-commutation)
- [Supervision](#-supervision)
- [Comparatifs rapides](#-comparatifs-rapides)
- [Lien avec les commandes Linux](#-lien-avec-les-commandes-linux)
- [Points à compléter](#-points-à-compléter)

---

## 📍 Adressage et identification

| Sigle | Nom complet | Rôle |
| :--- | :--- | :--- |
| **IP** | Internet Protocol | Adresse unique pour les appareils d'un réseau |
| **MAC** | Media Access Control | Adresse matérielle unique d'un équipement réseau (ex. `00:1A:2B:3C:4D:5E`) |
| **DNS** | Domain Name System | Traduit les noms de domaine en adresses IP |
| **DHCP** | Dynamic Host Configuration Protocol | Attribue automatiquement des adresses IP aux appareils |
| **NAT** | Network Address Translation | Permet à plusieurs appareils de partager une seule IP |
| **ARP** | Address Resolution Protocol | Associe les adresses IP aux adresses MAC |

## 🏠 Portée et réseaux locaux

| Sigle | Nom complet | Rôle |
| :--- | :--- | :--- |
| **LAN** | Local Area Network | Réseau limité à une petite zone (maison, bureau) |
| **WAN** | Wide Area Network | Réseau couvrant de grandes zones géographiques |
| **VLAN** | Virtual Local Area Network | Crée plusieurs réseaux virtuels |
| **SSID** | Service Set Identifier | Nom d'un réseau Wi-Fi |

## 🔁 Transport et web

| Sigle | Nom complet | Rôle |
| :--- | :--- | :--- |
| **TCP** | Transmission Control Protocol | Garantit une livraison fiable des données |
| **UDP** | User Datagram Protocol | Protocole plus rapide, sans livraison garantie |
| **HTTP** | HyperText Transfer Protocol | Utilisé pour la communication web |
| **HTTPS** | HyperText Transfer Protocol Secure | Version sécurisée de HTTP |
| **FTP** | File Transfer Protocol | Transfère des fichiers sur un réseau |

## ✉️ Messagerie

| Sigle | Nom complet | Rôle |
| :--- | :--- | :--- |
| **SMTP** | Simple Mail Transfer Protocol | Envoie les messages e-mail |
| **POP3** | Post Office Protocol 3 | Récupère les e-mails vers un serveur local [À vérifier dans le document source] |
| **IMAP** | Internet Message Access Protocol | Accède aux e-mails sur le serveur |

## 🔒 Sécurité et qualité de service

| Sigle | Nom complet | Rôle |
| :--- | :--- | :--- |
| **VPN** | Virtual Private Network | Connexion chiffrée et sécurisée via Internet |
| **QoS** | Quality of Service | Priorise le trafic réseau |

## 🩺 Diagnostic et couche physique

| Sigle | Nom complet | Rôle |
| :--- | :--- | :--- |
| **ICMP** | Internet Control Message Protocol | Utilisé pour le diagnostic réseau (icône : `PING`) |
| **TTL** | Time To Live | Limite la durée de vie des paquets de données dans un réseau |
| **MTU** | Maximum Transmission Unit | Taille maximale d'un paquet réseau (valeur affichée : `1500`) |
| **PoE** | Power over Ethernet | Fournit alimentation et données via un seul câble |

## 🧭 Routage et commutation

| Sigle | Nom complet | Rôle |
| :--- | :--- | :--- |
| **BGP** | Border Gateway Protocol | Aiguille le trafic entre les réseaux sur Internet |
| **OSPF** | Open Shortest Path First | Protocole de routage interne (*interior gateway*) |
| **RIP** | Routing Information Protocol | Échange des informations de routes entre routeurs |
| **STP** | Spanning Tree Protocol | Évite les boucles dans les réseaux de commutateurs |

## 📡 Supervision

| Sigle | Nom complet | Rôle |
| :--- | :--- | :--- |
| **NTP** | Network Time Protocol | Synchronise l'heure entre les équipements réseau |
| **SNMP** | Simple Network Management Protocol | Surveille et gère les équipements réseau |

---

## ⚖️ Comparatifs rapides

| Paire | Différence |
| :--- | :--- |
| **TCP** vs **UDP** | TCP garantit la livraison ; UDP est plus rapide mais sans garantie |
| **HTTP** vs **HTTPS** | HTTPS est la version sécurisée de HTTP |
| **POP3** vs **IMAP** | POP3 récupère les e-mails ; IMAP y accède directement sur le serveur |
| **LAN** vs **WAN** | LAN : petite zone ; WAN : grandes zones géographiques |
| **IP** vs **MAC** | IP : adresse sur un réseau ; MAC : adresse matérielle de l'équipement. ARP fait le lien entre les deux |
| **OSPF** / **RIP** vs **BGP** | OSPF et RIP : routage au sein d'un réseau * ; BGP : entre réseaux sur Internet |

> [!NOTE]
> Les lignes marquées `*` sont des rapprochements déduits des définitions de l'image, pas des affirmations de la source.

## 🔗 Lien avec les commandes Linux

| Commande | Sigles associés |
| :--- | :--- |
| `ip a` | IP, MAC * |
| `ping` | ICMP, TTL * |
| `curl` | HTTP, HTTPS * |
| `ss -tuln` | TCP, UDP * |

Voir [`linux-reseau-memo.md`](linux-reseau-memo.md).

## ✅ Points à compléter

- **POP3** : l'image indique « vers un serveur local », formulation ambiguë (probablement l'appareil local). [À vérifier dans le document source]
- Numéros de ports usuels (HTTP, HTTPS, SMTP, etc.) : absents de la source. *
- Modèle OSI / TCP-IP et couche de chaque protocole : absents de la source. *
