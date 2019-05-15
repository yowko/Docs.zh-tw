---
title: 移轉至混合式雲端案例
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |移轉至混合式雲端案例
ms.date: 04/30/2018
ms.openlocfilehash: 04c618681c61f5584e641e0a4735e1261ab34fa3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643724"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>移轉至混合式雲端案例

某些組織和企業無法移轉部分到 Microsoft Azure 這類公用雲端應用程式或其他任何公用雲端，因為法規或自己的原則。 不過，很可能在任何組織，可能會從具有某些在公用雲端和其他應用程式在內部部署應用程式受益。 但是，混合式的環境可能會導致過多複雜性，因為不同的平台和技術在公用雲端與內部部署環境中使用的環境中。

Microsoft 會提供最佳的混合式雲端解決方案，在其中您可以充分運用現有資產的其中一個內部部署和公用雲端，同時確保可在 Azure 的混合式雲端中的一致性。 您可以將現有的技能，最大化，並取得彈性且統一的方式，建置可以在雲端或內部部署，多虧了 Azure Stack （內部） 與 Azure （公用雲端） 中執行的應用程式。

當談到安全性時，則您可以集中管理和安全性，跨混合式雲端。 您可以取得控制所有資產，從您的資料中心到雲端，提供單一登入內部部署和雲端應用程式。 藉由將 Active Directory 延伸至混合式雲端，以及使用身分識別管理，您可以這麼做。

最後，您可以散發和順暢地分析資料、 雲端和內部部署資產使用相同的查詢語言以及套用分析及深度學習來豐富您的資料，不論其來源為何 Azure 中。

## <a name="azure-stack"></a>Azure Stack

Azure Stack 是混合式雲端平台，可讓您從貴組織的資料中心提供 Azure 服務。 Azure Stack 被設計來支援您在索引鍵的情況下，例如邊緣和未連線的環境中或符合特定的安全性與合規性需求的現代應用程式的新選項。

圖 4-13 顯示 Microsoft 提供了真正的混合式雲端平台的概觀。

![使用 Azure Stack 和 Azure 的 Microsoft 混合式雲端平台](./media/image13.jpg)

> **圖 4-13。** 使用 Azure Stack 和 Azure 的 Microsoft 混合式雲端平台

Azure Stack 提供以下兩種部署選項，以符合您需求：

- Azure Stack 整合系統

- Azure Stack 開發套件

### <a name="azure-stack-integrated-systems"></a>Azure Stack 整合系統

Azure Stack 整合系統提供的 Microsoft 和硬體合作夥伴的合作關係。 此合作關係會建立提供管理簡易性平衡雲端步調的創新的解決方案。 提供 Azure Stack 整合系統的硬體和軟體，因為您會取得適度的彈性和控制，同時仍然會採用來自雲端的創新。 Azure Stack 整合系統的大小範圍從 4 到 12 的節點，並且由硬體合作夥伴與 Microsoft 共同支援。 您可以使用 Azure Stack 整合系統來實作新的案例，為您的生產工作負載。

### <a name="azure-stack-development-kit"></a>Azure Stack 開發套件

Microsoft Azure Stack 開發套件是 Azure Stack，您可以使用來評估和了解 Azure Stack 的單一節點部署。 您也可以使用 Azure Stack 開發套件作為開發人員環境，其中您可以使用 Api 進行開發和工具，而且與 Azure 一致。 Azure Stack 開發套件不適用於生產環境。

### <a name="additional-resources"></a>其他資源

- **Azure 的混合式雲端**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **適用於 Windows 容器的 active Directory 服務帳戶**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **使用 Active Directory 支援來建立容器**

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- **Azure Hybrid Benefit 授權**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[上一頁](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[下一頁](../walkthroughs-technical-get-started-overview.md)
