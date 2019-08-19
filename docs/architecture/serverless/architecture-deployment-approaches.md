---
title: 架構部署方法-無伺服器應用程式
description: 以不同方式將企業架構部署到雲端的指南, 其中包含 IaaS、PaaS、容器和無伺服器之間的比較。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8a1203ea2fc7089223c03b3a3e02fd3303610272
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577631"
---
# <a name="architecture-deployment-approaches"></a>架構部署方法

無論用來設計商務應用程式的架構方法為何, 執行或部署這些應用程式都可能有所不同。 企業將應用程式裝載在實體硬體到無伺服器函式的所有專案上。

## <a name="n-tier-applications"></a>多層式架構應用程式

多[層式架構模式](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)是成熟的架構, 只是指將各種邏輯層分成不同實體層的應用程式。 多層式架構是多層式架構的實體執行。 此架構最常見的執行包括:

* 展示層, 例如 web 應用程式。
* API 或資料存取層, 例如 REST API。
* 資料層, 例如 SQL 資料庫。

![多層式架構](./media/n-tier-architecture.png)

多層式解決方案具有下列特性:

* 專案通常會與層對齊。
* 測試可能會因層而異。
* 層提供抽象層, 例如展示層通常不會有資料層的執行細節。
* 一般而言, 圖層只會與相鄰層互動。
* 發行通常會在專案上進行管理, 因而是層級。 簡單的 API 變更可能需要新版本的整個仲介層。

這種方法提供數個優點, 包括:

* 隔離資料庫 (通常前端並不會直接存取資料庫後端)。
* 重複使用 API (例如, 行動、桌面和 web 應用程式用戶端都可以重複使用相同的 Api)。
* 能夠相應放大彼此獨立的層。
* 重構隔離: 可能會重構一層, 而不會影響其他層。

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>內部部署和基礎結構即服務 (IaaS)

裝載應用程式的傳統方法需要購買硬體及管理所有軟體安裝, 包括作業系統。 最初這牽涉到昂貴的資料中心和實體硬體。 營運實體硬體所帶來的挑戰很多, 包括:

* 需要購買多餘的「以防萬一」或尖峰需求案例。
* 保護硬體的實體存取。
* 硬體失敗 (例如磁片失敗) 的責任。
* 裝置.
* 設定路由器和負載平衡器。
* 電源冗余。
* 保護軟體存取。

![IaaS 方法](./media/iaas-approach.png)

透過「虛擬機器」的硬體虛擬化可啟用基礎結構即服務 (IaaS)。 主機電腦會有效率地進行分割, 以提供資源給具有自己的記憶體、CPU 和儲存體配置的實例。 小組會布建必要的 Vm, 並設定相關聯的網路和儲存體的存取權。

如需詳細資訊, 請參閱[虛擬機器多層式參考架構](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)。

