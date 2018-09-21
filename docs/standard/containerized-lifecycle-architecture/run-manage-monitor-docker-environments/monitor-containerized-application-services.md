---
title: 監視容器化應用程式服務
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 4bdc4470624ce6e905ab858a2bd8b607c8d3d646
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46524924"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="9ef4e-103">監視容器化應用程式服務</span><span class="sxs-lookup"><span data-stu-id="9ef4e-103">Monitor containerized application services</span></span>

<span data-ttu-id="9ef4e-104">最重要的是應用程式分割成多個容器和微服務的方式，來監視及分析應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-104">It is critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the application.</span></span>

## <a name="microsoft-application-insights"></a><span data-ttu-id="9ef4e-105">Microsoft Application Insights</span><span class="sxs-lookup"><span data-stu-id="9ef4e-105">Microsoft Application Insights</span></span>

<span data-ttu-id="9ef4e-106">[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview)是可延伸分析服務，可監視您即時應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-106">[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="9ef4e-107">它可協助您偵測並診斷效能問題，並了解使用者實際如何運用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="9ef4e-108">它被專為開發人員，協助您持續改善效能的目的與您的服務或應用程式的可用性。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="9ef4e-109">Application Insights 可搭配 web/服務和獨立上各種不同的平台，例如.NET、 Java、 Node.js 和許多其他平台，裝載於內部部署或雲端中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-109">Application Insights works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a><span data-ttu-id="9ef4e-110">在 QA 環境中使用 Application Insights 分析的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="9ef4e-110">Analyzing Docker apps in QA environments using Application Insights</span></span>

