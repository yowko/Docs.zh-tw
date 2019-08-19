---
title: 逐步解說和技術入門概觀
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |逐步解說和技術入門總覽
ms.date: 04/28/2018
ms.openlocfilehash: 81f7d9fbf596a23b83e2dc9251788b33a8817e16
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577851"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>逐步解說和技術入門概觀

為了限制此電子書的大小, GitHub 存放庫中提供了其他的技術檔和完整的逐步解說。 本章所述的線上逐步解說系列涵蓋以 Windows 容器為基礎的多個環境, 以及部署至 Azure 的逐步設定。

下列各節說明每個逐步解說的相關事項、其目標和高階願景, 並提供相關工作的圖表。 您可以在的*eShopModernizing* apps GitHub 存放庫 wiki <https://github.com/dotnet-architecture/eShopModernizing/wiki>中取得逐步解說本身。

## <a name="technical-walkthrough-list"></a>技術逐步解說清單

下列快速入門逐步解說針對您可以使用容器隨即轉移的範例應用程式, 提供一致且完整的技術指導方針, 然後在 Azure 中使用多個部署選項進行移動。

下列每個逐步解說都會使用新的範例 eShopLegacy 和 eShopModernizing apps, 這些應用程式可在<https://github.com/dotnet-architecture/eShopModernizing>GitHub 的上取得。

- **EShop 繼承應用程式教學課程 (要現代化的基準應用程式)**

- **使用 Windows 容器容器化現有的 ASP.NET web 應用程式 (WebForms & MVC)**

- **使用 Windows 容器容器化您現有的 WCF 服務 (多層式應用程式)**

- **將以 Windows 容器為基礎的應用程式部署至 Azure Vm**

- **將以 Windows 容器為基礎的應用程式部署至 Azure Container Service 中的 Kubernetes**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>逐步解說 1:EShop 繼承應用程式的教學課程

### <a name="technical-walkthrough-availability"></a>技術逐步解說可用性

您可以在 eShopModernizing GitHub 存放庫 wiki 中取得完整的技術逐步解說:

