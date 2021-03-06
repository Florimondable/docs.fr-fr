---
title: Architecture logique et architecture physique
description: Comprendre les différences entre l’architecture logique et l’architecture physique.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: e8ed375899637d06db8eb9b12a0e1cb0c05591f9
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129920"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Architecture logique et architecture physique

Il est utile, à ce stade, de s’arrêter et d’expliquer en quoi l’architecture logique et l’architecture physique sont différentes, et de voir comment cela s’applique à la conception des applications basées sur des microservices.

Pour commencer, notez que la création de microservices ne nécessite l’utilisation d’aucune technologie spécifique. Par exemple, les conteneurs Docker ne sont pas obligatoires pour créer une architecture basée sur des microservices. Ces microservices peuvent également être exécutés comme processus ordinaires. Les microservices constituent une architecture logique.

De plus, même si un microservice peut être physiquement implémenté comme un simple service, processus ou conteneur (par souci de simplicité, c’est l’approche adoptée dans la version initiale de [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)), cette parité entre un microservice métier et un service ou un conteneur physique n’est pas une exigence dans tous les cas quand vous créez une grande application complexe composée de plusieurs dizaines voire centaines de services.

C’est sur ce point qu’il y a une réelle différence entre l’architecture logique et l’architecture physique d’une application. L’architecture logique et les limites logiques d’un système ne correspondent pas nécessairement selon une relation un-à-un à l’architecture physique ou du déploiement. Cela peut se produire, mais ce n’est pas souvent le cas.

Même si vous avez identifié certains microservices métier ou des contextes délimités, cela ne signifie pas que la meilleure façon de les implémenter est toujours de créer un service (comme une API web ASP.NET) ou un conteneur Docker pour chaque microservice métier. Une règle spécifiant que chaque microservice métier doit être implémenté en utilisant un service ou un conteneur est trop rigide.

Par conséquent, un microservice métier ou un contexte délimité est une architecture logique qui peut (ou non) coïncider avec l’architecture physique. Le point important est qu’un microservice métier ou un contexte délimité doit être autonome en permettant au code et à l’état d’être versionnés, déployés et mis à l’échelle indépendamment l’un de l’autre.

Comme le montre la figure 4-8, le microservice métier du catalogue pourrait être composé de plusieurs services ou processus. Il pourrait s’agir de plusieurs services d’API web ASP.NET ou de tout autre type de service utilisant HTTP ou un autre protocole. Plus important encore, les services pourraient partager les mêmes données, dès lors que ces services sont cohésifs pour le même domaine métier.

![Diagramme du microservice métier Catalog, qui contient un service API, un service de recherche et une base de données SQL Server.](./media/image8.png)

**Figure 4-8**. Microservice métier avec plusieurs services physiques

Les services de l’exemple partagent le même modèle de données, car le service d’API web cible les mêmes données que le service de recherche. Ainsi, dans l’implémentation physique du microservice métier, vous divisez cette fonctionnalité afin d’effectuer un scale-up ou un scale-down de chacun de ces services internes selon les besoins. Le service d’API web nécessite peut-être généralement plus d’instances que le service de recherche, ou inversement.

En bref, l’architecture logique des microservices n’a pas toujours à coïncider avec l’architecture du déploiement physique. Dans ce guide, quand nous mentionnons un microservice, nous entendons par là un microservice métier ou logique, qui peut correspondre à un ou plusieurs services (physiques). Dans la plupart des cas, il s’agit d’un seul service, mais il peut y en avoir plus.

>[!div class="step-by-step"]
>[Précédent](data-sovereignty-per-microservice.md)
>[Suivant](distributed-data-management.md)