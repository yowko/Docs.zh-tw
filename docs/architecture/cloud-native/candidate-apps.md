---
title: 雲本機的候選應用
description: 瞭解哪些類型的應用程式受益於雲原生方法
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 8e58f5bd3aa0a4503ea73ab454e42e863eb0bb5d
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805621"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="f5852-103">雲本機的候選應用</span><span class="sxs-lookup"><span data-stu-id="f5852-103">Candidate apps for cloud native</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="f5852-104">查看產品群組中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5852-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="f5852-105">其中有多少人有資格獲得雲原生架構?</span><span class="sxs-lookup"><span data-stu-id="f5852-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="f5852-106">全部？</span><span class="sxs-lookup"><span data-stu-id="f5852-106">All of them?</span></span> <span data-ttu-id="f5852-107">也許有些?</span><span class="sxs-lookup"><span data-stu-id="f5852-107">Perhaps some?</span></span>

<span data-ttu-id="f5852-108">應用成本/收益分析,大多數人很可能不支援雲原生所需的高昂價格標籤。</span><span class="sxs-lookup"><span data-stu-id="f5852-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="f5852-109">雲原生成本將遠遠超過應用程式的業務價值。</span><span class="sxs-lookup"><span data-stu-id="f5852-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="f5852-110">哪種應用程式可能是雲本機的候選類型?</span><span class="sxs-lookup"><span data-stu-id="f5852-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="f5852-111">需要不斷發展業務能力/功能的大型戰略企業系統</span><span class="sxs-lookup"><span data-stu-id="f5852-111">A large, strategic enterprise system that needs to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="f5852-112">需要高釋放速度的應用程式 - 高度置信度</span><span class="sxs-lookup"><span data-stu-id="f5852-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="f5852-113">具有單一功能且無需完全重新部署整個系統*即可發布的系統*</span><span class="sxs-lookup"><span data-stu-id="f5852-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="f5852-114">由具有不同技術堆疊專業知識的團隊開發的應用程式</span><span class="sxs-lookup"><span data-stu-id="f5852-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="f5852-115">具有必須獨立擴充的元件的應用程式</span><span class="sxs-lookup"><span data-stu-id="f5852-115">An application with components that must scale independently</span></span>

<span data-ttu-id="f5852-116">然後是遺留系統。</span><span class="sxs-lookup"><span data-stu-id="f5852-116">Then there are legacy systems.</span></span> <span data-ttu-id="f5852-117">雖然我們都希望構建新的應用程式,但我們通常負責實現對業務至關重要的遺留工作負載的現代化。</span><span class="sxs-lookup"><span data-stu-id="f5852-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="f5852-118">隨著時間的推移,舊應用程式可以分解為微服務,容器化,並最終"重新平臺"到雲本機體系結構。</span><span class="sxs-lookup"><span data-stu-id="f5852-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="f5852-119">現代化傳統應用</span><span class="sxs-lookup"><span data-stu-id="f5852-119">Modernizing legacy apps</span></span>

