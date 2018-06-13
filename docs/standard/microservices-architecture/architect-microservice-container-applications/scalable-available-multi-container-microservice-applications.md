---
title: 協調微服務和多容器應用程式的高延展性和可用性
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 協調微服務和多容器應用程式的高延展性和可用性
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: e8552f79a4196c161ec70d7ea46156215e52db26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578881"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>協調微服務和多容器應用程式的高延展性和可用性

如果您的應用程式是以微服務為基礎或分散於多個容器，您就必須為適用於生產環境的應用程式使用協調器。 如之前所介紹，以微服務為基礎的方法中，每個微服務都擁有自己的模型和資料，因此從開發和部署的角度來看，它是非常自主的。 但是，即使您擁有的是由多個服務組成的傳統應用程式 (例如 SOA)，您也會使用多個容器或服務來組成單一商務應用程式，而這些項目都必須部署為分散式系統。 向外延展和管理這類系統非常的複雜；因此，如果您想要擁有一個適用於生產環境且可延展的多容器應用程式，就一定要使用協調器。

圖 4-23 說明由多個微服務 (容器) 所組成之應用程式叢集中的部署。

![](./media/image23.PNG)

**圖 4-23**： 容器叢集

看起來像邏輯方法。 不過，您該如何處理這些組成應用程式的負載平衡、路由及協調作業？

如果是一部主機上單一映像執行個體的管理需求，可靠單一 Docker 主機中的單純 Docker 引擎來滿足，但若是更複雜的分散式應用程式，它就無法滿足部署於多個主機上多個容器的管理需求。 在大部分情況下，您需要的管理平台應能自動啟動容器、向外延展容器 (其中每個映像含多個執行個體)、視需要暫停或關閉它們，最好也能控制資源 (例如網路和資料儲存體) 的存取方式。

如果您不只要管理個別容器或組成非常簡單的應用程式，而是要進展到含有微服務的大型企業應用程式，就必須採用協調流程和叢集平台。

從架構和開發角度來看，如果您要建置由微服務應用程式所組成的大型企業應用程式，請務必了解下列可支援進階案例的平台和產品：

**叢集和協調器**： 當您要跨許多 Docker 主機向外延展應用程式時 (亦即大型微服務應用程式)，您必須簡化基礎平台的複雜性，並以單一叢集的形式來管理其中的所有主機。 而這正是容器叢集和協調器所提供的功能。 Azure Service Fabric、Kubernetes、Docker Swarm 和 Mesosphere DC/OS 都是範例協調器。 最後三個是開放原始碼協調器；您可以透過 Azure Container Service 在 Azure 中取得。

**排程器**： 「排程」可讓系統管理員啟動叢集中的容器，因此這些排程器也會提供 UI。 叢集排程器有下列職責：有效率地使用叢集的資源、設定使用者所提供的條件約束、跨節點或主機有效進行容器負載平衡，以及維持容錯性並保障高可用性。

叢集與排程器的概念密切相關，因此不同廠商所提供的產品通常會兩組功能都提供。 下列清單顯示您可以針對叢集和排程器選擇的最重要平台和軟體。 一般來說，Azure 這類公用雲端都會提供這些協調器。

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>用於容器叢集、協調流程和排程的軟體平台

Kubernetes

![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image24.png)

> Kubernetes 是開放原始碼產品，可提供叢集基礎結構、容器排程到容器協調等功能。 它可讓您跨主機叢集自動化部署、規模調整及應用程式容器的作業。
>
> Kubernetes 提供以容器為中心的基礎結構，讓您將應用程式容器分組為邏輯單元，以便於管理及探索。
>
> 比起 Windows，Kubernetes 在 Linux 中相對成熟穩定。

Docker Swarm

![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image25.png)

> Docker Swarm 可讓您為 Docker 容器進行叢集與排程作業。 使用 Swarm 時，您可以將 Docker 主機集區轉換成單一的虛擬 Docker 主機。 用戶端可以向 Swarm 提出 API 要求 (與向主機提出要求的方式相同)，也就是說 Swarm 可以輕鬆地讓應用程式順應多部主機來調整規模。
>
> Docker Swarm 是 Docker 公司的產品。
>
> Docker v1.12 或更新版本可以執行原生與內建的 Swarm 模式。

Mesosphere DC/OS

![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image26.png)

> Mesosphere Enterprise DC/OS (以 Apache Mesos 為基礎) 是一種適用於生產環境的平台，可執行容器和分散式應用程式。
>
> DC/OS 的運作方式是將叢集中可用的資源集合簡化，讓這些資源可供建置其上的元件使用。 Marathon 通常作為與 DC/OS 整合的排程器。
>
> 比起 Windows，DC/OS 在 Linux 中相對成熟穩定。

Azure Service Fabric

![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image27.png)

