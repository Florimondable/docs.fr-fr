---
title: Définition de votre application à plusieurs conteneurs avec docker-compose.yml
description: Architecture de microservices .NET pour les applications .NET conteneurisées | Guide pratique pour spécifier la composition des microservices d’une application multiconteneur avec docker-compose.yml.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: dc9149cb1a17e3af66abd995fd2a2196109e0e05
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145252"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Définition de votre application à plusieurs conteneurs avec docker-compose.yml 

Dans ce guide, le fichier [docker-compose.yml](https://docs.docker.com/compose/compose-file/) a été introduit dans la section [Étape 4. Définir vos services dans docker-compose.yml au moment de générer une application Docker à plusieurs conteneurs](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application). Toutefois, il existe d’autres modes d’utilisation des fichiers docker-compose qui méritent d’être abordés plus en détail.

Par exemple, vous pouvez décrire explicitement la façon dont vous souhaitez déployer votre application à plusieurs conteneurs dans le fichier docker-compose.yml. Éventuellement, vous pouvez également décrire la façon dont vous allez générer vos images Docker personnalisées. (Vous pouvez également générer des images Docker personnalisées avec l’interface de ligne de commande Docker CLI.)

Pour l’essentiel, vous définissez chacun des conteneurs à déployer, ainsi que certaines caractéristiques relatives à chaque déploiement de conteneur. Une fois que vous disposez d’un fichier de description de déploiement à plusieurs conteneurs, vous pouvez déployer l’ensemble de la solution en une seule action orchestrée par la commande CLI [docker-compose up](https://docs.docker.com/compose/overview/), ou la déployer de manière transparente à partir de Visual Studio. Sinon, vous devez utiliser l’interface CLI Docker pour effectuer un déploiement conteneur par conteneur en plusieurs étapes à l’aide de la commande `docker run` à partir de la ligne de commande. Ainsi, chaque service défini dans docker-compose.yml doit spécifier une seule image ou une seule build. Les autres clés sont facultatives et sont analogues à leurs homologues de ligne de commande `docker run`.

Le code YAML suivant représente la définition d’un éventuel fichier docker-compose.yml global mais unique pour l’exemple eShopOnContainers. Il ne s’agit pas du fichier docker-compose réel d’eShopOnContainers. Il s’agit plutôt d’une version simplifiée et centralisée dans un fichier unique, ce qui n’est pas la meilleure façon d’utiliser les fichiers docker-compose, comme cela sera expliqué plus tard.

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
    ports:
      - "5100:80"
    depends_on:
      - catalog.api
      - ordering.api
      - basket.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  basket.api:
    image: eshop/basket.api
    environment:
      - ConnectionString=sql.data
    ports:
      - "5103:80"
    depends_on:
      - sql.data

  sql.data:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basket.data:
    image: redis
```

La clé racine de ce fichier est services. Sous cette clé, vous définissez les services que vous souhaitez déployer et exécuter quand vous exécutez la commande `docker-compose up` ou quand vous effectuez un déploiement à partir de Visual Studio à l’aide du fichier docker-compose.yml. Dans le cas présent, plusieurs services sont définis pour le fichier docker-compose.yml, comme indiqué dans le tableau suivant.

| Nom du service | Description |
|--------------|-------------|
| webmvc       | Conteneur incluant l’application ASP.NET Core MVC qui consomme les microservices à partir du code C\# côté serveur|
| catalog.api  | Conteneur incluant le microservice Catalog de l’API web ASP.NET Core |
| ordering.api | Conteneur incluant le microservice Ordering de l’API web ASP.NET Core |
| sql.data     | Conteneur exécutant SQL Server pour Linux et contenant les bases de données de microservices |
| basket.api   | Conteneur incluant le microservice Basket de l’API web ASP.NET Core |
| basket.data  | Conteneur exécutant le service de cache REDIS, avec la base de données du panier comme cache REDIS |

### <a name="a-simple-web-service-api-container"></a>Conteneur d’API de service web simple

Dans la mesure où il se concentre sur un seul conteneur, le microservice du conteneur catalog.api a une définition simple :

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data
```

Ce service conteneurisé a la configuration de base suivante :

-   Il est basé sur l’image personnalisée eshop/catalog.api. Par souci de simplicité, il n’existe aucun paramètre de clé build: dans le fichier. Cela signifie que l’image doit avoir été préalablement générée (avec docker build) ou téléchargée (avec la commande docker pull) à partir du registre Docker.

-   Il définit une variable d’environnement nommée ConnectionString à l’aide de la chaîne de connexion à utiliser par Entity Framework pour accéder à l’instance SQL Server qui contient le modèle de données du catalogue. Dans le cas présent, le même conteneur SQL Server contient plusieurs bases de données. Vous avez donc besoin de moins de mémoire sur votre machine de développement pour Docker. Toutefois, vous pouvez également déployer un conteneur SQL Server pour chaque base de données de microservice.

-   Le nom SQL Server est sql.data, le même nom que celui utilisé pour le conteneur qui exécute l’instance SQL Server pour Linux. Cela est très pratique, car cette résolution de noms (interne à l’hôte Docker) permet de résoudre l’adresse réseau, ce qui vous évite d’avoir à connaître l’adresse IP interne des conteneurs auxquels vous accédez à partir d’autres conteneurs.

Dans la mesure où la chaîne de connexion est définie par une variable d’environnement, vous pouvez définir cette variable via un autre mécanisme et à un autre moment. Par exemple, vous pouvez définir une chaîne de connexion distincte durant le déploiement en production sur les hôtes finaux, ou à partir de vos pipelines d’intégration continue/de livraison continue dans Azure DevOps Services ou votre système DevOps préféré.

-   Il expose le port 80 pour l’accès interne au service catalog.api dans l’hôte Docker. L’hôte est une machine virtuelle Linux, car elle est basée sur une image Docker pour Linux, mais vous pouvez configurer le conteneur pour qu’il s’exécute plutôt sur une image Windows.

-   Il réachemine le port 80 exposé sur le conteneur vers le port 5101 de la machine hôte Docker (machine virtuelle Linux).

-   Il lie le service web au service sql.data (instance SQL Server pour la base de données Linux s’exécutant dans un conteneur). Quand vous spécifiez cette dépendance, le conteneur catalog.api ne démarre pas tant que le conteneur sql.data n’a pas démarré. Cela est important, car catalog.api a besoin que la base de données SQL Server soit d’abord opérationnelle. Toutefois, ce genre de dépendance de conteneur ne suffit pas dans la plupart des cas, car Docker effectue uniquement une vérification au niveau du conteneur. Parfois, le service (dans le cas présent, SQL Server) n’est peut-être pas encore prêt. Il est donc conseillé d’implémenter une logique de réexécution avec interruption exponentielle dans vos microservices clients. Ainsi, si un conteneur de dépendances n’est pas prêt pendant une courte période, l’application reste résiliente.

-   Il est configuré pour autoriser l’accès aux serveurs externes : le paramètre extra\_hosts vous permet d’accéder à des serveurs ou machines externes à l’hôte Docker (c’est-à-dire, situées en dehors de la machine virtuelle Linux par défaut qui est un hôte Docker de développement), par exemple une instance SQL Server locale sur votre PC de développement.

Il existe également d’autres paramètres docker-compose.yml plus avancés que nous aborderons dans les sections suivantes.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Utilisation de fichiers docker-compose pour cibler plusieurs environnements

Les fichiers docker-compose.yml sont des fichiers de définition. Ils peuvent être utilisés par plusieurs infrastructures qui comprennent ce format. L’outil le plus simple est la commande docker-compose.

Ainsi, à l’aide de la commande docker-compose, vous pouvez cibler les principaux scénarios suivants.

#### <a name="development-environments"></a>Environnements de développement

Quand vous développez des applications, il est important de pouvoir les exécuter dans un environnement de développement isolé. Vous pouvez vous servir de la commande CLI docker-compose pour créer cet environnement, ou utiliser Visual Studio qui exécute docker-compose de manière interne.

Le fichier docker-compose.yml vous permet de configurer et de documenter toutes les dépendances de service de votre application (autres services, mises en cache, bases de données, files d’attente, etc.). À l’aide de la commande CLI docker-compose, vous pouvez créer et démarrer un ou plusieurs conteneurs pour chaque dépendance avec une seule commande (docker-compose up).

Les fichiers docker-compose.yml sont des fichiers config interprétés par le moteur Docker. Toutefois, ils servent également de fichiers de documentation pratiques sur la composition de votre application à plusieurs conteneurs.

#### <a name="testing-environments"></a>Environnements de test

Les tests unitaires et les tests d’intégration sont une partie importante d’un processus de déploiement continu ou d’intégration continue (CI). Ces tests automatisés nécessitent un environnement isolé pour ne pas être impactés par les utilisateurs ou par tout autre changement dans les données de l’application.

Avec Docker Compose, vous pouvez créer et détruire très facilement cet environnement isolé en quelques commandes, à partir de votre invite de commandes ou de vos scripts, à l’image des commandes suivantes :

```
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a>Déploiements de production

Vous pouvez également utiliser Compose pour effectuer un déploiement sur un moteur Docker distant. Il est assez courant d’effectuer un déploiement sur une seule instance d’hôte Docker (par exemple une machine virtuelle de production ou un serveur provisionné avec [Docker Machine](https://docs.docker.com/machine/overview/)).

Si vous utilisez un autre orchestrateur (Azure Service Fabric, Kubernetes, etc.), vous devrez peut-être ajouter des paramètres d’installation et de configuration de métadonnées comme ceux de docker-compose.yml, mais dans le format demandé par l’autre orchestrateur.

Dans tous les cas, docker-compose est un outil pratique et un format de métadonnées adapté aux workflows de développement, de test et de production, même si le workflow de production peut varier selon l’orchestrateur utilisé.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Utilisation de plusieurs fichiers docker-compose pour prendre en charge plusieurs environnements

Quand vous ciblez des environnements différents, vous devez utiliser plusieurs fichiers Compose. Cela vous permet de créer plusieurs variantes de configuration en fonction de l’environnement.

#### <a name="overriding-the-base-docker-compose-file"></a>Remplacement du fichier docker-compose de base

Vous pouvez utiliser un fichier docker-compose.yml unique comme dans les exemples simplifiés présentés dans les sections précédentes. Toutefois, cela n’est pas recommandé pour la plupart des applications.

Par défaut, Compose lit deux fichiers, un fichier docker-compose.yml et un fichier docker-compose.override.yml facultatif. Comme indiqué dans la figure 6-11, quand vous utilisez Visual Studio et que vous activez la prise en charge de Docker, Visual Studio crée également un fichier docker-compose.vs.debug.g.yml supplémentaires pour le débogage de l’application, vous pouvez examiner ce fichier dans le dossier obj\\Docker\\ du dossier de solution principal.

![Structure du fichier projet docker-compose : .dockerignore, pour ignorer les fichiers ; docker-compose.yml, pour composer des microservices ; docker-compose.override.yml, pour configurer l’environnement des microservices.](./media/image12.png)

**Figure 6-11.** Fichiers docker-compose dans Visual Studio 2017

Vous pouvez modifier les fichiers docker-compose à l’aide de n’importe quel éditeur, comme Visual Studio Code ou Sublime, et exécuter l’application avec la commande docker-compose up.

Par convention, le fichier docker-compose.yml contient votre configuration de base et d’autres paramètres statiques. Cela signifie que la configuration du service ne doit pas changer en fonction de l’environnement de déploiement ciblé.

Comme son nom l’indique, le fichier docker-compose.override.yml contient des paramètres de configuration qui remplacent la configuration de base par une configuration dépendante de l’environnement de déploiement. Vous pouvez également avoir plusieurs fichiers de substitution avec des noms différents. Les fichiers de substitution contiennent généralement des informations supplémentaires nécessaires à l’application mais spécifiques à un environnement ou un déploiement.

#### <a name="targeting-multiple-environments"></a>Ciblage de plusieurs environnements

Il est courant de définir plusieurs fichiers Compose pour cibler plusieurs environnements : production, préproduction, intégration continue (CI) ou développement, par exemple. Pour permettre la prise en charge de ces différences, vous pouvez diviser votre configuration Compose en plusieurs fichiers, comme le montre la figure 6-12.

![Vous pouvez combiner plusieurs fichiers docker-compose*.fml pour gérer différents environnements.](./media/image13.png)

**Figure 6-12.** Plusieurs fichiers docker-compose remplaçant des valeurs du fichier docker-compose.yml de base

Vous commencez avec le fichier docker-compose.yml de base. Ce fichier de base doit contenir les paramètres de configuration de base ou statiques qui ne changent pas en fonction de l’environnement. Par exemple, eShopOnContainers a le fichier de base docker-compose.yml suivant (simplifié avec moins de services) comme fichier de base.

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile    
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile    
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile    
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile    
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api
      - marketing.api

  sql.data:
    image: microsoft/mssql-server-linux:2017-latest

  nosql.data:
    image: mongo

  basket.data:
    image: redis
      
  rabbitmq:
    image: rabbitmq:3-management

```

Les valeurs du fichier docker-compose.yml de base ne doivent pas changer malgré les différents environnements de déploiement cibles.

Si vous vous concentrez sur la définition de service webmvc, par exemple, vous pouvez constater que les informations sont les mêmes, quel que soit l’environnement ciblé. Vous disposez des informations suivantes :

-   Nom du service : webmvc

-   Image personnalisée du conteneur : eshop/webmvc

-   Commande de génération de l’image Docker personnalisée, indiquant quel fichier Docker utiliser

-   Dépendances avec d’autres services, pour empêcher ce conteneur de démarrer avant les autres conteneurs de dépendances

Vous pouvez avoir une configuration supplémentaire, mais le point important est que le fichier docker-compose.yml de base vous sert simplement à définir les informations communes aux environnements. Ensuite, dans le fichier docker-compose.override.yml ou les fichiers similaires de production ou de préproduction, vous devez placer une configuration spécifique à chaque environnement.

En règle générale, le fichier docker-compose.override.yml est utilisé pour votre environnement de développement, comme dans l’exemple suivant d’eShopOnContainers :

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services: 
# Simplified number of services here: 
      
  basket.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basket.data}
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}      
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5202/api/v1/catalog/items/[0]/pic/}   
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}         
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}          
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - PurchaseUrl=http://webshoppingapigw
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://webmarketingapigw
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
  basket.data:
    ports:
      - "6379:6379"      
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

