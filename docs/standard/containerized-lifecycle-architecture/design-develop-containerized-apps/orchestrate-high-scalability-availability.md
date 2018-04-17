---
title: 協調 microservices 及 multicontainer 應用程式的高延展性和可用性
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 92bfd4516866fe82408dd3dd341a13db0ee216c0
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>協調 microservices 及 multicontainer 應用程式的高延展性和可用性

如果您的應用程式是以微服務為基礎或分散於多個容器，您就必須為適用於生產環境的應用程式使用協調器。 如之前所介紹，以微服務為基礎的方法中，每個微服務都擁有自己的模型和資料，因此從開發和部署的角度來看，它是非常自主的。 但是，即使您擁有更傳統的應用程式所組成的多個服務 （例如 SOA)，您也會有多個容器或組成單一商務應用程式中需要部署為分散式系統的服務。 這類系統很複雜向外擴充和管理。因此，您一定需要 orchestrator 如果您想要已備妥且可延展 multicontainer 應用程式。

圖 4-6 說明到叢集中的多個 microservices （容器） 所組成的應用程式的部署。

![](./media/image6.png)

圖 4-6： 在叢集的容器

看起來像邏輯方法。 不過，如何為您處理負載平衡、 路由及協調這些組成的應用程式嗎？

Docker 命令列介面 (CLI) 符合管理一部的主機上的一個容器的需求，但它會管理更複雜的分散式應用程式的多個主機上部署的多個容器時落簡短。 在大部分情況下，您需要的管理平台會自動啟動容器、 暫止，或關閉它們需要時，並在理想情況下也控制存取資源，例如網路及儲存資料的方式。

如果您不只要管理個別容器或組成非常簡單的應用程式，而是要進展到含有微服務的大型企業應用程式，就必須採用協調流程和叢集平台。

從架構和開發觀點來看，如果您建置大型的企業，microservices 為基礎的應用程式，很一定要了解下列平台和產品可支援進階的案例：

-   **叢集和 orchestrators** 當您需要調整-out 跨 Docker 主機數目太多的應用程式，例如大型 microservices 型應用程式，以相當重要，能夠與由單一叢集管理所有的主機抽象化基礎平台的複雜性。 而這正是容器叢集和協調器所提供的功能。 Orchestrators 範例包括 Docker Swarm、 Mesosphere DC/OS、 Kubernetes （前三個可透過 Azure 容器服務） 和 Azure Service Fabric。

-   **排程器** *排程*表示系統管理員，才能啟動叢集中的容器，讓它們也提供使用者介面的功能。 叢集的排程器有多項責任： 有效率地使用叢集的資源設定使用者，有效率地跨主機或節點負載平衡容器所提供的條件約束，是錯誤的穩固同時提供高可用性。

叢集與排程器的概念密切相關，因此不同廠商所提供的產品通常會兩組功能都提供。 表 4-1 列出的最重要的平台和軟體選擇您的叢集和排程器。 這些叢集通常會提供如 Azure 公用雲端中。

表 4-1： 群集的容器、 協調流程，和排程的軟體平台

| 平台 | 描述 |
|---|---|
| Docker Swarm<br/> ![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image7.png) | Docker 群集會提供叢集和排程 Docker 容器的能力。 使用 Swarm 時，您可以將 Docker 主機集區轉換成單一的虛擬 Docker 主機。 用戶端可以進行相同的方式表示，群集輕鬆的應用程式擴充至多部主機的主機進行應用程式開發介面要求群集。 <br /><br /> Docker Swarm 是 Docker 公司的產品。 <br /><br /> Docker v1.12 或更新版本可以執行原生與內建的 Swarm 模式。 |
| Mesosphere DC/OS<br/>![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image8.png) |  Mesosphere Enterprise DC/OS (以 Apache Mesos 為基礎) 是一種適用於生產環境的平台，可執行容器和分散式應用程式。 <br /><br /> DC/OS 的運作方式是將叢集中可用的資源集合簡化，讓這些資源可供建置其上的元件使用。 Marathon 通常作為與 DC/OS 整合的排程器。 |
| Google Kubernetes<br />![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image9.png) | Kubernetes 是開放原始碼產品，可提供叢集基礎結構、容器排程到容器協調等功能。 有了它，您可以自動化部署、 調整及應用程式容器的作業在叢集中的主機。 <br /><br /> Kubernetes 提供以容器為中心的基礎結構，讓您將應用程式容器分組為邏輯單元，以便於管理及探索。 |
| Azure Service Fabric<br />![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image10.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) 是一種 Microsoft 微服務平台，可用來建置應用程式。 它是一種服務的[協調器](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)，並可建立電腦叢集。 根據預設，Service Fabric 部署並啟動服務以處理序，但是 Service Fabric 可以部署在 Docker 容器映像中的服務。 更重要的是，您可以與服務相同的應用程式中的容器中混合處理序中的服務。 <br /><br /> 可能 2017 年 Service Fabric 支援部署服務 」 做為 Docker 容器的功能處於預覽狀態。 <br /><br /> 您可以開發在許多方面，使用從 Service Fabric 服務[程式設計模型的 Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)部署[客體可執行檔](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app)以及容器。 Service Fabric 支援規定的應用程式模型，像[可設定狀態服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)和[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)。

