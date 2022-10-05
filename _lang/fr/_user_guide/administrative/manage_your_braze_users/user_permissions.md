---
nav_title: Autorisations utilisateur du compte Braze
article_title: Autorisations utilisateur du compte Braze
page_order: 2
page_type: reference
description: "Cet article de référence couvre les autorisations d’utilisateur de Braze, comme choisir qui peut accéder à vos applications sur le tableau de bord de Braze."
tool: Dashboard

---

# Définition des autorisations utilisateur

<style>
.fa-crown {
  color: gold;
}
</style>

La fonction d’autorisation de l’utilisateur de Braze vous permet de choisir qui peut accéder à vos applications sur le tableau de bord de Braze en attribuant des utilisateurs différents à l’un ou l’autre des administrateurs (désignés par un <i class="fas  fa-crown" aria-label="crown icon"></i> à côté de votre nom d’utilisateur) ou une autorisation limitée. Le créateur du groupe d’apps sera automatiquement autorisé à accéder à l’administrateur. Vous pouvez trouver ces paramètres en accédant à votre nom dans le tableau de bord et en sélectionnant **Manage Users** (Gérer les utilisateurs) dans la liste déroulante. 

![Liste des utilisateurs du compte sur la page Manage Settings (Gérer les paramètres)][30]

|Niveau d’accès|Autorisations|
|---|---|
|Administrateur|Les administrateurs ont accès à toutes les fonctionnalités disponibles.|
|Limité|Les utilisateurs limités sont entièrement personnalisés à plusieurs niveaux, décrits dans les sections suivantes. Lorsque vous faites passer les permissions d’un utilisateur d’« admin » à « limité », cet utilisateur n’a plus accès à aucune partie du tableau de bord de Braze tant que vous n’avez pas l’intention de l’utiliser à l’aide des cases à cocher qui apparaissent sous la zone Edit User (Modifier l’utilisateur).|
{: .reset-td-br-1 .reset-td-br-2}

## Modification des autorisations utilisateur

À partir de la page Manage Users (Gérer les utilisateurs), vous pouvez modifier les autorisations d’un utilisateur spécifique, soit en lui permettant de conserver son rôle d’administrateur par défaut, soit en le faisant passer à un rôle limité. Pour modifier son rôle, cliquez sur l’icône Edit (Modifier) dans la ligne de l’utilisateur et sélectionnez Limited (Limité) dans le menu déroulant User Role (Rôle utilisateur).

![Sélection du rôle administrateur ou limité lors de la modification d’un utilisateur][29]{: style="border:none"}

Lorsque vous faites passer les permissions d’un utilisateur d’Administrateur à Limité, cet utilisateur n’a plus accès à aucune partie de Braze jusqu’à ce que vous définissiez ces permissions spécifiques à l’aide des cases à cocher qui apparaissent sous la zone Edit User (Modifier l’utilisateur). Les explications pour chacune de ces autorisations se trouvent dans le graphique Level of Access (Niveau d’accès) en haut de cette page.

## Autorisations limitées et de rôle de la team

Vous pouvez gérer les autorisations utilisateur par groupe ou sur une base individuelle à l’aide de la page User Permissions (Autorisations utilisateur).

![Gérer les autorisations utilisateur][89]

