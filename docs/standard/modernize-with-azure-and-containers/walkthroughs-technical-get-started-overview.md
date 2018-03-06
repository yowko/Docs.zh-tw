---
title: "逐步解說和技術取得已啟動的概觀"
description: "現代化現有的.NET 應用程式與 Azure 雲端和 Windows Containers |逐步解說和技術取得已啟動的概觀"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bced3bed84d138dbda4f322322213b47c0159016
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>逐步解說和技術取得已啟動的概觀 

若要限制此的電子書的大小，我們已進行其他技術文件和完整的逐步解說 GitHub 儲存機制。 此章節所述的逐步解說線上系列涵蓋 Windows 容器和部署至 Azure 為基礎的多個環境的逐步安裝。

下列各節將說明每個逐步解說何謂有關其目標，及其高階的願景-，並提供所涉及的工作的圖表。 您可以取得自己的逐步解說中*eShopModernizing*在應用程式 GitHub 儲存機制 wiki [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki)。

# <a name="technical-walkthrough-list"></a>技術的逐步解說清單

下列 get 開始逐步解說提供一致且完整的範例應用程式，您可以拿起和移位藉由使用容器，並接著在 Azure 中使用多個部署選項之間移動技術的指引。

下列逐步解說使用的新範例 eShopLegacy 和 eShopModernizing 應用程式，可在 GitHub 上[https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing)。

-   **教學課程的資格舊版應用程式**

-   **化您現有的.NET 應用程式與 Windows 容器**

-   **將 Windows 容器基礎應用程式部署至 Azure Vm**

-   **將 Windows 容器基礎應用程式部署到 Kubernetes Azure 容器服務中**

-   **將 Windows 容器基礎應用程式部署至 Azure Service Fabric**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>逐步解說 1： 教學課程的資格舊版應用程式

### <a name="technical-walkthrough-availability"></a>可用性技術的逐步解說

EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a>總覽

