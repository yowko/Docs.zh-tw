---
title: "提起並移動現有應用程式的 Azure IaaS"
description: "現代化現有的.NET 應用程式與 Azure 雲端與 Windows 容器。"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eed17ad06c138c3a4eb85f5e023427b681488784
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="lift-and-shift-existing-apps-azure-iaas"></a><span data-ttu-id="06764-103">提起並移動現有應用程式的 Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="06764-103">Lift and shift existing apps Azure IaaS</span></span>

> <span data-ttu-id="06764-104">願景： 以降低您在內部部署投資和總成本的硬體和網路功能維護，只是重新裝載的現有應用程式在雲端中的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="06764-104">Vision: As a first step, to reduce your on-premises investment and total cost of hardware and networking maintenance, simply rehost your existing applications in the cloud.</span></span>

<span data-ttu-id="06764-105">之前*如何*若要移轉至 Azure 的基礎結構即服務 (IaaS) 平台的現有應用程式，務必分析原因*為什麼*您會想要直接與 IaaS 移轉在 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="06764-105">Before getting into *how* to migrate your existing applications to the Azure infrastructure as a service (IaaS) platform, it's important to analyze the reasons *why* you'd want to migrate directly to IaaS in Azure.</span></span> <span data-ttu-id="06764-106">若要開始使用 Vm 雲端，而不是繼續使用目前的內部部署基礎結構中基本上是此現代化成熟度層級的案例。</span><span class="sxs-lookup"><span data-stu-id="06764-106">The scenario at this modernization maturity level essentially is to start using VMs in the cloud, instead of continuing to use your current, on-premises infrastructure.</span></span>

<span data-ttu-id="06764-107">若要分析的另一個點是*為什麼*您可能想要移轉到純虛擬的 IaaS 雲端，而非只新增更多進階在 Azure 中受管理的服務。</span><span class="sxs-lookup"><span data-stu-id="06764-107">Another point to analyze is *why* you might want to migrate to pure IaaS cloud instead of just adding more advanced managed services in Azure.</span></span> <span data-ttu-id="06764-108">您必須判斷的情況下可能會在第一次需要 IaaS。</span><span class="sxs-lookup"><span data-stu-id="06764-108">You need to determine what cases might require IaaS in the first place.</span></span>

<span data-ttu-id="06764-109">圖 2-1 放現代化成熟度層級中的雲端基礎結構就緒應用程式：</span><span class="sxs-lookup"><span data-stu-id="06764-109">Figure 2-1 positions Cloud Infrastructure-Ready applications in the modernization maturity levels:</span></span>

![定位雲端基礎結構就緒應用程式](./media/image2-1.png)

> <span data-ttu-id="06764-111">**圖 2-1。**</span><span class="sxs-lookup"><span data-stu-id="06764-111">**Figure 2-1.**</span></span> <span data-ttu-id="06764-112">定位雲端基礎結構就緒應用程式</span><span class="sxs-lookup"><span data-stu-id="06764-112">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a><span data-ttu-id="06764-113">為什麼要移轉現有的.NET web 應用程式至 Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="06764-113">Why migrate existing .NET web applications to Azure IaaS</span></span> 

<span data-ttu-id="06764-114">若要移轉至雲端，甚至在初始的 IaaS 層級的主要原因是達成成本大幅降低。</span><span class="sxs-lookup"><span data-stu-id="06764-114">The main reason to migrate to the cloud, even at an initial IaaS level, is to achieve cost reductions.</span></span> <span data-ttu-id="06764-115">藉由使用更多的受管理的基礎結構服務，您的組織可以降低其硬體維護、 伺服器或 VM 佈建和部署和管理基礎結構的投資。</span><span class="sxs-lookup"><span data-stu-id="06764-115">By using more managed infrastructure services, your organization can lower its investment in hardware maintenance, server or VM provisioning and deployment, and infrastructure management.</span></span>

