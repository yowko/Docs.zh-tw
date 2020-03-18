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
# <a name="migrate-to-hybrid-cloud-scenarios"></a>移轉至混合式雲端案例

由於法規或他們自己的策略，某些組織和企業無法將其某些應用程式遷移到公共雲（如 Microsoft Azure 或任何其他公共雲）。 但是，任何組織都有可能從在公共雲和其他本地應用程式中部署某些應用程式中獲益。 但是，由於公共雲中使用的平臺和技術與本地環境不同，混合環境可能會導致環境中過於複雜。

Microsoft 提供了最佳的混合雲解決方案，您可以在其中優化本地和公共雲中的現有資產，同時確保 Azure 混合雲的一致性。 您可以最大化現有技能，並獲得一種靈活、統一的方法來構建可在雲或本地運行的應用，這要歸功於 Azure 堆疊（本地）和 Azure（公共雲）。

在安全性方面，您可以將管理和安全性集中到混合雲中。 通過提供本地和雲應用的單一登入，您可以控制從資料中心到雲的所有資產。 通過將 Active Directory 擴展到混合雲並使用標識管理來實現此目的。

最後，您可以無縫分發和分析資料，對雲和本地資產使用相同的查詢語言，並在 Azure 中應用分析和深度學習來豐富資料，而不管資料的來源如何。

## <a name="azure-stack"></a>Azure Stack

Azure 堆疊是一個混合雲平臺，允許您從組織的資料中心提供 Azure 服務。 Azure Stack 旨在支援關鍵方案中的現代應用程式的新選項，如邊緣和未連接的環境，或滿足特定的安全性和合規性要求。

圖 4-13 顯示了 Microsoft 提供的真實混合雲平臺的概述。

![具有 Azure 堆疊和 Azure 的 Microsoft 混合雲平臺圖。](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**圖 4-13。** 微軟混合雲平臺與 Azure 堆疊和 Azure

Azure 堆疊提供兩種部署選項，以滿足您的需求：

- Azure Stack 整合系統

- Azure Stack 開發套件

### <a name="azure-stack-integrated-systems"></a>Azure Stack 整合系統

Azure 堆疊集成系統通過 Microsoft 和硬體合作夥伴的合作夥伴關係提供。 該合作夥伴關係創造了一種解決方案，提供雲節奏創新，在管理上實現簡單性。 由於是以硬體與軟體的整合系統形式來提供 Azure Stack，因此除了仍然會採用來自雲端的創新之外，您還有適度的彈性和控制。 Azure Stack 集成系統的大小範圍從 4 到 12 個節點，並且由硬體合作夥伴和 Microsoft 共同支援。 使用 Azure 堆疊集成系統為生產工作負荷實施新方案。

### <a name="azure-stack-development-kit"></a>Azure Stack 開發套件

「Microsoft Azure Stack 開發套件」是單一節點的 Azure Stack 部署，您可以用來評估和瞭解 Azure Stack。 還可以將 Azure 堆疊開發工具組用作開發人員環境，您可以在其中使用與 Azure 一致的 API 和工具進行開發。 「Azure Stack 開發套件」不應該用來作為生產環境。

### <a name="additional-resources"></a>其他資源

- **Azure 混合雲**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure 堆疊**

    <https://azure.microsoft.com/overview/azure-stack/>

- **適用於 Windows 容器的 Active Directory 服務帳戶**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **創建支援活動目錄的容器**

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- **Azure 混合權益許可**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[上一個](life-cycle-ci-cd-pipelines-devops-tools.md)
>[下一個](../walkthroughs-technical-get-started-overview.md)
