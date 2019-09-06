---
title: 將現有 .NET 應用程式部署為 Windows 容器
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |將現有的 .NET 應用程式部署為 Windows 容器
ms.date: 04/29/2018
ms.openlocfilehash: 4d58be828418abe4964e26a983f194fd5d30b93d
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374025"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>將現有 .NET 應用程式部署為 Windows 容器

以 Windows 容器為基礎的部署適用于雲端優化應用程式和雲端原生應用程式。

不過，在本指南中，尤其是在下列各節中，其主要著重于針對*雲端優化*應用程式使用 Windows 容器，而您不需要重新架構應用程式。

## <a name="what-are-containers-linux-or-windows"></a>什麼是容器？ （Linux 或 Windows）

容器是將應用程式包裝成自己的隔離套件的一種方式。 在其容器中，應用程式不會受到位於容器外的應用程式或進程所影響。 應用程式所依賴的所有專案，都可以在容器內成功執行，以做為進程。 無論容器移至何處，應用程式的需求一律會符合直接相依性，因為它會與需要執行的所有專案（程式庫相依性、執行時間等等）結合。

容器的主要特性是讓環境在不同的部署中都是相同的，因為容器本身會隨附所需的所有相依性。 您可以在您的電腦上進行應用程式的偵錯工具，然後將它部署到另一部已保證相同環境的電腦上。

容器是容器映射的實例。 容器映射是一種封裝應用程式或服務（例如快照集），然後以可靠且可重現的方式部署它的方式。 您可以說，Docker 不只是一項技術，同時也是一個原理和一個程式。

隨著容器每日變得更常見，它們會成為整個產業的「部署單位」。

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>容器的優點（Linux 或 Windows 上的 Docker 引擎）

使用容器建立應用程式（也可能定義為輕量建立區塊）可大幅增加在任何基礎結構中建立、交付及執行任何應用程式的靈活性。

使用容器，您可以將任何應用程式從開發到生產環境，幾乎不需要變更程式碼，因為 Docker 在 Microsoft 開發人員工具、作業系統和雲端之間的整合。

當您部署到純虛擬機器時，您可能已經有方法可將 ASP.NET 應用程式部署至您的 Vm。 不過，您的方法很可能會使用 Puppet 之類的部署工具或類似的工具，來牽涉到多個手動步驟或複雜的自動化流程。 您可能需要執行工作，例如修改設定專案、在伺服器之間複製應用程式內容，以及根據 .msi 安裝程式，然後再進行測試。 部署中的所有步驟都會增加部署的時間和風險。 當目標環境中沒有相依性時，您會收到失敗。

在 Windows 容器中，封裝應用程式的流程會完全自動化。 Windows 容器是以 Docker 平臺為基礎，可為容器部署提供自動更新和復原。 使用 Docker 引擎所得到的主要改進，就是您會建立映射，像是應用程式的快照集，以及它的所有相依性。 映射是 Docker 映射（在此案例中為 Windows 容器映射）。 這些映射會在容器中執行 ASP.NET 應用程式，而不會回到原始碼。 容器快照集會成為部署的單位。

許多組織都是容器化現有的整合型應用程式，原因如下：

- **透過改良的部署來發行靈活性**。 容器在開發與作業之間提供一致的部署合約。 當您使用容器時，您不會聽到開發人員說：「它可在我的電腦上運作，為什麼不在生產環境中？」 他們可以說：「它會以容器的形式執行，因此它會在生產環境中執行」。 封裝的應用程式及其所有相依性，都可以在任何支援的容器型環境中執行。 它會執行其預定在所有部署目標（開發、QA、預備、生產）中執行的方式。 當容器從一個階段移到下一個階段時，會消除大部分的摩擦，這會大幅改善部署，而且您可以更快交付。

- **成本降低**。 容器可透過合併和移除現有的硬體，或在每個硬體單位以較高的密度執行應用程式，而導致成本降低。

- 可**移植性**。 容器具有模組化和可攜性。 所有伺服器作業系統（Linux 和 Windows）、任何主要公用雲端（Microsoft Azure、Amazon AWS、Google、IBM），以及內部部署和私人或混合式雲端環境都支援 Docker 容器。

- **控制項**。 容器提供彈性且安全的環境，可在容器層級控制。 藉由在容器上設定執行條件約束原則，可以保護、隔離或限制容器。 如關於 Windows 容器的一節中所述，Windows Server 2016 和 Hyper-v 容器提供其他企業支援選項。

當您使用容器來開發和維護應用程式時，靈活性、可攜性和控制項的重大改進最終會導致大幅降低成本。

