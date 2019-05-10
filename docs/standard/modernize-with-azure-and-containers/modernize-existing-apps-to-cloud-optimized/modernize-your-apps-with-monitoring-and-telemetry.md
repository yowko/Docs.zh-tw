---
title: 使用監視和遙測將應用程式現代化
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |現代化您的應用程式監視和遙測
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: a8135031d2879ff377881d246c532573a2149fe7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611649"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a><span data-ttu-id="a31fc-103">使用監視和遙測將應用程式現代化</span><span class="sxs-lookup"><span data-stu-id="a31fc-103">Modernize your apps with monitoring and telemetry</span></span>

<span data-ttu-id="a31fc-104">當您在生產環境中執行應用程式時，務必您已深入了解如何執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a31fc-104">When you run an application in production, it's critical that you have insights about how your application is performing.</span></span> <span data-ttu-id="a31fc-105">它很高的層級嗎？</span><span class="sxs-lookup"><span data-stu-id="a31fc-105">Is it performing at a high level?</span></span> <span data-ttu-id="a31fc-106">使用者收到錯誤，或是為穩定且可靠的應用程式嗎？</span><span class="sxs-lookup"><span data-stu-id="a31fc-106">Are users getting errors, or is the application stable and reliable?</span></span> <span data-ttu-id="a31fc-107">您需要豐富的效能監視、 功能強大警示與儀表板，以協助確保您的應用程式可用且如預期般執行。</span><span class="sxs-lookup"><span data-stu-id="a31fc-107">You need rich performance monitoring, powerful alerting, and dashboards to help ensure that your application is available and performing as expected.</span></span> <span data-ttu-id="a31fc-108">您也需要能夠快速查看是否有問題、 判斷多少客戶會受到影響，以及執行根本原因分析，以找出並修正問題。</span><span class="sxs-lookup"><span data-stu-id="a31fc-108">You also need to be able to see quickly if there's a problem, determine how many customers are affected, and perform a root-cause analysis to find and fix the issue.</span></span>

## <a name="monitor-your-application-with-application-insights"></a><span data-ttu-id="a31fc-109">監視您的應用程式使用 Application Insights</span><span class="sxs-lookup"><span data-stu-id="a31fc-109">Monitor your application with Application Insights</span></span>

<span data-ttu-id="a31fc-110">Application Insights 是可延伸的應用程式效能管理 (APM) 服務的 web 開發人員在多個平台上運作。</span><span class="sxs-lookup"><span data-stu-id="a31fc-110">Application Insights is an extensible Application Performance Management (APM) service for web developers who work on multiple platforms.</span></span> <span data-ttu-id="a31fc-111">您可以使用它來監視即時 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a31fc-111">Use it to monitor your live web application.</span></span> <span data-ttu-id="a31fc-112">Application Insights 會自動偵測效能異常。</span><span class="sxs-lookup"><span data-stu-id="a31fc-112">Application Insights automatically detects performance anomalies.</span></span> <span data-ttu-id="a31fc-113">其中包括強大的分析工具可協助您診斷問題，並可協助您了解使用者實際如何運用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a31fc-113">It includes powerful analytics tools to help you diagnose issues, and to help you understand what users actually do with your app.</span></span> <span data-ttu-id="a31fc-114">Application Insights 可協助您持續改善效能和可用性。</span><span class="sxs-lookup"><span data-stu-id="a31fc-114">Application Insights is designed to help you continuously improve performance and usability.</span></span> <span data-ttu-id="a31fc-115">它適用於應用程式在各種不同的平台，包括.NET、 Node.js 和 J2EE，是否裝載於內部部署或雲端中。</span><span class="sxs-lookup"><span data-stu-id="a31fc-115">It works for apps on a wide variety of platforms, including .NET, Node.js, and J2EE, whether hosted on-premises or in the cloud.</span></span> <span data-ttu-id="a31fc-116">Application Insights 整合您的 DevOps 程序，並有各種不同的開發工具的連接點。</span><span class="sxs-lookup"><span data-stu-id="a31fc-116">Application Insights integrates with your DevOps processes, and has connection points to a variety of development tools.</span></span>