[eShopModernizing wiki 逐步解說](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>總覽

在此逐步解說中, 您可以探索三個範例繼承應用程式的初始執行。 前兩個範例 web 應用程式具有整合型架構, 而且是使用傳統 ASP.NET 建立的。 其中一個應用程式是以 ASP.NET 4.x MVC 為基礎;第二個應用程式是以 ASP.NET 4.x Web Forms 為基礎。
第三個應用程式是由用戶端 WinForms 應用程式和伺服器端[Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md)服務所組成的3層應用程式。

所有這些應用程式都可以在[EShopModernizing GitHub](https://github.com/dotnet-architecture/eShopModernizing)存放庫中取得。

### <a name="goals"></a>目標

本逐步解說的主要目標是要熟悉這些應用程式, 並使用其程式碼和設定。 您可以設定應用程式, 讓它們產生及使用模擬資料, 而不需要使用 SQL 資料庫來進行測試。 這個選擇性的設定是以分離的方式, 以相依性插入為基礎。

### <a name="scenario-1-aspnet-web-apps"></a>案例 1:ASP.NET Web 應用程式

下圖顯示原始舊版 ASP.NET web 應用程式的簡單案例。

![原始舊版 ASP.NET web 應用程式的簡單架構案例](./media/image5-1.png)

從商務網域的觀點來看, 這兩個應用程式都提供相同的目錄管理功能。 EShop enterprise 小組的成員會使用此應用程式來查看和編輯產品目錄。

下圖顯示初始應用程式螢幕擷取畫面。

![ASP.NET MVC 和 ASP.NET Web Forms 應用程式 (現有/舊版技術)](./media/image5-2.png)

ASP.NET 4.x 或更早版本中的相依性 (適用于 MVC 或 Web form) 表示這些應用程式不會在 .NET Core 上執行, 除非已使用 ASP.NET Core MVC 來完全重寫程式碼。

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>案例 2:WCF 服務和 WinForms 用戶端應用程式 (3 層應用程式)

下圖顯示原始3層繼承應用程式的簡單案例。

![使用 WCF 服務和 WinForms 用戶端應用程式的原始舊版3層應用程式的簡單架構案例](./media/image5-1.5.png)

### <a name="benefits"></a>權益

這個逐步解說的優點很簡單:只要熟悉程式碼和初始應用程式即可。

### <a name="next-steps"></a>後續步驟

在 GitHub wiki 深入探索此內容:

- [ASP.NET MVC 和 Web form 「舊版」應用程式的基準導覽](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [基準 WCF 服務和 WinForms (3 層) 「舊版」應用程式的導覽](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>逐步解說 2:使用 Windows 容器容器化現有的 .NET 應用程式

### <a name="overview"></a>總覽

使用 Windows 容器改善現有 .NET 應用程式的部署, 像是以 MVC、Web form 或 WCF 為基礎, 到生產、開發和測試環境。

### <a name="goals"></a>目標

本逐步解說的目標是要示範容器化現有 .NET Framework 應用程式的數個選項。 您可以：

- 使用[適用于 Docker 的 Visual Studio 2017 工具](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)(Visual Studio 2017 或更新版本) 來容器化您的應用程式。

- 手動新增[Dockerfile](https://docs.docker.com/engine/reference/builder/), 然後使用[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)來容器化您的應用程式。

- 使用[Img2Docker](https://github.com/docker/communitytools-image2docker-win)工具 (Docker 中的開放原始碼工具) 來容器化您的應用程式。

本逐步解說著重于適用于 Docker 的 Visual Studio 2017 工具方法, 但其他兩種方法在使用 Dockerfile 方面相當類似。

### <a name="scenario-1-containerized-aspnet-web-apps"></a>案例 1:容器化 ASP.NET web 應用程式

下圖顯示容器化 eShop 舊版 web apps 應用程式的案例。

![開發環境中容器化 ASP.NET 應用程式的簡化架構圖](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>案例 2:容器化 WCF 服務

下圖顯示具有容器化 WCF 服務的3層式應用程式案例。

![開發環境中容器化 WCF 服務的簡化架構圖](./media/image5-3.5.png)

### <a name="benefits"></a>權益

在容器中執行整合型應用程式有其優點。 首先, 您要建立應用程式的映射。 從該時間點開始, 每個部署都會在相同的環境中執行。 每個容器都會使用相同的作業系統版本、已安裝相同版本的相依性、使用相同的 .NET framework 版本, 並使用相同的程式建立。 基本上, 您可以使用 Docker 映射來控制應用程式的相依性。 當您部署容器時, 相依性會與應用程式一起移動。

另一個優點是, 開發人員可以在 Windows 容器所提供的一致環境中執行應用程式。 只有特定版本才會出現的問題可以立即發現, 而不是在預備或生產環境中呈現。 開發小組成員使用的開發環境, 在容器中執行應用程式時的差異較少。

容器化應用程式也具有簡單的相應放大麯線。 容器化應用程式可讓您在 VM 或實體機器中擁有更多應用程式和服務實例 (以容器為基礎), 相較于每部電腦的一般應用程式部署。 這會轉譯為較高的密度和較少的必要資源, 特別是當您使用類似 Kubernetes 的協調器時。

在理想的情況下, 容器化並不需要對應用程式代碼 (C\#) 進行任何變更。 在大部分的情況下, 您只需要 Docker 部署中繼資料檔案 (Dockerfile 和 Docker Compose 檔案)。

### <a name="next-steps"></a>後續步驟

在 GitHub wiki 深入探索此內容:

- [如何使用 Windows 容器和 Docker 容器化 .NET Framework web 應用程式](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [將 Docker 支援新增至 WCF 服務](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>逐步解說 3:將以 Windows 容器為基礎的應用程式部署至 Azure Vm

### <a name="technical-walkthrough-availability"></a>技術逐步解說可用性

您可以在 eShopModernizing GitHub 存放庫 wiki 中取得完整的技術逐步解說:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>總覽

在 Azure 中的 Windows Server 2016 虛擬機器 (VM) 上部署至 Docker 主機, 可讓您快速設定開發/測試/預備環境。 此外, 它也會提供測試人員或商務使用者用來驗證應用程式的一般位置。 Vm 也可以是有效的基礎結構即服務 (IaaS) 生產環境。

### <a name="goals"></a>目標

本逐步解說的目標是要說明當您將 Windows 容器部署至以 Windows Server 2016 或更新版本為基礎的 Azure Vm 時, 所擁有的多個替代方案。

### <a name="scenarios"></a>案例

本逐步解說涵蓋數個案例。

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>案例 A:透過 Docker Engine 連線從開發電腦部署至 Azure VM

![透過 Docker 引擎連線從開發電腦部署至 Azure VM](./media/image5-4.png)

**圖 5-4.** 透過 Docker 引擎連線從開發電腦部署至 Azure VM

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>案例 B:透過 Docker Registry 部署至 Azure VM

![透過 Docker Registry 部署至 Azure VM](./media/image5-5.png)

**圖 5-5.** 透過 Docker Registry 部署至 Azure VM

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>案例 C:從 Azure DevOps Services 中的 CI/CD 管線部署至 Azure VM

![從 Azure DevOps Services 中的 CI/CD 管線部署至 Azure VM](./media/image5-6.png)

**圖 5-6。** 從 Azure DevOps Services 中的 CI/CD 管線部署至 Azure VM

### <a name="azure-vms-for-windows-containers"></a>適用于 Windows 容器的 Azure Vm

適用于 Windows 容器的 Azure Vm 是以 Windows Server 2016、Windows 10 或更新版本為基礎的 Vm, 並已設定 Docker 引擎。 在大部分情況下, Azure Vm 中會使用 Windows Server 2016。

Azure 目前提供名為**Windows Server 2016 與容器**的 VM。 您可以使用此 VM 來試用 Windows server Core 或 Windows Nano Server 這項新的 Windows Server 容器功能。 已安裝容器 OS 映射, 然後 VM 即可與 Docker 搭配使用。

### <a name="benefits"></a>權益

雖然 Windows 容器可以部署到內部部署的 Windows Server 2016 Vm, 但當您部署到 Azure 時, 您可以使用立即可用的 Windows Server 容器 Vm, 輕鬆地開始使用。 您也會取得可供測試人員存取的常見線上位置, 並透過 Azure 虛擬機器擴展集自動調整規模。

### <a name="next-steps"></a>後續步驟

在 GitHub wiki 深入探索此內容:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>逐步解說 4:將以 Windows 容器為基礎的應用程式部署至 Azure 容器實例 (ACI)

### <a name="technical-walkthrough-availability"></a>技術逐步解說可用性

您可以在 eShopModernizing GitHub 存放庫 wiki 中取得完整的技術逐步解說:

[將應用程式部署至 ACI (Azure 容器實例)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>總覽

[Azure 容器實例 (ACI)](https://docs.microsoft.com/azure/container-instances/)是擁有容器開發/測試/預備環境的最快方式, 您可以在其中部署容器的單一實例。

### <a name="goals"></a>目標

本逐步解說會示範將 Windows 容器部署至 Azure 容器實例 (ACI) 時的主要案例, 以及如何將 eShopModernizing 應用程式部署到 ACI。

### <a name="scenarios"></a>案例

將 eShopModernizing 應用程式部署至 ACI 可能會有一些變化, 例如只部署一個或所有應用程式 (MVC 應用程式、WebForms 應用程式或 WCF 服務)。 在下面所示的案例中, 您可以看到 ASP.NET MVC 應用程式加上 SQL Server 容器, 這兩個都是以容器形式部署至 ACI (Azure 容器實例)。

![從開發環境部署至 ACI](./media/image5-3.5.6.png)

### <a name="benefits"></a>權益

Azure 容器實例可讓您輕鬆地在 Azure 中建立及管理 Docker 容器, 而不需要布建虛擬機器或採用更高層級的服務。 使用 ACI 時, 您可以直接在 Azure 中部署 Windows 容器, 並使用完整功能變數名稱 (FQDN) 在幾秒內向網際網路公開 (前提是您已在 docker 主機 (例如 Docker Hub 或 Azure 容器) 中準備好 Windows 容器映射登錄)。

### <a name="considerations"></a>考量

將具有完整 .NET Framework/ASP.NET 或 SQL Server 的 Windows 容器部署至 Azure 容器實例 (ACI) 並不像部署到一般 Docker 主機 (例如 Windows Server 2016 with Windows 容器) 一樣快速, 因為 Docker 映射必須是每次都已下載 (從 Docker 登錄中提取), 而 SQL 容器映射的大小 (15.1 GB) 和 ASP.NET 容器映射 (13.9 GB) 很大, 但比維護您自己的 Docker 主機 (永久線上) 更便宜Windows Server 2016 搭配 Azure 中的 Windows 容器 VM) 不會提及整個協調器, 例如 Azure 中的 Kubernetes (AKS), 另一方面, 這是生產部署的絕佳選擇。

主要結論是, 使用 Azure 容器實例對於開發/測試案例和 CI/CD 管線而言, 是非常吸引人的選項。

## <a name="next-steps"></a>後續步驟

在 GitHub wiki 深入探索此內容:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>逐步解說 5:將以 Windows 容器為基礎的應用程式部署至 Azure Container Service 中的 Kubernetes

### <a name="technical-walkthrough-availability"></a>技術逐步解說可用性

您可以在 eShopModernizing GitHub 存放庫 wiki 中取得完整的技術逐步解說:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>總覽

以 Windows 容器為基礎的應用程式, 很快就需要使用平臺, 甚至從 IaaS Vm 繼續進行。 這是為了輕鬆達成高擴充性和更好的自動化擴充性, 以及在自動化部署和版本控制方面的重大改進所需要的。 您可以使用[Azure Container service](https://azure.microsoft.com/services/container-service/)中提供的 orchestrator [Kubernetes](https://kubernetes.io/)來達到這些目標。

### <a name="goals"></a>目標

本逐步解說的目標是要瞭解如何在 Azure Container Service 中, 將 Windows 容器型應用程式部署至 Kubernetes (也稱為*K8s*)。 從頭開始部署至 Kubernetes 是兩個步驟的程式:

1. 將 Kubernetes 叢集部署到 Azure Container Service。

2. 將應用程式和相關資源部署至 Kubernetes 叢集。

### <a name="scenarios"></a>案例

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>案例 A:從開發環境直接部署至 Kubernetes 叢集

![從開發環境直接部署至 Kubernetes 叢集](./media/image5-7.png)

**圖 5-7.** 從開發環境直接部署至 Kubernetes 叢集

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>案例 B:從 Azure DevOps Services 中的 CI/CD 管線部署至 Kubernetes 叢集

![從 Azure DevOps Services 中的 CI/CD 管線部署至 Kubernetes 叢集](./media/image5-8.png)

**圖 5-8.** 從 Azure DevOps Services 中的 CI/CD 管線部署至 Kubernetes 叢集

### <a name="benefits"></a>權益

在 Kubernetes 中部署至叢集有許多好處。 最大的好處是, 您會取得生產環境就緒的環境, 您可以根據想要使用的容器實例數目 (現有節點中的內部擴充性), 以及根據叢集中的節點或 Vm 數目來相應放大應用程式 (叢集的全域擴充性)。

Azure Container Service 專為 Azure 優化熱門的開放原始碼工具和技術。 您會取得一個開放的解決方案, 為您的容器和您的應用程式設定提供可攜性。 您可以選取 [大小]、[主機數] 和 [orchestrator 工具-容器服務] 來處理其他所有專案。

有了 Kubernetes, 開發人員就可以從考慮實體和虛擬機器開始, 規劃以容器為中心的基礎結構來加速下列功能, 還有其他能力:

- 以多個容器為基礎的應用程式

- 複寫容器實例和水準自動調整

- 命名和探索 (例如, 內部 DNS)

- 平衡負載

- 輪流更新

- 發佈秘密

- 應用程式健康情況檢查

## <a name="next-steps"></a>後續步驟

在 GitHub wiki 深入探索此內容:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>逐步解說 6:將以 Windows 容器為基礎的應用程式部署至適用于容器的 Azure App Service

### <a name="technical-walkthrough-availability"></a>技術逐步解說可用性

您可以在 eShopModernizing GitHub 存放庫 wiki 中取得完整的技術逐步解說:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>總覽

使用 Windows 容器的簡單容器化應用程式, 可以輕鬆地部署到適用于容器的 Azure App Service。 對於大部分的 Windows 容器型應用程式而言, 這是建議的方法。

### <a name="goals"></a>目標

本逐步解說的目標是瞭解如何部署 Windows 容器型應用程式, 以從登錄 (Docker Hub 或 Azure Container Registry) Azure App Service 容器。

### <a name="scenario"></a>狀況

![將以 Windows 容器為基礎的應用程式部署至適用于容器的 Azure App Service](./media/image5-11.png)

### <a name="benefits"></a>權益

部署至容器的 Azure App Service 可提供與 Azure App Service 的 PaaS 優點配對之容器的優點。 App service 可輕鬆地以垂直和水準方式調整, 並可設定為符合不斷變化的需求。 您也可以輕鬆地在不停機的情況中執行更新, 以及從登錄中設定連續部署。

## <a name="next-steps"></a>後續步驟

在 GitHub wiki 深入探索此內容:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [上一頁](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [下一頁](conclusions.md)
