---
title: 'Comment : mesurer les performances de requêtes PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd9e3a0ead62450e87225212f4fc6ecec6ec9489
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45749107"
---
# <a name="how-to-measure-plinq-query-performance"></a>Comment : mesurer les performances de requêtes PLINQ
Cet exemple montre comment utiliser la classe <xref:System.Diagnostics.Stopwatch> pour mesurer le temps nécessaire à l’exécution d’une requête PLINQ.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise une boucle `foreach` vide (`For Each` en Visual Basic) pour mesurer le temps nécessaire à l’exécution de la requête. Dans le code réel, la boucle contient généralement des étapes de traitement supplémentaires qui s’ajoutent à la durée d’exécution totale de la requête. Notez que le chronomètre est démarré juste avant la boucle qui marque le début d’exécution de la requête. Si vous avez besoin de mesures plus poussées, vous pouvez utiliser la propriété `ElapsedTicks` au lieu de `ElapsedMilliseconds`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 La durée d’exécution totale est une mesure utile lorsque vous expérimentez des implémentations de requête, même si elle ne donne pas toujours tous les détails. Utilisez le visualiseur concurrentiel pour avoir une vision plus approfondie et plus riche de l’interaction des threads de requête entre eux et avec d’autres processus en cours d’exécution. Pour plus d’informations, consultez [Visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
