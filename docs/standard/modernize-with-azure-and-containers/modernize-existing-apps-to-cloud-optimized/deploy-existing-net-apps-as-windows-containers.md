---
title: 將現有 .NET 應用程式部署為 Windows 容器
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |將現有.NET 應用程式部署為 Windows 容器
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 9d84924317e7c6e3dd4386f851ee902e2b5a7caf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216661"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>將現有 .NET 應用程式部署為 Windows 容器

Windows 容器為基礎的部署是適用於雲端最佳化應用程式和雲端原生應用程式。

不過，本指南中，尤其是在下列各節中，它大部分著重於使用 Windows 容器*雲端最佳化*您不需要重新架構您的應用程式的應用程式。

## <a name="what-are-containers-linux-or-windows"></a>什麼是容器？ （Linux 或 Windows）

容器是總結自己獨立模式的套件將應用程式的方式。 在其容器中，應用程式不會受到應用程式或容器之外存在的處理程序。 所有應用程式依存執行已成功為處理序在容器內。 容器可能會移動任何地方，應用程式的需求會一律符合，以直接的相依性，因為它隨附於所有執行 （程式庫相依性、 執行階段，等等） 所需要的項目。

容器的主要特性是，它會使環境相同跨不同的部署由於容器本身隨附所有需要的相依性。 您可以在您的電腦上偵錯應用程式，然後再部署到另一部電腦的它保證的相同環境。

容器是容器映像的執行個體。 容器映像已封裝應用程式或服務 （例如快照集），和可靠及可重現的方式將部署的方式。 您可以說，Docker 不只技術 it 也的原理和程序。

容器每天變得更為普遍，因為它們會成為業界 「 部署單位 」。

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>容器 （在 Linux 或 Windows 上的 Docker 引擎） 的優點

使用容器，可用來建置應用程式也可能會定義為輕量級的建置組塊提供大幅增加在靈活度方面，來建置、 出貨，及執行任何應用程式中，於任何基礎結構。

與容器，您可以將任何應用程式從開發到生產環境有少量或沒有程式碼變更，這會在 Microsoft 開發人員工具、 作業系統、 與雲端之間的 Docker 整合。

當您部署到純文字的 Vm 時，您可能已經有方法讓 ASP.NET 應用程式部署到您的 Vm。 可能是，不過，您的方法牽涉到多個手動步驟或複雜的自動化程序使用 Puppet 等部署工具或類似的工具。 您可能需要執行工作，例如修改設定項目、 將應用程式內容，在伺服器之間複製和執行.msi 安裝程式，後面接著測試為基礎的互動式安裝程式。 在部署中的所有這些步驟將加入部署的時間和風險。 相依性不存在目標環境中時，您將會發生失敗。

在 Windows 容器中，封裝應用程式的程序完全自動化。 Windows 容器為基礎的 Docker 平台，可提供自動更新 」 和 「 回復容器部署。 使用 Docker 引擎而獲得的主要改進是，您會建立映像，就像是您的應用程式的快照集，其所有相依性。 映像為 Docker 映像 （Windows 容器映像，在此情況下）。 在容器中執行 ASP.NET 應用程式，而不需要回到原始碼映像。 容器快照會成為部署的單位。

許多組織會將現有單體式應用程式容器化，原因如下：

-   **釋出透過改良的部署的靈活性**。 容器會提供開發與作業之間的一致性部署合約。 當您使用容器時，您將不會聽到開發人員說，「 它能用在我的電腦上為何不在生產環境中？ 」 它們可以說 「 它以執行容器，其會在生產環境中執行。 」 封裝的應用程式，其所有相依性，可以在任何支援的容器型環境中執行。 它會執行它要用來在所有部署目標 （開發、 品管、 暫存、 生產環境） 中執行的方式。 容器會消除大部分的摩擦，它們將移至下一步，可大幅提升部署，從一個階段時，您可以更快交付。

-   **成本降低**。 容器會導致較低成本，藉由彙總與移除現有的硬體，或是從執行的應用程式在更高的密度，每個硬體單位。

-   **可攜性**。 容器是模組化和可攜式。 在任何伺服器作業系統 （Linux 和 Windows），在任何的主要公用雲端 （Microsoft Azure、 Amazon AWS、 Google、 IBM） 和內部部署和私人或混合式雲端環境上支援 docker 容器。

-   **控制**。 容器可提供彈性且安全的環境控制容器層級。 容器可以保護、 隔離，和甚至是有限的容器上設定執行原則的條件約束。 為 Windows 容器的相關章節中所述，Windows Server 2016 和 HYPER-V 容器會提供額外的企業支援選項。

