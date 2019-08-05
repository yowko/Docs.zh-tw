---
title: ASP.NET Web Core 應用程式的 Azure 裝載建議
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | ASP.NET Web Core 應用程式的 Azure 裝載建議
author: ardalis
ms.author: wiwagn
ms.date: 06/06/2019
ms.openlocfilehash: 7cfb9ada4f963aa392a41cfb9f1b2df22f542d41
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675465"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>ASP.NET Web Core 應用程式的 Azure 裝載建議

> 「企業營運領導者都繞過 IT 部門，從雲端中取得應用程式 (亦稱為 SaaS) 並為其付費，就像訂閱雜誌一樣。 當不再需要服務的時候，他們可以取消訂閱，且不會有任何設備在角落裡閒置。」  
> _\- Daryl Plummer，Gartner 分析師_

無論您的應用程式需求和架構是什麼，Microsoft Azure 都可以支援。 您的裝載需求可以像靜態網站一樣簡單，也可以像由數十種服務組成的應用程式一樣複雜。 針對 ASP.NET Core 整合型 Web 應用程式和支援的服務，建議幾種眾所周知的組態。 本文中的建議根據裝載資源的類型分組，不論是完整應用程式、個別處理程序或是資料。

## <a name="web-applications"></a>Web 應用程式

可裝載的 Web 應用程式：

- App Service Web Apps

- 容器 (數個選項)

- 虛擬機器 (VM)

其中，App Service Web Apps 是大多數情況下建議的方法，包括簡單的容器型應用程式。 針對微服務架構，請考慮容器式方法。 如果您需要更充分掌控執行應用程式的機器，請考慮 Azure 虛擬機器。

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps 提供全受管的平台，針對裝載 Web 應用程式最佳化。 其為一種平台即服務 (PaaS) 供應項目，可讓您專注於商務邏輯；Azure 則負責執行和調整應用程式所需的基礎結構。 App Service Web Apps 的一些主要功能：

- DevOps 最佳化 (持續整合與傳遞、多種環境、A/B測試、指令碼支援)。

- 全域規模與高可用性。

- 連接至 SaaS 平台和您的內部部署資料。

- 安全性與合規性。

- Visual Studio 整合。

Azure App Service 是大部分 Web 應用程式的最佳選擇。 部署和管理整合至平台中、網站可快速調整以處理高流量負載，以及內建的負載平衡和流量管理員提供高可用性。 您可以使用線上移轉工具，輕鬆將現有網站移動到 Azure App Service、使用 Web 應用程式資源庫中的開放原始碼應用程式，或使用您選擇的架構和工具來建立新網站。 WebJobs 功能可輕鬆將背景工作處理新增至 App Service Web 應用程式。 如果您有使用本機資料庫裝載在內部部署的現有 ASP.NET 應用程式，則有一個明確的路徑，可以使用 Azure SQL Database，將應用程式移轉至 App Service Web 應用程式 (或者如果想要的話，對內部部署資料庫伺服器進行安全存取)。

![將內部部署 .NET 應用程式移轉至 Azure App Service 的建議策略](./media/image1-6.png)

在大部分情況下，從本機裝載的 ASP.NET 應用程式移至 App Service Web 應用程式是一個簡單的程序。 幾乎或完全不需要修改應用程式本身，而且它可以快速開始使用 Azure App Service Web Apps 提供的許多功能。

除了未針對雲端最佳化的應用程式之外，Azure App Service Web Apps 還是許多簡單整合型 (非分散式) 應用程式 (例如許多 ASP.NET Core 應用程式) 的絕佳解決方案。 利用這種方法，架構會是基本的，而且易於了解和管理：

![基本 Azure 架構](./media/image1-5.png)

單一資源群組中的少數資源通常就足以管理這類應用程式。 通常部署為單一單元的應用程式 (而不是組成許多不同處理程序的應用程式) 非常適合這種[基本架構方法](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app)。 雖然在架構上很簡單，但此方法仍然可讓裝載的應用程式向上擴充 (每個節點多個資源) 以及橫向擴充 (更多裝載的節點) 以符合任何增加需求。 透過自動調整，應用程式可以設定為根據需求和節點間的平均負載，自動調整裝載應用程式的節點數目。

### <a name="app-service-web-apps-for-containers"></a>用於容器的 App Service Web Apps

