---
title: ASP.NET Web Core 應用程式的 Azure 裝載建議
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | ASP.NET Web Core 應用程式的 Azure 裝載建議
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: a93009e66d63aa7d9c3b60951d43eafa3c351a63
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053269"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>ASP.NET Web Core 應用程式的 Azure 裝載建議

> 「企業營運領導者都繞過 IT 部門，從雲端中取得應用程式 (又名 SaaS) 並為其付費，就像訂閱雜誌一樣。 當不再需要服務的時候，他們可以取消訂閱，且不會有任何設備在角落裡閒置。」  
> _\- Daryl Plummer，Gartner 分析師_

無論您的應用程式需求和架構是什麼，Windows Azure 都可以支援。 您的裝載需求可以像靜態網站一樣簡單，也可以像由數十種服務組成的應用程式一樣複雜。 針對 ASP.NET Core 整合型 Web 應用程式和支援的服務，建議幾種眾所周知的組態。 本文中的建議根據裝載資源的類型分組，不論是完整應用程式、個別處理程序或是資料。

## <a name="web-applications"></a>Web 應用程式

可裝載的 Web 應用程式：

- App Service Web Apps

- 容器

- 虛擬機器 (VM)

其中，App Service Web Apps 是大多數情況下建議的方法。 針對微服務架構，請考慮容器式方法。 如果您需要更充分掌控執行應用程式的機器，請考慮 Azure 虛擬機器。

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps 提供全受管的平台，針對裝載 Web 應用程式最佳化。 其為一種平台即服務 (PaaS) 供應項目，可讓您專注於商務邏輯；Azure 則負責執行和調整應用程式所需的基礎結構。 App Service Web Apps 的一些主要功能：

- DevOps 最佳化 (持續整合與傳遞、多種環境、A/B測試、指令碼支援)。

- 全域規模與高可用性。

- 連接至 SaaS 平台和您的內部部署資料。

- 安全性與合規性。

- Visual Studio 整合。

- 透過[用於容器的 Web App](https://azure.microsoft.com/services/app-service/containers/) 支援 Linux 及 Windows 容器。

Azure App Service 是大部分 Web 應用程式的最佳選擇。 部署和管理整合至平台中、網站可快速調整以處理高流量負載，以及內建的負載平衡和流量管理員提供高可用性。 您可以使用線上移轉工具，輕鬆將現有網站移動到 Azure App Service、使用 Web 應用程式資源庫中的開放原始碼應用程式，或使用您選擇的架構和工具來建立新網站。 WebJobs 功能可輕鬆將背景工作處理新增至 App Service Web 應用程式。

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Service (AKS) 管理您託管的 Kubernetes 環境，可讓您快速輕鬆地部署及管理容器化應用程式，而不需要容器協調流程專業知識。 您可以視需要佈建、升級資源及調整其規模，而不需要讓應用程式離線，因此也會排除持續性操作和維護的負擔。

AKS 透過將大部分責任轉移給 Azure，來降低管理 Kubernetes 叢集的複雜度和操作額外負荷。 Azure 是託管的 Kubernetes 服務，為您處理狀況監控和維護等重要工作。 此外，您只需針對叢集內的代理程式節點，而不需針對 master 支付費用。 AKS 是受控 Kubernetes 服務，提供：

- 自動化的 Kubernetes 版本升級和修補。
- 簡單的叢集規模調整。
- 自我修復託管控制介面 (master)。
- 節省成本 - 只需支付執行中代理程式集區節點的費用。

有了 Azure 負責管理您 AKS 叢集中的節點，您就不再需要手動執行許多工作，像是叢集升級。 由於 Azure 會為您處理這些重要的維護工作，因此 AKS 不提供對叢集的直接存取 (例如透過 SSH)。

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
