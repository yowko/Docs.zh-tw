---
title: '將現有的 .NET 應用程式隨即轉移到 Azure IaaS (雲端基礎結構就緒) '
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化。
ms.date: 04/28/2018
ms.openlocfilehash: d610222aa6649c1b28e198c074794dd316f895ec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172166"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a><span data-ttu-id="ad01e-103">將現有的 .NET 應用程式隨即轉移到 Azure IaaS (雲端基礎結構就緒) </span><span class="sxs-lookup"><span data-stu-id="ad01e-103">Lift and shift existing .NET apps to Azure IaaS (Cloud Infrastructure-Ready)</span></span>

> <span data-ttu-id="ad01e-104">願景：第一個步驟是減少內部部署的投資，以及硬體和網路維護的總成本，只要在雲端重新裝載現有的應用程式即可。</span><span class="sxs-lookup"><span data-stu-id="ad01e-104">Vision: As a first step, to reduce your on-premises investment and total cost of hardware and networking maintenance, simply rehost your existing applications in the cloud.</span></span>

<span data-ttu-id="ad01e-105">在*瞭解如何*將現有的應用程式遷移至 azure 基礎結構即服務 (IaaS) 平臺之前，請務必先分析您想要直接遷移至 Azure 中 IaaS*的原因。*</span><span class="sxs-lookup"><span data-stu-id="ad01e-105">Before getting into *how* to migrate your existing applications to the Azure infrastructure as a service (IaaS) platform, it's important to analyze the reasons *why* you'd want to migrate directly to IaaS in Azure.</span></span> <span data-ttu-id="ad01e-106">這個現代化成熟度層級的案例基本上是開始使用雲端中的 Vm，而不是繼續使用您目前的內部部署基礎結構。</span><span class="sxs-lookup"><span data-stu-id="ad01e-106">The scenario at this modernization maturity level essentially is to start using VMs in the cloud, instead of continuing to use your current, on-premises infrastructure.</span></span>

<span data-ttu-id="ad01e-107">要分析的另一個 *重點是，* 您可能想要遷移至單純的 IaaS 雲端，而不是只在 Azure 中新增更先進的受控服務。</span><span class="sxs-lookup"><span data-stu-id="ad01e-107">Another point to analyze is *why* you might want to migrate to pure IaaS cloud instead of just adding more advanced managed services in Azure.</span></span> <span data-ttu-id="ad01e-108">判斷哪些案例可能需要 IaaS。</span><span class="sxs-lookup"><span data-stu-id="ad01e-108">Determine what cases might require IaaS in the first place.</span></span>

<span data-ttu-id="ad01e-109">圖2-1 將雲端基礎結構就緒的應用程式置於現代化成熟度層級：</span><span class="sxs-lookup"><span data-stu-id="ad01e-109">Figure 2-1 positions Cloud Infrastructure-Ready applications in the modernization maturity levels:</span></span>

![定位雲端基礎結構就緒的應用程式](./media/image2-1.png)

<span data-ttu-id="ad01e-111">**圖2-1。**</span><span class="sxs-lookup"><span data-stu-id="ad01e-111">**Figure 2-1.**</span></span> <span data-ttu-id="ad01e-112">定位雲端基礎結構就緒的應用程式</span><span class="sxs-lookup"><span data-stu-id="ad01e-112">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a><span data-ttu-id="ad01e-113">將現有 .NET web 應用程式遷移至 Azure IaaS 的原因</span><span class="sxs-lookup"><span data-stu-id="ad01e-113">Why migrate existing .NET web applications to Azure IaaS</span></span>

<span data-ttu-id="ad01e-114">遷移至雲端的主要原因是，即使是在初始 IaaS 層級，也是為了達成成本降低。</span><span class="sxs-lookup"><span data-stu-id="ad01e-114">The main reason to migrate to the cloud, even at an initial IaaS level, is to achieve cost reductions.</span></span> <span data-ttu-id="ad01e-115">藉由使用更多受控基礎結構服務，您的組織可以降低其硬體維護、伺服器或 VM 布建和部署的投資，以及基礎結構管理。</span><span class="sxs-lookup"><span data-stu-id="ad01e-115">By using more managed infrastructure services, your organization can lower its investment in hardware maintenance, server or VM provisioning and deployment, and infrastructure management.</span></span>

