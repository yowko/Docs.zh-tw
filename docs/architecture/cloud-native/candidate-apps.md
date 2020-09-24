---
title: 適用于雲端原生的候選應用程式
description: 瞭解哪些類型的應用程式受益于雲端原生方法
author: robvet
ms.date: 05/14/2020
ms.openlocfilehash: 8f00633a575dad12b0bc1d5adb83acac03db0659
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160940"
---
# <a name="candidate-apps-for-cloud-native"></a>適用于雲端原生的候選應用程式

查看您組合中的應用程式。 有多少人符合雲端原生架構？ 全部？ 或許有部分？

套用成本/效益分析，有很多人很可能不支援雲端原生所需的等於沉重價格標記。 雲端原生的成本遠超過應用程式的商業價值。

哪種類型的應用程式可能是雲端原生的候選項目？

- 需要不斷演進商務功能/功能的策略性企業系統

- 需要高發行速度的應用程式-具有高信賴度

- 個別功能必須在 *不需* 完全重新部署整個系統的情況下發行的系統

- 小組開發的應用程式，具有不同技術堆疊的專業知識

- 具有必須獨立調整之元件的應用程式

然後有舊版系統。 雖然我們都是要建立新的應用程式，但我們通常負責現代化對企業至關重要的舊版工作負載。 經過一段時間後，繼承應用程式可能會分解成微服務、容器化，最後「replatformed」到雲端原生架構。

### <a name="modernizing-legacy-apps"></a>現代化繼承應用程式

[使用 Azure 雲端和 Windows 容器將現有 .net 應用程式現代化](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)的免費 Microsoft 電子書，提供將內部部署工作負載遷移至雲端的指引。 圖1-10 顯示現代化繼承應用程式沒有單一大小適用的唯一策略。

![遷移舊版工作負載的策略](./media/strategies-for-migrating-legacy-workloads.png)

**圖 1-10**。 遷移舊版工作負載的策略

非關鍵的整合型應用程式，主要是從快速入門 ([雲端基礎結構就緒](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) 遷移中獲益。 在這裡，內部部署工作負載會重新裝載至雲端式 VM，而不需要變更。 這種方法會使用 [IaaS (基礎結構即服務) 模型](https://azure.microsoft.com/overview/what-is-iaas/)。 Azure 包含數個工具，例如 [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/)、 [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)和 [Azure 資料庫移轉服務](https://azure.microsoft.com/campaigns/database-migration/) ，可讓您更輕鬆地進行這類移動。 雖然此策略可以節省一些成本，但這類應用程式通常不會將其設計為可解除鎖定並利用雲端運算的優點。

對企業而言很重要的整合型應用程式，通常會受益于改良的隨即轉移 (*雲端優化*) 的遷移。 這種方法包含可啟用主要雲端服務的部署優化，而不需要變更應用程式的核心架構。 例如，您可能會 [將](/virtualization/windowscontainers/about/) 應用程式，並將它部署到容器協調器，例如本書籍稍後討論的 [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/)。 在雲端中，應用程式可能會使用其他雲端服務，例如資料庫、訊息佇列、監視和分散式快取。

最後，執行策略性企業功能的整合型應用程式，可能會因為 *雲端原生* 方法（本書的主旨）而獲得最大的好處。 這種方法可提供靈活性和速度。 但是，它有遷移、重新架構和重寫程式碼的成本。

如果您和您的小組認為適當的雲端原生方法，它會對您，以合理化組織的決策。 雲端原生方法可解決的商務問題到底是什麼？ 它會如何與商務需求一致？

- 增強了功能的快速發行功能，並提高信心？

- 更精細的擴充性更有效率地使用資源？

- 改進的系統復原能力？

- 改善的系統效能？

- 更深入瞭解作業？

- Blend 開發平臺和資料存放區，以達到工作的最佳工具嗎？

- 未來考驗的應用程式投資？

適當的遷移策略取決於組織優先順序和您的目標系統。 對許多人而言，雲端優化整合型應用程式，或將粗略的服務新增至多層式應用程式，可能會更符合成本效益。 在這些情況下，您仍然可以充分利用雲端 PaaS 功能，例如 Azure App Service 所提供的功能。

## <a name="summary"></a>摘要

在本章中，我們引進了雲端原生計算。 我們提供了一種定義，以及驅動雲端原生應用程式的主要功能。 我們探討了可能證明這項投資和努力的應用程式類型。

在簡介之後，我們現在深入探討雲端原生的詳細資訊。

### <a name="references"></a>參考資料

- [雲端原生運算基礎](https://www.cncf.io/)

- [.NET 微服務：容器化 .NET 應用程式的架構](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [雲端原生模式（依 Cornelia Davis）](https://www.manning.com/books/cloud-native-patterns)

- [超越十二要素應用程式](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [什麼是基礎結構即程式碼](/azure/devops/learn/what-is-infrastructure-as-code)

- [Uber 工程的微部署：每日放心部署](https://eng.uber.com/micro-deploy/)

- [Netflix 如何部署程式碼](https://www.infoq.com/news/2013/06/netflix/)

- [調整 WeChat 微服務的多載控制項](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[上一個](definition.md) 
>[下一步](introduce-eshoponcontainers-reference-app.md)
