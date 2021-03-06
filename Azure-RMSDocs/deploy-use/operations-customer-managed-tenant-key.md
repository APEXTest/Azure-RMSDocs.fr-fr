---
title: "Gérée par le client : opérations de cycle de vie des clés de locataires AIP"
description: "Informations sur les opérations de cycle de vie applicables si vous gérez votre clé de locataire pour Azure Information Protection (dans le cadre d’un scénario BYOK, ou Bring Your Own Key)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: fa92a0f3179c884b7e5fc278525a471a27cb2a96
ms.lasthandoff: 02/24/2017


---


# <a name="customer-managed-tenant-key-lifecycle-operations"></a>Gérée par le client : opérations de cycle de vie des clés de locataires

>*S’applique à : Azure Information Protection, Office 365*

Si vous gérez votre clé de locataire pour Azure Information Protection (dans le cadre d’un scénario BYOK, ou Bring Your Own Key), utilisez les sections suivantes pour obtenir plus d’informations sur les opérations de cycle de vie qui s’appliquent à cette topologie.

## <a name="revoke-your-tenant-key"></a>Révocation de votre clé de locataire
Dans Azure Key Vault, vous pouvez modifier les autorisations sur le coffre de clés qui contient votre clé de locataire Azure Information Protection pour que le service Azure Rights Management ne puisse plus accéder à la clé. Cependant, si vous effectuez cette opération, personne ne peut ouvrir les documents et les e-mails que vous avez précédemment protégés à l’aide du service Azure Rights Management.

Quand vous annulez votre abonnement Azure Information Protection, Azure Information Protection arrête d’utiliser votre clé de locataire, et aucune action n’est nécessaire de votre part.


## <a name="re-key-your-tenant-key"></a>Renouvellement de votre clé de locataire
Le renouvellement de la clé est également appelé déploiement de la clé. Ne renouvelez pas votre clé de locataire à moins que ce soit vraiment nécessaire. Les clients plus anciens, tels qu’Office 2010, n’ont pas été conçus pour gérer naturellement les changements de clés. Dans ce scénario, vous devez effacer l’état Rights Management des ordinateurs à l’aide d’une stratégie de groupe ou d’un mécanisme similaire. Toutefois, certains événements légitimes peuvent vous obliger à renouveler votre clé de locataire. Par exemple :

-   Votre entreprise s'est divisée en deux sociétés distinctes ou plus. Lorsque vous renouvelez votre clé de locataire, la nouvelle société n'aura pas accès au nouveau contenu publié par vos employés. Elle pourra toujours accéder à l'ancien contenu si elle dispose d'une copie de l'ancienne clé de locataire.

-   Vous pensez que la copie principale de votre clé de locataire (celle en votre possession) a été compromise.

Lorsque vous renouvelez votre clé de locataire, le nouveau contenu est protégé à l'aide de la nouvelle clé de locataire. Vous obtenez ce résultat en plusieurs étapes. Ainsi, pendant un certain temps, certains nouveaux contenus continueront d'être protégés par l'ancienne clé de locataire. Le contenu précédemment protégé reste protégé par l'ancienne clé de locataire. Pour prendre en charge ce scénario, Azure Information Protection conserve votre ancienne clé de locataire afin de pouvoir émettre des licences pour l’ancien contenu.

Pour recréer votre clé de locataire, recréez d’abord votre clé de locataire Azure Information Protection dans Key Vault. Ensuite, exécutez l’applet de commande Add-AadrmKeyVaultKey en spécifiant l’URL de la nouvelle clé.

## <a name="backup-and-recover-your-tenant-key"></a>Sauvegarde et récupération de votre clé de locataire
Vous êtes responsable de la sauvegarde de votre clé de locataire. Si vous avez généré votre clé de locataire dans un module de sécurité matériel Thales, pour sauvegarder la clé, il vous suffit de sauvegarder le fichier de clé tokénisée, le fichier Word ainsi que les cartes Administrateur.

Comme vous avez transféré votre clé en suivant les procédures décrites dans la section [Implémentation de BYOK (Bring Your Own Key)](../plan-design/plan-implement-tenant-key.md#implementing-your-azure-information-protection-tenant-key) de l’article [Planification et implémentation de la clé de locataire Azure Rights Management](../plan-design/plan-implement-tenant-key.md), Key Vault conserve le fichier de clé tokenisée pour se protéger des défaillances des nœuds du service. Ce fichier est lié à la sécurité de l’instance ou de la région Azure spécifique. Cependant, il ne s'agit pas là d'une sauvegarde complète. Par exemple, si vous avez besoin d’une copie en texte brut de votre clé pour l’utiliser en dehors d’un HSM Thales, Azure Key Vault ne peut pas la récupérer à votre place, car il a seulement une copie non récupérable.

## <a name="export-your-tenant-key"></a>Exportation de votre clé de locataire
Si vous utilisez BYOK, vous ne pouvez pas exporter votre clé de locataire à partir d’Azure Key Vault ou d’Azure Information Protection. La copie dans Azure Key Vault est non récupérable. 

## <a name="respond-to-a-breach"></a>Réponse à une violation
Un système de sécurité est incomplet sans un processus de réponse aux violations. Votre clé de locataire peut être compromise ou volée. Même si elle est bien protégée, des vulnérabilités peuvent être détectées dans la technologie actuelle du module de sécurité matériel (HSM), ou dans les longueurs et les algorithmes des clés.

Microsoft dispose d'une équipe chargée de répondre aux incidents de sécurité survenant dans ses produits et services. Dès la réception d'un rapport d'incident avéré, cette équipe met tout en œuvre pour analyser la portée, la cause première et les actions de correction à mettre en place. Si ces incidents affectent vos ressources, Microsoft envoie une notification par e-mail (à l’adresse fournie lors de la création de l’abonnement) aux administrateurs de votre locataire Azure Information Protection.

En cas de violation, la meilleure mesure que vous ou Microsoft puissiez prendre dépend de la portée de la violation. Microsoft vous accompagnera dans ce processus. Le tableau suivant présente des situations type et les réponses que vous pouvez mettre en place. Toutefois, la réponse exacte que vous apporterez dépendra des informations obtenues lors de l'analyse.

|Description de l'incident|Réponse possible|
|------------------------|-------------------|
|Votre clé de locataire a fait l'objet d'une fuite.|Renouvelez votre clé de locataire. Consultez [Renouvellement de votre clé de locataire](#re-key-your-tenant-key).|
|Une personne non autorisée ou un programme malveillant a obtenu le droit d'utiliser votre clé de locataire, sans que celle-ci ait fait l'objet d'une fuite.|Dans ce cas, le renouvellement de votre clé de locataire ne sera pas utile et une analyse de la cause première sera obligatoire. Si un bogue au niveau d'un processus ou d'un logiciel est responsable de l'accès de l'individu non autorisé, cette situation doit être résolue.|
|Vulnérabilité détectée dans la technologie HSM actuelle.|Microsoft doit mettre à jour les modules de sécurité matériels. S'il y a des raisons de penser que les clés ont été exposées via cette vulnérabilité, Microsoft demandera à tous les clients de renouveler leur clé de locataire.|
|Une vulnérabilité a été découverte dans l'algorithme RSA ou la longueur de la clé, ou des attaques en force brute peuvent être envisagées au niveau informatique.|Microsoft doit mettre à jour Azure Key Vault ou Azure Information Protection pour prendre en charge de nouveaux algorithmes et des clés plus longues qui sont résilientes. Elle doit également indiquer à tous les clients qu’ils doivent renouveler leur clé de locataire.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