## <a name="using-container-based-orchestrators-in-azure"></a>在 Azure 中使用容器型 orchestrators

許多雲端廠商提供 Docker 容器支援加上 Docker 叢集和協調流程的支援，包括 Azure、 Amazon EC2 容器服務和 Google 容器引擎。 Azure 提供的 Docker 叢集和 orchestrator 支援透過 Azure 容器服務下, 一節中所述。

另一個選擇是使用 Azure Service Fabric 也支援根據 Linux 與 Windows 容器的 Docker。 Service Fabric 執行 Azure 或任何其他雲端上如[內部](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)。

## <a name="using-azure-container-service"></a>使用 Azure Container Service

Docker 叢集裝載了多部 Docker 主機，並將其公開為單一虛擬 Docker 主機，因此您可以部署多個容器到該叢集中。 叢集會處理所有複雜的管理配管例如延展性和健全狀況。 圖 4-7 代表容器服務組成的應用程式的 Docker 叢集中的對應方式。

容器服務可用來簡化建立、 設定及管理叢集的執行容器化應用程式已預先設定的 Vm。 使用最佳化的組態的熱門的開放原始碼排程和協調流程工具，容器服務可讓您使用現有的技術或社群專業能力來部署和管理容器基礎大量且不斷主體上繪製Azure 中的應用程式。

容器服務進行最佳化熱門 Docker 群集的開放原始碼工具和技術的組態，特別針對 Azure。 這樣的開放解決方案，可賦予您容器和應用程式組態的可攜性。 您只要選取主機大小和數目，其餘工作全都由協調器工具和 Container Service 處理。

容器服務會確保您的應用程式容器可完整移植使用 Docker 映像。 它支援的開放原始碼的協調流程等 DC/OS、 Kubernetes，和 Docker Swarm 的平台的選擇，以確保這些應用程式可以擴充到數千、 數萬甚至數千張的容器。

Azure 容器服務時，您可以利用 Azure 的企業級功能仍然維持應用程式可攜性，包括協調流程層級。

![](./media/image11.png)

圖 4-7： 叢集 Azure 容器服務中的選項

所示圖 4-8，容器服務是只是為了部署 DC/OS、 Kubernetes，或 Docker Swarm，Azure 提供的基礎結構，但未實作任何其他 orchestrator。 因此，容器服務是不 orchestrator，在這種情況。它是利用現有的開放原始碼 orchestrators 容器的基礎結構。

![](./media/image12.png)

圖 4-8: Orchestrators 中容器服務

使用方式的觀點而言，容器服務的目標是提供容器的裝載環境使用熱門的開放原始碼工具和技術。 為此，它會為您所選擇的協調器公開標準的 API 端點。 藉由使用這些端點，您可以使用能與這些端點通訊的任何軟體。 比方說，在 Docker Swarm 結束點的情況下，您可能會選擇使用 Docker CLI。 若是 DC/OS，您可能會選擇使用 DC/OS CLI。

### <a name="getting-started-with-container-service"></a>開始使用容器服務

