---
title: "使用 Azure Service Fabric"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |使用 Azure Service Fabric"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: aa15f9cf9bc60e9e70607da921f2ce2c75e39ec2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="using-azure-service-fabric"></a>使用 Azure Service Fabric

Azure Service Fabric 會從 Microsoft 的來回轉換傳遞方塊產品是通常在樣式中整合，實現服務發生。 建立及操作大型小數位數，例如 Azure SQL Database、 Azure Cosmos DB、 Azure 服務匯流排、 或 Cortana 的後端中，在服務的經驗形狀 Service Fabric。 平台會歷經時間越來越多的服務採用它。 重要的是，Service Fabric 必須執行而不只是在 Azure 中獨立 Windows 伺服器部署中。

Service Fabric 的目的是，讓小組可以解決商務問題使用 microservices 方法解決艱難問題的建置和執行服務和有效率地使用基礎結構資源。

Service Fabric 提供兩個廣泛的區域，可協助您建置應用程式，請使用 microservices 方法：

-   平台，提供系統服務部署、 調整、 升級、 偵測，並重新啟動失敗的服務、 探索服務的位置，管理狀態，以及監視健全狀況。 這些系統服務作用中實現許多 microservices 先前所述的特性。

-   程式設計 Api 或架構，可協助您建置應用程式為 microservices:[可靠執行者與可靠的服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)。 當然，您可以選擇任何程式碼來建置您的微服務，但是這些 Api，讓工作更簡單，而且更深層級的平台整合。 如此一來，您可以取得健康情況和診斷資訊，或您可以利用穩定的狀態管理。

相對於您如何建置您的服務，Service Fabric 無關，而且您可以使用任何技術。 不過，它會提供內建的程式設計 Api，讓您更輕鬆地建置 microservices。

如所示圖 4-26，您可以建立及執行 microservices 服務網狀架構中，以簡單的程序或 Docker 容器。 它也可混合使用容器型 microservices 與程序為基礎的 microservices 相同的 Service Fabric 叢集中。

![](./media/image30.png)

**圖 4-26**。 部署 microservices，做為處理序，或做為 Azure Service Fabric 中的容器

Service Fabric 叢集基礎 Linux 和 Windows 主機上可以執行 Docker Linux 容器和 Windows 容器，分別。

