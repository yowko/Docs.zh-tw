---
title: 撤銷並轉移現有的.NET 應用程式至 Azure IaaS （雲端基礎結構就緒）
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 2b987d43f476f261bfdbd1b2af6ca7f792178cf8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266620"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a><span data-ttu-id="8afa6-103">撤銷並轉移現有的.NET 應用程式至 Azure IaaS （雲端基礎結構就緒）</span><span class="sxs-lookup"><span data-stu-id="8afa6-103">Lift and shift existing .NET apps to Azure IaaS (Cloud Infrastructure-Ready)</span></span>

> <span data-ttu-id="8afa6-104">願景：第一個步驟中，若要減少您的內部部署投資與硬體和網路維護的整體成本，只要重新裝載在雲端中現有的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8afa6-104">Vision: As a first step, to reduce your on-premises investment and total cost of hardware and networking maintenance, simply rehost your existing applications in the cloud.</span></span>

<span data-ttu-id="8afa6-105">進入*如何*若要移轉現有的應用程式至 Azure 的基礎結構即服務 (IaaS) 平台，務必要分析的原因*為什麼*您會想要直接到 IaaS 移轉在 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="8afa6-105">Before getting into *how* to migrate your existing applications to the Azure infrastructure as a service (IaaS) platform, it's important to analyze the reasons *why* you'd want to migrate directly to IaaS in Azure.</span></span> <span data-ttu-id="8afa6-106">若要開始使用 Vm 在雲端中，而不會繼續使用目前的內部部署基礎結構基本上是這個現代化成熟度等級的案例。</span><span class="sxs-lookup"><span data-stu-id="8afa6-106">The scenario at this modernization maturity level essentially is to start using VMs in the cloud, instead of continuing to use your current, on-premises infrastructure.</span></span>

<span data-ttu-id="8afa6-107">若要分析的另一個點是*為什麼*您可能想要移轉至純 IaaS 雲端，而非只新增更進階的受管理的服務，在 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="8afa6-107">Another point to analyze is *why* you might want to migrate to pure IaaS cloud instead of just adding more advanced managed services in Azure.</span></span> <span data-ttu-id="8afa6-108">判斷的情況下可能會在一開始需要 IaaS。</span><span class="sxs-lookup"><span data-stu-id="8afa6-108">Determine what cases might require IaaS in the first place.</span></span>

<span data-ttu-id="8afa6-109">圖 2-1 放置現代化成熟度等級的雲端基礎結構就緒應用程式：</span><span class="sxs-lookup"><span data-stu-id="8afa6-109">Figure 2-1 positions Cloud Infrastructure-Ready applications in the modernization maturity levels:</span></span>

![定位的雲端基礎結構就緒應用程式](./media/image2-1.png)

> <span data-ttu-id="8afa6-111">**圖 2-1。**</span><span class="sxs-lookup"><span data-stu-id="8afa6-111">**Figure 2-1.**</span></span> <span data-ttu-id="8afa6-112">定位的雲端基礎結構就緒應用程式</span><span class="sxs-lookup"><span data-stu-id="8afa6-112">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a><span data-ttu-id="8afa6-113">為什麼要移轉至 Azure IaaS 的現有.NET web 應用程式</span><span class="sxs-lookup"><span data-stu-id="8afa6-113">Why migrate existing .NET web applications to Azure IaaS</span></span>

<span data-ttu-id="8afa6-114">若要移轉至雲端，即使在初始的 IaaS 層級，主要原因是為了達成降低成本。</span><span class="sxs-lookup"><span data-stu-id="8afa6-114">The main reason to migrate to the cloud, even at an initial IaaS level, is to achieve cost reductions.</span></span> <span data-ttu-id="8afa6-115">藉由使用更多的受管理的基礎結構服務，您的組織可以降低其硬體維護、 伺服器或 VM 佈建和部署和管理基礎結構的投資。</span><span class="sxs-lookup"><span data-stu-id="8afa6-115">By using more managed infrastructure services, your organization can lower its investment in hardware maintenance, server or VM provisioning and deployment, and infrastructure management.</span></span>