Dans cet exemple, la configuration de substitution de l’environnement de développement expose certains ports à l’hôte, définit les variables d’environnement à l’aide d’URL de redirection et spécifie les chaînes de connexion de l’environnement de développement. Ces paramètres concernent juste l’environnement de développement.

Quand vous exécutez `docker-compose up`, ou quand vous lancez cette commande à partir de Visual Studio, elle lit automatiquement les remplacements comme si elle fusionnait les deux fichiers.

Supposons que vous souhaitiez un autre fichier Compose pour l’environnement de production, avec d’autres valeurs de configuration, ports ou chaînes de connexion. Vous pouvez créer un autre fichier de substitution, par exemple le fichier nommé `docker-compose.prod.yml`, avec d’autres paramètres et variables d’environnement.  Ce fichier peut être stocké dans un autre dépôt Git, ou être géré et sécurisé par une autre équipe.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Comment effectuer un déploiement avec un fichier de substitution spécifique

Pour utiliser plusieurs fichiers de substitution ou un fichier de substitution avec un autre nom, vous pouvez spécifier l’option -f avec la commande docker-compose et les fichiers souhaités. Compose fusionne les fichiers dans l’ordre indiqué sur la ligne de commande. L’exemple suivant montre comment effectuer un déploiement avec des fichiers de substitution.

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Utilisation de variables d’environnement dans les fichiers docker-compose

