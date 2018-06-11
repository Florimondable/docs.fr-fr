---
title: Moderniser vos applications avec la surveillance et télémétrie
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Moderniser vos applications avec la surveillance et télémétrie
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 8f5f9bfebf46db7b98bedc4b5b8204d23357c72e
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a><span data-ttu-id="b39fe-103">Moderniser vos applications avec la surveillance et télémétrie</span><span class="sxs-lookup"><span data-stu-id="b39fe-103">Modernize your apps with monitoring and telemetry</span></span>

<span data-ttu-id="b39fe-104">Lorsque vous exécutez une application en production, il est essentiel que vous disposez des informations sur les performances de votre application.</span><span class="sxs-lookup"><span data-stu-id="b39fe-104">When you run an application in production, it's critical that you have insights about how your application is performing.</span></span> <span data-ttu-id="b39fe-105">Il effectue un haut niveau ?</span><span class="sxs-lookup"><span data-stu-id="b39fe-105">Is it performing at a high level?</span></span> <span data-ttu-id="b39fe-106">Utilisateurs obtenez des erreurs ou l’application n’est stable et fiable ?</span><span class="sxs-lookup"><span data-stu-id="b39fe-106">Are users getting errors, or is the application stable and reliable?</span></span> <span data-ttu-id="b39fe-107">Vous avez besoin de l’analyse des performances riche, puissant alertes et tableaux de bord pour vous assurer que votre application est disponible et les performances comme prévu.</span><span class="sxs-lookup"><span data-stu-id="b39fe-107">You need rich performance monitoring, powerful alerting, and dashboards to help ensure that your application is available and performing as expected.</span></span> <span data-ttu-id="b39fe-108">Vous devez également être en mesure de voir rapidement s’il existe un problème, déterminer le nombre de clients est affecté et effectuer une analyse des causes pour rechercher et corriger le problème.</span><span class="sxs-lookup"><span data-stu-id="b39fe-108">You also need to be able to see quickly if there's a problem, determine how many customers are affected, and perform a root-cause analysis to find and fix the issue.</span></span>

## <a name="monitor-your-application-with-application-insights"></a><span data-ttu-id="b39fe-109">Analyser votre application avec Application Insights</span><span class="sxs-lookup"><span data-stu-id="b39fe-109">Monitor your application with Application Insights</span></span>

<span data-ttu-id="b39fe-110">Application Insights est un service de gestion des performances des applications (APM) extensible pour les développeurs web qui fonctionnent sur plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="b39fe-110">Application Insights is an extensible Application Performance Management (APM) service for web developers who work on multiple platforms.</span></span> <span data-ttu-id="b39fe-111">Il permet d’analyser votre application web dynamique.</span><span class="sxs-lookup"><span data-stu-id="b39fe-111">Use it to monitor your live web application.</span></span> <span data-ttu-id="b39fe-112">Application Insights détecte automatiquement les anomalies de performance.</span><span class="sxs-lookup"><span data-stu-id="b39fe-112">Application Insights automatically detects performance anomalies.</span></span> <span data-ttu-id="b39fe-113">Il inclut des outils puissants analytique pour vous aider à diagnostiquer les problèmes et pour vous aider à comprendre ce que les utilisateurs effectuent avec votre application.</span><span class="sxs-lookup"><span data-stu-id="b39fe-113">It includes powerful analytics tools to help you diagnose issues, and to help you understand what users actually do with your app.</span></span> <span data-ttu-id="b39fe-114">Application Insights est conçu pour vous aider à améliorer en permanence les performances et la convivialité.</span><span class="sxs-lookup"><span data-stu-id="b39fe-114">Application Insights is designed to help you continuously improve performance and usability.</span></span> <span data-ttu-id="b39fe-115">Il fonctionne pour les applications sur un large éventail de plateformes, y compris .NET, Node.js et J2EE, si hébergé localement ou dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="b39fe-115">It works for apps on a wide variety of platforms, including .NET, Node.js, and J2EE, whether hosted on-premises or in the cloud.</span></span> <span data-ttu-id="b39fe-116">Application Insights s’intègre à vos processus DevOps et a des points de connexion à une variété d’outils de développement.</span><span class="sxs-lookup"><span data-stu-id="b39fe-116">Application Insights integrates with your DevOps processes, and has connection points to a variety of development tools.</span></span>

