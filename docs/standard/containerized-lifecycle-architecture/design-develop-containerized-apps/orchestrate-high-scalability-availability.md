---
title: 協調微服務和多容器應用程式的高延展性和可用性
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: fa64562808bba9c9dea5a5eedc367af7decf83b7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126896"
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>協調微服務和多容器應用程式的高延展性和可用性

如果您的應用程式是以微服務為基礎或分散於多個容器，您就必須為適用於生產環境的應用程式使用協調器。 如之前所介紹，以微服務為基礎的方法中，每個微服務都擁有自己的模型和資料，因此從開發和部署的角度來看，它是非常自主的。 但是，即使您擁有更傳統的應用程式所組成的多個服務 （例如 SOA)，您也會有多個容器或服務來組成單一商務應用程式需要部署為分散式系統。 這類系統相當複雜，向外延展和管理;因此，您一定需要協調器如果您想要有一個生產環境且可延展的多容器應用程式。

圖 4-6 說明叢集中的多個微服務 （容器） 所組成的應用程式的部署。

![](./media/image6.png)

圖 4-6:容器叢集

看起來像邏輯方法。 但如何您處理負載平衡、 路由及協調這些組成應用程式嗎？

Docker 命令列介面 (CLI) 符合的需求管理一部的主機上的一個容器，但管理更複雜的分散式應用程式的多個主機上部署的多個容器時，它是簡短。 在大部分情況下，您需要的管理平台，可自動啟動容器、 暫止，或關閉它們需要時，及最好也能控制其存取資源，像是網路及資料的儲存體的方式。

如果您不只要管理個別容器或組成非常簡單的應用程式，而是要進展到含有微服務的大型企業應用程式，就必須採用協調流程和叢集平台。

從架構設計和開發觀點來看，如果您是建置大型的企業，微服務架構應用程式，務必了解下列平台和產品可支援進階的案例：

-   **叢集和協調器** 當您需要調整-out 跨許多 Docker 主機的應用程式，例如大型微服務型應用程式中，務必要能夠管理所有這些主機與由單一叢集抽象化基礎平台的複雜性。 這就是容器叢集和協調器提供的內容。 Orchestrator 的例子是 Docker Swarm、 Mesosphere DC/OS、 Kubernetes （前三個可透過 Azure Container Service） 和 Azure Service Fabric。

-   **排程器** *排程*表示要讓系統管理員啟動叢集中的容器，以便它們也提供使用者介面的功能。 叢集排程器有下列職責： 有效率地使用叢集的資源、 設定使用者，以有效率地跨節點或主機，進行容器負載平衡所提供的條件約束及具容錯性，同時提供最高可用性。

叢集與排程器的概念密切相關，因此不同廠商所提供的產品通常會兩組功能都提供。 表 4-1 列出的最重要的平台和您的叢集和排程器的軟體選項。 這些叢集通常都有提供這類 Azure 公用雲端。

表 4-1:用於容器叢集、協調流程和排程的軟體平台

| Platform | 描述 |
|---|---|
| Docker Swarm<br/> ![Docker Swarm 標誌](./media/image7.png) | Docker Swarm 可讓您能夠進行叢集與排程的 Docker 容器。 使用 Swarm 時，您可以將 Docker 主機集區轉換成單一的虛擬 Docker 主機。 用戶端可以對 Swarm 提出 API 要求向主機，這表示，Swarm 可以輕鬆地針對應用程式擴充到多部主機的相同方式。 <br /><br /> Docker Swarm 是 Docker 公司的產品。 <br /><br /> Docker v1.12 或更新版本可以執行原生與內建的 Swarm 模式。 |
| Mesosphere DC/OS<br/>![Mesosphere DC/OS 標誌](./media/image8.png) |  Mesosphere Enterprise DC/OS (以 Apache Mesos 為基礎) 是一種適用於生產環境的平台，可執行容器和分散式應用程式。 <br /><br /> DC/OS 的運作方式是將叢集中可用的資源集合簡化，讓這些資源可供建置其上的元件使用。 Marathon 通常作為與 DC/OS 整合的排程器。 |
| Google Kubernetes<br />![Google Kubernetes 標誌](./media/image9.png) | Kubernetes 是開放原始碼產品，可提供叢集基礎結構、容器排程到容器協調等功能。 有了它，您可以跨主機叢集自動化部署、 調整及應用程式容器的作業。 <br /><br /> Kubernetes 提供以容器為中心的基礎結構，讓您將應用程式容器分組為邏輯單元，以便於管理及探索。 |
| Azure Service Fabric<br />![Azure Service Fabric 標誌](./media/image10.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) 是一種 Microsoft 微服務平台，可用來建置應用程式。 它是一種服務的[協調器](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)，並可建立電腦叢集。 根據預設，Service Fabric 部署和啟動這些服務做為處理序，但 Service Fabric 可以部署 Docker 容器映像中的服務。 更重要的是，您可以在相同的應用程式中的容器中的服務與混合處理序中的服務。 <br /><br /> 截至 2017 年，Service fabric 可支援做為 Docker 容器部署的服務功能處於預覽狀態。 <br /><br /> 您可以開發在許多方面，使用 Service Fabric 服務[Service Fabric 程式設計模型](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)部署[來賓可執行檔](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app)以及容器。 Service Fabric 支援之類的規範的應用程式模型[具狀態服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)並[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)。

