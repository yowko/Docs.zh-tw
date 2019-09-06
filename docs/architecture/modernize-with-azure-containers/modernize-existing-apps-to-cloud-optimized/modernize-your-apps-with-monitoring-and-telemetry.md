---
title: 使用監視和遙測將應用程式現代化
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |使用監視和遙測將應用程式現代化
ms.date: 04/30/2018
ms.openlocfilehash: 65c464e27e326f6a60b4879ec787253dea019d92
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373958"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a><span data-ttu-id="c5e1e-103">使用監視和遙測將應用程式現代化</span><span class="sxs-lookup"><span data-stu-id="c5e1e-103">Modernize your apps with monitoring and telemetry</span></span>

<span data-ttu-id="c5e1e-104">當您在生產環境中執行應用程式時，請務必深入瞭解應用程式的執行方式。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-104">When you run an application in production, it's critical that you have insights about how your application is performing.</span></span> <span data-ttu-id="c5e1e-105">它在高階執行嗎？</span><span class="sxs-lookup"><span data-stu-id="c5e1e-105">Is it performing at a high level?</span></span> <span data-ttu-id="c5e1e-106">使用者是否遇到錯誤，或是應用程式穩定且可靠？</span><span class="sxs-lookup"><span data-stu-id="c5e1e-106">Are users getting errors, or is the application stable and reliable?</span></span> <span data-ttu-id="c5e1e-107">您需要豐富的效能監視、強大的警示和儀表板，以協助確保您的應用程式可供使用並如預期般執行。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-107">You need rich performance monitoring, powerful alerting, and dashboards to help ensure that your application is available and performing as expected.</span></span> <span data-ttu-id="c5e1e-108">如果發生問題、判斷有多少客戶受到影響，以及執行根本原因分析以找出問題並加以修正，您也必須能夠快速查看。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-108">You also need to be able to see quickly if there's a problem, determine how many customers are affected, and perform a root-cause analysis to find and fix the issue.</span></span>

## <a name="monitor-your-application-with-application-insights"></a><span data-ttu-id="c5e1e-109">使用 Application Insights 監視您的應用程式</span><span class="sxs-lookup"><span data-stu-id="c5e1e-109">Monitor your application with Application Insights</span></span>

<span data-ttu-id="c5e1e-110">Application Insights 是可延伸的應用程式效能管理（APM）服務，適用于在多個平臺上工作的 網頁程式開發人員。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-110">Application Insights is an extensible Application Performance Management (APM) service for web developers who work on multiple platforms.</span></span> <span data-ttu-id="c5e1e-111">使用它來監視您的即時 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-111">Use it to monitor your live web application.</span></span> <span data-ttu-id="c5e1e-112">Application Insights 會自動偵測效能異常。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-112">Application Insights automatically detects performance anomalies.</span></span> <span data-ttu-id="c5e1e-113">其中包含功能強大的分析工具，可協助您診斷問題，並協助您瞭解使用者實際上如何使用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-113">It includes powerful analytics tools to help you diagnose issues, and to help you understand what users actually do with your app.</span></span> <span data-ttu-id="c5e1e-114">Application Insights 的設計可協助您持續改善效能和可用性。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-114">Application Insights is designed to help you continuously improve performance and usability.</span></span> <span data-ttu-id="c5e1e-115">它適用于各種平臺上的應用程式，包括 .NET、node.js 和 J2EE，不論是裝載于內部部署或雲端。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-115">It works for apps on a wide variety of platforms, including .NET, Node.js, and J2EE, whether hosted on-premises or in the cloud.</span></span> <span data-ttu-id="c5e1e-116">Application Insights 與您的 DevOps 流程整合，並具有各種開發工具的連接點。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-116">Application Insights integrates with your DevOps processes, and has connection points to a variety of development tools.</span></span>

<span data-ttu-id="c5e1e-117">圖4-10 顯示 Application Insights 如何監視您的應用程式，以及它如何將這些深入解析加入儀表板的範例。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-117">Figure 4-10 shows an example of how Application Insights monitors your application and how it surfaces those insights to a dashboard.</span></span>

![Application Insights 監視儀表板](./media/image10.png)

<span data-ttu-id="c5e1e-119">**圖4-10。**</span><span class="sxs-lookup"><span data-stu-id="c5e1e-119">**Figure 4-10.**</span></span> <span data-ttu-id="c5e1e-120">Application Insights 監視儀表板</span><span class="sxs-lookup"><span data-stu-id="c5e1e-120">Application Insights monitoring dashboard</span></span>

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a><span data-ttu-id="c5e1e-121">使用 Log Analytics 和其容器監視解決方案監視您的 Docker 基礎結構</span><span class="sxs-lookup"><span data-stu-id="c5e1e-121">Monitor your Docker infrastructure with Log Analytics and its Container Monitoring solution</span></span>

