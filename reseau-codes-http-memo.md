# 📡 Mémo : codes de retour HTTP

Signification des codes de statut HTTP (1xx à 5xx) et manière de les lire avec `curl`.

**Sources** : aucun document fourni. Contenu rédigé à partir de connaissances générales : **l'ensemble du mémo est `[Complément hors document]`**.
**Référence officielle** : RFC 9110 (*HTTP Semantics*).

## 📖 Sommaire

- [Les 5 familles](#-les-5-familles)
- [1xx : information](#-1xx--information)
- [2xx : succès](#-2xx--succès)
- [3xx : redirection](#-3xx--redirection)
- [4xx : erreur client](#-4xx--erreur-client)
- [5xx : erreur serveur](#-5xx--erreur-serveur)
- [Distinctions fréquentes](#️-distinctions-fréquentes)
- [Lire un code avec curl](#-lire-un-code-avec-curl)
- [Points à compléter](#-points-à-compléter)

---

## 🧠 Les 5 familles

| Famille | Sens | Qui est concerné |
| :---: | :--- | :--- |
| **1xx** | Information : requête reçue, traitement en cours | Protocole |
| **2xx** | Succès | Tout va bien |
| **3xx** | Redirection : une autre action est nécessaire | Client |
| **4xx** | Erreur du **client** (requête incorrecte) | Client |
| **5xx** | Erreur du **serveur** | Serveur |

## ℹ️ 1xx : information

| Code | Nom | Sens |
| :---: | :--- | :--- |
| 100 | Continue | Le client peut envoyer le corps de la requête |
| 101 | Switching Protocols | Changement de protocole accepté (ex. WebSocket) |

## ✅ 2xx : succès

| Code | Nom | Sens |
| :---: | :--- | :--- |
| 200 | OK | Requête réussie |
| 201 | Created | Ressource créée (typiquement après un `POST`) |
| 202 | Accepted | Requête acceptée, traitement pas encore terminé |
| 204 | No Content | Réussi, sans contenu à renvoyer |

## ↪️ 3xx : redirection

| Code | Nom | Sens |
| :---: | :--- | :--- |
| 301 | Moved Permanently | Déplacée définitivement |
| 302 | Found | Déplacée temporairement |
| 304 | Not Modified | Inchangée : utiliser la version en cache |
| 307 | Temporary Redirect | Redirection temporaire, **méthode conservée** |
| 308 | Permanent Redirect | Redirection permanente, **méthode conservée** |

## ❌ 4xx : erreur client

| Code | Nom | Sens |
| :---: | :--- | :--- |
| 400 | Bad Request | Requête mal formée |
| 401 | Unauthorized | Authentification requise ou invalide |
| 403 | Forbidden | Authentifié, mais accès interdit |
| 404 | Not Found | Ressource introuvable |
| 405 | Method Not Allowed | Méthode non autorisée sur cette ressource |
| 408 | Request Timeout | Le client a mis trop de temps à envoyer la requête |
| 409 | Conflict | Conflit avec l'état actuel de la ressource |
| 410 | Gone | Ressource supprimée définitivement |
| 413 | Content Too Large | Corps de requête trop volumineux |
| 415 | Unsupported Media Type | Format de contenu non géré |
| 422 | Unprocessable Content | Requête bien formée mais invalide sur le fond |
| 429 | Too Many Requests | Trop de requêtes (limitation de débit) |

## 💥 5xx : erreur serveur

| Code | Nom | Sens |
| :---: | :--- | :--- |
| 500 | Internal Server Error | Erreur interne générique |
| 501 | Not Implemented | Fonction non prise en charge |
| 502 | Bad Gateway | Réponse invalide d'un serveur en amont |
| 503 | Service Unavailable | Service indisponible (surcharge, maintenance) |
| 504 | Gateway Timeout | Le serveur en amont n'a pas répondu à temps |

## ⚖️ Distinctions fréquentes

| Paire | Différence |
| :--- | :--- |
| **401** vs **403** | 401 : « qui êtes-vous ? » (pas ou mauvaise identification). 403 : « je sais qui vous êtes, mais non » |
| **301** vs **302** | 301 : permanent (les navigateurs et moteurs de recherche retiennent) ; 302 : temporaire |
| **302** vs **307** | 307 garantit que la méthode (`POST`…) est conservée |
| **400** vs **422** | 400 : syntaxe invalide ; 422 : syntaxe correcte mais données refusées |
| **502** vs **504** | 502 : réponse invalide en amont ; 504 : pas de réponse à temps |
| **500** vs **503** | 500 : bug ou panne ; 503 : indisponibilité volontaire ou surcharge |

## 🔎 Lire un code avec curl

```bash
curl -i https://example.com                         # en-têtes + corps
curl -I https://example.com                         # en-têtes seulement (requête HEAD)
curl -s -o /dev/null -w "%{http_code}\n" https://example.com   # seulement le code
curl -L https://example.com                         # suivre les redirections
curl -v https://example.com                         # détail complet de l'échange
```

> [!TIP]
> Pour déboguer une redirection, comparez `curl -I` (sans `-L`) et `curl -IL` : le premier montre le 3xx, le second la chaîne complète.

## ✅ Points à compléter

- Liste complète des codes : voir la RFC 9110 et le registre IANA « HTTP Status Code Registry ».
- Codes non standards (ex. spécifiques à un serveur ou un CDN) : non traités.
- Voir aussi : [`linux-reseau-memo.md`](linux-reseau-memo.md) (`curl`), [`reseau-abreviations-memo.md`](reseau-abreviations-memo.md) (HTTP, HTTPS).
