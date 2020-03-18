---
title: 逐步解說和技術入門概觀
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |演練和技術入門概述
ms.date: 04/28/2018
ms.openlocfilehash: 190b33c4307b09bab0543d481e66ac9328074a0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "69660890"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>逐步解說和技術入門概觀

為了限制此電子書的大小，在 GitHub 存儲庫中提供了其他技術文檔和完整的演練。 本章中描述的線上系列演練介紹了基於 Windows 容器的多個環境的分步設置以及部署到 Azure。

以下各節介紹每個演練的內容、目標和高級願景，並提供所涉及的任務的圖表。 你可以在*eShop 現代化*應用程式 GitHub 存儲庫 wiki 的<https://github.com/dotnet-architecture/eShopModernizing/wiki>eShop 現代化應用程式中獲得演練。

## <a name="technical-walkthrough-list"></a>技術演練清單

以下入門演練為示例應用提供一致且全面的技術指導，您可以使用容器提升和移動，然後在 Azure 中使用多個部署選項進行移動。

以下每個演練都使用新的示例 eShopLegacy 和 eShop 現代化應用，這些應用程式可在 GitHub 上<https://github.com/dotnet-architecture/eShopModernizing>提供。

- **參觀 eShop 舊版應用（要進行現代化的基線應用）**

- **使用 Windows 容器將現有ASP.NET Web 應用（Web 表單& MVC）容器化**

- **使用 Windows 容器將現有 WCF 服務（N 層應用）容器化**

- **將基於 Windows 容器的應用部署到 Azure VM**

- **在 Azure 容器服務中將基於 Windows 容器的應用部署到庫伯內斯**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>演練 1：eShop 傳統應用之旅

### <a name="technical-walkthrough-availability"></a>技術演練可用性

完整的技術演練可在 eShop 現代化 GitHub 存儲庫 wiki 中提供：

