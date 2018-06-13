---
title: ASP.NET Web Core 應用程式的 Azure 裝載建議
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | ASP.NET Web Core 應用程式的 Azure 裝載建議
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.openlocfilehash: aea8a54bdee7eebd977f8b67d9888c2288dcd26d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590329"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>ASP.NET Web Core 應用程式的 Azure 裝載建議

> 「企業營運領導者都繞過 IT 部門，從雲端中取得應用程式 (又名 SaaS) 並為其付費，就像訂閱雜誌一樣。 當不再需要服務的時候，他們可以取消訂閱，且不會有任何設備在角落裡閒置。」  
> _\- Daryl Plummer，Gartner 分析師_

## <a name="summary"></a>總結

無論您的應用程式需求和架構是什麼，Windows Azure 都可以支援。 您的裝載需求可以像靜態網站一樣簡單，也可以像由數十種服務組成的應用程式一樣複雜。 針對 ASP.NET Core 整合型 Web 應用程式和支援的服務，建議幾種眾所周知的組態。 下列建議根據裝載資源的類型分組，不論是完整應用程式、個別處理程序或是資料。

## <a name="web-applications"></a>Web 應用程式

可裝載的 Web 應用程式：

-   App Service Web Apps

-   容器

-   Azure Service Fabric

-   虛擬機器 (VM)

其中，App Service Web Apps 是大多數情況下建議的方法。 對於微服務結構，請考慮容器型方法或服務網狀架構。 如果您需要更充分掌控執行應用程式的機器，請考慮 Azure 虛擬機器。

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps 提供全受管的平台，針對裝載 Web 應用程式最佳化。 其為一種平台即服務 (PaaS) 產品，可讓您專注於商務邏輯；Azure 則負責執行和調整應用程式所需的基礎結構。 App Service Web Apps 的一些主要功能：

-   DevOps 最佳化 (持續整合與傳遞、多種環境、A/B測試、指令碼支援)

-   全域規模與高可用性

-   連線至 SaaS 平台和您的內部部署資料

-   安全性和合規性

-   Visual Studio 整合

Azure App Service 是大部分 Web 應用程式的最佳選擇。 部署和管理整合至平台中、網站可快速調整以處理高流量負載，以及內建的負載平衡和流量管理員提供高可用性。 您可以使用線上移轉工具，輕鬆將現有網站移動到 Azure App Service、使用 Web 應用程式資源庫中的開放原始碼應用程式，或使用您選擇的架構和工具來建立新網站。 WebJobs 功能可輕鬆將背景工作處理新增至 App Service Web 應用程式。

### <a name="containers-and-azure-container-service"></a>容器和 Azure Container Service

Azure Container Service 使您更容易建立、設定和管理預先設定為執行容器化應用程式的虛擬機器叢集。 使用熱門開放原始碼排程與協調流程工具的最佳設定。 可讓您使用現有技能，或運用大量且不斷成長的社群專業知識，在 Microsoft Azure 上部署及管理容器型應用程式。

Azure Container Service 使您更容易建立、設定和管理預先設定為執行容器化應用程式的虛擬機器叢集。 使用熱門開放原始碼排程與協調流程工具的最佳設定。 可讓您使用現有技能，或運用大量且不斷成長的社群專業知識，在 Microsoft Azure 上部署及管理容器型應用程式。

Azure Container Service 的其中一項目標是提供容器裝載環境，使用當今 Microsoft 客戶中熱門的開放原始碼工具和技術。 為此，Azure Container Service 將針對您選擇的協調器 (DC/OS、Docker Swarm 或 Kubernetes) 公開標準 API 端點。 藉由使用這些端點，您就能運用任何可與這些端點通訊的軟體。 比方說，若是 Docker Swarm 端點，您可能會選擇使用 Docker 命令列介面 (CLI)。 若為 DC/OS，您可選擇 DCOS CLI。 若為 Kubernetes，您可選擇 kubectl。 圖 11-1 示範如何使用這些端點來管理容器叢集。

![](./media/image11-1.png)

**圖 11-1。** Azure Container Service 管理與 Docker、Kubernetes 或 DC/OS 端點搭配使用。

### <a name="azure-service-fabric"></a>Azure Service Fabric

如果您要建立新應用程式或重新撰寫現有應用程式以使用微服務架構，則 Service Fabric 是不錯的選擇。 在機器共用集區運行的應用程式可以從小型起步，並視需要而成長為數百或數千部機器的龐大規模。 具狀態服務可讓您輕鬆保持應用程式狀態的一致性和可靠性，且 Service Fabric 會自動為您管理服務分區、擴展和可用性。 Service Fabric 也能使用 Open Web Interface for .NET (OWIN) 和 ASP.NET Core 來支援 WebAPI。 相較於 App Service，Service Fabric 還提供對基礎結構的更多控制或直接存取。 您可以從遠端存取伺服器或設定伺服器啟動工作。

