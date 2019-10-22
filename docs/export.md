---
id: export
title: Export document
---

| ENDPOINT               |
| ---------------------- |
| POST /export_documents |

Permet de faire un export des documents concernés dans un fichier du format choisi.

Il est nécessaire d'être [authentifié](authenticate).

## Parametres

```json
{
	"companyId": 71,
	"format": "ACD",
	"emailAddress": "megigayil@appmail24.com",
	"alreadyExported": 1,
	"flagAsExported": 0,
	"dateDebut": "2013-10-01",
	"dateFin": "2019-10-01"
}
```

### Requis

#### companyId *int*

Identifiant de la société dont vous voulez récupérer un export.

Vous pouvez récupérer la liste de vos sociétés (et leurs identifiants) avec [GET /companies](companies)

* * *

#### format *string*

Vous avez le choix d'utiliser les valeurs "FEC" ou "ACD" pour respectivement faire un export dans un fichier '.fec' ou dans un fichier '.in'.

Notez que si vous demandez un export "ACD", une archive contenant votre fichier '.in' ainsi que la liste des documents comptables concernés sera créée. 

### Optionnels

#### emailAddress *string (email)*

Une adresse email valide, si elle est présente, un email contenant un lien de téléchargement vers le document d'export généré.

* * *

#### alreadyExported *int* (*bool*)

Si la valeur est à 1, l'export sera effectué avec les documents qui ont déjà été exporté précédement.

Si elle est à 0, seuls les documents qui n'ont pas encore été exporté seront concernés.

Sera par défaut égale à 0 (false).

* * *

#### flagAsExported *int* (*bool*)

Si la valeur est à 1, les documents concernés par l'export seront enregistrés comme déjà exporté.

Par conséquent, il n'apparaitront plus pour les prochains appels vers cette requête avec 'alreadyExported' égal à 0.

Sera par défaut égale à 0 (false).

* * *

#### dateDebut *date*

Permet de choisir vos documents à exporter par rapport à leur date de création.

Ne seront donc concernés que les documents créés après cette date.

Sera par défaut égal à la date de création de votre premier document.

* * *

#### dateFin *date*

Permet de choisir vos documents à exporter par rapport à leur date de création.

Ne seront donc concernés que les documents créés avant cette date.

Sera par défaut égal à la date d'aujourd'hui.

## Reponse

Exemple

```json
{
    "success": true,
    "message": "export ACD effectué",
    "error": null,
    "file": {
        "name": "tsuidyk",
        "url": "https://app.jepilote.com/download/show/hash/26b13e1c520b78fb72e9c9d2c3509cf4d046cb8468556fec876902ecde19ce14e3325f1891b684cfc86d4d48db3f158fd2fe",
        "api_url": "http://apiv2.jepilote.com/get_export/26b13e1c520b78fb72e9c9d2c3509cf4d046cb8468556fec876902ecde19ce14e3325f1891b684cfc86d4d48db3f158fd2fe"
    }
}
```

* * *

#### success *bool*

True si le fichier/dossier d'export à été généré, sinon false

* * *

#### message *string*

Un message expliquant le résultat de la requète

* * *

#### error *string[]*

Liste de message(s) d'erreur ayant survenue lors de l'export

(ex: Un fichier .pdf lié à un document de l'export n'a pas été trouvé)

* * *

#### file *array*

Information sur le fichier/dossier d'export généré

* * *

#### file.name *string*

Correspond au nom du document créé.

Dans le cas d'un export ACD, le document créé est un .zip dont on a retiré l'extension.

#### file.url *string (url)*

Correspond à la page sur le site de Jepilote où vous pouvez télécharger le document généré.

Il est nécessaire d'avoir une session en cours sur le site pour pouvoir accèder au lien.

Cette url sera envoyé par email si vous en avez fourni un dans les paramètres de la requête, voir : [emailAddress](#emailAddress-string-email)

* * *

#### file.api_url *string (url)*

Correspond au lien de téléchargement direct du document généré en utilisant l'API Jepilote.

voir : [GET /export_document/{hash}](get_export)