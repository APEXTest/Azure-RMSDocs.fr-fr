---
title: Notes de publication | Azure RMS
description: 
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 06/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: CE379738-4E1D-42AD-83F4-F89B70456EBB
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79397c82d9478cbd55630a376fe2d12f3873ebc4
ms.openlocfilehash: 2892bc8242c3b6a90352829bf251b7044a919ed3


---

# Notes de publication

Cette rubrique contient des informations importantes sur cette version du Kit RMS SDK 2.1 et sur les versions précédentes.

## Nouveautés dans la mise à jour de la documentation du SDK de février 2016

>[!Note]
> Les mises à jour de la documentation de fonctionnalités dans cette section s’appliquent au téléchargement du SDK daté du 11/12/2015.

- **Amélioration du flux d’authentification** : utilisation de l’authentification basée sur les jetons OAuth2 par le biais de la [bibliothèque ADAL (Azure Active Directory Authentication Library)](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/). Pour plus d’informations sur ce processus et ses extensions d’API, consultez [Authentification ADAL pour votre application compatible RMS](how-to-use-adal-authentication.md).

- **Mise à jour vers la bibliothèque ADAL** : en mettant à jour votre application pour utiliser l’authentification ADAL au lieu de l’Assistant de connexion Microsoft Online, vous et vos clients pouvez :

 - Utiliser l’authentification multifacteur.
 - Installer le client RMS 2.1 sans nécessiter de privilèges d’administration sur l’ordinateur.
 - Certifier votre application pour Windows 10

- **La prise en charge de l’Assistant de connexion Microsoft Online avec le SDK RMS est supprimée.** Nous continuerons à prendre en charge l’utilisation de l’Assistant de connexion pendant six mois, après quoi la prise en charge cessera.


## Mise à jour de décembre 2015

- Des améliorations de performances ont été implémentées dans plusieurs domaines :
    - Publication depuis le serveur de licences principal lors de l’utilisation de serveurs de licence.
    - RMS SDK 2.1 échoue plus rapidement lorsqu’il n’existe aucune connexion réseau.

- Nombreuses mises à jour pour améliorer les messages d’erreur et le dépannage.
- Notez également que la liste des [plates-formes prises en charge](supported-platforms.md) est également mise à jour.
- Le besoin d’un environnement de préproduction et l’utilisation de manifestes d’application ont été supprimés de RMS SDK 2.1. Les sections de cet ensemble de documentation pour développeurs ont été supprimées et l’ensemble de la documentation simplifié et réorganisé.

## Mise à jour de mai 2015