### <a name="azure-virtual-machines"></a>Azure 虛擬機器

如果您的現有應用程式需要進行大量修改才能在 App Service 或 Service Fabric 中執行，則可以選擇虛擬機器以簡化移轉至雲端的過程。 但是，與 Azure App Service 和 Service Fabric 相比，正確設定、保護和維護 VM 需要更多的時間和 IT 專業知識。 如果您正在考慮 Azure 虛擬機器，請確保將修補、更新和管理 VM 環境所需的持續性維護工作納入考量。 Azure 虛擬機器是基礎結構即服務 (IaaS)，而 App Service 和 Service Fabric 是平台即服務 (Paas)。

#### <a name="feature-comparison"></a>功能比較

| App Service 功能 | Service Fabric | 虛擬機器 |
|---------|----------|----------|
| 幾乎立即部署 | X | X | |
| 調升規模至大型機器，而不需重新部署 | X | X | |
| 執行個體共用內容和組態；調整時無需重新部署或重新設定 | X | X | |
| 多個部署環境 (生產環境、預備環境) | X | X | |
| 作業系統自動更新管理 | X | | |
| 在 32/64 位元平台之間無縫切換 | X | | |
| 使用 Git、FTP 部署程式碼 | X | | X |
| 使用 WebDeploy 部署程式碼 | X | | X |
| 使用 TFS 部署程式碼 | X | X | X |
| 裝載 Web 或 Web 服務階層的多層式架構 | X | X | X |
| 存取 Azure 服務，例如服務匯流排、儲存體、SQL 資料庫 | X | X | X |
| 安裝任何自訂的 MSI | | X | X |

## <a name="logical-processes"></a>邏輯處理序

可以與應用程式的其餘部分分離的個別邏輯處理序，能以「無伺服器」方式獨立部署至 Azure 功能。 Azure 函式讓您只需撰寫特定問題所需的程式碼，而無需擔心應用程式或基礎結構運行。 您可以從各種程式設計語言中進行選擇，包括 C\#，F\#、Node.js、Python 和 PHP，允許您為手邊工作選擇最具生產力的語言。 與大多數基於雲端的解決方案一樣，您只需支付使用時間，並且可以信任 Azure 函式，來根據需要調升規模。

## <a name="data"></a>資料

Azure 提供各種資料儲存選項，以便您的應用程式可以針對有問題的資料使用適當的資料提供者。

針對交易式的關聯式資料，Azure SQL Database 是最佳選項。 對於高性能的唯讀資料，由 Azure SQL Database 支援之 Redis 快取是很好的解決方案。

非結構化的 JSON 資料可以透過各種方式進行儲存；從 SQL 資料庫的資料列到 Blob 或 Azure 儲存體中的表單到 DocumentDB。 其中 DocumentDB 提供最佳的查詢功能，且是大量 JSON 型文件的推薦選項，因為這些文件必須支援查詢。

用於協調應用程式行為的暫時性命令或事件型資料，可以使用 Azure 服務匯流排或 Azure 儲存體佇列。 Azure 儲存體匯流排提供更大的靈活性，並且是應用程式內部和之間非一般訊息的建議服務。

## <a name="architecture-recommendations"></a>架構建議

您的應用程式需求應指定其架構。 有許多不同的 Azure 服務可供選擇；選擇正確的服務是一項重要決策。 Microsoft 提供參考架構資源庫，以協助識別針對常見案例最佳化的常見架構。 您可以繫結對應至應用程式需求的參考架構，或至少提供一個起點。

圖 11-2 顯示參考架構範例。 此圖描述針對市場行銷進行最佳化的 Sitecore 內容管理系統網站之建議的架構方法。

![](./media/image11-2.png)

**圖 11-2。** Sitecore 行銷網站參考架構。

**參考 – Azure 裝載建議**

-   Azure 解決方案架構\
    <https://azure.microsoft.com/solutions/architecture/>

-   Azure 開發人員指南\
    <https://azure.microsoft.com/campaigns/developer-guide/>

-   什麼是 Azure App Service？\
    <https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is>

-   Azure App Service、虛擬機器、Service Fabric 和雲端服務比較\
    <https://docs.microsoft.com/azure/app-service-web/choose-web-site-cloud-service-vm>

>[!div class="step-by-step"]
[上一頁] (development-process-for-azure.md)
