---
title: "使用 Azure Service Fabric"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 使用 Azure Service Fabric"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9480a3f67e9d0a61d0669bf34be4b66208f5e9ce
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="using-azure-service-fabric"></a>使用 Azure Service Fabric

Azure Service Fabric 的前身是自傳遞方塊產品轉換而來的 Microsoft，這些產品通常會整合傳遞服務的樣式。 建置及操作 Azure SQL Database、Azure Cosmos DB、Azure 服務匯流排或 Cortana 後端等大規模大型服務的體驗，形成了 Service Fabric。 越來越多的服務採用與時俱進的平台。 重要的是，Service Fabric 不僅必須能在 Azure 中執行，還必須能在獨立的 Windows 伺服器部署中執行。

Service Fabric 的目標是解決建置和執行服務以及有效率使用基礎結構資源的難題，讓小組可以使用微服務方法解決商務問題。

Service Fabric 提供兩大區域，協助您建置使用微服務的應用程式：

-   平台，提供系統服務以部署、調整、升級、偵測及重新啟動失敗的服務、探索服務位置、管理狀態，以及監視健康狀態。 這些系統服務能夠發揮前述微服務的許多特性。

-   程式設計 API 或架構，可協助您將應用程式建置為微服務：[可靠的執行者與可靠的服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)。 當然，您可以選擇任何程式碼來建置您的微服務，但是這些 API 能讓工作更簡單，與平台深入整合。 如此一來，您就可以取得健康狀態和診斷資訊，或者可以利用穩定的狀態管理。

Service Fabric 不在乎您用什麼方法來建置服務，所以您可以使用任何技術。 不過，它會提供內建的程式設計 API，讓您更輕鬆地建置微服務。

如圖 4-26 所示，您可以在 Service Fabric 中建立微服務，當成簡單的程序或 Docker 容器執行。 它也可以將容器型微服務與程序型微服務混合在相同的 Service Fabric 叢集中。

![](./media/image30.png)

**圖 4-26**。 在 Azure Service Fabric 中將微服務部署為處理序或容器

以 Linux 和 Windows 主機為基礎的 Service Fabric 叢集，可以分別執行 Docker 的 Linux 容器和 Windows 容器。

