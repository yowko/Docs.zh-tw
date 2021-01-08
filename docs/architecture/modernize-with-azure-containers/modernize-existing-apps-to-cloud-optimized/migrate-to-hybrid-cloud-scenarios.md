---
title: 移轉至混合式雲端案例
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |遷移至混合式雲端案例
ms.date: 12/21/2020
ms.openlocfilehash: d5bf7f08381f3718061742b37c73604d8e57f1e2
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025221"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="a7a97-103">移轉至混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="a7a97-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="a7a97-104">某些組織和企業無法將部分應用程式遷移至公用雲端，例如 Microsoft Azure 或其他任何公用雲端（因為法規或其本身的原則）。</span><span class="sxs-lookup"><span data-stu-id="a7a97-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="a7a97-105">不過，在公用雲端和其他內部部署應用程式中，可能會有任何組織受益。</span><span class="sxs-lookup"><span data-stu-id="a7a97-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="a7a97-106">但是，混合的環境可能會在環境中造成過度複雜的情況，因為公用雲端與內部部署環境中使用不同的平臺和技術。</span><span class="sxs-lookup"><span data-stu-id="a7a97-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="a7a97-107">Microsoft 提供最佳的混合式雲端解決方案，可讓您在內部部署和公用雲端中優化現有的資產，同時確保 Azure 混合式雲端中的一致性。</span><span class="sxs-lookup"><span data-stu-id="a7a97-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="a7a97-108">您可以充分發揮現有技能的最大效用，並取得彈性、統一的方法來建立可在雲端或內部部署中執行的應用程式，因為 Azure Stack (內部部署) 和 Azure (公用雲端) 。</span><span class="sxs-lookup"><span data-stu-id="a7a97-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="a7a97-109">在安全性方面，您可以在混合式雲端集中管理和安全性。</span><span class="sxs-lookup"><span data-stu-id="a7a97-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="a7a97-110">您可以藉由提供對內部部署和雲端應用程式的單一登入，來掌控所有資產，從資料中心到雲端。</span><span class="sxs-lookup"><span data-stu-id="a7a97-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="a7a97-111">您可以藉由將 Active Directory 延伸至混合式雲端，以及使用身分識別管理來完成這項功能。</span><span class="sxs-lookup"><span data-stu-id="a7a97-111">You accomplish this functionality by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="a7a97-112">最後，您可以順暢地散發和分析資料、針對雲端和內部部署資產使用相同的查詢語言，並在 Azure 中套用分析和深度學習，以豐富您的資料，不論其來源為何。</span><span class="sxs-lookup"><span data-stu-id="a7a97-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="a7a97-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="a7a97-113">Azure Stack</span></span>

<span data-ttu-id="a7a97-114">Azure Stack 是混合式雲端平臺，可讓您從組織的資料中心提供 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="a7a97-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="a7a97-115">Azure Stack 的設計目的是在主要案例（例如 edge 和未連線的環境）中支援新式應用程式的新選項，或符合特定的安全性和合規性需求。</span><span class="sxs-lookup"><span data-stu-id="a7a97-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="a7a97-116">圖4-13 顯示 Microsoft 所提供之真正混合式雲端平臺的總覽。</span><span class="sxs-lookup"><span data-stu-id="a7a97-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Microsoft 混合式雲端平臺與 Azure Stack 和 Azure 的圖表。](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

<span data-ttu-id="a7a97-118">**圖4-13。**</span><span class="sxs-lookup"><span data-stu-id="a7a97-118">**Figure 4-13.**</span></span> <span data-ttu-id="a7a97-119">使用 Azure Stack 和 Azure 的 Microsoft 混合式雲端平臺</span><span class="sxs-lookup"><span data-stu-id="a7a97-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="a7a97-120">Azure Stack 提供兩種部署選項，以符合您的需求：</span><span class="sxs-lookup"><span data-stu-id="a7a97-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="a7a97-121">Azure Stack 整合系統</span><span class="sxs-lookup"><span data-stu-id="a7a97-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="a7a97-122">Azure Stack 開發套件</span><span class="sxs-lookup"><span data-stu-id="a7a97-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="a7a97-123">Azure Stack 整合系統</span><span class="sxs-lookup"><span data-stu-id="a7a97-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="a7a97-124">Azure Stack 整合系統是透過 Microsoft 與硬體合作夥伴的合作關係來提供。</span><span class="sxs-lookup"><span data-stu-id="a7a97-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="a7a97-125">合作關係所建立的解決方案可提供雲端進度的創新，並與管理中的簡易性保持平衡。</span><span class="sxs-lookup"><span data-stu-id="a7a97-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="a7a97-126">由於是以硬體與軟體的整合系統形式來提供 Azure Stack，因此除了仍然會採用來自雲端的創新之外，您還有適度的彈性和控制。</span><span class="sxs-lookup"><span data-stu-id="a7a97-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="a7a97-127">Azure Stack 整合式系統的大小範圍從4到12個節點，且由硬體合作夥伴與 Microsoft 共同支援。</span><span class="sxs-lookup"><span data-stu-id="a7a97-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="a7a97-128">使用 Azure Stack 整合系統，為您的生產工作負載執行新案例。</span><span class="sxs-lookup"><span data-stu-id="a7a97-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="a7a97-129">Azure Stack 開發套件</span><span class="sxs-lookup"><span data-stu-id="a7a97-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="a7a97-130">「Microsoft Azure Stack 開發套件」是單一節點的 Azure Stack 部署，您可以用來評估和瞭解 Azure Stack。</span><span class="sxs-lookup"><span data-stu-id="a7a97-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="a7a97-131">您也可以使用 Azure Stack 開發套件作為開發人員環境，您可以在其中使用與 Azure 一致的 Api 和工具進行開發。</span><span class="sxs-lookup"><span data-stu-id="a7a97-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="a7a97-132">「Azure Stack 開發套件」不應該用來作為生產環境。</span><span class="sxs-lookup"><span data-stu-id="a7a97-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a7a97-133">其他資源</span><span class="sxs-lookup"><span data-stu-id="a7a97-133">Additional resources</span></span>

- <span data-ttu-id="a7a97-134">**Azure 混合式雲端**</span><span class="sxs-lookup"><span data-stu-id="a7a97-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="a7a97-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="a7a97-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="a7a97-136">**適用於 Windows 容器的 Active Directory 服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="a7a97-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="a7a97-137">**建立具有 Active Directory 支援的容器**</span><span class="sxs-lookup"><span data-stu-id="a7a97-137">**Create a container with Active Directory support**</span></span>

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- <span data-ttu-id="a7a97-138">**Azure Hybrid Benefit 授權**</span><span class="sxs-lookup"><span data-stu-id="a7a97-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="a7a97-139">[上一個](life-cycle-ci-cd-pipelines-devops-tools.md) 
>[下一步](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="a7a97-139">[Previous](life-cycle-ci-cd-pipelines-devops-tools.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
