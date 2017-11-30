---
title: "協調 microservices 及多容器應用程式的高延展性和可用性"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |協調 microservices 及多容器應用程式的高延展性和可用性"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ec33901a0ddc9e5b58263440b0e4399e687c6904
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>協調 microservices 及多容器應用程式的高延展性和可用性

如果您的應用程式是根據 microservices 或只分割到多個容器，可實際執行的應用程式使用 orchestrators 就很重要。 推出之前，在微服務為基礎的方法中，每個微服務擁有其模型和資料，因此它會從開發和部署的觀點自發。 但是，即使您擁有更傳統的應用程式所組成的多個服務 （例如 SOA)，您也必須多個容器或組成單一商務應用程式中需要部署為分散式系統的服務。 這類系統很複雜向外擴充和管理。因此，您一定需要 orchestrator 如果您想要已備妥且可延展的多重容器應用程式。

圖 4-23 說明到叢集中的多個 microservices （容器） 所組成的應用程式的部署。

![](./media/image23.PNG)

**圖 4-23**。 叢集的容器

它看起來像邏輯方法。 不過，如何處理負載平衡、 路由及協調這些是您撰寫的應用程式嗎？

一般 Docker 引擎單一 Docker 主機中符合的需求管理一部的主機上的單一映像執行個體，但管理更複雜的分散式應用程式的多個主機上部署的多個容器時落短。 在大部分情況下，您需要的管理平台會自動啟動容器，每個影像的多個執行個體的向外延展容器、 擱置那些或關閉它們需要時，並在理想情況下也控制存取資源，例如網路和資料的方式儲存體。

若要超越個別容器或非常簡單的組成應用程式和大型企業應用程式與 microservices 嚴的管理，您必須開啟協調流程和叢集平台。

從 架構和開發觀點來看，如果您要建置 microservices 為基礎的應用程式所組成的大型企業務必瞭解下列平台和產品可支援進階的案例：

**叢集和 orchestrators**。 當您需要向外擴充的應用程式跨許多 Docker 主機，因為時的大型微服務應用程式，它是關鍵能夠管理與單一叢集的所有這些主機，藉由抽象化基礎平台的複雜性。 這是容器叢集和 orchestrators 提供的內容。 Orchestrators 範例包括 Azure Service Fabric、 Kubernetes、 Docker Swarm 和 Mesosphere DC/OS。 最後三個開放原始碼 orchestrators Azure 容器服務透過 Azure 中可用。

**排程器**。 *排程*表示系統管理員，才能啟動叢集中的容器，因此它們也會提供 UI 的功能。 叢集的排程器有多項責任： 有效率地使用叢集的資源設定使用者，有效率地跨主機或節點負載平衡容器所提供的條件約束，是錯誤的穩固同時提供高可用性。

密切相關的叢集，而排程器的概念，因此通常不同廠商所提供的產品提供兩個功能集。 下列清單顯示的最重要的平台和軟體選擇您的叢集和排程器。 這些 orchestrators 通常會提供如 Azure 公用雲端中。

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>叢集的容器、 協調流程，和排程軟體平台

Kubernetes

![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image24.png)

> Kubernetes 是開放原始碼產品，可提供功能，範圍可從叢集基礎結構和排程協調功能的容器。 它可讓您自動化部署、 調整及作業的應用程式容器主機的叢集上。
>
> Kubernetes 提供應用程式容器分組便於管理及探索的邏輯單元的容器中心基礎結構。
>
> Kubernetes 是成熟 Linux，較不成熟在 Windows 中。

Docker 群集

![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image25.png)

> Docker 群集可讓您叢集並排程 Docker 容器。 藉由使用群集，可以轉換成單一的虛擬的 Docker 主機的 Docker 主機的集區。 用戶端可以讓應用程式開發介面要求廣域相同的方式一樣這表示，群集輕鬆的應用程式擴充至多部主機的主機。
>
> Docker 群集是從 Docker，公司的產品。
>
> Docker v1.12 或更新版本可以執行原生和內建廣域模式。

Mesosphere DC/OS

![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image26.png)

> Mesosphere 企業 DC/OS （根據 Apache Mesos） 是可實際執行的平台執行容器和分散式應用程式。
>
> DC/OS 運作方式是抽象化叢集中可用的資源集合，並讓這些資源可供在其上建置的元件。 馬拉松通常做為與 DC/OS 整合的排程器。
>
> DC/OS 已成熟 Linux，較不成熟在 Windows 中。

Azure Service Fabric

![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image27.png)

> [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)是 Microsoft microservices 平台建置應用程式。 它是[orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)的服務，並會建立叢集的電腦。 Service Fabric 可以部署服務，做為容器，或做為一般的處理序。 它可以甚至混合中的服務處理程序與相同的應用程式和叢集內的容器中的服務。
>
> Service Fabric 提供其他和選擇性精準[程式設計模型的 Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)像[可設定狀態服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)和[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)。
>
> 服務網狀架構在 Windows 中 （在 Windows 中年發展），小於成熟在 Linux 中是成熟的。 
> 自 2017年中 Service Fabric 支援 Linux 和 Windows 容器。

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>在 Microsoft Azure 中使用容器型 orchestrators