如需 Azure Service Fabric 容器支援的最新資訊，請參閱 [Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

Service Fabric 是很好的平台範例，您可在此定義與實體實作不相同的邏輯架構 (商務微服務或繫結的內容)，有關實體實作的介紹請參閱[邏輯架構與實體架構](#logical-architecture-versus-physical-architecture)一節。 例如，如果您實作 [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) 的[具狀態可靠服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) (稍後[無狀態與具狀態的微服務](#stateless-versus-stateful-microservices)一節會介紹)，您就可以擁有具備多項實體服務的商業微服務概念。

如圖 4-27 所示，就邏輯/商務微服務的觀點而言，實作 Service Fabric 具狀態可靠服務時，您通常需要實作兩層服務。 第一項是後端具狀態可靠服務，處理多個分割 (每個分割都是一項具狀態服務)。 第二項是前端服務，或稱閘道服務，負責跨多個分割或具狀態服務執行個體的路由及資料彙總。 閘道服務也會使用存取後端服務的重試迴圈，處理用戶端通訊。
如果您實作您的自訂服務，它就稱為閘道服務；或者您也可以使用立即可用的 Service Fabric [反向 Proxy 服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)。

![](./media/image31.png)

**圖 4-27**。 使用數個具狀態服務執行個體和自訂閘道前端的商務微服務

在任何情況下，當您使用 Service Fabric 具狀態可靠服務時，您也會有邏輯或商務微服務 (繫結的內容)，它通常是由多項實體服務組成。 閘道服務和磁碟分割服務每一個都可實作為 ASP.NET Web API 服務，如圖 4-26 所示。

在 Service Fabric 中，您可以分組服務，並將這些服務群組部署為 [Service Fabric 應用程式](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)，這是協調器或叢集的封裝和部署單位。 因此，Service Fabric 應用程式也可以對應到此自發商務邏輯微服務界限或繫結內容，以便您自主部署這些服務。

## <a name="service-fabric-and-containers"></a>Service Fabric 和容器

至於 Service Fabric 的容器，您也可以在 Service Fabric 叢集內的容器映像中部署服務。 如圖 4-28 所示，每項服務大部分時候都只有一個容器。

![](./media/image32.png)

**圖 4-28**。 Service Fabric 中使用數個服務 (容器) 的商務微服務

不過，Service Fabric 也可能有所謂的「側車」容器 (必須一起部署為邏輯一部分的兩個容器)。 重點是商務微服務是圍繞數個緊密結合項目的邏輯界限。 在許多情況下，它可能是使用單一資料模型的單一服務，但在其他一些情況下，您可能也會有數項實體服務。

截至 2017 年中，您無法在 Service Fabric 中將 SF 可靠具狀態服務部署到容器上，只能在容器中部署無狀態服務和執行者服務。 但請注意，您可以在相同的 Service Fabric 應用程式中混合處理序的服務和容器的服務，如圖 4-29 所示。

![](./media/image33.png)

**圖 4-29**。 對應至具有容器和具狀態服務之 Service Fabric 應用程式的商務微服務

如需 Azure Service Fabric 容器支援的詳細資訊，請參閱 [Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

## <a name="stateless-versus-stateful-microservices"></a>無狀態微服務與具狀態微服務

如前所述，每項微服務 (邏輯繫結的內容) 都必須擁有其網域模型 (資料和邏輯)。 在無狀態微服務的案例中，資料庫會是外部的，採用如 SQL Server 的關聯式選項，或採用如 MongoDB 或 Azure Cosmos DB 的 NoSQL 選項。

但是服務本身在 Service Fabric 中也可以具狀態，這表示資料位在微服務內。 這項資料可能不只存在於相同的伺服器，也存在微服務程序、記憶體內部，並保存在硬碟上，會複寫到其他節點。 圖 4-30 顯示不同的方法。

![](./media/image34.png)

**圖 4-30**。 無狀態微服務與具狀態微服務

無狀態方法完全有效，而且比具狀態微服務更容易實作，因為方法類似於傳統和已知的模式。 但無狀態微服務會強制程序及資料來源之間的延遲。 當您嘗試使用額外的快取和佇列改善效能時，它們也牽涉到更多移動的片段。 您最後會得到有太多層的複雜架構。

相反地，[具狀態微服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)在進階案例中勝出，因為網域邏輯和資料之間沒有任何延遲。 大量的資料處理、競先搶回終點、資料庫即服務，以及其他低延遲狀況皆得益於具狀態服務，它讓本機狀態可供更快速存取。

無狀態與具狀態服務是互補的。 例如，您可以在圖 4-30 的右邊圖表中看到，具狀態服務可分割成多個分割。 若要存取這些分割，您可能需要作為閘道服務的無狀態服務，它知道如何根據分割索引鍵處理每個分割。

具狀態服務確實有缺點。 它們會強制施行某種程度的複雜性，以向外延展。本來通常由外部資料庫系統實作的工作功能，例如跨具狀態微服務和資料分割的資料複寫，必須予以處理。 不過，這是像 [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) 這類的協調器及其[具狀態可靠服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)提供最多幫助的其中一個區域，方法是使用[可靠的服務 API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) 和 [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction) 簡化開發和具狀態微服務的生命週期。

其他允許具狀態服務、支援執行者模式，以及改善商務邏輯和資料間容錯和延遲的微服務架構是 Microsoft [Orleans](https://github.com/dotnet/orleans)，來自 Microsoft 研究，以及 [Akka.NET](http://getakka.net/)。 這兩種架構目前都在改善它們對 Docker 的支援。

請注意，Docker 容器本身無狀態。 如果您想要實作具狀態服務，您需要前述的規範及較高層級架構之一。 

>[!div class="step-by-step"]
[上一頁] (scalable-available-multi-container-microservice-applications.md) [下一頁] (../docker-application-development-process/index.md)
