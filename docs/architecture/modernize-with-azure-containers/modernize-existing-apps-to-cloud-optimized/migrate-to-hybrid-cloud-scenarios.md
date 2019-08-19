---
title: 移轉至混合式雲端案例
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |遷移至混合式雲端案例
ms.date: 04/30/2018
ms.openlocfilehash: 04c618681c61f5584e641e0a4735e1261ab34fa3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578211"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>移轉至混合式雲端案例

有些組織和企業無法將部分應用程式遷移至公用雲端, 例如 Microsoft Azure 或任何其他公用雲端 (因為法規或其本身的原則)。 不過, 在公用雲端和其他內部部署應用程式中, 可能會有任何組織受益于其部分應用程式。 但混合式環境可能會因為公用雲端與內部部署環境中使用的不同平臺和技術, 而導致環境過度複雜。

Microsoft 提供最佳的混合式雲端解決方案, 其中您可以在內部部署和公用雲端中優化現有的資產, 同時確保 Azure 混合式雲端的一致性。 由於 Azure Stack (內部部署) 和 Azure (公用雲端), 您可以最大化現有的技能, 並取得彈性且一致的方式來建立可在雲端或內部部署中執行的應用程式。

在安全性方面, 您可以在混合式雲端集中管理和安全性。 您可以藉由提供對內部部署和雲端應用程式的單一登入, 從您的資料中心將所有資產控制到雲端。 您可以將 Active Directory 擴充至混合式雲端, 並使用身分識別管理來完成這項工作。

最後, 您可以順暢地散發和分析資料、針對雲端和內部部署資產使用相同的查詢語言, 以及在 Azure 中套用分析和深度學習, 以豐富您的資料 (不論其來源為何)。

## <a name="azure-stack"></a>Azure Stack

Azure Stack 是混合式雲端平臺, 可讓您從組織的資料中心提供 Azure 服務。 Azure Stack 的設計, 是為了在主要案例 (例如 edge 和未連線的環境) 中支援現代化應用程式的新選項, 或符合特定的安全性和合規性需求。

圖4-13 顯示 Microsoft 提供的真正混合式雲端平臺的總覽。

![使用 Azure Stack 和 Azure 的 Microsoft 混合式雲端平臺](./media/image13.jpg)

> **圖4-13。** 使用 Azure Stack 和 Azure 的 Microsoft 混合式雲端平臺

有兩個部署選項提供 Azure Stack, 以符合您的需求:

- Azure Stack 整合式系統

- Azure Stack 開發套件

### <a name="azure-stack-integrated-systems"></a>Azure Stack 整合式系統

Azure Stack 整合系統是透過 Microsoft 與硬體合作夥伴的合作關係來提供。 合作關係所建立的解決方案提供了雲端進度的創新, 並與管理中的簡單性達成平衡。 因為 Azure Stack 會當做硬體和軟體的整合系統提供, 所以您可以取得適當的彈性和控制量, 同時仍採用雲端的創新。 Azure Stack 整合系統的大小範圍是4到12個節點, 且硬體合作夥伴和 Microsoft 共同支援。 使用 Azure Stack 整合式系統, 為您的生產環境工作負載實行新的案例。

### <a name="azure-stack-development-kit"></a>Azure Stack 開發套件

Microsoft Azure Stack 開發工具組是 Azure Stack 的單一節點部署, 您可以用來評估和瞭解 Azure Stack。 您也可以使用 Azure Stack 開發套件做為開發人員環境, 您可以在其中使用與 Azure 一致的 Api 和工具進行開發。 Azure Stack 開發套件不適合作為生產環境使用。

### <a name="additional-resources"></a>其他資源

- **Azure 混合式雲端**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Active Directory Windows 容器的服務帳戶**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **建立具有 Active Directory 支援的容器**

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- **Azure Hybrid Benefit 授權**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[上一頁](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[下一頁](../walkthroughs-technical-get-started-overview.md)
