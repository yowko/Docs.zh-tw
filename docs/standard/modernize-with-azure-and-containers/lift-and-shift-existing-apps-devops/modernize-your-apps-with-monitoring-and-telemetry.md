---
title: "現代化應用程式與監控與遙測"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |現代化應用程式與監控與遙測"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3caeb60cf0107aaf5413d935f3bde11863561c7d
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a><span data-ttu-id="ac959-103">現代化應用程式與監控與遙測</span><span class="sxs-lookup"><span data-stu-id="ac959-103">Modernize your apps with monitoring and telemetry</span></span>

<span data-ttu-id="ac959-104">當您在生產環境中執行應用程式時，務必確認您尚未深入了解如何執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac959-104">When you run an application in production, it's critical that you have insights about how your application is performing.</span></span> <span data-ttu-id="ac959-105">它正在執行以高層級嗎？</span><span class="sxs-lookup"><span data-stu-id="ac959-105">Is it performing at a high level?</span></span> <span data-ttu-id="ac959-106">使用者會收到錯誤，或為穩定且可靠的應用程式嗎？</span><span class="sxs-lookup"><span data-stu-id="ac959-106">Are users getting errors, or is the application stable and reliable?</span></span> <span data-ttu-id="ac959-107">您需要監視豐富的效能、 強大警示與儀表板，以協助確保您的應用程式會使用並如預期般執行。</span><span class="sxs-lookup"><span data-stu-id="ac959-107">You need rich performance monitoring, powerful alerting, and dashboards to help ensure that your application is available and performing as expected.</span></span> <span data-ttu-id="ac959-108">您也必須能夠快速查看是否有問題，請判斷多少客戶受到影響，並執行根本原因分析，以找出並修正問題。</span><span class="sxs-lookup"><span data-stu-id="ac959-108">You also need to be able to see quickly if there's a problem, determine how many customers are affected, and perform a root-cause analysis to find and fix the issue.</span></span>

## <a name="monitor-your-application-with-application-insights"></a><span data-ttu-id="ac959-109">監視您的應用程式使用 Application Insights</span><span class="sxs-lookup"><span data-stu-id="ac959-109">Monitor your application with Application Insights</span></span>

<span data-ttu-id="ac959-110">Application Insights 是可延伸應用程式效能管理 (APM) 服務的 web 開發人員在多個平台上運作。</span><span class="sxs-lookup"><span data-stu-id="ac959-110">Application Insights is an extensible Application Performance Management (APM) service for web developers who work on multiple platforms.</span></span> <span data-ttu-id="ac959-111">您可以使用它來監視即時 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac959-111">Use it to monitor your live web application.</span></span> <span data-ttu-id="ac959-112">Application Insights 會自動偵測效能的異常狀況。</span><span class="sxs-lookup"><span data-stu-id="ac959-112">Application Insights automatically detects performance anomalies.</span></span> <span data-ttu-id="ac959-113">它包括強大的分析工具以協助您診斷問題，並協助您了解使用者實際執行的工作與您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac959-113">It includes powerful analytics tools to help you diagnose issues, and to help you understand what users actually do with your app.</span></span> <span data-ttu-id="ac959-114">Application Insights 被設計來協助您持續改善效能和可用性。</span><span class="sxs-lookup"><span data-stu-id="ac959-114">Application Insights is designed to help you continuously improve performance and usability.</span></span> <span data-ttu-id="ac959-115">這也適用於應用程式上各種不同的平台，包括.NET、 Node.js 和 J2EE，是否裝載於內部部署或雲端中。</span><span class="sxs-lookup"><span data-stu-id="ac959-115">It works for apps on a wide variety of platforms, including .NET, Node.js, and J2EE, whether hosted on-premises or in the cloud.</span></span> <span data-ttu-id="ac959-116">Application Insights 整合與您的 DevOps 程序，並且有各種不同的開發工具的連接點。</span><span class="sxs-lookup"><span data-stu-id="ac959-116">Application Insights integrates with your DevOps processes, and has connection points to a variety of development tools.</span></span>

<span data-ttu-id="ac959-117">圖 4-10 顯示如何 Application Insights 監視您的應用程式並將它提供這些 insights 諸如儀表板的範例。</span><span class="sxs-lookup"><span data-stu-id="ac959-117">Figure 4-10 shows an example of how Application Insights monitors your application and how it surfaces those insights to a dashboard.</span></span>

