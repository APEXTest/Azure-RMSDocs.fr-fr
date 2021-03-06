---
title: "Déployer le connecteur Azure Rights Management - AIP"
description: "Instructions pour déployer le connecteur RMS, qui fournit le service de protection des données dans le cas des déploiements locaux existants utilisant Exchange Server, SharePoint Server ou Windows Server et l’Infrastructure de classification des fichiers (ICF)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 90e7e33f-9ecc-497b-89c5-09205ffc5066
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 93246a239476331f8fc117560c8ce45420eea674
ms.lasthandoff: 02/24/2017


---

# <a name="deploying-the-azure-rights-management-connector"></a>Déploiement du connecteur Azure Rights Management

>*’applique à : Azure Information Protection, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Utilisez ces informations pour découvrir le connecteur Azure Rights Management et pour savoir comment le déployer correctement dans votre organisation. Ce connecteur assure la protection des données dans le cas des déploiements locaux existants qui utilisent **Microsoft Exchange Server**, **SharePoint Server** ou des serveurs de fichiers qui exécutent Windows Server et l’**Infrastructure de classification des fichiers** (ICF).

> [!TIP]
> Pour obtenir un exemple de scénario global illustré par des captures d’écran, consultez la section [Protection automatique de fichiers sur des serveurs de fichiers exécutant Windows Server et l’infrastructure de classification des fichiers](../understand-explore/what-admins-users-see.md#automatically-protecting-files-on-file-servers-running-windows-server-and-file-classification-infrastructure) dans l’article [Azure RMS en action](../understand-explore/what-admins-users-see.md).

## <a name="overview-of-the-microsoft-rights-management-connector"></a>Vue d'ensemble du connecteur Microsoft Rights Management
Le connecteur Microsoft Rights Management (RMS) permet d'activer rapidement des serveurs locaux existants pour utiliser les services RMS avec le service Microsoft Rights Management (Azure RMS) basé sur le cloud. Cette fonctionnalité permet au service informatique et aux utilisateurs de protéger facilement des documents et des images à l'intérieur comme à l'extérieur de l'organisation, sans avoir à installer des infrastructures supplémentaires ou à établir des relations de confiance avec d'autres organisations. 

Le connecteur RMS est un service à faible encombrement qui doit être installé en local sur des serveurs exécutant Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2. Outre la possibilité d'exécuter le connecteur sur des ordinateurs physiques, vous pouvez l'exécuter sur des machines virtuelles, y compris des machines virtuelles Azure IaaS. Une fois déployé, le connecteur joue le rôle d’interface de communication (relais) entre les serveurs locaux et le service cloud, comme le montre l’illustration suivante. Les flèches indiquent le sens dans lequel les connexions réseau sont démarrées.

![Vue d’ensemble de l’architecture du connecteur RMS](../media/RMS_connector.png)


### <a name="on-premises-servers-supported"></a>Serveurs locaux pris en charge

Le connecteur RMS prend en charge les serveurs locaux suivants : Exchange Server, SharePoint Server, ainsi que les serveurs de fichiers exécutant Windows Server et utilisant l’infrastructure de classification des fichiers pour classer et appliquer des stratégies à des documents Office dans un dossier. 

> [!NOTE]
> Si vous voulez protéger plusieurs types de fichiers (pas seulement les documents Office) à l’aide de l’Infrastructure de classification des fichiers, n’utilisez pas le connecteur RMS, mais des [applets de commande AzureInformationProtection](/powershell/azureinformationprotection/vlatest/aip).

Pour connaître les versions de ces serveurs locaux qui sont prises en charge par le connecteur RMS, consultez [Serveurs locaux qui prennent en charge Azure RMS](..\get-started\requirements-servers.md).


### <a name="support-for-hybrid-scenarios"></a>Prise en charge des scénarios hybrides

Vous pouvez utiliser ce connecteur RMS même si certains de vos utilisateurs se connectent à des services en ligne dans le cadre d’un scénario hybride. Par exemple, les boîtes aux lettres de certains utilisateurs utilisent Exchange Online et celles d'autres utilisateurs utilisent Exchange Server. Après installation du connecteur RMS, tous les utilisateurs peuvent protéger et consommer des courriers électroniques et pièces jointes à l'aide d'Azure RMS, et la protection des informations fonctionne de façon transparente entre les deux configurations de déploiement.

### <a name="support-for-customer-managed-keys-byok"></a>Prise en charge des clés gérées par le client (BYOK)

Si vous gérez votre propre clé de locataire pour Azure RMS (scénario BYOK, Bring You Own Key), le connecteur RMS et les serveurs locaux qui l’utilisent n’accèdent pas au module de sécurité matériel (HSM) qui contient votre clé de locataire. En effet, toutes les opérations de chiffrement qui utilisent la clé de locataire sont effectuées dans Azure RMS et non en local.

Si vous voulez découvrir plus en détail ce scénario dans lequel vous gérez votre clé de locataire, consultez [Planification et implémentation de votre clé de locataire Azure Rights Management](../plan-design\plan-implement-tenant-key.md).

## <a name="prerequisites-for-the-rms-connector"></a>Conditions requises pour l'installation du connecteur RMS
Avant d'installer le connecteur RMS, assurez-vous que les conditions requises suivantes sont remplies.

|Condition requise|Plus d'informations|
|---------------|--------------------|
|Service Rights Management (RMS) activé|[Activation d’Azure Rights Management](activate-service.md)|
|Synchronisation des annuaires entre vos forêts Active Directory locales et Azure Active Directory|Une fois RMS activé, Azure Active Directory doit être configuré pour travailler avec les utilisateurs et les groupes de votre base de données Active Directory.<br /><br />**Important** : vous devez effectuer cette étape de synchronisation des annuaires pour que le connecteur RMS fonctionne, même pour un réseau de test. Même si vous pouvez utiliser Office 365 et Azure Active Directory avec des comptes crées manuellement dans Azure Active Directory, ce connecteur nécessite que les comptes Azure Active Directory soient synchronisés avec les services de domaine Active Directory. La synchronisation manuelle des mots de passe n'est pas suffisante.<br /><br />Pour plus d'informations, consultez les ressources suivantes :<br /><br />[Intégration de vos identités locales à Azure Active Directory](/active-directory/active-directory-aadconnect)<br /><br />[Comparaison des outils d’intégration d’annuaire d’identités hybrides](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison)|
|Facultatif mais recommandé :<br /><br />Activation de la fédération entre l'annuaire Active Directory local et Azure Active Directory|Vous pouvez activer la fédération des identités entre votre annuaire local et Azure Active Directory. Cette configuration offre une expérience utilisateur plus homogène grâce à une authentification unique au service RMS. Sans l'authentification unique, les utilisateurs sont invités à saisir leurs identifiants pour pouvoir utiliser des contenus protégés par des droits.<br /><br />Pour plus d'informations sur la configuration de la fédération par le biais des services AD FS (Active Directory Federation Services) entre les services de domaine Active Directory et Azure Active Directory, consultez la rubrique [Liste de contrôle : Utiliser AD FS pour mettre en œuvre et gérer l'authentification unique](http://technet.microsoft.com/library/jj205462.aspx) dans la bibliothèque Windows Server.|
|Au moins deux ordinateurs membres sur lesquels installer le connecteur RMS :<br /><br />- Un ordinateur 64 bits virtuel ou physique exécutant l’un des systèmes d’exploitation suivants : Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2.<br /><br />- 1 Go de RAM minimum.<br /><br />- 64 Go d’espace disque minimum.<br /><br />- Au moins une interface réseau.<br /><br />- Un accès à Internet par le biais d’un pare-feu (ou proxy web) qui ne nécessite pas d’authentification.<br /><br />- Un emplacement au sein d’une forêt ou d’un domaine qui approuve les autres forêts de l’organisation contenant les installations des serveurs Exchange ou SharePoint à utiliser avec le connecteur RMS.|Pour une tolérance de panne et une haute disponibilité, vous devez installer le connecteur RMS sur un minimum de deux ordinateurs.<br /><br />**Conseil** : si vous utilisez Outlook Web Access ou des appareils mobiles qui utilisent Exchange ActiveSync IRM et qu’il est essentiel de maintenir l’accès aux messages électroniques et pièces jointes protégés par Azure RMS, nous vous recommandons de déployer un groupe de serveurs de connecteur faisant l’objet d’un équilibrage de charge pour garantir une haute disponibilité.<br /><br />Vous n'avez pas besoin de serveurs dédiés pour exécuter le connecteur, mais vous devez l'installer sur un ordinateur différent des serveurs qui utiliseront le connecteur.<br /><br />**Important** : n’installez pas le connecteur sur un ordinateur qui exécute Exchange Server, SharePoint Server ou un serveur de fichiers configuré pour l’infrastructure de classification des fichiers si vous voulez utiliser la fonctionnalité depuis ces services avec Azure RMS. En outre, n'installez pas ce connecteur sur un contrôleur de domaine.|

## <a name="steps-to-deploy-the-rms-connector"></a>Procédure de déploiement du connecteur RMS

Sachant que le connecteur ne vérifie pas automatiquement toutes les [conditions préalables](deploy-rms-connector.md#prerequisites-for-the-rms-connector) nécessaires à la réussite d’un déploiement, assurez-vous qu’elles sont réunies avant de commencer. À cet effet, vous devez installer le connecteur, le configurer et configurer ensuite les serveurs appelés à utiliser le connecteur. 

-   **Étape 1 :**  [Installation du connecteur RMS](install-configure-rms-connector.md#installing-the-rms-connector)

-   **Étape 2 :**  [Saisie des informations d’identification](install-configure-rms-connector.md#entering-credentials)

-   **Étape 3 :**  [Définition des serveurs autorisés à utiliser le connecteur RMS](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector)

-   **Étape 4 :**  [Configuration de l’équilibrage de charge et de la haute disponibilité](install-configure-rms-connector.md#configuring-load-balancing-and-high-availability)

-   Facultatif : [Configuration du connecteur RMS pour le protocole HTTPS](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https)

-   Facultatif : [Configuration du connecteur RMS pour un serveur proxy web](install-configure-rms-connector.md#configuring-the-rms-connector-for-a-web-proxy-server)

-   Facultatif : [Installation de l’outil d’administration du connecteur RMS sur les ordinateurs d’administration](install-configure-rms-connector.md#installing-the-rms-connector-administration-tool-on-administrative-computers)

-   **Étape 5 :**  [Configuration de serveurs afin d’utiliser le connecteur RMS](configure-servers-rms-connector.md)

    -   [Configuration d’un serveur Exchange afin d’utiliser le connecteur](configure-servers-rms-connector.md#configuring-an-exchange-server-to-use-the-connector)

    -   [Configuration d’un serveur SharePoint afin d’utiliser le connecteur](configure-servers-rms-connector.md#configuring-a-sharepoint-server-to-use-the-connector)

    -   [Configuration d’un serveur de fichiers pour l’infrastructure de classification des fichiers afin d’utiliser le connecteur](configure-servers-rms-connector.md#configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector)


## <a name="next-steps"></a>Étapes suivantes

Accédez à l’étape 1 : [Installation et configuration du connecteur Azure Rights Management](install-configure-rms-connector.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
