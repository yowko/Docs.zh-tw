---
title: 提升現有 .NET 應用並將其轉移到 Azure IaaS（雲基礎架構就緒）
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化改造。
ms.date: 04/28/2018
ms.openlocfilehash: c7638a034dbb27baea1b097bdb66175bfb5a71f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089640"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a><span data-ttu-id="52055-103">提升現有 .NET 應用並將其轉移到 Azure IaaS（雲基礎架構就緒）</span><span class="sxs-lookup"><span data-stu-id="52055-103">Lift and shift existing .NET apps to Azure IaaS (Cloud Infrastructure-Ready)</span></span>

> <span data-ttu-id="52055-104">願景：作為第一步，為了降低本地投資和硬體和網路維護總成本，只需在雲中重新託管現有應用程式即可。</span><span class="sxs-lookup"><span data-stu-id="52055-104">Vision: As a first step, to reduce your on-premises investment and total cost of hardware and networking maintenance, simply rehost your existing applications in the cloud.</span></span>

<span data-ttu-id="52055-105">在*瞭解如何*將現有應用程式作為服務 （IaaS） 平臺遷移到 Azure 基礎結構之前，請務必分析要直接遷移到 Azure 中的 IaaS*的原因。*</span><span class="sxs-lookup"><span data-stu-id="52055-105">Before getting into *how* to migrate your existing applications to the Azure infrastructure as a service (IaaS) platform, it's important to analyze the reasons *why* you'd want to migrate directly to IaaS in Azure.</span></span> <span data-ttu-id="52055-106">此現代化成熟度級別的方案實質是開始在雲中使用 VM，而不是繼續使用當前本地基礎結構。</span><span class="sxs-lookup"><span data-stu-id="52055-106">The scenario at this modernization maturity level essentially is to start using VMs in the cloud, instead of continuing to use your current, on-premises infrastructure.</span></span>

<span data-ttu-id="52055-107">需要分析的另一點是 *，為什麼*您可能希望遷移到純 IaaS 雲，而不只是在 Azure 中添加更高級的託管服務。</span><span class="sxs-lookup"><span data-stu-id="52055-107">Another point to analyze is *why* you might want to migrate to pure IaaS cloud instead of just adding more advanced managed services in Azure.</span></span> <span data-ttu-id="52055-108">首先確定哪些情況可能需要 IaaS。</span><span class="sxs-lookup"><span data-stu-id="52055-108">Determine what cases might require IaaS in the first place.</span></span>

<span data-ttu-id="52055-109">圖 2-1 將雲基礎架構就緒應用程式定位在現代化成熟度級別：</span><span class="sxs-lookup"><span data-stu-id="52055-109">Figure 2-1 positions Cloud Infrastructure-Ready applications in the modernization maturity levels:</span></span>

![定位雲基礎架構就緒應用程式](./media/image2-1.png)

<span data-ttu-id="52055-111">**圖 2-1。**</span><span class="sxs-lookup"><span data-stu-id="52055-111">**Figure 2-1.**</span></span> <span data-ttu-id="52055-112">定位雲基礎架構就緒應用程式</span><span class="sxs-lookup"><span data-stu-id="52055-112">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a><span data-ttu-id="52055-113">為什麼將現有的 .NET Web 應用程式遷移到 Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="52055-113">Why migrate existing .NET web applications to Azure IaaS</span></span>

<span data-ttu-id="52055-114">遷移到雲的主要原因，即使在初始 IaaS 級別，也是為了實現成本降低。</span><span class="sxs-lookup"><span data-stu-id="52055-114">The main reason to migrate to the cloud, even at an initial IaaS level, is to achieve cost reductions.</span></span> <span data-ttu-id="52055-115">通過使用更多託管基礎結構服務，您的組織可以降低其在硬體維護、伺服器或 VM 配置和部署以及基礎結構管理方面的投資。</span><span class="sxs-lookup"><span data-stu-id="52055-115">By using more managed infrastructure services, your organization can lower its investment in hardware maintenance, server or VM provisioning and deployment, and infrastructure management.</span></span>