若要開始使用容器服務，您部署使用 Azure Resource Manager 範本從 Azure 入口網站的容器服務叢集或[CLI](https://docs.microsoft.com/cli/azure/install-azure-cli)。 可用的範本包括 [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm)、[Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes) 和 [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos)。 您可以修改要包含其他或進階的 Azure 組態的快速入門範本。

**進一歩** 若要深入了解部署的容器服務叢集中，Azure 網站上，閱讀[部署 Azure 容器服務叢集](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment)。

隨附於 ACS 預設安裝的軟體均不會收取任何費用。 所有預設選項都是使用開放原始碼軟體來實作。

目前使用標準的、 D、 DS、 G 及 GS 系列 Linux Vm 在 Azure 中容器服務。 您只支付您選擇其他基礎基礎結構使用的資源，例如儲存體和網路功能以及計算執行個體。 沒有任何增量費用容器服務本身。

### <a name="additional-resources"></a>其他資源

以下是您可以在此找到其他資訊的位置：

-   裝載容器服務方案的 Docker 容器簡介：  
    https://docs.microsoft.com/azure/container-service/kubernetes/container-service-intro-kubernetes>

-   Docker 群集概觀：  
    <https://docs.docker.com/swarm/overview/>

-   群集模式概觀：  
    <https://docs.docker.com/engine/swarm/>

-   Mesosphere DC/OS 概觀：    
    <https://docs.mesosphere.com/1.7/overview/>

-   Kubernetes （官方站台）：  
    <http://kubernetes.io/>

## <a name="using-service-fabric"></a>使用 Service Fabric

Service Fabric 會發生從傳遞給傳遞服務的 「 方塊 」 產品，已通常龐大樣式中，從 Microsoft 的轉換。 建立及操作大型小數位數，例如 Azure SQL Database、 Azure 文件 DB、 Azure 服務匯流排、 或 Cortana 的後端中，在服務的經驗形狀 Service Fabric。 越來越多的服務採用與時俱進的平台。 重要的是，Service Fabric 不僅必須能在 Azure 中執行，還必須能在獨立的 Windows 伺服器部署中執行。

Service Fabric 的目的是解決建置及執行服務，讓小組可以解決商務問題使用 microservices 的方式，有效率地使用基礎結構資源的困難的問題。

Service Fabric 提供兩大區域，協助您建置使用微服務的應用程式：

-   平台，提供系統服務以部署、調整、升級、偵測及重新啟動失敗的服務、探索服務位置、管理狀態，以及監視健康狀態。 這些系統服務作用中提供的許多 microservices 先前所述的特性。

-   程式設計 API 或架構，可協助您將應用程式建置為微服務：[可靠的執行者與可靠的服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)。 當然，您可以選擇任何程式碼來建置您的微服務，但是這些 API 能讓工作更簡單，與平台深入整合。 如此一來，您就可以取得健康狀態和診斷資訊，或者可以利用穩定的狀態管理。

Service Fabric 不在乎您用什麼方法來建置服務，所以您可以使用任何技術。 不過，它會提供內建的程式設計 API，讓您更輕鬆地建置微服務。

圖 4 至 9 示範如何建立和執行 microservices 服務網狀架構中，以簡單的程序或 Docker 容器。 它也可以將容器型微服務與程序型微服務混合在相同的 Service Fabric 叢集中。

![](./media/image13.png)

圖 4-9： 部署 microservices，做為處理序，或做為 Azure Service Fabric 中的容器

Service Fabric 叢集基礎 Linux 和 Windows 主機上可以執行 Docker Linux 容器和 Windows 容器。

**進一歩** 有關最新 Service Fabric 中的容器支援 Azure 網站上，閱讀[Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

Service Fabric 是與您可以定義的實體實作於不同邏輯架構 （商務 microservices 或繫結的內容） 的平台的良好範例。 例如，如果您實作[Stateful Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)中[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)下, 一節中引進的 「[無狀態與可設定狀態 microservices](#stateless-versus-stateful-microservices)，「 您有商務微服務概念與多個實體的服務。

圖 4-10 和商務邏輯/微服務的觀點而言，實作服務網狀架構可設定狀態 Reliable Service 時考慮中所示，您通常必須實作兩個服務層。 第一個是後端可設定狀態可靠服務，用來處理多個資料分割。 第二項是前端服務，或稱閘道服務，負責跨多個分割或具狀態服務執行個體的路由及資料彙總。 閘道服務也會處理用戶端通訊重試迴圈存取後端服務搭配使用以 Service Fabric[反向 proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)。

![](./media/image14.png)

圖 4-10： 商務微服務與 Service Fabric 的數個可設定狀態，而且無狀態服務

在任何情況下，當您使用 Service Fabric 具狀態可靠服務時，您也會有邏輯或商務微服務 (繫結的內容)，它通常是由多項實體服務組成。 其中的閘道服務和服務磁碟分割的每個無法實作為 ASP.NET Web API 服務，如圖 4-10 所示。

在 Service Fabric 中，您可以分組服務，並將這些服務群組部署為 [Service Fabric 應用程式](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)，這是協調器或叢集的封裝和部署單位。 因此，Service Fabric 應用程式無法對應到此自發的商務和邏輯的微服務界限或繫結的內容，以及。

### <a name="service-fabric-and-containers"></a>Service Fabric 和容器

關於 Service Fabric 中的容器，您也可以部署 Service Fabric 叢集內的容器映像中的服務。 圖 4-11 說明，大部分的將只有一個容器，每個服務的時間。

![](./media/image15.png)

圖 4-11： 商務微服務與服務的網狀架構中的數個服務 （容器）

不過，也是服務的服務網狀架構中可能有所謂的 「 sidecar"容器 （必須為邏輯的一部分一起部署的兩個容器）。 重點是商務微服務是圍繞數個緊密結合項目的邏輯界限。 在許多情況下，它可能會使用單一資料模型時，單一服務，但在某些情況下，您可能會有實體數個服務，以及。

為準，此撰寫 (年 4 月 2017)，在 Service Fabric 您無法部署容器 SF 可靠可設定狀態服務，您可以部署客體容器、 無狀態服務或在容器中的動作項目服務。 但請注意，您可以混合中相同的 Service Fabric 應用程式中的容器處理序中的服務和服務如圖 4-12 版中所示。

![](./media/image16.png)

圖 4-12： 商務微服務對應至容器和可設定狀態服務的 Service Fabric 應用程式

也不同，視您使用的 Docker 容器在 Linux 或 Windows 容器支援。 Service Fabric 中容器的支援將擴充在即將發行版本。 如需在 Azure 網站中，Service Fabric 容器支援的最新消息讀取[Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

## <a name="stateless-versus-stateful-microservices"></a>無狀態微服務與具狀態微服務

如前所述，每項微服務 (邏輯繫結的內容) 都必須擁有其網域模型 (資料和邏輯)。 在無狀態 microservices，資料庫將會是外部，採用關聯式的選項，例如 SQL Server 或如 MongoDB 或 Azure DocumentDB 的 NoSQL 選項。

但是，服務本身也可以是可設定狀態，這表示資料所在的微服務。 這項資料可能存在不只是在相同伺服器上，但在微服務處理序，在記憶體中，內保存在磁碟機上和複寫到其他節點。 圖 4-13 顯示不同的方法。

![](./media/image17.png)

圖 4-13： 無狀態與可設定狀態的 microservices

無狀態的方法是完全有效，而且您更輕鬆地實作可設定狀態的 microservices 比，因為方法是類似於傳統和已知的模式。 但無狀態微服務會強制程序及資料來源之間的延遲。 當您嘗試使用額外的快取和佇列改善效能時，它們也牽涉到更多移動的片段。 您最後會得到有太多層的複雜架構。

相反地，[可設定狀態的 microservices](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)可以進階案例中，excel，因為沒有任何網域邏輯和資料之間的延遲。 大量的資料處理，遊戲的後端，資料庫服務，以及其他所有受益於可設定狀態服務，可以提供更快速存取本機狀態的低延遲案例。

無狀態與具狀態服務是互補的。 比方說，可設定狀態的服務可能會分割成多個資料分割。 若要存取這些分割，您可能需要作為閘道服務的無狀態服務，它知道如何根據分割索引鍵處理每個分割。

具狀態服務確實有缺點。 強制複雜性，讓向外延展的層的級。本來通常由外部資料庫系統實作的工作功能，例如跨具狀態微服務和資料分割的資料複寫，必須予以處理。 不過，這是其中一個區域 orchestrator 想在哪裡[Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture)與其[可設定狀態的可靠服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)最有助於 — 藉由簡化開發和生命週期的可設定狀態使用 microservices[可靠的服務應用程式開發介面](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections)和[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)。

其他允許具狀態服務、支援執行者模式，以及改善商務邏輯和資料間容錯和延遲的微服務架構是 Microsoft [Orleans](https://github.com/dotnet/orleans)，來自 Microsoft 研究，以及 [Akka.NET](http://getakka.net/)。 這兩種架構目前都在改善它們對 Docker 的支援。

請注意，Docker 容器本身無狀態。 如果您想要實作具狀態服務，您需要前述的規範及較高層級架構之一。 不過，撰寫本文時，可設定狀態的服務，Service Fabric 中不支援做為容器，只能當做一般 microservices。 在容器中的可靠的服務支援可在即將推出的 Service Fabric 版本中。


>[!div class="step-by-step"]
[上一個] (soa-applications.md) [下一步] (docker-應用程式層開發-environment.md)
