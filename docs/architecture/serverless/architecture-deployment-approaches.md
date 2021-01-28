---
title: 架構部署方法-無伺服器應用程式
description: 以不同方式將企業架構部署至雲端的指南，其中包含 IaaS、PaaS、容器和無伺服器之間的比較。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 89a8e6a52331b563be334a867f563e9ded8d8cc4
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957958"
---
# <a name="architecture-deployment-approaches"></a>架構部署方法

無論用來設計商務應用程式的架構方法為何，這些應用程式的執行或部署都可能不同。 企業會從實體硬體到無伺服器函式的所有專案上裝載應用程式。

## <a name="n-tier-applications"></a>多層式應用程式

多 [層式架構模式](/azure/architecture/guide/architecture-styles/n-tier) 是成熟的架構，而且只是指將各種不同的邏輯層分成不同的實體層的應用程式。 多層式架構是多層式架構的實體實行。 此架構最常見的實作為包括：

- 展示層，例如 web 應用程式。
- API 或資料存取層，例如 REST API。
- 資料層，例如 SQL 資料庫。

![多層式架構](./media/n-tier-architecture.png)

多層式解決方案具有下列特性：

- 專案通常會與層級對齊。
- 依階層的不同，可能會以不同的方式來進行測試。
- 層提供抽象層，例如展示層通常不是資料層的執行詳細資料。
- 一般而言，圖層只會與連續的圖層互動。
- 版本通常會在專案中管理，因此也會在層級層級進行管理。 簡單的 API 變更可能需要整個仲介層的新版本。

這種方法可提供數個優點，包括：

- 隔離資料庫 (通常前端無法直接存取資料庫後端) 。
- 重複使用 API (例如，行動裝置、桌面和 web 應用程式用戶端都可以使用相同的 Api) 。
- 能夠彼此獨立地相應放大層級。
- 重構隔離：一層可以重構，而不會影響其他層。

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a> (IaaS) 的內部部署和基礎結構即服務

裝載應用程式的傳統方法需要購買硬體和管理所有軟體安裝，包括作業系統。 這一開始涉及昂貴的資料中心和實體硬體。 營運實體硬體所帶來的挑戰很多，包括：

- 需要購買超過「單純案例」或尖峰需求案例的額外功能。
- 保護硬體的實體存取。
- 硬體故障的責任 (例如磁片失敗) 。
- 冷卻。
- 設定路由器和負載平衡器。
- 電源冗余。
- 保護軟體存取的安全。

![IaaS 方法](./media/iaas-approach.png)

透過「虛擬機器」的硬體虛擬化可讓基礎結構即服務 (IaaS) 。 主機電腦會有效地進行分割，以提供資源給具有自己記憶體、CPU 和儲存體配置的實例。 小組會布建必要的 Vm，並設定相關聯的網路和儲存體的存取權。

如需詳細資訊，請參閱 [虛擬機器多層式參考架構](/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)。

