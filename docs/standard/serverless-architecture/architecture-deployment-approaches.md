---
title: 架構部署方法-無伺服器應用程式
description: 不同的方式企業架構的指南會為已部署至雲端，透過 IaaS、 PaaS、 容器之間的比較和無伺服器。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5477b8c4531780fdebf194e4f798564e59cd2953
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640228"
---
# <a name="architecture-deployment-approaches"></a>架構部署方法

不管架構為何方法用來設計商務應用程式，實作或部署這些應用程式可能會有所不同。 企業會裝載在實體硬體的所有項目上的應用程式，無伺服器函式。

## <a name="n-tier-applications"></a>多層式架構應用程式

[多層式架構模式](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)是成熟的架構，而只會參考各邏輯層分成不同的實體層級的應用程式。 多層式架構是 N 層架構的實體實作。 最常見的實作，此架構包含：

* 展示層中，例如 web 應用程式。
* API 或資料存取層，例如 REST API。
* 資料層，例如 SQL database。

![多層式架構](./media/n-tier-architecture.png)

多層式架構方案具有下列特性：

* 專案通常會配合層。
* 測試可能會碰到有不同層。
* 層級提供的抽象層，例如展示層通常非持續性的資料層的實作詳細資料。
* 一般而言，層級只會與相鄰的圖層互動。
* 釋放通常在專案中，管理，並因此層級。 簡單的 API 變更可能需要整個的中介層的新版本。

此方法會提供幾項優點，包括：

* 隔離的資料庫 （通常後端不可以直接存取資料庫後端）。
* 重複使用的 api （例如，行動、 桌面和 web 應用程式用戶端可以所有重複使用相同的 Api）。
* 相應放大層彼此獨立的能力。
* 重構隔離： 可能重構一層，而不會影響其他層。

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>在內部部署環境和基礎結構即服務 (IaaS)

裝載應用程式的傳統方法需要購買硬體和管理所有軟體安裝，包括作業系統。 原本這項作業需要昂貴的資料中心與實體硬體。 隨附於作業系統的實體硬體的挑戰有很多，包括：

* 需要購買額外的 「 以防萬一 」 或尖峰需求的案例。
* 設定安全性實體存取硬體。
* 硬體失敗 （例如磁碟錯誤） 的責任。
* 冷卻系統。
* 設定路由器和負載平衡器。
* 電源備援性。
* 保護軟體的存取。

![IaaS 方法](./media/iaas-approach.png)

虛擬化硬體，透過 「 虛擬機器 」 會使基礎結構即服務 (IaaS)。 主機電腦可以有效地分割，以提供執行個體的資源配置與他們自己的記憶體、 CPU 和儲存體。 小組會佈建所需的 Vm，並設定相關聯的網路和儲存體的存取。

如需詳細資訊，請參閱 <<c0> [ 多層式架構參考架構的虛擬機器](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)。

