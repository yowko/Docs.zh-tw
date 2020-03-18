---
title: 將現有 .NET 應用程式部署為 Windows 容器
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |將現有的 .NET 應用部署為 Windows 容器
ms.date: 04/29/2018
ms.openlocfilehash: 28568ca363bfc8100f78b100f8a7f0242c4f04c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089551"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>將現有 .NET 應用程式部署為 Windows 容器

基於 Windows 容器的部署適用于雲優化應用程式和雲原生應用程式。

但是，在本指南中，尤其是以下部分中，它主要側重于將 Windows 容器用於*雲優化*應用程式的應用，而雲優化應用程式不需要重新構建應用程式。

## <a name="what-are-containers-linux-or-windows"></a>什麼是容器？ （Linux 或 Windows）

容器是一種將應用程式包裝到其自己的獨立包中的方法。 在其容器中，應用程式不受容器外部存在的應用程式或進程的影響。 應用程式所依賴的一切，以成功運行，因為進程位於容器內。 無論容器可能移動的位置，應用程式的要求將始終滿足直接依賴項，因為它與它需要運行的所有內容（庫依賴項、運行時等）捆綁在一起。

容器的主要特性是它使環境在不同的部署中相同，因為容器本身附帶了它需要的所有依賴項。 您可以在電腦上調試應用程式，然後將其部署到另一台電腦，並保證使用相同的環境。

容器是容器映射的實例。 容器映射是打包應用或服務（如快照）然後以可靠且可重現的方式部署它的方法。 你可以說Docker不僅是一種技術，而且是一種哲學和過程。

隨著容器每天變得越來越常見，它們正在成為全行業範圍內的"部署單元"。

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>容器的優勢（Linux 或 Windows 上的 Docker 引擎）

使用容器（也可以定義為羽量級構建基塊）構建應用程式，可顯著提高跨任何基礎結構構建、運輸和運行任何應用程式的敏捷性。

借助容器，借助 Microsoft 開發人員工具、作業系統和雲的 Docker 集成，您可以將任何應用從開發到生產，而代碼更改很少或根本沒有。

部署到普通 VM 時，您可能已經具備了將ASP.NET應用部署到 VM 的方法。 但是，使用 Puppet 或類似工具等部署工具，您的方法可能涉及多個手動步驟或複雜的自動化過程。 您可能需要執行修改配置項、在伺服器之間複製應用程式內容以及基於 .msi 設置運行互動式安裝程式等任務，然後進行測試。 部署中的所有這些步驟都增加了部署的時間和風險。 每當目標環境中不存在依賴項時，您就會收到失敗。

在 Windows 容器中，打包應用程式的過程是完全自動化的。 Windows 容器基於 Docker 平臺，該平臺為容器部署提供自動更新和回滾。 使用 Docker 引擎得到的主要改進是創建映射，這些映射類似于應用程式的快照及其所有依賴項。 這些映射是 Docker 映射（本例中為 Windows 容器映射）。 這些映射在容器中運行ASP.NET應用，而無需返回原始程式碼。 容器快照將成為部署單元。

許多組織正在容器化現有的單片應用程式，原因如下：

- **通過改進的部署釋放敏捷性**。 容器在開發和操作之間提供一致的部署協定。 當您使用容器時，您不會聽到開發人員說："它在我的機器上工作，為什麼不在生產中呢？ 他們可以說，"它作為一個容器運行，所以它將在生產中運行。 打包的應用程式及其所有依賴項都可以在任何受支援的基於容器的環境中執行。 它將以它打算在所有部署目標（開發、QA、暫存、生產）中運行的方式運行。 容器在從一個階段移動到下一個階段時消除了大多數摩擦，這極大地改進了部署，而且您可以更快地發貨。

- **成本降低**。 容器通過整合和刪除現有硬體或以每單元硬體的較高密度運行應用程式來降低成本。

- **可攜性**。 容器是模組化和便攜的。 在任何伺服器作業系統（Linux 和 Windows）、任何主要公共雲（Microsoft Azure、Amazon AWS、Google、IBM）以及本地和私有雲環境中都支援 Docker 容器。

- **控制**。 容器提供靈活和安全的環境，在容器級別進行控制。 可以通過在容器上設置執行約束策略來保護、隔離甚至限制容器。 如有關 Windows 容器的部分中所述，Windows Server 2016 和 Hyper-V 容器提供了其他企業支援選項。

當您使用容器開發和維護應用程式時，敏捷性、可攜性和控制性的重大改進最終可顯著降低成本。

## <a name="what-is-docker"></a>什麼是 Docker？