-   **Applications de service et service RMS cloud** - [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential_symmetric_key#msipc_ipc_credential_symmetric_key) a besoin de trois informations : la clé symétrique, **AppPrincipalId** et **TenantBposId**. La rubrique traitant de ce sujet a été mise à jour pour fournir des conseils sur le traitement de ces informations d’acquisition. Pour cette mise à jour, consultez la version mise à jour de [Permettre à votre application de service de fonctionner avec le service RMS cloud](how-to-use-file-api-with-aadrm-cloud.md).

## Mise à jour d’avril 2015

-   Le **suivi des documents** est maintenant possible grâce à un ensemble de nouvelles API. Pour plus d’informations, consultez [Suivi de contenu](tracking-content.md).
-   **Type de chiffrement** : nous prenons désormais en charge le contrôle au niveau de l’API pour la sélection du package de chiffrement. Pour plus d’informations, voir [Utilisation du chiffrement](working-with-encryption.md).

    **Remarque** Nous n’exposerons plus l’indicateur **IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS** dans notre API. Cela signifie que les futures applications ne seront plus compilées si elles font référence à cet indicateur. Toutefois les applications déjà créées continueront de fonctionner dans la mesure où nous respecterons de manière privée l’indicateur dans le code de l’API. Il est encore possible de tirer parti de l’ancien indicateur obsolète des algorithmes de chiffrement en modifiant simplement un indicateur. Pour plus d’informations, voir [Utilisation du chiffrement](working-with-encryption.md).

-   Les **applications en mode serveur**, celles utilisant une [**valeur du mode API**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER) de **IPC\_API\_MODE\_SERVER**, n’ont plus besoin d’installer de manifeste d’application. Vous pouvez tester votre application sur un serveur RMS de production et vous n’êtes pas obligé d’obtenir une licence de production quand vous passez à l’environnement de production. Pour plus d’informations sur les applications en mode serveur, consultez [Types d’applications](application-types.md).
-   La **journalisation** est maintenant implémentée par le biais du fichier et de méthodes de suivi d’événements pour Windows.
-   Si l’exécution s’effectue sur un **ordinateur Windows 7 SP1 ou Windows Server 2008 R2**, lisez la remarque suivante sous « Remarques importantes à l’attention des développeurs ».

## Mise à jour de janvier 2015

-   **Prise en charge de l’augmentation de la taille du fichier protégé (pfile)** : prise en charge de tailles de fichiers supérieures à un gigaoctet (1 Go). Pour plus d’informations sur les fichiers pfile, consultez [Formats de fichiers pris en charge](supported-file-formats.md).
-   **Amélioration de la journalisation pour un meilleur diagnostic** : les niveaux de journalisation indiquent **ERREUR** ou **AVERTISSEMENT** pour les messages qui doivent être examinés. Tous les autres messages, y compris les exceptions qui sont toujours affichées, seront enregistrés en tant que **INFO**.

    Nous avons choisi cette approche afin de ne perdre aucun détail. À présent, seuls les messages importants ayant le niveau AVERTISSEMENT sont affichés.

-   **Acquisition des modèles d’une société** :corrections importantes apportées au code d’acquisition de modèles en fonction des rapports et des commentaires clients.
-   Amélioration de la cohérence de la localisation

## Mise à jour d’octobre 2014

-   Les comportements par défaut du composant de l’API de fichier du SDK a été mis à jour. Pour plus d’informations, voir [Configuration de l’API de fichier](file-api-configuration.md).
-   La notification par courrier électronique, qui est une nouvelle fonctionnalité, est décrite dans la rubrique des remarques à l’attention des développeurs [Activation des notifications par courrier électronique](how-to-enable-email-notification.md).

## Mise à jour de juillet 2014

Le composant de l’API de fichier du SDK a été étendu et offre les fonctionnalités suivantes :

-   Identifie le protecteur à utiliser.
-   Fournit une protection RMS au niveau de granularité d’un fichier.

    Fonctions ajoutées dans cette version :

    **Remarque** D’autres types et structures de données de prise en charge, non répertoriés ici, ont été ajoutés pour les extensions d’API de fichier. Toutes les rubriques mises à jour pour cette version sont marquées comme étant **préliminaires et susceptible d’être modifiées**.

    -   [**IpcfOpenFileOnHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfopenfileonhandle)
    -   [**IpcfOpenFileOnILockBytes**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfopenfileonilockbytes)
    -   [**IpcfGetFileProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfgetfileproperty)
    -   [**IpcfLogicalFileRangeToRawFileRange**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcflogicalfilerangetorawfilerange)
    -   [**IpcfReadFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfreadfile)
    -   [**IpcfSetEndOfFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfsetendoffile)
    -   [**IpcfWriteFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfwritefile)

## Mise à jour d’avril 2014

-   L’**utilisation de la mémoire d’API de fichier**, en particulier pour les PFiles volumineux, a été considérablement améliorée.
-   L’**ID de contenu** est désormais accessible en écriture par le biais de la propriété **IPC\_LI\_CONTENT\_ID**. Pour plus d’informations, voir [**Types de propriété de licence**](/rights-management/sdk/2.1/api/win/License%20property%20types#msipc_license_property_types_IPC_LI_APP_SPECIFIC_DATA).
-   **Besoin du manifeste de production** : le manifeste n’est plus nécessaire lorsque votre service ou application compatible avec RMS est exécutée en mode serveur. Pour plus d’informations, voir [Types d’applications](application-types.md).
-   **Mises à jour de la documentation**

    **Meilleure pratique en matière de test** : ajout de conseils pour l’utilisation d’un serveur local avant le test avec Azure RMS. Pour plus d’informations, consultez [Permettre à votre application de service d’opérer avec le service RMS cloud](how-to-use-file-api-with-aadrm-cloud.md).

## Remarques importantes à l’attention des développeurs

-   **Prise en charge native pour tous les types de fichier**

    Une prise en charge native peut être ajoutée pour tout type de fichier (extension) avec cette version du SDK Rights Management Services 2.1. Par exemple, pour toute extension &lt;ext&gt; (non Office et pdf), \*.p&lt;ext&gt; est utilisé si la configuration d’administration pour cette extension est « NATIVE ».

    Pour plus d’informations sur les types de fichier pris en charge, voir [Configuration de l’API de fichier](file-api-configuration.md).

-   Les **ordinateurs Windows 7 SP1 et Windows Server 2008 R2 SP1** non dotés de la mise à jour [KB2533623](https://support.microsoft.com/en-us/kb/2533623) peuvent afficher l’erreur suivante lors de la protection des fichiers Office : « Le paramètre est incorrect. Code d’erreur 0x80070057 ». Si vous voyez cette erreur, installez de nouveau la mise à jour et réessayez. Si cette erreur persiste, contactez l’alias de commentaires de la version bêta du SDK Rights Management <rmcstbeta@microsoft.com>.

    **Remarque**  : à compter de la version d’avril 2015, une vérification a été ajoutée au processus d’installation pour cette base de connaissances.

     

-   **Intégration de l’API de fichier**

    L’ajout de l’API de fichier à Active Directory Rights Management Services offre les avantages et les fonctionnalités suivantes :

      - Vous pouvez protéger les données confidentielles de manière automatisée sans avoir à connaître les détails de l’implémentation de la Gestion des droits relatifs à l’information utilisée par les différents formats de fichiers.

      - Les fichiers Microsoft Office, Portable Document Format (PDF) et d’autres types de fichier sélectionnés peuvent être protégés à l’aide de la protection native. Pour obtenir une liste complète des types de fichiers pouvant être protégés à l’aide de la protection native, voir [Configuration de l’API de fichier](file-api-configuration.md).

      - Tous les fichiers, à l’exception des fichiers système et des fichiers Office peuvent être protégés à l’aide du format de fichier de protégé par RMS (PFile).

    L’API de fichier est implémentée par le biais des quatre nouvelles fonctions suivantes : [IpcfDecryptFile](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile), [IpcfEncryptFile](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile), [IpcfGetSerializedLicenseFromFile](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfgetserializedlicensefromfile) et [IpcfIsFileEncrypted](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfisfileencrypted).

    L’API de fichier exige l’installation du client RMS (Rights Management Services) 2.1 sur l’ordinateur client et la connectivité de l’ordinateur avec un serveur RMS. Pour plus d’informations sur le serveur RMS, sur le client RMS et sur leurs fonctionnalités, consultez le contenu TechNet de la [documentation RMS pour les professionnels de l’informatique](https://technet.microsoft.com/en-us/library/cc771234(v=ws.10).aspx).

-   **Problème** : lors de la création d’une nouvelle licence, les droits de propriété doivent être accordés de manière explicite.

    **Solution** : votre application doit ajouter explicitement les droits **Propriétaire** au propriétaire de la licence lors de la création d’une nouvelle licence à l’aide de [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch). Pour plus d’informations, voir [Ajouter des droits de propriétaire explicites](add-explicit-owner-rights.md).

-   **Problème** : si une application appelle [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow) ou [**IpcUnprotectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcunprotectwindow) deux fois pour la même fenêtre à l’aide de son handle, RMS SDK 2.1 renvoie un échec dans le **HRESULT**.

    **Solution** : pour obtenir des conseils spécifiques concernant ce problème, consultez la section Remarques dans [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow) et [**IpcUnprotectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcunprotectwindow).

-   **Problème** : lors de la création de plusieurs architectures, vous devez utiliser ce guide.

    **Solution** : si vous souhaitez utiliser le fichier Ipcsecproc\*isv.dll pour une architecture différente (par exemple, vous avez installé le SDK 64 bits sur un ordinateur 64 bits et vous souhaitez maintenant effectuer le déploiement sur un ordinateur 32 bits qui nécessite Ipcsecproc\*isv.dll), vous devez installer le SDK 32 bits sur un autre ordinateur et copier les fichiers Ipcsecproc\*isv.dll à cet emplacement à partir du dossier « "%PROGRAMFILES%\\Microsoft Information Protection And Control » (l’emplacement par défaut ou là où vous avez choisi d’installer le SDK).

## Forum aux questions

**Q** : Comment se comporte la langue par défaut avec des fonctions qui prennent un paramètre LCID ?

**R** : Utilisez 0 pour les paramètres régionaux par défaut. Dans ce cas, le client AD RMS 2.1 recherche les noms et les descriptions dans l’ordre suivant et récupère le premier disponible :

    1 - User preferred LCID.
    2 - System locale LCID.
    3 - The first available language specified in the Rights Management Server (RMS) template.

Si aucun nom et aucune description ne peuvent être récupérés, une erreur est renvoyée. Un LCID spécifique ne peut avoir qu’un seul nom et qu’une seule description.

## Rubriques connexes

* [Vue d'ensemble](ad-rms-overview.md)
* [Ajouter des droits de propriétaire explicites](add-explicit-owner-rights.md)
* [Configuration de l’API de fichier](file-api-configuration.md)
* [**IpcfGetSerializedLicenseFromFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfgetserializedlicensefromfile)
* [**IpcfEncryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile)
* [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile)
* [**IpcfIsFileEncrypted**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfisfileencrypted)
* [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)
* [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow)
* [**IpcUnprotectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcunprotectwindow)
 

 



<!--HONumber=Jul16_HO4-->

