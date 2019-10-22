---
id: companies
title: Companies
---

| ENDPOINT       |
| -------------- |
| GET /companies |

Permet de récupérer une liste de toutes les companies qui vous sont liées.

Il est nécessaire d'être [authentifié](authenticate).

## Filtres

Coming soon.

## Parametres

Doivent être envoyés avec un header : "Content-Type" = x-www-form-urlencoded

### Requis

#### _username *string*

Votre nom d'utilisateur enregistré sur le site de Jepilote, en général votre adresse email.

* * *

#### _password *string*

Votre mot de passe.

## Reponse

```json
{
    ...,
    "hydra:member": [
        {
            "@id": "/companies/143",
            "@type": "Companies",
            "companyId": 143,
            "companyName": "Nouvelle société test",
            "companyCode": "",
            "vat": "FR82 513890665",
            "address": "14 bd de la chapelle",
            "contactInfo": null,
            "address2": "",
            "city": "Paris",
            "zip": "75018",
            "country": "",
            "phoneNumber": "",
            "faxNumber": "",
            "webAddress": "",
            "email": "emailAddress@yahoo.fr",
            "facebook": "",
            "twitter": "",
            "created": "2012-10-15T00:00:00+02:00",
            "siret": "",
            "legalForm": "/legal_forms/2",
            "group": [],
            "user": [
                "/users/72"
            ],
            "siretNum": "",
            "vatDeclaration": 0
        },
        ...
    ],
    ...
}        
```
