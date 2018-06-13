---
title: 將現有的.NET 應用程式部署為 Windows 容器
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器 |將現有的.NET 應用程式部署為 Windows 容器
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 829f33aba14d79d7d9003d1ac7472a19060d401a
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957998"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>將現有的.NET 應用程式部署為 Windows 容器

Windows 容器為基礎的部署都適用於雲端最佳化應用程式和雲端原生應用程式。

不過，本指南中，尤其是在下列各節中，它通常著重於使用 Windows 容器*雲端最佳化*您不需要 rearchitect 您的應用程式的應用程式。

## <a name="what-are-containers-linux-or-windows"></a>什麼是容器？ （Linux 或 Windows）

容器是來包裝其本身的隔離套件將應用程式的方式。 在其容器中，應用程式不會受到應用程式或存在容器之外的處理程序。 所有應用程式依存執行已成功為處理序是在容器內。 無論在何處容器可能會移動，應用程式會永遠符合需求，方面直接相依性，因為它套件組合，它必須執行 （程式庫相依性、 執行階段，等等） 的所有項目。

容器的主要特性是，它會使環境相同跨不同的部署由於容器本身隨附它需要的所有相依性。 您可以在您的電腦上偵錯應用程式，並再部署到另一部電腦，以保證在相同的環境。

容器是容器映像的執行個體。 容器映像是封裝的應用程式或服務 （例如快照集），然後再可靠且可重現的方式部署它的方法。 您可以說，Docker 不只技術它也的基本概念和程序。

由於容器每天變得更為常見，它們會變得業界 「 部署單位 」。

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>容器 （在 Linux 或 Windows 上的 Docker 引擎） 的優點

使用容器來建置應用程式，可能也會定義為輕量型的建置組塊優惠大幅提高靈活度來建立、 傳送、 及執行任何應用程式中，於任何基礎結構中。

透過容器，您可以採取任何應用程式從開發到生產環境與少量或沒有程式碼變更，這點受惠 Microsoft 開發人員工具、 作業系統和雲端間的 Docker 整合。

當您部署到純文字的 Vm 時，您可能已經有方法可供部署 ASP.NET 應用程式到您的 Vm。 可能是，不過，您的方法牽涉到多個手動步驟或複雜的自動化程序使用 Puppet，這類部署工具或類似的工具。 您可能需要執行工作，例如修改設定項目、 複製，在伺服器之間的應用程式內容和執行.msi 安裝，後面接著測試為基礎的互動式安裝程式。 在部署中的所有這些步驟加入部署時間和風險。 相依性不存在於目標環境時，將會發生失敗。

在 Windows 容器中，已完全自動化封裝應用程式的程序。 Windows 容器根據 Docker 平台，提供自動更新與回復容器部署。 使用 Docker 引擎而獲得的主要改善就是您建立映像，就像是您的應用程式的快照集，所有相依性。 映像是指 Docker 映像 （Windows 容器映像，在此情況下）。 在容器中，執行 ASP.NET 應用程式，不需回到原始碼映像。 容器的快照集變得的部署單位。

許多組織會 containerizing 整合的現有應用程式，原因如下：

-   **釋放透過提升部署的靈活度**。 容器可提供一致的部署之間的合約開發和作業。 當您使用容器時，您將聽到說出的開發人員、"﹐ 我的電腦，為何不在生產環境中？ 」 他們可以說，「 執行當做容器時，其會在生產環境中執行。 」 已封裝應用程式，其相依性，可以在任何支援的容器型環境中執行。 它會執行它要設定所有的部署目標 （開發、 品管暫存、 生產環境） 中執行的方式。 容器會消除大部分 frictions 當他們從一個階段移到下一步，可大幅提升部署，您可以更快速及提供。

-   **成本大幅降低**。 容器會導致較低的成本，藉由移除現有的硬體，或是從執行的應用程式在更高的密度，每個單位的硬體與彙總。

-   **可攜性**。 容器是模組化和可移植。 Docker 容器支援的任何伺服器作業系統 （Linux 和 Windows） 中任何主要公用雲端 （Microsoft Azure、 AWS Amazon、 Google、 IBM） 中的內部和私用或混合式雲端環境。

-   **控制**。 容器可提供彈性且安全的環境控制容器層級。 容器可以保護、 隔離，和即使受限於在容器上設定執行原則的條件約束。 關於 Windows 容器 > 一節中有詳細說明，Windows Server 2016 和 HYPER-V 容器可提供額外的企業支援選項。

靈活度、 可攜性和控制項中的重大改良最終會導致顯著的成本大幅降低當您使用容器來開發和維護應用程式。

