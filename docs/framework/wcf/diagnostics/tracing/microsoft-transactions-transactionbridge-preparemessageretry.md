---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: f168cb24d87f3159a1ea41003c2ffa7041ce8c09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710441"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a>Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
Une nouvelle tentative de message prepare a été envoyée à un participant qui ne répond pas.  
  
## <a name="description"></a>Description  
 Tracé si le gestionnaire de transactions local a dû renvoyer un message prepare à un participant subalterne parce qu'il n'a pas reçu de réponse dans une délai donné.  
  
## <a name="troubleshooting"></a>Résolution des problèmes  
 Recherchez d'éventuels problèmes liés au réseau ou au produit pouvant empêcher la réponse d'être remise à temps.  Si un nombre élevé de ces messages apparaissent, cela peut indiquer des problèmes d'infrastructure ou des délais de réponse anormalement longs. Ces deux problèmes peuvent réduire considérablement le débit des transactions au sein du système.  
  
## <a name="see-also"></a>Voir aussi
- [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)
