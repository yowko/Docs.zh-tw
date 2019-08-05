---
title: 監視容器化應用程式服務
description: 了解監視容器架構的一些重要層面
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673455"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="ec0b0-103">監視容器化應用程式服務</span><span class="sxs-lookup"><span data-stu-id="ec0b0-103">Monitor containerized application services</span></span>

<span data-ttu-id="ec0b0-104">對於分割成多個容器和微服務的應用程式來說，最重要的是要有一種方法來監視及分析整個應用程式行為。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="ec0b0-105">Azure 監視器</span><span class="sxs-lookup"><span data-stu-id="ec0b0-105">Azure Monitor</span></span>

<span data-ttu-id="ec0b0-106">[Azure 監視器](https://azure.microsoft.com/services/monitor/)是一項可延伸的分析服務，用來監視您的即時應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="ec0b0-107">它可協助您偵測並診斷效能問題，以及了解實際上使用者如何運用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="ec0b0-108">它專為開發人員而設計，目的是協助您持續改善服務或應用程式的效能與可用性。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="ec0b0-109">Azure 監視器可與內部部署或雲端中所裝載之各種不同平台 (例如 .NET、Java、Node.js 及許多其他平台) 的 Web/服務和獨立應用程式搭配運作。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ec0b0-110">其他資源</span><span class="sxs-lookup"><span data-stu-id="ec0b0-110">Additional resources</span></span>

- <span data-ttu-id="ec0b0-111">**Azure 監視器的概觀** </span><span class="sxs-lookup"><span data-stu-id="ec0b0-111">**Overview of Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="ec0b0-112">**什麼是 Application Insights？**</span><span class="sxs-lookup"><span data-stu-id="ec0b0-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="ec0b0-113">**Azure 監視器計量是什麼？**</span><span class="sxs-lookup"><span data-stu-id="ec0b0-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="ec0b0-114">**Azure 監視器中的容器監視解決方案** </span><span class="sxs-lookup"><span data-stu-id="ec0b0-114">**Container Monitoring solution in Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="ec0b0-115">安全性與備份服務</span><span class="sxs-lookup"><span data-stu-id="ec0b0-115">Security and backup services</span></span>

<span data-ttu-id="ec0b0-116">您必須處理許多內含大量詳細資料的支援例行工作，以確保您的應用程式和基礎結構處於最佳狀態來支援商務需求，且這種情況在微服務領域中變得更加複雜，因此當您需要採取動作時，您需要想辦法同時擁有高階和詳細檢視。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="ec0b0-117">Azure 具有工具可用來管理雲端和內部部署資源的四個重要層面，並提供其統一檢視：</span><span class="sxs-lookup"><span data-stu-id="ec0b0-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="ec0b0-118">**安全性**。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-118">**Security**.</span></span> <span data-ttu-id="ec0b0-119">使用 [Azure 資訊安全中心](https://azure.microsoft.com/services/security-center/)。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="ec0b0-120">完整檢視及控制虛擬機器、應用程式和工作負載的安全性。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="ec0b0-121">集中管理您的安全性原則，並整合現有的處理序和工具。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="ec0b0-122">使用進階分析偵測真正的威脅。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="ec0b0-123">**備份**。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-123">**Backup**.</span></span> <span data-ttu-id="ec0b0-124">使用 [Azure 備份](https://azure.microsoft.com/services/backup/)。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="ec0b0-125">避免耗費資源的業務中斷情況、符合相容性目標，以及保護資料不受勒索軟體和人為錯誤影響。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="ec0b0-126">使資料在傳送過程及待用期間保持加密。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="ec0b0-127">確保根據多重要素驗證進行存取，以防止未經授權的使用。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="ec0b0-128">**內部部署資源**。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-128">**On-premises resources**.</span></span> <span data-ttu-id="ec0b0-129">使用[真正一致的混合式雲端](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/)。</span><span class="sxs-lookup"><span data-stu-id="ec0b0-129">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ec0b0-130">[上一頁](manage-production-docker-environments.md)
>[下一頁](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="ec0b0-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
