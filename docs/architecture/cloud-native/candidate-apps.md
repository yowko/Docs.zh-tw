---
title: 適用于雲端原生的候選應用程式
description: 瞭解哪些類型的應用程式可從雲端原生方法獲益
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 3ee13d4c636d08a58a7dcab6883725a55a08ae65
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183522"
---
# <a name="candidate-apps-for-cloud-native"></a>適用于雲端原生的候選應用程式

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

查看您的組合中的應用程式。 有多少人符合雲端原生架構的資格？ 全部都是嗎？ 也許有些嗎？

套用成本/權益分析，很有可能不會支援雲端原生所需的等於沉重 price 標記。 雲端原生的成本遠遠超過應用程式的商業價值。

何種類型的應用程式可能是雲端原生的候選項目？

- 需要不斷演進商務功能/功能的大型策略性企業系統

- 需要高發行速度的應用程式，具有高度信賴度

- 一種系統，其中個別功能必須在不完整重新部署整個系統的情況*下*發行

- 由小組開發的應用程式，具有不同技術堆疊的專業知識

- 具有必須獨立調整之元件的應用程式

那就是舊版系統。 雖然我們想要建立新的應用程式，但我們通常會負責現代化對企業而言非常重要的舊版工作負載。 一段時間後，繼承應用程式可能會分解成微服務、容器化，最後是「replatformed」到雲端原生架構中。  

### <a name="modernizing-legacy-apps"></a>現代化繼承應用程式

免費的 Microsoft 電子書[現代化現有的 .net 應用程式與 Azure 雲端和 Windows 容器](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)，提供將內部部署工作負載遷移至雲端的指引。 圖1-8 顯示現代化繼承應用程式不會有單一大小適用的策略。

![遷移舊版工作負載](./media/strategies-for-migrating-legacy-workloads.png)
的策略**圖 1-8**。 遷移舊版工作負載的策略

非關鍵的整合型應用程式，主要受益于快速隨即轉移（[雲端基礎結構就緒](https://docs.microsoft.com/dotnet/standard/modernize-with-azure-and-containers/lift-and-shift-existing-apps-azure-iaas)）的遷移。 在這裡，內部部署工作負載會重新裝載至雲端式 VM，而不會變更。 此方法使用[IaaS （基礎結構即服務）模型](https://azure.microsoft.com/overview/what-is-iaas/)。 Azure 包含數個工具，例如（[Azure Migrate](https://aka.ms/azuremigrate)、 [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)和[Azure 資料庫移轉服務](https://azure.microsoft.com/campaigns/database-migration/)），讓這類移動變得更容易。 雖然此策略可以節省一些成本，但這類應用程式通常無法解除鎖定並運用雲端運算的優點。 

對企業而言至關重要的整合型應用程式，往往受益于增強的隨即轉移（*雲端優化*）遷移。 此方法包含可啟用重要雲端服務的部署優化，而不需變更應用程式的核心架構。 例如，您可能會[容器化](https://docs.microsoft.com/virtualization/windowscontainers/about/)應用程式，並將它部署到容器協調器（例如[Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/)），這本書稍後會討論到。 一旦進入雲端，應用程式可能會耗用其他雲端服務，例如資料庫、訊息佇列、監視和分散式快取。

最後，執行策略性企業功能的整合型應用程式，對於*雲端原生*方法（本書的主旨）可能會有最大的好處。 這種方法提供了靈活性和速度。 但是，它的代價是遷移、重新架構和重寫程式碼。

如果您和您的小組相信雲端原生方法是適當的，它對您以合理化組織的決策。 雲端原生方法所能解決的商務問題到底是什麼？ 它如何與商務需求一致？

- 功能的快速發行增加了信心嗎？

- 更細緻的擴充性-更有效率地使用資源？

- 改良的系統復原功能？

- 已改善系統效能？

- 有更多的作業可見度嗎？

- Blend 開發平臺和資料存放區，以取得最適合工作的工具嗎？

- 未來證明應用程式的投資？

適當的遷移策略取決於組織優先順序和您的目標系統。 對許多人而言，將整合型應用程式優化，或將粗略服務新增至多層式應用程式，可能會更符合成本效益。 在這些情況下，您仍然可以充分利用雲端 PaaS 功能，例如 Azure App Service 所提供的功能。

## <a name="summary"></a>總結

在本章中，我們引進了雲端原生運算。 我們提供了一種定義，以及驅動雲端原生應用程式的主要功能。 我們探討了可能會證明這項投資和投入的應用程式類型。

隨著背後的介紹，我們現在深入探討雲端原生的詳細探討。

### <a name="references"></a>reference

- [雲端原生運算基礎](https://www.cncf.io/)

- [.NET 微服務：容器化 .NET 應用程式的架構](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [雲端原生模式，依 Cornelia Davis](https://www.manning.com/books/cloud-native-patterns)

- [超越12因素應用程式](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [什麼是基礎結構即程式碼](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [Uber 工程的微部署：放心地每天部署](https://eng.uber.com/micro-deploy/)

- [Netflix 如何部署程式碼](https://www.infoq.com/news/2013/06/netflix/)

- [調整 WeChat 微服務的多載控制](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

- [RayGun-案例研究](https://raygun.com/case-study/ovation)

>[!div class="step-by-step"]
>[上一頁](definition.md)
>[下一頁](introduce-eshoponcontainers-reference-app.md) <!-- Next Chapter -->
