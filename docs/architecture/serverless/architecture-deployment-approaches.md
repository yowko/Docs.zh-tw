---
title: 架構部署方法 - 無伺服器應用
description: 企業體系結構部署到雲的不同方式的指南，比較 IaaS、PaaS、容器和無伺服器。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c745a4eb1c6f4a00bf139100b02f31cf3327d01e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522723"
---
# <a name="architecture-deployment-approaches"></a>架構部署方法

無論用於設計商務應用程式的體系結構方法如何，這些應用程式的實現或部署可能會有所不同。 企業託管應用程式，從物理硬體到無伺服器功能。

## <a name="n-tier-applications"></a>N 層應用程式

[N-Tier 體系結構模式](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)是一個成熟的體系結構，它僅指將各種邏輯層分隔成獨立實體層的應用程式。 N 層體系結構是 N 層體系結構的物理實現。 此體系結構的最常見實現包括：

- 展示層，例如 Web 應用。
- API 或資料訪問層，如 REST API。
- 資料層，如 SQL 資料庫。

![N 層體系結構](./media/n-tier-architecture.png)

N 層解決方案具有以下特徵：

- 專案通常與層對齊。
- 按層處理測試的方式可能不同。
- 層提供抽象層，例如，展示層通常不知道資料層的實現細節。
- 通常，圖層僅與相鄰圖層交互。
- 版本通常在專案管理，因此在層級別進行管理。 簡單的 API 更改可能需要整個中介層的新版本。

此方法提供了幾個好處，包括：

- 資料庫的隔離（通常前端不能直接存取資料庫後端）。
- 重用 API（例如，移動、桌面和 Web 應用用戶端都可以重用相同的 API）。
- 能夠相互獨立地橫向擴展層。
- 重構隔離：一個層可以重構，而不會影響其他層。

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>本地和基礎架構即服務 （IaaS）

傳統的託管應用程式方法需要購買硬體和管理所有軟體安裝，包括作業系統。 最初，這涉及到昂貴的資料中心和物理硬體。 操作物理硬體面臨的挑戰很多，包括：

- 需要購買超額"以防萬一"或需求高峰的情況。
- 保護對硬體的物理訪問。
- 對硬體故障（如磁片故障）負責。
- 冷卻。
- 配置路由器和負載等化器。
- 電源冗余。
- 保護軟體訪問。

![IaaS 方法](./media/iaas-approach.png)

通過"虛擬機器"實現硬體虛擬化，支援基礎架構即服務 （IaaS）。 主機得到有效分區，為具有分配自身記憶體、CPU 和存儲的實例提供資源。 團隊提供必要的 VM 並配置關聯的網路和對存儲的訪問。

有關詳細資訊，請參閱虛擬機器[N 層引用體系結構](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)。