<span data-ttu-id="a31fc-117">圖 4-10 說明 Application Insights 監視您的應用程式的方式，和如何它的儀表板，會在呈現這些深入資訊時的範例。</span><span class="sxs-lookup"><span data-stu-id="a31fc-117">Figure 4-10 shows an example of how Application Insights monitors your application and how it surfaces those insights to a dashboard.</span></span>

![Application Insights 監視儀表板](./media/image10.png)

> <span data-ttu-id="a31fc-119">**圖 4-10。**</span><span class="sxs-lookup"><span data-stu-id="a31fc-119">**Figure 4-10.**</span></span> <span data-ttu-id="a31fc-120">Application Insights 監視儀表板</span><span class="sxs-lookup"><span data-stu-id="a31fc-120">Application Insights monitoring dashboard</span></span>

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a><span data-ttu-id="a31fc-121">監視您的 Docker 基礎結構，與 Log Analytics 和其容器監視解決方案</span><span class="sxs-lookup"><span data-stu-id="a31fc-121">Monitor your Docker infrastructure with Log Analytics and its Container Monitoring solution</span></span>

<span data-ttu-id="a31fc-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)屬於[Microsoft Azure 整體監視解決方案](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)。</span><span class="sxs-lookup"><span data-stu-id="a31fc-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) is part of the [Microsoft Azure overall monitoring solution](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span></span> <span data-ttu-id="a31fc-123">它也是服務[Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)。</span><span class="sxs-lookup"><span data-stu-id="a31fc-123">It's also a service in [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span></span> <span data-ttu-id="a31fc-124">Log Analytics 監視雲端和內部部署環境 (如內部部署的 OMS) 以協助維護可用性和效能。</span><span class="sxs-lookup"><span data-stu-id="a31fc-124">Log Analytics monitors cloud and on-premises environments (OMS for on-premises) to help maintain availability and performance.</span></span> <span data-ttu-id="a31fc-125">它會收集您的雲端和內部部署環境以及從其他監視工具，以分析跨多個來源的資源所產生的資料。</span><span class="sxs-lookup"><span data-stu-id="a31fc-125">It collects data generated by resources in your cloud and on-premises environments and from other monitoring tools to provide analysis across multiple sources.</span></span>

<span data-ttu-id="a31fc-126">Azure 基礎結構記錄檔，與 Log Analytics，做為 Azure 服務，內嵌來自其他 Azure 服務的記錄和計量資料 (透過[Azure 監視器](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor))，Azure Vm、 Docker 容器，並在內部部署環境或其他雲端基礎結構。</span><span class="sxs-lookup"><span data-stu-id="a31fc-126">In relation to Azure infrastructure logs, Log Analytics, as an Azure service, ingests log and metric data from other Azure services (via [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure VMs, Docker containers, and on-premises or other cloud infrastructures.</span></span> <span data-ttu-id="a31fc-127">Log Analytics 提供彈性的記錄搜尋和外的分析此資料。</span><span class="sxs-lookup"><span data-stu-id="a31fc-127">Log Analytics offers flexible log search and out-of-the box analytics on top of this data.</span></span> <span data-ttu-id="a31fc-128">它提供豐富的工具，可用來跨來源分析資料、 允許跨所有記錄，將複雜的查詢，它可以主動警示會根據指定的條件。</span><span class="sxs-lookup"><span data-stu-id="a31fc-128">It provides rich tools that you can use to analyze data across sources, it allows complex queries across all logs, and it can proactively alert based on specified conditions.</span></span> <span data-ttu-id="a31fc-129">您甚至可以在中央 Log Analytics 儲存機制，您可以在此查詢，並將其視覺化的自訂資料收集。</span><span class="sxs-lookup"><span data-stu-id="a31fc-129">You can even collect custom data in the central Log Analytics repository, where you can query and visualize it.</span></span> <span data-ttu-id="a31fc-130">您也可以充分利用 Log Analytics 內建解決方案，可以立即從中取得深入了解安全性和基礎結構的功能。</span><span class="sxs-lookup"><span data-stu-id="a31fc-130">You also can take advantage of the Log Analytics built-in solutions to immediately gain insights into the security and functionality of your infrastructure.</span></span>

<span data-ttu-id="a31fc-131">您可以透過 OMS 入口網站或 Azure 入口網站，在任何瀏覽器中執行，存取 Log Analytics，並提供您存取組態設定和多個工具來分析及處理收集到的資料。</span><span class="sxs-lookup"><span data-stu-id="a31fc-131">You can access Log Analytics through the OMS portal or the Azure portal, which run in any browser, and provide you with access to configuration settings and multiple tools to analyze and act on collected data.</span></span>

<span data-ttu-id="a31fc-132">[容器監視解決方案](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)Log Analytics 可以協助您檢視和管理您的 Docker 和 Windows 容器主機，在單一位置。</span><span class="sxs-lookup"><span data-stu-id="a31fc-132">The [Container Monitoring solution](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) in Log Analytics helps you view and manage your Docker and Windows Container hosts in a single location.</span></span> <span data-ttu-id="a31fc-133">解決方案會顯示哪些容器正在執行，哪些容器映像它們執行，以及容器執行的位置。</span><span class="sxs-lookup"><span data-stu-id="a31fc-133">The solution shows which containers are running, what container image they're running, and where containers are running.</span></span> <span data-ttu-id="a31fc-134">您可以檢視詳細的稽核資訊，包括容器正在使用的命令。</span><span class="sxs-lookup"><span data-stu-id="a31fc-134">You can view detailed audit information, including commands that are being used with containers.</span></span> <span data-ttu-id="a31fc-135">您也可以對容器進行疑難排解檢視及搜尋集中式記錄檔，而不需要從遠端檢視 Docker 或 Windows 的主機。</span><span class="sxs-lookup"><span data-stu-id="a31fc-135">You also can troubleshoot containers by viewing and searching centralized logs, without needing to remotely view Docker or Windows hosts.</span></span> <span data-ttu-id="a31fc-136">您可以找到可能會有雜訊且耗用過多的資源，在主機上的容器。</span><span class="sxs-lookup"><span data-stu-id="a31fc-136">You can find containers that might be noisy and consuming excess resources on a host.</span></span> <span data-ttu-id="a31fc-137">此外，您可以檢視集中式的 CPU、 記憶體、 儲存體和網路使用量和適用於容器的效能資訊。</span><span class="sxs-lookup"><span data-stu-id="a31fc-137">Additionally, you can view centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span> <span data-ttu-id="a31fc-138">在執行 Windows 的電腦，您可以集中管理，並比較記錄檔從 Windows Server、 HYPER-V 和 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="a31fc-138">On computers running Windows, you can centralize and compare logs from Windows Server, Hyper-V, and Docker containers.</span></span> <span data-ttu-id="a31fc-139">解決方案支援下列容器協調者：</span><span class="sxs-lookup"><span data-stu-id="a31fc-139">The solution supports the following container orchestrators:</span></span>

- <span data-ttu-id="a31fc-140">Docker Swarm</span><span class="sxs-lookup"><span data-stu-id="a31fc-140">Docker Swarm</span></span>

- <span data-ttu-id="a31fc-141">DC/OS</span><span class="sxs-lookup"><span data-stu-id="a31fc-141">DC/OS</span></span>

- <span data-ttu-id="a31fc-142">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a31fc-142">Kubernetes</span></span>

- <span data-ttu-id="a31fc-143">Service Fabric</span><span class="sxs-lookup"><span data-stu-id="a31fc-143">Service Fabric</span></span>

- <span data-ttu-id="a31fc-144">Red Hat OpenShift</span><span class="sxs-lookup"><span data-stu-id="a31fc-144">Red Hat OpenShift</span></span>

<span data-ttu-id="a31fc-145">圖 4-11 說明各種不同的容器主機和代理程式和 OMS 之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="a31fc-145">Figure 4-11 shows the relationships between various container hosts and agents and OMS.</span></span>

![Log Analytics 容器監視解決方案](./media/image11.png)

> <span data-ttu-id="a31fc-147">**圖 4-11。**</span><span class="sxs-lookup"><span data-stu-id="a31fc-147">**Figure 4-11.**</span></span> <span data-ttu-id="a31fc-148">Log Analytics 容器監視解決方案</span><span class="sxs-lookup"><span data-stu-id="a31fc-148">Log Analytics Container Monitoring solution</span></span>

<span data-ttu-id="a31fc-149">您可以使用 Log Analytics 容器監視解決方案：</span><span class="sxs-lookup"><span data-stu-id="a31fc-149">You can use the Log Analytics Container Monitoring solution to:</span></span>

- <span data-ttu-id="a31fc-150">請參閱在單一位置中的所有容器主機的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a31fc-150">See information about all container hosts in a single location.</span></span>

- <span data-ttu-id="a31fc-151">了解哪些容器正在執行，就會有何種映像它們執行，並正在執行的所在。</span><span class="sxs-lookup"><span data-stu-id="a31fc-151">Know which containers are running, what image they're running, and where they're running.</span></span>

- <span data-ttu-id="a31fc-152">容器，請參閱動作的稽核線索。</span><span class="sxs-lookup"><span data-stu-id="a31fc-152">See an audit trail for actions on containers.</span></span>

- <span data-ttu-id="a31fc-153">檢視及搜尋集中式記錄檔，而不需要 Docker 主機的遠端登入進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="a31fc-153">Troubleshoot by viewing and searching centralized logs without remote login to the Docker hosts.</span></span>

- <span data-ttu-id="a31fc-154">尋找可能 「 吵雜的芳鄰 」，而且會耗用過多的資源，在主機上的容器。</span><span class="sxs-lookup"><span data-stu-id="a31fc-154">Find containers that might be "noisy neighbors," and be consuming excess resources on a host.</span></span>

- <span data-ttu-id="a31fc-155">集中式的 CPU、 記憶體、 儲存體和網路使用量和適用於容器的效能資訊檢視。</span><span class="sxs-lookup"><span data-stu-id="a31fc-155">View centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a31fc-156">其他資源</span><span class="sxs-lookup"><span data-stu-id="a31fc-156">Additional resources</span></span>

- <span data-ttu-id="a31fc-157">**Microsoft Azure 中的監視概觀**</span><span class="sxs-lookup"><span data-stu-id="a31fc-157">**Overview of monitoring in Microsoft Azure**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="a31fc-158">**什麼是 Application Insights？**</span><span class="sxs-lookup"><span data-stu-id="a31fc-158">**What is Application Insights?**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="a31fc-159">**什麼是 Log Analytics？**</span><span class="sxs-lookup"><span data-stu-id="a31fc-159">**What is Log Analytics?**</span></span>

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- <span data-ttu-id="a31fc-160">**Azure 監視器中的容器監視解決方案**</span><span class="sxs-lookup"><span data-stu-id="a31fc-160">**Container Monitoring solution in Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- <span data-ttu-id="a31fc-161">**Azure 監視器概觀**</span><span class="sxs-lookup"><span data-stu-id="a31fc-161">**Overview of Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="a31fc-162">**什麼是 Operations Management Suite (OMS)？**</span><span class="sxs-lookup"><span data-stu-id="a31fc-162">**What is Operations Management Suite (OMS)?**</span></span>

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

- <span data-ttu-id="a31fc-163">**監視 Service Fabric 與 OMS 中的 Windows Server 容器**</span><span class="sxs-lookup"><span data-stu-id="a31fc-163">**Monitoring Windows Server containers in Service Fabric with OMS**</span></span>

<https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver>

>[!div class="step-by-step"]
><span data-ttu-id="a31fc-164">[上一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[下一頁](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="a31fc-164">[Previous](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Next](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span></span>