<span data-ttu-id="b39fe-117">Figure 4-10 illustre un exemple de comment Application Insights surveille votre application et comment il expose ces analyses au tableau de bord.</span><span class="sxs-lookup"><span data-stu-id="b39fe-117">Figure 4-10 shows an example of how Application Insights monitors your application and how it surfaces those insights to a dashboard.</span></span>

![Tableau de bord de surveillance application Insights](./media/image10.png)

> <span data-ttu-id="b39fe-119">**Figure 4-10.**</span><span class="sxs-lookup"><span data-stu-id="b39fe-119">**Figure 4-10.**</span></span> <span data-ttu-id="b39fe-120">Tableau de bord de surveillance application Insights</span><span class="sxs-lookup"><span data-stu-id="b39fe-120">Application Insights monitoring dashboard</span></span>

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a><span data-ttu-id="b39fe-121">Surveiller votre infrastructure de Docker avec Analytique de journal et de sa solution d’analyse de conteneur</span><span class="sxs-lookup"><span data-stu-id="b39fe-121">Monitor your Docker infrastructure with Log Analytics and its Container Monitoring solution</span></span>

<span data-ttu-id="b39fe-122">[Azure Analytique de journal](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) fait partie de la [globale de solution de surveillance de Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span><span class="sxs-lookup"><span data-stu-id="b39fe-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) is part of the [Microsoft Azure overall monitoring solution](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span></span> <span data-ttu-id="b39fe-123">Il est également un service [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span><span class="sxs-lookup"><span data-stu-id="b39fe-123">It's also a service in [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span></span> <span data-ttu-id="b39fe-124">Analytique de journal surveille le cloud et les environnements locaux (OMS pour local) pour aider à assurer la disponibilité et les performances.</span><span class="sxs-lookup"><span data-stu-id="b39fe-124">Log Analytics monitors cloud and on-premises environments (OMS for on-premises) to help maintain availability and performance.</span></span> <span data-ttu-id="b39fe-125">Il collecte les données générées par les ressources dans vos environnements locaux et cloud et d’autres outils de surveillance pour fournir une analyse à plusieurs sources.</span><span class="sxs-lookup"><span data-stu-id="b39fe-125">It collects data generated by resources in your cloud and on-premises environments and from other monitoring tools to provide analysis across multiple sources.</span></span>

<span data-ttu-id="b39fe-126">Par rapport aux journaux d’infrastructure Azure, Analytique de journal, comme un service Azure, résultants journal et mesure des données à partir d’autres services Azure (via [moniteur Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), machines virtuelles Azure, les conteneurs Docker et en local ou autres infrastructures de cloud.</span><span class="sxs-lookup"><span data-stu-id="b39fe-126">In relation to Azure infrastructure logs, Log Analytics, as an Azure service, ingests log and metric data from other Azure services (via [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure VMs, Docker containers, and on-premises or other cloud infrastructures.</span></span> <span data-ttu-id="b39fe-127">Analytique de journal offre de recherche de journal flexible et analytique hors de la zone au-dessus de ces données.</span><span class="sxs-lookup"><span data-stu-id="b39fe-127">Log Analytics offers flexible log search and out-of-the box analytics on top of this data.</span></span> <span data-ttu-id="b39fe-128">Il fournit des outils que vous pouvez utiliser pour analyser les données dans toutes les sources, il permet des requêtes complexes sur tous les journaux et peut informer proactive en fonction des conditions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b39fe-128">It provides rich tools that you can use to analyze data across sources, it allows complex queries across all logs, and it can proactively alert based on specified conditions.</span></span> <span data-ttu-id="b39fe-129">Vous pouvez même collecter des données personnalisées dans le référentiel central Analytique de journal, où vous pouvez interroger et visualiser.</span><span class="sxs-lookup"><span data-stu-id="b39fe-129">You can even collect custom data in the central Log Analytics repository, where you can query and visualize it.</span></span> <span data-ttu-id="b39fe-130">Vous pouvez également tirer parti des solutions intégrées Analytique de journal pour obtenir des informations détaillées dans la sécurité et les fonctionnalités de votre infrastructure.</span><span class="sxs-lookup"><span data-stu-id="b39fe-130">You also can take advantage of the Log Analytics built-in solutions to immediately gain insights into the security and functionality of your infrastructure.</span></span>

<span data-ttu-id="b39fe-131">Vous pouvez accéder Analytique de journal par le biais du portail OMS ou le portail Azure, qui s’exécutent dans n’importe quel navigateur, et fournir d’accéder aux paramètres de configuration et des plusieurs outils pour analyser et agir sur les données collectées.</span><span class="sxs-lookup"><span data-stu-id="b39fe-131">You can access Log Analytics through the OMS portal or the Azure portal, which run in any browser, and provide you with access to configuration settings and multiple tools to analyze and act on collected data.</span></span>

<span data-ttu-id="b39fe-132">Le [solution d’analyse de conteneur](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) dans Analytique de journal permet de consulter et de gérer vos hôtes Docker et conteneur Windows dans un emplacement unique.</span><span class="sxs-lookup"><span data-stu-id="b39fe-132">The [Container Monitoring solution](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) in Log Analytics helps you view and manage your Docker and Windows Container hosts in a single location.</span></span> <span data-ttu-id="b39fe-133">La solution montre les conteneurs sont en cours d’exécution, image de conteneur qu’ils s’exécutent et exécutant des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="b39fe-133">The solution shows which containers are running, what container image they're running, and where containers are running.</span></span> <span data-ttu-id="b39fe-134">Vous pouvez afficher des informations d’audit détaillées, y compris les commandes qui sont utilisés avec des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="b39fe-134">You can view detailed audit information, including commands that are being used with containers.</span></span> <span data-ttu-id="b39fe-135">Vous pouvez également résoudre les conteneurs en affichant et en recherche de journaux centralisées, sans avoir à afficher à distance des ordinateurs hôtes Docker ou Windows.</span><span class="sxs-lookup"><span data-stu-id="b39fe-135">You also can troubleshoot containers by viewing and searching centralized logs, without needing to remotely view Docker or Windows hosts.</span></span> <span data-ttu-id="b39fe-136">Vous pouvez rechercher des conteneurs qui peuvent être bruyants et beaucoup de ressources en excès sur un ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="b39fe-136">You can find containers that might be noisy and consuming excess resources on a host.</span></span> <span data-ttu-id="b39fe-137">En outre, vous pouvez afficher centralisée de l’UC, mémoire, stockage, l’utilisation du réseau et des informations sur les performances, pour les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="b39fe-137">Additionally, you can view centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span> <span data-ttu-id="b39fe-138">Sur les ordinateurs exécutant Windows, vous pouvez centraliser et comparer les journaux à partir de Windows Server, Hyper-V et des conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="b39fe-138">On computers running Windows, you can centralize and compare logs from Windows Server, Hyper-V, and Docker containers.</span></span> <span data-ttu-id="b39fe-139">La solution prend en charge les orchestrators conteneur suivant :</span><span class="sxs-lookup"><span data-stu-id="b39fe-139">The solution supports the following container orchestrators:</span></span>

-   <span data-ttu-id="b39fe-140">Docker Swarm</span><span class="sxs-lookup"><span data-stu-id="b39fe-140">Docker Swarm</span></span>

-   <span data-ttu-id="b39fe-141">CONTRÔLEUR DE DOMAINE/SYSTÈME D’EXPLOITATION</span><span class="sxs-lookup"><span data-stu-id="b39fe-141">DC/OS</span></span>

-   <span data-ttu-id="b39fe-142">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b39fe-142">Kubernetes</span></span>

-   <span data-ttu-id="b39fe-143">Service Fabric</span><span class="sxs-lookup"><span data-stu-id="b39fe-143">Service Fabric</span></span>

-   <span data-ttu-id="b39fe-144">Red Hat OpenShift</span><span class="sxs-lookup"><span data-stu-id="b39fe-144">Red Hat OpenShift</span></span>

<span data-ttu-id="b39fe-145">Figure 4-11 montre les relations entre les différents hôtes de conteneurs et les agents et OMS.</span><span class="sxs-lookup"><span data-stu-id="b39fe-145">Figure 4-11 shows the relationships between various container hosts and agents and OMS.</span></span>

![Solution de surveillance de conteneur Analytique de journal](./media/image11.png)

> <span data-ttu-id="b39fe-147">**Figure 4-11.**</span><span class="sxs-lookup"><span data-stu-id="b39fe-147">**Figure 4-11.**</span></span> <span data-ttu-id="b39fe-148">Solution de surveillance de conteneur Analytique de journal</span><span class="sxs-lookup"><span data-stu-id="b39fe-148">Log Analytics Container Monitoring solution</span></span>

<span data-ttu-id="b39fe-149">Vous pouvez utiliser la solution d’analyse de journal Analytique conteneur à :</span><span class="sxs-lookup"><span data-stu-id="b39fe-149">You can use the Log Analytics Container Monitoring solution to:</span></span>

-   <span data-ttu-id="b39fe-150">Afficher des informations sur tous les hôtes de conteneur dans un emplacement unique.</span><span class="sxs-lookup"><span data-stu-id="b39fe-150">See information about all container hosts in a single location.</span></span>

-   <span data-ttu-id="b39fe-151">Connaître les conteneurs sont en cours d’exécution, image qu’ils s’exécutent, et où ils s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="b39fe-151">Know which containers are running, what image they're running, and where they're running.</span></span>

-   <span data-ttu-id="b39fe-152">Consultez une piste d’audit pour les actions sur les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="b39fe-152">See an audit trail for actions on containers.</span></span>

-   <span data-ttu-id="b39fe-153">Résoudre les problèmes en affichant et en recherche de journaux centralisées sans connexion à distance aux ordinateurs hôtes Docker.</span><span class="sxs-lookup"><span data-stu-id="b39fe-153">Troubleshoot by viewing and searching centralized logs without remote login to the Docker hosts.</span></span>

-   <span data-ttu-id="b39fe-154">Rechercher des conteneurs qui peuvent être « voisin bruyant » et consomme des ressources supplémentaires sur un ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="b39fe-154">Find containers that might be "noisy neighbors," and be consuming excess resources on a host.</span></span>

-   <span data-ttu-id="b39fe-155">Afficher centralisée de l’UC, mémoire, stockage, l’utilisation du réseau et des informations sur les performances, pour les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="b39fe-155">View centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b39fe-156">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b39fe-156">Additional resources</span></span>

-   <span data-ttu-id="b39fe-157">**Vue d’ensemble de l’analyse dans Microsoft Azure**</span><span class="sxs-lookup"><span data-stu-id="b39fe-157">**Overview of monitoring in Microsoft Azure**</span></span>

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)

-   <span data-ttu-id="b39fe-158">**Nouveautés d’Application Insights ?**</span><span class="sxs-lookup"><span data-stu-id="b39fe-158">**What is Application Insights?**</span></span>

[https://docs.microsoft.com/azure/application-insights/app-insights-overview](https://docs.microsoft.com/azure/application-insights/app-insights-overview)

-   <span data-ttu-id="b39fe-159">**Quel est le journal Analytique ?**</span><span class="sxs-lookup"><span data-stu-id="b39fe-159">**What is Log Analytics?**</span></span>

[https://docs.microsoft.com/azure/log-analytics/log-analytics-overview](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)

-   <span data-ttu-id="b39fe-160">**Solution de surveillance de conteneur dans le journal Analytique**</span><span class="sxs-lookup"><span data-stu-id="b39fe-160">**Container Monitoring solution in Log Analytics**</span></span>

[https://docs.microsoft.com/azure/log-analytics/log-analytics-containers](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)

-   <span data-ttu-id="b39fe-161">**Vue d’ensemble du moniteur de Azure**</span><span class="sxs-lookup"><span data-stu-id="b39fe-161">**Overview of Azure Monitor**</span></span>

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)

-   <span data-ttu-id="b39fe-162">**Nouveautés d’Operations Management Suite (OMS) ?**</span><span class="sxs-lookup"><span data-stu-id="b39fe-162">**What is Operations Management Suite (OMS)?**</span></span>

[https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)

-   <span data-ttu-id="b39fe-163">**Analyse des conteneurs Windows Server dans l’infrastructure de Service auprès d’OMS**</span><span class="sxs-lookup"><span data-stu-id="b39fe-163">**Monitoring Windows Server containers in Service Fabric with OMS**</span></span>

[https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver](https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver)

>[!div class="step-by-step"]
<span data-ttu-id="b39fe-164">[Précédent](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Suivant](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="b39fe-164">[Previous](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Next](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span></span>