靈活度、 可攜性和控制的重大改進最終會導致重大的成本降低當您使用容器來開發及維護應用程式。

## <a name="what-is-docker"></a>什麼是 Docker？

[Docker](https://www.docker.com/)已[開放原始碼專案](https://github.com/docker/docker)，自動化應用程式部署為可攜式且自給自足的容器可以在雲端或內部部署中執行。 Docker 也是升級及發展這項技術的[公司](https://www.docker.com/)。 該公司可與雲端、 Linux 和 Windows 廠商，包括 Microsoft 共同作業。

![](./media/image6.png)

> **圖 4-6。** Docker 將容器部署在混合式雲端的所有圖層

人熟悉的虛擬機器，容器可能會出現非常類似。 容器執行之作業系統、 具有檔案系統中，而且可以存取網路，就像實體或虛擬電腦系統上。 不過，容器的基本概念與技術會大為不同的虛擬機器。 從開發人員的觀點而言，容器必須被視為更單一處理序。 事實上，容器會有一個處理序的單一進入點。

Docker 容器 (為了簡單起見，*容器*) 可以在 Linux 和 Windows 上的原生方式執行。 當執行規則的容器時，Windows 容器可以只在 Windows 主機 （主機伺服器或 VM） 上執行，並只在 Linux 主機上可以執行的 Linux 容器。 不過，在最新版 Windows Server 和 HYPER-V 容器的詳細資訊，Linux 容器也可以執行原生 Windows Server 上使用 HYPER-V 隔離技術，目前僅適用於 Windows Server 容器。

在不久的將來，可能也是更常見，將會有 Linux 和 Windows 容器的混合式的環境。

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>現有.NET 應用程式的 Windows 容器的權益

使用 Windows 容器的優點基本上都是相同的優點，一般情況下獲得容器。 使用 Windows 容器是關於大幅提升靈活度、 可攜性和控制能力。

現有.NET 應用程式是指使用.NET Framework 所建立的應用程式。 比方說，它們可能是傳統的 ASP.NET web 應用程式-將不會使用.NET Core，這是較新且會執行跨平台 Linux、 Windows、 和 MacOS。

主要的相依性，在.NET Framework 是 Windows。 它也會在傳統的 ASP.NET 有次要相依性，例如 IIS 和 System.Web。

.NET Framework 應用程式必須執行 Windows，期限。 如果您想要將現有的.NET Framework 應用程式容器化，您無法或不想要將心力灌注在移轉至.NET Core （「 如果它可以正常運作，不移轉它 」），您有適用於容器的唯一選擇是使用 Windows 容器。

因此，Windows 容器的主要優點之一是，它們提供您用來在現代化現有.NET Framework 應用程式在 Windows 透過容器化上執行。 最後，Windows 容器取得您所要使用容器靈活度、 可攜性和更好的控制能力的優點。

## <a name="choose-an-os-to-target-with-net-based-containers"></a>選擇要使用的目標作業系統。以.NET 為基礎的容器

您應該指定的 Docker，以及.NET Framework 和.NET Core 之間的差異所支援的作業系統多樣性，目標是特定的作業系統和您使用的架構為基礎的特定版本。

針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。 這些 Windows 版本提供 （例如自我裝載的 web 伺服器，例如 Kestrel 與 IIS) 可能需要.NET Framework 或.NET Core 應用程式的不同特性。

針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。

圖 4-7 顯示作業系統版本，您可以為目標，根據應用程式的.NET Framework 版本而定。

![](./media/image7.png)

> **圖 4-7。** 以.NET Framework 版本為基礎的目標作業系統

在現有或舊版的應用程式以.NET Framework 應用程式為基礎的移轉案例中，主要的相依性是在 Windows 和 IIS。 您的唯一選項是使用 Windows Server Core 和.NET Framework 為基礎的 Docker 映像。

當您將映像名稱加入您的 Dockerfile 檔案時，您可以選取的作業系統和版本所使用的標記，如下列範例，說明.NET Framework 為基礎的 Windows 容器映像所示：

> | **標記** | **系統和版本** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET framework 4.x 在 Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET framework 4.x 與其他 ASP.NET 自訂，在 Windows Server Core |

.NET Core （跨平台適用於 Linux 和 Windows），標記看起來會如下所示：

> | **標記** | **系統和版本**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET core 2.0 執行階段僅限在 Linux 上 |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | .NET core 2.0 執行階段僅限 Windows Nano Server 上 |

### <a name="multi-arch-images"></a>多架構映像