[Docker](https://www.docker.com/)是一個[開源專案](https://github.com/docker/docker)，它自動將應用程式部署為可在雲或本地運行的可移植的、自給自足的容器。 Docker 也是升級及發展這項技術的[公司](https://www.docker.com/)。 該公司與雲、Linux 和 Windows 供應商（包括 Microsoft）合作。

![顯示 Docker 如何在混合雲中部署容器的圖表。](./media/deploy-existing-net-apps-as-windows-containers/docker-deploys-containers-all-layers.png)

**圖 4-6。** Docker 將容器部署在混合式雲端的所有圖層

對於熟悉虛擬機器的人來說，容器可能看起來非常相似。 容器運行作業系統，具有檔案系統，並且可以通過網路訪問，就像物理或虛擬電腦系統一樣。 即便如此，容器的基本技術和概念還是與虛擬機器非常不同。 從開發人員的角度來看，容器必須更像一個進程。 實際上，容器具有一個進程的單個進入點。

Docker 容器（為了簡單起見，*容器*）可以在 Linux 和 Windows 上本機運行。 運行常規容器時，Windows 容器只能在 Windows 主機（主機伺服器或 VM）上運行，Linux 容器只能在 Linux 主機上運行。 但是，在最新版本的 Windows Server 和 Hyper-V 容器中，Linux 容器還可以通過使用當前僅在 Windows 伺服器容器中可用的 Hyper-V 隔離技術在 Windows Server 上本機運行。

在不久的將來，同時具有 Linux 和 Windows 容器的混合環境是可能的，甚至很常見。

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Windows 容器對現有 .NET 應用程式的優勢

使用 Windows 容器的好處與您從容器中通常獲得的好處基本相同。 使用 Windows 容器將極大地提高敏捷性、可攜性和控制性。

現有 .NET 應用程式是指使用 .NET 框架創建的應用程式。 例如，它們可能是傳統的ASP.NET Web 應用程式-他們不使用 .NET Core，這是更新的，並在 Linux、Windows 和 MacOS 上運行跨平臺。

.NET 框架中的主要依賴項是 Windows。 它還具有輔助依賴項，如 IIS 和 System.Web 在傳統ASP.NET。

.NET 框架應用程式必須在 Windows 期間運行。 如果要對現有的 .NET 框架應用程式進行容器化，並且不能或不想投資遷移到 .NET Core（"如果工作正常，不要遷移它"），則容器的唯一選擇是使用 Windows 容器。

因此，Windows 容器的主要優點之一是，它們提供了一種實現在 Windows 通過容器化上運行的現有 .NET 框架應用程式現代化的方法。 最終，Windows 容器通過使用容器敏捷性、可攜性和更好的控制功能，為您帶來您所尋找的優勢。

## <a name="choose-an-os-to-target-with-net-based-containers"></a>選擇要以 的目標作業系統。基於 NET 的容器

鑒於 Docker 支援的作業系統的多樣性以及 .NET 框架和 .NET Core 之間的差異，您應該根據正在使用的框架定位特定的作業系統和特定版本。

針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。 這些 Windows 版本提供了 .NET Framework 或 .NET Core 應用程式可能需要的不同特性（如 IIS 與自託管的 Web 服務器（如 Kestrel）。

針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。

圖 4-7 顯示了您可以定位的作業系統版本，具體取決於應用版本的 .NET Framework。

![顯示基於 .NET 框架版本的目標作業系統的圖表。](./media/deploy-existing-net-apps-as-windows-containers/dotnet-framework-operating-systems.png)

**圖 4-7。** 基於 .NET 框架版本定位的作業系統

在基於 .NET 框架應用程式的現有或舊應用程式遷移方案中，主要依賴項位於 Windows 和 IIS 上。 您唯一的選擇是基於 Windows 伺服器核心和 .NET 框架使用 Docker 映射。

將映射名稱添加到 Dockerfile 檔時，可以使用標記選擇作業系統和版本，如以下基於 .NET 框架的 Windows 容器映射的示例所示：

> | **標記** | **系統和版本** |
> |---|---|
> | **微軟/點網框架：4.x-windows伺服器核心** | .NET 框架 4.x 在 Windows 伺服器核心 |
> | **微軟/阿斯普內特：4.x-windows伺服器核心** | .NET 框架 4.x 在 Windows 伺服器核心上具有其他ASP.NET自訂 |

對於 .NET Core（適用于 Linux 和 Windows 的跨平臺），這些標記如下所示：

> | **標記** | **系統和版本**
> |---|---|
> | **微軟/點網：2.0.0-執行時間** | .NET 核心 2.0 僅在 Linux 上執行時間 |
> | **微軟/點網：2.0.0-運行時納米伺服器** | .NET 核心 2.0 僅在 Windows Nano 伺服器上運行時 |

### <a name="multi-arch-images"></a>多拱形圖像

從 2017 年年中開始，您還可以在 Docker 中使用稱為[多拱圖像的](https://github.com/moby/moby/issues/15866)新功能。 .NET 核心 Docker 映射可以使用多拱標記。 Dockerfile 檔不再需要定義您所針對的作業系統。 多拱功能允許跨多個電腦配置使用單個標記。 例如，對於多 arch，可以使用一個通用標記 **：microsoft/dotnet：2.0.0 運行時**。 如果從 Linux 容器環境中提取該標記，則獲取基於 Debian 的映射。 如果從 Windows 容器環境中提取該標記，則獲取基於 Nano Server 的圖像。

對於 .NET 框架圖像，由於傳統的 .NET 框架僅支援 Windows，因此無法使用多拱功能。

## <a name="windows-container-types"></a>視窗容器類型

與 Linux 容器一樣，Windows Server 容器使用 Docker 引擎進行管理。 與 Linux 容器不同，Windows 容器包括兩種不同的容器類型，或運行時 -Windows Server 容器和 Hyper-V 隔離。

**Windows 伺服器容器**：通過進程和命名空間隔離技術提供應用程式隔離。 Windows Server 容器與容器主機和主機上運行的所有容器共用內核。 這些容器沒有提供惡意防護界限，不應用來隔離未受信任的程式碼。 由於共用核心空間，因此這些容器需要相同的核心版本和組態。

**Hyper-V 隔離**：通過在高度優化的 VM 上運行每個容器，擴展 Windows 伺服器容器提供的隔離。 在此設定中，容器主機的核心不會與相同主機上的其他容器共用。 這些容器專為敵對的多租戶託管而設計，具有 VM 相同的安全保證。 由於這些容器不與主機上的主機或其他容器共用內核，因此它們可以使用不同的版本和配置（支援的版本）運行內核。 例如，Windows 10 上的所有 Windows 容器都使用 Hyper-V 隔離來利用 Windows Server 內核版本和配置。

在 Windows 上運行具有超 V 隔離或不帶 Hyper-V 隔離的容器是一個運行時決策。 您可以選擇最初使用 Hyper-V 隔離創建容器，在運行時，可以選擇將其作為 Windows Server 容器運行。

### <a name="additional-resources"></a>其他資源

- **Windows 容器文檔**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Windows 容器基礎知識**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **資訊圖：微軟和容器**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>Azure 中的容器生態系統

在前面的章節中，已經解釋了 Docker 容器的優勢以及 .NET 應用程式的特定容器映射的詳細資訊。 為了開發或容器化應用程式，所有這些通用資訊都是基礎資訊。
但是，在考慮生產部署環境甚至 QA 和開發人員/測試環境時，Microsoft Azure 提供了一個開放且廣泛的選擇，即雲中的完整容器生態系統（如下圖所示）。 根據特定應用程式的需求，應選擇一個或另一個 Azure 產品。

![Azure 中的容器生態系統圖。](./media/deploy-existing-net-apps-as-windows-containers/azure-container-ecosystem.png)

**圖 4-7.5。** Azure 中的容器生態系統

從 Azure 中的容器生態系統中，支援被視為基礎結構的容器的以下產品：

- **Azure 容器實例 （ACI）**
- **Azure 虛擬機器**（支援容器）
- **Azure 虛擬機器縮放集**（支援容器）

從這三個，ACI提供了一個很大的好處，這是事實，你不需要維護的基礎作業系統，不需要你升級/補丁等，但ACI仍然定位在基礎設施級別，更好地解釋在本書的後續部分。

Azure 支援容器中同時位於 PaaS（平臺即服務）級別的產品包括：

- **Azure App Service**
- **Azure 庫伯奈斯服務（AKS 和 ACS）**
- **Azure Batch**

然後，Azure 容器註冊表是託管在 Azure 中的高可擴展容器註冊表，您可以在註冊和部署自訂容器映射時從所有以前的產品中使用。

此外，在容器中，可以使用 Azure 中的其他託管服務，如 Azure SQL 資料庫、Azure Redis 緩存、Azure Cosmos DB 等。 此外，Azure 應用商店中還有協力廠商解決方案/平臺，如雲鑄造和 OpenShift，您也可以在 Azure 中使用容器。

在下一節中，您可以流覽 Microsoft 關於何時使用這些 Azure 產品和解決方案的建議，特別是針對 Windows 容器時。

>[!div class="step-by-step"]
>[上一個](what-about-cloud-native-applications.md)
>[下一個](when-not-to-deploy-to-windows-containers.md)
