---
title: 監視容器化應用程式服務
description: 了解一些重要的層面的監視容器架構
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 925db543617deb28590cf6631ebbda3ee96836c4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975741"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="fca1a-103">監視容器化應用程式服務</span><span class="sxs-lookup"><span data-stu-id="fca1a-103">Monitor containerized application services</span></span>

<span data-ttu-id="fca1a-104">最重要的是應用程式分割成多個容器和微服務的方式，來監視及分析整個應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="fca1a-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="microsoft-application-insights"></a><span data-ttu-id="fca1a-105">Microsoft Application Insights</span><span class="sxs-lookup"><span data-stu-id="fca1a-105">Microsoft Application Insights</span></span>

<span data-ttu-id="fca1a-106">[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview)是可延伸分析服務，可監視您即時應用程式。</span><span class="sxs-lookup"><span data-stu-id="fca1a-106">[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="fca1a-107">它可協助您偵測並診斷效能問題，並了解使用者實際如何運用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fca1a-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="fca1a-108">它被專為開發人員，協助您持續改善效能的目的與您的服務或應用程式的可用性。</span><span class="sxs-lookup"><span data-stu-id="fca1a-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="fca1a-109">Application Insights 可搭配 web/服務和獨立上各種不同的平台，例如.NET、 Java、 Node.js 和許多其他平台，裝載於內部部署或雲端中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fca1a-109">Application Insights works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a><span data-ttu-id="fca1a-110">在 QA 環境中使用 Application Insights 分析的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="fca1a-110">Analyzing Docker apps in QA environments using Application Insights</span></span>

<span data-ttu-id="fca1a-111">因為它適用於 Docker，您可以圖表生命週期事件和從 Application Insights 上的 Docker 容器的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="fca1a-111">As it pertains to Docker, you can chart life-cycle events and performance counters from Docker containers on Application Insights.</span></span> <span data-ttu-id="fca1a-112">您只需要執行[Application Insights 的 Docker 映像](https://hub.docker.com/r/microsoft/applicationinsights/)如的容器中您的主機，它會顯示的主機，以及其他的 Docker 映像的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="fca1a-112">You just need to run the [Application Insights Docker image](https://hub.docker.com/r/microsoft/applicationinsights/) as a container in your host, and it will display performance counters for the host as well as for the other Docker images.</span></span> <span data-ttu-id="fca1a-113">此應用程式深入解析的 Docker 映像 (圖 6-1） 可協助您監視您的容器化應用程式所收集的效能和活動，您的 Docker 主機 (也就是您的 Linux Vm) 及 Docker 容器執行的應用程式的遙測在其中。</span><span class="sxs-lookup"><span data-stu-id="fca1a-113">This Application Insights Docker image (Figure 6-1) helps you to monitor your containerized applications by collecting telemetry about the performance and activity of your Docker host (that is, your Linux VMs), Docker containers and the applications running within them.</span></span>

![範例](./media/image1.png)

<span data-ttu-id="fca1a-115">**圖 6-1**.</span><span class="sxs-lookup"><span data-stu-id="fca1a-115">**Figure 6-1**.</span></span> <span data-ttu-id="fca1a-116">Application Insights 監視 Docker 主機和容器</span><span class="sxs-lookup"><span data-stu-id="fca1a-116">Application Insights monitoring Docker hosts and containers</span></span>

<span data-ttu-id="fca1a-117">當您執行[Application Insights 的 Docker 映像](https://hub.docker.com/r/microsoft/applicationinsights/)上您的 Docker 主機，您可以從下列：</span><span class="sxs-lookup"><span data-stu-id="fca1a-117">When you run the [Application Insights Docker image](https://hub.docker.com/r/microsoft/applicationinsights/) on your Docker host, you benefit from the following:</span></span>

- <span data-ttu-id="fca1a-118">生命週期主機上執行的所有容器的相關遙測-啟動、 停止和等等。</span><span class="sxs-lookup"><span data-stu-id="fca1a-118">Life-cycle telemetry about all the containers running on the host—start, stop, and so on.</span></span>

- <span data-ttu-id="fca1a-119">所有容器的效能計數器：CPU、 記憶體、 網路使用量，等等。</span><span class="sxs-lookup"><span data-stu-id="fca1a-119">Performance counters for all the containers: CPU, memory, network usage, and more.</span></span>

- <span data-ttu-id="fca1a-120">如果您也安裝了[Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)在容器中執行的應用程式，這些應用程式的所有遙測資料會識別容器和主機電腦的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="fca1a-120">If you also installed [Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) in the apps running in the containers, all the telemetry of those apps will have additional properties identifying the container and host machine.</span></span> <span data-ttu-id="fca1a-121">因此，比方說，如果您有一個以上的主控件上執行的應用程式的執行個體時，輕易地就能夠篩選由主應用程式的應用程式遙測。</span><span class="sxs-lookup"><span data-stu-id="fca1a-121">So, for example, if you have instances of an app running in more than one host, you'll easily be able to filter your app telemetry by host.</span></span>

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a><span data-ttu-id="fca1a-122">設定 Application Insights 來監視 Docker 應用程式和 Docker 主機</span><span class="sxs-lookup"><span data-stu-id="fca1a-122">Setting up Application Insights to monitor Docker applications and Docker hosts</span></span>

<span data-ttu-id="fca1a-123">若要建立 Application Insights 資源，請遵循下列清單所述的文章中的指示。</span><span class="sxs-lookup"><span data-stu-id="fca1a-123">To create an Application Insights resource, follow the instructions in the articles presented in the list that follows.</span></span> <span data-ttu-id="fca1a-124">Azure 入口網站會為您建立必要的指令碼。</span><span class="sxs-lookup"><span data-stu-id="fca1a-124">Azure portal will create the necessary script for you.</span></span>

- <span data-ttu-id="fca1a-125">**在 Application Insights 中監視 Docker 應用程式：** \\</span><span class="sxs-lookup"><span data-stu-id="fca1a-125">**Monitor Docker applications in Application Insights:** \\</span></span>
  <https://docs.microsoft.com/azure/application-insights/app-insights-docker>

- <span data-ttu-id="fca1a-126">**在 Docker Hub 和 GitHub 應用程式深入解析的 Docker 映像：** \\</span><span class="sxs-lookup"><span data-stu-id="fca1a-126">**Application Insights Docker image at Docker Hub and GitHub:** \\</span></span>
  <span data-ttu-id="fca1a-127"><https://hub.docker.com/r/microsoft/applicationinsights/> 和 \\</span><span class="sxs-lookup"><span data-stu-id="fca1a-127"><https://hub.docker.com/r/microsoft/applicationinsights/> and \\</span></span>
  <https://github.com/Microsoft/ApplicationInsights-Docker>

- <span data-ttu-id="fca1a-128">**設定 ASP.NET web 應用程式和 ASP.NET Core 的 Application Insights:** \\</span><span class="sxs-lookup"><span data-stu-id="fca1a-128">**Set up Application Insights for ASP.NET web apps and ASP.NET Core:** \\</span></span>
  <https://docs.microsoft.com/azure/application-insights/app-insights-asp-net>

- <span data-ttu-id="fca1a-129">**適用於網頁的 application Insights:**</span><span class="sxs-lookup"><span data-stu-id="fca1a-129">**Application Insights for web pages:**</span></span>  
  <https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="security-backup-and-monitoring-services"></a><span data-ttu-id="fca1a-130">安全性、 備份及監視服務</span><span class="sxs-lookup"><span data-stu-id="fca1a-130">Security, backup, and monitoring services</span></span>

<span data-ttu-id="fca1a-131">有許多支援例行工作，有許多您必須處理以確保您的應用程式和基礎結構來支援商務需求的最上層的波陷條件的詳細資料，而且這種情況就會變成更複雜的微服務領域中，而您需要想辦法當您需要採取動作時，有高階和詳細檢視。</span><span class="sxs-lookup"><span data-stu-id="fca1a-131">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="fca1a-132">Azure 有工具來管理，並提供四個重要層面雲端和內部部署資源的統一的檢視：</span><span class="sxs-lookup"><span data-stu-id="fca1a-132">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="fca1a-133">**安全性**。</span><span class="sxs-lookup"><span data-stu-id="fca1a-133">**Security**.</span></span> <span data-ttu-id="fca1a-134">具有[Azure 資訊安全中心](https://azure.microsoft.com/services/security-center/)。</span><span class="sxs-lookup"><span data-stu-id="fca1a-134">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="fca1a-135">取得完整的可見度及控制您的虛擬機器、 應用程式和工作負載的安全性。</span><span class="sxs-lookup"><span data-stu-id="fca1a-135">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="fca1a-136">集中管理您的安全性原則，並整合現有的程序和工具。</span><span class="sxs-lookup"><span data-stu-id="fca1a-136">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="fca1a-137">偵測真正的威脅，使用進階分析。</span><span class="sxs-lookup"><span data-stu-id="fca1a-137">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="fca1a-138">**備份**。</span><span class="sxs-lookup"><span data-stu-id="fca1a-138">**Backup**.</span></span> <span data-ttu-id="fca1a-139">具有[Azure 備份](https://azure.microsoft.com/services/backup/)。</span><span class="sxs-lookup"><span data-stu-id="fca1a-139">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="fca1a-140">避免耗費資源的業務中斷情況、 符合合規性目標和保護資料不受勒索軟體和人為錯誤。</span><span class="sxs-lookup"><span data-stu-id="fca1a-140">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="fca1a-141">保留備份資料傳輸中和待用加密。</span><span class="sxs-lookup"><span data-stu-id="fca1a-141">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="fca1a-142">請確定以防止未經授權的使用多重要素驗證為基礎的存取。</span><span class="sxs-lookup"><span data-stu-id="fca1a-142">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="fca1a-143">**監視**。</span><span class="sxs-lookup"><span data-stu-id="fca1a-143">**Monitoring**.</span></span> <span data-ttu-id="fca1a-144">具有[Azure 監視](https://azure.microsoft.com/solutions/monitoring/)， [Log Analytics](https://azure.microsoft.com/services/log-analytics/)，並[Application Insights](https://azure.microsoft.com/services/application-insights/)。</span><span class="sxs-lookup"><span data-stu-id="fca1a-144">With [Azure monitoring](https://azure.microsoft.com/solutions/monitoring/), [Log Analytics](https://azure.microsoft.com/services/log-analytics/), and [Application Insights](https://azure.microsoft.com/services/application-insights/).</span></span>
  - <span data-ttu-id="fca1a-145">取得完整的可見性的健全狀況和效能，您的 Azure 工作負載、 應用程式和基礎結構。</span><span class="sxs-lookup"><span data-stu-id="fca1a-145">Get full visibility into the health and performance of your Azure workloads, apps, and infrastructure.</span></span>
  - <span data-ttu-id="fca1a-146">從任何來源收集資料，並取得豐富的深入了解您的虛擬機器、 容器和應用程式。</span><span class="sxs-lookup"><span data-stu-id="fca1a-146">Collect data from any source and get rich insights into your virtual machines, containers, and applications.</span></span>
  - <span data-ttu-id="fca1a-147">尋找您需要使用互動式查詢和全文檢索搜尋的資訊。</span><span class="sxs-lookup"><span data-stu-id="fca1a-147">Find the information you need using interactive queries and full-text search.</span></span> 
  - <span data-ttu-id="fca1a-148">執行根本原因分析使用進階分析，包括機器學習服務演算法。</span><span class="sxs-lookup"><span data-stu-id="fca1a-148">Perform root-cause analysis with advanced analytics, including machine learning algorithms.</span></span>

- <span data-ttu-id="fca1a-149">**在內部部署資源**。</span><span class="sxs-lookup"><span data-stu-id="fca1a-149">**On-premises resources**.</span></span> <span data-ttu-id="fca1a-150">具有[真正的一致性混合式雲端](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/)。</span><span class="sxs-lookup"><span data-stu-id="fca1a-150">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fca1a-151">[上一頁](manage-production-docker-environments.md)
>[下一頁](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="fca1a-151">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