在本逐步解說中，您可以瀏覽初始實作中的兩個範例舊版應用程式。 兩個範例應用程式整合的架構，並使用傳統 ASP.NET 所建立的。 一個應用程式根據 ASP.NET 4.x MVC;第二個應用程式是以 ASP.NET 4.x Web Form 為基礎。 這兩個應用程式處於[eShopModernizing GitHub 儲存機制](https://github.com/dotnet-architecture/eShopModernizing)。

可以化兩個範例應用程式，其方式類似於可以化傳統[Windows Communication Foundation](../../framework/wcf/whats-wcf.md)取用做為桌面應用程式 (WCF) 應用程式。 如需範例，請參閱[eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms)。

### <a name="goals"></a>目標

本逐步解說的主要目的是只要取得熟悉這些應用程式，以及其程式碼和組態。 您可以設定應用程式，以便產生並使用模擬的資料，而不需要使用 SQL database 中，基於測試目的。 這個選用的設定根據相依性插入解除解合的方式。

### <a name="scenario"></a>情節

圖 5-1 會顯示原始的舊版應用程式的簡單案例。

> ![原始的舊版應用程式的簡單架構案例](./media/image5-1.png)
>
> **圖 5-1。** 原始的舊版應用程式的簡單架構案例

商務網域的觀點而言，這兩個應用程式會提供在相同的目錄管理功能。 資格企業小組的成員可使用應用程式來檢視和編輯產品類別目錄。 圖 5-2 顯示的初始應用程式螢幕擷取畫面。

![ASP.NET MVC 與 ASP.NET Web Form 應用程式 （舊版現有技術）](./media/image5-2.png)

> **圖 5-2。** ASP.NET MVC 與 ASP.NET Web Form 應用程式 （舊版現有技術）

這些是 web 應用程式，可用來瀏覽並修改類別目錄項目。 兩個應用程式傳遞相同的功能/功能其實只是進行比較。 您可以看到類似的現代化程序所建立的 ASP.NET MVC 與 ASP.NET Web Form 架構的應用程式。

相依性中 ASP.NET 4.x 或更早的版本 （無論是 MVC 或 Web Form） 表示除非使用 ASP.NET Core MVC 完全重寫程式碼，將不會在.NET Core 上執行這些應用程式。 這示範了，如果您不想要重新建構或重寫程式碼，您可以化現有的應用程式，並且仍然使用相同的.NET 技術和相同的程式碼。 您可以查看如何執行這類在容器中，不進行任何變更，舊版程式碼的應用程式。

### <a name="benefits"></a>優點

本逐步解說的好處是簡單： 只讓您熟悉的程式碼和應用程式的組態，根據相依性插入。 然後，您可以嘗試透過這種方式化和未來部署至多個環境時。

### <a name="next-steps"></a>後續步驟

瀏覽更深入了解此內容上的 GitHub wiki:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>逐步解說 2： 化您現有的.NET 應用程式與 Windows 容器

### <a name="technical-walkthrough-availability"></a>可用性技術的逐步解說

EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：

[https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

### <a name="overview"></a>總覽

您可以使用 Windows 容器來改善現有的.NET 應用程式，例如根據 MVC、 Web Form 或 WCF、 生產、 開發和測試環境的部署。

### <a name="goals"></a>目標

本逐步解說的目標是示範幾個選項用於 containerizing 現有的.NET Framework 應用程式。 您可以：

-   化您的應用程式使用[Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) （Visual Studio 2017 或更新版本）。

-   化您的應用程式透過手動方式新增[Dockerfile](https://docs.docker.com/engine/reference/builder/)，然後使用[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)。

-   化您的應用程式使用[Img2Docker](https://github.com/docker/communitytools-image2docker-win)工具 （從 Docker 開放原始碼工具）。

本逐步解說著重於 Visual Studio 2017 Tools for Docker 方法，但其他兩種方法是在使用 Dockerfile 的方面相當類似。

### <a name="scenario"></a>情節

圖 5-3 顯示容器化的資格舊版應用程式的案例。

> ![在開發環境中的容器化應用程式的簡化的架構圖](./media/image5-3.png)
>
> **圖 5-3。** 在開發環境中的容器化應用程式的簡化的架構圖

### <a name="benefits"></a>優點

有許多優點容器中執行應用程式整合。 首先，您會建立應用程式的映像。 從該點上，每個部署在相同的環境中執行。 每個容器會使用相同的作業系統版本、 具有相同版本的相依性安裝、 使用相同的.NET framework 版本和建置使用相同的程序。 基本上，您可以控制您的應用程式的相依性使用 Docker 映像。 相依性會隨著應用程式，當您部署容器。

另一個優點是開發人員可以在 Windows 容器所提供一致性的環境中執行應用程式。 僅與特定版本一起出現的問題可以立即發現，而不是預備或生產環境的。 在容器中執行的應用程式時，開發小組的成員使用的開發環境中的差異重要小於。

容器化應用程式也會有更平面的向外延展曲線。 容器化應用程式可讓您有多個應用程式和服務執行個體 （根據容器） 中 VM 或實體機器相較於每部電腦的一般應用程式部署。 這會轉譯成更高的密度和較少的所需的資源，特別是當您使用 orchestrators Kubernetes 等服務網狀架構。

集裝箱化，在理想的情況下，不需要對應用程式程式碼進行任何變更 (C\#)。 在大部分情況下，您只需要 Docker 部署中繼資料檔案 （Dockerfiles 和 Docker Compose 檔案）。

### <a name="next-steps"></a>後續步驟

瀏覽 GitHub wiki 上的更深入了解此內容： [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>逐步解說 3： 將 Windows 容器基礎應用程式部署至 Azure Vm

### <a name="technical-walkthrough-availability"></a>可用性技術的逐步解說

EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a>總覽

部署至 Azure 中的 Windows Server 2016 VM 上的 Docker 主機，可讓您快速地設定開發/測試/預備環境。 它也可讓您為一般測試人員或商務使用者驗證應用程式。 Vm 也可以是有效的 IaaS 實際執行環境。

### <a name="goals"></a>目標

本逐步解說的目標在於說明您到 Windows Server 2016 或更新版本為基礎的 Azure Vm 中部署 Windows 容器時，您有多個替代項目。

### <a name="scenarios"></a>案例

在本逐步解說涵蓋數個案例。

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>從開發人員電腦透過 Docker 引擎連線的案例 a： 部署至 Azure VM

![從透過 Docker 引擎連線的開發電腦部署到 Azure VM](./media/image5-4.png)

> **圖 5-4。** 從透過 Docker 引擎連線的開發電腦部署到 Azure VM

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>案例 b： 部署至 Azure VM 透過 Docker 登錄

![部署至 Azure VM 透過 Docker 登錄](./media/image5-5.png)

> **圖 5-5。** 部署至 Azure VM 透過 Docker 登錄

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a>案例 c： 將部署至 Azure VM 從 Visual Studio Team Services 中的 CI/CD 管線

![從 Visual Studio Team Services 中的 CI/CD 管線部署至 Azure VM](./media/image5-6.png)

> **圖 5-6。** 從 Visual Studio Team Services 中的 CI/CD 管線部署至 Azure VM

### <a name="azure-vms-for-windows-containers"></a>Windows 容器的 azure Vm

為 Windows 容器 azure Vm 只根據 Windows Server 2016 中，Windows 10 的 Vm 或更新版本中，同時具有 Docker 引擎設定。 在大部分情況下，您將在 Azure Vm 中使用 Windows Server 2016。

Azure 目前提供名為的 VM**與容器的 Windows Server 2016**。 您可以使用此 VM 試用新的 Windows Server 容器功能，與 Windows Server Core 或 Windows Nano Server。 安裝容器 OS 映像，然後就可以開始使用 docker VM。

### <a name="benefits"></a>優點

雖然 Windows 容器可以部署到內部部署 Windows Server 2016 Vm 部署至 Azure 時，您會收到更簡單的方法，若要開始使用已備妥要使用 Windows Server 容器 Vm。 您也可以存取測試人員，並透過 Azure VM 規模集的自動延展性的一般線上位置。

### <a name="next-steps"></a>後續步驟

瀏覽更深入了解此內容上的 GitHub wiki:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>逐步解說 4： 將 Windows 容器基礎應用程式部署到 Kubernetes Azure 容器服務中

### <a name="technical-walkthrough-availability"></a>可用性技術的逐步解說

EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a>總覽

應用程式為基礎的 Windows 容器快速必須使用平台，移動離開更進一步的 IaaS Vm。 這需要輕易地達成高延展性和更自動化延展性，並大幅改善的自動化部署和版本控制。 您可以使用 orchestrator 來達成這些目標[Kubernetes](https://kubernetes.io/)，可用於[Azure 容器服務](https://azure.microsoft.com/services/container-service/)。

### <a name="goals"></a>目標

本逐步解說的目標是要了解如何部署 Kubernetes – 基礎 Windows 容器功能的應用程式 (也稱為*K8s*) Azure 容器服務中。 重新部署至 Kubernetes 是兩步驟程序：

1.  將 Kubernetes 叢集部署至 Azure 容器服務。

2.  Kubernetes 叢集部署的應用程式和相關的資源。

### <a name="scenarios"></a>案例

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>從開發環境的案例 a： 部署直接到 Kubernetes 叢集

![直接將部署到 Kubernetes 叢集從開發環境](./media/image5-7.png)

> **圖 5-7。** 直接將部署到 Kubernetes 叢集從開發環境

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a>在 Team Services 中的案例 b： 從將部署至 Kubernetes 叢集 CI/CD 管線

![從 Team Services 中的 CI/CD 管線部署到 Kubernetes 叢集](./media/image5-8.png)

> **圖 5-8。** 從 Team Services 中的 CI/CD 管線部署到 Kubernetes 叢集

### <a name="benefits"></a>優點

有許多優點，部署至 Kubernetes 中的叢集。 最大的好處是您取得的可實際執行環境，您可以向外延展應用程式根據您想要使用 （內部延展性中現有的節點），並根據叢集 （中的節點或 Vm 數目的容器執行個體數目全域延展性的叢集）。

Azure 容器服務，特別針對 Azure 最佳化熱門的開放原始碼工具和技術。 您會取得開啟的方案，提供可攜性，您的容器和應用程式組態。 您選取的大小，主機的數目和 orchestrator 工具-容器服務會處理所有其他項目。

與 Kubernetes，開發人員就可以開始從思考實體和虛擬機器進行規劃容器為中心的基礎結構，可促進下列功能，和其他項目：

-   根據多個容器的應用程式

-   複寫容器執行個體和水平的自動調整

-   命名及探索 (例如，內部 DNS)

-   平衡負載

-   輪流更新

-   散發密碼

-   應用程式健全狀況檢查

## <a name="next-steps"></a>後續步驟

瀏覽 GitHub wiki 上的更深入了解此內容： [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a>逐步解說 5： 將 Windows 容器基礎應用程式部署至 Azure Service Fabric

### <a name="technical-walkthrough-availability"></a>可用性技術的逐步解說

EShopModernizing GitHub 儲存機制 wiki 有完整的技術的逐步解說：

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a>總覽

應用程式為基礎的 Windows 容器快速必須使用平台，移動離開更進一步的 IaaS Vm。 這需要輕易地達成高延展性和更自動化延展性，並大幅改善的自動化部署和版本控制。 使用 orchestrator Azure Service Fabric 是用於 Azure 的雲端，但也可以使用內部部署，或甚至在不同的公用雲端中，您就可以達成這些目標。

### <a name="goals"></a>目標

本逐步解說的目標是了解如何部署 Windows 容器型應用程式至 Azure Service Fabric 叢集。 部署 Service fabric 從頭是兩個步驟：

1.  將 Service Fabric 叢集部署至 Azure （或不同的環境）。

2.  應用程式和相關的資源部署到 Service Fabric 叢集。

### <a name="scenarios"></a>案例

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a>從開發環境的案例 a： 部署直接到 Service Fabric 叢集

![從開發環境部署直接到 Service Fabric 叢集](./media/image5-9.png)

> **圖 5-9。** 從開發環境部署直接到 Service Fabric 叢集

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a>在 Team Services 中的案例 b： 從將部署到 Service Fabric 叢集 CI/CD 管線

![從 Visual Studio Team Services 中的 CI/CD 管線部署到 Service Fabric 叢集](./media/image5-10.png)

> **圖 5-10。** 從 Visual Studio Team Services 中的 CI/CD 管線部署到 Service Fabric 叢集

## <a name="benefits"></a>優點

部署至 Service Fabric 叢集的優點是類似於使用 Kubernetes 的優點。 一項差異，不過，是 2017年的服務網狀架構是 2017年的針對 Windows 應用程式相較於 Kubernetes，是 2017年的 Windows 容器之前早期預覽中切換非常成熟的實際執行環境。 （Kubernetes 是適用於 Linux 的成熟環境）。 

使用 Azure Service Fabric 的主要優點就是您取得的可實際執行環境，您可以向外延展應用程式根據您想要使用 （內部延展性中現有的節點），並根據數目的容器執行個體數目節點或叢集中 （全域延展性的叢集） Vm。

Azure Service Fabric 提供了適用於您的容器和應用程式組態的可攜性。 您可以讓 Service Fabric 叢集在 Azure 中，或將它安裝在內部部署在自己的資料中心。 可以甚至在您安裝 Service Fabric 叢集不同的雲端，例如[Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/)。

使用 Service Fabric，開發人員就可以開始從思考實體和虛擬機器進行規劃容器為中心的基礎結構，可促進下列功能，和其他項目：

-   根據多個容器應用程式。

-   複寫容器執行個體和水平的自動調整。

-   命名和探索 (例如，內部 DNS)。

-   平衡負載。

-   輪流更新。

-   散發密碼。

-   應用程式健全狀況檢查。

獨佔 （相較於其他 orchestrators） 的 Service Fabric 中有下列功能：

-   可設定狀態的服務功能，透過可靠的服務應用程式模型。

-   動作項目模式，透過 Reliable Actors 應用程式模型。

-   部署 / 骨處理程序，除了 Windows 或 Linux 容器。

-   進階輪流更新和健康情況檢查。

### <a name="next-steps"></a>後續步驟

瀏覽更深入了解此內容上的 GitHub wiki:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
[上一頁](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[下一頁](conclusions.md)