Il est pratique, surtout dans les environnements de production, d’obtenir des informations de configuration à partir de variables d’environnement, comme nous l’avons montré dans les exemples précédents. Vous pouvez référencer une variable d’environnement dans vos fichiers docker-compose à l’aide de la syntaxe ${MY\_VAR}. La ligne suivante d’un fichier docker-compose.prod.yml montre comment référencer la valeur d’une variable d’environnement.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Les variables d’environnement sont créées et initialisées de différentes manières, en fonction de votre environnement hôte (Linux, Windows, cluster Cloud, etc.). Toutefois, une approche pratique consiste à utiliser un fichier .env. Les fichiers docker-compose prennent en charge la déclaration de variables d’environnement par défaut dans le fichier .env. Ces valeurs de variables d’environnement sont les valeurs par défaut. Toutefois, elles peuvent être remplacées par les valeurs que vous avez définies dans chacun de vos environnements (OS hôte ou variables d’environnement de votre cluster). Vous placez ce fichier .env dans le dossier à partir duquel la commande docker-compose est exécutée.

L’exemple suivant illustre un fichier .env semblable au fichier [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) de l’application eShopOnContainers.

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker-compose s’attend à ce que chaque ligne d’un fichier .env soit au format \<variable\>=\<valeurs\>.