雖然虛擬化和基礎結構即服務 (IaaS) 解決許多問題，但在基礎結構小組的手中仍有很多責任。 小組會維護作業系統版本、套用安全性修補程式，並在目的電腦上安裝協力廠商相依性。 相較于測試環境，應用程式在生產電腦上的行為通常會有所不同。 由於不同的相依性版本和（或）作業系統 SKU 層級而產生的問題。 雖然許多組織會將多層式應用程式部署到這些目標，但是許多公司都受益于部署到更多雲端原生模型，例如 [平臺即服務](#platform-as-a-service-paas)。 具有微服務的架構更具挑戰性，因為需要相應放大以進行彈性和復原。

如需詳細資訊，請參閱 [虛擬機器](/azure/virtual-machines/)。

## <a name="platform-as-a-service-paas"></a>平台即服務 (PaaS)

「平臺即服務」 (PaaS) 提供了開發人員可以直接插入的已設定解決方案。 PaaS 是受控裝載的另一項詞彙。 它免除了管理基礎作業系統、安全性修補程式，以及在許多情況下都有協力廠商相依性的需求。 平臺範例包括 web 應用程式、資料庫和行動後端。

PaaS 可解決 IaaS 常見的挑戰。 PaaS 可讓開發人員專注于程式碼或資料庫架構，而不是部署的方式。 PaaS 的優點包括：

- 支付使用模型的費用，以消除投資閒置電腦的額外負荷。
- 直接部署及改進 DevOps、持續整合 (CI) 和持續傳遞 (CD) 管線。
- 自動升級、更新和安全性修補程式。
- 向外延展和擴大 (彈性調整) 。

通常，PaaS 的主要缺點是廠商鎖定。 例如，某些 PaaS 提供者只支援 ASP.NET、Node.js 或其他特定語言和平臺。 產品（例如 Azure App Service）已發展成可處理多個平臺，並支援各種不同的語言和架構來裝載 web 應用程式。

![平臺即服務架構](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>軟體即服務 (SaaS)

軟體即服務或 SaaS 是集中裝載的，且不需要本機安裝或布建即可使用。 SaaS 通常裝載于 PaaS 之上，作為部署軟體的平臺。 SaaS 提供執行和連接現有軟體的服務。 SaaS 通常是產業和垂直特定的。 SaaS 通常是經過授權的，通常會提供用戶端/伺服器模型。 大部分新式 SaaS 供應專案會針對用戶端使用 web 應用程式。 公司通常會將 SaaS 視為授權供應專案的企業解決方案。 它通常不會作為應用程式的擴充性和可維護性的架構考慮。 事實上，大部分的 SaaS 解決方案都是建立在 IaaS、PaaS 及/或無伺服器的後端。

透過 [範例應用程式](/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)深入瞭解 SaaS。

## <a name="containers-and-functions-as-a-service-faas"></a>容器和函式即服務 (FaaS) 

容器是一種有趣的解決方案，可在沒有 IaaS 額外負荷的情況下啟用類似 PaaS 的權益。 容器本質上是包含執行唯一應用程式所需之裸機基本的執行時間。 主機作業系統和服務（例如儲存體）的核心或核心部分會在主機間共用。 相較于一般虛擬機器) 的 gb 大小，共用的核心讓容器可以輕量 (部分的大小只是 mb。 使用已在執行中的主機，可以快速啟動容器，以加速高可用性。 快速啟動容器的能力也可提供額外的彈性層級。 Docker 是更受歡迎的容器的其中一個。

容器的優點包括：

- 輕量與可攜
- 獨立，不需要安裝相依性
- 提供一致的環境，不論主機 (在與雲端伺服器上相同的膝上型電腦上執行完全相同) 
- 可以快速布建以進行相應放大
- 可以快速重新開機以從失敗中復原

容器會在容器主機上執行， (接著可在裸機電腦或虛擬機器) 上執行。 相同容器的多個容器或實例可能會在單一主機上執行。 若要取得真正的容錯移轉和復原功能，您必須在主機之間調整容器。

如需 Docker 容器的詳細資訊，請參閱 [什麼是 docker](../microservices/container-docker-introduction/docker-defined.md)。

跨主機管理容器通常需要協調流程工具，例如 Kubernetes。 設定和管理協調流程解決方案可能會增加專案的額外負荷和複雜度。 幸運的是，許多雲端提供者都透過 PaaS 解決方案提供協調流程服務，以簡化容器的管理工作。

下圖說明 Kubernetes 安裝的範例。 安裝位址中的節點會相應放大及容錯移轉。 它們會執行主伺服器所管理的 Docker 容器實例。 *Kubelet* 是將命令從 Kubernetes 轉送至 Docker 的用戶端。

![Kubernetes](./media/kubernetes-example.png)

如需有關協調流程的詳細資訊，請參閱 [Azure 上的 Kubernetes](/azure/aks/intro-kubernetes)。

函式即服務 (FaaS) 是類似于無伺服器的特製化容器服務。 FaaS 的特定執行（稱為 [OpenFaaS](https://github.com/openfaas/faas)）位於容器之上，以提供無伺服器功能。 OpenFaaS 會提供範本，以封裝執行某段程式碼所需的所有容器相依性。 使用範本可簡化將程式碼部署為功能性單位的流程。 OpenFaaS 會以已包含容器和協調器的架構為目標，因為它可以使用現有的基礎結構。 雖然它提供無伺服器功能，但特別需要您使用 Docker 和協調器。

## <a name="serverless"></a>無伺服器

無伺服器架構可讓程式碼與其裝載環境之間有清楚的分隔。 您可以在由 *觸發* 程式叫 *用的函* 式中執行程式碼。 該函式結束之後，可能會釋出其所有所需的資源。 觸發程式可能是手動、計時進程、HTTP 要求或檔案上傳。 觸發程式的結果就是程式碼的執行。 雖然無伺服器平臺不同，但大部分會提供預先定義之 Api 和系結的存取權，以簡化工作（例如寫入資料庫或將結果排入佇列）的作業。

無伺服器是一種架構，主要依賴于退出主機環境以專注于程式碼。 您可以將它視為 *較少的伺服器*。

容器解決方案為開發人員提供現有的組建腳本，以將程式碼發佈到無伺服器就緒的映射。 其他的執行會使用現有的 PaaS 解決方案來提供可調整的架構。

此抽象概念表示 DevOps 小組不需要布建或管理伺服器，也不需要管理特定的容器。 無伺服器平臺會將程式碼裝載為使用相關 SDK 建立的腳本或封裝可執行檔，並配置程式碼所需的資源以進行調整。

下圖為四個無伺服器元件。 HTTP 要求會導致簽出 API 程式碼執行。 結帳 API 會將程式碼插入資料庫中，而插入會觸發其他數個函式來執行工作，例如運算工作和達成順序。

![無伺服器的執行](./media/serverless-implementation.png)

無伺服器的優點包括：

- **高密度。** 相較于容器或虛擬機器，相同的無伺服器程式碼的許多實例都可以在相同的主機上執行。 這些實例會跨多個主機擴充和復原。
- **微計費。** 大部分的無伺服器提供者會根據無伺服器執行計費，在某些情況下可節省大量成本。
- **立即調整規模。** 無伺服器可進行調整以自動且快速地符合工作負載。
- **加快上市時間。** 開發人員將焦點放在程式碼，並直接部署到無伺服器平臺。 元件可以獨立釋放。

無伺服器最常在計算的內容中討論，但也適用于資料。 例如， [AZURE SQL](/azure/sql-database) 和 [Cosmos DB](/azure/cosmos-db) 都提供不需要您設定主機電腦或叢集的雲端資料庫。 本書著重于無伺服器計算。

## <a name="summary"></a>摘要

架構有廣泛的可用選項，包括混合式方法。 無伺服器可簡化應用程式功能的方法、管理和成本，但代價是控制和可攜性。 不過，許多無伺服器平臺會公開設定，以協助微調解決方案。 良好的程式設計實務也可能會導致更具可攜性的程式碼，以及更少的無伺服器平臺鎖定。 下表說明並列的架構方法。 無論您是否想要管理執行時間，都可以根據您的調整需求選擇無伺服器，以及將工作負載分成小型元件的程度。 您將在下一章中瞭解無伺服器和其他決策點的潛在挑戰。

|         |IaaS     |PaaS     |容器|無伺服器|
|---------|---------|---------|---------|----------|
|**縮放**|VM       |執行個體 |應用程式      |函式  |
|**文摘**|硬體|平台|OS 主機|執行階段   |
|**單位** |VM       |Project  |映像    |程式碼      |
|**存留期**|月|天到數個月|分鐘到數天|毫秒到分鐘|
|**責任**|應用程式、相依性、執行時間和作業系統|應用程式和相依性|應用程式、相依性和執行時間|函式

- **Scale** 指的是用來調整應用程式的單位
- **抽象化** 指的是由執行所抽象化的圖層
- **單位** 是指部署的範圍
- **存留期** 指的是特定實例的一般執行時間
- **責任** 是指建立、部署及維護應用程式的額外負荷

下一章將著重于無伺服器架構、使用案例和設計模式。

## <a name="recommended-resources"></a>建議的資源

- [Azure 應用程式架構指南](/azure/architecture/guide/)
- [Azure Cosmos DB](/azure/cosmos-db)
- [Azure SQL](/azure/sql-database)
- [多層式架構模式](/azure/architecture/guide/architecture-styles/n-tier)
- [Azure 上的 Kubernetes](/azure/aks/intro-kubernetes)
- [微服務](/azure/architecture/guide/architecture-styles/microservices)
- [虛擬機器多層式參考架構](/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
- [虛擬機器](/azure/virtual-machines/)
- [什麼是 Docker？](../microservices/container-docker-introduction/docker-defined.md)
- [Wingtip 票證 SaaS 應用程式](/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[上一個](architecture-approaches.md) 
>[下一步](serverless-architecture.md)
