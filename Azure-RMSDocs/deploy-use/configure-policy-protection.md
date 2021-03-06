---
title: "Configurer une étiquette Azure Information Protection à des fins de protection"
description: "Vous pouvez protéger vos documents et e-mails les plus sensibles lorsque vous configurez une étiquette, de façon à utiliser la protection offerte par Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: 5bc117cbff3226a2ee0ff375f0aa02fc3232a183
ms.openlocfilehash: ed6bd63a945b73b792bcafcdc0d07e08e83fc344
ms.lasthandoff: 02/27/2017


---

# <a name="how-to-configure-a-label-for-rights-management-protection"></a>Comment configurer une étiquette pour la protection offerte par Rights Management

>*S’applique à : Azure Information Protection*

Vous pouvez protéger vos documents et e-mails les plus sensibles à l’aide d’un service Rights Management qui utilise des stratégies de chiffrement, d’identité et d’autorisation pour éviter la perte de données. Cette protection est appliquée lorsque vous configurez une étiquette de manière à utiliser un modèle Rights Management pour les documents et e-mails, ou l’option **Ne pas transférer** pour les messages électroniques de Microsoft Outlook. 

Il peut s’agir de l’un des modèles par défaut créés automatiquement lorsque vous activez Azure Rights Management, ou d’un modèle personnalisé. Les modèles pour services Azure Rights Management sont pris en charge, mais appliquent la protection uniquement lorsque l’auteur du document ou de l’e-mail figure dans l’étendue configurée du modèle. Si l’utilisateur n’y figure pas, il reçoit un message indiquant qu’Azure Information Protection ne peut pas appliquer l’étiquette.

## <a name="how-the-protection-works"></a>Fonctionnement de la protection

Quand un document ou un e-mail est protégé par Rights Management, il est chiffré au repos et en transit et peut uniquement être déchiffré par les utilisateurs autorisés. Ce chiffrement est conservé avec le document ou l’e-mail, même si ce dernier est renommé. En outre, vous pouvez configurer des droits d’utilisation et des restrictions, comme dans les exemples suivants :

- Seuls les utilisateurs de votre organisation peuvent ouvrir le document ou l’e-mail confidentiel de l’entreprise.

- Seuls les utilisateurs du service marketing peuvent modifier et imprimer le document ou l’e-mail d’annonce de la promotion. Tous les autres utilisateurs de votre organisation peuvent uniquement lire le document ou l’e-mail.

- Les utilisateurs ne peuvent pas transférer un e-mail qui contient des informations sur une réorganisation interne.

- Il est impossible d’ouvrir la liste de prix actuelle envoyée à des partenaires commerciaux après une date spécifiée.

Pour plus d’informations sur les modèles Azure Rights Management et la façon de configurer ces droits et ces restrictions d’utilisation, consultez [Configuration de modèles personnalisés pour le service Azure Rights Management](../deploy-use/configure-custom-templates.md).

