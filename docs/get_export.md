---
id: get_export
title: Get export
---

| ENDPOINT                       |
| ------------------------------ |
| GET /export_documents/{*hash*} |

Lance un lien de téléchargement direct du fichier d'export identifié par *hash*

Il est nécessaire d'être [authentifié](authenticate).

## Parametres

Aucun

## Reponse

Si le *hash* n'identifie aucun fichier existant, une erreur http 404 est retourné.

Si le *hash* identifie un fichier ne vous appartenant pas ou que vous n'êtes pas authentifié, une erreur http 403 est retourné. 

Sinon, un processus de téléchargement de fichier est lancé.