Notez que les valeurs définies dans l’environnement d’exécution remplacent toujours les valeurs définies dans le fichier .env. De même, les valeurs passées via les arguments de ligne de commande remplacent également les valeurs par défaut définies dans le fichier .env.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Vue d’ensemble de Docker Compose** <br/>
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **Fichiers Compose multiples** <br/>
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Génération d’images Docker ASP.NET Core optimisées

Si vous recherchez des sources relatives à Docker et .NET Core sur Internet, vous trouverez des fichiers Docker qui illustrent la simplicité de la génération d’une image Docker. En effet, il vous suffit de copier votre source dans un conteneur. Ces exemples suggèrent qu’à l’aide d’une configuration toute simple, vous pouvez disposer d’une image Docker où l’environnement et votre application font partie d’un même package. L’exemple suivant montre un fichier Docker de ce genre.

```
FROM microsoft/dotnet
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

Un fichier Docker comme celui-ci va fonctionner correctement. Toutefois, vous pouvez considérablement optimiser vos images, en particulier vos images de production.

Dans le modèle reposant sur un conteneur et des microservices, vous démarrez constamment des conteneurs. En règle générale, l’utilisation de conteneurs n’entraîne pas le redémarrage d’un conteneur en veille, car le conteneur peut être supprimé. Les orchestrateurs (comme Kubernetes et Azure Service Fabric) créent simplement des instances d’images. Cela signifie que vous devez effectuer une optimisation en précompilant l’application au moment de sa génération pour accélérer le processus d’instanciation. Une fois que le conteneur a démarré, il est prêt à s’exécuter. N’effectuez pas d’opérations de restauration ou de compilation au moment de l’exécution à l’aide des commandes `dotnet restore` et `dotnet build` à partir de l’interface CLI dotnet, comme indiqué dans de nombreux billets de blog sur .NET Core et Docker.

L’équipe .NET a effectué un travail important pour faire de .NET Core et d’ASP.NET Core un framework optimisé pour les conteneurs. .NET Core n’est pas seulement un framework léger avec un faible encombrement mémoire. L’équipe s’est concentrée sur les images Docker optimisées pour les trois principaux scénarios et les a publiées dans le registre Docker Hub à l’emplacement <span class="underline">microsoft/dotnet</span>, en commençant par la version 2.1 :

1.  **Développement** : la priorité est la capacité à rapidement intégrer et déboguer les changements, et la taille est secondaire.

2.  **Génération** : la priorité est la compilation de l’application, et cela inclut les fichiers binaires et les autres dépendances pour optimiser les fichiers binaires.

3.  **Production** : quand la priorité est le déploiement et le démarrage rapides de conteneurs, ces images sont limitées aux fichiers binaires et au contenu nécessaire pour exécuter l’application.

Pour ce faire, l’équipe .NET fournit trois variantes de base dans [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) (sur Docker Hub) :

1.  **sdk** : pour les scénarios de développement et de génération.
2.  **runtime** : pour le scénario de production, et
3.  **Runtime-deps** : pour le scénario de production des [applications autonomes](https://docs.microsoft.com/dotnet/core/deploying/index#self-contained-deployments-scd).

Pour faciliter un démarrage plus rapide, les images runtime affectent également le paramètre automatique aspnetcore\_urls au port 80 et le cache d’assemblys préalable à l’exécution de ngen.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Génération d’images Docker optimisées avec ASP.NET Core** <br/>
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

-   **Création d’images Docker pour les applications .NET Core** <br/>
    [*https://docs.microsoft.com/en-us/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/en-us/dotnet/core/docker/building-net-docker-images)

>[!div class="step-by-step"]
>[Précédent](data-driven-crud-microservice.md)
>[Suivant](database-server-container.md)