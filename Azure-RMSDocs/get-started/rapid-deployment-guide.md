---
title: "Guide de déploiement rapide pour Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c994d616-cff6-4930-9228-a7f7d198a160
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed50d87138c428fadfd22cd5b3ef3c7f7e421848
ms.openlocfilehash: 01c2436218e0d7fd80a31cdc037d9dc8933e42f2


---

# Guide de déploiement rapide pour Azure Rights Management

*S’applique à : Azure Rights Management, Office 365*

Utilisez ce guide en complément des informations de configuration fournies dans la section **Déployer et utiliser** pour vous aider à déployer et à utiliser rapidement Azure Rights Management (Azure RMS) en choisissant dans une liste de scénarios spécifiques à implémenter.

Ces scénarios contiennent des instructions destinées aux administrateurs et une documentation associée à l’adresse des utilisateurs finaux. Avant de fournir la documentation (instructions ou annonces) à vos utilisateurs finaux, vous devez la personnaliser en fonction de vos besoins et des flux de travail existants. Un exemple d’instructions ou d’annonce montre à quoi peut ressembler la documentation destinée aux utilisateurs finaux.

Chaque scénario comporte une liste d’exigences et des liens vers des informations supplémentaires qui vous aideront à déployer ces solutions indépendamment et dans n’importe quel ordre.

Les scénarios répertoriés ici sont un échantillon des plus populaires. Azure RMS pouvant servir à protéger des informations dans un grand nombre de scénarios à la fois au sein d’une organisation et parmi plusieurs organisations, vous pouvez définir vos propres scénarios et les déployer dans votre environnement et pour vos utilisateurs à l’aide de ce même modèle. En se concentrant sur des scénarios spécifiques, votre déploiement d’Azure RMS répondra au mieux à vos objectifs professionnels. De plus, d’après notre expérience, les utilisateurs ont tendance à suivre les instructions spécifiques à un scénario beaucoup plus étroitement et systématiquement que des conseils généraux tels que « protéger les documents sensibles ».

Avant de déployer ces solutions, vous souhaiterez peut-être envoyer une annonce aux utilisateurs finaux pour leur signaler que certains changements vont avoir lieu pour aider à protéger les données de l’entreprise, et qu’ils seront peut-être mis à contribution. Un exemple d’annonce est fourni après le tableau suivant.

> [!NOTE]
> Si vous avez des questions et des commentaires concernant ce guide, utilisez les mécanismes de commentaires indiqués sur cette page ou envoyez un e-mail à [AskIPTeam@Microsoft.com](mailto:%20askipteam@microsoft.com?subject=Rapid%20Deployment%20Guide%20feedback).

## Scénarios pour Azure RMS
Pour vous aider à déployer rapidement Azure RMS pour résoudre des problèmes spécifiques, choisissez les scénarios qui correspondent le plus à vos objectifs commerciaux et adaptez-les si nécessaire.



**Envoyer en toute sécurité par e-mail un fichier Office à des utilisateurs d’une autre organisation, en ayant la possibilité de suivre les accès ultérieurs (collaboration interentreprises)**

Exemples :

- Envoyer une liste de prix, une feuille de route ou un calendrier de publication à un client

- Envoyer un ordre de fabrication ou des spécifications marketing à un fournisseur

- Envoyer une offre ou une demande de devis à un partenaire

Voir : [Scénario : partager un fichier Office avec des utilisateurs d’une autre organisation](scenario-share-office-file-externally.md)

**S’assurer que les documents stockés dans une bibliothèque SharePoint restent sous votre contrôle**

Exemples :

- Rapports et feuilles de calcul par service

- Collaboration entre les équipes pour des documents de conception ou autres éléments livrables

Voir : [Scénario : conserver le contrôle des documents stockés dans SharePoint](scenario-sharepoint.md)

**Des cadres peuvent échanger des informations confidentielles en toute sécurité par e-mail**

Exemples :

- Partage de projets d'acquisition

- Examen ou diffusion de problèmes juridiques

- Informations sur des licenciements potentiels ou d'autres sujets sensibles

Voir : [Scénario - Des cadres échangent des informations confidentielles](scenario-executives-email.md)

**Protéger automatiquement tous les fichiers sur un serveur de fichiers**

Exemples :

- Documents CAO qui doivent être conservés en interne pour éviter la perte de propriété intellectuelle