<span data-ttu-id="ad01e-116">決定將您的應用程式移至雲端之後，您可能會選擇 IaaS 而非更先進的選項（例如 PaaS），因為 IaaS 環境將更加熟悉。</span><span class="sxs-lookup"><span data-stu-id="ad01e-116">After you make the decision to move your apps to the cloud, the main reason why you might choose IaaS instead of more advanced options like PaaS is simply that the IaaS environment will be more familiar.</span></span> <span data-ttu-id="ad01e-117">移至與您目前的內部部署環境類似的環境，可提供較低的學習曲線，讓它成為最快的雲端途徑。</span><span class="sxs-lookup"><span data-stu-id="ad01e-117">Moving to an environment that's similar to your current, on-premises environment offers a lower learning curve, which makes it the quickest path to the cloud.</span></span>

<span data-ttu-id="ad01e-118">不過，採用最快的雲端途徑，並不表示您在雲端中執行應用程式時，將獲得最大效益。</span><span class="sxs-lookup"><span data-stu-id="ad01e-118">However, taking the quickest path to the cloud doesn't mean that you will gain the most benefit from having your applications running in the cloud.</span></span> <span data-ttu-id="ad01e-119">任何組織都能從雲端遷移中獲得最大的優勢，也就是已推出的雲端優化和雲端原生成熟度等級。</span><span class="sxs-lookup"><span data-stu-id="ad01e-119">Any organization will gain the most significant benefits from a cloud migration at the already introduced Cloud-Optimized and Cloud-Native maturity levels.</span></span>

<span data-ttu-id="ad01e-120">此外，當應用程式已在雲端中執行時，甚至是在 IaaS 上執行時，也會變得更容易現代化和重新架構。</span><span class="sxs-lookup"><span data-stu-id="ad01e-120">It also has become evident that applications are easier to modernize and rearchitect in the future when they are already running in the cloud, even on IaaS.</span></span> <span data-ttu-id="ad01e-121">已達到應用程式資料移轉。</span><span class="sxs-lookup"><span data-stu-id="ad01e-121">Application data migration has already been achieved.</span></span> <span data-ttu-id="ad01e-122">此外，您的組織也會獲得在雲端中工作所需的技能，並讓轉變成為「雲端文化」中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="ad01e-122">Also, your organization will have gained skills required for working in the cloud and made the shift to operating in a "cloud culture."</span></span>

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a><span data-ttu-id="ad01e-123">何時遷移至 IaaS 而非 PaaS</span><span class="sxs-lookup"><span data-stu-id="ad01e-123">When to migrate to IaaS instead of to PaaS</span></span>

<span data-ttu-id="ad01e-124">接下來的幾節將討論大部分的雲端優化應用程式，這些應用程式大多是以 PaaS 平臺和服務為基礎。</span><span class="sxs-lookup"><span data-stu-id="ad01e-124">The next sections discuss Cloud-Optimized applications that are mostly based on PaaS platforms and services.</span></span> <span data-ttu-id="ad01e-125">這些應用程式可讓您從遷移至雲端獲得最大效益。</span><span class="sxs-lookup"><span data-stu-id="ad01e-125">These apps give you the most benefits from migrating to the cloud.</span></span>

<span data-ttu-id="ad01e-126">如果您的目標只是要將現有的應用程式移至雲端，請先找出不需要大量修改才能在 Azure App Service 中執行的現有應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad01e-126">If your goal is simply to move existing applications to the cloud, first, identify existing applications that would not require substantial modification to run in Azure App Service.</span></span> <span data-ttu-id="ad01e-127">這些應用程式應該是第一個雲端優化的候選項目。</span><span class="sxs-lookup"><span data-stu-id="ad01e-127">These apps should be the first candidates for Cloud-Optimized.</span></span>

