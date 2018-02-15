---
title: "Azure 裝載的 ASP.NET Core web 應用程式的建議"
description: "使用 ASP.NET Core 和 Azure 的現代化 Web 應用程式架構設計人員 |Azure 裝載的 ASP.NET web 應用程式的建議"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 868f1b7ce452be9e29b921888f90d128e074ba13
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Azure 裝載的 ASP.NET Core Web 應用程式的建議

> 「 業務的 everywhere 會略過 IT 部門以取得從雲端 (也稱為 SaaS) 應用程式項目和支付它們，就像訂閱雜誌一樣。 然後當不再需要服務時，他們可以取消訂用帳戶的邊角中未使用任何設備。 」  
> _\- Daryl Plummer，Gartner 分析師_

## <a name="summary"></a>總結

無論您的應用程式需求和架構，Windows Azure 可以支援它。 您的裝載需求可以簡單到非常複雜的數十個服務組成應用程式的靜態網站。 ASP.NET Core 龐大的 web 應用程式和支援服務，都有數個已知的組態建議。 下列建議是根據資源，以裝載、 是否完整應用程式、 個別的處理程序或資料類型來分組。

## <a name="web-applications"></a>Web 應用程式

可以與裝載 web 應用程式：

-   App Service Web 應用程式

-   容器

-   Azure Service Fabric

-   虛擬機器 (Vm)

其中，App Service Web 應用程式會在大部分情況下建議的方法。 微服務架構，請考慮容器為基礎的方法或服務的網狀架構。 如果您需要更充分掌控執行您的應用程式的機器，請考慮 Azure 虛擬機器。

### <a name="app-service-web-apps"></a>App Service Web 應用程式

App Service Web 應用程式提供完整的管理平台針對裝載 web 應用程式最佳化。 它是 platform-as-a-service(PaaS) 供應項目可讓您專注於商務邏輯中，Azure 會負責基礎結構時需要執行，並調整應用程式。 App Service Web 應用程式的一些主要功能：

-   DevOps 最佳化 (持續整合與傳遞，多個環境中，A / B 測試、 指令碼支援)

-   全域的延展性和高可用性

-   SaaS 平台，在內部部署資料連接

-   安全性與相容性

-   Visual Studio 整合

Azure App Service 是大部分 web 應用程式的最佳選擇。 部署及管理整合平台、 站台可以快速地調整，以處理高流量負載，和內建的負載平衡與流量管理員提供高可用性。 您可以移動現有的站台至 Azure App Service 與線上移轉工具，輕鬆地使用開放原始碼應用程式庫中的 Web 應用程式，或建立新的網站使用的架構和工具，您的選擇。 WebJobs 功能可讓您更輕鬆地加入至您的 App Service web 應用程式處理的背景工作。

### <a name="containers-and-azure-container-service"></a>容器和 Azure 容器服務

Azure 容器服務可讓您建立、 設定和管理執行容器化應用程式已預先設定的虛擬機器的叢集更簡單。 它會使用熱門的開放原始碼排程和協調流程工具的最佳的設定。 這可讓您使用現有的技術，或利用大量且不斷社群的專業知識，來部署和管理容器應用程式在 Microsoft Azure 上的主體。

Azure 容器服務可讓您建立、 設定和管理執行容器化應用程式已預先設定的虛擬機器的叢集更簡單。 它會使用熱門的開放原始碼排程和協調流程工具的最佳的設定。 這可讓您使用現有的技術，或利用大量且不斷社群的專業知識，來部署和管理容器應用程式在 Microsoft Azure 上的主體。

Azure 容器服務的其中一個目標是提供使用開放原始碼工具和技術，現在都喜歡 Microsoft 之客戶的容器主機的環境。 為此，Azure 容器服務會公開您所選擇的 orchestrator （DC/OS，Docker Swarm，或 Kubernetes） 標準的應用程式開發介面端點。 藉由使用這些端點，您可以利用能夠這些端點進行交談的任何軟體。 比方說，在 Docker Swarm 結束點的情況下，您可能會選擇使用 Docker 命令列介面 (CLI)。 DC/作業系統，您可能會選擇 DCOS CLI。 Kubernetes，您可能會選擇 kubectl。 圖 11-1 會示範如何使用這些端點來管理容器叢集。

![](./media/image11-1.png)

**圖 11-1。** Azure 容器服務管理與 Docker、 Kubernetes 或 DC/OS 的端點。

### <a name="azure-service-fabric"></a>Azure Service Fabric