## <a name="what-is-docker"></a>什麼是 Docker？

[Docker](https://www.docker.com/)是[開放原始碼專案](https://github.com/docker/docker)，自動化應用程式的部署，做為可攜式且足可雲端或內部部署中執行的容器。 Docker 也是升級及發展這項技術的[公司](https://www.docker.com/)。 公司中共同作業與雲端，Linux 和 Windows 廠商，包括 Microsoft 的運作方式。

![](./media/image6.png)

> **圖 4-6。** Docker 將容器部署在混合式雲端的所有圖層

給其他人熟悉的虛擬機器，容器可能會出現非常類似。 容器執行作業系統、 具有檔案系統，而且可以存取網路，就像實體或虛擬電腦系統上。 不過，在容器的基本概念與技術是從虛擬機器非常不同。 從開發人員觀點來看，容器必須被視為一個單一處理程序。 事實上，容器會有一個處理序的單一進入點。

Docker 容器 (為了簡單起見，*容器*) 可以原生 Linux 及 Windows 上執行。 僅限於 Windows 主機 （主機伺服器或 VM） 上執行時一般容器，可以執行 Windows 容器和 Linux 容器可以只在 Linux 主機上執行。 不過，在最新版 Windows Server 和 HYPER-V 容器的詳細資訊，Linux 容器也可以執行原生 Windows Server 上使用 HYPER-V 隔離技術，目前僅適用於 Windows Server 容器。

在不久的將來，可能發生而且甚至一般，將會包含 Linux 和 Windows 容器的混合式的環境。

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>對於現有的.NET 應用程式的 Windows 容器的優點

使用 Windows 容器的優點基本上都是相同的優點，您通常從容器取得。 使用 Windows 容器是關於大幅改善靈活度、 可攜性，以及控制項。

現有的.NET 應用程式是指使用.NET Framework 所建立的那些應用程式。 例如，它們可能是傳統的 ASP.NET web 應用程式-不使用.NET 核心的較新，並可執行跨平台上 Linux、 Windows 和 MacOS。

.NET Framework 中主要的相依性是 Windows。 它也會有次要相依性，例如 IIS 和 System.Web 在傳統的 ASP.NET。

.NET Framework 應用程式必須在 Windows 中，期間執行。 如果您想要化現有的.NET Framework 應用程式，您無法或不想要投資移轉至.NET Core （「 如果能夠正常運作，不移轉 」），您有容器的唯一選擇是使用 Windows 容器。

因此，Windows 容器的主要優點是，它們提供您的方式，來現代化現有的.NET Framework 應用程式上 Windows 透過得以執行。 最後，Windows 容器獲得您想要使用容器靈活度、 可攜性和更佳控制的優點。

## <a name="choose-an-os-to-target-with-net-based-containers"></a>選擇要鎖定的作業系統。以網路為基礎的容器

提供多樣化的 Docker，以及.NET Framework 和.NET Core 之間的差異所支援的作業系統，您應將目標設特定作業系統和您使用的架構為基礎的特定版本。

針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。 這些 Windows 版本提供不同的特性 （例如與自我裝載的 web 伺服器 Kestrel 例如 IIS) 可能需要.NET Framework 或.NET Core 應用程式。

針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。

圖 4-7 顯示您可以為目標，根據應用程式的.NET Framework 版本的作業系統版本。

![](./media/image7.png)

> **圖 4-7。** 目標.NET Framework 版本為基礎的作業系統

在現有或舊版.NET Framework 應用程式為基礎的應用程式的移轉案例，主要的相依性是在 Windows 和 IIS 上。 唯一的選擇是使用 Windows Server Core 和.NET Framework 為基礎的 Docker 映像。

當您將映像名稱加入您 Dockerfile 的檔案時，您可以選取使用的標記，如下列範例針對以.NET Framework 為基礎的 Windows 容器映像的作業系統和版本：

> | **標記** | **系統與版本** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET framework 4.x 在 Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET framework 4.x 與其他 ASP.NET 自訂程序，在 Windows Server Core |

適用於.NET Core （跨平台適用於 Linux 和 Windows），標記看起來會如下所示：

> | **標記** | **系統與版本**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET core 2.0 執行階段僅 on Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | .NET core 2.0 執行階段僅限 Windows Nano Server 上 |

### <a name="multi-arch-images"></a>多重 arch 映像