## <a name="using-container-based-orchestrators-in-azure"></a>在 Azure 中使用容器協調器

許多雲端廠商都提供支援 Docker 容器以及 Docker 叢集和協調流程的支援，包括 Azure、 Amazon EC2 Container Service 和 Google Container Engine。 下一節中所述，azure 將提供 Docker 叢集和協調器支援透過 Azure Container Service。

另一個選擇是使用 Azure Service Fabric 也支援 Docker Linux 和 Windows 容器。 Service Fabric 會在 Azure 或任何其他雲端上執行，以及[內部](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)。

## <a name="using-azure-container-service"></a>使用 Azure Container Service

Docker 叢集裝載了多部 Docker 主機，並將其公開為單一虛擬 Docker 主機，因此您可以部署多個容器到該叢集中。 叢集會處理所有複雜的管理連接，像是延展性和健全狀況。 圖 4-7 表示組成應用程式的 Docker 叢集如何對應到容器服務。

Container Service 提供簡化建立、 設定及管理預先設定為執行容器化應用程式的 Vm 叢集的方法。 使用熱門的開放原始碼排程和協調流程工具的最佳化的組態，Container Service 可讓您能夠運用您現有的技能，或運用大量且不斷成長的社群專業知識，來部署和管理容器型主體在 Azure 中的應用程式。

Container Service 最佳化特別適用於 Azure 的熱門 Docker 叢集開放原始碼工具和技術設定。 這樣的開放解決方案，可賦予您容器和應用程式組態的可攜性。 您只要選取主機大小和數目，其餘工作全都由協調器工具和 Container Service 處理。

容器服務會使用 Docker 映像，以確保您的應用程式容器具有完全的可攜式特性。 它支援的開放原始碼協調流程平台，例如 DC/OS、 Kubernetes 和 Docker Swarm 的選擇，以確保這些應用程式可以擴充至數千或甚至數萬個容器。

使用 Azure Container Service，您可以充分利用 Azure 的企業級功能，同時仍可保有應用程式可攜性，包括協調流程層。

![](./media/image11.png)

圖 4-7:Azure Container Service 中的叢集選項

如所示的 圖 4-8，Container Service 是只是為了部署 DC/OS、 Kubernetes 或 Docker Swarm，Azure 所提供的基礎結構，但它不會實作任何其他協調器。 因此，Container Service 是不協調器時，這類;它是利用現有的開放原始碼協調器適用於容器的基礎結構。

![](./media/image12.png)

圖 4-8:在 Container Service 中的協調器

使用方式的觀點而言，Container Service 的目標是提供容器裝載環境使用熱門的開放原始碼工具和技術。 為此，它會為您所選擇的協調器公開標準的 API 端點。 藉由使用這些端點，您可以使用任何軟體，可以與這些端點進行通訊。 比方說，在 Docker Swarm 端點的情況下，您可能會選擇使用 Docker CLI。 若是 DC/OS，您可能會選擇使用 DC/OS CLI。

### <a name="getting-started-with-container-service"></a>開始使用容器服務

