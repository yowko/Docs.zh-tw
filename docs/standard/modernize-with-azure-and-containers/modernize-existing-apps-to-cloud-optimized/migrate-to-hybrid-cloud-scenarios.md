---
title: 移轉至混合式雲端案例
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器 |移轉至混合式雲端案例
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 8885ee8fce4f8c11c14ee8936f3ee0ffd89ece04
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="13676-103">移轉至混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="13676-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="13676-104">有些組織和企業無法移轉應用程式，以如 Microsoft Azure 公用雲端，或是其他任何公用雲端，因為法規或自己的原則。</span><span class="sxs-lookup"><span data-stu-id="13676-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="13676-105">不過，很可能在任何組織可能會受益需要某些公用雲端和其他應用程式在內部部署其應用程式。</span><span class="sxs-lookup"><span data-stu-id="13676-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="13676-106">但在混合的環境可能會造成過多的複雜性，因為不同平台和公用雲端與內部部署環境中所用技術的環境中。</span><span class="sxs-lookup"><span data-stu-id="13676-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="13676-107">Microsoft 提供最佳的混合式雲端解決方案，其中一個可以最佳化現有的資產內部和公用雲端，同時確保可在 Azure 的混合式雲端中的一致性。</span><span class="sxs-lookup"><span data-stu-id="13676-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="13676-108">您可以將現有的技術，最大化，並取得建置雲端或內部部署，這點受惠 Azure 堆疊 （內部） 和 Azure （公用雲端） 中執行的應用程式彈性、 統一的方式。</span><span class="sxs-lookup"><span data-stu-id="13676-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="13676-109">當安全性方面時，您可以混合式雲端間集中管理和安全性。</span><span class="sxs-lookup"><span data-stu-id="13676-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="13676-110">您可以從您的資料中心到雲端，取得所有資產，控制權，藉由提供單一登入至內部和雲端應用程式。</span><span class="sxs-lookup"><span data-stu-id="13676-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="13676-111">您完成這項作業將 Active Directory 延伸到混合式雲端，並使用身分識別管理。</span><span class="sxs-lookup"><span data-stu-id="13676-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="13676-112">最後，您可以發佈和順暢地分析資料，請使用相同的查詢語言的雲端和內部部署資產，並套用分析和深入了解 Azure 來充實資料，不論其來源中。</span><span class="sxs-lookup"><span data-stu-id="13676-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="13676-113">Azure 的堆疊</span><span class="sxs-lookup"><span data-stu-id="13676-113">Azure Stack</span></span>

<span data-ttu-id="13676-114">Azure 堆疊是混合式雲端平台，可讓您提供 Azure 服務，從您組織的資料中心。</span><span class="sxs-lookup"><span data-stu-id="13676-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="13676-115">Azure 堆疊被設計來支援您在索引鍵的情況下，例如邊緣和未連接的環境中或符合特定的安全性與相容性需求的現代應用程式的新選項。</span><span class="sxs-lookup"><span data-stu-id="13676-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="13676-116">圖 4-13 顯示，則為 true 的混合式雲端平台 Microsoft 所提供的概觀。</span><span class="sxs-lookup"><span data-stu-id="13676-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Microsoft Azure 堆疊與 Azure 混合式雲端平台](./media/image13.jpg)

> <span data-ttu-id="13676-118">**圖 4-13。**</span><span class="sxs-lookup"><span data-stu-id="13676-118">**Figure 4-13.**</span></span> <span data-ttu-id="13676-119">Microsoft Azure 堆疊與 Azure 混合式雲端平台</span><span class="sxs-lookup"><span data-stu-id="13676-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="13676-120">Azure 堆疊提供兩種部署選項，以符合您需求：</span><span class="sxs-lookup"><span data-stu-id="13676-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

-   <span data-ttu-id="13676-121">Azure 整合堆疊系統</span><span class="sxs-lookup"><span data-stu-id="13676-121">Azure Stack integrated systems</span></span>

-   <span data-ttu-id="13676-122">Azure 堆疊開發套件</span><span class="sxs-lookup"><span data-stu-id="13676-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="13676-123">Azure 整合堆疊系統</span><span class="sxs-lookup"><span data-stu-id="13676-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="13676-124">透過 Microsoft 和硬體合作夥伴的合作關係提供 azure 堆疊整合系統。</span><span class="sxs-lookup"><span data-stu-id="13676-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="13676-125">合作關係建立的方案提供平衡為了簡單起見，在管理雲端操作創新。</span><span class="sxs-lookup"><span data-stu-id="13676-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="13676-126">Azure 堆疊只提供作為整合的系統的硬體和軟體，因為您會取得適合容量的彈性和控制，同時仍採用創新從雲端。</span><span class="sxs-lookup"><span data-stu-id="13676-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="13676-127">Azure 整合堆疊系統大小介於 4 到 12 的節點，並共同支援硬體合作夥伴和 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="13676-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="13676-128">使用 Azure 堆疊整合系統，以實作您的生產工作負載的新案例。</span><span class="sxs-lookup"><span data-stu-id="13676-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="13676-129">Azure 堆疊開發套件</span><span class="sxs-lookup"><span data-stu-id="13676-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="13676-130">Microsoft Azure 堆疊開發套件是單一節點部署 Azure 堆疊，您可以使用來評估，並了解 Azure 堆疊。</span><span class="sxs-lookup"><span data-stu-id="13676-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="13676-131">您也可以使用 Azure 堆疊開發套件做為開發人員環境，其中您可以使用 Api 來開發及工具，會與 Azure 一致。</span><span class="sxs-lookup"><span data-stu-id="13676-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="13676-132">Azure 堆疊開發套件不是要做為實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="13676-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="13676-133">其他資源</span><span class="sxs-lookup"><span data-stu-id="13676-133">Additional resources</span></span>

-   <span data-ttu-id="13676-134">**Azure 的混合式雲端**</span><span class="sxs-lookup"><span data-stu-id="13676-134">**Azure hybrid cloud**</span></span>

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   <span data-ttu-id="13676-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="13676-135">**Azure Stack**</span></span>

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   <span data-ttu-id="13676-136">**Windows 容器的 active Directory 服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="13676-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   <span data-ttu-id="13676-137">**使用 Active Directory 支援建立容器**</span><span class="sxs-lookup"><span data-stu-id="13676-137">**Create a container with Active Directory support**</span></span>

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   <span data-ttu-id="13676-138">**Azure 的混合式權益授權**</span><span class="sxs-lookup"><span data-stu-id="13676-138">**Azure Hybrid Benefit licensing**</span></span>

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
<span data-ttu-id="13676-139">[上一頁](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[下一頁](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="13676-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