<span data-ttu-id="06764-116">您決定要將您的應用程式移到雲端之後，將會更熟悉為什麼您可能會選擇 IaaS 而不是更進階的選項，例如 PaaS 只為的 IaaS 環境的主要原因。</span><span class="sxs-lookup"><span data-stu-id="06764-116">After you make the decision to move your apps to the cloud, the main reason why you might choose IaaS instead of more advanced options like PaaS is simply that the IaaS environment will be more familiar.</span></span> <span data-ttu-id="06764-117">在內部部署環境移至類似於您目前的環境，提供較低的學習曲線，使它的最快速的路徑至雲端。</span><span class="sxs-lookup"><span data-stu-id="06764-117">Moving to an environment that's similar to your current, on-premises environment offers a lower learning curve, which makes it the quickest path to the cloud.</span></span>

<span data-ttu-id="06764-118">不過，採用至雲端最快速的路徑並不表示您將獲得最大效益，不必在雲端中執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="06764-118">However, taking the quickest path to the cloud doesn't mean that you will gain the most benefit from having your applications running in the cloud.</span></span> <span data-ttu-id="06764-119">任何組織會獲得最重要的優點，從雲端移轉已導入了雲端 DevOps 就緒和 PaaS （雲端最佳化） 的成熟度層級。</span><span class="sxs-lookup"><span data-stu-id="06764-119">Any organization will gain the most significant benefits from a cloud migration at the already introduced Cloud DevOps-Ready and PaaS (Cloud-Optimized) maturity levels.</span></span>

<span data-ttu-id="06764-120">它也有變得顯而易見的應用程式會更輕鬆地現代化及重新設計架構，未來在雲端中，即使在 IaaS 上執行時。</span><span class="sxs-lookup"><span data-stu-id="06764-120">It also has become evident that applications are easier to modernize and re-architect in the future when they are already running in the cloud, even on IaaS.</span></span> <span data-ttu-id="06764-121">這是 true 部分因為應用程式資料移轉已完成。</span><span class="sxs-lookup"><span data-stu-id="06764-121">This is true in part because application data migration has already been achieved.</span></span> <span data-ttu-id="06764-122">此外，您的組織會有獲得技術所需的工作在雲端中，並對排班運作 」 雲端文化特性 」。</span><span class="sxs-lookup"><span data-stu-id="06764-122">Also, your organization will have gained skills required for working in the cloud, and made the shift to operating in a "cloud culture."</span></span>

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a><span data-ttu-id="06764-123">當移轉到 PaaS 而不是 IaaS 至</span><span class="sxs-lookup"><span data-stu-id="06764-123">When to migrate to IaaS instead of to PaaS</span></span>

<span data-ttu-id="06764-124">在下一步 區段中，我們將討論主要是基礎 PaaS 平台和服務的 DevOps 雲端應用程式。</span><span class="sxs-lookup"><span data-stu-id="06764-124">In the next sections, we discuss Cloud DevOps-Ready applications that are mostly based on PaaS platforms and services.</span></span> <span data-ttu-id="06764-125">這些應用程式可讓您的大部分優點從移轉至雲端。</span><span class="sxs-lookup"><span data-stu-id="06764-125">These apps give you the most benefits from migrating to the cloud.</span></span>

<span data-ttu-id="06764-126">如果您的目標是單純將現有的應用程式到雲端，首先，識別現有應用程式將會需要大幅修改 Azure App Service 中執行。</span><span class="sxs-lookup"><span data-stu-id="06764-126">If your goal is simply to move existing applications to the cloud, first, identify existing applications that will require substantial modification to run in Azure App Service.</span></span> <span data-ttu-id="06764-127">這些應用程式應該是第一個候選項目。</span><span class="sxs-lookup"><span data-stu-id="06764-127">These apps should be the first candidates.</span></span>

<span data-ttu-id="06764-128">然後，如果您不想要或無法將移到 Windows 容器和/或 Azure Service Fabric 等 Kubernetes orchestrators，棒的是，則當您會使用純文字的 Vm (IaaS)。</span><span class="sxs-lookup"><span data-stu-id="06764-128">Then, if you don't want or still cannot move to Windows Containers and or orchestrators like Azure Service Fabric or Kubernetes, yet, then is when you would use plain VMs (IaaS).</span></span>