許多雲端廠商提供 Docker 容器支援加上 Docker 叢集和協調流程的支援，包括 Microsoft Azure、 Amazon EC2 容器服務和 Google 容器引擎。 Microsoft Azure 提供的 Docker 叢集和 orchestrator 支援透過 Azure 容器服務 (ACS) 下, 一節中所述。

另一個選擇是使用 Microsoft Azure Service Fabric （microservices 平台），也支援根據 Linux 與 Windows 容器的 Docker。 Service Fabric 在 Azure 或其他雲端上執行，而且也會執行[內部](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)。

## <a name="using-azure-container-service"></a>使用 Azure 容器服務

Docker 叢集集區的多部 Docker 主機，其公開成單一虛擬 Docker 主機，主機，因此您可以部署到叢集中的多個容器。 叢集會處理所有複雜的管理配置作業，例如延展性、 健康及其他等等。 圖 4-24 表示組成應用程式的 Docker 叢集中將 Azure 容器服務 (ACS) 的對應。

ACS 提供簡化建立、 設定及管理叢集的執行容器化應用程式已預先設定的虛擬機器的方式。 ACS 使用最佳化的組態的熱門的開放原始碼排程和協調流程工具，讓您使用現有的技術或大量且不斷社群專業能力來部署和管理容器應用程式在 Microsoft Azure 上的主體上繪製.

Azure 容器服務進行最佳化熱門 Docker 群集的開放原始碼工具和技術的組態，特別針對 Azure。 您會取得開啟的方案，提供您的容器和應用程式組態的可攜性。 您選取大小、 主機、 數目和 orchestrator 工具，且容器服務會處理所有其他項目。

![](./media/image28.png)

**圖 4-24**。 Azure 容器服務中的群集選項

ACS 會利用 Docker 映像，以確保您的應用程式容器可完整移植。 它支援您選擇的開放原始碼的協調流程平台，如 DC/OS （由 Apache Mesos 所提供）、 Kubernetes （原本所建立 Google），以及 Docker Swarm，以確保這些應用程式，可以調整到數千、 數萬甚至數千張的容器。

Azure 容器服務可讓您利用 Azure 的企業級功能仍然維持應用程式可攜性，包括協調流程層級。

![](./media/image29.png)

**圖 4-25**。 在 ACS 中 orchestrators

所示圖 4-25，Azure 容器服務是只是為了部署 DC/OS、 Kubernetes 或 Docker Swarm，Azure 提供的基礎結構，但是 ACS 未實作任何其他 orchestrator。 因此，ACS 不 orchestrator 在這種情況，會利用現有的開放原始碼 orchestrators 容器的基礎結構。

使用方式的觀點而言，Azure 容器服務的目標是提供容器的裝載環境使用熱門的開放原始碼工具和技術。 為此，它會為您所選擇的 orchestrator 公開標準的應用程式開發介面端點。 藉由使用這些端點，您可以利用這些端點可以彼此通訊的任何軟體。 比方說，在 Docker Swarm 結束點的情況下，您可能會選擇使用 Docker 命令列介面 (CLI)。 DC/作業系統，您可能會選擇使用 DC/OS CLI。

### <a name="getting-started-with-azure-container-service"></a>開始使用 Azure 容器服務 

若要開始使用 Azure 容器服務，您必須部署從 Azure 入口網站與 Azure 容器服務的叢集使用 Azure Resource Manager 範本或[CLI](https://docs.microsoft.com/cli/azure/install-azure-cli)。 可用的範本包含[Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm)， [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes)，和[DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos)。 快速入門範本可以修改為包含其他或進階的 Azure 組態。 如需有關如何部署 Azure 容器服務叢集的詳細資訊，請參閱[部署 Azure 容器服務叢集](https://docs.microsoft.com/azure/container-service/container-service-deployment)Azure 網站上。

沒有任何預設安裝的 ACS 一部分的軟體的費用。 使用開放原始碼軟體，來實作所有預設選項。

標準的、 D、 DS、 G 及 GS 系列 Azure 中 Linux 虛擬機器目前使用 ACS。 您必須支付只選擇，計算執行個體，以及其他基本基礎結構耗用的資源，例如儲存體和網路功能。 沒有任何累加的費用，acs 本身。

## <a name="additional-resources"></a>其他資源

-   **裝載 Azure 容器服務方案的 Docker 容器簡介**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Docker 群集概觀**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **廣域模式概觀**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **Mesosphere DC/OS 概觀**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Kubernetes。** 官方網站。 \
    [*http://kubernetes.io/*](http://kubernetes.io/)


>[!div class="step-by-step"]
[上一個](具有恢復功能-高的可用性-microservices.md) [下一步] (使用-azure-服務-fabric.md)
