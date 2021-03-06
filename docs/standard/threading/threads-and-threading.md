---
title: Threads et threading
ms.date: 11/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET]
- threading [.NET], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 095bd92921c9cd54d3a7d97ed07b35526b85c57f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147676"
---
# <a name="threads-and-threading"></a>Threads et threading

Le multithreading vous permet d’accélérer la réactivité de votre application et, si votre application s’exécute sur un système multiprocesseur ou multicœur, d’accélérer son débit.

## <a name="processes-and-threads"></a>Processus et threads

Un *processus* est un programme d’exécution. Un système d’exploitation utilise des processus pour séparer les applications qui sont en cours d’exécution. Un *thread* est l’unité de base à laquelle un système d’exploitation alloue du temps processeur. Chaque thread a une [priorité de planification](scheduling-threads.md) et maintient un ensemble de structures utilisé par le système pour enregistrer le contexte du thread quand l’exécution du thread est en pause. Le contexte du thread comprend toutes les informations dont le thread a besoin pour reprendre l’exécution sans interruption, notamment son ensemble de registres de CPU et de pile. Plusieurs threads peuvent s’exécuter dans le contexte d’un processus. Tous les threads d’un processus partagent son espace d’adressage virtuel. Un thread peut exécuter n’importe quelle partie du code du programme, y compris les parties exécutées par un autre thread.

> [!NOTE]
> Le .NET Framework fournit un moyen d’isoler les applications dans un processus à l’aide de *domaines d’application*. (Les domaines d’application ne sont pas disponibles sur .NET Core.) Pour plus d’informations, consultez la section [Domaines d’application et threads](../../framework/app-domains/application-domains.md#application-domains-and-threads) de l’article [Domaines d’application](../../framework/app-domains/application-domains.md).

Par défaut, un programme .NET est démarré avec un thread unique, souvent appelé thread *principal*. Toutefois, il peut créer des threads supplémentaires pour exécuter du code en parallèle ou en même temps que le thread principal. Ces threads sont souvent appelés threads *de travail*.

## <a name="when-to-use-multiple-threads"></a>Quand utiliser plusieurs threads

Vous pouvez utiliser plusieurs threads pour accélérer la réactivité de votre application et tirer parti d’un système multiprocesseur ou multicœur pour accélérer son débit.

Imaginez une application de bureau dans laquelle le thread principal est responsable des éléments d’interface utilisateur et répond aux actions des utilisateurs. Utilisez des threads de travail pour effectuer des opérations longues qui, sinon, occuperaient le thread principal et rendraient l’interface utilisateur non réactive. Vous pouvez aussi utiliser un thread dédié pour que la communication réseau ou des appareils soit plus réactive aux messages ou événements entrants.

Si votre programme procède à des opérations pouvant être effectuées en parallèle, la durée totale d’exécution peut être raccourcie en effectuant ces opérations dans des threads distincts et en exécutant le programme sur un système multiprocesseur ou multicœur. Sur un tel système, l’utilisation du multithreading peut accélérer le débit et la réactivité.

## <a name="how-to-use-multithreading-in-net"></a>Comment utiliser le multithreading dans .NET

À compter de .NET Framework 4, la méthode recommandée pour utiliser le multithreading consiste à utiliser la [bibliothèque parallèle de tâches (TPL)](../parallel-programming/task-parallel-library-tpl.md) et [Parallel LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md). Pour plus d’informations, consultez [Programmation parallèle](../parallel-programming/index.md).

La bibliothèque TPL et PLINQ reposent sur les threads <xref:System.Threading.ThreadPool>. La classe <xref:System.Threading.ThreadPool?displayProperty=nameWithType> fournit une application .NET avec un pool de threads de travail. Vous pouvez aussi utiliser des threads de pool de threads. Pour plus d’informations, consultez [Pool de threads managé](the-managed-thread-pool.md).

Enfin, vous pouvez utiliser la classe <xref:System.Threading.Thread?displayProperty=nameWithType> qui représente un thread managé. Pour plus d’informations, consultez [Utilisation de threads et de threading](using-threads-and-threading.md).

Plusieurs threads peuvent avoir besoin d’accéder à une ressource partagée. Pour garder la ressource dans un état non endommagé et éviter des conditions de concurrence, vous devez synchroniser l’accès des threads à cette ressource. Vous voudrez peut-être aussi coordonner l’interaction de plusieurs threads. .NET fournit un éventail de types que vous pouvez utiliser pour synchroniser l’accès à une ressource partagée ou coordonner l’interaction des threads. Pour plus d’informations, consultez [Vue d’ensemble des primitives de synchronisation](overview-of-synchronization-primitives.md).

Ne gérez pas les exceptions dans les threads. Les exceptions non gérées dans les threads entraînent généralement la fin du processus. Pour plus d’informations, consultez [Exceptions dans les threads managés](exceptions-in-managed-threads.md).

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités et objets de threading](threading-objects-and-features.md)
- [Bonnes pratiques de threading managé](managed-threading-best-practices.md)
- [Traitement parallèle, accès concurrentiel et programmation asynchrone dans .NET](../parallel-processing-and-concurrency.md)
- [À propos des processus et des threads](/windows/desktop/procthread/about-processes-and-threads)