<span data-ttu-id="52055-116">在決定將應用移動到雲中後，選擇 IaaS 而不是像 PaaS 等更高級選項的主要原因很簡單，IaaS 環境將更為熟悉。</span><span class="sxs-lookup"><span data-stu-id="52055-116">After you make the decision to move your apps to the cloud, the main reason why you might choose IaaS instead of more advanced options like PaaS is simply that the IaaS environment will be more familiar.</span></span> <span data-ttu-id="52055-117">遷移到與當前本地環境類似的環境提供了較低的學習曲線，使其成為通往雲的最快路徑。</span><span class="sxs-lookup"><span data-stu-id="52055-117">Moving to an environment that's similar to your current, on-premises environment offers a lower learning curve, which makes it the quickest path to the cloud.</span></span>

<span data-ttu-id="52055-118">但是，以最快的路徑訪問雲並不意味著您將從在雲中運行應用程式中獲得最大好處。</span><span class="sxs-lookup"><span data-stu-id="52055-118">However, taking the quickest path to the cloud doesn't mean that you will gain the most benefit from having your applications running in the cloud.</span></span> <span data-ttu-id="52055-119">在已經引入的雲優化和雲原生成熟度級別，任何組織都將從雲遷移中獲得最重要的好處。</span><span class="sxs-lookup"><span data-stu-id="52055-119">Any organization will gain the most significant benefits from a cloud migration at the already introduced Cloud-Optimized and Cloud-Native maturity levels.</span></span>

<span data-ttu-id="52055-120">也很明顯，應用程式將來在雲中運行時更容易實現現代化和重新構建，甚至在 IaaS 上也是如此。</span><span class="sxs-lookup"><span data-stu-id="52055-120">It also has become evident that applications are easier to modernize and rearchitect in the future when they are already running in the cloud, even on IaaS.</span></span> <span data-ttu-id="52055-121">應用程式資料移轉已經實現。</span><span class="sxs-lookup"><span data-stu-id="52055-121">Application data migration has already been achieved.</span></span> <span data-ttu-id="52055-122">此外，您的組織將獲得在雲中工作所需的技能，並轉向在"雲文化中"運營。</span><span class="sxs-lookup"><span data-stu-id="52055-122">Also, your organization will have gained skills required for working in the cloud and made the shift to operating in a "cloud culture."</span></span>

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a><span data-ttu-id="52055-123">何時遷移到 IaaS 而不是 PaaS</span><span class="sxs-lookup"><span data-stu-id="52055-123">When to migrate to IaaS instead of to PaaS</span></span>

<span data-ttu-id="52055-124">下一節將討論主要基於 PaaS 平臺和服務的雲優化應用程式。</span><span class="sxs-lookup"><span data-stu-id="52055-124">The next sections discuss Cloud-Optimized applications that are mostly based on PaaS platforms and services.</span></span> <span data-ttu-id="52055-125">這些應用從遷移到雲中為您提供最大的好處。</span><span class="sxs-lookup"><span data-stu-id="52055-125">These apps give you the most benefits from migrating to the cloud.</span></span>

<span data-ttu-id="52055-126">如果目標只是將現有應用程式移動到雲中，請首先確定不需要大量修改即可在 Azure 應用服務中運行的現有應用程式。</span><span class="sxs-lookup"><span data-stu-id="52055-126">If your goal is simply to move existing applications to the cloud, first, identify existing applications that would not require substantial modification to run in Azure App Service.</span></span> <span data-ttu-id="52055-127">這些應用應該是雲優化的首批候選應用。</span><span class="sxs-lookup"><span data-stu-id="52055-127">These apps should be the first candidates for Cloud-Optimized.</span></span>

