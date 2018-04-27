---
title: 移轉至混合式雲端案例
description: 容器化的.NET 應用程式的.NET Microservices 架構 |移轉至混合式雲端案例
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/2/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a2fc5a2118736d3491a5a0731e47c697edd674f1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>移轉至混合式雲端案例

有些組織和企業無法移轉應用程式，以如 Microsoft Azure 公用雲端，或是其他任何公用雲端，因為法規或自己的原則。 不過，很可能在任何組織可能會受益需要某些公用雲端和其他應用程式在內部部署其應用程式。 但在混合的環境可能會造成過多的複雜性，因為不同平台和公用雲端與內部部署環境中所用技術的環境中。

Microsoft 提供最佳的混合式雲端解決方案，其中一個可以最佳化現有的資產內部和公用雲端，同時確保可在 Azure 的混合式雲端中的一致性。 您可以將現有的技術，最大化，並取得建置雲端或內部部署，這點受惠 Azure 堆疊 （內部） 和 Azure （公用雲端） 中執行的應用程式彈性、 統一的方式。

當安全性方面時，您可以混合式雲端間集中管理和安全性。 您可以從您的資料中心到雲端，取得所有資產，控制權，藉由提供單一登入至內部和雲端應用程式。 您完成這項作業將 Active Directory 延伸到混合式雲端，並使用身分識別管理。

最後，您可以發佈和順暢地分析資料，請使用相同的查詢語言的雲端和內部部署資產，並套用分析和深入了解 Azure 來充實資料，不論其來源中。

## <a name="azure-stack"></a>Azure 的堆疊

Azure 堆疊是混合式雲端平台，可讓您提供 Azure 服務，從您組織的資料中心。 Azure 堆疊被設計來支援您在索引鍵的情況下，例如邊緣和未連接的環境中或符合特定的安全性與相容性需求的現代應用程式的新選項。

圖 4-13 顯示，則為 true 的混合式雲端平台 Microsoft 所提供的概觀。

![Microsoft Azure 堆疊與 Azure 混合式雲端平台](./media/image13.jpg)

> **圖 4-13。** Microsoft Azure 堆疊與 Azure 混合式雲端平台

Azure 堆疊提供兩種部署選項，以符合您需求：

-   Azure 整合堆疊系統

-   Azure 堆疊開發套件

### <a name="azure-stack-integrated-systems"></a>Azure 整合堆疊系統

透過 Microsoft 和硬體合作夥伴的合作關係提供 azure 堆疊整合系統。 合作關係建立的方案提供平衡為了簡單起見，在管理雲端操作創新。 Azure 堆疊只提供作為整合的系統的硬體和軟體，因為您會取得適合容量的彈性和控制，同時仍採用創新從雲端。 Azure 整合堆疊系統大小介於 4 到 12 的節點，並共同支援硬體合作夥伴和 Microsoft。 使用 Azure 堆疊整合系統，以實作您的生產工作負載的新案例。

### <a name="azure-stack-development-kit"></a>Azure 堆疊開發套件

Microsoft Azure 堆疊開發套件是單一節點部署 Azure 堆疊，您可以使用來評估，並了解 Azure 堆疊。 您也可以使用 Azure 堆疊開發套件做為開發人員環境，其中您可以使用 Api 來開發及工具，會與 Azure 一致。 Azure 堆疊開發套件不是要做為實際執行環境。

### <a name="additional-resources"></a>其他資源

-   **Azure 的混合式雲端**

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   **Azure Stack**

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   **Windows 容器的 active Directory 服務帳戶**

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   **使用 Active Directory 支援建立容器**

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   **Azure 的混合式權益授權**

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
[上一頁](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[下一頁](../walkthroughs-technical-get-started-overview.md)
