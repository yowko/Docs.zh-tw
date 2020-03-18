---
title: 移轉至混合式雲端案例
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |遷移到混合雲方案
ms.date: 04/30/2018
ms.openlocfilehash: dcbb799a45609f8bb811866c4041951abf1fda8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937368"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="9434f-103">移轉至混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="9434f-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="9434f-104">由於法規或他們自己的策略，某些組織和企業無法將其某些應用程式遷移到公共雲（如 Microsoft Azure 或任何其他公共雲）。</span><span class="sxs-lookup"><span data-stu-id="9434f-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="9434f-105">但是，任何組織都有可能從在公共雲和其他本地應用程式中部署某些應用程式中獲益。</span><span class="sxs-lookup"><span data-stu-id="9434f-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="9434f-106">但是，由於公共雲中使用的平臺和技術與本地環境不同，混合環境可能會導致環境中過於複雜。</span><span class="sxs-lookup"><span data-stu-id="9434f-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="9434f-107">Microsoft 提供了最佳的混合雲解決方案，您可以在其中優化本地和公共雲中的現有資產，同時確保 Azure 混合雲的一致性。</span><span class="sxs-lookup"><span data-stu-id="9434f-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="9434f-108">您可以最大化現有技能，並獲得一種靈活、統一的方法來構建可在雲或本地運行的應用，這要歸功於 Azure 堆疊（本地）和 Azure（公共雲）。</span><span class="sxs-lookup"><span data-stu-id="9434f-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="9434f-109">在安全性方面，您可以將管理和安全性集中到混合雲中。</span><span class="sxs-lookup"><span data-stu-id="9434f-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="9434f-110">通過提供本地和雲應用的單一登入，您可以控制從資料中心到雲的所有資產。</span><span class="sxs-lookup"><span data-stu-id="9434f-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="9434f-111">通過將 Active Directory 擴展到混合雲並使用標識管理來實現此目的。</span><span class="sxs-lookup"><span data-stu-id="9434f-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="9434f-112">最後，您可以無縫分發和分析資料，對雲和本地資產使用相同的查詢語言，並在 Azure 中應用分析和深度學習來豐富資料，而不管資料的來源如何。</span><span class="sxs-lookup"><span data-stu-id="9434f-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="9434f-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="9434f-113">Azure Stack</span></span>

<span data-ttu-id="9434f-114">Azure 堆疊是一個混合雲平臺，允許您從組織的資料中心提供 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="9434f-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="9434f-115">Azure Stack 旨在支援關鍵方案中的現代應用程式的新選項，如邊緣和未連接的環境，或滿足特定的安全性和合規性要求。</span><span class="sxs-lookup"><span data-stu-id="9434f-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="9434f-116">圖 4-13 顯示了 Microsoft 提供的真實混合雲平臺的概述。</span><span class="sxs-lookup"><span data-stu-id="9434f-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![具有 Azure 堆疊和 Azure 的 Microsoft 混合雲平臺圖。](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

<span data-ttu-id="9434f-118">**圖 4-13。**</span><span class="sxs-lookup"><span data-stu-id="9434f-118">**Figure 4-13.**</span></span> <span data-ttu-id="9434f-119">微軟混合雲平臺與 Azure 堆疊和 Azure</span><span class="sxs-lookup"><span data-stu-id="9434f-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="9434f-120">Azure 堆疊提供兩種部署選項，以滿足您的需求：</span><span class="sxs-lookup"><span data-stu-id="9434f-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="9434f-121">Azure Stack 整合系統</span><span class="sxs-lookup"><span data-stu-id="9434f-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="9434f-122">Azure Stack 開發套件</span><span class="sxs-lookup"><span data-stu-id="9434f-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="9434f-123">Azure Stack 整合系統</span><span class="sxs-lookup"><span data-stu-id="9434f-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="9434f-124">Azure 堆疊集成系統通過 Microsoft 和硬體合作夥伴的合作夥伴關係提供。</span><span class="sxs-lookup"><span data-stu-id="9434f-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="9434f-125">該合作夥伴關係創造了一種解決方案，提供雲節奏創新，在管理上實現簡單性。</span><span class="sxs-lookup"><span data-stu-id="9434f-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="9434f-126">由於是以硬體與軟體的整合系統形式來提供 Azure Stack，因此除了仍然會採用來自雲端的創新之外，您還有適度的彈性和控制。</span><span class="sxs-lookup"><span data-stu-id="9434f-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="9434f-127">Azure Stack 集成系統的大小範圍從 4 到 12 個節點，並且由硬體合作夥伴和 Microsoft 共同支援。</span><span class="sxs-lookup"><span data-stu-id="9434f-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="9434f-128">使用 Azure 堆疊集成系統為生產工作負荷實施新方案。</span><span class="sxs-lookup"><span data-stu-id="9434f-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="9434f-129">Azure Stack 開發套件</span><span class="sxs-lookup"><span data-stu-id="9434f-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="9434f-130">「Microsoft Azure Stack 開發套件」是單一節點的 Azure Stack 部署，您可以用來評估和瞭解 Azure Stack。</span><span class="sxs-lookup"><span data-stu-id="9434f-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="9434f-131">還可以將 Azure 堆疊開發工具組用作開發人員環境，您可以在其中使用與 Azure 一致的 API 和工具進行開發。</span><span class="sxs-lookup"><span data-stu-id="9434f-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="9434f-132">「Azure Stack 開發套件」不應該用來作為生產環境。</span><span class="sxs-lookup"><span data-stu-id="9434f-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9434f-133">其他資源</span><span class="sxs-lookup"><span data-stu-id="9434f-133">Additional resources</span></span>

- <span data-ttu-id="9434f-134">**Azure 混合雲**</span><span class="sxs-lookup"><span data-stu-id="9434f-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="9434f-135">**Azure 堆疊**</span><span class="sxs-lookup"><span data-stu-id="9434f-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="9434f-136">**適用於 Windows 容器的 Active Directory 服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="9434f-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="9434f-137">**創建支援活動目錄的容器**</span><span class="sxs-lookup"><span data-stu-id="9434f-137">**Create a container with Active Directory support**</span></span>

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- <span data-ttu-id="9434f-138">**Azure 混合權益許可**</span><span class="sxs-lookup"><span data-stu-id="9434f-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="9434f-139">[上一個](life-cycle-ci-cd-pipelines-devops-tools.md)
>[下一個](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="9434f-139">[Previous](life-cycle-ci-cd-pipelines-devops-tools.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
