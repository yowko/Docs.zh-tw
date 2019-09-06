---
title: 協調微服務和多容器應用程式的高延展性和可用性
description: 您必須使用協調器來部署和管理實際生產應用程式，以便處理所有容器的健康狀態、工作負載和生命週期。
ms.date: 02/15/2019
ms.openlocfilehash: 8c1161127eb6b239384444c369de7f11abd3d424
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373697"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>協調微服務和多容器應用程式的高延展性和可用性

如果您的應用程式是以微服務為基礎或分散在多個容器，您就必須為適用於生產環境的應用程式使用協調器。 如之前所介紹，以微服務為基礎的方法中，每個微服務都擁有自己的模型和資料，因此從開發和部署的角度來看，它是非常自主的。 但是，即使您擁有的是由多個服務組成的傳統應用程式 (例如 SOA)，您也會使用多個容器或服務來組成單一商務應用程式，而這些項目都必須部署為分散式系統。 向外延展和管理這類系統非常的複雜；因此，如果您想要擁有一個適用於生產環境且可延展的多容器應用程式，就一定要使用協調器。

圖 4-6 說明由多個微服務 (容器) 所組成應用程式叢集中的部署。

![叢集中組合的 Docker 應用程式：您可以為每個服務執行個體各使用一個容器。 Docker 容器是「部署的單位」，而容器是 Docker 的執行個體。一部主機可處理多個容器](./media/image6.png)

**圖 4-6**： 容器叢集

看起來像邏輯方法。 不過，您該如何處理這些組成應用程式的負載平衡、路由及協調作業？

Docker 命令列介面 (CLI) 滿足一部主機上一個容器的管理需求，但若是更複雜的分散式應用程式，它就無法滿足部署於多部主機上多個容器的管理需求。 在大部分情況下，您需要的管理平台應能自動啟動容器、向外延展容器 (其中每個映像具有多個執行個體)、請視需要暫停或關閉它們，最好也能控制資源 (例如網路和資料儲存體) 的存取方式。

如果您不只要管理個別容器或組成簡單的應用程式，而是要進展到具有微服務的大型企業應用程式，就必須採用協調流程和叢集平台。

從架構和開發角度來看，如果您要建置大型企業微服務應用程式，請務必了解下列可支援進階案例的平台和產品：

- **叢集和協調器**： 當您要跨許多 Docker 主機向外延展應用程式時 (例如大型微服務應用程式)，您必須簡化基礎平台的複雜性，並以單一叢集的形式來管理其中所有主機。 而這正是容器叢集和協調器所提供的功能。 Azure Service Fabric 和 Kubernetes 都是範例協調器。 您可以透過 Azure Kubernetes Service 在 Azure 中取得 Kubernetes。

- **排程器**： 「排程」可讓系統管理員啟動叢集中的容器，因此這些排程器也會提供使用者介面來執行此作業。 叢集排程器有下列職責：有效率地使用叢集的資源、設定使用者所提供的條件約束、跨節點或主機有效進行容器負載平衡，以及維持容錯性並保障高可用性。

叢集與排程器的概念密切相關，因此不同廠商所提供的產品通常會兩組功能都提供。 下一節顯示您可以針對叢集和排程器選擇的最重要平台和軟體。 Azure 這類公用雲端普遍都會提供這些協調器。

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>用於容器叢集、協調流程和排程的軟體平台