<span data-ttu-id="8afa6-116">決定您的應用程式移至雲端之後，為什麼您可能會選擇 IaaS 而不是更進階的選項，例如 PaaS 只是，IaaS 環境的主要原因將會更熟悉。</span><span class="sxs-lookup"><span data-stu-id="8afa6-116">After you make the decision to move your apps to the cloud, the main reason why you might choose IaaS instead of more advanced options like PaaS is simply that the IaaS environment will be more familiar.</span></span> <span data-ttu-id="8afa6-117">在內部部署環境移至類似於您目前的環境，提供較低的學習曲線，讓它的最快路徑至雲端。</span><span class="sxs-lookup"><span data-stu-id="8afa6-117">Moving to an environment that's similar to your current, on-premises environment offers a lower learning curve, which makes it the quickest path to the cloud.</span></span>

<span data-ttu-id="8afa6-118">不過，採用最快路徑到雲端並不表示您會獲得最大效益，不需要在雲端中執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8afa6-118">However, taking the quickest path to the cloud doesn't mean that you will gain the most benefit from having your applications running in the cloud.</span></span> <span data-ttu-id="8afa6-119">任何組織會獲得最大的好處，從已導入的雲端最佳化和雲端原生成熟度等級的雲端移轉。</span><span class="sxs-lookup"><span data-stu-id="8afa6-119">Any organization will gain the most significant benefits from a cloud migration at the already introduced Cloud-Optimized and Cloud-Native maturity levels.</span></span>

<span data-ttu-id="8afa6-120">也變得更明顯，應用程式是您更輕鬆地現代化，並在雲端中，即使在 IaaS 上執行時在未來重新架構。</span><span class="sxs-lookup"><span data-stu-id="8afa6-120">It also has become evident that applications are easier to modernize and rearchitect in the future when they are already running in the cloud, even on IaaS.</span></span> <span data-ttu-id="8afa6-121">應用程式資料移轉已完成。</span><span class="sxs-lookup"><span data-stu-id="8afa6-121">Application data migration has already been achieved.</span></span> <span data-ttu-id="8afa6-122">此外，您的組織會有獲得在雲端中工作所需的技能和對排班作業系統中 「 雲端文化特性 」。</span><span class="sxs-lookup"><span data-stu-id="8afa6-122">Also, your organization will have gained skills required for working in the cloud and made the shift to operating in a "cloud culture."</span></span>

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a><span data-ttu-id="8afa6-123">移轉至 IaaS 而不是，PaaS</span><span class="sxs-lookup"><span data-stu-id="8afa6-123">When to migrate to IaaS instead of to PaaS</span></span>

<span data-ttu-id="8afa6-124">下一節中討論大部分基礎 PaaS 平台和服務的雲端最佳化應用程式。</span><span class="sxs-lookup"><span data-stu-id="8afa6-124">The next sections discuss Cloud-Optimized applications that are mostly based on PaaS platforms and services.</span></span> <span data-ttu-id="8afa6-125">這些應用程式可讓您的大部分優點從移轉至雲端。</span><span class="sxs-lookup"><span data-stu-id="8afa6-125">These apps give you the most benefits from migrating to the cloud.</span></span> 

<span data-ttu-id="8afa6-126">如果您的目標是單純將現有的應用程式到雲端，首先，識別現有的應用程式不需要在 Azure App Service 中執行的大幅修改。</span><span class="sxs-lookup"><span data-stu-id="8afa6-126">If your goal is simply to move existing applications to the cloud, first, identify existing applications that would not require substantial modification to run in Azure App Service.</span></span> <span data-ttu-id="8afa6-127">這些應用程式應該是第一個適合雲端最佳化。</span><span class="sxs-lookup"><span data-stu-id="8afa6-127">These apps should be the first candidates for Cloud-Optimized.</span></span> 

