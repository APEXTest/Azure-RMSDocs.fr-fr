---
title: "Guide de l’administrateur de l’application de partage Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
ms.reviewer: esaggese
ms.suite: ems
ms.sourcegitcommit: f7dd88d90357c99c69fe4fdde67c1544595e02f8
ms.openlocfilehash: e67d0ab5537aa7444940a5e7ce3a653cc6e66993


---


# Guide de l'administrateur de l'application de partage Rights Management

*S’applique à : Active Directory Rights Management Services, Azure Rights Management, Windows 10, Windows 7 avec SP1, Windows 8, Windows 8.1*


Utilisez les informations suivantes si vous êtes responsable de l’application de partage Microsoft Rights Management sur un réseau d’entreprise ou si vous souhaitez des informations plus techniques que celles qui figurent dans le [Guide de l’utilisateur de l’application de partage Rights Management](sharing-app-user-guide.md) ou sur le [Forum Aux Questions sur l’application de partage Microsoft Rights Management pour Windows](http://go.microsoft.com/fwlink/?LinkId=303971).

L'application de partage RMS est mieux adaptée au travail avec Azure RMS, car cette configuration de déploiement prend en charge l'envoi de pièces jointes protégées à des utilisateurs d'une autre organisation et des options telles que les notifications par courrier électronique et le suivi des document avec révocation.  Toutefois, elle fonctionne également avec la version locale, AD RMS, avec certaines limitations. Pour une comparaison complète des fonctionnalités prises en charge par Azure RMS et AD RMS, consultez [Comparaison d’Azure Rights Management avec AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). Si vous avez AD RMS et que vous voulez migrer vers Azure RMS, consultez [Migration d’AD RMS vers Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

## Déploiement automatique de l'application de partage Microsoft Rights Management
La version Windows de l'application de partage RMS prend en charge une installation scriptée, ce qui la rend appropriée pour les déploiements d'entreprise.

Les seules conditions préalables à l'installation sont que les ordinateurs exécutent une version minimale de Windows 7 Service Pack 1 et que Microsoft Framework, version minimale 4.0, soit installé. Si vous devez installer Microsoft .NET Framework 4.0, vous pouvez le [télécharger pour installation à partir du Centre de téléchargement Microsoft](http://www.microsoft.com/download/details.aspx?id=17718).

### Pour télécharger l’application de partage RMS pour un déploiement automatique

1.  Accédez à la page [Microsoft Rights Management sharing application for Windows - Français](http://www.microsoft.com/download/details.aspx?id=40857) dans le Centre de téléchargement Microsoft, puis cliquez sur **Télécharger**.

2.  Sélectionnez et téléchargez les fichiers dont vous avez besoin. Il existe deux packages d’installation client : un pour Windows 64 bits (Microsoft Rights Management sharing application x64.zip) et un autre pour Windows 32 bits (Microsoft Rights Management sharing application x86.zip).

3.  Extrayez les fichiers des packages d’installation compressés, par exemple, en double-cliquant dessus. Ensuite, copiez les fichiers extraits dans un emplacement réseau auquel les ordinateurs clients peuvent accéder.

Les packages d'installation pour l'application de partage RMS prennent en charge différents scénarios de déploiement et incluent les éléments suivants :

|Description|Scénario de déploiement|
|---------------|-----------------------|
|Assistant de connexion Microsoft Online|Office 2010 et Azure RMS<br /><br />Office 2013 et Azure RMS si vous n’avez pas installé la [mise à jour du 9 juin 2015 pour Office 2013](https://support.microsoft.com/kb/3054853) (KB3054853)|
|Correctif pour Office (KB2596501)|Office 2010 et Azure RMS<br /><br />Office 2010 et Active Directory RMS|
|Correctif d'activation du client AD RMS 1.0 pour le travail avec Azure RMS (KB2843630)|Office 2010 et Azure RMS<br /><br />Office 2010 et Active Directory RMS|
|Client AD RMS et application de partage RMS|Office 2016 ou Office 2013 et Azure RMS ou Active Directory RMS<br /><br />Office 2010 et Azure RMS<br /><br />Office 2010 et Active Directory RMS<br /><br />Application de partage RMS et complément Office uniquement|
|Complément Office pour le ruban|Office 2016 ou Office 2013 et Azure RMS ou Active Directory RMS<br /><br />Office 2010 et Azure RMS<br /><br />Office 2010 et Active Directory RMS<br /><br />Application de partage RMS et complément Office uniquement|
|Outil de préparation Azure Active Directory Rights Management|Office 2010 et Azure RMS|
Utilisez les procédures suivantes afin d'identifier les commandes nécessaires au déploiement de l'application de partage RMS pour les scénarios de déploiement suivants :

-   **Office 2016 ou Office 2013 et Azure RMS ou Active Directory RMS**

    Vos utilisateurs exécutent Office 2016 ou Office 2013, votre organisation utilise Azure RMS ou Active Directory RMS et les utilisateurs collaborent avec d'autres organisations qui utilisent Azure RMS ou Active Directory RMS.

-   **Office 2010 et Azure RMS**

    Vos utilisateurs exécutent Office 2010, votre organisation utilise Azure RMS et les utilisateurs collaborent avec d'autres organisations qui utilisent Azure RMS ou Active Directory RMS.

-   **Office 2010 et Active Directory RMS**

    Vos utilisateurs exécutent Office 2010, votre organisation utilise AD RMS et les utilisateurs collaborent avec d'autres organisations qui utilisent Azure RMS.

-   **Application de partage RMS et complément Office uniquement**

    Vos utilisateurs exécutent Office 2016, Office 2013 ou Office 2010, votre organisation utilise AD RMS et les utilisateurs n'ont pas besoin de collaborer avec d'autres organisations qui utilisent Azure RMS. Cette installation vous permet d'installer uniquement l’application de partage et le complément Office.

> [!NOTE]
> Dans ces scénarios, si votre organisation exécute AD RMS, vos utilisateurs peuvent recevoir du contenu protégé d'autres organisations qui utilisent Azure RMS, mais ils ne peuvent pas envoyer du contenu protégé aux utilisateurs d'une organisation qui utilise Azure RMS. Toutefois, si votre organisation exécute Azure RMS, vos utilisateurs peuvent envoyer et recevoir du contenu protégé d'autres organisations.

Pour terminer l'installation relative à chaque procédure, vous devez redémarrer l'ordinateur. Vous pouvez lancer un redémarrage automatique à l’aide d’une commande, comme **shutdown /i**.

### Pour déployer l'application de partage RMS pour Office 2016 ou Office 2013 et Azure RMS ou Active Directory RMS

-   Sur chaque ordinateur sur lequel vous souhaitez installer l'application de partage RMS et les composants associés, exécutez la commande suivante avec des privilèges élevés :

    ```
    setup.exe /s
    ```

Pour vérifier que l’opération a réussi, consultez la section [Vérification de la réussite de l’installation](#verifying-installation-success) dans cet article.

### Pour déployer l'application de partage RMS pour Office 2010 et Azure RMS

1.  Vous devez être l'administrateur général de votre locataire Office 365 ou Azure Active Directory pour pouvoir obtenir l'URL du service de certification de votre organisation en exécutant l'outil de préparation Active Directory Azure Rights Management. Vous ne devez exécuter cet outil qu'une seule fois, sur un seul ordinateur. Vous allez utiliser l'URL du service de certification lors de l'installation de l'application de partage RMS sur chaque ordinateur :

    1.  Connectez-vous à un ordinateur à l'aide d'un compte d'administrateur local.

    2.  Sur cet ordinateur, [téléchargez et installez l'Assistant d'inscription en ligne Microsoft](http://www.microsoft.com/download/details.aspx?id=28177).

    3.  Exécutez la commande suivante pour afficher l'URL du service de certification à l'écran, que vous pouvez ensuite copier et enregistrer pour l'étape suivante :

        -   Pour Windows 8.1 et Windows 8, 64 bits :

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Pour Windows 8.1 et Windows 8, 32 bits :

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Pour Windows 7, 64 bits :

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > Cette commande peut vous inviter à entrer vos informations d'identification pour Azure. Si l'ordinateur n'est pas joint à un domaine, ces informations vous seront demandées. Si l'ordinateur est joint à un domaine, l'outil devrait pouvoir utiliser les informations d'identification mises en cache.

2.  Sur chaque ordinateur sur lequel vous allez installer l'application de partage RMS, exécutez la commande suivante avec des privilèges élevés :

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  Sur chaque ordinateur sur lequel vous allez installer l'application de partage RMS, les utilisateurs doivent exécuter la commande suivante (aucun besoin de privilèges élevés). Il existe différentes manières d'effectuer cette opération, y compris en demandant aux utilisateurs d'exécuter la commande (par exemple, un lien dans un message électronique ou un lien sur le portail du support technique), ou vous pouvez l'ajouter à leur script d'ouverture de session :

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

Pour vérifier que l’opération a réussi, consultez la section [Vérification de la réussite de l’installation](#verifying-installation-success) dans cet article.

### Pour déployer l'application de partage RMS pour Office 2010 et Active Directory RMS

1.  Sur chaque ordinateur sur lequel vous allez installer l'application de partage RMS, exécutez la commande suivante avec des privilèges élevés :

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  Sur chaque ordinateur sur lequel vous allez installer l'application de partage RMS, les utilisateurs doivent exécuter la commande suivante (aucun besoin de privilèges élevés). Il existe différentes manières d'effectuer cette opération, y compris en demandant aux utilisateurs d'exécuter la commande (par exemple, un lien dans un message électronique ou un lien sur le portail du support technique), ou vous pouvez l'ajouter à leur script d'ouverture de session :

    -   Pour Windows 10, Windows 8.1 et Windows 8, 64 bits :

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   Pour Windows 10, Windows 8.1 et Windows 8, 32 bits :

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   Pour Windows 7, 64 bits :

        ```
        x64\win7\aadrmpep.exe /configureO2010
        ```

Pour vérifier que l’opération a réussi, consultez la section [Vérification de la réussite de l’installation](#verifying-installation-success) dans cet article.

### Pour installer l'application de partage RMS et le complément Office uniquement

1.  Installez le client AD RMS et l'application de partage RMS en utilisant la commande suivante :

    -   Pour Windows 64 bits :

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   Pour Windows 32 bits :

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Exemple : `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Installez le complément Office à l’aide des commandes suivantes :

    -   Pour la version 64 bits d’Office :

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Pour la version 32 bits d’Office :

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    Exemple : `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

Pour vérifier que l’opération a réussi, consultez la section [Vérification de la réussite de l’installation](#verifying-installation-success) dans cet article.

## Vérification de la réussite de l'installation
Vous pouvez utiliser les fichiers journaux d'installation pour vérifier que l'installation a réussi.

### Pour vérifier la réussite de l'installation de l'application de partage RMS pour Office 2016 ou Office 2013 et Azure RMS ou Active Directory RMS

-   Pour vérifier que la commande Setup.exe a fonctionné sur chaque ordinateur, recherchez le fichier journal d’installation **RMInstaller.log** dans le dossier *%temp%\RMS_installer_&lt;guid&gt;*, puis identifiez le code de sortie.

    Une installation réussie a le code de sortie 0, et tout autre numéro indique l'échec de l'installation.

    Exemple de nom de fichier journal : **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

### Pour vérifier la réussite de l'installation de l'application de partage RMS pour Office 2010 et Azure RMS

1.  Pour vérifier que la commande Setup.exe a fonctionné sur chaque ordinateur, recherchez le fichier journal d’installation **RMInstaller.log** dans le dossier *%temp%\RMS_installer_&lt;guid&gt;*, puis identifiez le code de sortie.

    Une installation réussie a le code de sortie 0, et tout autre numéro indique l'échec de l'installation.

    Exemple de nom de fichier journal : **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Pour vérifier la réussite de la commande RMSSetup.exe, l’utilisateur doit avoir les fichiers suivants créés dans le dossier *%localappdata%\microsoft\drm* :

    -   CERT-ordinateur-2048.drm

    -   CERT-Machine.drm

    -   CLC-&#42;.drm

    -   GIC-&#42;.drm

    Exemple de fichier CLC-&#42;.drm :

    **CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf;k5b11;k4a10;kac15;k29b2b6980f4c}.drm**

### Pour vérifier la réussite de l'installation de l'application de partage RMS pour Office 2010 et Active Directory RMS

1.  Pour vérifier que la commande Setup.exe a fonctionné sur chaque ordinateur, recherchez le fichier journal d’installation dans le dossier *%temp%\RMS_installer_&lt;guid&gt;*, puis identifiez le code de sortie.

    Une installation réussie a le code de sortie 0, et tout autre numéro indique l'échec de l'installation.

    Exemple de nom de fichier journal : **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Pour vérifier la réussite de la commande aadrmprep.exe sur chaque ordinateur, recherchez le texte suivant dans le fichier journal d'installation : **aadrmprep.exe exited with status SUCCESS**

    > [!NOTE]
    > Dans certains cas, cette installation peut s'exécuter deux fois : la première échoue et la seconde réussit.

    Si vous souhaitez vérifier manuellement les modifications de registre effectuées par cet outil, les voici :

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationaccueilRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationaccueilRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @="&lt;certification url&gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser="&lt;default_user&gt;"

### Pour vérifier la réussite de l'installation de l'application de partage RMS et du complément Office uniquement

1.  Pour vérifier la réussite de la commande Setup_ipviewer.exe, recherchez le texte suivant dans le fichier journal d’installation : **Réussite de l’installation ou état d’erreur : 0**

    Exemples de lignes pour une installation réussie :

    **MSI (s) (F0:B8) [14:19:57:854]: Product: Active Directory Rights Management Services Client 2.1 -- Installation completed successfully.**

    **MSI (s) (F0:B8) [14:19:57:854]: Windows Installer installed the product. Product Name: Active Directory Rights Management Services Client 2.1. Product Version: 1.0.1179.1. Product Language: 1033. Fabricant : Microsoft Corporation. Installation success ou le errou le status: 0.**

2.  Pour vérifier la réussite du complément Office, recherchez le texte suivant dans le fichier journal d’installation : **Réussite de l’installation ou état d’erreur : 0**

    Exemples de lignes pour une installation réussie :

    **MSI (s) (9C:88) [18:49:04:007]: Product: Microsoft RMS Office Addins -- Installation completed successfully.**

    **MSI (s) (9C:88) [18:49:04:007]: Windows Installer installed the product. Product Name: Microsoft RMS Office Addins. Product Version: 1.0.7. Product Language: 1033. Fabricant : Microsoft. Installation success ou le errou le status: 0.**

## Commandes de désinstallation
Certaines des commandes d'installation requises pour ces déploiements ne prennent pas de commande de désinstallation en charge. Vous pouvez désinstaller le client AD RMS et l’application de partage et vous pouvez désinstaller le complément Office. Utilisez les commandes suivantes pour désinstaller ces éléments.

### Pour désinstaller le client AD RMS et l'application de partage RMS

-   Utilisez les commandes suivantes :

    -   Pour Windows 64 bits :

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   Pour Windows 32 bits :

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

### Pour désinstaller le complément Office

-   Utilisez les commandes suivantes :

    -   Pour la version 64 bits d’Office :

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   Pour la version 32 bits d'Office :

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

## Suppression des mises à jour automatiques
Par défaut, les utilisateurs sont avertis s'il existe une version ultérieure de l'application de partage RMS et sont invités à la télécharger. Vous pouvez supprimer cette notification en apportant la modification suivante au Registre :

1.  Accédez à **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** et, si elle n’est pas déjà présente, créez une clé nommée **RmsSharingApp**.

2.  Sélectionnez **RmsSharingApp**, créez une valeur DWORD de **AllowUpdatePrompt**et définissez la valeur sur **0**.

Étant donné que l'application de partage RMS n'est pas prise en charge par WSUS, vous pouvez utiliser la technique suivante pour tester les nouvelles versions de l'application de partage RMS avant de les déployer vers tous les utilisateurs :

1.  Sur les ordinateurs de tous les utilisateurs, exécutez un script pour supprimer les mises à jour automatiques. Sur les ordinateurs que les administrateurs utilisent pour tester les nouvelles versions, n'exécutez pas ce script.

2.  Lorsqu'une nouvelle version est disponible, les administrateurs la téléchargent et la testent.

3.  Quand le test est terminé et que les problèmes sont résolus, déployez la dernière version vers tous les utilisateurs à l'aide des instructions de déploiement automatique de ce guide.

## Azure RMS uniquement : configuration du suivi des documents
Si votre [abonnement prend en charge le suivi des documents](https://technet.microsoft.com/dn858608), le site de suivi des documents est activé par défaut pour tous les utilisateurs de votre organisation.  Le suivi des documents fournit des informations telles que les adresses de messagerie des personnes qui ont tenté d'accéder aux documents protégés que les utilisateurs ont partagés et indique quand ces personnes ont tenté d'y accéder, ainsi que leur emplacement. Si l’affichage de ces informations est interdit dans votre organisation pour des raisons de confidentialité, vous pouvez désactiver l’accès au site de suivi des documents à l’aide de l’applet de commande [Disable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032). Vous pouvez réactiver l’accès au site à tout moment en utilisant [Enable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037) et vérifier si l’accès est actuellement activé ou désactivé à l’aide de [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037).

Pour exécuter ces applets de commande, vous devez disposer au moins de la version **2.3.0.0** du module Azure RMS pour Windows PowerShell.  Pour obtenir des instructions d’installation, consultez [Installation de Windows PowerShell pour Azure Rights Management](../deploy-use/install-powershell.md).

> [!TIP]
> Si vous avez précédemment téléchargé et installé le module, vérifiez le numéro de version en exécutant la commande suivante : `(Get-Module aadrm –ListAvailable).Version`

Les URL suivantes sont utilisées pour le suivi des documents et doivent être autorisées (par exemple, ajoutez-les à vos sites approuvés si vous utilisez Internet Explorer avec sécurité renforcée) :

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > Cette URL est pour Bing Maps.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

## AD RMS uniquement : prise en charge de plusieurs domaines de messagerie au sein de votre organisation
Si vous utilisez les services AD RMS et que les utilisateurs de votre organisation disposent de plusieurs domaines de messagerie, suite à une fusion ou une acquisition par exemple, vous devez apporter la modification suivante au Registre :

1.  Accédez à **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** et, si elle n’est pas déjà présente, créez une clé nommée **RmsSharingApp**.

2.  Sélectionnez **RmsSharingApp**, créez une valeur de chaînes multiples nommée **FederatedDomains**, puis ajoutez les domaines et tous les sous-domaines utilisés par votre organisation. Les caractères génériques ne sont pas pris en charge.

    Par exemple : la société Coho Vineyard &amp; Winery dispose du domaine de messagerie standard **cohovineyardandwinery.com** mais, à la suite de fusions, elle utilise également les domaines de messagerie **cohowinery.com**, **eastcoast.cohowinery.com** et **cohovineyard**. Pour les données de valeur **FederatedDomains**, l’administrateur entre **cohowinery.com; eastcoast.cohowinery.com; cohovineyard**

Si vous n'apportez pas cette modification au Registre, les utilisateurs risquent de ne pas pouvoir consommer le contenu qui a été protégé par d'autres utilisateurs de leur organisation. Cette modification du Registre n'est pas nécessaire si vous utilisez Azure RMS.


## Étapes suivantes
Pour obtenir des informations techniques supplémentaires sur notamment la différence entre les niveaux de protection (native et générique), les types de fichiers pris en charge, les extensions de nom de fichier et la façon de modifier le niveau de protection par défaut, consultez [Présentation technique de l’application de partage Rights Management](sharing-app-admin-guide-technical.md).




<!--HONumber=Jun16_HO4-->