最新 Azure Service Fabric 中的容器支援的詳細資訊，請參閱[Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

Service Fabric 是不錯的範例，為平台可讓您定義是以不同邏輯架構 （商務 microservices 或繫結的內容） 中導入的實體實作比[邏輯與實體架構架構](#logical-architecture-versus-physical-architecture)> 一節。 例如，如果您實作[Stateful Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)中[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)，這一節中導入[無狀態與可設定狀態的 microservices](#stateless-versus-stateful-microservices)稍後，您可以讓商業微服務概念與多個實體的服務。

圖 4-27 和商務邏輯/微服務的觀點而言，實作服務網狀架構可設定狀態 Reliable Service 時考慮中所示，您通常必須實作兩個服務層。 第一個是後端可設定狀態可靠服務，用來處理多個資料分割 （每個資料分割是可設定狀態的服務）。 第二個是前端服務或閘道器服務，橫跨多個資料分割或可設定狀態的服務執行個體的路由及資料彙總負責。 閘道服務也會處理重試迴圈存取後端服務的用戶端通訊。
如果您實作您的自訂服務或您也可以使用的方塊外 Service Fabric alternatevely 呼叫閘道服務[反向 Proxy 服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)。

![](./media/image31.png)

**圖 4-27**。 使用數個可設定狀態的服務執行個體和自訂閘道前端商務微服務

在任何情況下，當您使用服務網狀架構 Stateful Reliable Services 時，您也可以邏輯或商務微服務 （繫結的內容） 通常由組成的多個實體的服務。 其中的閘道服務和服務磁碟分割的每個無法實作為 ASP.NET Web API 服務，如圖 4-26 所示。

服務網狀架構中，您可以群組及部署的服務做為群組[Service Fabric 應用程式](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)，這是封裝和部署 orchestrator 或叢集的單位。 因此，Service Fabric 應用程式無法對應到此自發的商務邏輯的微服務界限或繫結內容中，也讓您可以自發部署這些服務。

## <a name="service-fabric-and-containers"></a>Service Fabric 和容器

關於 Service Fabric 中的容器，您也可以部署 Service Fabric 叢集內的容器映像中的服務。 如圖 4-28 所示，大部分的情況下只會有一個容器，每個服務。

![](./media/image32.png)

**圖 4-28**。 商務微服務與服務的網狀架構中的數個服務 （容器）

不過，也是服務的服務網狀架構中可能有所謂的 「 sidecar"容器 （必須為邏輯的一部分一起部署的兩個容器）。 商務微服務是數種凝聚的項目周圍的邏輯界限是重要的事情。 在許多情況下，它可能會使用單一資料模型時，單一服務，但在某些情況下您可能也有數個服務實體。

從 mid 2017，開始，您也無法在 Service Fabric 中部署容器 SF 可靠可設定狀態服務，您可以只部署無狀態服務 」 和 「 動作項目容器中的服務。 但請注意您可以混合在處理序中的服務和服務在相同的 Service Fabric 應用程式中的容器中所示圖 4-29。

![](./media/image33.png)

**圖 4-29**。 對應至容器和可設定狀態服務的 Service Fabric 應用程式的商務微服務

如需有關 Azure Service Fabric 中的容器支援的詳細資訊，請參閱[Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

## <a name="stateless-versus-stateful-microservices"></a>無狀態與可設定狀態的 microservices

如先前所述，每個微服務 （邏輯繫結的內容） 必須擁有其網域模型 （資料和邏輯）。 在無狀態 microservices，資料庫將會是外部，採用關聯式的選項，例如 SQL Server 或 NoSQL 選項，例如 MongoDB 或 Azure Cosmos DB。

但是，服務本身也可以在服務網狀架構中，這表示資料所在的微服務內可設定狀態。 這項資料可能存在不只是在相同伺服器上，但在微服務程序，在記憶體中保存在硬碟上和複寫到其他節點。 圖 4-30 顯示不同的方法。

![](./media/image34.png)

**圖 4-30**。 無狀態與可設定狀態的 microservices

無狀態的方法是完全有效，而且比容易實作可設定狀態 microservices，因為方法是類似於傳統和已知的模式。 但無狀態 microservices 強制程序及資料來源之間的延遲。 當您嘗試以改善效能，使用其他快取和佇列時，它們也牽涉到更移動棋子。 結果是，您可以以結束複雜有太多層的架構。

相反地，[可設定狀態的 microservices](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)可以在進階案例中，excel，因為沒有任何網域邏輯和資料之間的延遲。 大量的資料處理回遊戲結束，為服務時，資料庫和所有其他低延遲實例受益可設定狀態服務，可讓更快速存取本機狀態。

無狀態與可設定狀態服務是互補的。 比方說，您可以看到在圖 4-30，在右邊的圖表中，可設定狀態的服務可能會分割成多個資料分割。 若要存取這些資料分割，您可能需要無狀態服務，做為閘道服務知道如何處理每個資料分割索引鍵為基礎的資料分割。

可設定狀態的服務沒有缺點。 強制複雜性，讓使用者能夠向外延展的層的級。通常會由外部資料庫的系統實作的功能必須處理的工作，例如資料複寫，可設定狀態的 microservices 與資料分割的資料。 不過，這是其中一個區域 orchestrator 想在哪裡[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture)與其[可設定狀態的可靠服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)最有助於 — 藉由簡化開發和生命週期的可設定狀態使用 microservices[可靠的服務應用程式開發介面](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections)和[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)。

允許可設定狀態的服務、 支援的動作項目模式，以及改善容錯和商務邏輯和資料之間的延遲其他微服務架構是 Microsoft[奧良](https://github.com/dotnet/orleans)，從 Microsoft Research 及[Akka.NET](http://getakka.net/)。 目前，這兩種架構可改善其對 Docker 的支援。

請注意，Docker 容器本身就是無狀態。 如果您想要實作可設定狀態的服務，您需要其中一個其他慣用且較高層級架構先前所述。 

>[!div class="step-by-step"]
[上一個](scalable-available-multi-container-microservice-applications.md) [下一步] (.../docker-application-development-process/index.md)