除了支援直接裝載 Web 應用程式之外，[用於容器的 App Service Web Apps](https://azure.microsoft.com/services/app-service/containers/) 還可以用來在 Windows 和 Linux 上執行容器化的應用程式。 您可以使用這項服務，輕鬆地部署並執行可隨業務調整的容器化應用程式。 此應用程式具備上述所列的所有 App Service Web Apps 功能。 此外，用於容器的 Web Apps 支援簡化的 CI/CD 搭配 Docker Hub、Azure Container Registry 和 GitHub。 您可以使用 Azure DevOps 定義將變更發佈至登錄的組建和部署管線。 這些變更之後可以在預備環境中加以測試，並使用部署位置自動部署至生產環境，進而允許零停機時間升級。 回復到先前的版本可以輕易地完成。

在某些情況下，用於容器的 Web Apps 最合理。 如果您有可以容器化的現有應用程式，則無論是在 Windows 還是 Linux 容器中，您都可以使用此工具組輕鬆地裝載這些應用程式。 只要發佈容器，然後將用於容器的 Web Apps 設定為從選擇的登錄提取該映像的最新版本即可。 這是「隨即轉移」方法，可從傳統的應用程式裝載模型移轉至雲端最佳化模型。

![將容器化的內部部署 .NET 應用程式移轉至用於容器的 Azure Web Apps](./media/image1-8.png)

如果您的開發小組可移至容器型開發程序，這個方法也適用。 開發應用程式含有容器的「內部迴圈」包含建置含有容器的應用程式。 對程式碼以及容器設定所做的變更會推送至原始檔控制，而自動化組建則負責將新的容器映像發佈至 Docker Hub 或 Azure Container Registry 之類的登錄。 這些映像之後會當作其他開發以及部署到生產環境的基礎使用，如下圖所示：

![端對端 Docker DevOps 生命週期工作流程](./media/image1-7.png)

使用容器開發可提供許多優點，特別是在容器用於生產環境時。 相同的容器設定用來裝載每個環境中所執行的應用程式，從本機開發電腦到將系統建置到生產環境並進行測試。 這可大幅降低因電腦設定或軟體版本不同而產生缺失的可能性。 開發人員也可以使用他們最具生產力的任何工具，包括作業系統，因為容器可以在任何 OS 上執行。 在某些情況下，涉及許多容器的分散式應用程式在單一開發電腦上執行可能非常耗費資源。 在此情況下，升級為使用 Kubernetes 和 Azure Dev Spaces 可能是有意義的，如下一節所述。

因為較大應用程式的部分會分割成較小的獨立*微服務*，其他設計模式則可用來改善應用程式行為。 *API 閘道*可以簡化存取以及將用戶端與其後端分離，而不是直接使用個別的服務。 為不同的前端提供個別的服務後端時，也可讓服務隨著其取用者擴展。 常見的服務可以透過個別*側車*容器存取，其中可能包含使用*大使*模式的常見用戶端連線程式庫。

![註明幾種常見設計模式的微服務範例架構。](./media/image1-10.png)

[深入了解要在建置微服務型系統時考慮的設計模式。](https://docs.microsoft.com/azure/architecture/microservices/design/patterns)

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Service (AKS) 管理您託管的 Kubernetes 環境，可讓您快速輕鬆地部署及管理容器化應用程式，而不需要容器協調流程專業知識。 您可以視需要佈建、升級資源及調整其規模，而不需要讓應用程式離線，因此也會排除持續性操作和維護的負擔。

AKS 透過將大部分責任轉移給 Azure，來降低管理 Kubernetes 叢集的複雜度和操作額外負荷。 Azure 是託管的 Kubernetes 服務，為您處理狀況監控和維護等重要工作。 此外，您只需針對叢集內的代理程式節點，而不需針對 master 支付費用。 AKS 是受控 Kubernetes 服務，提供：

- 自動化的 Kubernetes 版本升級和修補。
- 簡單的叢集規模調整。
- 自我修復託管控制介面 (master)。
- 節省成本 - 只需支付執行中代理程式集區節點的費用。

有了 Azure 負責管理您 AKS 叢集中的節點，您就不再需要手動執行許多工作，像是叢集升級。 由於 Azure 會為您處理這些重要的維護工作，因此 AKS 不提供對叢集的直接存取 (例如透過 SSH)。

運用 AKS 的小組也可以使用 Azure Dev Spaces。 Azure Dev Spaces 可協助小組透過允許小組直接使用其在 AKS 中執行的整個微服務架構或應用程式，藉此將注意力放在其微服務應用程式的開發與快速反覆運算。 Azure Dev Spaces 也會提供一種獨立更新微服務架構部分的方法，而不會影響到其餘的 AKS 叢集或其他開發人員。

![Azure Dev Spaces 工作流程範例](./media/image1-9.gif)

Azure Dev Spaces：

- 將本機電腦設定時間和資源需求降到最低
- 讓小組更快速地逐一查看
- 減少小組所需的整合環境數量
- 開發/測試時，在分散式系統中移除模擬特定服務的需求

[深入了解 Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/about)

### <a name="azure-virtual-machines"></a>Azure 虛擬機器

如果您的現有應用程式需要進行大量修改才能在 App Service 中執行，您可以選擇虛擬機器以簡化移轉至雲端的程序。 但是，與 Azure App Service 相較，正確設定、保護和維護 VM 需要更多的時間和 IT 專業知識。 如果您正在考慮 Azure 虛擬機器，請確保將修補、更新和管理 VM 環境所需的持續性維護工作納入考量。 Azure 虛擬機器是基礎結構即服務 (IaaS)，而 App Service 是 PaaS。 建議您也考慮將您的應用程式作為 Windows 容器部署至用於容器的 Web App，是否是您範例的可用選項。

## <a name="logical-processes"></a>邏輯處理序

可以與應用程式的其餘部分分離的個別邏輯處理序，能以「無伺服器」方式獨立部署至 Azure 功能。 Azure 函式讓您只需撰寫特定問題所需的程式碼，而無需擔心應用程式或基礎結構運行。 您可以從各種程式設計語言中進行選擇，包括 C\#，F\#、Node.js、Python 和 PHP，允許您為手邊工作選擇最具生產力的語言。 與大多數基於雲端的解決方案一樣，您只需支付使用時間，並且可以信任 Azure 函式，來根據需要調升規模。

## <a name="data"></a>資料

Azure 提供各種資料儲存選項，以便您的應用程式可以針對有問題的資料使用適當的資料提供者。

針對交易式的關聯式資料，Azure SQL Database 是最佳選項。 對於高性能的唯讀資料，由 Azure SQL Database 支援之 Redis 快取是很好的解決方案。

非結構化的 JSON 資料可以透過各種方式進行儲存；從 SQL 資料庫的資料列到 Blob 或 Azure 儲存體中的表單到 DocumentDB。 其中 DocumentDB 提供最佳的查詢功能，且是大量 JSON 型文件的推薦選項，因為這些文件必須支援查詢。

用於協調應用程式行為的暫時性命令或事件型資料，可以使用 Azure 服務匯流排或 Azure 儲存體佇列。 Azure 儲存體匯流排提供更大的靈活性，並且是應用程式內部和之間非一般訊息的建議服務。

## <a name="architecture-recommendations"></a>架構建議

您的應用程式需求應指定其架構。 有許多不同的 Azure 服務可供選擇。 選擇正確的服務是一項重要決策。 Microsoft 提供參考架構資源庫，以協助識別針對常見案例最佳化的常見架構。 您可以尋找緊密對應至應用程式需求的參考架構，或至少提供一個起點。

圖 11-2 顯示參考架構範例。 此圖描述針對市場行銷進行最佳化的 Sitecore 內容管理系統網站之建議的架構方法。

![](./media/image11-2.png)

**圖 11-1。** Sitecore 行銷網站參考架構。

**參考資料 - Azure 裝載建議**

- Azure 解決方案架構\
  <https://azure.microsoft.com/solutions/architecture/>

- Azure 的基本 Web 應用程式架構\
  <https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app>

- 微服務的設計模式\
  <https://docs.microsoft.com/azure/architecture/microservices/design/patterns>

- Azure 開發人員指南\
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Web Apps 概觀\
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- 用於容器的 Web App\
  <https://azure.microsoft.com/services/app-service/containers/>

- Azure Kubernetes Service (AKS) 簡介\
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[上一步](development-process-for-azure.md)