> [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) 是一種 Microsoft 微服務平台，可用來建置應用程式。 它是一種服務的[協調器](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)，並可建立電腦叢集。 Service Fabric 可以將服務部署為容器或一般處理序。 它甚至可以將處理序中的服務與相同應用程式和叢集內容器中的服務混合。
>
> Service Fabric 也提供其他選用的規範 [Service Fabric 程式設計模型](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)，例如[具狀態的服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)和 [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)。
>
> 比起 Linux，Service Fabric 在 Windows 中相對成熟 (但仍在持續演進中)。 
> 自 2017 年起，Service Fabric 即可支援 Linux 和 Windows 容器。

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>在 Microsoft Azure 中使用容器協調器

許多雲端廠商都支援 Docker 容器以及 Docker 叢集和協調流程，包括 Microsoft Azure、Amazon EC2 Container Service 和 Google Container Engine。 如下節所說明，Microsoft Azure 可透過 Azure Container Service (ACS) 支援 Docker 叢集和協調器。

您也可以選擇使用 Microsoft Azure Service Fabric (微服務平台)，其亦可支援 Linux 和 Windows 容器的 Docker。 Service Fabric 可在 Azure 或任何其他雲端上執行，亦可於[內部部署](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)執行。

## <a name="using-azure-container-service"></a>使用 Azure Container Service

Docker 叢集裝載了多部 Docker 主機，並將其公開為單一虛擬 Docker 主機，因此您可以部署多個容器到該叢集中。 叢集會處理所有複雜的管理配置作業，例如延展性、健康狀態等等。 圖 4-24 表示組成應用程式的 Docker 叢集如何與 Azure Container Service (ACS) 對應。

ACS 可讓您以簡化的方式，建立、設定及管理預先設定為執行容器化應用程式的虛擬機器叢集。 ACS 使用熱門開放原始碼排程和協調流程工具的最佳化組態，可讓您使用現有技能，或運用大量且不斷成長的社群專業知識，在 Microsoft Azure 上部署及管理容器化應用程式。

Azure Container Service 特別針對 Azure，提供熱門 Docker 叢集開放原始碼工具和技術的最佳化組態。 這樣的開放解決方案，可賦予您容器和應用程式組態的可攜性。 您只要選取主機大小和數目，其餘工作全都由協調器工具和 Container Service 處理。

![](./media/image28.png)

**圖 4-24**： Azure Container Service 中的叢集選項

ACS 會利用 Docker 映像，以確保您的應用程式容器具有完整可攜性。 它可支援您選擇的開放原始碼協調流程平台，如 DC/OS (由 Apache Mesos 提供技術支援)、Kubernetes (由 Google 初創) 與 Docker Swarm，以確保這些應用程式可以調整到數千、甚至數萬個容器的規模。

藉由使用 Azure Container Service，您可以充分利用 Azure 的企業級功能，同時仍可保有應用程式的可攜性，包括協調流程層級。

![](./media/image29.png)

**圖 4-25**： ACS 的協調器

如圖 4-25 所示，Azure Container Service 只是 Azure 為了部署 DC/OS、Kubernetes 或 Docker Swarm 所提供的基礎結構，但是 ACS 並未實作任何其他協調器。 因此，ACS 不是協調器，而只是一種運用容器現有開放原始碼協調器的基礎結構。

從用途角度來看，Azure Container Service 的目標是使用熱門的開放原始碼工具和技術來提供容器裝載環境。 為此，它會為您所選擇的協調器公開標準的 API 端點。 藉由使用這些端點，您就能運用任何可與這些端點通訊的軟體。 比方說，若是 Docker Swarm 端點，您可能會選擇使用 Docker 命令列介面 (CLI)。 若是 DC/OS，您可能會選擇使用 DC/OS CLI。

### <a name="getting-started-with-azure-container-service"></a>開始使用 Azure Container Service 

若要開始使用 Azure Container Service，請使用 Azure Resource Manager 範本或 [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli)，從 Azure 入口網站部署 Azure Container Service。 可用的範本包括 [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm)、[Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes) 和 [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos)。 您可以修改快速入門範本，以包含其他或進階的 Azure 組態。 如需如何部署 Azure Container Service 叢集的詳細資訊，請參閱 Azure 網站上的[部署 Azure Container Service 叢集](https://docs.microsoft.com/azure/container-service/container-service-deployment)。

隨附於 ACS 預設安裝的軟體均不會收取任何費用。 所有預設選項都是使用開放原始碼軟體來實作。

ACS 目前可供 Azure 中的標準 A、D、DS、G 及 GS 系列 Linux 虛擬機器使用。 您僅需支付所選計算執行個體的費用，以及其他已使用的基礎結構資源費用，例如儲存體和網路功能。 ACS 本身沒有任何累加的費用。

## <a name="additional-resources"></a>其他資源

-   **使用 Azure Container Service 裝載解決方案的 Docker 容器簡介**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Docker Swarm 概觀**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **Swarm 模式概觀**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **Mesosphere DC/OS 概觀**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Kubernetes** 官方網站。
    [*https://kubernetes.io/*](https://kubernetes.io/)


>[!div class="step-by-step"]
[Previous] (resilient-high-availability-microservices.md) [下一頁] (using-azure-service-fabric.md)
