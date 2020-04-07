---
title: 雲本機的候選應用
description: 瞭解哪些類型的應用程式受益於雲原生方法
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 8e58f5bd3aa0a4503ea73ab454e42e863eb0bb5d
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805621"
---
# <a name="candidate-apps-for-cloud-native"></a>雲本機的候選應用

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

查看產品群組中的應用程式。 其中有多少人有資格獲得雲原生架構? 全部？ 也許有些?

應用成本/收益分析,大多數人很可能不支援雲原生所需的高昂價格標籤。 雲原生成本將遠遠超過應用程式的業務價值。

哪種應用程式可能是雲本機的候選類型?

- 需要不斷發展業務能力/功能的大型戰略企業系統

- 需要高釋放速度的應用程式 - 高度置信度

- 具有單一功能且無需完全重新部署整個系統*即可發布的系統*

- 由具有不同技術堆疊專業知識的團隊開發的應用程式

- 具有必須獨立擴充的元件的應用程式

然後是遺留系統。 雖然我們都希望構建新的應用程式,但我們通常負責實現對業務至關重要的遺留工作負載的現代化。 隨著時間的推移,舊應用程式可以分解為微服務,容器化,並最終"重新平臺"到雲本機體系結構。

### <a name="modernizing-legacy-apps"></a>現代化傳統應用

免費的 Microsoft 電子書[使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化改造](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook),為將本地工作負載遷移到雲提供了指南。 圖 1-10 顯示了沒有一種單一、一刀切的策略來實現舊應用程式的現代化。

![遷移舊工作負載的策略](./media/strategies-for-migrating-legacy-workloads.png)

**圖 1-10**. 遷移舊工作負載的策略

非關鍵應用主要受益於快速提升和移動 ([雲端基礎架構就緒](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) 遷移。 在這裡,本地工作負載將重新託管到基於雲的 VM,無需更改。 此方法使用[IaaS(基礎設施即服務)模型](https://azure.microsoft.com/overview/what-is-iaas/)。 Azure 包括多個工具,如[Azure 遷移](https://azure.microsoft.com/services/azure-migrate/)[、Azure 網站恢復](https://azure.microsoft.com/services/site-recovery/)和[Azure 資料庫遷移服務](https://azure.microsoft.com/campaigns/database-migration/),以便更輕鬆地移動。 雖然這種策略可以節省一些成本,但此類應用程式通常不是為解鎖和利用雲端運算的優勢而構建的。

對業務至關重要的單一應用通常受益於增強的提升和移位(*雲優化*) 遷移。 此方法包括啟用關鍵雲服務的部署優化, 而無需更改應用程式的核心體系結構。 例如,您可以將應用程式[容器化](https://docs.microsoft.com/virtualization/windowscontainers/about/),並將其部署到容器協調器,如本書後面討論的[Azure Kubernetes 服務](https://azure.microsoft.com/services/kubernetes-service/)。 進入雲后,應用程式可能會使用其他雲服務,如資料庫、消息佇列、監視和分散式緩存。

最後,執行戰略企業功能的單一應用可能最好受益於*雲原生*方法,這是本書的主題。 此方法提供敏捷性和速度。 但是,它的代價是重新平臺、重新構建和重寫代碼。

如果您和您的團隊認為雲原生方法是適當的,則您應該與組織一起使決策合理化。 雲原生方法將解決的業務問題究竟是什麼? 它如何與業務需求保持一致?

- 快速發佈功能,增強信心?

- 細粒度可擴充性 - 更有效地使用資源?

- 提高系統彈性?

- 提高系統性能?

- 對操作的更多可見性?

- 混合開發平臺和數據存儲,以找到最適合作業的工具?

- 面向未來的應用投資?

正確的遷移策略取決於組織優先順序和您所針對的系統。 對許多人來說,雲優化單片應用程式或向 N-Tier 應用添加粗粒度服務可能更具成本效益。 在這些情況下,您仍然可以充分利用雲 PaaS 功能,如 Azure 應用服務提供的功能。

## <a name="summary"></a>摘要

在本章中,我們介紹了雲原生計算。 我們提供了一個定義以及驅動雲本機應用程式的關鍵功能。 我們研究了可能證明這種投資和努力合理的應用程序類型。

在介紹之後,我們現在將深入探討雲原生。

### <a name="references"></a>參考

- [雲原生計算基金會](https://www.cncf.io/)

- [.NET 微服務:容器化 .NET 應用程式的體系結構](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [科妮莉亞·大衛斯的雲原生模式](https://www.manning.com/books/cloud-native-patterns)

- [超越十二因素應用](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [什麼是基礎架構作為代碼](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [優步工程的微觀部署:自信地每天部署](https://eng.uber.com/micro-deploy/)

- [Netflix 如何部署程式碼](https://www.infoq.com/news/2013/06/netflix/)

- [用於擴展微信微服務的過載控制](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[前一個](definition.md)
>[下一個](introduce-eshoponcontainers-reference-app.md)
