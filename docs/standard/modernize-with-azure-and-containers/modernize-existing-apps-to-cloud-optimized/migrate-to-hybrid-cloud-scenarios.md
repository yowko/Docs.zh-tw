---
title: 移轉至混合式雲端案例
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |移轉至混合式雲端案例
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 3d6fc272854654d890559d5db032b05667627d94
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147329"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="75389-103">移轉至混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="75389-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="75389-104">某些組織和企業無法移轉部分到 Microsoft Azure 這類公用雲端應用程式或其他任何公用雲端，因為法規或自己的原則。</span><span class="sxs-lookup"><span data-stu-id="75389-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="75389-105">不過，很可能在任何組織，可能會從具有某些在公用雲端和其他應用程式在內部部署應用程式受益。</span><span class="sxs-lookup"><span data-stu-id="75389-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="75389-106">但是，混合式的環境可能會導致過多複雜性，因為不同的平台和技術在公用雲端與內部部署環境中使用的環境中。</span><span class="sxs-lookup"><span data-stu-id="75389-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="75389-107">Microsoft 會提供最佳的混合式雲端解決方案，在其中您可以充分運用現有資產的其中一個內部部署和公用雲端，同時確保可在 Azure 的混合式雲端中的一致性。</span><span class="sxs-lookup"><span data-stu-id="75389-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="75389-108">您可以將現有的技能，最大化，並取得彈性且統一的方式，建置可以在雲端或內部部署，多虧了 Azure Stack （內部） 與 Azure （公用雲端） 中執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="75389-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="75389-109">當談到安全性時，則您可以集中管理和安全性，跨混合式雲端。</span><span class="sxs-lookup"><span data-stu-id="75389-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="75389-110">您可以取得控制所有資產，從您的資料中心到雲端，提供單一登入內部部署和雲端應用程式。</span><span class="sxs-lookup"><span data-stu-id="75389-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="75389-111">藉由將 Active Directory 延伸至混合式雲端，以及使用身分識別管理，您可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="75389-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="75389-112">最後，您可以散發和順暢地分析資料、 雲端和內部部署資產使用相同的查詢語言以及套用分析及深度學習來豐富您的資料，不論其來源為何 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="75389-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="75389-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="75389-113">Azure Stack</span></span>

<span data-ttu-id="75389-114">Azure Stack 是混合式雲端平台，可讓您從貴組織的資料中心提供 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="75389-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="75389-115">Azure Stack 被設計來支援您在索引鍵的情況下，例如邊緣和未連線的環境中或符合特定的安全性與合規性需求的現代應用程式的新選項。</span><span class="sxs-lookup"><span data-stu-id="75389-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="75389-116">圖 4-13 顯示 Microsoft 提供了真正的混合式雲端平台的概觀。</span><span class="sxs-lookup"><span data-stu-id="75389-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![使用 Azure Stack 和 Azure 的 Microsoft 混合式雲端平台](./media/image13.jpg)

> <span data-ttu-id="75389-118">**圖 4-13。**</span><span class="sxs-lookup"><span data-stu-id="75389-118">**Figure 4-13.**</span></span> <span data-ttu-id="75389-119">使用 Azure Stack 和 Azure 的 Microsoft 混合式雲端平台</span><span class="sxs-lookup"><span data-stu-id="75389-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="75389-120">Azure Stack 提供以下兩種部署選項，以符合您需求：</span><span class="sxs-lookup"><span data-stu-id="75389-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

-   <span data-ttu-id="75389-121">Azure Stack 整合系統</span><span class="sxs-lookup"><span data-stu-id="75389-121">Azure Stack integrated systems</span></span>

-   <span data-ttu-id="75389-122">Azure Stack 開發套件</span><span class="sxs-lookup"><span data-stu-id="75389-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="75389-123">Azure Stack 整合系統</span><span class="sxs-lookup"><span data-stu-id="75389-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="75389-124">Azure Stack 整合系統提供的 Microsoft 和硬體合作夥伴的合作關係。</span><span class="sxs-lookup"><span data-stu-id="75389-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="75389-125">此合作關係會建立提供管理簡易性平衡雲端步調的創新的解決方案。</span><span class="sxs-lookup"><span data-stu-id="75389-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="75389-126">提供 Azure Stack 整合系統的硬體和軟體，因為您會取得適度的彈性和控制，同時仍然會採用來自雲端的創新。</span><span class="sxs-lookup"><span data-stu-id="75389-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="75389-127">Azure Stack 整合系統的大小範圍從 4 到 12 的節點，並且由硬體合作夥伴與 Microsoft 共同支援。</span><span class="sxs-lookup"><span data-stu-id="75389-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="75389-128">您可以使用 Azure Stack 整合系統來實作新的案例，為您的生產工作負載。</span><span class="sxs-lookup"><span data-stu-id="75389-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="75389-129">Azure Stack 開發套件</span><span class="sxs-lookup"><span data-stu-id="75389-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="75389-130">Microsoft Azure Stack 開發套件是 Azure Stack，您可以使用來評估和了解 Azure Stack 的單一節點部署。</span><span class="sxs-lookup"><span data-stu-id="75389-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="75389-131">您也可以使用 Azure Stack 開發套件作為開發人員環境，其中您可以使用 Api 進行開發和工具，而且與 Azure 一致。</span><span class="sxs-lookup"><span data-stu-id="75389-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="75389-132">Azure Stack 開發套件不適用於生產環境。</span><span class="sxs-lookup"><span data-stu-id="75389-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="75389-133">其他資源</span><span class="sxs-lookup"><span data-stu-id="75389-133">Additional resources</span></span>

-   <span data-ttu-id="75389-134">**Azure 的混合式雲端**</span><span class="sxs-lookup"><span data-stu-id="75389-134">**Azure hybrid cloud**</span></span>

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   <span data-ttu-id="75389-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="75389-135">**Azure Stack**</span></span>

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   <span data-ttu-id="75389-136">**適用於 Windows 容器的 active Directory 服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="75389-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   <span data-ttu-id="75389-137">**使用 Active Directory 支援來建立容器**</span><span class="sxs-lookup"><span data-stu-id="75389-137">**Create a container with Active Directory support**</span></span>

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   <span data-ttu-id="75389-138">**Azure Hybrid Benefit 授權**</span><span class="sxs-lookup"><span data-stu-id="75389-138">**Azure Hybrid Benefit licensing**</span></span>

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
><span data-ttu-id="75389-139">[上一頁](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[下一頁](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="75389-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>