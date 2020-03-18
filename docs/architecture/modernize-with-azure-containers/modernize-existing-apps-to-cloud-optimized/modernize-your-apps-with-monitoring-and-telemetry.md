---
title: 使用監視和遙測將應用程式現代化
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |通過監視和遙測實現應用現代化
ms.date: 04/30/2018
ms.openlocfilehash: 3d629e89a73c870d4b6396c6b1d0ecbe95b79ead
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393858"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a><span data-ttu-id="7ee1c-103">使用監視和遙測將應用程式現代化</span><span class="sxs-lookup"><span data-stu-id="7ee1c-103">Modernize your apps with monitoring and telemetry</span></span>

<span data-ttu-id="7ee1c-104">在生產中運行應用程式時，瞭解應用程式的性能至關重要。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-104">When you run an application in production, it's critical that you have insights about how your application is performing.</span></span> <span data-ttu-id="7ee1c-105">性能是否較高？</span><span class="sxs-lookup"><span data-stu-id="7ee1c-105">Is it performing at a high level?</span></span> <span data-ttu-id="7ee1c-106">使用者是否收到錯誤，或者應用程式是否穩定可靠？</span><span class="sxs-lookup"><span data-stu-id="7ee1c-106">Are users getting errors, or is the application stable and reliable?</span></span> <span data-ttu-id="7ee1c-107">您需要豐富的效能監控、強大的警報和儀表板，以説明確保應用程式可用並按預期運行。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-107">You need rich performance monitoring, powerful alerting, and dashboards to help ensure that your application is available and performing as expected.</span></span> <span data-ttu-id="7ee1c-108">您還需要能夠快速查看是否存在問題，確定受影響的客戶數，並執行根本原因分析以查找和解決問題。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-108">You also need to be able to see quickly if there's a problem, determine how many customers are affected, and perform a root-cause analysis to find and fix the issue.</span></span>

## <a name="monitor-your-application-with-application-insights"></a><span data-ttu-id="7ee1c-109">使用應用程式見解監控應用程式</span><span class="sxs-lookup"><span data-stu-id="7ee1c-109">Monitor your application with Application Insights</span></span>

<span data-ttu-id="7ee1c-110">應用程式見解是一種可擴展的應用程式性能管理 （APM） 服務，適用于在多個平臺上工作的 Web 開發人員。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-110">Application Insights is an extensible Application Performance Management (APM) service for web developers who work on multiple platforms.</span></span> <span data-ttu-id="7ee1c-111">您可以使用它來監視即時 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-111">Use it to monitor your live web application.</span></span> <span data-ttu-id="7ee1c-112">應用程式見解可自動檢測性能異常。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-112">Application Insights automatically detects performance anomalies.</span></span> <span data-ttu-id="7ee1c-113">它包括強大的分析工具，可説明您診斷問題，並説明您瞭解使用者實際使用你的應用做什麼。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-113">It includes powerful analytics tools to help you diagnose issues, and to help you understand what users actually do with your app.</span></span> <span data-ttu-id="7ee1c-114">Application Insights 設計用來協助您持續改善效能和可用性。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-114">Application Insights is designed to help you continuously improve performance and usability.</span></span> <span data-ttu-id="7ee1c-115">它適用于各種平臺上的應用，包括 .NET、Node.js 和 J2EE，無論是本地託管還是雲中託管。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-115">It works for apps on a wide variety of platforms, including .NET, Node.js, and J2EE, whether hosted on-premises or in the cloud.</span></span> <span data-ttu-id="7ee1c-116">應用程式見解與您的 DevOps 流程集成，並具有與各種開發工具的連接點。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-116">Application Insights integrates with your DevOps processes, and has connection points to a variety of development tools.</span></span>

<span data-ttu-id="7ee1c-117">圖 4-10 顯示了應用程式見解如何監視應用程式以及如何將這些見解顯示到儀表板的示例。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-117">Figure 4-10 shows an example of how Application Insights monitors your application and how it surfaces those insights to a dashboard.</span></span>