<span data-ttu-id="52055-128">然後，對於仍無法移動到 Windows 容器和 PaaS 的應用（如應用服務或 Azure Kubernetes 服務等協調器），將這些應用遷移到簡單的普通 VM （IaaS）。</span><span class="sxs-lookup"><span data-stu-id="52055-128">Then, for the apps that still cannot move to Windows Containers and PaaS such as App Service or orchestrators like Azure Kubernetes Service, migrate those to simple plain VMs (IaaS).</span></span>

<span data-ttu-id="52055-129">但是，請記住，與在 Azure 中使用 PaaS 服務相比，正確配置、保護和維護 VM 需要更多的時間和 IT 專業知識。</span><span class="sxs-lookup"><span data-stu-id="52055-129">But, keep in mind that correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to using PaaS services in Azure.</span></span> <span data-ttu-id="52055-130">如果正在考慮 Azure 虛擬機器，請確保考慮到修補、更新和管理 VM 環境所需的持續維護工作。</span><span class="sxs-lookup"><span data-stu-id="52055-130">If you are considering Azure Virtual Machines, make sure that you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="52055-131">Azure 虛擬機器是 IaaS。</span><span class="sxs-lookup"><span data-stu-id="52055-131">Azure Virtual Machines is IaaS.</span></span>

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a><span data-ttu-id="52055-132">使用 Azure 遷移分析現有應用程式並將其遷移到 Azure</span><span class="sxs-lookup"><span data-stu-id="52055-132">Use Azure Migrate to analyze and migrate your existing applications to Azure</span></span>

<span data-ttu-id="52055-133">遷移到雲並不一定困難。</span><span class="sxs-lookup"><span data-stu-id="52055-133">Migrating to the cloud doesn't have to be difficult.</span></span> <span data-ttu-id="52055-134">但是，許多組織很難開始工作-要深入瞭解環境以及應用程式、工作負載和資料之間的緊密相互依賴性。</span><span class="sxs-lookup"><span data-stu-id="52055-134">But many organizations struggle to get started - to get deep visibility into the environment and the tight interdependencies between applications, workloads, and data.</span></span> <span data-ttu-id="52055-135">如果沒有這種可見度，就很難規劃前進的道路。</span><span class="sxs-lookup"><span data-stu-id="52055-135">Without that visibility, it can be difficult to plan the path forward.</span></span> <span data-ttu-id="52055-136">如果沒有有關成功遷移所需的詳細資訊，則無法在組織內進行正確的對話。</span><span class="sxs-lookup"><span data-stu-id="52055-136">Without detailed information on what's required for a successful migration, you can't have the right conversations within your organization.</span></span> <span data-ttu-id="52055-137">您對潛在的成本優勢瞭解不足，或者工作負載是否可以只是提升和移動，或者成功遷移需要大量的重新工作。</span><span class="sxs-lookup"><span data-stu-id="52055-137">You don't know enough about the potential cost benefits, or whether workloads could just lift-and-shift or would require significant rework to migrate successfully.</span></span> <span data-ttu-id="52055-138">難怪許多組織猶豫不決。</span><span class="sxs-lookup"><span data-stu-id="52055-138">No wonder many organizations hesitate.</span></span>

