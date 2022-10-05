---
nav_title: Limites de débit
article_title: Limites de débit de l’API
page_order: 4.5
description: "Cet article de référence couvre les limites de débit de l’API pour l’infrastructure API Braze."
page_type: reference

---

# Limites de débit de l’API

L’infrastructure API Braze est conçue pour gérer des volumes élevés de données sur l’ensemble de notre base de clients. Afin de garantir l’utilisation responsable de l’API, nous appliquons des limites de débit à l’API par groupe d’apps. Une limite de débit correspond au nombre de demandes que l’API peut recevoir dans une période donnée. Si trop de demandes sont envoyées dans un délai donné, vous pouvez voir les réponses d’erreur avec un code de statut de `429`, qui indique que la limite de débit a été atteinte.

{% alert warning %}
Les limites de débit de l’API et leurs valeurs (limitées ou illimitées) sont sujettes à modification en fonction de l’utilisation correcte de notre système. Nous encourageons des limites raisonnables lors de l’appel d’API afin d’éviter tout dommage ou toute mauvaise utilisation.
{% endalert %}

## Limites de débit par type de demande

Le tableau suivant répertorie les limites de débit d’API spécifiques pour différents types de demandes. Toutes les autres demandes non répertoriées dans ce tableau ont une limite de débit par défaut de 250 000 demandes par heure.