<span data-ttu-id="c5e1e-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)是[Microsoft Azure 整體監視解決方案](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)的一部分。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) is part of the [Microsoft Azure overall monitoring solution](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span></span> <span data-ttu-id="c5e1e-123">它也是[Operations Management Suite （OMS）](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)中的一項服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-123">It's also a service in [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span></span> <span data-ttu-id="c5e1e-124">Log Analytics 會監視雲端和內部部署環境（適用于內部部署的 OMS），以協助維護可用性和效能。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-124">Log Analytics monitors cloud and on-premises environments (OMS for on-premises) to help maintain availability and performance.</span></span> <span data-ttu-id="c5e1e-125">它會收集您的雲端和內部部署環境中的資源所產生的資料，以及從其他監視工具來提供跨多個來源的分析。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-125">It collects data generated by resources in your cloud and on-premises environments and from other monitoring tools to provide analysis across multiple sources.</span></span>

<span data-ttu-id="c5e1e-126">相對於 Azure 基礎結構記錄檔，Log Analytics 是 Azure 服務，可從其他 Azure 服務（透過[Azure 監視器](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)）、Azure Vm、Docker 容器，以及內部部署或其他雲端基礎結構內嵌記錄和計量資料。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-126">In relation to Azure infrastructure logs, Log Analytics, as an Azure service, ingests log and metric data from other Azure services (via [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure VMs, Docker containers, and on-premises or other cloud infrastructures.</span></span> <span data-ttu-id="c5e1e-127">Log Analytics 提供彈性的記錄搜尋，以及此資料之上的現成分析。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-127">Log Analytics offers flexible log search and out-of-the box analytics on top of this data.</span></span> <span data-ttu-id="c5e1e-128">它提供豐富的工具，讓您用來跨來源分析資料、允許跨所有記錄進行複雜的查詢，而且可以根據指定的條件主動發出警示。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-128">It provides rich tools that you can use to analyze data across sources, it allows complex queries across all logs, and it can proactively alert based on specified conditions.</span></span> <span data-ttu-id="c5e1e-129">您甚至可以在中央 Log Analytics 存放庫中收集自訂資料，您可以在其中查詢並將其視覺化。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-129">You can even collect custom data in the central Log Analytics repository, where you can query and visualize it.</span></span> <span data-ttu-id="c5e1e-130">您也可以利用 Log Analytics 內建解決方案，立即深入瞭解基礎結構的安全性和功能。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-130">You also can take advantage of the Log Analytics built-in solutions to immediately gain insights into the security and functionality of your infrastructure.</span></span>

<span data-ttu-id="c5e1e-131">您可以透過 OMS 入口網站或 Azure 入口網站（在任何瀏覽器中執行）存取 Log Analytics，並讓您存取設定和多項工具來分析及處理所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-131">You can access Log Analytics through the OMS portal or the Azure portal, which run in any browser, and provide you with access to configuration settings and multiple tools to analyze and act on collected data.</span></span>

<span data-ttu-id="c5e1e-132">Log Analytics 中的[容器監視解決方案](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)可協助您在單一位置中，查看及管理您的 Docker 和 Windows 容器主機。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-132">The [Container Monitoring solution](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) in Log Analytics helps you view and manage your Docker and Windows Container hosts in a single location.</span></span> <span data-ttu-id="c5e1e-133">解決方案會顯示哪些容器正在執行、其執行所在的容器映射，以及容器的執行位置。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-133">The solution shows which containers are running, what container image they're running, and where containers are running.</span></span> <span data-ttu-id="c5e1e-134">您可以查看詳細的審核資訊，包括與容器搭配使用的命令。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-134">You can view detailed audit information, including commands that are being used with containers.</span></span> <span data-ttu-id="c5e1e-135">您也可以藉由查看及搜尋集中式記錄來對容器進行疑難排解，而不需要遠端查看 Docker 或 Windows 主機。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-135">You also can troubleshoot containers by viewing and searching centralized logs, without needing to remotely view Docker or Windows hosts.</span></span> <span data-ttu-id="c5e1e-136">您可以在主機上找到可能有雜訊和耗用過量資源的容器。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-136">You can find containers that might be noisy and consuming excess resources on a host.</span></span> <span data-ttu-id="c5e1e-137">此外，您可以針對容器來查看集中式 CPU、記憶體、儲存體和網路使用量，以及效能資訊。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-137">Additionally, you can view centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span> <span data-ttu-id="c5e1e-138">在執行 Windows 的電腦上，您可以集中化和比較 Windows Server、Hyper-v 和 Docker 容器的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-138">On computers running Windows, you can centralize and compare logs from Windows Server, Hyper-V, and Docker containers.</span></span> <span data-ttu-id="c5e1e-139">此解決方案支援下列容器協調器：</span><span class="sxs-lookup"><span data-stu-id="c5e1e-139">The solution supports the following container orchestrators:</span></span>