<span data-ttu-id="06764-129">但是，請記住，正確地設定、 保護以及維護 Vm 需要更多的時間和相較於使用 PaaS 服務在 Azure 中的 IT 專業知識。</span><span class="sxs-lookup"><span data-stu-id="06764-129">But, keep in mind that correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to using PaaS services in Azure.</span></span> <span data-ttu-id="06764-130">如果您考慮 Azure 虛擬機器，請確定您進行考量的修補程式、 更新和管理 VM 環境所需的持續性維護工作。</span><span class="sxs-lookup"><span data-stu-id="06764-130">If you are considering Azure Virtual Machines, make sure that you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="06764-131">Azure 虛擬機器是 IaaS。</span><span class="sxs-lookup"><span data-stu-id="06764-131">Azure Virtual Machines is IaaS.</span></span>

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a><span data-ttu-id="06764-132">使用 Azure 移轉分析並移轉現有的應用程式至 Azure</span><span class="sxs-lookup"><span data-stu-id="06764-132">Use Azure Migrate to analyze and migrate your existing applications to Azure</span></span>

<span data-ttu-id="06764-133">移轉至雲端不一定要是困難。</span><span class="sxs-lookup"><span data-stu-id="06764-133">Migrating to the cloud doesn't have to be difficult.</span></span> <span data-ttu-id="06764-134">但是，許多組織難開始-以進一步顯示環境中，應用程式、 工作負載和資料之間的緊密相互依存性。</span><span class="sxs-lookup"><span data-stu-id="06764-134">But many organizations struggle to get started - to get deep visibility into the environment and the tight interdependencies between applications, workloads, and data.</span></span> <span data-ttu-id="06764-135">能見度不足，可能很難計劃的路徑向前復原。</span><span class="sxs-lookup"><span data-stu-id="06764-135">Without that visibility, it can be difficult to plan the path forward.</span></span> <span data-ttu-id="06764-136">未成功移轉的必要條件的詳細資訊，您不能有右交談組織內。</span><span class="sxs-lookup"><span data-stu-id="06764-136">Without detailed information on what's required for a successful migration, you can't have the right conversations within your organization.</span></span> <span data-ttu-id="06764-137">您不知道可能成本的優點，或工作負載是否可以只增益集和-shift 或需要大幅重新作業已成功移轉。</span><span class="sxs-lookup"><span data-stu-id="06764-137">You don't know enough about the potential cost benefits, or whether workloads could just lift-and-shift or would require significant rework to migrate successfully.</span></span> <span data-ttu-id="06764-138">難怪，許多組織延遲。</span><span class="sxs-lookup"><span data-stu-id="06764-138">No wonder many organizations hesitate.</span></span>

