---
title: 監視容器化應用程式服務
description: 了解一些重要的層面的監視容器架構
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641203"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="d31db-103">監視容器化應用程式服務</span><span class="sxs-lookup"><span data-stu-id="d31db-103">Monitor containerized application services</span></span>

<span data-ttu-id="d31db-104">最重要的是應用程式分割成多個容器和微服務的方式，來監視及分析整個應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="d31db-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="d31db-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="d31db-105">Azure Monitor</span></span>

<span data-ttu-id="d31db-106">[Azure 監視器](https://azure.microsoft.com/services/monitor/)是可延伸分析服務，可監視您即時應用程式。</span><span class="sxs-lookup"><span data-stu-id="d31db-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="d31db-107">它可協助您偵測並診斷效能問題，並了解使用者實際如何運用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d31db-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="d31db-108">它被專為開發人員，協助您持續改善效能的目的與您的服務或應用程式的可用性。</span><span class="sxs-lookup"><span data-stu-id="d31db-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="d31db-109">Azure 監視器可搭配 web/服務和獨立上各種不同的平台，例如.NET、 Java、 Node.js 和許多其他平台，裝載於內部部署或雲端中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d31db-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d31db-110">其他資源</span><span class="sxs-lookup"><span data-stu-id="d31db-110">Additional resources</span></span>

- <span data-ttu-id="d31db-111">**Azure 監視器概觀** \\</span><span class="sxs-lookup"><span data-stu-id="d31db-111">**Overview of Azure Monitor** \\</span></span>
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="d31db-112">**什麼是 Application Insights？**</span><span class="sxs-lookup"><span data-stu-id="d31db-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="d31db-113">**什麼是 Azure 監視器計量？**</span><span class="sxs-lookup"><span data-stu-id="d31db-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="d31db-114">**Azure 監視器中的容器監視解決方案** \\</span><span class="sxs-lookup"><span data-stu-id="d31db-114">**Container Monitoring solution in Azure Monitor** \\</span></span>
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="d31db-115">安全性與備份服務</span><span class="sxs-lookup"><span data-stu-id="d31db-115">Security and backup services</span></span>

<span data-ttu-id="d31db-116">有許多支援例行工作，有許多您必須處理以確保您的應用程式和基礎結構來支援商務需求的最上層的波陷條件的詳細資料，而且這種情況就會變成更複雜的微服務領域中，而您需要想辦法當您需要採取動作時，有高階和詳細檢視。</span><span class="sxs-lookup"><span data-stu-id="d31db-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="d31db-117">Azure 有工具來管理，並提供四個重要層面雲端和內部部署資源的統一的檢視：</span><span class="sxs-lookup"><span data-stu-id="d31db-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="d31db-118">**安全性**。</span><span class="sxs-lookup"><span data-stu-id="d31db-118">**Security**.</span></span> <span data-ttu-id="d31db-119">具有[Azure 資訊安全中心](https://azure.microsoft.com/services/security-center/)。</span><span class="sxs-lookup"><span data-stu-id="d31db-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="d31db-120">取得完整的可見度及控制您的虛擬機器、 應用程式和工作負載的安全性。</span><span class="sxs-lookup"><span data-stu-id="d31db-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="d31db-121">集中管理您的安全性原則，並整合現有的程序和工具。</span><span class="sxs-lookup"><span data-stu-id="d31db-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="d31db-122">偵測真正的威脅，使用進階分析。</span><span class="sxs-lookup"><span data-stu-id="d31db-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="d31db-123">**備份**。</span><span class="sxs-lookup"><span data-stu-id="d31db-123">**Backup**.</span></span> <span data-ttu-id="d31db-124">具有[Azure 備份](https://azure.microsoft.com/services/backup/)。</span><span class="sxs-lookup"><span data-stu-id="d31db-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="d31db-125">避免耗費資源的業務中斷情況、 符合合規性目標和保護資料不受勒索軟體和人為錯誤。</span><span class="sxs-lookup"><span data-stu-id="d31db-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="d31db-126">保留備份資料傳輸中和待用加密。</span><span class="sxs-lookup"><span data-stu-id="d31db-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="d31db-127">請確定以防止未經授權的使用多重要素驗證為基礎的存取。</span><span class="sxs-lookup"><span data-stu-id="d31db-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="d31db-128">**在內部部署資源**。</span><span class="sxs-lookup"><span data-stu-id="d31db-128">**On-premises resources**.</span></span> <span data-ttu-id="d31db-129">具有[真正的一致性混合式雲端](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/)。</span><span class="sxs-lookup"><span data-stu-id="d31db-129">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d31db-130">[上一頁](manage-production-docker-environments.md)
>[下一頁](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="d31db-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