<span data-ttu-id="8afa6-128">然後，應用程式，仍無法將移至 Windows 容器和 PaaS 例如 App Service 或 Azure Service Fabric 等協調器移轉到簡單純文字的 Vm (IaaS)。</span><span class="sxs-lookup"><span data-stu-id="8afa6-128">Then, for the apps that still cannot move to Windows Containers and PaaS such as App Service or orchestrators like Azure Service Fabric, migrate those to simple plain VMs (IaaS).</span></span> 

<span data-ttu-id="8afa6-129">但請記住，正確地設定、 保護和維護 Vm 需要更多的時間和相較於在 Azure 中使用 PaaS 服務的 IT 專業知識。</span><span class="sxs-lookup"><span data-stu-id="8afa6-129">But, keep in mind that correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to using PaaS services in Azure.</span></span> <span data-ttu-id="8afa6-130">如果您考慮 Azure 虛擬機器，請確定，您需要考慮修補、 更新和管理 VM 環境所需的持續性維護工作。</span><span class="sxs-lookup"><span data-stu-id="8afa6-130">If you are considering Azure Virtual Machines, make sure that you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="8afa6-131">Azure 虛擬機器是 IaaS。</span><span class="sxs-lookup"><span data-stu-id="8afa6-131">Azure Virtual Machines is IaaS.</span></span>

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a><span data-ttu-id="8afa6-132">使用 Azure Migrate 分析並移轉您現有的應用程式至 Azure</span><span class="sxs-lookup"><span data-stu-id="8afa6-132">Use Azure Migrate to analyze and migrate your existing applications to Azure</span></span>

<span data-ttu-id="8afa6-133">移轉至雲端，不一定要很困難。</span><span class="sxs-lookup"><span data-stu-id="8afa6-133">Migrating to the cloud doesn't have to be difficult.</span></span> <span data-ttu-id="8afa6-134">不過，許多組織必須努力開始建置，以取得深入了解環境中，應用程式、 工作負載和資料之間的緊密相互依存性。</span><span class="sxs-lookup"><span data-stu-id="8afa6-134">But many organizations struggle to get started - to get deep visibility into the environment and the tight interdependencies between applications, workloads, and data.</span></span> <span data-ttu-id="8afa6-135">能見度，它可能難以規劃路徑轉接。</span><span class="sxs-lookup"><span data-stu-id="8afa6-135">Without that visibility, it can be difficult to plan the path forward.</span></span> <span data-ttu-id="8afa6-136">沒有上要成功移轉的必要條件的詳細資訊，您不能有對話在組織內。</span><span class="sxs-lookup"><span data-stu-id="8afa6-136">Without detailed information on what's required for a successful migration, you can't have the right conversations within your organization.</span></span> <span data-ttu-id="8afa6-137">您不知道夠清楚的潛在成本效益，或是否可以只和轉移工作負載，或需要大幅修改一下，才能成功移轉。</span><span class="sxs-lookup"><span data-stu-id="8afa6-137">You don't know enough about the potential cost benefits, or whether workloads could just lift-and-shift or would require significant rework to migrate successfully.</span></span> <span data-ttu-id="8afa6-138">難怪，許多組織不太願意。</span><span class="sxs-lookup"><span data-stu-id="8afa6-138">No wonder many organizations hesitate.</span></span>

