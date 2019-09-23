---
title: EShopOnContainers 參考應用程式簡介
description: 介紹適用于 ASP.NET Core 和 Azure 的 eShopOnContainers Cloud Native 微服務 Reference 應用程式。
ms.date: 06/30/2019
ms.openlocfilehash: 20f9175ada2e5439be363781a2b187c10ba86d37
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182857"
---
# <a name="introducing-eshoponcontainers-reference-app"></a>EShopOnContainers 參考應用程式簡介

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Microsoft 與領先的社區專家合作，已產生全功能的雲端原生微服務參考應用程式 eShopOnContainers。 此應用程式建置於使用 .NET Core 和 Docker，並選擇性地建立 Azure、Kubernetes 和 Visual Studio，以打造線上店面。

![eShopOnContainers 範例應用程式螢幕擷取畫面。](./media/eshoponcontainers-sample-app-screenshot.png)

**圖 2-1**. eShopOnContainers 範例應用程式螢幕擷取畫面。

在開始本章之前，建議您先下載[eShopOnContainers reference 應用程式](https://github.com/dotnet-architecture/eShopOnContainers)。 如果您這樣做，您就可以更輕鬆地追蹤所呈現的資訊。

## <a name="features-and-requirements"></a>功能和需求

讓我們先複習一下應用程式的功能和需求。 EShopOnContainers 應用程式代表銷售各種實體產品（例如 t 恤和咖啡馬克杯）的線上商店。 如果您之前已在線上購買任何專案，使用存放區的體驗應該相當熟悉。 以下是存放區所實行的一些基本功能：

- 列出目錄專案
- 依類型篩選項目
- 依品牌篩選項目
- 將專案新增至購物籃
- 編輯或移除購物籃中的專案
- 準備
- 註冊帳戶
- 登入
- 登出
- 審查訂單

應用程式也具有下列非功能性需求：

- 它必須具有高度可用性，而且必須自動調整以符合增加的流量（並在流量 contosoconcerthall 後相應減少）。 
- 它應該提供容易使用的監視其健康情況和診斷記錄，以協助疑難排解其遇到的任何問題。 
- 它應該支援 agile 開發流程，包括支援持續整合和部署（CI/CD）。 
- 除了兩個 web 前端（傳統和單頁應用程式）之外，應用程式也必須支援執行不同種類作業系統的行動用戶端應用程式。 
- 它應該支援跨平臺裝載和跨平臺開發。

![eShopOnContainers 參考應用程式開發架構。](./media/eshoponcontainers-development-architecture.png)

**圖 2-2**。 eShopOnContainers 參考應用程式開發架構。

EShopOnContainers 應用程式可從透過 HTTPS 存取應用程式的 web 或行動用戶端存取，其目標為 ASP.NET Core MVC 伺服器應用程式或適當的 API 閘道。 API 閘道提供幾項優點，例如將後端服務與個別的前端用戶端分離，並提供更好的安全性。 應用程式也會使用稱為後端前端（BFF）的相關模式，這會建議為每個前端用戶端建立個別的 API 閘道。 參考架構會根據要求是否來自 web 或行動用戶端，來示範如何細分 API 閘道。

應用程式的功能會分成多個不同的微服務。 有一些服務負責驗證和身分識別、列出產品目錄中的專案、管理使用者的購物籃，以及放置訂單。 每個個別的服務都有自己的持續性儲存體。 請注意，並非所有服務都有互動的單一主要資料存放區。 相反地，服務之間的協調和通訊是根據需要進行，並透過使用訊息匯流排來完成。

每個不同的微服務都會根據其個別需求，以不同的方式設計。 這表示其技術堆疊可能不同，但它們都是使用 .NET Core 所建立，並專為雲端設計。 較簡單的服務提供基礎資料存放區的基本建立-讀取-更新-刪除（CRUD）存取，而更先進的服務則使用領域導向設計方法和模式來管理商務複雜度。

![不同種類的微服務](./media/different-kinds-of-microservices.png)

**圖 2-3**。 不同種類的微服務。

## <a name="overview-of-the-code"></a>程式碼的總覽

因為它會利用微服務，所以 eShopOnContainers 應用程式會在其 GitHub 存放庫中包含相當多的個別專案和解決方案。 除了個別的解決方案和可執行檔，各種服務都設計成在本機開發期間和生產環境中的執行時間，于自己的容器內執行。 圖2-4 顯示完整的 Visual Studio 方案，其中會組織各種不同的專案。

![Visual Studio 方案中的專案。](./media/projects-in-visual-studio-solution.png)

**圖 2-4**： Visual Studio 方案中的專案。

程式碼會組織成支援不同的微服務，而在每個微服務中，程式碼會細分為領域邏輯、基礎結構考慮，以及使用者介面或服務端點。 在許多情況下，Azure 服務會在生產環境中滿足每個服務的相依性，以及用於本機開發的替代選項。 讓我們來檢查應用程式的需求如何對應至 Azure 服務。

## <a name="understanding-microservices"></a>瞭解微服務

本書著重在使用 Azure 技術建立的雲端原生應用程式。 若要深入瞭解微服務的最佳做法，以及如何架構微服務型應用程式，請閱讀隨附書[，.net 微服務：容器化 .NET 應用程式的架構](https://dotnet.microsoft.com/learn/aspnet/microservices-architecture)。 本書可從線上、PDF 或 eReader 格式取得。

>[!div class="step-by-step"]
>[上一頁](candidate-apps.md)
>[下一頁](map-eshoponcontainers-azure-services.md)