Pour plus d’informations sur Azure Rights Management et son fonctionnement, consultez [Qu'est-ce qu'Azure Rights Management ?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Pour configurer une étiquette pour appliquer la protection Azure Rights Management, le service Azure Rights Management doit être activé pour votre organisation. Si vous ne le n’avez pas déjà fait, consultez [Activation d'Azure Rights Management](../deploy-use/activate-service.md).

Exchange ne doit pas être configuré pour IRM (Information Rights Management, Gestion des droits relatifs à l'information) avant que les utilisateurs ne puissent appliquer des étiquettes dans Outlook pour protéger leurs e-mails. Toutefois, vous n’obtiendrez pas toutes les fonctionnalités de la protection Azure Rights Management avec Exchange jusqu'à ce qu’Exchange soit configuré pour IRM. Par exemple, les utilisateurs ne seront pas en mesure d’afficher des e-mails protégés sur un téléphone mobile ou Outlook Web Access. Les e-mails protégés ne peuvent pas être indexés pour la recherche, et vous ne pourrez pas configurer DLP Exchange Online pour la protection Rights Management. Consultez les ressources suivantes pour configurer Exchange de manière à prendre en charge ces scénarios supplémentaires :

- Pour Exchange Online, consultez les instructions figurant dans [Exchange Online : configuration de la gestion des droits relatifs à l'information](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Pour Exchange sur site, vous devez déployer le [connecteur RMS et configurer vos serveurs Exchange](../deploy-use/deploy-rms-connector.md). 


## <a name="to-configure-a-label-for-rights-management-protection"></a>Configurer une étiquette pour la protection Rights Management

1. Si ce n’est déjà fait, ouvrez une nouvelle fenêtre de navigateur et connectez-vous au [portail Azure](https://portal.azure.com) en tant qu’administrateur général, puis accédez au panneau **Azure Information Protection**. 

    Par exemple, dans le menu du hub, cliquez sur **Autres services** et commencez à taper **Information** dans la zone Filtrer. Sélectionnez **Azure Information Protection**.

2. Si l’étiquette à configurer s’applique à tous les utilisateurs, sélectionnez **Global** dans le panneau **Azure Information Protection**. Par contre, si l’étiquette à configurer se trouve dans une [stratégie délimitée](configure-policy-scope.md) pour qu’elle s’applique uniquement aux utilisateurs sélectionnés, choisissez plutôt la stratégie délimitée en question.

3. Dans le panneau **Stratégie**, sélectionnez l’étiquette que vous souhaitez configurer. Le panneau **Étiquette** s’ouvre. 

4. Dans le panneau **Étiquette**, recherchez la zone **Définir des autorisations pour les documents et les e-mails contenant cette étiquette** et sélectionnez l’une des options suivantes.
    
    - **Non configuré** : sélectionnez cette option si l’étiquette est actuellement configurée pour appliquer la protection et que vous ne voulez plus qu’elle le fasse. Passez ensuite à l’étape 10.
    
    - **Protéger** : sélectionnez cette option pour appliquer la protection, puis passez à l’étape 5.
    
    - **Supprimer la protection** : sélectionnez cette option pour supprimer la protection si elle est configurée pour un document ou un e-mail. Passez ensuite à l’étape 10.
        
        Remarque : les utilisateurs doivent disposer des autorisations nécessaires pour pouvoir supprimer la protection Rights Management et appliquer une étiquette associée à cette option. Cette option implique que l’utilisateur dispose du [droit d’utilisation](../deploy-use/configure-usage-rights.md) **Exporter** ou **Contrôle total**, ou qu’il soit propriétaire de Rights Management (ce qui accorde automatiquement le droit d’utilisation Contrôle total), ou encore qu’il soit un [super utilisateur dans Azure Rights Management](../deploy-use/configure-super-users.md). Les modèles Azure Rights Management par défaut n’incluent pas les droits d’utilisation qui permettent aux utilisateurs de supprimer la protection. 
        
        Si les utilisateurs ne disposent pas des autorisations nécessaires pour supprimer la protection Rights Management et qu’ils sélectionnent une étiquette configurée avec l’option **Supprimer la protection**, ils reçoivent le message suivant : **Azure Information Protection ne peut pas appliquer cette étiquette. Si le problème persiste, contactez votre administrateur.**

5. Si vous avez sélectionné **Protéger**, sélectionnez maintenant **Protection** pour ouvrir le panneau **Protection** :
    
    ![Configurer la protection d’une étiquette Azure Information Protection](../media/info-protect-protection-bar.png)

6. Dans le panneau **Protection**, sélectionnez **Azure RMS** ou **HYOK (AD RMS)**. 
    
    Dans la plupart des cas, vous devrez sélectionner **Azure RMS** pour vos paramètres d’autorisation. Ne sélectionnez **HYOK (AD RMS)** que si vous avez lu et compris les prérequis et les restrictions qui accompagnent cette configuration « *conservez votre propre clé* » (HYOK, hold your own key). Pour plus d’informations, consultez [HYOK (conservez votre propre clé) : exigences et restrictions pour la protection AD RMS](configure-adrms-restrictions.md). Pour poursuivre la configuration de la fonction HYOK (AD RMS), passez à l’étape 9.
    
7. Sélectionnez **Ne pas transférer** si vous voulez définir cette option Outlook pour les e-mails ou **Sélectionner un modèle**. 
    
8. Si vous avez sélectionné **Sélectionner un modèle** pour **Azure RMS**, cliquez sur la zone de liste déroulante et sélectionnez le [modèle](../deploy-use/configure-custom-templates.md) à utiliser pour protéger les documents et les e-mails avec cette étiquette.
    
    Si vous sélectionnez un **modèle de service** ou que vous avez configuré des [contrôles d’intégration](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) :
    
    - Les utilisateurs en dehors de l’étendue configurée du modèle ou qui sont exclus de l’application de la protection d’Azure Rights Management continuent de voir l’étiquette, mais ne peuvent pas l’appliquer. S’ils sélectionnent l’étiquette, ils voient le message suivant : **Azure Information Protection ne peut pas appliquer cette étiquette. Si le problème persiste, contactez votre administrateur.**
    
        Notez que tous les modèles sont toujours affichés, même si vous configurez une stratégie délimitée. Par exemple, vous configurez une stratégie délimitée au groupe Marketing. Les modèles Azure RMS que vous pouvez sélectionner ne se limitent pas aux modèles délimités au groupe Marketing et il est possible de sélectionner un modèle de service que les utilisateurs sélectionnés ne peuvent pas utiliser. Pour faciliter la configuration et minimiser la résolution des problèmes, envisagez d’attribuer le même nom au modèle de service et à l’étiquette de votre stratégie délimitée. 
            
9. Si vous avez sélectionné **Sélectionner un modèle** pour **HYOK (AD RMS)** : indiquez le GUID du modèle et l’URL de licence de votre cluster AD RMS. [Plus d’informations](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

10. Cliquez sur **Terminé** pour fermer le panneau **Protection** et voir apparaître la valeur que vous avez choisie pour **Ne pas transférer** ou le modèle que vous avez sélectionné pour l’option **Protection** dans le panneau **Étiquette**.

10. Dans le panneau **Étiquette**, cliquez sur **Enregistrer**.

11. Pour que les utilisateurs puissent voir ces modifications, cliquez dans le panneau **Azure Information Protection** sur **Publier**.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la configuration de votre stratégie Azure Information Protection, utilisez les liens figurant dans la section [Configuration de la stratégie de votre organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