<span data-ttu-id="06764-139">[Azure 移轉](https://aka.ms/azuremigrate)是一種新的服務，提供指引、 深入資訊，以及協助您移轉至 Azure 時所需的機制。</span><span class="sxs-lookup"><span data-stu-id="06764-139">[Azure Migrate](https://aka.ms/azuremigrate) is a new service that provides the guidance, insights, and mechanisms needed to assist you in migrating to Azure.</span></span> <span data-ttu-id="06764-140">提供 azure 移轉：</span><span class="sxs-lookup"><span data-stu-id="06764-140">Azure Migrate provides:</span></span>

-   <span data-ttu-id="06764-141">探索及評估在內部部署虛擬機器</span><span class="sxs-lookup"><span data-stu-id="06764-141">Discovery and assessment for on-premises virtual machines</span></span>

-   <span data-ttu-id="06764-142">內建的相依性對應的多層應用程式的高信心探索</span><span class="sxs-lookup"><span data-stu-id="06764-142">Inbuilt dependency mapping for high-confidence discovery of multi-tier applications</span></span>

-   <span data-ttu-id="06764-143">智慧型優化到 Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="06764-143">Intelligent rightsizing to Azure virtual machines</span></span>

-   <span data-ttu-id="06764-144">相容性報告與修復的潛在問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="06764-144">Compatibility reporting with guidelines for remediating potential issues</span></span>

-   <span data-ttu-id="06764-145">資料庫探索和移轉 Azure 資料庫管理服務整合</span><span class="sxs-lookup"><span data-stu-id="06764-145">Integration with Azure Database Management Service for database discovery and migration</span></span>

<span data-ttu-id="06764-146">Azure 的移轉可讓您對於的信心，您的工作負載可以移轉與業務的影響降到最低，並如預期般在 Azure 中執行。</span><span class="sxs-lookup"><span data-stu-id="06764-146">Azure Migrate gives you confidence that your workloads can migrate with minimal impact to the business and run as expected in Azure.</span></span> <span data-ttu-id="06764-147">使用適當的工具和指引，您可以達到時以確保重大效能的投資報酬率最大，並且符合可靠性的需求。</span><span class="sxs-lookup"><span data-stu-id="06764-147">With the right tools and guidance, you can achieve maximum return on investment while assuring that critical performance and reliability needs are met.</span></span>

<span data-ttu-id="06764-148">圖 2-2 會顯示由 Azure 移轉的所有伺服器和應用程式連接的內建的相依性對應。</span><span class="sxs-lookup"><span data-stu-id="06764-148">Figure 2-2 shows you the built-in dependency mapping for all server and application connections performed by Azure Migrate.</span></span>

![定位雲端基礎結構就緒應用程式](./media/image2-2.png)

> <span data-ttu-id="06764-150">**圖 2-2。**</span><span class="sxs-lookup"><span data-stu-id="06764-150">**Figure 2-2.**</span></span> <span data-ttu-id="06764-151">定位雲端基礎結構就緒應用程式</span><span class="sxs-lookup"><span data-stu-id="06764-151">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a><span data-ttu-id="06764-152">使用 Azure Site Recovery，以將您現有的 Vm 移轉到 Azure Vm</span><span class="sxs-lookup"><span data-stu-id="06764-152">Use Azure Site Recovery to migrate your existing VMs to Azure VMs</span></span>

<span data-ttu-id="06764-153">做為端對端的一部分[Azure 移轉](https://aka.ms/azuremigrate)， [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)是一種工具可讓您輕鬆地將您的 web 應用程式移轉至 Azure 中的 Vm。</span><span class="sxs-lookup"><span data-stu-id="06764-153">As part of the end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) is a tool that you can use to easily migrate your web apps to VMs in Azure.</span></span> <span data-ttu-id="06764-154">在內部部署 Vm 和實體伺服器複寫至 Azure，或將它們複寫至次要內部部署位置，您可以使用站台復原。</span><span class="sxs-lookup"><span data-stu-id="06764-154">You can use Site Recovery to replicate on-premises VMs and physical servers to Azure, or to replicate them to a secondary on-premises location.</span></span> <span data-ttu-id="06764-155">您甚至可以複寫支援的 Azure VM，在內部部署上執行的工作負載*HYPER-V* VM 上*VMware* VM，或在 Windows 或 Linux 的實體伺服器上。</span><span class="sxs-lookup"><span data-stu-id="06764-155">You can even replicate a workload that's running on a supported Azure VM, on an on-premises *Hyper-V* VM, on a *VMware* VM, or on a Windows or Linux physical server.</span></span> <span data-ttu-id="06764-156">複寫至 Azure 排除的成本和複雜度維護次要資料中心。</span><span class="sxs-lookup"><span data-stu-id="06764-156">Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.</span></span>

<span data-ttu-id="06764-157">站台復原也會特別針對混合式環境的部分在內部部署和部分在 Azure。</span><span class="sxs-lookup"><span data-stu-id="06764-157">Site Recovery is also made specifically for hybrid environments that are partly on-premises and partly on Azure.</span></span> <span data-ttu-id="06764-158">站台復原可協助確保商務持續性會保留您在 Vm 執行的應用程式和內部部署可用的實體伺服器如果站台效能降低。</span><span class="sxs-lookup"><span data-stu-id="06764-158">Site Recovery helps ensure business continuity by keeping your apps that are running on VMs and on-premises physical servers available if a site goes down.</span></span> <span data-ttu-id="06764-159">它會複寫，讓它們留可用在次要位置，如果無法使用主要站台 Vm 和實體伺服器執行的工作負載。</span><span class="sxs-lookup"><span data-stu-id="06764-159">It replicates workloads that are running on VMs and physical servers so that they remain available in a secondary location if the primary site isn't available.</span></span> <span data-ttu-id="06764-160">它會復原到主要站台時的設定而定，再次執行的工作負載。</span><span class="sxs-lookup"><span data-stu-id="06764-160">It recovers workloads to the primary site when it's up and running again.</span></span>

<span data-ttu-id="06764-161">圖 2-3 顯示使用 Azure Site Recovery 的多個 VM 的移轉作業執行。</span><span class="sxs-lookup"><span data-stu-id="06764-161">Figure 2-3 shows the execution of multiple VM migrations by using Azure Site Recovery.</span></span>

![定位雲端基礎結構就緒應用程式](./media/image2-3.png)

> <span data-ttu-id="06764-163">**圖 2-3。**</span><span class="sxs-lookup"><span data-stu-id="06764-163">**Figure 2-3.**</span></span> <span data-ttu-id="06764-164">定位雲端基礎結構就緒應用程式</span><span class="sxs-lookup"><span data-stu-id="06764-164">Positioning Cloud Infrastructure-Ready applications</span></span>

### <a name="additional-resources"></a><span data-ttu-id="06764-165">其他資源</span><span class="sxs-lookup"><span data-stu-id="06764-165">Additional resources</span></span>

-   <span data-ttu-id="06764-166">**Azure 移轉的資料工作表**</span><span class="sxs-lookup"><span data-stu-id="06764-166">**Azure Migrate Datasheet**</span></span>

    [<span data-ttu-id="06764-167">https://aka.ms/azuremigration\_datasheet</span><span class="sxs-lookup"><span data-stu-id="06764-167">https://aka.ms/azuremigration\_datasheet</span></span>](https://aka.ms/azuremigration\_datasheet)

-   <span data-ttu-id="06764-168">**Azure Migrate**</span><span class="sxs-lookup"><span data-stu-id="06764-168">**Azure Migrate**</span></span>

    [<span data-ttu-id="06764-169">http://azuremigrationcenter.com/</span><span class="sxs-lookup"><span data-stu-id="06764-169">http://azuremigrationcenter.com/</span></span>](http://azuremigrationcenter.com/)

-   <span data-ttu-id="06764-170">**移轉至 Azure Site recovery**</span><span class="sxs-lookup"><span data-stu-id="06764-170">**Migrate to Azure with Site Recovery**</span></span>

    [<span data-ttu-id="06764-171">https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure</span><span class="sxs-lookup"><span data-stu-id="06764-171">https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure</span></span>](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

-   <span data-ttu-id="06764-172">**Azure Site Recovery 服務概觀**</span><span class="sxs-lookup"><span data-stu-id="06764-172">**Azure Site Recovery service overview**</span></span>

    [<span data-ttu-id="06764-173">https://docs.microsoft.com/azure/site-recovery/site-recovery-overview</span><span class="sxs-lookup"><span data-stu-id="06764-173">https://docs.microsoft.com/azure/site-recovery/site-recovery-overview</span></span>](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

-   <span data-ttu-id="06764-174">**在 Azure Vm 的 AWS 移轉 Vm**</span><span class="sxs-lookup"><span data-stu-id="06764-174">**Migrating VMs in AWS to Azure VMs**</span></span>

    [<span data-ttu-id="06764-175">https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure</span><span class="sxs-lookup"><span data-stu-id="06764-175">https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure</span></span>](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
<span data-ttu-id="06764-176">[上一頁](index.md)
[下一頁](migrate-your-relational-databases-to-azure.md)</span><span class="sxs-lookup"><span data-stu-id="06764-176">[Previous](index.md)
[Next](migrate-your-relational-databases-to-azure.md)</span></span>