## <a name="what-is-docker"></a>什麼是 Docker？

[Docker](https://www.docker.com/)是一個[開放原始碼專案](https://github.com/docker/docker)，可將應用程式自動化部署為可在雲端或內部部署中執行的可移植、自我充分的容器。 Docker 也是升級及發展這項技術的[公司](https://www.docker.com/)。 該公司與雲端、Linux 和 Windows 廠商（包括 Microsoft）合作。

![Docker 將容器部署在混合式雲端的所有圖層](./media/image6.png)

**圖4-6。** Docker 將容器部署在混合式雲端的所有圖層

對於熟悉虛擬機器的人而言，容器可能看起來大致類似。 容器會執行作業系統、具有檔案系統，並且可透過網路存取，就像實體或虛擬電腦系統一樣。 不過，容器背後的技術和概念與虛擬機器的差異大不相同。 從開發人員的觀點來看，容器的處理方式必須和單一進程更類似。 事實上，容器有一個進程的單一進入點。

Docker 容器（為了簡單起見，*容器*）可以在 Linux 和 Windows 上以原生方式執行。 執行一般容器時，Windows 容器只能在 Windows 主機（主機伺服器或 VM）上執行，而 Linux 容器只能在 Linux 主機上執行。 不過，在最新版本的 Windows Server 和 Hyper-v 容器中，Linux 容器也可以使用目前僅適用于 Windows Server 容器的 Hyper-v 隔離技術，在 Windows Server 上以原生方式執行。

在不久的將來，同時具有 Linux 和 Windows 容器的混合式環境將是可行的，甚至是常見的。

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Windows 容器適用于您現有 .NET 應用程式的優點

使用 Windows 容器的優點基本上與您在容器中取得的優勢相同。 使用 Windows 容器是關於大幅提升靈活性、可攜性和控制能力。

現有的 .NET 應用程式會參考使用 .NET Framework 所建立的應用程式。 例如，它們可能是傳統的 ASP.NET web 應用程式，它們不會使用 .NET Core，這在 Linux、Windows 和 MacOS 上的較新版本和跨平臺執行。

.NET Framework 中的主要相依性是 Windows。 在傳統 ASP.NET 中，它也有次要相依性，例如 IIS 和 System.web。

.NET Framework 的應用程式必須在 Windows、period 上執行。 如果您想要容器化現有 .NET Framework 應用程式，而且您不能或不想要投資遷移至 .NET Core （「如果運作正常，不要加以遷移」），您對容器唯一的選擇就是使用 Windows 容器。

因此，Windows 容器的其中一個主要優點是，它們可讓您將現有的 .NET Framework 應用程式現代化，以在 Windows 上執行容器化。 最後，Windows 容器可讓您使用容器（靈活性、可攜性和更佳的控制）來取得您所需的優勢。

## <a name="choose-an-os-to-target-with-net-based-containers"></a>選擇要設為目標的作業系統。以網路為基礎的容器

由於 Docker 支援的作業系統多樣性以及 .NET Framework 和 .NET Core 之間的差異，因此您應該根據所使用的架構，以特定作業系統和特定版本為目標。

針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。 這些 Windows 版本提供 .NET Framework 或 .NET Core 應用程式可能需要的不同特性（例如 IIS 與自我裝載的 web 伺服器，例如 Kestrel）。

針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。

圖4-7 顯示您可以設為目標的作業系統版本，視應用程式的 .NET Framework 版本而定。

![根據 .NET Framework 版本目標的作業系統](./media/image7.png)

**圖4-7。** 根據 .NET Framework 版本目標的作業系統

在以 .NET Framework 應用程式為基礎的現有或繼承應用程式的遷移案例中，主要相依性是在 Windows 和 IIS 上。 唯一的選項是使用以 Windows Server Core 和 .NET Framework 為基礎的 Docker 映射。

當您將映射名稱新增至 Dockerfile 檔案時，您可以使用標記來選取作業系統和版本，如下列 .NET Framework 為基礎的 Windows 容器映射範例所示：

> | **標記** | **系統和版本** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | Windows Server Core 上的 .NET Framework 4。x |
> | **microsoft/aspnet:4.x-windowsservercore** | 在 Windows Server Core 上使用其他 ASP.NET 自訂的 .NET Framework 4。x |

針對 .NET Core （適用于 Linux 和 Windows 的跨平臺），標記看起來會像下面這樣：

> | **標記** | **系統和版本**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET Core 2.0 執行時間-僅適用于 Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | .NET Core 2.0 執行時間-僅適用于 Windows Nano Server |

### <a name="multi-arch-images"></a>多架構映射

從2017年中開始，您也可以使用 Docker 的新功能，稱為[多](https://github.com/moby/moby/issues/15866)架構映射。 .NET Core Docker 映射可以使用多架構標記。 您的 Dockerfile 檔案不再需要定義您的目標作業系統。 多架構功能可跨多個電腦設定使用單一標記。 例如，使用多架構時，您可以使用一個常見的標記： **microsoft/dotnet： 2.0.0**。 如果您從 Linux 容器環境中提取該標記，則會取得以 Debian 為基礎的映射。 如果您從 Windows 容器環境中提取該標記，則會取得 Nano 伺服器架構的映射。

針對 .NET Framework 的影像，因為傳統 .NET Framework 僅支援 Windows，所以您無法使用多架構功能。

## <a name="windows-container-types"></a>Windows 容器類型

就像 Linux 容器，Windows Server 容器是使用 Docker 引擎來管理。 不同于 Linux 容器，Windows 容器包含兩種不同的容器類型，或執行時間-Windows Server 容器和 Hyper-v 隔離。

**Windows Server 容器**：透過進程和命名空間隔離技術，提供應用程式隔離。 Windows Server 容器與容器主機和所有在主機上執行的容器共用核心。 這些容器不會提供惡意的安全性界限，而且不應該用來隔離不受信任的程式碼。 由於共用核心空間的不同，這些容器需要相同的核心版本和設定。

**Hyper-v 隔離**：藉由在高度優化的 VM 上執行每個容器，擴充 Windows Server 容器所提供的隔離。 在此設定中，容器主機的核心不會與相同主機上的其他容器共用。 這些容器是針對惡意多租使用者裝載所設計，具有與 VM 相同的安全性保證。 因為這些容器不會與主機或主機上的其他容器共用核心，所以可以使用不同的版本和設定（支援的版本）來執行核心。 例如，Windows 10 上的所有 Windows 容器都使用 Hyper-v 隔離來利用 Windows Server 核心版本和設定。

在具有或不含 Hyper-v 隔離的 Windows 上執行容器是一種執行時間決策。 一開始，您可以選擇建立具有 Hyper-v 隔離的容器，並在執行時間選擇改為執行 Windows Server 容器。

### <a name="additional-resources"></a>其他資源

- **Windows 容器檔案**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Windows 容器基本概念**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **資訊圖Microsoft 和容器**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>Azure 中的容器生態系統

在先前的章節中，我們已說明 Docker 容器的優點，以及 .NET 應用程式的特定容器映射的詳細資料。 一般資訊都是開發或容器化應用程式的基礎。
不過，在考慮生產部署環境或甚至是 QA 和開發/測試環境時，Microsoft Azure 提供了一種開放且廣泛的選擇，也就是雲端中的完整容器生態系統（如下圖所示）。 根據您的特定應用程式需求，您應該選擇一個或另一個 Azure 產品。

![Azure 中的容器生態系統](./media/image7.5.png)

**圖 4-7.5。** Azure 中的容器生態系統

從 Azure 中的容器生態系統，下列產品支援被視為基礎結構的容器：
- **Azure 容器執行個體 (ACI)**
- **Azure 虛擬機器**（有容器的支援）
- **Azure 虛擬機器擴展集**（有容器的支援）

從這三種方式來看，ACI 提供了絕佳的優勢，這就是您不需要維護基礎作業系統、不需要升級/修補等等的事實。但 ACI 仍然位於基礎結構層級，如本書後續章節中所述。

Azure 中支援同時位於 PaaS （平臺即服務）層級之容器的產品如下：

- **Azure App Service**
- **Azure Kubernetes Service （AKS 和 ACS）**
- **Azure Batch** 

然後，Azure Container Registry 是 Azure 中託管的高擴充性容器登錄，您可以在註冊和部署自訂容器映射時，從所有先前的產品使用這些登錄。

此外，您可以從容器使用 Azure 中的其他受控服務，例如 Azure SQL Database、Azure Redis 快取、Azure Cosmos DB 等。 另外還有協力廠商解決方案/平臺，Azure Marketplace 例如 Cloud Foundry 和 OpenShift，您也可以在其中使用 Azure 中的容器。 

在接下來的章節中，您可以探索 Microsoft 對於以 Windows 容器為目標時特別使用每個 Azure 產品和解決方案的建議。

>[!div class="step-by-step"]
>[上一頁](what-about-cloud-native-applications.md)
>[下一頁](when-not-to-deploy-to-windows-containers.md)