<span data-ttu-id="52055-139">[Azure 遷移](https://aka.ms/azuremigrate)是一項新服務，它提供説明您遷移到 Azure 所需的指導、見解和機制。</span><span class="sxs-lookup"><span data-stu-id="52055-139">[Azure Migrate](https://aka.ms/azuremigrate) is a new service that provides the guidance, insights, and mechanisms needed to assist you in migrating to Azure.</span></span> <span data-ttu-id="52055-140">Azure Migrate 提供：</span><span class="sxs-lookup"><span data-stu-id="52055-140">Azure Migrate provides:</span></span>

- <span data-ttu-id="52055-141">本地虛擬機器的發現和評估</span><span class="sxs-lookup"><span data-stu-id="52055-141">Discovery and assessment for on-premises virtual machines</span></span>

- <span data-ttu-id="52055-142">內置依賴項映射，用於高置度發現多層應用程式</span><span class="sxs-lookup"><span data-stu-id="52055-142">Inbuilt dependency mapping for high-confidence discovery of multi-tier applications</span></span>

- <span data-ttu-id="52055-143">智慧右大小調整到 Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="52055-143">Intelligent right sizing to Azure virtual machines</span></span>

- <span data-ttu-id="52055-144">相容性報告與修復潛在問題的準則</span><span class="sxs-lookup"><span data-stu-id="52055-144">Compatibility reporting with guidelines for remediating potential issues</span></span>

- <span data-ttu-id="52055-145">與 Azure 資料庫管理服務集成，用於資料庫發現和遷移</span><span class="sxs-lookup"><span data-stu-id="52055-145">Integration with Azure Database Management Service for database discovery and migration</span></span>

<span data-ttu-id="52055-146">Azure 遷移讓您確信工作負荷可以遷移，對業務的影響最小，並在 Azure 中按預期運行。</span><span class="sxs-lookup"><span data-stu-id="52055-146">Azure Migrate gives you confidence that your workloads can migrate with minimal impact to the business and run as expected in Azure.</span></span> <span data-ttu-id="52055-147">借助正確的工具和指南，您可以實現最大的投資回報，同時確保滿足關鍵性能和可靠性需求。</span><span class="sxs-lookup"><span data-stu-id="52055-147">With the right tools and guidance, you can achieve maximum return on investment while assuring that critical performance and reliability needs are met.</span></span>

<span data-ttu-id="52055-148">圖 2-2 顯示了 Azure 遷移執行的所有伺服器和應用程式連接的內置依賴關係映射。</span><span class="sxs-lookup"><span data-stu-id="52055-148">Figure 2-2 shows you the built-in dependency mapping for all server and application connections performed by Azure Migrate.</span></span>

![定位雲基礎架構就緒應用程式](./media/image2-2.png)

<span data-ttu-id="52055-150">**圖2-2。**</span><span class="sxs-lookup"><span data-stu-id="52055-150">**Figure 2-2.**</span></span> <span data-ttu-id="52055-151">定位雲基礎架構就緒應用程式</span><span class="sxs-lookup"><span data-stu-id="52055-151">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a><span data-ttu-id="52055-152">使用 Azure 網站恢復將現有 VM 遷移到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="52055-152">Use Azure Site Recovery to migrate your existing VMs to Azure VMs</span></span>

<span data-ttu-id="52055-153">作為端到端[Azure 遷移](https://aka.ms/azuremigrate)的一部分[，Azure 網站恢復](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)是一種工具，可用於輕鬆地將 Web 應用遷移到 Azure 中的 VM。</span><span class="sxs-lookup"><span data-stu-id="52055-153">As part of the end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) is a tool that you can use to easily migrate your web apps to VMs in Azure.</span></span> <span data-ttu-id="52055-154">可以使用網站恢復將本地 VM 和物理伺服器複製到 Azure，或將其複製到輔助本地位置。</span><span class="sxs-lookup"><span data-stu-id="52055-154">You can use Site Recovery to replicate on-premises VMs and physical servers to Azure, or to replicate them to a secondary on-premises location.</span></span> <span data-ttu-id="52055-155">您甚至可以複製在受支援的 Azure VM、本地*Hyper-V* *VM、VMware* VM 上或在 Windows 或 Linux 物理伺服器上運行的工作負載。</span><span class="sxs-lookup"><span data-stu-id="52055-155">You can even replicate a workload that's running on a supported Azure VM, on an on-premises *Hyper-V* VM, on a *VMware* VM, or on a Windows or Linux physical server.</span></span> <span data-ttu-id="52055-156">複寫至 Azure 可排除維護次要資料中心的成本和複雜度。</span><span class="sxs-lookup"><span data-stu-id="52055-156">Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.</span></span>

<span data-ttu-id="52055-157">網站恢復還專門針對部分本地和部分在 Azure 上的混合環境。</span><span class="sxs-lookup"><span data-stu-id="52055-157">Site Recovery is also made specifically for hybrid environments that are partly on-premises and partly on Azure.</span></span> <span data-ttu-id="52055-158">網站恢復通過在 VM 和本地物理伺服器上運行的應用（如果網站出現故障時）保持可用，有助於確保業務連續性。</span><span class="sxs-lookup"><span data-stu-id="52055-158">Site Recovery helps ensure business continuity by keeping your apps that are running on VMs and on-premises physical servers available if a site goes down.</span></span> <span data-ttu-id="52055-159">它複製在 VM 和物理伺服器上運行的工作負載，以便在主網站無法接通，這些工作負載在輔助位置保持可用。</span><span class="sxs-lookup"><span data-stu-id="52055-159">It replicates workloads that are running on VMs and physical servers so that they remain available in a secondary location if the primary site isn't available.</span></span> <span data-ttu-id="52055-160">當主要網站再次開始運作及執行時，它會將工作負載復原至其中。</span><span class="sxs-lookup"><span data-stu-id="52055-160">It recovers workloads to the primary site when it's up and running again.</span></span>

<span data-ttu-id="52055-161">圖 2-3 顯示了使用 Azure 網站恢復執行多個 VM 遷移。</span><span class="sxs-lookup"><span data-stu-id="52055-161">Figure 2-3 shows the execution of multiple VM migrations by using Azure Site Recovery.</span></span>

![定位雲基礎架構就緒應用程式](./media/image2-3.png)

<span data-ttu-id="52055-163">**圖 2-3。**</span><span class="sxs-lookup"><span data-stu-id="52055-163">**Figure 2-3.**</span></span> <span data-ttu-id="52055-164">定位雲基礎架構就緒應用程式</span><span class="sxs-lookup"><span data-stu-id="52055-164">Positioning Cloud Infrastructure-Ready applications</span></span>

### <a name="additional-resources"></a><span data-ttu-id="52055-165">其他資源</span><span class="sxs-lookup"><span data-stu-id="52055-165">Additional resources</span></span>

- <span data-ttu-id="52055-166">**Azure 遷移資料表**</span><span class="sxs-lookup"><span data-stu-id="52055-166">**Azure Migrate Datasheet**</span></span>

    <https://aka.ms/azuremigration\_datasheet>

- <span data-ttu-id="52055-167">**Azure 遷移**</span><span class="sxs-lookup"><span data-stu-id="52055-167">**Azure Migrate**</span></span>

    <https://aka.ms/azuremigrate>

- <span data-ttu-id="52055-168">**Azure 遷移中心**</span><span class="sxs-lookup"><span data-stu-id="52055-168">**Azure migration center**</span></span>

    <https://azure.microsoft.com/migration/>

- <span data-ttu-id="52055-169">**使用 Site Recovery 移轉至 Azure**</span><span class="sxs-lookup"><span data-stu-id="52055-169">**Migrate to Azure with Site Recovery**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- <span data-ttu-id="52055-170">**Azure 網站恢復服務概述**</span><span class="sxs-lookup"><span data-stu-id="52055-170">**Azure Site Recovery service overview**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- <span data-ttu-id="52055-171">**將 AWS 中的 VM 遷移到 Azure VM**</span><span class="sxs-lookup"><span data-stu-id="52055-171">**Migrating VMs in AWS to Azure VMs**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
><span data-ttu-id="52055-172">[上一個](index.md)
>[下一個](migrate-your-relational-databases-to-azure.md)</span><span class="sxs-lookup"><span data-stu-id="52055-172">[Previous](index.md)
[Next](migrate-your-relational-databases-to-azure.md)</span></span> <!-- Next Chapter -->
