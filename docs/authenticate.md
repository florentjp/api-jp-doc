---
id: authenticate
title: Authentification
---

| ENDPOINT         |
| ---------------- |
| GET /login_check |

Permet de s'authentifier en recevant un *token* à utiliser pour accèder aux fonctionnalités de l'API.

Le token est à rajouter dans le header de requête: "Authorization" = bearer *token*

## Parametres

Doivent être envoyés avec un header : "Content-Type" = x-www-form-urlencoded

### Requis

#### _username *string*

Votre nom d'utilisateur enregistré sur le site de Jepilote, en général votre adresse email.

* * *

#### _password *string*

Votre mot de passe.

## Reponse

Si vos identifiants de connection sont correctes :

```json
{
  "token": "VotreToken"
}
```

Sinon, une erreur http 401 est retournée.