儘管虛擬化和基礎架構即服務 （IaaS） 解決了許多問題，但它仍然將大部分責任推給基礎架構團隊。 團隊維護作業系統版本，應用安全修補程式，並在目的電腦上安裝協力廠商依賴項。 與測試環境相比，應用在生產電腦上的行為通常不同。 由於依賴項版本和/或 OS SKU 級別不同，會出現問題。 儘管許多組織將 N-Tier 應用程式部署到這些目標，但許多公司從部署到更雲本機模型（如[平臺即服務](#platform-as-a-service-paas)）中獲益。 具有微服務的體系結構更具挑戰性，因為需要橫向擴展以擴展彈性和彈性。

有關詳細資訊，請參閱[虛擬機器](https://docs.microsoft.com/azure/virtual-machines/)。

## <a name="platform-as-a-service-paas"></a>平台即服務 (PaaS)

平臺即服務 （PaaS） 提供配置的解決方案，開發人員可以直接插入這些解決方案。 PaaS 是託管託管的另一個術語。 它消除了管理基本作業系統、安全修補程式以及在許多情況下任何協力廠商依賴關係的需要。 平臺的示例包括 Web 應用程式、資料庫和移動後端。

PaaS 解決了 IaaS 面臨的共同挑戰。 PaaS 允許開發人員專注于代碼或資料庫架構，而不是部署方式。 PaaS 的優勢包括：

- 支付使用模型，消除投資閒置機器的開銷。
- 直接部署和改進的 DevOps、持續集成 （CI） 和持續交付 （CD） 管道。
- 自動升級、更新和安全修補程式。
- 按鈕橫向擴展和放大（彈性刻度）。

傳統上，PaaS 的主要缺點是供應商鎖定。 例如，某些 PaaS 提供程式僅支援ASP.NET、Node.js 或其他特定語言和平臺。 Azure 應用服務等產品已演變為針對多個平臺，並支援託管 Web 應用的各種語言和框架。

![平臺即服務架構](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>軟體即服務 (SaaS)

軟體即服務或 SaaS 是集中託管的，無需本地安裝或預配即可使用。 SaaS 通常託管在 PaaS 之上，作為部署軟體的平臺。 SaaS 提供用於運行和連接現有軟體的服務。 SaaS 通常是行業和垂直特定的。 SaaS 通常獲得許可，通常提供用戶端/伺服器模型。 大多數現代 SaaS 產品都使用基於 Web 的應用程式來為用戶端服務。 公司通常將 SaaS 視為許可產品的業務解決方案。 它通常不作為應用程式的可伸縮性和可維護性的體系結構考慮實現。 實際上，大多數 SaaS 解決方案都基於 IaaS、PaaS 和/或無伺服器後端構建。

通過[應用程式範例](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)瞭解有關 SaaS 的更多。

## <a name="containers-and-functions-as-a-service-faas"></a>容器和功能作為服務 （FaaS）

容器是一個有趣的解決方案，可實現類似 PaaS 的好處，而無需 IaaS 開銷。 容器本質上是一個運行時，其中包含運行唯一應用程式所需的基本要素。 主機作業系統的內核或核心部分以及存儲等服務在主機之間共用。 共用內核使容器具有羽量級（有些容器的大小僅為百萬位元組，而典型虛擬機器的大小僅為千百萬位元組）。 主機已經運行，容器可以快速啟動，從而促進高可用性。 快速啟動容器的能力也提供了額外的彈性層。 Docker 是容器中較流行的實現之一。

容器的優點包括：

- 輕便便攜
- 自包含，因此無需安裝依賴項
- 無論主機如何，都能提供一致的環境（在可擕式電腦上運行與雲伺服器上完全相同）
- 可快速調配，用於橫向擴展
- 可以快速重新開機以從故障中恢復

容器在容器主機上運行（該容器可能在裸機或虛擬機器上運行）。 同一容器的多個容器或實例可能在單個主機上運行。 為了實現真正的容錯移轉和恢復能力，容器必須跨主機縮放。

有關 Docker 容器的詳細資訊，請參閱[什麼是 Docker](../microservices/container-docker-introduction/docker-defined.md)。

跨主機管理容器通常需要業務流程工具（如 Kubernetes）。 配置和管理業務流程解決方案可能會增加專案的額外開銷和複雜性。 幸運的是，許多雲供應商通過 PaaS 解決方案提供編排服務，以簡化容器的管理。

下圖演示了庫伯內斯安裝的示例。 安裝位址中的節點橫向擴展和容錯移轉。 它們運行由主伺服器管理的 Docker 容器實例。 *庫貝萊特*是中繼命令從庫伯內斯到 Docker 的用戶端。

![Kubernetes](./media/kubernetes-example.png)

有關業務流程的詳細資訊，請參閱 Azure[上的庫伯內斯](https://docs.microsoft.com/azure/aks/intro-kubernetes)。

服務功能 （FaaS） 是類似于無伺服器的專用容器服務。 FaaS 的一個特定實現，稱為[OpenFaaS，](https://github.com/openfaas/faas)位於容器頂部，提供無伺服器功能。 OpenFaaS 提供範本，用於打包運行程式碼片段所需的所有容器依賴項。 使用範本簡化了將代碼作為功能單元部署的過程。 OpenFaaS 面向已包含容器和協調器的體系結構，因為它可以使用現有的基礎結構。 儘管它提供無伺服器功能，但它特別要求您使用 Docker 和協調器。

## <a name="serverless"></a>無伺服器

無伺服器體系結構在代碼及其託管環境之間提供了明確的分離。 在*由觸發器*調用的*函數*中實現代碼。 退出該函數後，可以釋放其所有所需的資源。 觸發器可以是手動的、定時的過程、HTTP 要求或檔上載。 觸發器的結果是代碼的執行。 儘管無伺服器平臺各不相同，但大多數平臺都提供對預定義的 API 和綁定的訪問，以簡化任務，如寫入資料庫或排隊結果。

無伺服器是一種嚴重依賴抽象主機環境以專注于代碼的體系結構。 它可以被認為是*更少的伺服器*。

容器解決方案為開發人員提供現有生成腳本，將代碼發佈到無伺服器就緒映射。 其他實現使用現有的 PaaS 解決方案來提供可擴展的體系結構。

抽象意味著 DevOps 團隊不必預配或管理伺服器，也不必管理特定的容器。 無伺服器平臺託管代碼，作為使用相關 SDK 構建的腳本或打包可執行檔，並為代碼分配必要的資源進行擴展。

下圖顯示了四個無伺服器元件。 HTTP 要求會導致簽出 API 代碼運行。 簽出 API 將代碼插入到資料庫中，插入將觸發其他幾個函數來運行以執行計算任務和完成順序等任務。

![無伺服器實現](./media/serverless-implementation.png)

無伺服器的優點包括：

- **高密度。** 與容器或虛擬機器相比，同一無伺服器代碼的許多實例可以在同一主機上運行。 實例跨多個主機擴展並進行恢復。
- **微計費。** 大多數無伺服器供應商都根據無伺服器執行計費，從而在某些情況下大幅節約成本。
- **即時縮放。** 無伺服器可以自動快速擴展以匹配工作負載。
- **更快的上市時間。** 開發人員專注于代碼並直接部署到無伺服器平臺。 元件可以相互獨立釋放。

無伺服器最常在計算上下文中討論，但也可應用於資料。 例如[，Azure SQL](https://docs.microsoft.com/azure/sql-database)和[Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)都提供雲資料庫，這些資料庫不需要配置主機或群集。 本書側重于無伺服器計算。

## <a name="summary"></a>摘要

架構有多種可用選擇，包括混合方法。 無伺服器簡化了應用程式功能的方法、管理和成本，但代價是控制和可攜性。 但是，許多無伺服器平臺公開配置以説明微調解決方案。 良好的程式設計實踐還會導致更多的可移植代碼和更少的無伺服器平臺鎖定。 下表說明了並行體系結構方法。 根據您的規模需求選擇無伺服器，無論您是否想要管理運行時，以及將工作負載分解為小型元件的能力。 在下一章中，您將瞭解無伺服器和其他決策點的潛在挑戰。

|         |IaaS     |PaaS     |容器|無伺服器|
|---------|---------|---------|---------|----------|
|**規模**|VM       |執行個體 |App      |函式  |
|**文摘**|硬體|平台|作業系統主機|執行階段   |
|**單位** |VM       |隨附此逐步解說的專案  |映像    |程式碼      |
|**一生**|Months|天數到月數|分鐘到天數|毫秒到分鐘數|
|**責任**|應用程式、依賴項、運行時和作業系統|應用程式和依賴項|應用程式、依賴項和運行時|函式

- **縮放**是指用於擴展應用程式的單位
- **摘要**是指由實現抽象的層
- **單元**是指部署的範圍
- **存留期**是指特定實例的典型運行時
- **責任**是指構建、部署和維護應用程式的開銷

下一章將重點討論無伺服器體系結構、用例和設計模式。

## <a name="recommended-resources"></a>建議的資源

- [Azure 應用程式體系結構指南](https://docs.microsoft.com/azure/architecture/guide/)
- [Azure 宇宙資料庫](https://docs.microsoft.com/azure/cosmos-db)
- [Azure SQL](https://docs.microsoft.com/azure/sql-database)
- [N 層體系結構模式](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
- [Azure 上的 Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes)
- [微服務](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
- [虛擬機器 N 層參考體系結構](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
- [虛擬機器](https://docs.microsoft.com/azure/virtual-machines/)
- [什麼是 Docker？](../microservices/container-docker-introduction/docker-defined.md)
- [翼尖門票SaaS應用程式](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[上一個](architecture-approaches.md)
>[下一個](serverless-architecture.md)