![應用程式見解監視儀表板的螢幕截圖。](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

<span data-ttu-id="7ee1c-119">**圖 4-10。**</span><span class="sxs-lookup"><span data-stu-id="7ee1c-119">**Figure 4-10.**</span></span> <span data-ttu-id="7ee1c-120">應用程式洞察監控儀表板</span><span class="sxs-lookup"><span data-stu-id="7ee1c-120">Application Insights monitoring dashboard</span></span>

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a><span data-ttu-id="7ee1c-121">使用日誌分析及其容器監視解決方案監視 Docker 基礎結構</span><span class="sxs-lookup"><span data-stu-id="7ee1c-121">Monitor your Docker infrastructure with Log Analytics and its Container Monitoring solution</span></span>

<span data-ttu-id="7ee1c-122">[Azure 日誌分析](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)是[Microsoft Azure 整體監視解決方案](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)的一部分。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) is part of the [Microsoft Azure overall monitoring solution](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span></span> <span data-ttu-id="7ee1c-123">這也是[運營管理套件 （OMS） 中的](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)服務。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-123">It's also a service in [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span></span> <span data-ttu-id="7ee1c-124">日誌分析監控雲和本地環境（用於本地的 OMS），以説明維護可用性和性能。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-124">Log Analytics monitors cloud and on-premises environments (OMS for on-premises) to help maintain availability and performance.</span></span> <span data-ttu-id="7ee1c-125">它會收集您的雲端和內部部署環境中的資源所產生的資料，以及從其他監視工具提供橫跨多個來源的分析。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-125">It collects data generated by resources in your cloud and on-premises environments and from other monitoring tools to provide analysis across multiple sources.</span></span>

<span data-ttu-id="7ee1c-126">相對於 Azure 基礎結構日誌，日誌分析作為 Azure 服務，從其他 Azure 服務（通過[Azure 監視器](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)）、Azure VM、Docker 容器以及本地或其他雲基礎結構引入日誌和指標資料。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-126">In relation to Azure infrastructure logs, Log Analytics, as an Azure service, ingests log and metric data from other Azure services (via [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure VMs, Docker containers, and on-premises or other cloud infrastructures.</span></span> <span data-ttu-id="7ee1c-127">日誌分析提供靈活的日誌搜索和開箱即用的分析。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-127">Log Analytics offers flexible log search and out-of-the box analytics on top of this data.</span></span> <span data-ttu-id="7ee1c-128">它提供了豐富的工具，可用於分析跨源的資料，它允許跨所有日誌進行複雜的查詢，並且它可以根據指定條件主動發出警報。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-128">It provides rich tools that you can use to analyze data across sources, it allows complex queries across all logs, and it can proactively alert based on specified conditions.</span></span> <span data-ttu-id="7ee1c-129">您甚至可以在中央日誌分析存儲庫中收集自訂資料，您可以在其中查詢和視覺化這些資料。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-129">You can even collect custom data in the central Log Analytics repository, where you can query and visualize it.</span></span> <span data-ttu-id="7ee1c-130">您還可以利用日誌分析內置解決方案立即深入瞭解基礎架構的安全性和功能。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-130">You also can take advantage of the Log Analytics built-in solutions to immediately gain insights into the security and functionality of your infrastructure.</span></span>

<span data-ttu-id="7ee1c-131">您可以通過 OMS 門戶或在任何瀏覽器中運行的 Azure 門戶訪問日誌分析，並為您提供對配置設置和多個工具的存取權限，以分析和處理收集的資料。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-131">You can access Log Analytics through the OMS portal or the Azure portal, which run in any browser, and provide you with access to configuration settings and multiple tools to analyze and act on collected data.</span></span>

<span data-ttu-id="7ee1c-132">日誌分析中的[容器監視解決方案](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)可説明您在單個位置查看和管理 Docker 和 Windows 容器主機。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-132">The [Container Monitoring solution](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) in Log Analytics helps you view and manage your Docker and Windows Container hosts in a single location.</span></span> <span data-ttu-id="7ee1c-133">該解決方案顯示正在運行的容器、正在運行的容器映射以及容器的運行位置。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-133">The solution shows which containers are running, what container image they're running, and where containers are running.</span></span> <span data-ttu-id="7ee1c-134">您可以查看詳細的審核資訊，包括與容器一起使用的命令。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-134">You can view detailed audit information, including commands that are being used with containers.</span></span> <span data-ttu-id="7ee1c-135">您還可以通過查看和搜索集中式日誌來對容器進行故障排除，而無需遠端查看 Docker 或 Windows 主機。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-135">You also can troubleshoot containers by viewing and searching centralized logs, without needing to remotely view Docker or Windows hosts.</span></span> <span data-ttu-id="7ee1c-136">您可以找到可能嘈雜的容器，並在主機上消耗多餘的資源。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-136">You can find containers that might be noisy and consuming excess resources on a host.</span></span> <span data-ttu-id="7ee1c-137">此外，您還可以查看容器的集中式 CPU、記憶體、存儲和網路使用方式以及性能資訊。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-137">Additionally, you can view centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span> <span data-ttu-id="7ee1c-138">您可以在執行 Windows 的電腦上集中管理，並從 Windows Server、HYPER-V 和 Docker 容器比較記錄。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-138">On computers running Windows, you can centralize and compare logs from Windows Server, Hyper-V, and Docker containers.</span></span> <span data-ttu-id="7ee1c-139">解決方案支援下列容器協調者：</span><span class="sxs-lookup"><span data-stu-id="7ee1c-139">The solution supports the following container orchestrators:</span></span>

- <span data-ttu-id="7ee1c-140">Docker Swarm</span><span class="sxs-lookup"><span data-stu-id="7ee1c-140">Docker Swarm</span></span>

- <span data-ttu-id="7ee1c-141">DC/OS</span><span class="sxs-lookup"><span data-stu-id="7ee1c-141">DC/OS</span></span>

- <span data-ttu-id="7ee1c-142">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="7ee1c-142">Kubernetes</span></span>

- <span data-ttu-id="7ee1c-143">Red Hat OpenShift</span><span class="sxs-lookup"><span data-stu-id="7ee1c-143">Red Hat OpenShift</span></span>

<span data-ttu-id="7ee1c-144">圖 4-11 顯示了各種容器主機和代理與 OMS 之間的關係。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-144">Figure 4-11 shows the relationships between various container hosts and agents and OMS.</span></span>

![日誌分析容器監視解決方案的螢幕截圖。](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

<span data-ttu-id="7ee1c-146">**圖 4-11。**</span><span class="sxs-lookup"><span data-stu-id="7ee1c-146">**Figure 4-11.**</span></span> <span data-ttu-id="7ee1c-147">日誌分析容器監視解決方案</span><span class="sxs-lookup"><span data-stu-id="7ee1c-147">Log Analytics Container Monitoring solution</span></span>

<span data-ttu-id="7ee1c-148">您可以使用日誌分析容器監視解決方案：</span><span class="sxs-lookup"><span data-stu-id="7ee1c-148">You can use the Log Analytics Container Monitoring solution to:</span></span>

- <span data-ttu-id="7ee1c-149">查看有關單個位置中所有容器主機的資訊。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-149">See information about all container hosts in a single location.</span></span>

- <span data-ttu-id="7ee1c-150">瞭解正在運行的容器、正在運行的映射以及它們運行的位置。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-150">Know which containers are running, what image they're running, and where they're running.</span></span>

- <span data-ttu-id="7ee1c-151">有關容器上的操作，請參閱審核跟蹤。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-151">See an audit trail for actions on containers.</span></span>

- <span data-ttu-id="7ee1c-152">通過查看和搜索集中式日誌進行故障排除，而無需遠端登入到 Docker 主機。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-152">Troubleshoot by viewing and searching centralized logs without remote login to the Docker hosts.</span></span>

- <span data-ttu-id="7ee1c-153">查找可能是"嘈雜鄰居"的容器，並在主機上消耗多餘的資源。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-153">Find containers that might be "noisy neighbors," and be consuming excess resources on a host.</span></span>

- <span data-ttu-id="7ee1c-154">查看容器的集中式 CPU、記憶體、存儲和網路使用方式以及性能資訊。</span><span class="sxs-lookup"><span data-stu-id="7ee1c-154">View centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7ee1c-155">其他資源</span><span class="sxs-lookup"><span data-stu-id="7ee1c-155">Additional resources</span></span>

- <span data-ttu-id="7ee1c-156">**微軟 Azure 中的監視概述**</span><span class="sxs-lookup"><span data-stu-id="7ee1c-156">**Overview of monitoring in Microsoft Azure**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="7ee1c-157">**什麼是應用見解？**</span><span class="sxs-lookup"><span data-stu-id="7ee1c-157">**What is Application Insights?**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="7ee1c-158">**什麼是 Log Analytics？**</span><span class="sxs-lookup"><span data-stu-id="7ee1c-158">**What is Log Analytics?**</span></span>

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- <span data-ttu-id="7ee1c-159">**Azure 監視器中的容器監視解決方案**</span><span class="sxs-lookup"><span data-stu-id="7ee1c-159">**Container Monitoring solution in Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- <span data-ttu-id="7ee1c-160">**Azure 監視器的概觀**</span><span class="sxs-lookup"><span data-stu-id="7ee1c-160">**Overview of Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="7ee1c-161">**Operations Management Suite (OMS) 是什麼？**</span><span class="sxs-lookup"><span data-stu-id="7ee1c-161">**What is Operations Management Suite (OMS)?**</span></span>

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
><span data-ttu-id="7ee1c-162">[上一個](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[下一個](life-cycle-ci-cd-pipelines-devops-tools.md)</span><span class="sxs-lookup"><span data-stu-id="7ee1c-162">[Previous](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Next](life-cycle-ci-cd-pipelines-devops-tools.md)</span></span>