自 mid 2017 起，您也可以使用的新功能中呼叫的 Docker[多 arch](https://github.com/moby/moby/issues/15866)映像。 .NET core Docker 映像可以使用多 arch 標記。 Dockerfile 的檔案不再需要定義您的目標的作業系統。 多重 arch 的功能可讓單一標記使用於跨多個電腦組態。 比方說，多重架構，您可以使用一個通用的標記： **microsoft/dotnet:2.0.0-runtime**。 如果提取該標記從 Linux 容器環境時，您會取得 Debian 基礎映像。 如果提取該標籤，從 Windows 容器環境時，您會取得 Nano Server 基礎映像。

.NET Framework 映像，因為傳統的.NET Framework 支援只有 Windows，您無法使用多重 arch 功能。

## <a name="windows-container-types"></a>Windows 容器類型

類似 Linux 容器使用 Docker 引擎會管理 Windows Server 容器。 不同於 Linux 容器，Windows 容器包含兩種不同的容器類型，或執行時間-Windows Server 容器和 HYPER-V 隔離。

**Windows Server 容器**： 提供透過程序和命名空間隔離技術的應用程式隔離。 Windows Server 容器與容器主機和主機執行的所有容器共用核心。 這些容器不提供惡意的安全性界限，而且不應該用來找出不受信任的程式碼。 因為共用的核心空間，而這些容器需要相同的核心版本和組態。

**HYPER-V 隔離**： 擴充了 Windows Server 容器提供高度最佳化的 VM 上執行每個容器的隔離。 在此組態中，容器主機的核心不會與相同的主機上的其他容器共用。 這些容器專為惡意多租用戶，使用裝載於虛擬機器的相同安全性保證。 因為這些容器不與主機或主機上的其他容器共用核心，可以執行核心與不同的版本和設定 （但有支援的版本）。 例如，在 Windows 10 上的所有 Windows 容器會都使用 HYPER-V 隔離以便利用 Windows Server 核心版本和組態。

在 Windows 上執行的容器或 HYPER-V 隔離不是執行階段決定。 您可能會選擇一開始，HYPER-V 隔離建立容器，並在執行階段，請選擇執行做為 Windows Server 容器。

### <a name="additional-resources"></a>其他資源

-   **Windows 容器文件**

    [https://docs.microsoft.com/virtualization/windowscontainers/](https://docs.microsoft.com/virtualization/windowscontainers/)

-   **Windows 容器的基本概念**

    [https://docs.microsoft.com/virtualization/windowscontainers/about/](https://docs.microsoft.com/virtualization/windowscontainers/about/)

-   **資訊圖： Microsoft 和容器**

    [https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf](https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf)


## <a name="the-container-ecosystem-in-azure"></a>在 Azure 中的容器生態系統

上一節，它有已說明 Docker 容器的優點為以及對於.NET 應用程式特定的容器映像的詳細資訊。 一般資訊是為了開發或化應用程式的基礎。
不過，在思考生產部署環境或甚至不必在 QA 和開發/測試環境，Microsoft Azure 提供開放且廣泛的各種選項，完整容器生態系統，在雲端 （如下圖所示）。 根據特定應用程式的需求，您應該選擇一個或另一個 Azure 的產品。

![](./media/image7.5.png)

> **圖 4-7.5。** 在 Azure 中的容器生態系統

從容器生態系統在 Azure 中，下列產品支援會被視為基礎結構的容器：
-   **Azure 容器執行個體 (ACI)**
-   **Azure 虛擬機器**（與容器的支援）
-   **Azure 虛擬機器擴展集**（與容器的支援）

從這些三，ACI 提供極大的好處，也就是您不需要維護基礎作業系統，不需要您升級/修補程式等等，但 ACI 仍位於基礎結構層級，這本書的後續各節中會有進一步說明中的事實。

Azure 會在同一時間放置在 PaaS （平台即服務） 的多層級的支援容器中的產品為：

-   **Azure App Service**
-   **Azure Kubernetes 服務 （AKS 和 ACS）**
-   **Azure Service Fabric** 
-   **Azure 批次** 

接著，Azure 容器登錄中是高可擴充容器登錄中您可以從所有先前產品登錄與部署您的自訂容器映像時使用的 Azure 中託管。

此外，從您的容器，您可以使用其他受管理的服務在 Azure SQL Database、 Azure Redis 快取 Azure Cosmos DB，例如 Azure 中等等。 加上有可用的協力廠商解決方案平台在 Azure Marketplace 雲端 Foundry 和 OpenShift，您也可以使用在 Azure 中的容器中。 

在下一步 區段中，您可以瀏覽 Microsoft 何時使用每個這些 Azure 產品和解決方案，特別是當目標為 Windows 容器時的建議事項。


>[!div class="step-by-step"]
[上一頁](what-about-cloud-native-applications.md)
[下一頁](when-not-to-deploy-to-windows-containers.md)