<span data-ttu-id="8afa6-139">[Azure Migrate](https://aka.ms/azuremigrate)是新的服務可提供指引、 深入解析，以及可協助您移轉至 Azure 所需的機制。</span><span class="sxs-lookup"><span data-stu-id="8afa6-139">[Azure Migrate](https://aka.ms/azuremigrate) is a new service that provides the guidance, insights, and mechanisms needed to assist you in migrating to Azure.</span></span> <span data-ttu-id="8afa6-140">Azure Migrate 提供：</span><span class="sxs-lookup"><span data-stu-id="8afa6-140">Azure Migrate provides:</span></span>

- <span data-ttu-id="8afa6-141">探索及評定內部部署虛擬機器</span><span class="sxs-lookup"><span data-stu-id="8afa6-141">Discovery and assessment for on-premises virtual machines</span></span>

- <span data-ttu-id="8afa6-142">值得高度信賴的多層式應用程式的探索內建的相依性對應</span><span class="sxs-lookup"><span data-stu-id="8afa6-142">Inbuilt dependency mapping for high-confidence discovery of multi-tier applications</span></span>

- <span data-ttu-id="8afa6-143">智慧型的正確調整大小，以 Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="8afa6-143">Intelligent right sizing to Azure virtual machines</span></span>

- <span data-ttu-id="8afa6-144">相容性報告，修復的潛在問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="8afa6-144">Compatibility reporting with guidelines for remediating potential issues</span></span>

- <span data-ttu-id="8afa6-145">資料庫探索和移轉的 Azure 資料庫管理服務整合</span><span class="sxs-lookup"><span data-stu-id="8afa6-145">Integration with Azure Database Management Service for database discovery and migration</span></span>

<span data-ttu-id="8afa6-146">Azure Migrate 提供信心，您的工作負載可以移轉與業務的影響降到最低，並如預期般在 Azure 中執行。</span><span class="sxs-lookup"><span data-stu-id="8afa6-146">Azure Migrate gives you confidence that your workloads can migrate with minimal impact to the business and run as expected in Azure.</span></span> <span data-ttu-id="8afa6-147">使用適當的工具和指引，就能夠同時以確保效能的重要投資報酬率上限，並符合可靠性需求。</span><span class="sxs-lookup"><span data-stu-id="8afa6-147">With the right tools and guidance, you can achieve maximum return on investment while assuring that critical performance and reliability needs are met.</span></span>

<span data-ttu-id="8afa6-148">圖 2-2 會顯示 Azure Migrate 所執行的所有伺服器和應用程式連接的內建的相依性對應。</span><span class="sxs-lookup"><span data-stu-id="8afa6-148">Figure 2-2 shows you the built-in dependency mapping for all server and application connections performed by Azure Migrate.</span></span>

![定位的雲端基礎結構就緒應用程式](./media/image2-2.png)

> <span data-ttu-id="8afa6-150">**圖 2-2。**</span><span class="sxs-lookup"><span data-stu-id="8afa6-150">**Figure 2-2.**</span></span> <span data-ttu-id="8afa6-151">定位的雲端基礎結構就緒應用程式</span><span class="sxs-lookup"><span data-stu-id="8afa6-151">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a><span data-ttu-id="8afa6-152">使用 Azure Site Recovery 將您現有的 Vm 移轉至 Azure Vm</span><span class="sxs-lookup"><span data-stu-id="8afa6-152">Use Azure Site Recovery to migrate your existing VMs to Azure VMs</span></span>

<span data-ttu-id="8afa6-153">做為端對端的一部分[Azure Migrate](https://aka.ms/azuremigrate)， [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)是一種工具，可用來輕鬆地將您的 web 應用程式移轉到 Azure 中 Vm。</span><span class="sxs-lookup"><span data-stu-id="8afa6-153">As part of the end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) is a tool that you can use to easily migrate your web apps to VMs in Azure.</span></span> <span data-ttu-id="8afa6-154">您可以使用 Site Recovery，將內部部署 Vm 和實體伺服器複寫至 Azure，或將它們複寫至次要內部部署位置。</span><span class="sxs-lookup"><span data-stu-id="8afa6-154">You can use Site Recovery to replicate on-premises VMs and physical servers to Azure, or to replicate them to a secondary on-premises location.</span></span> <span data-ttu-id="8afa6-155">您甚至可以複寫在支援的 Azure VM，在內部部署執行的工作負載*HYPER-V* VM 上*VMware* VM，或在 Windows 或 Linux 實體伺服器上。</span><span class="sxs-lookup"><span data-stu-id="8afa6-155">You can even replicate a workload that's running on a supported Azure VM, on an on-premises *Hyper-V* VM, on a *VMware* VM, or on a Windows or Linux physical server.</span></span> <span data-ttu-id="8afa6-156">複寫至 Azure 可排除維護次要資料中心的複雜度與成本。</span><span class="sxs-lookup"><span data-stu-id="8afa6-156">Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.</span></span>

<span data-ttu-id="8afa6-157">Site Recovery 也會針對混合式環境的部分在內部部署和部分在 Azure。</span><span class="sxs-lookup"><span data-stu-id="8afa6-157">Site Recovery is also made specifically for hybrid environments that are partly on-premises and partly on Azure.</span></span> <span data-ttu-id="8afa6-158">Site Recovery 可協助確保業務持續性讓您在 Vm 執行的應用程式和內部部署可用的實體伺服器如果站台無法運作。</span><span class="sxs-lookup"><span data-stu-id="8afa6-158">Site Recovery helps ensure business continuity by keeping your apps that are running on VMs and on-premises physical servers available if a site goes down.</span></span> <span data-ttu-id="8afa6-159">它會複寫，讓它們仍可在次要位置如果主要站台無法使用，在 Vm 和實體伺服器執行的工作負載。</span><span class="sxs-lookup"><span data-stu-id="8afa6-159">It replicates workloads that are running on VMs and physical servers so that they remain available in a secondary location if the primary site isn't available.</span></span> <span data-ttu-id="8afa6-160">它會復原到主要站台，當它啟動時，再次執行的工作負載。</span><span class="sxs-lookup"><span data-stu-id="8afa6-160">It recovers workloads to the primary site when it's up and running again.</span></span>

<span data-ttu-id="8afa6-161">圖 2-3 會顯示執行的多個 VM 移轉，藉由使用 Azure Site Recovery。</span><span class="sxs-lookup"><span data-stu-id="8afa6-161">Figure 2-3 shows the execution of multiple VM migrations by using Azure Site Recovery.</span></span>

![定位的雲端基礎結構就緒應用程式](./media/image2-3.png)

> <span data-ttu-id="8afa6-163">**圖 2-3。**</span><span class="sxs-lookup"><span data-stu-id="8afa6-163">**Figure 2-3.**</span></span> <span data-ttu-id="8afa6-164">定位的雲端基礎結構就緒應用程式</span><span class="sxs-lookup"><span data-stu-id="8afa6-164">Positioning Cloud Infrastructure-Ready applications</span></span>

### <a name="additional-resources"></a><span data-ttu-id="8afa6-165">其他資源</span><span class="sxs-lookup"><span data-stu-id="8afa6-165">Additional resources</span></span>

- <span data-ttu-id="8afa6-166">**Azure Migrate Datasheet**</span><span class="sxs-lookup"><span data-stu-id="8afa6-166">**Azure Migrate Datasheet**</span></span>

    [https://aka.ms/azuremigration\_datasheet](https://aka.ms/azuremigration\_datasheet)

- <span data-ttu-id="8afa6-167">**Azure Migrate**</span><span class="sxs-lookup"><span data-stu-id="8afa6-167">**Azure Migrate**</span></span>

    [https://aka.ms/azuremigrate](https://aka.ms/azuremigrate)

- <span data-ttu-id="8afa6-168">**Azure 移轉中心**</span><span class="sxs-lookup"><span data-stu-id="8afa6-168">**Azure migration center**</span></span>

    [https://azure.microsoft.com/migration/](https://azure.microsoft.com/migration/)

- <span data-ttu-id="8afa6-169">**使用 Site Recovery 移轉至 Azure**</span><span class="sxs-lookup"><span data-stu-id="8afa6-169">**Migrate to Azure with Site Recovery**</span></span>

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

- <span data-ttu-id="8afa6-170">**Azure Site Recovery 服務概觀**</span><span class="sxs-lookup"><span data-stu-id="8afa6-170">**Azure Site Recovery service overview**</span></span>

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

- <span data-ttu-id="8afa6-171">**在 Azure Vm 的 AWS Vm 移轉**</span><span class="sxs-lookup"><span data-stu-id="8afa6-171">**Migrating VMs in AWS to Azure VMs**</span></span>

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
><span data-ttu-id="8afa6-172">[上一頁](index.md)
>[下一頁](migrate-your-relational-databases-to-azure.md)</span><span class="sxs-lookup"><span data-stu-id="8afa6-172">[Previous](index.md)
[Next](migrate-your-relational-databases-to-azure.md)</span></span>