若要開始使用 Container Service，您必須部署從 Azure 入口網站的 Container Service 叢集使用 Azure Resource Manager 範本或有[CLI](https://docs.microsoft.com/cli/azure/install-azure-cli)。 可用的範本包括 [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm)、[Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes) 和 [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos)。 您可以修改快速入門範本，以包含其他或進階 Azure 組態。

**進一歩** 若要深入了解部署容器服務叢集，在 Azure 網站上的閱讀[部署 Azure Container Service 叢集](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment)。

隨附於 ACS 預設安裝的軟體均不會收取任何費用。 所有預設選項都是使用開放原始碼軟體來實作。

目前適用於標準 A、 D、 DS、 G 及 GS 系列 Linux Vm，在 Azure 容器服務。 您只需支付其他基礎結構資源費用，例如儲存體和網路功能以及您選擇的計算執行個體。 沒有累加的費用，容器服務本身。

### <a name="additional-resources"></a>其他資源

以下是您可以在此找到其他資訊的位置：

-   Docker 容器主控解決方案使用 Container Service 簡介：  
    https://docs.microsoft.com/azure/container-service/kubernetes/container-service-intro-kubernetes>

-   Docker Swarm 概觀：  
    <https://docs.docker.com/swarm/overview/>

-   Swarm 模式概觀：  
    <https://docs.docker.com/engine/swarm/>

-   Mesosphere DC/OS 概觀：    
    <https://docs.mesosphere.com/1.7/overview/>

-   Kubernetes （官方的站台）：  
    <https://kubernetes.io/>

## <a name="using-service-fabric"></a>使用 Service Fabric

Service Fabric 的前身是自傳遞到提供服務的 「 箱型 」 產品，通常是單體樣式，來自 Microsoft 的轉換。 建置和操作 Azure SQL Database、 Azure Documentdb、 Azure 服務匯流排或 Cortana 後端，等大規模大型服務的經驗圖形化 Service Fabric。 越來越多的服務採用與時俱進的平台。 重要的是，Service Fabric 不僅必須能在 Azure 中執行，還必須能在獨立的 Windows 伺服器部署中執行。

Service Fabric 的目標是解決建置和執行服務以及有效率使用基礎結構資源，以便小組可以解決使用微服務方法的商務問題的困難的問題。

Service Fabric 提供兩大區域，協助您建置使用微服務的應用程式：

-   平台，提供系統服務以部署、調整、升級、偵測及重新啟動失敗的服務、探索服務位置、管理狀態，以及監視健康狀態。 這些系統服務實際上會提供許多先前所述的微服務的特性。

-   程式設計 API 或架構，可協助您將應用程式建置為微服務：[可靠的執行者與可靠的服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)。 當然，您可以選擇任何程式碼來建置您的微服務，但是這些 API 能讓工作更簡單，與平台深入整合。 如此一來，您就可以取得健康狀態和診斷資訊，或者可以利用穩定的狀態管理。

Service Fabric 不在乎您用什麼方法來建置服務，所以您可以使用任何技術。 不過，它會提供內建的程式設計 API，讓您更輕鬆地建置微服務。

圖 4-9 示範如何建立和執行 Service Fabric 中的微服務，以簡單處理序或 Docker 容器。 它也可以將容器型微服務與程序型微服務混合在相同的 Service Fabric 叢集中。

![](./media/image13.png)

圖 4 至 9:在 Azure Service Fabric 中將微服務部署為處理序或容器

Docker Linux 容器和 Windows 容器，可以執行 Linux 和 Windows 主機為基礎的 Service Fabric 叢集。

**進一歩** 如 Azure 網站上最新 Service Fabric 中的容器支援相關資訊，請參閱[Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

Service Fabric 是平台與中，您可以定義相同的邏輯架構 （商務微服務或限定內容） 比實體實作的理想範例。 比方說，如果您實作[具狀態 Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)中[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)，在下一步 區段中，會介紹 「[無狀態與具狀態微服務](#stateless-versus-stateful-microservices)，「 您有與多個實體服務的商務微服務概念。

在 圖 4-10，就邏輯/商務微服務的觀點而言，實作 Service Fabric 具狀態可靠服務時所示，您通常必須實作兩層級的服務。 第一個是後端具狀態可靠服務，用來處理多個資料分割。 第二個是前端服務或閘道服務，負責跨多個資料分割或具狀態服務執行個體的路由及資料彙總。 閘道服務也會處理用戶端通訊與存取後端服務與 Service Fabric 搭配使用的重試迴圈[反向 proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)。

![](./media/image14.png)

圖 4-10:與 Service Fabric 中的數個具狀態與無狀態服務的商務微服務

在任何情況下，當您使用 Service Fabric 具狀態可靠服務時，您也會有邏輯或商務微服務 (繫結的內容)，它通常是由多項實體服務組成。 如所示的 圖 4-10，可能會實作每個這些，閘道服務和資料分割服務為 ASP.NET Web API 服務。

在 Service Fabric 中，您可以分組服務，並將這些服務群組部署為 [Service Fabric 應用程式](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)，這是協調器或叢集的封裝和部署單位。 因此，Service Fabric 應用程式無法對應到此自發商務和邏輯微服務界限或繫結的內容，以及。

### <a name="service-fabric-and-containers"></a>Service Fabric 和容器

關於 Service Fabric 中的容器，您也可以部署在 Service Fabric 叢集內的容器映像的服務。 圖 4-11 說明大部分的時間會有每個服務只能有一個容器。

![](./media/image15.png)

圖 4-11:Service Fabric 中使用數個服務 (容器) 的商務微服務

不過，也會在 Service Fabric 中所謂的 「 側車 」 容器 （必須一起作為邏輯的服務一部分部署的兩個容器）。 重點是商務微服務是圍繞數個緊密結合項目的邏輯界限。 在許多情況下，它可能是一項服務與單一資料模型，但在某些情況下，您可能會有數項實體服務，以及。

截至本文撰寫 (年 4 月 2017) 時，您也無法在 Service Fabric 中部署容器 SF 可靠具狀態服務，您可以部署客體容器、 無狀態服務或在容器中的動作項目服務。 但請注意您可以混合使用處理序中的服務與相同的 Service Fabric 應用程式中的容器中的服務所示在圖 4 到 12 個。

![](./media/image16.png)

圖 4 到 12 個：對應至具有容器和具狀態服務之 Service Fabric 應用程式的商務微服務

支援也是取決於您使用 Docker 容器在 Linux 或 Windows 容器上的不同。 在即將發行的版本中，將會擴充支援 Service Fabric 中的容器。 如在 Service Fabric 中，在 Azure 網站上的容器支援的最新消息，請參閱[Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

## <a name="stateless-versus-stateful-microservices"></a>無狀態微服務與具狀態微服務

如前所述，每項微服務 (邏輯繫結的內容) 都必須擁有其網域模型 (資料和邏輯)。 在使用無狀態的微服務的情況下，為資料庫會是外部，採用關聯式的選項，例如 SQL Server 或如 MongoDB 或 Azure DocumentDB 的 NoSQL 選項。

但是，服務本身也可以是具狀態，這表示資料位於微服務中。 這項資料可能會有不只是在相同伺服器上，但在微服務處理序中，在記憶體中，保存在磁碟機上和複寫到其他節點。 圖 4-13 顯示不同的方法。

![](./media/image17.png)

圖 4-13:無狀態微服務與具狀態微服務

無狀態的方法完全有效，而且您更輕鬆地實作比具狀態微服務，因為方法是類似於傳統和已知的模式。 但無狀態微服務會強制程序及資料來源之間的延遲。 當您嘗試使用額外的快取和佇列改善效能時，它們也牽涉到更多移動的片段。 您最後會得到有太多層的複雜架構。

相反地，[具狀態微服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)因為沒有任何網域邏輯與資料之間的延遲，所以在進階案例中勝出。 大量的資料處理，遊戲的後端、 資料庫即服務，與其他所有受惠於具狀態服務，可以提供更快速存取本機狀態的低延遲案例。

無狀態與具狀態服務是互補的。 比方說，具狀態服務，可能會分割成多個資料分割。 若要存取這些分割，您可能需要作為閘道服務的無狀態服務，它知道如何根據分割索引鍵處理每個分割。

具狀態服務確實有缺點。 它們會造成某種程度的複雜性，讓他們向外擴充。本來通常由外部資料庫系統實作的工作功能，例如跨具狀態微服務和資料分割的資料複寫，必須予以處理。 不過，這是其中一個區域協調器想在哪裡[Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture)具有其[具狀態 reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)有助於最 — 藉由簡化開發和具狀態的生命週期使用微服務[Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections)並[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)。

其他允許具狀態服務、支援執行者模式，以及改善商務邏輯和資料間容錯和延遲的微服務架構是 Microsoft [Orleans](https://github.com/dotnet/orleans)，來自 Microsoft 研究，以及 [Akka.NET](https://getakka.net/)。 這兩種架構目前都在改善它們對 Docker 的支援。

請注意，Docker 容器本身無狀態。 如果您想要實作具狀態服務，您需要前述的規範及較高層級架構之一。 不過，本文撰寫時，Service Fabric 中的具狀態服務不支援做為容器，只能以純文字的微服務。 在容器中的 reliable services 支援可在未來的 Service Fabric 版本。

>[!div class="step-by-step"]
>[上一頁](soa-applications.md)
>[下一頁](docker-apps-development-environment.md)