- Plans de promotion marketing et dates qui doivent être tenus secrets pour éviter toute divulgation et conserver un avantage concurrentiel

Voir : [Scénario - Protéger les fichiers situés sur un partage de serveur de fichiers](scenario-fci.md)

**Protéger étroitement vos documents professionnels les plus confidentiels et importants**

Exemples :

- Informations relatives à des recettes ou formules uniques à votre entreprise

- Plans de fusion ou d’acquisition hautement confidentiels

- Données d’exploration de ressources naturelles

Voir : [Scénario - Sécuriser vos fichiers les plus précieux](scenario-secure-most-valuable-files.md)

**Envoyer en toute sécurité des e-mails et des pièces jointes confidentiels**

Exemples :

- Énoncé de vision d’entreprise

- Organigrammes, informations relatives à des réorganisations ou annonces de promotion

- Informations relatives aux stratégies d’entreprise

Voir : [Scénario - Envoyer un e-mail confidentiel de l’entreprise](scenario-company-confidential-email.md)

**Appliquer une protection permanente aux fichiers Office dans les dossiers de travail**

Exemples :

- Documents Word modifiés localement pour un projet confidentiel de l’entreprise

- Feuilles de calcul créées localement qui contiennent des données sensibles ou à impact commercial élevé

- Présentations PowerPoint relatives à des projets en cours et stockées localement, qui doivent être protégées contre toute fuite ou partage accidentel avec des personnes extérieures à l’organisation tant que les présentations ne sont pas définitives

Voir : [Scénario - Configurer des dossiers de travail pour la protection permanente](scenario-work-folders.md)




## Annonce pour les utilisateurs avant le déploiement
Vous pouvez utiliser l’exemple de message de communication suivant pour signaler aux utilisateurs que le déploiement d’Azure RMS va impliquer certains changements. Copiez et collez le texte suivant, et faites-le envoyer par e-mail à tous les utilisateurs par un membre de l’équipe dirigeante de votre organisation, de préférence le Directeur général. Apportez au texte toute modification susceptible de le rendre plus pertinent pour vos utilisateurs et votre organisation.

![Exemple de bannière de documentation utilisateur pour un déploiement rapide Azure RMS](../media/AzRMS_ExampleBanner.png)

### Modifications que nous apportons pour protéger nos données
Avez-vous déjà souhaité bloquer l’accès à un document envoyé par erreur à vos partenaires ? Vous êtes-vous déjà demandé s’il existait un moyen de savoir lesquels de vos clients avaient lu les dernières nouveautés sur les produits que vous leur aviez envoyées ? Souhaiteriez-vous pouvoir partager des informations de produits confidentielles sans risquer qu’elles soient transférées à des personnes qui ne doivent pas les voir ?

Vous pourrez bientôt bénéficier de toutes ces fonctionnalités, car le service Informatique va déployer des modifications qui implémentent Microsoft Azure Rights Management (Azure RMS) comme solution de protection des données d’entreprise. Une grande partie de ces modifications appliqueront automatiquement la protection dont nous avons besoin, sans que vous ayez à faire quoi que ce soit de différent. En revanche, certaines modifications pourront nécessiter un comportement différent de votre part. Dans ce cas, le service Informatique vous enverra des informations et des instructions, et vous pourrez bénéficier d’une aide de la part du Support technique en cas de question ou de problème.

Par exemple, pour effectuer le suivi (et, si nécessaire, la révocation) des documents que vous partagez, vous utiliserez le site de suivi des documents :

![Captures d’écran de suivi de documents Azure RMS](../media/AzRMS_Tutorial_5_Screenshots.png)

Pour obtenir un aperçu de son fonctionnement, regardez cette vidéo de deux minutes : [Suivi et révocation de documents Azure RMS](https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

Les données (celles que nous générons, stockons et utilisons au quotidien) sont l’une des ressources les plus précieuses de cette organisation. Ce sont elles qui nous procurent un avantage concurrentiel et contribuent à notre succès. C’est pourquoi il est si important que nous conservions le contrôle de nos données et veillions à ce que les utilisateurs non autorisés ne puissent pas y accéder.

Les solutions que nous implémentons nous aideront à protéger nos données les plus précieuses et vous donneront les outils nécessaires pour conserver le contrôle de ces données. Nous vous remercions de votre collaboration pendant l’implémentation de ces modifications.




<!--HONumber=Jun16_HO4-->