<span data-ttu-id="9ef4e-111">因為它適用於 Docker，您可以圖表生命週期事件和從 Application Insights 上的 Docker 容器的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-111">As it pertains to Docker, you can chart life-cycle events and performance counters from Docker containers on Application Insights.</span></span> <span data-ttu-id="9ef4e-112">您只需要執行[Application Insights 的 Docker 映像](https://hub.docker.com/r/microsoft/applicationinsights/)如的容器中您的主機，它會顯示的主機，以及其他的 Docker 映像的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-112">You just need to run the [Application Insights Docker image](https://hub.docker.com/r/microsoft/applicationinsights/) as a container in your host, and it will display performance counters for the host as well as for the other Docker images.</span></span> <span data-ttu-id="9ef4e-113">此應用程式深入解析的 Docker 映像 (圖 6-1） 可協助您監視您的容器化應用程式所收集的效能和活動，您的 Docker 主機 (也就是您的 Linux Vm) 及 Docker 容器執行的應用程式的遙測在其中。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-113">This Application Insights Docker image (Figure 6-1) helps you to monitor your containerized applications by collecting telemetry about the performance and activity of your Docker host (that is, your Linux VMs), Docker containers and the applications running within them.</span></span>

![範例](./media/image1.png)

<span data-ttu-id="9ef4e-115">圖 6-1: Application Insights 監視 Docker 主機和容器</span><span class="sxs-lookup"><span data-stu-id="9ef4e-115">Figure 6-1: Application Insights monitoring Docker hosts and containers</span></span>

<span data-ttu-id="9ef4e-116">當您執行[Application Insights 的 Docker 映像](https://hub.docker.com/r/microsoft/applicationinsights/)上您的 Docker 主機，您可以從下列：</span><span class="sxs-lookup"><span data-stu-id="9ef4e-116">When you run the [Application Insights Docker image](https://hub.docker.com/r/microsoft/applicationinsights/) on your Docker host, you benefit from the following:</span></span>

-   <span data-ttu-id="9ef4e-117">生命週期主機上執行的所有容器的相關遙測-啟動、 停止和等等。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-117">Life-cycle telemetry about all the containers running on the host—start, stop, and so on.</span></span>

-   <span data-ttu-id="9ef4e-118">所有容器的效能計數器： CPU、 記憶體、 網路使用量，等等。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-118">Performance counters for all the containers: CPU, memory, network usage, and more.</span></span>

-   <span data-ttu-id="9ef4e-119">如果您也安裝了[Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)在容器中執行的應用程式，這些應用程式的所有遙測資料會識別容器和主機電腦的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-119">If you also installed [Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) in the apps running in the containers, all the telemetry of those apps will have additional properties identifying the container and host machine.</span></span> <span data-ttu-id="9ef4e-120">因此，比方說，如果您有一個以上的主控件上執行的應用程式的執行個體時，輕易地就能夠篩選由主應用程式的應用程式遙測。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-120">So, for example, if you have instances of an app running in more than one host, you'll easily be able to filter your app telemetry by host.</span></span>

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a><span data-ttu-id="9ef4e-121">設定 Application Insights 來監視 Docker 應用程式和 Docker 主機</span><span class="sxs-lookup"><span data-stu-id="9ef4e-121">Setting up Application Insights to monitor Docker applications and Docker hosts</span></span>

<span data-ttu-id="9ef4e-122">若要建立 Application Insights 資源，請遵循下列清單所述的文章中的指示。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-122">To create an Application Insights resource, follow the instructions in the articles presented in the list that follows.</span></span> <span data-ttu-id="9ef4e-123">Azure 入口網站會為您建立必要的指令碼。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-123">Azure Portal will create the necessary script for you.</span></span>

-   <span data-ttu-id="9ef4e-124">**在 Application Insights 中監視 Docker 應用程式：**  [https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)</span><span class="sxs-lookup"><span data-stu-id="9ef4e-124">**Monitor Docker applications in Application Insights:**  [https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)</span></span>

-   <span data-ttu-id="9ef4e-125">**在 Docker Hub 和 Github 應用程式深入解析的 Docker 映像：**</span><span class="sxs-lookup"><span data-stu-id="9ef4e-125">**Application Insights Docker image at Docker Hub and Github:**</span></span>  
<span data-ttu-id="9ef4e-126">[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) 和 <https://github.com/Microsoft/ApplicationInsights-Docker></span><span class="sxs-lookup"><span data-stu-id="9ef4e-126">[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) and <https://github.com/Microsoft/ApplicationInsights-Docker></span></span>

-   <span data-ttu-id="9ef4e-127">**設定適用於 ASP.NET 的 Application Insights:**</span><span class="sxs-lookup"><span data-stu-id="9ef4e-127">**Set up Application Insights for ASP.NET:**</span></span>  
[https://docs.microsoft.com/azure/application-insights/app-insights-asp-net](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   <span data-ttu-id="9ef4e-128">**適用於網頁的 application Insights:**</span><span class="sxs-lookup"><span data-stu-id="9ef4e-128">**Application Insights for web pages:**</span></span>  
<https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="microsoft-operations-management-suite"></a><span data-ttu-id="9ef4e-129">Microsoft Operations Management Suite</span><span class="sxs-lookup"><span data-stu-id="9ef4e-129">Microsoft Operations Management Suite</span></span>

<span data-ttu-id="9ef4e-130">[Operations Management Suite](https://microsoft.com/oms)是簡化的 IT 管理解決方案，提供 log analytics、 自動化、 備份和 site recovery。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-130">[Operations Management Suite](https://microsoft.com/oms) is a simplified IT management solution that provides log analytics, automation, backup, and site recovery.</span></span> <span data-ttu-id="9ef4e-131">根據[查詢](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/)在 Operations Management Suite，您可以提高[警示](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts)並設定透過補救[Azure 自動化](https://docs.microsoft.com/azure/automation/)。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-131">Based on [queries](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/) in Operations Management Suite, you can raise [alerts](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts) and set remediation via [Azure Automation](https://docs.microsoft.com/azure/automation/).</span></span> <span data-ttu-id="9ef4e-132">它也會順暢地整合與您現有的管理解決方案，以提供單一的半透明效果 窗格檢視。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-132">It also seamlessly integrates with your existing management solutions to provide a single pane-of-glass view.</span></span> <span data-ttu-id="9ef4e-133">Operations Management Suite 可協助您管理並保護您內部部署和雲端基礎結構。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-133">Operations Management Suite helps you to manage and protect your on-premises and cloud infrastructure.</span></span>

### <a name="operations-management-suitehttpsmicrosoftcomoms-container-solution-for-docker"></a><span data-ttu-id="9ef4e-134">[Operations Management Suite](https://microsoft.com/oms)適用於 Docker 的容器解決方案</span><span class="sxs-lookup"><span data-stu-id="9ef4e-134">[Operations Management Suite](https://microsoft.com/oms) Container Solution for Docker</span></span>

<span data-ttu-id="9ef4e-135">除了自行提供重要服務，Operations Management Suite 的容器解決方案管理和監視 Docker 主機和容器所顯示的詳細資訊，您的容器和容器主機，哪些容器正在執行或失敗，並傳送至 Docker 精靈和容器記錄*stdout*並*stderr*。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-135">In addition to providing valuable services on its own, the Operations Management Suite Container Solution can manage and monitor Docker hosts and containers by showing information about where your containers and container hosts are, which containers are running or failed, and Docker daemon and container logs sent to *stdout* and *stderr*.</span></span> <span data-ttu-id="9ef4e-136">它也會顯示效能計量 (例如容器和主機的 CPU、記憶體、網路和儲存體)，以協助您進行疑難排解，並找出有雜訊的鄰近容器。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-136">It also shows performance metrics such as CPU, memory, network, and storage for the container and hosts to help you troubleshoot and find noisy neighbor containers.</span></span>

![](./media/image2.png)

<span data-ttu-id="9ef4e-137">圖 6-2： 顯示 Operations Management suite 的 Docker 容器的資訊</span><span class="sxs-lookup"><span data-stu-id="9ef4e-137">Figure 6-2: Information about Docker containers shown by Operations Management Suite</span></span>

<span data-ttu-id="9ef4e-138">Application Insights 和 Operations Management Suite 焦點放在監視活動;不過，Application Insights 著重於更監視的應用程式本身由於其應用程式內執行的 SDK。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-138">Application Insights and Operations Management Suite both focus on monitoring activities; however, Application Insights focuses more on monitoring the apps themselves thanks to its SDK running within the app.</span></span> <span data-ttu-id="9ef4e-139">不過，Operations Management Suite 更著重於基礎結構主機，再加上它同時提供極具彈性的資料導向搜尋/查詢系統提供大規模的記錄檔的深入分析。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-139">However, Operations Management Suite focuses much more on the infrastructure around the hosts, plus it offers deep analysis on logs at scale while providing a very flexible data-driven search/query system.</span></span>

<span data-ttu-id="9ef4e-140">由於 Operations Management Suite 會實作為雲端服務中，您可以將它啟動並執行快速且最少的投資，基礎結構服務中。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-140">Because Operations Management Suite is implemented as a cloud-based service, you can have it up and running quickly with minimal investment in infrastructure services.</span></span> <span data-ttu-id="9ef4e-141">新功能會自動提供，以節省持續維護和升級成本。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-141">New features are delivered automatically, saving you from ongoing maintenance and upgrade costs.</span></span>

<span data-ttu-id="9ef4e-142">使用 Operations Management Suite 容器解決方案，您可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="9ef4e-142">Using Operations Management Suite Container Solution, you can do the following:</span></span>

-   <span data-ttu-id="9ef4e-143">集中管理，並將相互關聯數以百萬計的大規模的 Docker 容器記錄</span><span class="sxs-lookup"><span data-stu-id="9ef4e-143">Centralize and correlate millions of logs from Docker containers at scale</span></span>

-   <span data-ttu-id="9ef4e-144">請參閱在單一位置中的所有容器主機的相關資訊</span><span class="sxs-lookup"><span data-stu-id="9ef4e-144">See information about all container hosts in a single location</span></span>

-   <span data-ttu-id="9ef4e-145">了解哪些容器正在執行，就會有何種映像它們執行，並執行所在</span><span class="sxs-lookup"><span data-stu-id="9ef4e-145">Know which containers are running, what image they're running, and where they're running</span></span>

-   <span data-ttu-id="9ef4e-146">快速診斷可能會造成問題，在容器主機的 「 吵雜鄰居 」 容器</span><span class="sxs-lookup"><span data-stu-id="9ef4e-146">Quickly diagnose "noisy neighbor" containers that can cause problems on container hosts</span></span>

-   <span data-ttu-id="9ef4e-147">在容器上查看動作的稽核線索</span><span class="sxs-lookup"><span data-stu-id="9ef4e-147">See an audit trail for actions on containers</span></span>

-   <span data-ttu-id="9ef4e-148">檢視及搜尋集中式記錄檔，而不需要遠端 Docker 主機來進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="9ef4e-148">Troubleshoot by viewing and searching centralized logs without remoting to the Docker hosts</span></span>

-   <span data-ttu-id="9ef4e-149">尋找可能 「 吵雜芳鄰 」 且耗用過多的資源，在主機上的容器</span><span class="sxs-lookup"><span data-stu-id="9ef4e-149">Find containers that might be "noisy neighbors" and consuming excess resources on a host</span></span>

-   <span data-ttu-id="9ef4e-150">檢視集中式的 CPU、 記憶體、 儲存體，以及適用於容器的網路使用量和效能資訊</span><span class="sxs-lookup"><span data-stu-id="9ef4e-150">View centralized CPU, memory, storage, and network usage and performance information for containers</span></span>

-   <span data-ttu-id="9ef4e-151">產生測試使用 Azure 自動化的 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="9ef4e-151">Generate test Docker containers with Azure Automation</span></span>

<span data-ttu-id="9ef4e-152">您可以執行類似類型的查詢，以便查看效能資訊 = 效能，如所示的圖 6-3。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-152">You can see performance information by running queries like Type=Perf, as shown in Figure 6-3.</span></span>

![DockerPerfMetricsView](./media/image3.png)<span data-ttu-id="9ef4e-154">{width="5.78625in" height="3.25in"}</span><span class="sxs-lookup"><span data-stu-id="9ef4e-154">{width="5.78625in" height="3.25in"}</span></span>

<span data-ttu-id="9ef4e-155">圖 6-3： 效能度量的顯示 Operations Management suite 的 Docker 主機</span><span class="sxs-lookup"><span data-stu-id="9ef4e-155">Figure 6-3: Performance metrics of Docker hosts shown by Operations Management Suite</span></span>

<span data-ttu-id="9ef4e-156">儲存查詢也是 Operations Management Suite 中的標準功能，可協助您保留您認為有用，並找出您的系統中的趨勢的查詢。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-156">Saving queries is also a standard feature in Operations Management Suite and can help you keep queries you've found useful and discover trends in your system.</span></span>

<span data-ttu-id="9ef4e-157">**進一歩** 若要尋找有關安裝及設定 Docker 中的容器解決方案[Operations Management Suite](https://microsoft.com/oms)，請移至<https://docs.microsoft.com/azure/log-analytics/log-analytics-containers>。</span><span class="sxs-lookup"><span data-stu-id="9ef4e-157">**More info** To find information on installing and configuring the Docker container solution in [Operations Management Suite](https://microsoft.com/oms), go to <https://docs.microsoft.com/azure/log-analytics/log-analytics-containers>.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="9ef4e-158">[上一頁](manage-production-docker-environments.md)
[下一頁](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="9ef4e-158">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