- <span data-ttu-id="c5e1e-140">Docker Swarm</span><span class="sxs-lookup"><span data-stu-id="c5e1e-140">Docker Swarm</span></span>

- <span data-ttu-id="c5e1e-141">DC/OS</span><span class="sxs-lookup"><span data-stu-id="c5e1e-141">DC/OS</span></span>

- <span data-ttu-id="c5e1e-142">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="c5e1e-142">Kubernetes</span></span>

- <span data-ttu-id="c5e1e-143">Red Hat OpenShift</span><span class="sxs-lookup"><span data-stu-id="c5e1e-143">Red Hat OpenShift</span></span>

<span data-ttu-id="c5e1e-144">圖4-11 顯示各種容器主機和代理程式與 OMS 之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-144">Figure 4-11 shows the relationships between various container hosts and agents and OMS.</span></span>

![Log Analytics 容器監視解決方案](./media/image11.png)

<span data-ttu-id="c5e1e-146">**圖4-11。**</span><span class="sxs-lookup"><span data-stu-id="c5e1e-146">**Figure 4-11.**</span></span> <span data-ttu-id="c5e1e-147">Log Analytics 容器監視解決方案</span><span class="sxs-lookup"><span data-stu-id="c5e1e-147">Log Analytics Container Monitoring solution</span></span>

<span data-ttu-id="c5e1e-148">您可以使用 Log Analytics 容器監視解決方案來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c5e1e-148">You can use the Log Analytics Container Monitoring solution to:</span></span>

- <span data-ttu-id="c5e1e-149">請參閱單一位置中所有容器主機的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-149">See information about all container hosts in a single location.</span></span>

- <span data-ttu-id="c5e1e-150">知道哪些容器正在執行、它們正在執行哪些映射，以及它們在何處執行。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-150">Know which containers are running, what image they're running, and where they're running.</span></span>

- <span data-ttu-id="c5e1e-151">查看容器上動作的審核記錄。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-151">See an audit trail for actions on containers.</span></span>

- <span data-ttu-id="c5e1e-152">藉由在不遠端登入 Docker 主機的情況下，查看及搜尋集中式記錄來進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-152">Troubleshoot by viewing and searching centralized logs without remote login to the Docker hosts.</span></span>

- <span data-ttu-id="c5e1e-153">尋找可能是「有雜訊的鄰近專案」的容器，並耗用主機上的過量資源。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-153">Find containers that might be "noisy neighbors," and be consuming excess resources on a host.</span></span>

- <span data-ttu-id="c5e1e-154">針對容器，觀看集中化的 CPU、記憶體、儲存體和網路使用量，以及效能資訊。</span><span class="sxs-lookup"><span data-stu-id="c5e1e-154">View centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c5e1e-155">其他資源</span><span class="sxs-lookup"><span data-stu-id="c5e1e-155">Additional resources</span></span>

- <span data-ttu-id="c5e1e-156">**在 Microsoft Azure 中監視的總覽**</span><span class="sxs-lookup"><span data-stu-id="c5e1e-156">**Overview of monitoring in Microsoft Azure**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="c5e1e-157">**什麼是 Application Insights？**</span><span class="sxs-lookup"><span data-stu-id="c5e1e-157">**What is Application Insights?**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="c5e1e-158">**什麼是 Log Analytics？**</span><span class="sxs-lookup"><span data-stu-id="c5e1e-158">**What is Log Analytics?**</span></span>

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- <span data-ttu-id="c5e1e-159">**Azure 監視器中的容器監視解決方案**</span><span class="sxs-lookup"><span data-stu-id="c5e1e-159">**Container Monitoring solution in Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- <span data-ttu-id="c5e1e-160">**Azure 監視器總覽**</span><span class="sxs-lookup"><span data-stu-id="c5e1e-160">**Overview of Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="c5e1e-161">**何謂 Operations Management Suite （OMS）？**</span><span class="sxs-lookup"><span data-stu-id="c5e1e-161">**What is Operations Management Suite (OMS)?**</span></span>

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
><span data-ttu-id="c5e1e-162">[上一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[下一頁](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="c5e1e-162">[Previous](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Next](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span></span>