![Application Insights 監視儀表板](./media/image10.png)

> <span data-ttu-id="ac959-119">**圖 4-10。**</span><span class="sxs-lookup"><span data-stu-id="ac959-119">**Figure 4-10.**</span></span> <span data-ttu-id="ac959-120">Application Insights 監視儀表板</span><span class="sxs-lookup"><span data-stu-id="ac959-120">Application Insights monitoring dashboard</span></span>

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a><span data-ttu-id="ac959-121">監視與記錄分析和其容器的監視解決方案 Docker 基礎結構</span><span class="sxs-lookup"><span data-stu-id="ac959-121">Monitor your Docker infrastructure with Log Analytics and its Container Monitoring solution</span></span>

<span data-ttu-id="ac959-122">[Azure 記錄分析](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)屬於[整體監控解決方案的 Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)。</span><span class="sxs-lookup"><span data-stu-id="ac959-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) is part of the [Microsoft Azure overall monitoring solution](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span></span> <span data-ttu-id="ac959-123">它也是的服務[Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)。</span><span class="sxs-lookup"><span data-stu-id="ac959-123">It's also a service in [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span></span> <span data-ttu-id="ac959-124">記錄分析會監視雲端和內部部署環境 (內部部署的 OMS) 可以協助維護可用性和效能。</span><span class="sxs-lookup"><span data-stu-id="ac959-124">Log Analytics monitors cloud and on-premises environments (OMS for on-premises) to help maintain availability and performance.</span></span> <span data-ttu-id="ac959-125">它會收集您的雲端和內部部署環境中的其他監視工具來分析跨多個來源的資源所產生的資料。</span><span class="sxs-lookup"><span data-stu-id="ac959-125">It collects data generated by resources in your cloud and on-premises environments and from other monitoring tools to provide analysis across multiple sources.</span></span>