Service Fabric 是不錯的選擇，如果您在建立新的應用程式或重新撰寫現有的應用程式使用微服務架構。 應用程式，在機器的共用集區上執行，也可以從小型專案開始並成長到數百或數千部電腦，視使用的大幅延展。 可設定狀態服務讓您輕鬆一致且可靠地儲存應用程式狀態，Service Fabric 自動服務資料分割、 調整及可用性會為您管理。 服務網狀架構也會支援.NET (OWIN) 和 ASP.NET Core WebAPI 開啟 Web 介面。 相較於應用程式服務，Service Fabric 還提供更多控制或直接存取基礎結構。 您可以從遠端存取伺服器，或設定伺服器啟動工作。

### <a name="azure-virtual-machines"></a>Azure 虛擬機器

如果您有現有的應用程式需要大幅修改應用程式服務或服務的網狀架構中執行時，您可以選擇以簡化移轉至雲端的虛擬機器。 不過，正確地設定、 保護和維護的 Vm 需要更多的時間和相較於 Azure App Service 與 Service Fabric 的 IT 專業知識。 如果您考慮 Azure 虛擬機器，請確定您納入考量的修補程式、 更新和管理 VM 環境所需的持續性維護工作。 Azure 虛擬機器為基礎結構做為服務 (IaaS)，而應用程式服務與 Service Fabric 平台做為服務 (Paas)。

#### <a name="feature-comparison"></a>功能比較

| 功能的應用程式服務 | Service Fabric | 虛擬機器 |
|---------|----------|----------|
| 幾乎立即的部署 | X | X | |
| 向上延展至大型的機器，不需重新部署 | X | X | |
| 執行個體共用內容和組態。不需要重新部署或重新設定時調整 | X | X | |
| 多個部署環境 （生產環境、 預備環境） | X | X | |
| 作業系統自動更新管理 | X | | |
| 無縫式 32/64 位元平台之間切換 | X | | |
| 使用 Git、 FTP 部署程式碼 | X | | X |
| 使用 WebDeploy 部署程式碼 | X | | X |
| 部署與 TFS 的程式碼 | X | X | X |
| 主機 web 或 web 服務層的多層式架構 | X | X | X |
| 存取 Azure 服務，例如服務匯流排、 儲存體、 SQL 資料庫 | X | X | X |
| 安裝任何自訂的 MSI | | X | X |

## <a name="logical-processes"></a>邏輯的處理程序

個別邏輯的處理序可以與應用程式的其餘部分分離可能獨立部署至 Azure 函式以 「 無伺服器 」 的方式。 Azure 的函式可讓您只要撰寫的程式碼，您需要針對給定的問題，而不需擔心應用程式或基礎結構來執行它。 您可以選擇各種不同的程式語言，包括 C\#，F\#、 Node.js、 Python 和 PHP，好讓您手邊選取工作的最高生產力的語言。 以雲端為基礎的大多數解決方案而言，類似的時間長度只支付您使用，而您可以信任 Azure 函式，來視需要向上延展。

## <a name="data"></a>資料

Azure 會提供各種不同的資料儲存體選項，以便您的應用程式可以使用適當的資料提供者的資料有問題。

針對交易式的關聯式資料，Azure SQL Database 是最佳選項。 針對高效能最常讀取資料，Azure SQL Database 所支援的 Redis 快取是很好的解決方案。

非結構化的 JSON 資料可以儲存在各種不同的方式，從 Blob 或 Azure 儲存體中的資料表的 SQL 資料庫資料行 DocumentDB 中。 其中，DocumentDB 提供最佳的查詢功能，並建議的選項有大量的查詢必須支援的 JSON 型文件。

用來協調應用程式行為的暫時性命令或事件型資料可以使用 Azure Service Bus 或 Azure 儲存體佇列。 Azure 儲存體匯流排提供更多彈性，而是適用於非一般的訊息與應用程式間建議的服務。

## <a name="architecture-recommendations"></a>架構建議

您的應用程式需求應該會指定其架構。 另外還有許多不同的 Azure 服務，請選擇正確的重要決策。 Microsoft 提供，找出最佳化的常見案例的一般架構的參考架構的組件庫。 您可以繫結參考架構對應密切至您的應用程式需求，或在至少提供起始點。

圖 11 2 顯示的範例參考架構。 此圖表描述最佳化行銷 Sitecore 內容管理系統網站的建議的架構方法。

![](./media/image11-2.png)

**圖 11-2。** Sitecore 行銷網站參考架構。

**參考 – Azure 主機的建議**

-   Azure 方案 Architectures\
    <https://azure.microsoft.com/solutions/architecture/>

-   Azure 開發人員 Guide\
    <https://azure.microsoft.com/campaigns/developer-guide/>

-   什麼是 Azure App Service？ \
    <https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is>

-   Azure App Service 中，虛擬機器、 服務網狀架構和雲端服務 Comparison\
    <https://docs.microsoft.com/azure/app-service-web/choose-web-site-cloud-service-vm>

>[!div class="step-by-step"]
[Previous] (development-process-for-azure.md)
