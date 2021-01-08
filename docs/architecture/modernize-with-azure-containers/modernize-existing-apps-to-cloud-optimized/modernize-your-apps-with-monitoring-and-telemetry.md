---
title: 使用監視和遙測將應用程式現代化
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |使用監視和遙測將應用程式現代化
ms.date: 12/21/2020
ms.openlocfilehash: c79a16400ce9dadca50fabb6c7df2859e4519a41
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025234"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a><span data-ttu-id="1bdc4-103">使用監視和遙測將應用程式現代化</span><span class="sxs-lookup"><span data-stu-id="1bdc4-103">Modernize your apps with monitoring and telemetry</span></span>

<span data-ttu-id="1bdc4-104">當您在生產環境中執行應用程式時，您必須深入瞭解應用程式的執行方式。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-104">When you run an application in production, it's critical that you have insights about how your application is performing.</span></span> <span data-ttu-id="1bdc4-105">它是以高層級執行嗎？</span><span class="sxs-lookup"><span data-stu-id="1bdc4-105">Is it performing at a high level?</span></span> <span data-ttu-id="1bdc4-106">使用者是否會收到錯誤，或應用程式穩定且可靠？</span><span class="sxs-lookup"><span data-stu-id="1bdc4-106">Are users getting errors, or is the application stable and reliable?</span></span> <span data-ttu-id="1bdc4-107">您需要豐富的效能監視、強大的警示和儀表板，以協助確保您的應用程式可供使用，並如預期般執行。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-107">You need rich performance monitoring, powerful alerting, and dashboards to help ensure that your application is available and performing as expected.</span></span> <span data-ttu-id="1bdc4-108">如果發生問題，您也必須能夠快速查看，判斷有多少客戶受到影響，並執行根本原因分析，以找出並修正問題。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-108">You also need to be able to see quickly if there's a problem, determine how many customers are affected, and perform a root-cause analysis to find and fix the issue.</span></span>

## <a name="monitor-your-application-with-application-insights"></a><span data-ttu-id="1bdc4-109">使用 Application Insights 監視您的應用程式</span><span class="sxs-lookup"><span data-stu-id="1bdc4-109">Monitor your application with Application Insights</span></span>

<span data-ttu-id="1bdc4-110">Application Insights 是適用于多個平臺的 網頁程式開發人員，可延伸的應用程式效能管理 (APM) 服務。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-110">Application Insights is an extensible Application Performance Management (APM) service for web developers who work on multiple platforms.</span></span> <span data-ttu-id="1bdc4-111">您可以使用它來監視即時 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-111">Use it to monitor your live web application.</span></span> <span data-ttu-id="1bdc4-112">Application Insights 會自動偵測效能異常。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-112">Application Insights automatically detects performance anomalies.</span></span> <span data-ttu-id="1bdc4-113">它包含強大的分析工具，可協助您診斷問題，並協助您瞭解使用者實際如何運用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-113">It includes powerful analytics tools to help you diagnose issues, and to help you understand what users actually do with your app.</span></span> <span data-ttu-id="1bdc4-114">Application Insights 設計用來協助您持續改善效能和可用性。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-114">Application Insights is designed to help you continuously improve performance and usability.</span></span> <span data-ttu-id="1bdc4-115">它適用于各種平臺上的應用程式，包括 .NET、Node.js 和 J2EE，無論是裝載于內部部署或雲端。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-115">It works for apps on a wide variety of platforms, including .NET, Node.js, and J2EE, whether hosted on-premises or in the cloud.</span></span> <span data-ttu-id="1bdc4-116">Application Insights 與您的 DevOps 程式整合，並有各種開發工具的連接點。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-116">Application Insights integrates with your DevOps processes, and has connection points to various development tools.</span></span>

<span data-ttu-id="1bdc4-117">圖4-10 顯示 Application Insights 如何監視您的應用程式，以及它如何向儀表板呈現這些深入解析的範例。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-117">Figure 4-10 shows an example of how Application Insights monitors your application and how it surfaces those insights to a dashboard.</span></span>

