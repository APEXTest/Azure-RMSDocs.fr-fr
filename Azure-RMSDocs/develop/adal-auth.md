---
title: "Configuration de votre application pour l’authentification ADAL | Microsoft Docs"
description: "Étapes de configuration de l&quot;application Azure Information Protection pour utiliser l’authentification Azure ADAL"
keywords: authentification, RMS, ADAL, protection des informations,
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7415265d0e27896df2bdf6a62e7c875ba681345
ms.openlocfilehash: d51730af8a1f410ad890087200f64864eceb2268


---

# <a name="configure-your-app-for-adal-authentication"></a>Configuration de votre application pour l’authentification ADAL

Cette rubrique décrit les étapes de configuration de votre application pour l’authentification basée sur Azure Active Directory Authentication Library (ADAL).

## <a name="azure-authentication-setup"></a>Configuration de l’authentification Azure

Vous avez besoin des éléments suivants :

- Un [abonnement à Microsoft Azure](https://azure.microsoft.com/en-us/) (une version d’évaluation gratuite suffit). Pour plus d’informations, consultez [Inscription à RMS for Individuals](../understand-explore/rms-for-individuals-user-sign-up.md)
- Un abonnement à Microsoft Azure Rights Management (un compte [RMS for Individuals](https://technet.microsoft.com/en-us/library/dn592127.aspx) gratuit suffit).

> [!NOTE]
> Vérifiez auprès de votre administrateur informatique si vous avez un abonnement Microsoft Azure Rights Management et demandez-lui d’effectuer les étapes ci-dessous. Si votre organisation n’a pas d’abonnement, demandez à votre administrateur informatique d’en créer un. En outre, votre administrateur informatique doit s’abonner avec un *compte professionnel ou scolaire*, et non un *compte Microsoft* (tel que Hotmail).

Après vous être inscrit à Microsoft Azure :

- Connectez-vous au [portail de gestion Azure](https://manage.windowsazure.com) de votre organisation à l’aide d’un compte disposant de privilèges d’administrateur.

![Connexion Azure](../media/AzurePortalLogin.png)

- Naviguez jusqu’à l’application **Active Directory** sur le côté gauche du portail.

![Sélectionnez Active Directory](../media/AzureADPick.png)

- Si vous n’avez pas encore créé d’annuaire, cliquez sur le bouton **Nouveau** dans le coin inférieur gauche du portail.

![Sélectionnez NOUVEAU](../media/AzureNewBtn.png)

- Sélectionnez l’onglet **Rights Management** et vérifiez que **Statut de Rights Management** est **Actif**, **Inconnu** ou **Non autorisé**. Si le statut est **Inactif**, cliquez sur le bouton **Activer** situé en bas au milieu du portail et confirmez votre sélection.

![Choisissez ACTIVER](../media/RMTab.png)

- Maintenant, créez une *Application native* dans votre annuaire en le sélectionnant et en choisissant Applications.

![Sélectionnez APPLICATIONS](../media/CreateNativeApp.png)

- Ensuite, cliquez sur le bouton **Ajouter** situé dans la partie inférieure et centrale du portail.

![Sélectionnez AJOUTER](../media/AddAppBtn.png)

- À l’invite, choisissez **Ajouter une application développée par mon organisation**.

![Sélectionnez Ajouter une application développée par mon organisation](../media/AddAnAppPick.png)

- Nommez votre application en sélectionnant **APPLICATION CLIENTE NATIVE** et en cliquant sur le bouton **Suivant**.

![Nommez votre application](../media/TellUsInput.png)

- Ajoutez une URI de redirection et cliquez sur Suivant.
  L’URI de redirection doit être un URI valide et unique dans votre annuaire. Par exemple, vous pouvez utiliser quelque chose comme `com.mycompany.myapplication://authorize`.

![Ajoutez un URI de redirection](../media/RedirectURI.png)

- Sélectionnez votre application dans l’annuaire et choisissez **CONFIGURER**.

![Choisissez CONFIGURER](../media/ConfigYourApp.png)

>[!NOTE]
> Copiez l’**ID CLIENT** et l’**URI de redirection** et stockez-les pour une utilisation ultérieure lors de la configuration du client RMS.

- Accédez au bas de vos paramètres d’application et cliquez sur le bouton **Ajouter une application** sous **Autorisations pour d’autres applications**.

>[!NOTE]
> Les **autorisations déléguées** affichées pour Microsoft Azure Active Directory sont correctes par défaut : une seule option doit être sélectionnée et cette option est **Activer la connexion et lire le profil utilisateur**.

![Sélectionnez Ajouter une application](../media/PermissionsToOtherBtn.png)

- Cliquez sur le signe plus (+) situé en regard de **Microsoft Rights Management**.

![Sélectionnez le bouton +](../media/ChoosePlusBtn.png)

- Maintenant, cliquez sur la coche située dans le coin inférieur gauche de la boîte de dialogue.

![Cliquez sur la coche](../media/choosecheck01.png)

- Vous êtes maintenant prêt à ajouter une dépendance à votre application pour Azure RMS. Pour ajouter la dépendance, sélectionnez la nouvelle entrée **Microsoft Rights Management Services** sous **Autorisations pour d’autres applications** et cochez la case **Créer et accéder au contenu protégé pour les utilisateurs** dans la liste déroulante **Autorisations déléguées**.

![Configurez les autorisations](../media/AddDependency.png)

- Enregistrez votre application pour conserver les modifications en cliquant sur l’icône **Enregistrer** située en bas au milieu du portail.

![Sélectionnez ENREGISTRER](../media/SaveApplication.png)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