| 平台 | 註解 |
|:---:|:---|
| **Kubernetes** <br/> ![Kubernetes 標誌](./media/kubernetes-logo.png) | [*Kubernetes*](https://kubernetes.io/) 是開放原始碼產品，可提供叢集基礎結構、容器排程到容器協調等功能。 它可讓您跨主機叢集自動化部署、規模調整及應用程式容器的作業。 <br/> <br/> *Kubernetes* 提供以容器為中心的基礎結構，讓您將應用程式容器分組為邏輯單元，以便於管理及探索。 <br/> <br/> 比起 Windows，*Kubernetes* 在 Linux 中相對成熟穩定。 |
| **Azure Kubernetes Service (AKS)** <br/> ![Azure Kubernetes Service 標誌](./media/aks-logo.png) | [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/) 是 Azure 中的受控 Kubernetes 容器協調流程服務，可簡化 Kubernetes 叢集的管理、部署和作業。 |
| **Azure Service Fabric** <br/> ![Azure Service Fabric 標誌](./media/service-fabric-logo.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) 是一種 Microsoft 微服務平台，可用來建置應用程式。 它是一種服務的[協調器](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)，並可建立電腦叢集。 Service Fabric 可以將服務部署為容器或一般處理序。 它甚至可以將處理序中的服務與相同應用程式和叢集內容器中的服務混合。 <br/> <br/> *Service Fabric* 叢集可以在 Azure 中部署、內部部署或部署到任何雲端。 不過，Azure 中的部署會透過受控方法簡化。 <br/> <br/> *Service Fabric* 也提供其他選用的規範 [Service Fabric 程式設計模型](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/)，例如[具狀態的服務](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/)和 [Reliable Actors](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/)。 <br/> <br/> 比起 Linux，*Service Fabric* 在 Windows 中相對成熟 (但仍在持續演進中)。 <br/> <br/> 自 2017 年起，Service Fabric 即可支援 Linux 和 Windows 容器。 |
| **Azure Service Fabric Mesh** <br/> ![Azure Service Fabric Mesh 標誌](./media/azure-service-fabric-mesh-logo.png) | [*Azure Service Fabric Mesh*](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) 提供與 Service Fabric 相同的可靠性、任務關鍵性效能和規模，但還提供完全受控且無伺服器的平台。 您不需要管理叢集、VM、儲存體或網路組態。 只要專注於您的應用程式開發即可。 <br/> <br/> *Service Fabric Mesh* 支援 Windows 和 Linux 容器，讓您可以使用所選擇的任何程式設計語言和架構進行開發。

## <a name="using-container-based-orchestrators-in-azure"></a>在 Azure 中使用容器協調器

許多雲端廠商都支援 Docker 容器以及 Docker 叢集和協調流程，包括 Azure、Amazon EC2 Container Service 和 Google Container Engine。 Azure 透過 Azure Kubernetes Service (AKS)、Azure Service Fabric 和 Azure Service Fabric Mesh 提供 Docker 叢集和協調器支援。

## <a name="using-azure-kubernetes-service"></a>使用 Azure Kubernetes Service

Kubernetes 叢集裝載多部 Docker 主機，並將其公開為單一虛擬 Docker 主機，因此您可以部署多個容器到該叢集中，並以任意容器執行個體數目向外延展。 叢集會處理所有複雜的管理配置作業，例如延展性、健康狀態等等。

AKS 可讓您以簡化的方式，在 Azure 中建立、組態及管理預先設定為執行容器化應用程式的虛擬機器叢集。 AKS 使用熱門開放原始碼排程和協調流程工具的最佳化組態，可讓您使用現有技能，或運用大量且不斷成長的社群專業知識，在 Microsoft Azure 上部署及管理容器化應用程式。

Azure Kubernetes Service 特別針對 Azure，提供熱門 Docker 叢集開放原始碼工具和技術的最佳化組態。 這樣的開放解決方案，可賦予您容器和應用程式組態的可攜性。 您只要選取主機大小和數目，其餘工作全都由協調器工具和 AKS 處理。

![Kubernetes 叢集結構：有一個處理 DNS、排程器、Proxy 等的主要節點，以及裝載容器的數個背景工作節點。](media/image36.png)

**圖 4-7**. Kubernetes 叢集的簡化結構和拓撲

圖 4-7 顯示 Kubernetes 叢集結構中的主要節點 (VM) 會控制大部分的叢集協調，且您可以將容器部署到其餘節點。從應用程式角度來看，這些節點是以單一集區來管理。 這讓您可以擴充到數以千計或甚至數以萬計的容器。

## <a name="development-environment-for-kubernetes"></a>Kubernetes 的開發環境

在 [Docker 於 2018 年 7 月宣告](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/)的開發環境中，Kubernetes 也可以在單一開發電腦 (Windows 10 或 macOS) 上執行，只要安裝 [Docker Desktop](https://www.docker.com/community-edition) 即可。 您稍後可以部署到雲端 (AKS) 來進一步執行整合測試，如圖 4-8 所示。

![Docker 於 2018 年 7 月宣佈透過 Docker Desktop 提供 Kubernetes 叢集的開發電腦支援。](media/kubernetes-development-environment.png)

**圖 4-8**： 在開發電腦和雲端中執行 Kubernetes

## <a name="get-started-with-azure-kubernetes-service-aks"></a>開始使用 Azure Kubernetes Service (AKS)

若要開始使用 AKS，請從 Azure 入口網站或使用 CLI 部署 AKS 叢集。 如需將 Kubernetes 叢集部署到 Azure 的詳細資訊，請參閱[部署 Azure Kubernetes Service (AKS) 叢集](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)。

隨附於 AKS 預設安裝的軟體均不會收取任何費用。 所有預設選項都是使用開放原始碼軟體來實作。 AKS 可供 Azure 中的多部虛擬機器使用。 您僅需支付所選計算執行個體的費用，以及其他已使用的基礎結構資源費用，例如儲存體和網路功能。 AKS 本身沒有任何累加的費用。

如需根據 `kubectl` 和原始 `.yaml` 檔案部署到 Kubernetes 的進一步實作資訊，請參閱 [Setting eShopOnContainers up in AKS (Azure Kubernetes Service)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)) (在 AKS (Azure Kubernetes Service) 中設定 eShopOnContainers) 上的文章。

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>使用 Helm 圖表部署到 Kubernetes 叢集中

將應用程式部署到 Kubernetes 叢集時，您可以搭配採用原生格式的部署檔案 (`.yaml` 檔案) 來使用原始 `kubectl.exe` CLI 工具，如上一節中所述。 不過，對於更複雜的 Kubernetes 應用程式 (例如部署複雜的微服務應用程式時)，則建議使用 [Helm](https://helm.sh/)。

即便是最複雜的 Kubernetes 應用程式，Helm 圖表也能協助您定義、設定版本、安裝、共用、升級或復原。

此外，建議使用 Helm 還有一個原因，那就是因為 Azure 中的其他 Kubernetes 環境 (例如 [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces)) 也是以 Helm 圖表為依據。

Helm 是由 [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) 以及 Microsoft、Google、Bitnami 和 Helm 參與者社群共同維護。

如需 Helm 圖表和 Kubernetes 的進一步實作資訊，請參閱 [Using Helm Charts to deploy eShopOnContainers to AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts) (使用 Helm 圖表將 eShopOnContainers 部署到 AKS) 上的文章。

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>在您的 Kubernetes 應用程式生命週期中使用 Azure Dev Spaces

[Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) 為小組提供快速的 Kubernetes 反覆開發體驗。 只要最少的開發電腦設定，您就可以直接在 Azure Kubernetes Service (AKS) 中反覆執行並偵錯容器。 您可以使用 Visual Studio、Visual Studio Code 或命令列等熟悉的工具，在 Windows、Mac 或 Linux 上進行開發。

如前所述，Azure Dev Spaces 在部署容器應用程式時使用 Helm 圖表。

Azure Dev Spaces 可協助開發小組在 Kubernetes 上更具生產力，因為它讓您只要使用 Visual Studio 2017 或 Visual Studio Code，就能夠直接在 Azure 的全域 Kubernetes 叢集中快速逐一查看並偵錯程式碼。 Azure 中的 Kubernetes 叢集是共用的受控 Kubernetes 叢集，讓您的小組可以共同合作。 您可以在隔離的狀況下開發程式碼，然後部署到全域叢集並使用其他元件進行端對端測試，不需要複寫或模擬相依性。

如圖 4-9 所示，Azure Dev Spaces 中最與眾不同的功能，就是能夠建立與叢集中全域部署其餘部分整合的執行「空間」。

![Azure Dev Spaces 可以無障礙地混搭生產環境的微服務與開發容器執行個體，以便測試新版本。](media/image38.png)

**圖 4-9**。 在 Azure Dev Spaces 中使用多個空間

基本上，您可以在 Azure 中設定共用的開發空間。 每位開發人員可以只專注於他們的應用程式部分，並可在已包含其案例所依存之所有其他服務和雲端資源的開發空間中，反覆開發「預先認可的」程式碼。 相依性一律保持最新狀態，而開發人員會以鏡像處理生產環境的方式工作。

Azure Dev Spaces 提供空間概念，讓您能夠在隔離的狀況下工作，不用擔心中斷您小組成員的工作。 這項功能是以 URL 首碼為依據；如果在 URL 中使用開發空間首碼，則針對容器的要求，Azure Dev Spaces 會執行部署給該空間的特殊容器版本 (如果存在)。 否則，它會執行全域/合併版本。

您可以查看 [Azure Dev Spaces 上的 eShopOnContainers Wiki 頁面](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS)，以取得具體範例的實用觀點。

如需進一步資訊，請參閱[使用 Azure Dev Spaces 進行小組開發](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore)一文。

## <a name="additional-resources"></a>其他資源

- **開始使用 Azure Kubernetes Service (AKS)**  \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes** 官方網站。 \
  <https://kubernetes.io/>

## <a name="using-azure-service-fabric"></a>使用 Azure Service Fabric

Azure Service Fabric 的出現來自於 Microsoft 從提供「盒裝」產品轉換成提供服務，「盒裝」產品的風格通常具整體性。 大規模建置及操作 Azure SQL Database、Azure Cosmos DB、Azure 服務匯流排或 Cortana 後端等大型服務的體驗，形成了 Service Fabric。 越來越多的服務採用與時俱進的平台。 重要的是，Service Fabric 不僅必須能在 Azure 中執行，還必須能在獨立的 Windows 伺服器部署中執行。

Service Fabric 的目標是解決建置和執行服務以及有效率使用基礎結構資源的難題，讓小組可以使用微服務方法解決商務問題。

Service Fabric 提供兩大區域，協助您建置使用微服務的應用程式：

- 平台，提供系統服務以部署、調整、升級、偵測及重新啟動失敗的服務、探索服務位置、管理狀態，以及監視健康狀態。 這些系統服務能夠發揮前述微服務的許多特性。

- 程式設計 API 或架構，可協助您將應用程式建置為微服務：[可靠的執行者與可靠的服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)。 您可以選擇任何程式碼來建置您的微服務，但是這些 API 能讓工作更簡單，而且它們與平台的整合更深入。 如此一來，您就可以取得健康狀態和診斷資訊，或者可以利用穩定的狀態管理。

Service Fabric 不在乎您用什麼方法來建置服務，所以您可以使用任何技術。 不過，它會提供內建的程式設計 API，讓您更輕鬆地建置微服務。

如圖 4-10 所示，您可以在 Service Fabric 中建立微服務，將其作為簡單的處理序或 Docker 容器執行。 它也可以將容器型微服務與程序型微服務混合在相同的 Service Fabric 叢集中。

![比較 Azure 服務網狀架構叢集：微服務作為處理序，每個節點針對每個微服務執行一個處理序；微服務作為容器，每個節點使用數個容器來執行 Docker，每個微服務一個容器。](./media/azure-service-fabric-cluster-types.png)

**圖 4-10**： 在 Azure Service Fabric 中將微服務部署為處理序或容器

以 Linux 和 Windows 主機為基礎的 Service Fabric 叢集，可以分別執行 Docker 的 Linux 容器和 Windows 容器。

如需 Azure Service Fabric 容器支援的最新資訊，請參閱 [Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

Service Fabric 是良好的平台範例，您可在此定義與實體實作不同的邏輯架構 (商務微服務或繫結的內容)。 例如，如果您實作 [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) 的[具狀態可靠服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) (下一節＜[無狀態與具狀態的微服務](#stateless-versus-stateful-microservices)＞中會介紹)，您會擁有具備多項實體服務的商務微服務概念。

如圖 4-10 所示，就邏輯/商務微服務的觀點而言，實作 Service Fabric 具狀態可靠服務時，您通常需要實作兩層服務。 第一項是後端具狀態可靠服務，處理多個分割 (每個分割都是一項具狀態服務)。 第二項是前端服務，或稱閘道服務，負責跨多個分割或具狀態服務執行個體的路由及資料彙總。 閘道服務也會使用存取後端服務的重試迴圈來處理用戶端通訊。 如果您實作您的自訂服務，它就稱為閘道服務；或者您也可以使用現成可用的 Service Fabric [反向 Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)。

![Service Fabric 已支援在容器中有數個具狀態可靠服務。](./media/service-fabric-stateful-business-microservice.png)

**圖 4-11**： 使用數個具狀態服務執行個體和自訂閘道前端的商務微服務

在任何情況下，當您使用 Service Fabric 具狀態可靠服務時，您也會有邏輯或商務微服務 (繫結的內容)，它是由多項實體服務組成。 閘道服務和磁碟分割服務每一個都可實作為 ASP.NET Web API 服務，如圖 4-11 所示。

在 Service Fabric 中，您可以分組服務，並將這些服務群組部署為 [Service Fabric 應用程式](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)，這是協調器或叢集的封裝和部署單位。 因此，Service Fabric 應用程式也可以對應到此自發商務邏輯微服務界限或繫結內容，以便您自主部署這些服務。

### <a name="service-fabric-and-containers"></a>Service Fabric 和容器

至於 Service Fabric 的容器，您也可以在 Service Fabric 叢集內的容器映像中部署服務。 如圖 4-12 所示，每項服務大部分時候都只有一個容器。

![Service Fabric 應用程式可以執行存取外部資料庫的數個容器，而整個集合會是商務微服務的邏輯界限](./media/azure-service-fabric-business-microservice.png)

**圖 4-12**. Service Fabric 中使用數個服務 (容器) 的商務微服務

不過，Service Fabric 也可能有所謂的「側車」容器 (必須一起部署為邏輯服務一部分的兩個容器)。 重點是商務微服務是圍繞數個緊密結合項目的邏輯界限。 在許多情況下，它可能是使用單一資料模型的單一服務，但在其他一些情況下，您可能也會有數項實體服務。

請注意，您可以在相同 Service Fabric 應用程式中混合處理序和容器的服務，如圖 4-13 所示。

![在相同節點中執行服務和容器的 Service Fabric 應用程式。](./media/business-microservice-mapped-to-service-fabric-application.png)

**圖 4-13**. 對應至具有容器和具狀態服務之 Service Fabric 應用程式的商務微服務

如需 Azure Service Fabric 容器支援的詳細資訊，請參閱 [Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

## <a name="stateless-versus-stateful-microservices"></a>無狀態微服務與具狀態微服務

如前所述，每項微服務 (邏輯繫結的內容) 都必須擁有其網域模型 (資料和邏輯)。 在無狀態微服務的案例中，資料庫會是外部的、採用如 SQL Server 的關聯式選項，或採用如 Azure Cosmos DB 或 MongoDB 的 NoSQL 選項。

但是服務本身在 Service Fabric 中也可以具狀態，這表示資料位在微服務內。 這項資料可能不只存在於相同的伺服器，也存在微服務程序、記憶體內部，並保存在硬碟上，會複寫到其他節點。 圖4-14 顯示不同的方法。

![在無狀態服務中，狀態 (持續性、資料庫) 會保留在微服務之外。 在具狀態服務中，狀態會保留在微服務內。](./media/stateless-vs-stateful-microservices.png)

**圖 4-14**. 無狀態微服務與具狀態微服務

無狀態方法完全有效，而且比具狀態微服務更容易實作，因為方法類似於傳統和已知的模式。 但無狀態微服務會強制程序及資料來源之間的延遲。 當您嘗試使用其他快取和佇列來改善效能時，它們也牽涉到更多移動片段。 您最後會得到有太多層的複雜架構。

相反地，[具狀態微服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)在進階案例中勝出，因為領域邏輯和資料之間沒有任何延遲。 大量的資料處理、競先搶回終點、資料庫即服務，以及其他低延遲狀況皆得益於具狀態服務，它讓本機狀態可供更快速存取。

無狀態與具狀態服務是互補的。 例如，您可以在圖4-14 的右邊圖表中看到，具狀態服務可以分割成多個資料分割。 若要存取這些分割，您可能需要作為閘道服務的無狀態服務，它知道如何根據分割索引鍵處理每個分割。

具狀態服務確實有缺點。 向外延展時會提高複雜度。本來通常由外部資料庫系統實作的工作功能，例如跨具狀態微服務和資料分割的資料複寫，必須予以處理。 不過，這是像 [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) 這類的協調器及其[具狀態可靠服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)提供最多幫助的其中一個區域，方法是使用[可靠的服務 API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) 和 [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction) 簡化開發和具狀態微服務的生命週期。

其他允許具狀態服務、支援執行者模式，以及改善商務邏輯和資料間容錯和延遲的微服務架構是 Microsoft [Orleans](https://github.com/dotnet/orleans)，來自 Microsoft 研究，以及 [Akka.NET](https://getakka.net/)。 這兩種架構目前都在改善它們對 Docker 的支援。

請記住，Docker 容器本身無狀態。 如果您想要實作具狀態服務，您需要前述的規範及較高層級架構之一。

## <a name="using-azure-service-fabric-mesh"></a>使用 Azure Service Fabric Mesh

Azure Service Fabric Mesh 是完全受控的服務，它讓開發人員能建置及部署任務關鍵性應用程式，而不需要管理任何基礎結構。 使用 Service Fabric Mesh 來建置並執行能視需要調整的安全、分散式微服務應用程式。

如圖 4-15 所示，裝載於 Service Fabric Mesh 的應用程式會執行並擴充，您不需要擔心推動它的基礎結構。

![在 Docker Desktop 執行的多容器應用程式，可以部署至 Azure Service Fabric Mesh，而不需擔心基礎結構。](media/image39.png)

**圖 4-15**： 將微服務/容器應用程式部署至 Service Fabric Mesh

實際上，Service Fabric Mesh 包含數千部機器的叢集。 開發人員不會察覺所有叢集作業。 您只需要上傳容器，並指定需要的資源、可用性需求和資源限制。 Service Fabric Mesh 會自動配置應用程式部署要求的基礎結構，也會處理基礎結構失敗，確定您的應用程式具備高可用性。 您只需要關心應用程式的健全狀況和回應性，不需要關心基礎結構。

如需詳細資訊，請參閱 [Service Fabric Mesh 文件](https://docs.microsoft.com/azure/service-fabric-mesh/)。

## <a name="choosing-orchestrators-in-azure"></a>在 Azure 中選擇協調器

下表提供根據工作負載和 OS 焦點要使用哪個協調器的指導。

![Azure Kubernetes Services 在 Linux 中比起在 Windows 中更成熟，且最常用於根據容器部署微服務。 Azure Service Fabric (叢集和網格) 在 Windows 中比起在 Linux 中更成熟，通常根據容器用於微服務，根據一般處理序和具狀態服務用於微服務。](media/image40.png)

**圖 4-16**： 在 Azure 中選取協調器的指導

>[!div class="step-by-step"]
>[上一頁](soa-applications.md)
>[下一頁](deploy-azure-kubernetes-service.md)
