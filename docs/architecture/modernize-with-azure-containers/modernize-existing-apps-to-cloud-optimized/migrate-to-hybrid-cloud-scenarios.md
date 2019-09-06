---
title: 移轉至混合式雲端案例
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |遷移至混合式雲端案例
ms.date: 04/30/2018
ms.openlocfilehash: 313608c41427b3833bbc873398595ceb37bd7c7d
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373938"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="5c6f7-103">移轉至混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="5c6f7-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="5c6f7-104">有些組織和企業無法將部分應用程式遷移至公用雲端，例如 Microsoft Azure 或任何其他公用雲端（因為法規或其本身的原則）。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="5c6f7-105">不過，在公用雲端和其他內部部署應用程式中，可能會有任何組織受益于其部分應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="5c6f7-106">但混合式環境可能會因為公用雲端與內部部署環境中使用的不同平臺和技術，而導致環境過度複雜。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="5c6f7-107">Microsoft 提供最佳的混合式雲端解決方案，其中您可以在內部部署和公用雲端中優化現有的資產，同時確保 Azure 混合式雲端的一致性。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="5c6f7-108">由於 Azure Stack （內部部署）和 Azure （公用雲端），您可以最大化現有的技能，並取得彈性且一致的方式來建立可在雲端或內部部署中執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="5c6f7-109">在安全性方面，您可以在混合式雲端集中管理和安全性。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="5c6f7-110">您可以藉由提供對內部部署和雲端應用程式的單一登入，從您的資料中心將所有資產控制到雲端。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="5c6f7-111">您可以將 Active Directory 擴充至混合式雲端，並使用身分識別管理來完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="5c6f7-112">最後，您可以順暢地散發和分析資料、針對雲端和內部部署資產使用相同的查詢語言，以及在 Azure 中套用分析和深度學習，以豐富您的資料（不論其來源為何）。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="5c6f7-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="5c6f7-113">Azure Stack</span></span>

<span data-ttu-id="5c6f7-114">Azure Stack 是混合式雲端平臺，可讓您從組織的資料中心提供 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="5c6f7-115">Azure Stack 的設計，是為了在主要案例（例如 edge 和未連線的環境）中支援現代化應用程式的新選項，或符合特定的安全性和合規性需求。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="5c6f7-116">圖4-13 顯示 Microsoft 提供的真正混合式雲端平臺的總覽。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![使用 Azure Stack 和 Azure 的 Microsoft 混合式雲端平臺](./media/image13.jpg)

<span data-ttu-id="5c6f7-118">**圖4-13。**</span><span class="sxs-lookup"><span data-stu-id="5c6f7-118">**Figure 4-13.**</span></span> <span data-ttu-id="5c6f7-119">使用 Azure Stack 和 Azure 的 Microsoft 混合式雲端平臺</span><span class="sxs-lookup"><span data-stu-id="5c6f7-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="5c6f7-120">有兩個部署選項提供 Azure Stack，以符合您的需求：</span><span class="sxs-lookup"><span data-stu-id="5c6f7-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="5c6f7-121">Azure Stack 整合式系統</span><span class="sxs-lookup"><span data-stu-id="5c6f7-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="5c6f7-122">Azure Stack 開發套件</span><span class="sxs-lookup"><span data-stu-id="5c6f7-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="5c6f7-123">Azure Stack 整合式系統</span><span class="sxs-lookup"><span data-stu-id="5c6f7-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="5c6f7-124">Azure Stack 整合系統是透過 Microsoft 與硬體合作夥伴的合作關係來提供。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="5c6f7-125">合作關係所建立的解決方案提供了雲端進度的創新，並與管理中的簡單性達成平衡。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="5c6f7-126">因為 Azure Stack 會當做硬體和軟體的整合系統提供，所以您可以取得適當的彈性和控制量，同時仍採用雲端的創新。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="5c6f7-127">Azure Stack 整合系統的大小範圍是4到12個節點，且硬體合作夥伴和 Microsoft 共同支援。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="5c6f7-128">使用 Azure Stack 整合式系統，為您的生產環境工作負載實行新的案例。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="5c6f7-129">Azure Stack 開發套件</span><span class="sxs-lookup"><span data-stu-id="5c6f7-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="5c6f7-130">Microsoft Azure Stack 開發工具組是 Azure Stack 的單一節點部署，您可以用來評估和瞭解 Azure Stack。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="5c6f7-131">您也可以使用 Azure Stack 開發套件做為開發人員環境，您可以在其中使用與 Azure 一致的 Api 和工具進行開發。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="5c6f7-132">Azure Stack 開發套件不適合作為生產環境使用。</span><span class="sxs-lookup"><span data-stu-id="5c6f7-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5c6f7-133">其他資源</span><span class="sxs-lookup"><span data-stu-id="5c6f7-133">Additional resources</span></span>

- <span data-ttu-id="5c6f7-134">**Azure 混合式雲端**</span><span class="sxs-lookup"><span data-stu-id="5c6f7-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="5c6f7-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="5c6f7-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="5c6f7-136">**Active Directory Windows 容器的服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="5c6f7-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="5c6f7-137">**建立具有 Active Directory 支援的容器**</span><span class="sxs-lookup"><span data-stu-id="5c6f7-137">**Create a container with Active Directory support**</span></span>

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- <span data-ttu-id="5c6f7-138">**Azure Hybrid Benefit 授權**</span><span class="sxs-lookup"><span data-stu-id="5c6f7-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="5c6f7-139">[上一頁](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[下一頁](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="5c6f7-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