雖然虛擬化和基礎結構即服務 (IaaS) 解決許多問題，它會保留大的責任的基礎結構小組手中。 小組會維護作業系統版本、 套用安全性修補程式，並在目標電腦上安裝協力廠商相依性。 應用程式通常有不同的行為相較於測試環境的實際執行電腦上。 由於不同的相依性版本和/或 OS SKU 層級，會發生問題。 雖然許多組織部署這些目標的多層式架構應用程式，但許多公司都受益於這類部署更多的雲端原生模式[平台即服務](#platform-as-a-service-paas)。 使用微服務架構會更具有挑戰性，因為向外擴充彈性和恢復功能的需求。

如需詳細資訊，請參閱 <<c0> [ 虛擬機器](https://docs.microsoft.com/azure/virtual-machines/)。

## <a name="platform-as-a-service-paas"></a>平台即服務 (PaaS)

提供服務 (PaaS) 平台設定開發人員可以直接插入的解決方案。 PaaS 是另一種說法受控裝載。 它就不需要管理基礎作業系統，安全性修補程式，並在許多情況下任何協力廠商相依性。 平台的範例包括 web 應用程式、 資料庫和行動後端。

PaaS 解決常見 IaaS 的挑戰。 PaaS 讓開發人員專注於程式碼或資料庫結構描述，而不是它取得部署的方式。 PaaS 的好處包括：

* 需支付使用的模型，可排除的投資閒置機器的額外負荷。
* 直接部署及提升的 DevOps、 持續整合 (CI) 和持續傳遞 (CD) 管線。
* 自動升級、 更新和安全性修補程式。
* 按相應放大和相應增加 （彈性延展）。

PaaS 的主要缺點一直都廠商鎖定中。 比方說，有些 PaaS 提供者僅支援 ASP.NET、 Node.js 或其他特定的語言及平台。 Azure App Service 等產品已演變成解決多個平台，並支援各種不同的語言和架構來裝載 web 應用程式。

![平台即服務架構](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>軟體即服務 (SaaS)

軟體即服務或 SaaS 是集中託管，毋需本機安裝或佈建。 SaaS 通常裝載在 PaaS 上做為部署軟體平台。 SaaS 提供服務給執行並連接現有的軟體。 業界和垂直特定，通常是 SaaS。 SaaS 通常授權，而且通常會提供用戶端/伺服器模型。 現今大部分的 SaaS 供應項目會用於用戶端中的 web 應用程式。 通常公司會將 SaaS 視為授權產品的商務解決方案中。 它通常不被實作為以獲得延展性和可維護性應用程式的架構考量。 事實上，大部分的 SaaS 解決方案是建置 IaaS、 PaaS 及/或無伺服器的後端。

深入了解透過 SaaS[範例應用程式](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)。

## <a name="containers-and-functions-as-a-service-faas"></a>容器和服務 」 (FaaS) 當做函式

容器是有趣的解決方案，可讓 IaaS 不必類似 PaaS 的優勢。 容器是基本上包含基本執行重複的應用程式所需的必要功能的執行階段。 跨越主機共用核心或核心的一部分的主機作業系統和服務，例如儲存體。 共用的核心，可讓 「 輕量型的容器 （有些是 mere 的大小，相較於一般的虛擬機器的 gb 大小的 mb）。 與已在執行中的主機，容器就可以啟動速度快，促進高可用性。 能夠快速啟動容器也會提供額外的層級的復原能力。 Docker 是其中一個更熱門的容器實作。

容器的優點包括：

* 輕量型和可攜式性質
* 自封式因此不需要安裝相依性
* 提供一致的環境，無論主機 （會執行在膝上型電腦上的雲端伺服器上完全相同）
* 可以向外延展快速佈建
* 您可從失敗復原快速重新啟動

容器會執行的容器主機上 （接著可以執行裸機機器或虛擬機器上）。 多個容器或相同的容器執行個體可能會在單一主機上執行。 真正的容錯移轉和恢復功能，容器必須跨越主機。

如需有關 Docker 容器的詳細資訊，請參閱[什麼是 Docker](../microservices-architecture/container-docker-introduction/docker-defined.md)？

管理容器主機上，通常需要 Kubernetes 等的協調流程工具。 設定和管理協調流程解決方案可能會加入額外的負擔與複雜性專案。 幸運的是，許多雲端提供者會提供透過 PaaS 解決方案，以簡化管理容器的協調流程服務。

下圖顯示範例的 Kubernetes 安裝。 在安裝位址向外延展和容錯移轉的節點。 執行 Docker 容器執行個體所管理的主要伺服器。 *Kubelet*是轉送命令給 Docker Kubernetes 的用戶端。

![Kubernetes](./media/kubernetes-example.png)

如需有關協調流程的詳細資訊，請參閱[在 Azure 上的 Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes)。

為服務 」 (FaaS) 的函式是特製化的容器服務，類似於無伺服器。 FaaS，呼叫的特定實作[OpenFaaS](https://github.com/openfaas/faas)，位於之上提供無伺服器功能的容器。 OpenFaaS 提供封裝所有執行一段程式碼所需的相依性容器的範本。 使用範本，可簡化部署做為功能單位的程式碼的程序。 OpenFaaS 的目標已包含容器和協調器，因為它可以使用現有的基礎結構的架構。 雖然它提供無伺服器的功能，它特別需要您使用 Docker 和協調器。

## <a name="serverless"></a>無伺服器

無伺服器架構提供清楚的區隔之間的程式碼，其裝載的環境。 實作中的程式碼*函式*藉由叫用*觸發程序*。 該函式結束之後，可能會釋放它所需的資源。 手動、 逾時的處理程序、 HTTP 要求或檔案上傳，可能是觸發程序。 觸發程序的結果是執行的程式碼。 雖然無伺服器平台而有所不同，最提供存取預先定義的 Api 和繫結，來簡化工作，例如寫入資料庫或排入佇列的結果。

無伺服器是高度依賴抽離主機環境，以專注於程式碼的架構。 它可以視為*較少的伺服器*。

容器解決方案，提供現有的開發人員建置無伺服器準備映像發佈的程式碼的指令碼。 其他實作可將現有的 PaaS 解決方案提供可擴充的架構。

抽象概念表示，DevOps 小組不需要佈建或管理伺服器或特定的容器。 無伺服器平台主機程式碼，做為指令碼或封裝的可執行檔以相關的 SDK，建置，並配置的程式碼來調整所需的資源。

下圖的圖表四個的無伺服器元件。 HTTP 要求會導致執行簽出 API 程式碼。 簽出 API 會將程式碼插入資料庫中，並執行插入觸發程序的數個其他函式來執行工作，例如運算工作和履行的訂單。

![無伺服器的實作](./media/serverless-implementation.png)

無伺服器的優點包括：

* **高的密度。** 相較於容器或虛擬機器在相同主機上，可以執行許多相同的無伺服器程式碼的執行個體。 跨多個主機向外延展和恢復功能的執行個體小數位數。
* **Micro 計費**。 根據無伺服器的執行，以便將節省大量成本在某些情況下最無伺服器的提供者帳單。
* **立即調整**。 無伺服器可調整以符合工作負載，自動並快速。
* **加速上市時間，** 開發人員專注於程式碼，並將直接部署到無伺服器平台。 元件可以彼此釋放。

無伺服器計算內容中最常討論，但也可以套用至資料。 例如， [Azure SQL](https://docs.microsoft.com/azure/sql-database)並[Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)兩者都提供不需要您設定主機電腦或叢集的雲端資料庫。 這本書，著重於無伺服器計算。

## <a name="summary"></a>總結

沒有廣泛的架構，包括混合式方法的可用選項。 方法、 管理和成本的代價是控制項和可攜性的應用程式功能，可簡化無伺服器。 不過，許多的無伺服器平台，並公開設定，以協助調整解決方案。 可攜性的程式碼以及較無伺服器平台鎖定中，也可能會導致的良好程式設計作法。 下表說明的架構方法並存。 選擇無伺服器根據您的擴展需求、 在您想要管理的執行階段和程度您可以讓您的工作負載分成小型的元件。 您將了解潛在的挑戰，使用無伺服器和下一步 一章中的其他決策點。

|         |IaaS     |PaaS     |容器|無伺服器|
|---------|---------|---------|---------|----------|
|**縮放**|VM       |執行個體 |應用程式      |功能  |
|**Abstracts**|硬體|Platform|作業系統的主機|執行階段   |
|**Unit** |VM       |專案  |Image    |程式碼      |
|**存留期**|幾個月|月份的天數|天前的分鐘|分鐘的時間 （毫秒)|
|**責任**|應用程式、 相依性、 執行階段和作業系統|應用程式和相依性|應用程式、 相依性，以及執行階段|功能

* **擴展**指的是用來調整應用程式的單位
* **抽象化**所實作的抽象的層級是指
* **單位**指的是部署的內容範圍
* **存留期**指的是典型的執行階段的特定執行個體
* **責任**指的是建置、 部署及維護應用程式的額外負荷

下一步 一章將焦點放在無伺服器架構、 使用案例和設計模式。

## <a name="recommended-resources"></a>建議的資源

* [Azure 應用程式架構指南](https://docs.microsoft.com/azure/architecture/guide/)
* [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
* [Azure SQL](https://docs.microsoft.com/azure/sql-database)
* [多層式架構模式](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
* [在 Azure 上的 Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes)
* [Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
* [虛擬機器的多層式架構參考架構](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
* [虛擬機器](https://docs.microsoft.com/azure/virtual-machines/)
* [什麼是 Docker？](../microservices-architecture/container-docker-introduction/docker-defined.md)
* [Wingtip Tickets SaaS 應用程式](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[上一頁](architecture-approaches.md)
>[下一頁](serverless-architecture.md)