<span data-ttu-id="ad01e-128">然後，針對仍無法移至 Windows 容器和 PaaS 的應用程式（例如 Azure Kubernetes Service App Service 或協調器），請將這些應用程式遷移至簡單的一般 Vm (IaaS) 。</span><span class="sxs-lookup"><span data-stu-id="ad01e-128">Then, for the apps that still cannot move to Windows Containers and PaaS such as App Service or orchestrators like Azure Kubernetes Service, migrate those to simple plain VMs (IaaS).</span></span>

<span data-ttu-id="ad01e-129">但請記住，相較于在 Azure 中使用 PaaS 服務，正確設定、保護和維護 Vm 需要更多的時間和 IT 專業知識。</span><span class="sxs-lookup"><span data-stu-id="ad01e-129">But, keep in mind that correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to using PaaS services in Azure.</span></span> <span data-ttu-id="ad01e-130">如果您考慮使用 Azure 虛擬機器，請務必考慮修補、更新和管理 VM 環境所需的持續性維護工作。</span><span class="sxs-lookup"><span data-stu-id="ad01e-130">If you are considering Azure Virtual Machines, make sure that you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="ad01e-131">Azure 虛擬機器為 IaaS。</span><span class="sxs-lookup"><span data-stu-id="ad01e-131">Azure Virtual Machines is IaaS.</span></span>

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a><span data-ttu-id="ad01e-132">使用 Azure Migrate 來分析現有的應用程式，並將其遷移至 Azure</span><span class="sxs-lookup"><span data-stu-id="ad01e-132">Use Azure Migrate to analyze and migrate your existing applications to Azure</span></span>

<span data-ttu-id="ad01e-133">遷移至雲端並不難。</span><span class="sxs-lookup"><span data-stu-id="ad01e-133">Migrating to the cloud doesn't have to be difficult.</span></span> <span data-ttu-id="ad01e-134">但許多組織都不難開始著手，以深入瞭解環境，以及應用程式、工作負載和資料之間的緊密相互相關性。</span><span class="sxs-lookup"><span data-stu-id="ad01e-134">But many organizations struggle to get started - to get deep visibility into the environment and the tight interdependencies between applications, workloads, and data.</span></span> <span data-ttu-id="ad01e-135">如果沒有該可見度，就很難規劃轉寄途徑。</span><span class="sxs-lookup"><span data-stu-id="ad01e-135">Without that visibility, it can be difficult to plan the path forward.</span></span> <span data-ttu-id="ad01e-136">若沒有成功遷移所需的詳細資訊，您的組織就不能有正確的交談。</span><span class="sxs-lookup"><span data-stu-id="ad01e-136">Without detailed information on what's required for a successful migration, you can't have the right conversations within your organization.</span></span> <span data-ttu-id="ad01e-137">您並不知道可能的成本優勢，或工作負載是否可以立即轉移，或需要大量的改變才能成功遷移。</span><span class="sxs-lookup"><span data-stu-id="ad01e-137">You don't know enough about the potential cost benefits, or whether workloads could just lift-and-shift or would require significant rework to migrate successfully.</span></span> <span data-ttu-id="ad01e-138">對許多組織來說，並沒有任何疑惑。</span><span class="sxs-lookup"><span data-stu-id="ad01e-138">No wonder many organizations hesitate.</span></span>

