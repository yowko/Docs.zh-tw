---
title: 將現有 .NET 應用程式部署為 Windows 容器
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |將現有的 .NET 應用程式部署為 Windows 容器
ms.date: 12/21/2020
ms.openlocfilehash: f3f164ca0578d5358f2c5365fd5a1d2e8e22d8c5
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025341"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>將現有 .NET 應用程式部署為 Windows 容器

以 Windows 容器為基礎的部署適用于 Cloud-Optimized 應用程式和 Cloud-Native 應用程式。

不過，在本指南中，特別是在下列各節中，它大多著重于在您不需要重新架構應用程式的情況下，針對 *雲端優化* 應用程式使用 Windows 容器。

## <a name="what-are-containers-linux-or-windows"></a>什麼是容器？  (Linux 或 Windows) 

容器可讓您將應用程式包裝到它自己的隔離套件中。 在其容器中，應用程式不會受到存在於容器外部的應用程式或進程所影響。 應用程式所相依的所有專案，在容器內都能以進程的形式順利執行。 無論容器可能移動的位置，應用程式的需求一律會符合直接相依性，因為它會與執行 (程式庫相依性、執行時間等等) 所需的所有專案結合在一起。

容器的主要特性是它會讓環境在不同的部署中都是相同的，因為容器本身會提供它所需的所有相依性。 您可以在電腦上進行應用程式的偵錯工具，然後將它部署到另一部電腦，並保證相同的環境。

容器是容器映射的實例。 容器映射是一種封裝應用程式或服務 (像是) 的快照集，然後以可靠且可重現的方式進行部署。 您可以說，Docker 不只是一項技術，它也是一種原理和程式。