| Type de demande | Limite de débit de l’API par défaut |
| --- | --- |
| [`/users/track`][10] | **Demandes :** 50 000 demandes par minute. Cette limite peut être augmentée sur demande. Contactez votre gestionnaire du succès des clients pour plus d’informations.<br><br>**Traitement par lot :** 75 événements, 75 achats et 75 attributs par demande API. Voir [Demandes de suivi utilisateur du traitement par lots](#batch-user-track) pour en savoir plus. |
| [`/users/export/ids`][11] | 2 500 demandes par minute. |
| [`/users/delete`][12]<br>[`/users/alias/new`][13]<br>[`/users/identify`][14] | 20 000 demandes par minute, partagées entre les endpoints. |
| [`/users/external_id/rename`][20] | 1 000 demandes par minute. |
| [`/users/external_id/remove`][21] | 1 000 demandes par minute. |
| [`/events/list`][15] | 1 000 demandes par heure, partagées avec l’endpoint `/purchases/product_list`. |
| [`/purchases/product_list`][16] | 1 000 demandes par heure, partagées avec l’endpoint `/events/list`. |
| [`/messages/send`][17] | 250 demandes par minute lors de la spécification d’un segment ou d’une audience connecté(e). Sinon, 250 000 demandes par heure. |
| [`/campaigns/trigger/send`][17.1] | 250 demandes par minute lors de la spécification d’un segment ou d’une audience connecté(e). Sinon, 250 000 demandes par heure. |
| [`/canvas/trigger/send`][17.2] | 250 demandes par minute lors de la spécification d’un segment ou d’une audience connecté(e). Sinon, 250 000 demandes par heure. |
| [`/sends/id/create`][18] | 100 demandes par jour. |
| [`/subscription/status/set`][19] | 5 000 demandes par minute. |
{: .reset-td-br-1 .reset-td-br-2}
<!--
| [`GET: /scim/v2/Users/YOUR_ID_HERE`][22] | 5,000 requests per day, per company, shared with the `/scim/v2/Users/YOUR_ID_HERE` PUT, DELETE and `/scim/v2/Users` POST endpoints. |
| [`PUT: /scim/v2/Users/YOUR_ID_HERE`][25] | 5,000 requests per day, per company, shared with the `/scim/v2/Users/YOUR_ID_HERE` GET, DELETE and `/scim/v2/Users` POST endpoints. |
| [`DELETE: /scim/v2/Users/YOUR_ID_HERE`][24] | 5,000 requests per day, per company, shared with the `/scim/v2/Users/YOUR_ID_HERE` PUT, GET and `/scim/v2/Users` POST endpoints. |
| [`POST: /scim/v2/Users/`][23] | 5,000 requests per day, per company, shared with the `/scim/v2/Users/YOUR_ID_HERE` PUT, GET, and DELETE endpoints. |
--->

## Traitement des demandes d’API par lot

Les API de Braze sont conçues pour prendre en charge le traitement par lot. Grâce au traitement par lot, Braze peut prendre autant de données que possible dans un seul appel d’API afin que vous n’ayez pas besoin de passer beaucoup d’appels d’API. Il est plus efficace pour Braze de traiter les données par lots que de les traiter par appel. Par exemple, la gestion de 1 000 appels d’API par lots nécessite moins de ressources que la gestion de 75 000 appels individuels. L’utilisation du traitement par lot est extrêmement importante pour les applications qui peuvent nécessiter plus de 75 000 appels par heure.

{% alert note %}
Les augmentations de limite de débit API REST sont envisagées en fonction du besoin des clients qui utilisent les capacités de traitement par lot de l’API.
{% endalert %}

### Demandes de suivi utilisateur du traitement par lot {#batch-user-track}

Chaque demande `/users/track` peut contenir jusqu’à 75 événements, 75 mises à jour d’attributs et 75 achats. Chaque composant (tableau d’événements, d’attributs et d’achats) peut mettre à jour jusqu’à 75 utilisateurs chacun (pour un maximum de 225 utilisateurs individuels). Chaque mise à jour peut également appartenir au même utilisateur pour un maximum de 225 mises à jour par utilisateur dans une demande.

Les demandes adressées à cet endpoint commencent généralement à traiter dans cet ordre : 

1. Attributs
2. Événements
3. Achats

### Demandes de traitement par lot aux endpoints de messagerie

Une seule demande aux [endpoints de messagerie][1] peut atteindre l’un des éléments suivants :

- Jusqu’à 50 `external_ids` spécifiques, chacun avec des paramètres de message individuels
- Un segment de toute taille créée dans le tableau de bord de Braze, spécifié par son `segment_id`
- Un segment public ad hoc de toute taille, défini dans la demande en tant qu’objet [Audience connectée][2]

## Surveiller vos limites de débit

Chaque demande API envoyée à Braze renvoie les informations suivantes dans les en-têtes de réponse :

Nom d’en-tête             | Description
----------------------- | -----------------------
`X-RateLimit-Limit`     | Nombre maximum de demandes que vous pouvez effectuer dans un intervalle spécifié (votre limite de débit).
`X-RateLimit-Remaining` | Nombre de demandes restant dans la fenêtre de limite de débit actuelle.
`X-RateLimit-Reset`     | Heure à laquelle la fenêtre de limite de débit actuelle se réinitialise en secondes d’époque UTC.
{: .reset-td-br-1 .reset-td-br-2}

Ces informations sont intentionnellement incluses dans l’en-tête de la réponse à la demande API plutôt que sur le tableau de bord de Braze. Cela permet à votre système de mieux réagir en temps réel lorsque vous interagissez avec notre API. Par exemple, si la valeur `X-RateLimit-Remaining` chute en dessous d’un certain seuil, vous voudrez peut-être ralentir l’envoi pour vous assurer que tous les e-mails transactionnels partent. Ou, si elle atteint zéro, vous voudrez peut-être suspendre tous les envois jusqu’à ce que le temps spécifié dans `X-RateLimit-Reset` s’écoule.

Si vous avez des questions sur les limites d’API, contactez votre gestionnaire du succès des clients ou ouvrez un [ticket d’assistance][support].

### Délai optimal entre les endpoints

> Nous vous recommandons de prévoir un délai de 5 minutes entre les appels suivants afin de minimiser la probabilité d’erreur.

Il est crucial de comprendre le délai optimal entre les endpoints lors de la réalisation d’appels consécutifs vers l’API Braze. Des problèmes surviennent lorsque les endpoints dépendent du traitement réussi d’autres endpoints, et s’ils sont appelés trop tôt, ils peuvent provoquer des erreurs. Par exemple, si vous assignez un alias à un utilisateur via notre endpoint `/user/alias/new`, puis que vous appuyez sur cet alias pour envoyer un événement personnalisé via notre endpoint `/users/track`, combien de temps devrez-vous attendre ?

Dans des conditions normales, le temps pour que la cohérence éventuelle de nos données se produise est de 10 à 100 ms (1/10 d’une seconde). Cependant, il peut y avoir des cas où il faut plus longtemps pour que cette cohérence se produise. Par conséquent, nous vous recommandons de prévoir un délai de 5 minutes entre les appels suivants afin de minimiser la probabilité d’erreur.

[1]: {{site.baseurl}}/api/endpoints/messaging/
[2]: {{site.baseurl}}/api/objects_filters/connected_audience/
[support]: {{site.baseurl}}/braze_support/

[10]: {{site.baseurl}}/api/endpoints/user_data/post_user_track/
[11]: {{site.baseurl}}/api/endpoints/export/user_data/post_users_identifier/
[12]: {{site.baseurl}}/api/endpoints/user_data/post_user_delete/
[13]: {{site.baseurl}}/api/endpoints/user_data/post_user_alias/
[14]: {{site.baseurl}}/api/endpoints/user_data/post_user_identify/
[15]: {{site.baseurl}}/api/endpoints/export/custom_events/get_custom_events/
[16]: {{site.baseurl}}/api/endpoints/export/purchases/get_list_product_id/
[17]: {{site.baseurl}}/api/endpoints/messaging/send_messages/post_send_messages/
[17.1]: {{site.baseurl}}/api/endpoints/messaging/send_messages/post_send_triggered_campaigns/
[17.2]: {{site.baseurl}}/api/endpoints/messaging/send_messages/post_send_triggered_canvases/
[18]: {{site.baseurl}}/api/endpoints/messaging/send_messages/post_create_send_ids/
[19]: {{site.baseurl}}/api/endpoints/subscription_groups/post_update_user_subscription_group_status/
[20]: {{site.baseurl}}/api/endpoints/user_data/external_id_migration/post_external_ids_rename/
[21]: {{site.baseurl}}/api/endpoints/user_data/external_id_migration/post_external_ids_remove/
[22]: {{site.baseurl}}/scim/get/
[23]: {{site.baseurl}}/scim/post/
[24]: {{site.baseurl}}/scim/delete/
[25]: {{site.baseurl}}/scim/put