<span data-ttu-id="ad01e-139">[Azure Migrate](https://aka.ms/azuremigrate) 是新的服務，可提供協助您遷移至 Azure 所需的指引、見解和機制。</span><span class="sxs-lookup"><span data-stu-id="ad01e-139">[Azure Migrate](https://aka.ms/azuremigrate) is a new service that provides the guidance, insights, and mechanisms needed to assist you in migrating to Azure.</span></span> <span data-ttu-id="ad01e-140">Azure Migrate 提供：</span><span class="sxs-lookup"><span data-stu-id="ad01e-140">Azure Migrate provides:</span></span>

- <span data-ttu-id="ad01e-141">內部部署虛擬機器的探索和評量</span><span class="sxs-lookup"><span data-stu-id="ad01e-141">Discovery and assessment for on-premises virtual machines</span></span>

- <span data-ttu-id="ad01e-142">用於高度信賴探索多層式應用程式的內建相依性對應</span><span class="sxs-lookup"><span data-stu-id="ad01e-142">Inbuilt dependency mapping for high-confidence discovery of multi-tier applications</span></span>

- <span data-ttu-id="ad01e-143">對 Azure 虛擬機器進行智慧型適當大小調整</span><span class="sxs-lookup"><span data-stu-id="ad01e-143">Intelligent right sizing to Azure virtual machines</span></span>

- <span data-ttu-id="ad01e-144">相容性報告以及補救潛在問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="ad01e-144">Compatibility reporting with guidelines for remediating potential issues</span></span>

- <span data-ttu-id="ad01e-145">與 Azure 資料庫管理服務整合，以進行資料庫探索和遷移</span><span class="sxs-lookup"><span data-stu-id="ad01e-145">Integration with Azure Database Management Service for database discovery and migration</span></span>

<span data-ttu-id="ad01e-146">Azure Migrate 可讓您安心地遷移工作負載，對企業的影響最低，並在 Azure 中如預期般執行。</span><span class="sxs-lookup"><span data-stu-id="ad01e-146">Azure Migrate gives you confidence that your workloads can migrate with minimal impact to the business and run as expected in Azure.</span></span> <span data-ttu-id="ad01e-147">使用適當的工具和指導方針，您可以獲得最大投資報酬率，同時確保符合重要的效能和可靠性需求。</span><span class="sxs-lookup"><span data-stu-id="ad01e-147">With the right tools and guidance, you can achieve maximum return on investment while assuring that critical performance and reliability needs are met.</span></span>

<span data-ttu-id="ad01e-148">圖2-2 顯示 Azure Migrate 所執行之所有伺服器和應用程式連接的內建相依性對應。</span><span class="sxs-lookup"><span data-stu-id="ad01e-148">Figure 2-2 shows you the built-in dependency mapping for all server and application connections performed by Azure Migrate.</span></span>

![定位雲端基礎結構就緒的應用程式](./media/image2-2.png)

<span data-ttu-id="ad01e-150">**圖2-2。**</span><span class="sxs-lookup"><span data-stu-id="ad01e-150">**Figure 2-2.**</span></span> <span data-ttu-id="ad01e-151">定位雲端基礎結構就緒的應用程式</span><span class="sxs-lookup"><span data-stu-id="ad01e-151">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a><span data-ttu-id="ad01e-152">使用 Azure Site Recovery 將現有的 Vm 遷移至 Azure Vm</span><span class="sxs-lookup"><span data-stu-id="ad01e-152">Use Azure Site Recovery to migrate your existing VMs to Azure VMs</span></span>

<span data-ttu-id="ad01e-153">作為端對端 [Azure Migrate](https://aka.ms/azuremigrate)的一部分， [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) 是一種工具，可讓您輕鬆地將 web 應用程式遷移至 Azure 中的 vm。</span><span class="sxs-lookup"><span data-stu-id="ad01e-153">As part of the end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) is a tool that you can use to easily migrate your web apps to VMs in Azure.</span></span> <span data-ttu-id="ad01e-154">您可以使用 Site Recovery 將內部部署 Vm 和實體伺服器複寫至 Azure，或將其複寫至次要內部部署位置。</span><span class="sxs-lookup"><span data-stu-id="ad01e-154">You can use Site Recovery to replicate on-premises VMs and physical servers to Azure, or to replicate them to a secondary on-premises location.</span></span> <span data-ttu-id="ad01e-155">您甚至可以複寫在支援的 Azure VM、內部部署 *Hyper-v* VM、 *VMware* Vm 或 Windows 或 Linux 實體伺服器上執行的工作負載。</span><span class="sxs-lookup"><span data-stu-id="ad01e-155">You can even replicate a workload that's running on a supported Azure VM, on an on-premises *Hyper-V* VM, on a *VMware* VM, or on a Windows or Linux physical server.</span></span> <span data-ttu-id="ad01e-156">複寫至 Azure 可排除維護次要資料中心的成本和複雜度。</span><span class="sxs-lookup"><span data-stu-id="ad01e-156">Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.</span></span>

<span data-ttu-id="ad01e-157">Site Recovery 也專門針對部分在內部部署且部分在 Azure 上的混合式環境進行。</span><span class="sxs-lookup"><span data-stu-id="ad01e-157">Site Recovery is also made specifically for hybrid environments that are partly on-premises and partly on Azure.</span></span> <span data-ttu-id="ad01e-158">Site Recovery 有助於確保商務持續性，方法是讓在 Vm 上執行的應用程式和內部部署實體伺服器保持可用狀態（如果網站停止運作）。</span><span class="sxs-lookup"><span data-stu-id="ad01e-158">Site Recovery helps ensure business continuity by keeping your apps that are running on VMs and on-premises physical servers available if a site goes down.</span></span> <span data-ttu-id="ad01e-159">它會複寫在 Vm 和實體伺服器上執行的工作負載，以便在主要網站無法使用時，仍可在次要位置中使用。</span><span class="sxs-lookup"><span data-stu-id="ad01e-159">It replicates workloads that are running on VMs and physical servers so that they remain available in a secondary location if the primary site isn't available.</span></span> <span data-ttu-id="ad01e-160">當主要網站再次開始運作及執行時，它會將工作負載復原至其中。</span><span class="sxs-lookup"><span data-stu-id="ad01e-160">It recovers workloads to the primary site when it's up and running again.</span></span>

<span data-ttu-id="ad01e-161">圖2-3 顯示如何使用 Azure Site Recovery 來執行多個 VM 遷移。</span><span class="sxs-lookup"><span data-stu-id="ad01e-161">Figure 2-3 shows the execution of multiple VM migrations by using Azure Site Recovery.</span></span>

![定位雲端基礎結構就緒的應用程式](./media/image2-3.png)

<span data-ttu-id="ad01e-163">**圖2-3。**</span><span class="sxs-lookup"><span data-stu-id="ad01e-163">**Figure 2-3.**</span></span> <span data-ttu-id="ad01e-164">定位雲端基礎結構就緒的應用程式</span><span class="sxs-lookup"><span data-stu-id="ad01e-164">Positioning Cloud Infrastructure-Ready applications</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ad01e-165">其他資源</span><span class="sxs-lookup"><span data-stu-id="ad01e-165">Additional resources</span></span>

- <span data-ttu-id="ad01e-166">**Azure Migrate 資料工作表**</span><span class="sxs-lookup"><span data-stu-id="ad01e-166">**Azure Migrate Datasheet**</span></span>

    <https://aka.ms/azuremigration\_datasheet>

- <span data-ttu-id="ad01e-167">**Azure Migrate**</span><span class="sxs-lookup"><span data-stu-id="ad01e-167">**Azure Migrate**</span></span>

    <https://aka.ms/azuremigrate>

- <span data-ttu-id="ad01e-168">**Azure 移轉中心**</span><span class="sxs-lookup"><span data-stu-id="ad01e-168">**Azure migration center**</span></span>

    <https://azure.microsoft.com/migration/>

- <span data-ttu-id="ad01e-169">**使用 Site Recovery 移轉至 Azure**</span><span class="sxs-lookup"><span data-stu-id="ad01e-169">**Migrate to Azure with Site Recovery**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- <span data-ttu-id="ad01e-170">**Azure Site Recovery 服務總覽**</span><span class="sxs-lookup"><span data-stu-id="ad01e-170">**Azure Site Recovery service overview**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- <span data-ttu-id="ad01e-171">**將 AWS 中的 Vm 遷移至 Azure Vm**</span><span class="sxs-lookup"><span data-stu-id="ad01e-171">**Migrating VMs in AWS to Azure VMs**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
><span data-ttu-id="ad01e-172">[上一個](index.md) 
>[下一步](migrate-your-relational-databases-to-azure.md)</span><span class="sxs-lookup"><span data-stu-id="ad01e-172">[Previous](index.md)
[Next](migrate-your-relational-databases-to-azure.md)</span></span> <!-- Next Chapter -->