|Nom de l’autorisation|Définition/Paramètres|
|---|---|
|Admin|Accès à toutes les fonctions disponibles, réglage par défaut pour tous les nouveaux utilisateurs. Peut mettre à jour les paramètres de la société (nom de la société et fuseau horaire), que les utilisateurs limités ne peuvent pas faire.|
|Campagnes d’accès, Canvas, cartes, segments, bibliothèque multimédia| L’utilisateur peut consulter les mesures de performance de la campagne et des Canvas, créer et dupliquer des projets de campagnes et de Canvas, afficher des projets de fil d’actualités, des segments, des modèles et des médias, créer des modèles, télécharger des médias et afficher des engagement reports. Cependant, les utilisateurs avec cette autorisation ne peuvent pas afficher le contenu en direct existant. |
|Envoyer des campagnes, des Canvas| Permet à l’utilisateur de modifier, d’archiver et d’arrêter des campagnes et des canvas, de créer des campagnes, de lancer des canvas. Pour lancer des blocs de contenu existants, les deux autorisations **Send campaigns, Canvases** (Envoyer des campagnes, des Canvas) et **Publish Cards** (Publier des cartes) sont requises. |
|Publier des cartes| Permet à l’utilisateur de créer et de modifier des cartes de fil d’actualités. Vous pouvez toujours afficher les cartes sans cette autorisation. Pour lancer des blocs de contenu existants, les deux autorisations **Publish Cards** (Publier des cartes) et **Send campaigns, Canvases** (Envoyer des campagnes, des Canvas) sont requises. |
|Modifier les segments| Permet à l’utilisateur de créer et de modifier des segments. Vous pouvez toujours créer des campagnes avec des segments et filtres existants sans cette autorisation. Vous avez besoin de cette autorisation pour générer un segment des utilisateurs dans un CSV ou recibler le groupe d’utilisateurs dans le CSV.|
|Exporter les données utilisateur| Permet à l’utilisateur d’exporter ses données utilisateur à partir de segments, de campagnes et de canvas. |
|Afficher les Informations personnellement identifiables | Permet à l’utilisateur d’afficher des informations personnellement identifiables dans le tableau de bord. Notez que l’adresse e-mail et le numéro de téléphone seront visibles. |
|Afficher le profil utilisateur| Permet à l’utilisateur d’accéder à la page User Search (Rechercher un utilisateur).|
|Gérer les utilisateurs du tableau de bord| Permet à l’utilisateur d’afficher, de modifier et de gérer l’onglet **Manage Users** (Gérer les utilisateurs). Les utilisateurs disposant de cette autorisation peuvent modifier les autorisations de tout utilisateur, y compris eux-mêmes. Ainsi, cette autorisation doit être considérée comme un niveau d’accès administratif.|
|Gérer la bibliothèque multimédia| Permet à l’utilisateur de charger des images dans la bibliothèque. Vous pouvez toujours télécharger des images/audio, etc. directement à une campagne sans cette autorisation.|
|Afficher les données d’utilisation| Permet à l’utilisateur d’afficher l’utilisation de l’application.|
|Importer et mettre à jour les données utilisateur| Permet à l’utilisateur d’importer les fichiers CSV et de mettre à jour les fichiers des utilisateurs d’applications, ainsi que de visualiser la page User Import (Importation d’utilisateurs).|
|Afficher les détails de facturation| Permet à l’utilisateur d’afficher les abonnements et la facturation. |
|Accéder à la Developer console| Permet d’accéder à la Developer Console (où vous pouvez afficher les clés API, le journal des activités de campagne API, le journal des utilisateurs de l’événement et les groupes internes pour les messages de test).|
|Gérer les intégrations externes| Permet d’accéder à tous les onglets sous **Technology Partners** et offre la possibilité de synchroniser Braze avec d’autres plateformes.|
|Gérer les applications| Permet à l’utilisateur de modifier les paramètres (sous **Manage Settings** (Gérer les paramètres)).|
|Gérer les Teams|Permet à l’utilisateur de gérer les équipes dans **Manage settings** (Gérer les paramètres). La possibilité de sélectionner cette autorisation dépend de votre contrat avec Braze.|
|Gérer les événements, attributs, achats|Permet à l’utilisateur de modifier des attributs personnalisés (les utilisateurs ne disposant pas de cette fonctionnalité peuvent toujours afficher des attributs personnalisés), modifier et afficher les propriétés des événements personnalisés, modifier et afficher les propriétés des produits sous **Manage Settings** (Gérer les paramètres).|
|Gérer les balises|Permet aux utilisateurs de modifier ou de supprimer des balises (sous **Manage Settings** (Gérer les paramètres)). Vous n’avez pas besoin de cette autorisation pour ajouter des balises aux campagnes ou segments.|
|Gérer les paramètres d’e-mail|Permet à l’utilisateur d’enregistrer les modifications de configuration d’e-mail (onglet de paramètres d’e-mail sous **Manage Settings** (Gérer les paramètres)).|
|Gérer les groupes d’abonnement  | Permet à l’utilisateur de créer et de gérer des groupes d’abonnement. |
{: .reset-td-br-1 .reset-td-br-2}

## Autorisations de l’utilisateur application par application

Les utilisateurs individuels peuvent recevoir différents degrés d’accès application par application.

|Degré d’autorisation limité|Détails|
|---|---|---|
|Niveau de l’entreprise|En ce qui concerne la gestion des paramètres de groupe et d’application de l’entreprise.|
|Autorisations de niveau groupe d’apps|Quels groupes d’apps l’utilisateur limité doit-il pouvoir gérer ?|
|Paramètres de niveau d’application|Quel niveau d’accès à la modification doit avoir cet utilisateur limité ?|
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3}

[29]: {% image_buster /assets/img_archive/editing_user_permission_new.png %} "Edit User Permission"
[30]: {% image_buster /assets/img_archive/two_factor_authentication_manage_users_new.png %}
[76]: {{site.baseurl}}/user_guide/administrative/manage_your_braze_users/user_permissions/
[89]: {% image_buster /assets/img/user_permissions_selection.png %}