![Application Insights 監視儀表板的螢幕擷取畫面。](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

<span data-ttu-id="1bdc4-119">**圖4-10。**</span><span class="sxs-lookup"><span data-stu-id="1bdc4-119">**Figure 4-10.**</span></span> <span data-ttu-id="1bdc4-120">Application Insights 監視儀表板</span><span class="sxs-lookup"><span data-stu-id="1bdc4-120">Application Insights monitoring dashboard</span></span>

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a><span data-ttu-id="1bdc4-121">使用 Log Analytics 與其容器監視解決方案來監視您的 Docker 基礎結構</span><span class="sxs-lookup"><span data-stu-id="1bdc4-121">Monitor your Docker infrastructure with Log Analytics and its Container Monitoring solution</span></span>

<span data-ttu-id="1bdc4-122">[Azure Log Analytics](/azure/log-analytics/log-analytics-overview) 是 [Microsoft Azure 整體監視解決方案](/azure/monitoring-and-diagnostics/monitoring-overview)的一部分。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-122">[Azure Log Analytics](/azure/log-analytics/log-analytics-overview) is part of the [Microsoft Azure overall monitoring solution](/azure/monitoring-and-diagnostics/monitoring-overview).</span></span> <span data-ttu-id="1bdc4-123">它也是 [Operations Management Suite (OMS) ](/azure/operations-management-suite/operations-management-suite-overview)的服務。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-123">It's also a service in [Operations Management Suite (OMS)](/azure/operations-management-suite/operations-management-suite-overview).</span></span> <span data-ttu-id="1bdc4-124">Log Analytics 會監視雲端和內部部署環境 (OMS 進行內部部署) ，以協助維護可用性和效能。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-124">Log Analytics monitors cloud and on-premises environments (OMS for on-premises) to help maintain availability and performance.</span></span> <span data-ttu-id="1bdc4-125">它會收集您的雲端和內部部署環境中的資源所產生的資料，以及從其他監視工具提供橫跨多個來源的分析。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-125">It collects data generated by resources in your cloud and on-premises environments and from other monitoring tools to provide analysis across multiple sources.</span></span>

<span data-ttu-id="1bdc4-126">與 Azure 基礎結構記錄檔、Log Analytics 和 azure 服務相關，可透過 [Azure 監視器](/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)) 、Azure Vm、Docker 容器，以及內部部署或其他雲端基礎結構，從其他 Azure 服務 (內嵌記錄和度量資料。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-126">In relation to Azure infrastructure logs, Log Analytics, as an Azure service, ingests log and metric data from other Azure services (via [Azure Monitor](/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure VMs, Docker containers, and on-premises or other cloud infrastructures.</span></span> <span data-ttu-id="1bdc4-127">Log Analytics 提供彈性的記錄搜尋，以及此資料之上的現成分析。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-127">Log Analytics offers flexible log search and out-of-the box analytics on top of this data.</span></span> <span data-ttu-id="1bdc4-128">它提供豐富的工具，可讓您用來跨來源分析資料、允許跨所有記錄進行複雜的查詢，而且可以根據指定的條件主動發出警示。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-128">It provides rich tools that you can use to analyze data across sources, it allows complex queries across all logs, and it can proactively alert based on specified conditions.</span></span> <span data-ttu-id="1bdc4-129">您甚至可以在中央 Log Analytics 存放庫中收集自訂資料，您可以在其中進行查詢並將其視覺化。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-129">You can even collect custom data in the central Log Analytics repository, where you can query and visualize it.</span></span> <span data-ttu-id="1bdc4-130">您也可以利用 Log Analytics 內建解決方案來立即深入瞭解基礎結構的安全性和功能。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-130">You can also take advantage of the Log Analytics built-in solutions to immediately gain insights into the security and functionality of your infrastructure.</span></span>

<span data-ttu-id="1bdc4-131">您可以透過 OMS 入口網站或 Azure 入口網站（在任何瀏覽器中執行）來存取 Log Analytics，並讓您能夠存取設定和多個工具來分析及處理收集到的資料。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-131">You can access Log Analytics through the OMS portal or the Azure portal, which run in any browser, and provide you with access to configuration settings and multiple tools to analyze and act on collected data.</span></span>

<span data-ttu-id="1bdc4-132">Log Analytics 中的 [容器監視解決方案](/azure/log-analytics/log-analytics-containers) 可協助您在單一位置中查看和管理 Docker 和 Windows 容器主機。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-132">The [Container Monitoring solution](/azure/log-analytics/log-analytics-containers) in Log Analytics helps you view and manage your Docker and Windows Container hosts in a single location.</span></span> <span data-ttu-id="1bdc4-133">解決方案會顯示正在執行的容器、它們正在執行的容器映射，以及容器的執行位置。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-133">The solution shows which containers are running, what container image they're running, and where containers are running.</span></span> <span data-ttu-id="1bdc4-134">您可以查看詳細的審核資訊，包括搭配容器使用的命令。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-134">You can view detailed audit information, including commands that are being used with containers.</span></span> <span data-ttu-id="1bdc4-135">您也可以藉由查看及搜尋集中式記錄來疑難排解容器，而不需要遠端查看 Docker 或 Windows 主機。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-135">You can also troubleshoot containers by viewing and searching centralized logs, without needing to remotely view Docker or Windows hosts.</span></span> <span data-ttu-id="1bdc4-136">您可以找出可能有雜訊的容器，並在主機上耗用過度的資源。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-136">You can find containers that might be noisy and consuming excess resources on a host.</span></span> <span data-ttu-id="1bdc4-137">此外，您可以針對容器查看集中式 CPU、記憶體、儲存體和網路使用量，以及效能資訊。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-137">Additionally, you can view centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span> <span data-ttu-id="1bdc4-138">您可以在執行 Windows 的電腦上集中管理，並從 Windows Server、HYPER-V 和 Docker 容器比較記錄。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-138">On computers running Windows, you can centralize and compare logs from Windows Server, Hyper-V, and Docker containers.</span></span> <span data-ttu-id="1bdc4-139">解決方案支援下列容器協調者：</span><span class="sxs-lookup"><span data-stu-id="1bdc4-139">The solution supports the following container orchestrators:</span></span>

- <span data-ttu-id="1bdc4-140">Docker Swarm</span><span class="sxs-lookup"><span data-stu-id="1bdc4-140">Docker Swarm</span></span>

- <span data-ttu-id="1bdc4-141">DC/OS</span><span class="sxs-lookup"><span data-stu-id="1bdc4-141">DC/OS</span></span>

- <span data-ttu-id="1bdc4-142">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="1bdc4-142">Kubernetes</span></span>

- <span data-ttu-id="1bdc4-143">Red Hat OpenShift</span><span class="sxs-lookup"><span data-stu-id="1bdc4-143">Red Hat OpenShift</span></span>

<span data-ttu-id="1bdc4-144">圖4-11 顯示各種容器主機和代理程式與 OMS 之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-144">Figure 4-11 shows the relationships between various container hosts and agents and OMS.</span></span>

![Log Analytics 容器監視解決方案的螢幕擷取畫面。](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

<span data-ttu-id="1bdc4-146">**圖4-11。**</span><span class="sxs-lookup"><span data-stu-id="1bdc4-146">**Figure 4-11.**</span></span> <span data-ttu-id="1bdc4-147">Log Analytics 容器監視解決方案</span><span class="sxs-lookup"><span data-stu-id="1bdc4-147">Log Analytics Container Monitoring solution</span></span>

<span data-ttu-id="1bdc4-148">您可以使用 Log Analytics 容器監視解決方案來：</span><span class="sxs-lookup"><span data-stu-id="1bdc4-148">You can use the Log Analytics Container Monitoring solution to:</span></span>

- <span data-ttu-id="1bdc4-149">查看單一位置中所有容器主機的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-149">See information about all container hosts in a single location.</span></span>

- <span data-ttu-id="1bdc4-150">知道哪些容器正在執行、其正在執行的映射，以及執行的位置。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-150">Know which containers are running, what image they're running, and where they're running.</span></span>

- <span data-ttu-id="1bdc4-151">查看容器上動作的審核記錄。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-151">See an audit trail for actions on containers.</span></span>

- <span data-ttu-id="1bdc4-152">藉由在不遠端登入 Docker 主機的情況下，查看及搜尋集中式記錄來進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-152">Troubleshoot by viewing and searching centralized logs without remote login to the Docker hosts.</span></span>

- <span data-ttu-id="1bdc4-153">尋找可能是「有雜訊的鄰近專案」的容器，並在主機上耗用過度的資源。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-153">Find containers that might be "noisy neighbors," and be consuming excess resources on a host.</span></span>

- <span data-ttu-id="1bdc4-154">查看容器的集中式 CPU、記憶體、儲存體和網路使用量，以及效能資訊。</span><span class="sxs-lookup"><span data-stu-id="1bdc4-154">View centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1bdc4-155">其他資源</span><span class="sxs-lookup"><span data-stu-id="1bdc4-155">Additional resources</span></span>

- <span data-ttu-id="1bdc4-156">**Microsoft Azure 中的監視總覽**</span><span class="sxs-lookup"><span data-stu-id="1bdc4-156">**Overview of monitoring in Microsoft Azure**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="1bdc4-157">**什麼是 Application Insights？**</span><span class="sxs-lookup"><span data-stu-id="1bdc4-157">**What is Application Insights?**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="1bdc4-158">**什麼是 Log Analytics？**</span><span class="sxs-lookup"><span data-stu-id="1bdc4-158">**What is Log Analytics?**</span></span>

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- <span data-ttu-id="1bdc4-159">**Azure 監視器中的容器監視解決方案**</span><span class="sxs-lookup"><span data-stu-id="1bdc4-159">**Container Monitoring solution in Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- <span data-ttu-id="1bdc4-160">**Azure 監視器的概觀**</span><span class="sxs-lookup"><span data-stu-id="1bdc4-160">**Overview of Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="1bdc4-161">**Operations Management Suite (OMS) 是什麼？**</span><span class="sxs-lookup"><span data-stu-id="1bdc4-161">**What is Operations Management Suite (OMS)?**</span></span>

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
><span data-ttu-id="1bdc4-162">[上一個](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md) 
>[下一步](life-cycle-ci-cd-pipelines-devops-tools.md)</span><span class="sxs-lookup"><span data-stu-id="1bdc4-162">[Previous](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Next](life-cycle-ci-cd-pipelines-devops-tools.md)</span></span>
