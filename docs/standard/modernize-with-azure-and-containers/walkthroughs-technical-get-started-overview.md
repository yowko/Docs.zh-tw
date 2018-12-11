---
title: 逐步解說和技術開始入門的概觀
description: 將現有.NET 應用程式與 Azure 雲端和 Windows 容器現代化 |逐步解說和技術開始入門的概觀
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: f5a9d0c7c1c45a6afca390e93384af4c8386fe09
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150585"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>逐步解說和技術開始入門的概觀

若要限制此電子書的大小，其他的技術文件和完整的逐步解說所提供的 GitHub 存放庫中。 線上系列這一章所述的逐步解說涵蓋 Windows 容器和部署至 Azure 為基礎的多個環境的逐步安裝程式。

下列各節說明每個逐步解說是什麼相關高階的願景，其目標，提供所涉及的工作的圖表。 您可以取得自己的逐步解說中*eShopModernizing*在應用程式 GitHub 儲存機制的 wiki [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki)。

## <a name="technical-walkthrough-list"></a>技術逐步解說清單

下列快速入門逐步解說提供一致且完整的範例應用程式，您可以隨即轉移藉由使用容器，和在 Azure 中使用多個部署選項然後移動的技術指導。

每個下列逐步解說使用的新範例 eShopLegacy 和 eShopModernizing 應用程式，也就是在 GitHub 上的可用[ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing)。

- **教學課程的 eShop 舊版應用程式 （如將現代化的應用程式基準）**

- **將現有 ASP.NET web 應用程式 （WebForms 和 MVC） 與 Windows 容器的容器化**

- **將現有的 WCF 服務 （多層式架構應用程式） 與 Windows 容器的容器化**

- **將 Windows 容器型應用程式部署至 Azure Vm**

- **在 Azure Container Service 的 kubernetes 部署 Windows 容器型應用程式**

- **部署到 Azure Service Fabric Windows 容器型應用程式**


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>逐步解說 1:EShop 舊版應用程式的教學課程

### <a name="technical-walkthrough-availability"></a>技術逐步解說可用性

完整的技術逐步解說位於 eShopModernizing GitHub 存放庫 wiki:

[eShopModernizing wiki 逐步解說](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a>總覽

在本逐步解說中，您可以瀏覽三個範例的舊版應用程式的初始實作。 前兩個範例 web 應用程式已整合型架構，並使用傳統的 ASP.NET 所建立的。 一個應用程式根據 ASP.NET 4.x MVC;第二個應用程式是以 ASP.NET 4.x Web Form 為基礎。 第三個應用程式是由用戶端 WinForms 應用程式和伺服器端所組成的 3 層式架構應用程式[Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md)服務。

所有這些應用程式位於[eShopModernizing GitHub 存放庫](https://github.com/dotnet-architecture/eShopModernizing)。

### <a name="goals"></a>目標

本逐步解說中的主要目標是只取得熟悉這些應用程式，以及其程式碼和組態。 您可以設定應用程式，以便產生並使用模擬 （mock） 的資料，而不需使用 SQL database 中，基於測試目的。 此選擇性的組態根據相依性插入的低耦合的方式。

### <a name="scenario-1-aspnet-web-apps"></a>案例 1:ASP.NET Web 應用程式

下圖顯示原始的舊版 ASP.NET web 應用程式的簡單案例。

> ![原始的舊版 ASP.NET web 應用程式的簡單架構案例](./media/image5-1.png)
>

商務網域的觀點而言，這兩個應用程式會提供相同的目錄管理功能。 EShop 企業小組成員會使用應用程式，來檢視和編輯產品目錄。 

下圖顯示的初始應用程式螢幕擷取畫面。

![ASP.NET MVC 和 ASP.NET Web Forms 應用程式 （現有/舊版技術）](./media/image5-2.png)

相依性在 ASP.NET 4.x 或更早版本 （無論是 MVC 或 Web Form） 表示除非使用 ASP.NET Core MVC 會完全重寫程式碼，不會在.NET Core 上執行這些應用程式。 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>案例 2:WCF 服務與 WinForms 用戶端應用程式 （3 層式架構應用程式）

下圖顯示原始 3 層式架構的舊版應用程式的簡單案例。

> ![原始的 WCF 服務與舊版 3 層式架構應用程式和 WinForms 用戶端應用程式的簡單架構案例](./media/image5-1.5.png)
>

### <a name="benefits"></a>優點

本逐步解說的好處很簡單：剛開始熟悉的程式碼與初始的應用程式。

### <a name="next-steps"></a>後續步驟

探索 GitHub wiki 上的此更深入的內容：

  - [基準 ASP.NET MVC 教學課程和 Web Forms 「 舊版 」 應用程式](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [基準 WCF 服務及 WinForms （3 層） 的 「 舊版 」 應用程式的教學課程](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>逐步解說 2:將您現有的.NET 應用程式與 Windows 容器的容器化

### <a name="overview"></a>總覽

您可以使用 Windows 容器來改善現有的.NET 應用程式，例如生產、 開發和測試環境來根據 MVC、 Web Form 或 WCF 部署。

### <a name="goals"></a>目標

本逐步解說的目的是要說明幾個選項用於容器化現有的.NET Framework 應用程式。 您可以：

- 將您的應用程式使用容器化[Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) （Visual Studio 2017 或更新版本）。

- 將您的應用程式容器化將手動新增[Dockerfile](https://docs.docker.com/engine/reference/builder/)，然後使用[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)。

- 將您的應用程式使用容器化[Img2Docker](https://github.com/docker/communitytools-image2docker-win)工具 （從 Docker 開放原始碼工具）。

本逐步解說著重於 Visual Studio 2017 Tools for Docker 的方法，但其他兩種方法都使用 Dockerfile 方面相當類似。

### <a name="scenario-1-containerized-aspnet-web-apps"></a>案例 1:容器化的 ASP.NET web 應用程式

下圖顯示容器化的 eShop 舊版 web 應用程式的應用程式的案例。

> ![簡化的架構圖表的容器化的開發環境中的 ASP.NET 應用程式](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a>案例 2:容器化的 WCF 服務

下圖顯示容器化的 WCF 服務的 3 層式架構應用程式的案例。 

> ![簡化的開發環境中的容器化 WCF 服務的架構圖](./media/image5-3.5.png)
>

### <a name="benefits"></a>優點

有一些優點，以在容器中執行整合型應用程式。 首先，您會建立應用程式的映像。 從那時起，每個部署相同的環境中執行。 每個容器會使用相同的 OS 版本、 具有相同版本的相依性安裝、 使用相同的.NET framework 版本和建置使用相同的程序。 基本上，您可以控制您的應用程式的相依性所使用的 Docker 映像。 相依性會跟著應用程式，當您部署容器。

另一個優點是開發人員可以在一致的環境所提供的 Windows 容器中執行應用程式。 只能搭配特定版本出現的問題可以立即看出，而不是呈現在預備或生產環境中。 在容器中執行的應用程式時，開發小組的成員所用的開發環境中的差異重要小於。

容器化應用程式也會有 flatter 的向外延展曲線。 容器化應用程式可讓您有多個應用程式和服務執行個體 （以容器為基礎） 中的 VM 或實體機器相較於每部機器的一般應用程式部署。 這會轉譯為密度增加且較少的所需的資源，特別是當您使用 Kubernetes 或 Service Fabric 等協調器。

容器化，在理想的情況下，不需要對應用程式程式碼進行任何變更 (C\#)。 在大部分情況下，您只需要 Docker 部署中繼資料檔案 （Dockerfiles 和 Docker Compose 檔案）。

### <a name="next-steps"></a>後續步驟

探索 GitHub wiki 上的此更深入的內容：

  - [如何將容器化.NET Framework web 應用程式與 Windows 容器和 Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [將 Docker 支援新增至 WCF 服務](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>逐步解說 3:將 Windows 容器型應用程式部署至 Azure Vm

### <a name="technical-walkthrough-availability"></a>技術逐步解說可用性

完整的技術逐步解說位於 eShopModernizing GitHub 存放庫 wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a>總覽

部署到 Docker 主機上 Windows Server 2016 虛擬機器 (VM) 在 Azure 中，可讓您快速地設定開發/測試/預備環境。 它也可讓您為通用測試人員或業務使用者來驗證應用程式。 Vm 也可以有效的基礎結構即服務 (IaaS) 」 生產環境。

### <a name="goals"></a>目標

本逐步解說的目的是要說明您將 Windows 容器部署到 Windows Server 2016 或更新版本為基礎的 Azure Vm 時，您有多個替代項目。

### <a name="scenarios"></a>案例

在本逐步解說涵蓋數個案例。

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>案例 a:從 透過 Docker 引擎連線的開發電腦部署至 Azure VM

![從 透過 Docker 引擎連線的開發電腦部署至 Azure VM](./media/image5-4.png)

> **圖 5-4.** 從 透過 Docker 引擎連線的開發電腦部署至 Azure VM

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>案例 b:部署至 Azure VM 透過 Docker 登錄

![部署至 Azure VM 透過 Docker 登錄](./media/image5-5.png)

> **圖 5-5.** 部署至 Azure VM 透過 Docker 登錄

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>案例 c:從 Azure DevOps 服務中的 CI/CD 管線部署至 Azure VM

![從 Azure DevOps 服務中的 CI/CD 管線部署至 Azure VM](./media/image5-6.png)

> **圖 5-6。** 從 Azure DevOps 服務中的 CI/CD 管線部署至 Azure VM

### <a name="azure-vms-for-windows-containers"></a>適用於 Windows 容器的 azure Vm

Azure Vm 的 Windows 容器是根據 Windows Server 2016、 Windows 10 或更新版本的 Vm，都有 Docker 引擎設定。 在大部分情況下，Windows Server 2016 會在 Azure Vm。

Azure 目前提供的 VM **Windows Server 2016 with Containers**。 您可以試用新的 Windows Server 容器功能，與 Windows Server Core 或 Windows Nano Server 中使用此 VM。 安裝容器 OS 映像，並就準備好搭配 Docker VM。

### <a name="benefits"></a>優點

雖然 Windows 容器可以部署到內部部署 Windows Server 2016 Vm，當您部署至 Azure 時，您會得到更簡單的方法，若要開始使用已準備好使用 Windows Server 容器的 Vm。 您也可以存取軟體測試人員，並透過 Azure 虛擬機器擴展集的自動延展性的一般線上位置。

### <a name="next-steps"></a>後續步驟

探索 GitHub wiki 上的此更深入的內容：

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>逐步解說 4:將 Windows 容器型應用程式部署至 Azure Container Instances (ACI)

### <a name="technical-walkthrough-availability"></a>技術逐步解說可用性

完整的技術逐步解說位於 eShopModernizing GitHub 存放庫 wiki:

[將應用程式部署至 ACI （Azure 容器執行個體）](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>總覽

[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/)最快的方式，讓您可以在其中部署容器的單一執行個體的容器開發/測試/預備環境。

### <a name="goals"></a>目標

本逐步解說會示範的主要案例將 Windows 容器部署至 Azure Container Instances (ACI) 以及您如何部署至 ACI eShopModernizing 應用程式時。

### <a name="scenarios"></a>案例

可以有變化，需將 eShopModernizing 應用程式部署至 ACI 中，例如部署其中一個或所有應用程式 （MVC 應用程式、 WebForms 應用程式或 WCF 服務）。 如下所示的下列案例中您所見的 ASP.NET MVC 應用程式加上這兩個部署的 SQL Server 容器做為容器至 ACI （Azure 容器執行個體）。

![從開發環境部署至 ACI](./media/image5-3.5.6.png)

### <a name="benefits"></a>優點

Azure Container Instances 可讓您輕鬆地建立及管理 Docker 容器，在 Azure 中，而不需要佈建虛擬機器或採用高階服務。 使用 ACI，您可以直接部署在 Azure 中的 Windows 容器並將它公開到網際網路的完整的網域名稱 (FQDN) 而幾秒內 （前提是您將 Windows 容器映像準備好在像 Docker Hub 或 Azure 容器的 Docker 登錄登錄中）。

### <a name="considerations"></a>考量

將 Windows 容器，使用任一個完整的.NET Framework 部署 / ASP.NET 或 SQL Server 到 Azure Container Instances (ACI) 不是相當一樣快速，因為 Docker 映像必須部署到一般的 Docker 主機 （例如 Windows Server 2016 和 Windows 容器)每次下載 （提取從 Docker 登錄） 和 SQL 容器映像 (15.1 GB) 和 ASP.NET 的容器映像 (13.9 GB) 的大小會相當龐大，不過它是比維護您自己的 docker 主機 （永久線上操作的成本更低Windows Server 2016 與 Windows 容器在 Azure 中的 VM) 在 Azure (AKS/ACS) 或 Azure Service Fabric 中，也就是，相反地，生產環境部署的絕佳選擇的 Kubernetes 等的整個 orchestrator 更是不在話下。

為主要的結束時，使用 Azure Container Instances 是令人信服選項適用於開發/測試案例及 CI/CD 管線。

## <a name="next-steps"></a>後續步驟

探索 GitHub wiki 上的此更深入的內容： 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>逐步解說 5:在 Azure Container Service 的 kubernetes 部署 Windows 容器型應用程式

### <a name="technical-walkthrough-availability"></a>技術逐步解說可用性

完整的技術逐步解說位於 eShopModernizing GitHub 存放庫 wiki:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a>總覽

應用程式為基礎的 Windows 容器快速必須使用平台，從 IaaS 虛擬機器移動更進一步地消失。 這即可以輕鬆地達到高延展性和更自動化延展性，並大幅提升的自動化部署和版本控制。 您可以使用協調器，以達成這些目標[Kubernetes](https://kubernetes.io/)，可用於[Azure Container Service](https://azure.microsoft.com/services/container-service/)。

### <a name="goals"></a>目標

本逐步解說的目標是要了解如何部署至 Kubernetes Windows 容器型應用程式 (也稱為*K8s*) 在 Azure Container Service 中。 重新部署至 Kubernetes 是兩步驟程序：

1.  部署至 Azure Container Service 的 Kubernetes 叢集。

2.  應用程式和相關的資源部署到 Kubernetes 叢集。

### <a name="scenarios"></a>案例

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>案例 a:將直接部署到 Kubernetes 叢集中從開發環境

![將直接部署到 Kubernetes 叢集中從開發環境](./media/image5-7.png)

> **圖 5-7.** 將直接部署到 Kubernetes 叢集中從開發環境

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>案例 b:從 Azure DevOps 服務中的 CI/CD 管線部署至 Kubernetes 叢集

![從 Azure DevOps 服務中的 CI/CD 管線部署至 Kubernetes 叢集](./media/image5-8.png)

> **圖 5-8.** 從 Azure DevOps 服務中的 CI/CD 管線部署至 Kubernetes 叢集

### <a name="benefits"></a>優點

有許多好處，部署至 Kubernetes 叢集。 最大的好處是您在其中您可以相應放大您想要使用 （內部-現有的節點中的延展性），而且在叢集 （節點或 Vm 的數目為基礎的容器執行個體數目為基礎的應用程式的可實際執行環境全域延展性的叢集）。

Azure Container Service 會特別針對 Azure 最佳化熱門開放原始碼工具和技術。 您取得開啟的方案，提供可攜性，適用於您容器和應用程式組態。 您選取的大小，主機的數目和 orchestrator 工具-容器服務會處理所有其他項目。

使用 Kubernetes，開發人員可以開始進行思考實體和虛擬機器，從規劃以容器為中心的基礎結構，可簡化下列功能，其他項目：

- 多個容器為基礎的應用程式

- 複寫的容器執行個體和水平自動調整

- 命名和探索 (例如，內部 DNS)

- 平衡負載

- 輪流更新

- 散發祕密

- 應用程式健康情況檢查

## <a name="next-steps"></a>後續步驟

探索 GitHub wiki 上的此更深入的內容： [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a>逐步解說 6:部署到 Azure Service Fabric Windows 容器型應用程式

### <a name="technical-walkthrough-availability"></a>技術逐步解說可用性

完整的技術逐步解說位於 eShopModernizing GitHub 存放庫 wiki:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a>總覽

基礎 Windows 容器快速的應用程式必須使用平台，從 IaaS 虛擬機器移動更進一步地消失。 這即可以輕鬆地達到高延展性和更自動化延展性，並大幅提升的自動化部署和版本控制。 若要達成這些目標，您即可使用 orchestrator Azure Service Fabric 中，也就是可在 Azure 雲端中，但也可以使用內部部署，或甚至在不同的公用雲端。

### <a name="goals"></a>目標

本逐步解說的目標是了解如何部署 Windows 容器型應用程式到 Azure 中 Service Fabric 叢集。 重新部署至 Service Fabric 是兩個步驟的程序：

1.  將 Service Fabric 叢集部署至 Azure （或不同的環境）。

2.  應用程式和相關的資源部署到 Service Fabric 叢集。

### <a name="scenarios"></a>案例

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a>案例 a:將直接部署到 Service Fabric 叢集從開發環境

![將直接部署到 Service Fabric 叢集從開發環境](./media/image5-9.png)

> **圖 5-9.** 將直接部署到 Service Fabric 叢集從開發環境

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-azure-devops-services"></a>案例 b:從 Azure DevOps 服務中的 CI/CD 管線部署至 Service Fabric 叢集

![從 Azure DevOps 服務中的 CI/CD 管線部署至 Service Fabric 叢集](./media/image5-10.png)

> **圖 5-10.** 從 Azure DevOps 服務中的 CI/CD 管線部署至 Service Fabric 叢集

## <a name="benefits"></a>優點

部署到 Service Fabric 中的叢集的優點是類似於使用 Kubernetes 的優點。 一項差異，不過是 Service Fabric 是成熟的生產環境，相較於 Kubernetes，是在 beta 階段，適用於在 Kubernetes 中 1.9 版的 Windows 容器的 Windows 應用程式 (12 月 2017)。 Kubernetes 是成熟的環境，適用於 Linux。

使用 Azure Service Fabric 的主要優點是您取得在其中您可以相應放大您想要使用 （內部-現有的節點中的延展性），並根據數目的容器執行個體數目為基礎的應用程式的可實際執行環境節點或叢集 （叢集的全域延展性） 中的 Vm。

Azure Service Fabric 會提供適用於您容器和應用程式組態的可攜性。 您可以讓 Service Fabric 叢集在 Azure 中，或將它安裝在內部部署在自己的資料中心。 您可以更安裝 Service Fabric 叢集在不同的雲端，例如[Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/)。

Service fabric，開發人員就可以開始思考實體和虛擬機器從進行規劃以容器為中心的基礎結構，可簡化下列功能，其他項目：

- 多個容器為基礎的應用程式。

- 將容器執行個體和水平自動調整的複寫。

- 命名和探索 (例如，內部 DNS)。

- 平衡負載。

- 輪流更新。

- 散發祕密。

- 應用程式健康狀態檢查。

獨佔 （相較於其他協調器） 的 Service Fabric 中的下列功能︰

- 具狀態服務功能，透過 Reliable Services 應用程式模型。

- 動作項目模式，透過 Reliable Actors 應用程式模型。

- 部署簡易的程序，除了 Windows 或 Linux 容器。

- 進階輪流更新和健康情況檢查。

### <a name="next-steps"></a>後續步驟

探索 GitHub wiki 上的此更深入的內容：

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
>[上一頁](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
>[下一頁](conclusions.md)