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
# <a name="migrate-to-hybrid-cloud-scenarios"></a>移轉至混合式雲端案例

某些組織和企業無法將部分應用程式遷移至公用雲端，例如 Microsoft Azure 或其他任何公用雲端（因為法規或其本身的原則）。 不過，在公用雲端和其他內部部署應用程式中，可能會有任何組織受益。 但是，混合的環境可能會在環境中造成過度複雜的情況，因為公用雲端與內部部署環境中使用不同的平臺和技術。

Microsoft 提供最佳的混合式雲端解決方案，可讓您在內部部署和公用雲端中優化現有的資產，同時確保 Azure 混合式雲端中的一致性。 您可以充分發揮現有技能的最大效用，並取得彈性、統一的方法來建立可在雲端或內部部署中執行的應用程式，因為 Azure Stack (內部部署) 和 Azure (公用雲端) 。

在安全性方面，您可以在混合式雲端集中管理和安全性。 您可以藉由提供對內部部署和雲端應用程式的單一登入，來掌控所有資產，從資料中心到雲端。 您可以藉由將 Active Directory 延伸至混合式雲端，以及使用身分識別管理來完成這項功能。

最後，您可以順暢地散發和分析資料、針對雲端和內部部署資產使用相同的查詢語言，並在 Azure 中套用分析和深度學習，以豐富您的資料，不論其來源為何。

## <a name="azure-stack"></a>Azure Stack

Azure Stack 是混合式雲端平臺，可讓您從組織的資料中心提供 Azure 服務。 Azure Stack 的設計目的是在主要案例（例如 edge 和未連線的環境）中支援新式應用程式的新選項，或符合特定的安全性和合規性需求。

圖4-13 顯示 Microsoft 所提供之真正混合式雲端平臺的總覽。

![Microsoft 混合式雲端平臺與 Azure Stack 和 Azure 的圖表。](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**圖4-13。** 使用 Azure Stack 和 Azure 的 Microsoft 混合式雲端平臺

Azure Stack 提供兩種部署選項，以符合您的需求：

- Azure Stack 整合系統

- Azure Stack 開發套件

### <a name="azure-stack-integrated-systems"></a>Azure Stack 整合系統

Azure Stack 整合系統是透過 Microsoft 與硬體合作夥伴的合作關係來提供。 合作關係所建立的解決方案可提供雲端進度的創新，並與管理中的簡易性保持平衡。 由於是以硬體與軟體的整合系統形式來提供 Azure Stack，因此除了仍然會採用來自雲端的創新之外，您還有適度的彈性和控制。 Azure Stack 整合式系統的大小範圍從4到12個節點，且由硬體合作夥伴與 Microsoft 共同支援。 使用 Azure Stack 整合系統，為您的生產工作負載執行新案例。

### <a name="azure-stack-development-kit"></a>Azure Stack 開發套件

「Microsoft Azure Stack 開發套件」是單一節點的 Azure Stack 部署，您可以用來評估和瞭解 Azure Stack。 您也可以使用 Azure Stack 開發套件作為開發人員環境，您可以在其中使用與 Azure 一致的 Api 和工具進行開發。 「Azure Stack 開發套件」不應該用來作為生產環境。

### <a name="additional-resources"></a>其他資源

- **Azure 混合式雲端**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **適用於 Windows 容器的 Active Directory 服務帳戶**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **建立具有 Active Directory 支援的容器**

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- **Azure Hybrid Benefit 授權**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[上一個](life-cycle-ci-cd-pipelines-devops-tools.md) 
>[下一步](../walkthroughs-technical-get-started-overview.md)