從 2017年開始，您也可以使用的新功能中呼叫的 Docker[多架構](https://github.com/moby/moby/issues/15866)映像。 .NET core Docker 映像可以使用多架構標記。 您的 Dockerfile 檔案不再需要定義您的目標作業系統。 多架構的功能可讓跨多個機器設定使用單一標記。 比方說，多架構，您可以使用一個常見的標記： **microsoft/dotnet:2.0.0-runtime**。 如果您提取該標記從 Linux 容器環境時，您會取得以 Debian 為基礎的映像。 如果您提取該標記從 Windows 容器環境時，您會取得 Nano Server 基礎映像。

針對.NET Framework 映像，因為傳統的.NET Framework 支援只是 Windows，您就無法使用多架構的功能。

## <a name="windows-container-types"></a>Windows 容器類型

Linux 容器，例如 Windows Server 容器會管理使用 Docker 引擎。 與 Linux 容器，不同的是 Windows 容器包含兩種不同的容器類型，或執行時間-Windows Server 容器和 HYPER-V 隔離。

**Windows Server 容器**:提供透過程序和命名空間隔離技術的應用程式隔離。 Windows Server 容器與容器主機和主機執行的所有容器共用核心。 這些容器不提供惡意的安全性界限，而且不應該用來隔離不受信任的程式碼。 因為共用的核心空間，而這些容器會要求相同的核心版本和組態。

**HYPER-V 隔離**:擴充了 Windows Server 容器提供高度最佳化的 VM 上執行每個容器的隔離。 在此組態中，容器主機的核心不會與相同主機上的其他容器共用。 這些容器是針對惡意多租用戶裝載，使用相同的安全性保證，VM 的設計。 因為這些容器不會與主機或主機上的其他容器共用核心，可以使用不同的版本和設定 （具有支援的版本） 執行的核心。 比方說，Windows 10 上的所有 Windows 容器會都使用 HYPER-V 隔離，利用 Windows Server 的核心版本和組態。

在 Windows 上執行的容器，包含或不含 HYPER-V 隔離是執行階段的決策。 您可以選擇一開始，建立容器與 HYPER-V 隔離，並在執行階段，選擇改為執行 Windows Server 容器。

### <a name="additional-resources"></a>其他資源

-   **Windows 容器文件**

    [https://docs.microsoft.com/virtualization/windowscontainers/](https://docs.microsoft.com/virtualization/windowscontainers/)

-   **Windows 容器基本概念**

    [https://docs.microsoft.com/virtualization/windowscontainers/about/](https://docs.microsoft.com/virtualization/windowscontainers/about/)

-   **資訊圖︰Microsoft 和容器**

    [https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf](https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf)

## <a name="the-container-ecosystem-in-azure"></a>在 Azure 中的容器生態系統

在先前章節中，它有已說明 Docker 容器的優點是在.NET 應用程式特定的容器映像的詳細資料。 一般資訊是為了開發，或將容器化應用程式的基礎。
不過，當考慮生產部署環境或甚至 QA 和開發/測試環境，Microsoft Azure 會提供開放且廣泛的各種選項，完整容器生態系統在雲端 （如圖所示）。 根據特定應用程式的需求，您應該選擇一個或另一個 Azure 產品。

![](./media/image7.5.png)

> **圖 4-7.5。** 在 Azure 中的容器生態系統

容器生態系統在 Azure 中，下列的產品支援是基礎結構的容器：
-   **Azure Container Instances (ACI)**
-   **Azure 虛擬機器**（含容器的支援）
-   **Azure 虛擬機器擴展集**（含容器的支援）

從這三個，ACI 提供極大的好處，也就是您不需要維護基礎作業系統，也就是您不需要升級/修補等等，但仍 ACI 將放置在基礎結構層級，為進一步說明這本書接下來的章節中的事實。

Azure 會在相同的時間更置於 PaaS （平台即服務） 層級的支援容器中的產品包括：

-   **Azure App Service**
-   **Azure Kubernetes Service （AKS 和 ACS）**
-   **Azure Service Fabric** 
-   **Azure Batch** 

然後，Azure Container Registry 是裝載於 Azure，您可以從所有先前的產品註冊或部署您的自訂容器映像時使用的高可調整的容器登錄。

此外，從您的容器，您可以使用其他受管理的服務在 Azure SQL Database、 Azure Redis 快取中，Azure Cosmos DB，例如 Azure 中等等。 此外，您也可以使用容器在 Azure 中的 OpenShift 等 Cloud Foundry 的 Azure Marketplace 中有第三方解決方案/平台。 

在下一節中，您可以瀏覽 Microsoft 的建議，關於何時應該使用每個這些 Azure 產品和解決方案，特別是當目標為 Windows 容器時。

>[!div class="step-by-step"]
>[上一頁](what-about-cloud-native-applications.md)
>[下一頁](when-not-to-deploy-to-windows-containers.md)