雖然虛擬化和基礎結構即服務 (IaaS) 解決了許多問題, 但仍會在基礎結構小組的手中承擔相當大的責任。 小組會維護作業系統版本、套用安全性修補程式, 並在目的電腦上安裝協力廠商相依性。 相較于測試環境, 應用程式在生產電腦上通常會有不同的行為。 因相依性版本和 (或) OS SKU 層級不同而引發的問題。 雖然許多組織都將多層式應用程式部署到這些目標, 但許多公司都受益于部署到更多雲端原生模型, 例如[平臺即服務](#platform-as-a-service-paas)。 具有微服務的架構較具挑戰性, 因為需要相應放大以進行彈性和復原。

如需詳細資訊, 請參閱[虛擬機器](https://docs.microsoft.com/azure/virtual-machines/)。

## <a name="platform-as-a-service-paas"></a>平臺即服務 (PaaS)

平臺即服務 (PaaS) 提供了已設定的解決方案, 可讓開發人員直接插入。 PaaS 是受控主機的另一種詞彙。 它不需要管理基礎作業系統、安全性修補程式, 以及許多情況下的任何協力廠商相依性。 平臺的範例包括 web 應用程式、資料庫和行動後端。

PaaS 解決了 IaaS 的常見挑戰。 PaaS 可讓開發人員專注于程式碼或資料庫架構, 而不是部署它的方式。 PaaS 的優點包括:

* 使用模型的費用, 可免除投資閒置機器的額外負荷。
* 直接部署和改良的 DevOps、持續整合 (CI) 和持續傳遞 (CD) 管線。
* 自動升級、更新和安全性修補程式。
* 推播按鈕相應放大和相應增加 (彈性調整)。

在傳統上, PaaS 的主要缺點是廠商鎖定。 例如, 有些 PaaS 提供者只支援 ASP.NET、node.js 或其他特定語言和平臺。 Azure App Service 之類的產品演變成可處理多個平臺, 並支援各種語言和架構來裝載 web 應用程式。

![平臺即服務架構](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>軟體即服務 (SaaS)

軟體即服務或 SaaS 會集中裝載並可供使用, 而不需要本機安裝或布建。 SaaS 通常裝載于 PaaS 之上, 作為部署軟體的平臺。 SaaS 提供服務來執行和連接現有軟體。 SaaS 通常是產業和垂直特定。 SaaS 通常是授權的, 而且通常會提供用戶端/伺服器模型。 最新的 SaaS 供應專案會針對用戶端使用 web 應用程式。 公司通常會將 SaaS 視為授權供應專案的商務解決方案。 它通常不會實作為應用程式的擴充性和可維護性的架構考慮。 事實上, 大部分的 SaaS 解決方案都是以 IaaS、PaaS 和 (或) 無伺服器後端為基礎。

透過[範例應用程式](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)深入瞭解 SaaS。

## <a name="containers-and-functions-as-a-service-faas"></a>容器和函式即服務 (FaaS)

容器是一種有趣的解決方案, 能在沒有 IaaS 額外負荷的情況下啟用 PaaS 的優點。 容器基本上是一個執行時間, 其中包含執行唯一應用程式所需的裸機基本知識。 主機作業系統和服務 (例如儲存體) 的核心或核心部分會在主機之間共用。 共用的核心可讓容器更輕量 (相較于一般虛擬機器的 gb 大小, 有些是大小的 mb)。 當主機已在執行中時, 可以快速啟動容器, 以加速高可用性。 快速啟動容器的能力也會提供額外的復原層級。 Docker 是其中一個較熱門的容器執行方式。

容器的優點包括:

* 輕量和可攜
* 獨立, 因此不需要安裝相依性
* 提供一致的環境, 無論主機為何 (在與雲端伺服器上的膝上型電腦上執行完全相同)
* 可以快速布建以進行相應放大
* 可以快速重新開機, 以從失敗中復原

容器會在容器主機上執行 (接著可能會在裸機機器或虛擬機器上執行)。 同一個容器的多個容器或實例可能會在單一主機上執行。 針對真正的容錯移轉和復原, 必須在主機間調整容器。

如需 Docker 容器的詳細資訊, 請參閱[什麼是 docker](../microservices/container-docker-introduction/docker-defined.md)？

管理跨主機的容器通常需要協調流程工具, 例如 Kubernetes。 設定和管理協調流程方案可能會對專案增加額外的負荷和複雜度。 幸運的是, 許多雲端提供者都透過 PaaS 解決方案提供協調流程服務, 以簡化容器的管理。

下圖說明 Kubernetes 安裝的範例。 安裝位址中的節點會相應放大和容錯移轉。 它們會執行由主伺服器管理的 Docker 容器實例。 *Kubelet*是將命令從 Kubernetes 轉送至 Docker 的用戶端。

![Kubernetes](./media/kubernetes-example.png)

如需協調流程的詳細資訊, 請參閱[Azure 上的 Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes)。

函式即服務 (FaaS) 是類似于無伺服器的特製化容器服務。 FaaS 的特定執行 (稱為[OpenFaaS](https://github.com/openfaas/faas)) 位於容器之上, 以提供無伺服器功能。 OpenFaaS 提供範本來封裝執行一段程式碼所需的所有容器相依性。 使用範本可簡化將程式碼部署為功能單位的程式。 OpenFaaS 是以已經包含容器和協調器的架構為目標, 因為它可以使用現有的基礎結構。 雖然它提供無伺服器功能, 但特別需要您使用 Docker 和協調器。

## <a name="serverless"></a>無伺服器

無伺服器架構會在程式碼與其主控環境之間提供清楚的分隔。 您會在*觸發*程式所叫用的函式中實*作用*程式碼。 該函式結束之後, 可能會釋放其所有所需的資源。 觸發程式可能是手動、計時進程、HTTP 要求或檔案上傳。 觸發程式的結果就是執行程式碼。 雖然無伺服器平臺有所不同, 但大部分都會提供預先定義之 Api 和系結的存取權, 以簡化寫入資料庫或將結果排入佇列的作業。

無伺服器是一種架構, 其高度依賴于將焦點放在主機環境, 以專注于程式碼。 它可以視為*較少的伺服器*。

容器解決方案為開發人員提供現有的組建腳本, 以將程式碼發佈至無伺服器的映射。 其他的執行會使用現有的 PaaS 解決方案來提供可擴充的架構。

抽象概念表示 DevOps 小組不需要布建或管理伺服器, 也不必提供特定容器。 無伺服器平臺會裝載程式碼, 做為使用相關 SDK 所建立的腳本或封裝的可執行檔, 並配置必要的資源以進行調整。

下圖說明四個無伺服器元件。 HTTP 要求會導致簽出 API 程式碼執行。 簽出 API 會將程式碼插入資料庫中, 而插入會觸發數個其他函式來執行工作, 例如運算工作和履行訂單。

![無伺服器的執行](./media/serverless-implementation.png)

無伺服器的優點包括:

* **高密度。** 相較于容器或虛擬機器, 相同的無伺服器程式碼的許多實例可以在相同的主機上執行。 實例會在多個主機相應放大和恢復功能之間進行調整。
* **微計費**。 大部分的無伺服器提供者會根據無伺服器執行計費, 在某些情況下可節省大量成本。
* **立即調整**。 無伺服器可以自動且快速地調整以符合工作負載。
* **加快上市時間**開發人員將焦點放在程式碼, 並直接部署到無伺服器平臺。 元件可以獨立發行。

無伺服器最常在計算的內容中討論, 但也可以套用至資料。 例如, [AZURE SQL](https://docs.microsoft.com/azure/sql-database)和[Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)都提供不需要您設定主機機器或叢集的雲端資料庫。 本書著重在無伺服器計算。

## <a name="summary"></a>總結

架構有廣泛的可用選項, 包括混合式方法。 無伺服器可簡化應用程式功能的方法、管理和成本, 同時也能提供控制和可攜性的費用。 不過, 許多無伺服器平臺確實會公開設定, 以協助微調解決方案。 良好的程式設計作法也可能導致更具可攜性的程式碼, 以及較少的無伺服器平臺鎖定。 下表說明並排的架構方法。 根據您的規模需求選擇無伺服器, 不論您是否要管理執行時間, 以及將工作負載分解成小型元件有多好。 在下一章中, 您將瞭解無伺服器和其他決策點的潛在挑戰。

|         |IaaS     |PaaS     |容器|無伺服器|
|---------|---------|---------|---------|----------|
|**縮放**|VM       |執行個體 |App      |函數  |
|**摘要**|硬體|平台|OS 主機|執行階段   |
|**單元** |VM       |專案  |Image    |程式碼      |
|**存留期**|以前|天到數月|分鐘到數天|毫秒到分鐘|
|**宣言**|應用程式、相依性、執行時間和作業系統|應用程式和相依性|應用程式、相依性和執行時間|函數

* 「**調整**」指的是用來調整應用程式的單位
* [**摘要**] 是指由執行所抽象化的圖層
* **單位**是指已部署之內容的範圍
* 「**存留期**」是指特定實例的一般執行時間
* **責任**指的是建立、部署和維護應用程式的額外負荷。

下一章將著重于無伺服器架構、使用案例和設計模式。

## <a name="recommended-resources"></a>建議的資源

* [Azure 應用程式架構指南](https://docs.microsoft.com/azure/architecture/guide/)
* [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
* [Azure SQL](https://docs.microsoft.com/azure/sql-database)
* [多層式架構模式](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
* [Azure 上的 Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes)
* [微服務](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
* [虛擬機器多層式參考架構](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
* [虛擬機器](https://docs.microsoft.com/azure/virtual-machines/)
* [什麼是 Docker？](../microservices/container-docker-introduction/docker-defined.md)
* [Wingtip 票證 SaaS 應用程式](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[上一頁](architecture-approaches.md)
>[下一頁](serverless-architecture.md)