<span data-ttu-id="ac959-126">相對於 Azure 基礎結構記錄檔，記錄分析作為 Azure 服務，內嵌來自其他 Azure 服務的記錄檔和度量資料 (透過[Azure 監視器](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor))，Azure Vm、 Docker 容器，並在內部部署或其他雲端基礎結構。</span><span class="sxs-lookup"><span data-stu-id="ac959-126">In relation to Azure infrastructure logs, Log Analytics, as an Azure service, ingests log and metric data from other Azure services (via [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure VMs, Docker containers, and on-premises or other cloud infrastructures.</span></span> <span data-ttu-id="ac959-127">記錄分析提供彈性的記錄搜尋和不足的方塊分析此資料之上。</span><span class="sxs-lookup"><span data-stu-id="ac959-127">Log Analytics offers flexible log search and out-of-the box analytics on top of this data.</span></span> <span data-ttu-id="ac959-128">它提供豐富的工具，可用來分析資料來源間、 複雜的查詢可讓到所有的記錄檔，而它可以主動警示會根據指定的條件。</span><span class="sxs-lookup"><span data-stu-id="ac959-128">It provides rich tools that you can use to analyze data across sources, it allows complex queries across all logs, and it can proactively alert based on specified conditions.</span></span> <span data-ttu-id="ac959-129">您甚至可以收集自訂資料的中央記錄分析儲存機制中，您可以在此查詢，並將其視覺化。</span><span class="sxs-lookup"><span data-stu-id="ac959-129">You can even collect custom data in the central Log Analytics repository, where you can query and visualize it.</span></span> <span data-ttu-id="ac959-130">您也可以利用的記錄分析的內建解決方案立即深入了解安全性與您的基礎結構的功能。</span><span class="sxs-lookup"><span data-stu-id="ac959-130">You also can take advantage of the Log Analytics built-in solutions to immediately gain insights into the security and functionality of your infrastructure.</span></span>

<span data-ttu-id="ac959-131">您可以存取記錄分析透過 OMS 入口網站或 Azure 入口網站在任何瀏覽器中執行，並提供您的組態設定的存取權和多個工具必須分析以及操作收集的資料。</span><span class="sxs-lookup"><span data-stu-id="ac959-131">You can access Log Analytics through the OMS portal or the Azure portal, which run in any browser, and provide you with access to configuration settings and multiple tools to analyze and act on collected data.</span></span>

<span data-ttu-id="ac959-132">[容器監視解決方案](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)中記錄分析可讓您檢視和管理您的 Docker 和 Windows 容器主機，在單一位置。</span><span class="sxs-lookup"><span data-stu-id="ac959-132">The [Container Monitoring solution](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) in Log Analytics helps you view and manage your Docker and Windows Container hosts in a single location.</span></span> <span data-ttu-id="ac959-133">解決方案會顯示哪些容器執行時，哪些容器映像它們正在執行，並執行容器。</span><span class="sxs-lookup"><span data-stu-id="ac959-133">The solution shows which containers are running, what container image they're running, and where containers are running.</span></span> <span data-ttu-id="ac959-134">您可以檢視詳細的稽核資訊，包括與容器正在使用的命令。</span><span class="sxs-lookup"><span data-stu-id="ac959-134">You can view detailed audit information, including commands that are being used with containers.</span></span> <span data-ttu-id="ac959-135">您也可以透過檢視和搜尋集中式記錄檔，而不需要從遠端檢視 Docker 或 Windows 主機疑難排解容器。</span><span class="sxs-lookup"><span data-stu-id="ac959-135">You also can troubleshoot containers by viewing and searching centralized logs, without needing to remotely view Docker or Windows hosts.</span></span> <span data-ttu-id="ac959-136">您可以找到可能會有很多雜訊並消耗多餘的資源，在主機上的容器。</span><span class="sxs-lookup"><span data-stu-id="ac959-136">You can find containers that might be noisy and consuming excess resources on a host.</span></span> <span data-ttu-id="ac959-137">此外，您可以檢視集中式的 CPU、 記憶體、 儲存和網路使用量和效能資訊的容器。</span><span class="sxs-lookup"><span data-stu-id="ac959-137">Additionally, you can view centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span> <span data-ttu-id="ac959-138">您可以在執行 Windows 的電腦，集中管理，並比較記錄檔，從 Windows Server HYPER-V 和 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="ac959-138">On computers running Windows, you can centralize and compare logs from Windows Server, Hyper-V, and Docker containers.</span></span> <span data-ttu-id="ac959-139">解決方案支援下列容器 orchestrators:</span><span class="sxs-lookup"><span data-stu-id="ac959-139">The solution supports the following container orchestrators:</span></span>

-   <span data-ttu-id="ac959-140">Docker Swarm</span><span class="sxs-lookup"><span data-stu-id="ac959-140">Docker Swarm</span></span>

-   <span data-ttu-id="ac959-141">DC/OS</span><span class="sxs-lookup"><span data-stu-id="ac959-141">DC/OS</span></span>

-   <span data-ttu-id="ac959-142">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="ac959-142">Kubernetes</span></span>

-   <span data-ttu-id="ac959-143">Service Fabric</span><span class="sxs-lookup"><span data-stu-id="ac959-143">Service Fabric</span></span>

-   <span data-ttu-id="ac959-144">Red Hat OpenShift</span><span class="sxs-lookup"><span data-stu-id="ac959-144">Red Hat OpenShift</span></span>

<span data-ttu-id="ac959-145">圖 4-11 顯示各種容器主機和代理程式和 OMS 之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="ac959-145">Figure 4-11 shows the relationships between various container hosts and agents and OMS.</span></span>

![記錄分析容器監視解決方案](./media/image11.png)

> <span data-ttu-id="ac959-147">**圖 4-11。**</span><span class="sxs-lookup"><span data-stu-id="ac959-147">**Figure 4-11.**</span></span> <span data-ttu-id="ac959-148">記錄分析容器監視解決方案</span><span class="sxs-lookup"><span data-stu-id="ac959-148">Log Analytics Container Monitoring solution</span></span>

<span data-ttu-id="ac959-149">您可以使用監視容器記錄分析解決方案：</span><span class="sxs-lookup"><span data-stu-id="ac959-149">You can use the Log Analytics Container Monitoring solution to:</span></span>

-   <span data-ttu-id="ac959-150">請參閱在單一位置中的所有容器主機的資訊。</span><span class="sxs-lookup"><span data-stu-id="ac959-150">See information about all container hosts in a single location.</span></span>

-   <span data-ttu-id="ac959-151">知道哪些容器執行時，哪些映像它們正在執行，並執行所在。</span><span class="sxs-lookup"><span data-stu-id="ac959-151">Know which containers are running, what image they're running, and where they're running.</span></span>

-   <span data-ttu-id="ac959-152">容器，請參閱動作的稽核線索。</span><span class="sxs-lookup"><span data-stu-id="ac959-152">See an audit trail for actions on containers.</span></span>

-   <span data-ttu-id="ac959-153">透過檢視和搜尋沒有遠端登入 Docker 主機的集中式的記錄進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="ac959-153">Troubleshoot by viewing and searching centralized logs without remote login to the Docker hosts.</span></span>

-   <span data-ttu-id="ac959-154">尋找可能是 「 雜訊鄰近項目，"，而且會耗用過多的資源，在主機上的容器。</span><span class="sxs-lookup"><span data-stu-id="ac959-154">Find containers that might be "noisy neighbors," and be consuming excess resources on a host.</span></span>

-   <span data-ttu-id="ac959-155">集中式的 CPU、 記憶體、 儲存和網路使用量和容器的效能資訊檢視。</span><span class="sxs-lookup"><span data-stu-id="ac959-155">View centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ac959-156">其他資源</span><span class="sxs-lookup"><span data-stu-id="ac959-156">Additional resources</span></span>

-   <span data-ttu-id="ac959-157">**監視 Microsoft Azure 中的概觀**</span><span class="sxs-lookup"><span data-stu-id="ac959-157">**Overview of monitoring in Microsoft Azure**</span></span>

[<span data-ttu-id="ac959-158">https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview</span><span class="sxs-lookup"><span data-stu-id="ac959-158">https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview</span></span>](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)

-   <span data-ttu-id="ac959-159">**Application Insights 是什麼？**</span><span class="sxs-lookup"><span data-stu-id="ac959-159">**What is Application Insights?**</span></span>

[<span data-ttu-id="ac959-160">https://docs.microsoft.com/azure/application-insights/app-insights-overview</span><span class="sxs-lookup"><span data-stu-id="ac959-160">https://docs.microsoft.com/azure/application-insights/app-insights-overview</span></span>](https://docs.microsoft.com/azure/application-insights/app-insights-overview)

-   <span data-ttu-id="ac959-161">**什麼是記錄分析？**</span><span class="sxs-lookup"><span data-stu-id="ac959-161">**What is Log Analytics?**</span></span>

[<span data-ttu-id="ac959-162">https://docs.microsoft.com/azure/log-analytics/log-analytics-overview</span><span class="sxs-lookup"><span data-stu-id="ac959-162">https://docs.microsoft.com/azure/log-analytics/log-analytics-overview</span></span>](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)

-   <span data-ttu-id="ac959-163">**記錄分析容器監控解決方案**</span><span class="sxs-lookup"><span data-stu-id="ac959-163">**Container Monitoring solution in Log Analytics**</span></span>

[<span data-ttu-id="ac959-164">https://docs.microsoft.com/azure/log-analytics/log-analytics-containers</span><span class="sxs-lookup"><span data-stu-id="ac959-164">https://docs.microsoft.com/azure/log-analytics/log-analytics-containers</span></span>](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)

-   <span data-ttu-id="ac959-165">**Azure 監視的概觀**</span><span class="sxs-lookup"><span data-stu-id="ac959-165">**Overview of Azure Monitor**</span></span>

[<span data-ttu-id="ac959-166">https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor</span><span class="sxs-lookup"><span data-stu-id="ac959-166">https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor</span></span>](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)

-   <span data-ttu-id="ac959-167">**Operations Management Suite (OMS) 是什麼？**</span><span class="sxs-lookup"><span data-stu-id="ac959-167">**What is Operations Management Suite (OMS)?**</span></span>

[<span data-ttu-id="ac959-168">https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview</span><span class="sxs-lookup"><span data-stu-id="ac959-168">https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview</span></span>](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)

-   <span data-ttu-id="ac959-169">**在 OMS 服務的網狀架構監視的 Windows Server 容器**</span><span class="sxs-lookup"><span data-stu-id="ac959-169">**Monitoring Windows Server containers in Service Fabric with OMS**</span></span>

[<span data-ttu-id="ac959-170">https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver</span><span class="sxs-lookup"><span data-stu-id="ac959-170">https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver)

>[!div class="step-by-step"]
<span data-ttu-id="ac959-171">[上一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[下一頁](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="ac959-171">[Previous](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Next](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span></span>