[eShop 現代化維琪演練](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>概觀

在本演練中，您可以探討三個示例遺留應用程式的初始實現。 前兩個示例 Web 應用具有整體體系結構，並使用經典ASP.NET創建。 一個應用程式基於ASP.NET 4.x MVC;第二個應用程式基於ASP.NET 4.x Web 表單。
第三個應用是由用戶端 WinForms 應用和伺服器端[Windows 通信基礎 （WCF）](../../framework/wcf/whats-wcf.md)服務組成的 3 層應用。

所有這些應用程式都可以在[eShop現代化GitHub存儲庫](https://github.com/dotnet-architecture/eShopModernizing)中使用。

### <a name="goals"></a>目標

本演練的主要目標是熟悉這些應用及其代碼和配置。 您可以配置應用，以便它們生成和使用類比資料，而無需使用 SQL 資料庫進行測試。 此可選配置基於依賴項注入，以分離方式使用。

### <a name="scenario-1-aspnet-web-apps"></a>方案 1：ASP.NET Web 應用

下圖顯示了原始遺留ASP.NET Web 應用程式的簡單方案。

![原始遺留ASP.NET Web 應用程式的簡單體系結構方案](./media/image5-1.png)

從業務域的角度來看，這兩個應用都提供相同的目錄管理功能。 eShop 企業團隊的成員將使用該應用程式查看和編輯產品目錄。

下圖顯示了初始應用螢幕截圖。

![ASP.NET MVC 和ASP.NET Web 表單應用程式（現有/遺留技術）](./media/image5-2.png)

ASP.NET 4.x 或早期版本中的依賴項（對於 MVC 或 Web 表單）意味著這些應用程式不會在 .NET Core 上運行，除非使用 ASP.NET 核心 MVC 完全重寫代碼。

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>方案 2：WCF 服務和 WinForms 用戶端應用（3 層應用）

下圖顯示了原始 3 層舊應用程式的簡單方案。

![具有 WCF 服務和 WinForms 用戶端應用的原始傳統 3 層應用的簡單體系結構方案](./media/image5-1.5.png)

### <a name="benefits"></a>優點

本演練的好處很簡單：只需熟悉代碼和初始應用即可。

### <a name="next-steps"></a>後續步驟

在 GitHub wiki 上更深入地流覽此內容：

- [在 MVC 和 Web 表單"舊"應用ASP.NET基線進行巡視](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [流覽基線 WCF 服務和 WinForms（3 層）"舊"應用程式](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>演練 2：使用 Windows 容器對現有的 .NET 應用程式進行容器化

### <a name="overview"></a>概觀

使用 Windows 容器改進現有 .NET 應用程式的部署，例如基於 MVC、Web 表單或 WCF 的應用程式，以生產、開發和測試環境。

### <a name="goals"></a>目標

本演練的目標是向您展示用於容器化現有 .NET 框架應用程式的幾個選項。 您可以：

- 使用 Visual Studio [2017 Docker 工具](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)（Visual Studio 2017 或更高版本）對應用程式進行容器化。

- 通過手動添加[Docker 檔](https://docs.docker.com/engine/reference/builder/)，然後使用[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)來容器化應用程式。

- 使用[Img2Docker](https://github.com/docker/communitytools-image2docker-win)工具（Docker 的開源工具）對應用程式進行容器化。

本演練重點介紹 Visual Studio 2017 Docker 工具方法，但其他兩種方法在使用 Dockerfile 方面相當相似。

### <a name="scenario-1-containerized-aspnet-web-apps"></a>方案 1：容器化ASP.NET Web 應用

下圖顯示了容器化 eShop 舊版 Web 應用程式的方案。

![簡化開發環境中的容器化ASP.NET應用程式的體系結構圖](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>方案 2：容器化 WCF 服務

下圖顯示了具有容器化 WCF 服務的 3 層應用的方案。

![開發環境中容器化 WCF 服務的簡化體系結構圖](./media/image5-3.5.png)

### <a name="benefits"></a>優點

在容器中運行整體應用程式具有優勢。 首先，為應用程式創建映射。 從那時起，每個部署都在同一環境中運行。 每個容器使用相同的作業系統版本，安裝相同的依賴項版本，使用相同的 .NET 框架版本，並且使用相同的進程構建。 基本上，您可以使用 Docker 映射來控制應用程式的依賴項。 部署容器時，依賴項隨應用程式一起移動。

另一個好處是，開發人員可以在 Windows 容器提供的一致環境中運行應用程式。 可以立即發現僅在某些版本中顯示的問題，而不是在暫存或生產環境中出現。 當應用程式在容器中運行時，開發團隊成員使用的開發環境的差異就不那麼重要了。

容器化應用也有平坦的橫向擴展曲線。 與每台電腦的常規應用程式部署相比，容器化應用使您能夠在 VM 或物理電腦中有更多的應用程式和服務實例（基於容器）。 這轉化為更高的密度和更少的所需資源，特別是當您使用像 Kubernetes 這樣的協調器時。

在理想情況下，容器化不需要對應用程式代碼 （C\#） 進行任何更改。 在大多數情況下，您只需要 Docker 部署元資料檔案（Dockerfile 和 Docker 撰寫檔）。

### <a name="next-steps"></a>後續步驟

在 GitHub wiki 上更深入地流覽此內容：

- [如何使用 Windows 容器和 Docker 對 .NET 框架 Web 應用進行容器化](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [將 Docker 支援添加到 WCF 服務](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>演練 3：將基於 Windows 容器的應用部署到 Azure VM

### <a name="technical-walkthrough-availability"></a>技術演練可用性

完整的技術演練可在 eShop 現代化 GitHub 存儲庫 wiki 中提供：<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>概觀

部署到 Azure 中的 Windows Server 2016 虛擬機器 （VM） 上的 Docker 主機，可以快速設置開發/測試/暫存環境。 它還為測試人員或企業用戶提供了驗證應用的常見位置。 VM 也可以是有效的基礎架構即服務 （IaaS） 生產環境。

### <a name="goals"></a>目標

本演練的目標是向您展示將 Windows 容器部署到基於 Windows Server 2016 或更高版本的 Azure VM 時具有的多種替代方法。

### <a name="scenarios"></a>案例

本演練將介紹幾種方案。

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>方案 A：通過 Docker 引擎連接從開發 PC 部署到 Azure VM

![通過 Docker 引擎連接從開發 PC 部署到 Azure VM](./media/image5-4.png)

**圖 5-4。** 通過 Docker 引擎連接從開發 PC 部署到 Azure VM

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>方案 B：通過 Docker 註冊表部署到 Azure VM

![通過 Docker 註冊表部署到 Azure VM](./media/image5-5.png)

**圖 5-5。** 通過 Docker 註冊表部署到 Azure VM

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>方案 C：從 Azure DevOps 服務中的 CI/CD 管道部署到 Azure VM

![從 Azure DevOps 服務中的 CI/CD 管道部署到 Azure VM](./media/image5-6.png)

**圖 5-6。** 從 Azure DevOps 服務中的 CI/CD 管道部署到 Azure VM

### <a name="azure-vms-for-windows-containers"></a>用於 Windows 容器的 Azure VM

Windows 容器的 Azure VM 是基於 Windows 伺服器 2016、Windows 10 或更高版本的 VM，兩者都設置了 Docker 引擎。 在大多數情況下，Windows Server 2016 在 Azure VM 中使用。

Azure 目前提供一個名為**Windows Server 2016 的 VM，其中包含容器**。 您可以使用此 VM 嘗試新的 Windows 伺服器容器功能，使用 Windows 伺服器核心或 Windows Nano 伺服器。 安裝容器作業系統映射，然後 VM 即可與 Docker 一起使用。

### <a name="benefits"></a>優點

儘管 Windows 容器可以部署到本地 Windows Server 2016 VM，但當您部署到 Azure 時，您可以通過隨時使用的 Windows Server 容器 VM 獲得一種更簡單的入門方法。 您還可以獲得測試人員可訪問的常見連線位置，以及通過 Azure 虛擬機器縮放集自動可伸縮。

### <a name="next-steps"></a>後續步驟

在 GitHub wiki 上更深入地流覽此內容：

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>演練 4：將基於 Windows 容器的應用部署到 Azure 容器實例 （ACI）

### <a name="technical-walkthrough-availability"></a>技術演練可用性

完整的技術演練可在 eShop 現代化 GitHub 存儲庫 wiki 中提供：

[將應用部署到 ACI（Azure 容器實例）](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>概觀

[Azure 容器實例 （ACI）](https://docs.microsoft.com/azure/container-instances/)是具有容器開發/測試/暫存環境的最快方法，您可以在其中部署容器的單個實例。

### <a name="goals"></a>目標

本演練將 Windows 容器部署到 Azure 容器實例 （ACI） 時的主要方案，以及如何將 eShop 現代化應用部署到 ACI 中。

### <a name="scenarios"></a>案例

在將 eShop 現代化應用部署到 ACI 方面可能會有一些差異，例如只部署一個或多個應用（MVC 應用、WebForms 應用或 WCF 服務）。 在下面顯示的以下方案中，您可以看到ASP.NET MVC 應用以及 SQL Server 容器都作為容器部署到 ACI（Azure 容器實例）中。

![從開發環境部署到 ACI](./media/image5-3.5.6.png)

### <a name="benefits"></a>優點

Azure Container Instances 能讓您在 Azure 中輕鬆建立及管理 Docker 容器，不需要佈建虛擬機器或採用高階服務即可完成。 使用 ACI，可以直接在 Azure 中部署 Windows 容器，並在數秒內使用完全限定的功能變數名稱 （FQDN） 將其公開到 Internet 上（前提是您在 Docker Hub 或 Azure 容器等 Docker 註冊表中準備好 Windows 容器映射註冊表）。

### <a name="considerations"></a>考量

將具有完整 .NET 框架/ASP.NET或 SQL Server 的 Windows 容器部署到 Azure 容器實例 （ACI） 的速度不如部署到常規 Docker 主機（如 Windows Server 2016 與 Windows 容器一起），因為每次必須下載 Docker 映射（從 Docker 註冊表中拉出），SQL 容器映射（15.1 GB）和ASP.NET容器映射（13.9 GB）的大小明顯較大， 然而，它比維護自己的 Docker 主機（永久線上 Windows）便宜得多伺服器 2016 在 Azure 中包含 Windows 容器 VM），更不用說像 Azure （AKS） 中的 Kubernetes 這樣的整個協調器，這是生產部署的絕佳選擇。

作為主要結論，對於開發人員/測試方案和 CI/CD 管道，使用 Azure 容器實例是一個非常引人注目的選項。

## <a name="next-steps"></a>後續步驟

在 GitHub wiki 上更深入地流覽此內容：

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>演練 5：將基於 Windows 容器的應用部署到 Azure 容器服務中的庫伯內斯

### <a name="technical-walkthrough-availability"></a>技術演練可用性

完整的技術演練可在 eShop 現代化 GitHub 存儲庫 wiki 中提供：

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>概觀

基於 Windows 容器的應用程式將快速使用平臺，甚至遠離 IaaS VM。 這一點對於輕鬆實現高可擴充性和更好的自動化可擴充性，以及自動化部署和版本控制的重大改進，需要這樣做。 您可以使用[Azure 容器服務](https://azure.microsoft.com/services/container-service/)中可用的協調器[Kubernetes](https://kubernetes.io/)來實現這些目標。

### <a name="goals"></a>目標

本演練的目標是瞭解如何在 Azure 容器服務中將基於 Windows 容器的應用程式部署到 Kubernetes（也稱為*K8s）。* 從頭開始部署到庫伯奈斯是一個兩步過程：

1. 將庫伯內斯群集部署到 Azure 容器服務。

2. 將應用程式和相關資源部署到庫伯奈斯群集。

### <a name="scenarios"></a>案例

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>方案 A：直接從開發環境部署到庫伯奈斯群集

![直接從開發環境部署到庫伯奈斯群集](./media/image5-7.png)

**圖 5-7。** 直接從開發環境部署到庫伯奈斯群集

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>方案 B：從 Azure DevOps 服務中的 CI/CD 管道部署到 Kubernetes 群集

![從 Azure DevOps 服務中的 CI/CD 管道部署到 Kubernetes 群集](./media/image5-8.png)

**圖 5-8。** 從 Azure DevOps 服務中的 CI/CD 管道部署到 Kubernetes 群集

### <a name="benefits"></a>優點

部署到庫貝內斯的群集有很多好處。 最大的好處是，您可以獲得一個生產就緒的環境，您可以在其中根據要使用的容器實例數（現有節點中的內部可伸縮性）以及群集中的節點或 VM 數量來擴展應用程式（群集的全域可伸縮性）。

Azure 容器服務優化了專為 Azure 而使用的熱門開源工具和技術。 您將獲得一個開放的解決方案，既為您的容器提供可攜性，也可用於應用程式佈建。 您可以選擇大小、主機數，協調器工具-容器服務處理其他所有內容。

借助 Kubernetes，開發人員可以從考慮物理和虛擬機器，到規劃以容器為中心的基礎結構，從而促進以下功能，等等：

- 基於多個容器的應用程式

- 複製容器實例和水準自動縮放

- 命名和發現（例如，內部 DNS）

- 平衡負載

- 滾動更新

- 分發機密

- 應用程式運行狀況檢查

## <a name="next-steps"></a>後續步驟

在 GitHub wiki 上更深入地流覽此內容：<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>演練 6：將基於 Windows 容器的應用部署到容器的 Azure 應用服務

### <a name="technical-walkthrough-availability"></a>技術演練可用性

完整的技術演練可在 eShop 現代化 GitHub 存儲庫 wiki 中提供：

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>概觀

使用 Windows 容器的簡單容器化應用程式可以輕鬆地部署到容器的 Azure 應用服務。 對於大多數基於 Windows 容器的應用程式，這是推薦的方法。

### <a name="goals"></a>目標

本演練的目標是瞭解如何從註冊表（Docker Hub 或 Azure 容器註冊表）將基於 Windows 容器的應用程式部署到適用于容器的 Azure 應用服務。

### <a name="scenario"></a>狀況

![將基於 Windows 容器的應用部署到容器的 Azure 應用服務](./media/image5-11.png)

### <a name="benefits"></a>優點

為容器部署到 Azure 應用服務提供了與 Azure 應用服務的 PaaS 優勢配對的容器的優勢。 應用服務可以輕鬆垂直和水準縮放，並可配置為自動縮放以滿足不斷變化的需求。 更新可以在零停機時間下執行，並且從註冊表進行連續部署的配置也很容易配置。

## <a name="next-steps"></a>後續步驟

在 GitHub wiki 上更深入地流覽此內容：<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [上一個](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [下一個](conclusions.md) <!-- Next Chapter -->