隨著容器每日變得更常見，它們變成整個產業的「部署單位」。

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>在 Linux 或 Windows) 上 (Docker 引擎之容器的優點

使用容器來建立應用程式（也可能會定義為輕量組建區塊），可在任何基礎結構上大幅增加建立、傳送和執行任何應用程式的靈活性。

透過容器，您可以在幾乎不需要變更程式碼的情況下，從開發環境中取得任何應用程式，因為 Docker 會跨 Microsoft 開發人員工具、作業系統和雲端進行整合。

當您部署至一般 Vm 時，您可能已經有可將 ASP.NET 應用程式部署至 Vm 的方法。 不過，您的方法可能牽涉到使用部署工具（例如 Puppet）或類似的工具，來執行多個手動步驟或複雜的自動化流程。 您可能需要執行如下的工作：修改設定專案、複製伺服器之間的應用程式內容，以及根據 .msi 安裝程式執行互動式安裝程式，然後再進行測試。 部署中的所有步驟都會增加部署的時間和風險。 只要目標環境中沒有相依性，您就會收到失敗。

在 Windows 容器中，封裝應用程式的程式完全自動化。 Windows 容器是以 Docker 平臺為基礎，可為容器部署提供自動更新和復原。 您使用 Docker 引擎所獲得的主要改進，就是建立映射，像是應用程式的快照集及其所有相依性。 映射是 (Windows 容器映射的 Docker 映射，在此案例中) 。 這些映射會在容器中執行 ASP.NET 應用程式，而不會回到原始程式碼。 容器快照集會成為部署單位。

許多組織都容器化現有的整合型應用程式，原因如下：

- **透過改善的部署來發行敏捷** 的功能。 容器會在開發與作業之間提供一致的部署合約。 當您使用容器時，您不會聽到開發人員說：「它在我的電腦上運作，為什麼不在生產環境中？」 它們可以說：「它會以容器的形式執行，因此它會在生產環境中執行」。 封裝的應用程式及其所有相依性，都可以在任何支援的容器架構環境中執行。 它會執行它要在所有部署目標中執行的方式 (開發、QA、預備、生產) 。 容器會在從一個階段移至下一個階段時排除大部分的摩擦，以大幅改善部署，而且您可以更快交付。

- **降低成本**。 容器會導致成本降低，方法是合併和移除現有的硬體，或從每個硬體單位以較高的密度執行應用程式。

- 可 **移植性**。 容器為模組化和可攜性。 在任何主要公用雲端 (Microsoft Azure、Amazon AWS、Google、IBM) ，以及內部部署和私人或混合式雲端環境中的任何伺服器作業系統 (Linux 和 Windows) 都支援 Docker 容器。

- **控制項**。 容器提供彈性且安全的環境，可在容器層級進行控制。 您可以藉由設定容器上的執行條件約束原則，來保護、隔離或甚至限制容器。 如 Windows 容器、Windows Server 2016 和 Hyper-v 容器一節中所述，提供其他的企業支援選項。

當您使用容器來開發和維護應用程式時，靈活性、可攜性和控制的重大改進最終會導致大量成本降低。

## <a name="what-is-docker"></a>什麼是 Docker？

[Docker](https://www.docker.com/) 是一個 [開放原始碼專案](https://github.com/docker/docker) ，可將應用程式的部署自動化為可在雲端或內部部署中執行的可移植、自我足夠的容器。 Docker 也是升級及發展這項技術的[公司](https://www.docker.com/)。 公司與雲端、Linux 和 Windows 廠商（包括 Microsoft）共同合作。

![此圖顯示 Docker 如何在混合式雲端中部署容器。](./media/deploy-existing-net-apps-as-windows-containers/docker-deploys-containers-all-layers.png)

**圖4-6。** Docker 將容器部署在混合式雲端的所有圖層

對於熟悉虛擬機器的人，容器可能看起來很類似。 容器會執行作業系統、具有檔案系統，並且可透過網路存取，就像實體或虛擬電腦系統一樣。 即便如此，容器的基本技術和概念還是與虛擬機器非常不同。 從開發人員的觀點來看，容器必須被視為單一進程。 事實上，容器具有一個進程的單一進入點。

為了簡單起見，Docker 容器 (，) 可在 Linux 和 Windows 上以原生方式執行 *容器* 。 執行一般容器時，Windows 容器只能在 (主機伺服器或 VM) 的 Windows 主機上執行，而 Linux 容器只能在 Linux 主機上執行。 不過，在最新版本的 Windows Server 和 Hyper-v 容器中，Linux 容器也可以使用目前僅適用于 Windows Server 容器的 Hyper-v 隔離技術，在 Windows Server 上以原生方式執行。

在不久的將來，同時具有 Linux 和 Windows 容器的混合環境也可以使用，甚至是常見的環境。

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>適用于現有 .NET 應用程式之 Windows 容器的優點

使用 Windows 容器的優點基本上與您從容器取得的優點相同。 使用 Windows 容器可大幅提升靈活性、可攜性和控制能力。

現有的 .NET 應用程式會參考使用 .NET Framework 所建立的應用程式。 例如，它們可能是傳統的 ASP.NET web 應用程式，而不是使用 .NET Core 或 .NET 5.0，這是較新的，而且在 Linux、Windows 和 MacOS 上跨平臺執行。

.NET Framework 中的主要相依性是 Windows。 它也有次要相依性，例如 IIS，以及傳統 ASP.NET 中的 System.object。

.NET Framework 的應用程式必須在 Windows、句號上執行。 如果您想要將現有的 .NET Framework 應用程式，但不能或不想要投資遷移至 .NET Core 或更新版本 ( 「如果運作正常，請不要將它遷移」 ) （容器的唯一選擇是使用 Windows 容器）。

因此，Windows 容器的主要優點之一，就是讓您能夠將在 Windows 上執行的現有 .NET Framework 應用程式現代化容器化。 最後，Windows 容器可讓您利用容器（彈性、可攜性和更佳的控制）來取得您所需的優點。

## <a name="choose-an-os-to-target-with-net-based-containers"></a>選擇要作為目標的作業系統。以網路為基礎的容器

由於 Docker 支援的作業系統多樣性，以及 .NET Framework 和 .NET Core 之間的差異，您應該根據您所使用的架構，以特定的 OS 和特定版本為目標。

針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。 這些 Windows 版本提供不同的特性 (例如 IIS 與自我裝載的 web 伺服器（例如 .NET Framework 或 .NET 應用程式可能需要的 Kestrel) ）。

針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。

圖4-7 顯示您可以設定目標的作業系統版本，視 .NET Framework 的應用程式版本而定。

![此圖顯示根據 .NET Framework 版本的目標作業系統。](./media/deploy-existing-net-apps-as-windows-containers/dotnet-framework-operating-systems.png)

**圖4-7。** 以 .NET Framework 版本為目標的作業系統

在以 .NET Framework 應用程式為基礎之現有或繼承應用程式的遷移案例中，主要相依性是在 Windows 和 IIS 上。 唯一的選項是使用以 Windows Server Core 和 .NET Framework 為基礎的 Docker 映射。

當您將映射名稱新增至 Dockerfile 檔案時，您可以使用標記來選取作業系統和版本，如下列 .NET Framework 為基礎的 Windows 容器映射範例所示：

> | **Tag** | **系統和版本** |
> |---|---|
> | **mcr.microsoft.com/dotnet/framework/runtime:4.x-windowsservercore-20H2** | 在 Windows Server Core 上 .NET Framework 4。x |
> | **mcr.microsoft.com/dotnet/framework/aspnet:4.x-windowsservercore-20H2** | 在 Windows Server Core 上搭配其他 ASP.NET 自訂的 .NET Framework 4。x |

針對適用于 Linux 和 Windows) 的 .NET (跨平臺，標記如下所示：

> | **Tag** | **系統和版本**
> |---|---|
> | **mcr.microsoft.com/dotnet/runtime:5.0** | .NET 執行時間-僅適用于 Linux |
> | **mcr.microsoft.com/dotnet/runtime:5.0-nanoserver-20H2** | .NET 執行時間-僅適用于 Windows Nano Server |

### <a name="multi-arch-images"></a>多架構影像

從2017中開始，您也可以在 Docker 中使用稱為 [多](https://github.com/moby/moby/issues/15866) 架構映射的新功能。 .NET Docker 映射可以使用多架構標記。 您的 Dockerfile 檔案不再需要定義您的目標作業系統。 多架構功能可讓您在多部電腦設定之間使用單一標記。 例如，使用多架構時，您可以使用一個常見的標記： **mcr.microsoft.com/dotnet/runtime:5.0**。 如果您從 Linux 容器環境中提取該標記，就會取得以 Debian 為基礎的映射。 如果您從 Windows 容器環境中提取該標記，就會取得 Nano 伺服器映射。

針對 .NET Framework 映射，因為傳統 .NET Framework 只支援 Windows，所以您無法使用多架構功能。

## <a name="windows-container-types"></a>Windows 容器類型

Windows Server 容器和 Linux 容器一樣，都是使用 Docker 引擎來管理。 不同于 Linux 容器，Windows 容器包含兩種不同的容器類型，或執行時間-Windows Server 容器和 Hyper-v 隔離。

**Windows Server 容器**：透過程式和命名空間隔離技術，提供應用程式隔離。 Windows Server 容器與容器主機和主機上執行的所有容器共用核心。 這些容器沒有提供惡意防護界限，不應用來隔離未受信任的程式碼。 由於共用核心空間，因此這些容器需要相同的核心版本和組態。

**Hyper-v 隔離**：藉由在高度優化的 VM 上執行每個容器，擴充 Windows Server 容器所提供的隔離。 在此設定中，容器主機的核心不會與相同主機上的其他容器共用。 這些容器是針對惡意多租使用者裝載所設計，具有相同的虛擬機器安全性保證。 因為這些容器不會與主機或主機上的其他容器共用核心，所以它們可以使用支援的版本)  (不同的版本和設定來執行核心。 例如，Windows 10 上的所有 Windows 容器會使用 Hyper-v 隔離來利用 Windows Server 核心版本和設定。

在 Windows 上執行具有或不具有 Hyper-v 隔離的容器是執行時間決策。 您可以選擇一開始先建立具有 Hyper-v 隔離的容器，並在執行時間選擇改為以 Windows Server 容器的形式執行。

### <a name="additional-resources"></a>其他資源

- **Windows 容器檔案**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Windows 容器基礎**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **資訊圖： Microsoft 和容器**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>Azure 中的容器生態系統

在前面幾節中，我們已說明 Docker 容器的優點，以及適用于 .NET 應用程式的特定容器映射的詳細資料。 所有一般資訊都是開發或將應用程式的基礎。
不過，在考慮生產部署環境或甚至是 QA 和開發/測試環境時，Microsoft Azure 提供了一種開放且廣泛的選擇，也就是雲端中的完整容器生態系統 (，如下圖所示) 。 根據您的特定應用程式需求，您應該選擇一個或另一個 Azure 產品。

![Azure 中容器生態系統的圖表。](./media/deploy-existing-net-apps-as-windows-containers/azure-container-ecosystem.png)

**圖 4-7.5。** Azure 中的容器生態系統

從 Azure 中的容器生態系統，下列產品支援被視為基礎結構的容器：

- **Azure 容器執行個體 (ACI)**
- **Azure 虛擬機器** (容器的支援) 
- **Azure 虛擬機器擴展集** (容器的支援) 

從這三個外掛程式提供絕佳的優點，也就是您不需要維護基礎作業系統、不需要升級/修補等功能，但是 ACI 仍會定位在基礎結構層級中，如此一來，這本書的後續章節將會更詳細地說明。

Azure 中的產品支援的容器同時位於 PaaS (平臺即服務) 層級：

- **Azure App Service**
- **Azure Kubernetes Service (AKS 和 ACS)**
- **Azure Batch**

然後，Azure Container Registry 是裝載在 Azure 中的高可擴充容器登錄，可讓您在註冊及部署自訂容器映射時，從所有先前的產品中使用。

此外，您可以從容器使用 Azure 中的其他受控服務，例如 Azure SQL Database、Azure Redis 快取、Azure Cosmos DB 等等。 另外還有協力廠商解決方案/平臺可用 Azure Marketplace 例如 Cloud Foundry 和 OpenShift，您也可以在 Azure 中使用容器。

在接下來的幾節中，您可以探索 Microsoft 對於以 Windows 容器為目標時，如何特別使用這些 Azure 產品和解決方案的建議。

>[!div class="step-by-step"]
>[上一個](what-about-cloud-native-applications.md) 
>[下一步](when-not-to-deploy-to-windows-containers.md)
