---
title: Prévention des attaques par relecture en cas d'hébergement d'un service WCF dans une batterie de serveurs Web
ms.date: 03/30/2017
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
ms.openlocfilehash: b0e52624ef4483672abd8cd0995dbc2e58f95ca1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684864"
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>Prévention des attaques par relecture en cas d'hébergement d'un service WCF dans une batterie de serveurs Web
Lors de l'utilisation de la sécurité du message, WCF empêche toute attaque par relecture en créant une valeur à usage unique à partir du message entrant et en vérifiant le `InMemoryNonceCache` interne pour voir si la valeur à usage unique générée est présente. Si tel est le cas, le message est ignoré comme relecture. Lorsqu'un service WCF est hébergé dans une batterie de serveurs Web, étant donné que `InMemoryNonceCache` n'est pas partagé entre les nœuds de la batterie de serveurs Web, le service est vulnérable aux attaques par relecture.  Pour limiter ce risque, WCF 4.5 fournit un point d'extensibilité qui vous permet d'implémenter votre propre cache partagé de valeurs à usage unique en dérivant une classe de la classe abstraite <xref:System.ServiceModel.Security.NonceCache>.  
  
## <a name="noncecache-implementation"></a>Implémentation de NonceCache  
 Pour implémenter votre propre cache partagé de valeurs à usage unique, dérivez une classe de <xref:System.ServiceModel.Security.NonceCache> et substituez les méthodes <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> et <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A>. <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> vérifiera pour voir si la valeur à usage unique spécifiée existe dans le cache. <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> tente d'ajouter une valeur à usage unique au cache. Une fois que la classe est implémentée, vous l'accrochez en instanciant une instance et en l'assignant à <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> pour la détection de relecture côté client et à <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> pour la détection de relecture côté serveur. Il n’existe aucune prise en charge de configuration prête à l’emploi pour cette fonctionnalité.  
  
## <a name="see-also"></a>Voir aussi
- [Sécurité de message](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [SymmetricSecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)