<span data-ttu-id="f5852-120">免費的 Microsoft 電子書[使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化改造](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook),為將本地工作負載遷移到雲提供了指南。</span><span class="sxs-lookup"><span data-stu-id="f5852-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="f5852-121">圖 1-10 顯示了沒有一種單一、一刀切的策略來實現舊應用程式的現代化。</span><span class="sxs-lookup"><span data-stu-id="f5852-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![遷移舊工作負載的策略](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="f5852-123">**圖 1-10**.</span><span class="sxs-lookup"><span data-stu-id="f5852-123">**Figure 1-10**.</span></span> <span data-ttu-id="f5852-124">遷移舊工作負載的策略</span><span class="sxs-lookup"><span data-stu-id="f5852-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="f5852-125">非關鍵應用主要受益於快速提升和移動 ([雲端基礎架構就緒](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) 遷移。</span><span class="sxs-lookup"><span data-stu-id="f5852-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) migration.</span></span> <span data-ttu-id="f5852-126">在這裡,本地工作負載將重新託管到基於雲的 VM,無需更改。</span><span class="sxs-lookup"><span data-stu-id="f5852-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="f5852-127">此方法使用[IaaS(基礎設施即服務)模型](https://azure.microsoft.com/overview/what-is-iaas/)。</span><span class="sxs-lookup"><span data-stu-id="f5852-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="f5852-128">Azure 包括多個工具,如[Azure 遷移](https://azure.microsoft.com/services/azure-migrate/)[、Azure 網站恢復](https://azure.microsoft.com/services/site-recovery/)和[Azure 資料庫遷移服務](https://azure.microsoft.com/campaigns/database-migration/),以便更輕鬆地移動。</span><span class="sxs-lookup"><span data-stu-id="f5852-128">Azure includes several tools such as [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) to make such a move easier.</span></span> <span data-ttu-id="f5852-129">雖然這種策略可以節省一些成本,但此類應用程式通常不是為解鎖和利用雲端運算的優勢而構建的。</span><span class="sxs-lookup"><span data-stu-id="f5852-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="f5852-130">對業務至關重要的單一應用通常受益於增強的提升和移位(*雲優化*) 遷移。</span><span class="sxs-lookup"><span data-stu-id="f5852-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="f5852-131">此方法包括啟用關鍵雲服務的部署優化, 而無需更改應用程式的核心體系結構。</span><span class="sxs-lookup"><span data-stu-id="f5852-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="f5852-132">例如,您可以將應用程式[容器化](https://docs.microsoft.com/virtualization/windowscontainers/about/),並將其部署到容器協調器,如本書後面討論的[Azure Kubernetes 服務](https://azure.microsoft.com/services/kubernetes-service/)。</span><span class="sxs-lookup"><span data-stu-id="f5852-132">For example, you might [containerize](https://docs.microsoft.com/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="f5852-133">進入雲后,應用程式可能會使用其他雲服務,如資料庫、消息佇列、監視和分散式緩存。</span><span class="sxs-lookup"><span data-stu-id="f5852-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="f5852-134">最後,執行戰略企業功能的單一應用可能最好受益於*雲原生*方法,這是本書的主題。</span><span class="sxs-lookup"><span data-stu-id="f5852-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="f5852-135">此方法提供敏捷性和速度。</span><span class="sxs-lookup"><span data-stu-id="f5852-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="f5852-136">但是,它的代價是重新平臺、重新構建和重寫代碼。</span><span class="sxs-lookup"><span data-stu-id="f5852-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="f5852-137">如果您和您的團隊認為雲原生方法是適當的,則您應該與組織一起使決策合理化。</span><span class="sxs-lookup"><span data-stu-id="f5852-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="f5852-138">雲原生方法將解決的業務問題究竟是什麼?</span><span class="sxs-lookup"><span data-stu-id="f5852-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="f5852-139">它如何與業務需求保持一致?</span><span class="sxs-lookup"><span data-stu-id="f5852-139">How would it align with business needs?</span></span>

- <span data-ttu-id="f5852-140">快速發佈功能,增強信心?</span><span class="sxs-lookup"><span data-stu-id="f5852-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="f5852-141">細粒度可擴充性 - 更有效地使用資源?</span><span class="sxs-lookup"><span data-stu-id="f5852-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="f5852-142">提高系統彈性?</span><span class="sxs-lookup"><span data-stu-id="f5852-142">Improved system resiliency?</span></span>

- <span data-ttu-id="f5852-143">提高系統性能?</span><span class="sxs-lookup"><span data-stu-id="f5852-143">Improved system performance?</span></span>

- <span data-ttu-id="f5852-144">對操作的更多可見性?</span><span class="sxs-lookup"><span data-stu-id="f5852-144">More visibility into operations?</span></span>

- <span data-ttu-id="f5852-145">混合開發平臺和數據存儲,以找到最適合作業的工具?</span><span class="sxs-lookup"><span data-stu-id="f5852-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="f5852-146">面向未來的應用投資?</span><span class="sxs-lookup"><span data-stu-id="f5852-146">Future-proof application investment?</span></span>

<span data-ttu-id="f5852-147">正確的遷移策略取決於組織優先順序和您所針對的系統。</span><span class="sxs-lookup"><span data-stu-id="f5852-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="f5852-148">對許多人來說,雲優化單片應用程式或向 N-Tier 應用添加粗粒度服務可能更具成本效益。</span><span class="sxs-lookup"><span data-stu-id="f5852-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="f5852-149">在這些情況下,您仍然可以充分利用雲 PaaS 功能,如 Azure 應用服務提供的功能。</span><span class="sxs-lookup"><span data-stu-id="f5852-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="f5852-150">摘要</span><span class="sxs-lookup"><span data-stu-id="f5852-150">Summary</span></span>

<span data-ttu-id="f5852-151">在本章中,我們介紹了雲原生計算。</span><span class="sxs-lookup"><span data-stu-id="f5852-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="f5852-152">我們提供了一個定義以及驅動雲本機應用程式的關鍵功能。</span><span class="sxs-lookup"><span data-stu-id="f5852-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="f5852-153">我們研究了可能證明這種投資和努力合理的應用程序類型。</span><span class="sxs-lookup"><span data-stu-id="f5852-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="f5852-154">在介紹之後,我們現在將深入探討雲原生。</span><span class="sxs-lookup"><span data-stu-id="f5852-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="f5852-155">參考</span><span class="sxs-lookup"><span data-stu-id="f5852-155">References</span></span>

- [<span data-ttu-id="f5852-156">雲原生計算基金會</span><span class="sxs-lookup"><span data-stu-id="f5852-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="f5852-157">.NET 微服務:容器化 .NET 應用程式的體系結構</span><span class="sxs-lookup"><span data-stu-id="f5852-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="f5852-158">使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化</span><span class="sxs-lookup"><span data-stu-id="f5852-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="f5852-159">科妮莉亞·大衛斯的雲原生模式</span><span class="sxs-lookup"><span data-stu-id="f5852-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="f5852-160">超越十二因素應用</span><span class="sxs-lookup"><span data-stu-id="f5852-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="f5852-161">什麼是基礎架構作為代碼</span><span class="sxs-lookup"><span data-stu-id="f5852-161">What is Infrastructure as Code</span></span>](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="f5852-162">優步工程的微觀部署:自信地每天部署</span><span class="sxs-lookup"><span data-stu-id="f5852-162">Uber Engineering's Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="f5852-163">Netflix 如何部署程式碼</span><span class="sxs-lookup"><span data-stu-id="f5852-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="f5852-164">用於擴展微信微服務的過載控制</span><span class="sxs-lookup"><span data-stu-id="f5852-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
><span data-ttu-id="f5852-165">[前一個](definition.md)
>[下一個](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="f5852-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>
