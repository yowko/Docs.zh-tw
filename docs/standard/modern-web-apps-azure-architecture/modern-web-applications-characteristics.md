---
title: 現代化 Web 應用程式的特性
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | 現代化 Web 應用程式的特性
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: 4c73ab59148325f66d3ee17db3fb78d397b73f15
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404482"
---
# <a name="characteristics-of-modern-web-applications"></a>現代化 Web 應用程式的特性

> "… 有了適當的設計，功能即容易取得。 這種方法艱鉅，但會持續成功。」  
> _\- Dennis Ritchie_

現代化 Web 應用程式具有比以往更高的使用者期望和更高的需求。 現今的 Web 應用程式應該要在世界上的任何地方全天候可用，並可讓幾乎所有裝置或所有尺寸的螢幕使用。 Web 應用程式必須安全、靈活、可調整，以符合尖峰需求。 越來越複雜的案例應透過使用 JavaScript 建置在用戶端上豐富的使用者體驗來處理，並有效率地透過 Web API 進行通訊。

ASP.NET Core 已針對現代化 Web 應用程式和雲端式裝載案例最佳化。 其模組化設計可讓應用程式僅依賴於實際使用的功能，改善應用程式安全性和效能，並同時降低裝載資源需求。

## <a name="reference-application-eshoponweb"></a>參考應用程式：eShopOnWeb

本指南包含參考應用程式 _eShopOnWeb_ 來示範一些原則與建議。 該應用程式是一個簡單的線上商店，支援瀏覽上衣、咖啡馬克杯以及其他行銷商品目錄。 參考應用程式刻意簡單化，以便於理解。

**圖 2-1。** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>參考應用程式
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>雲端裝載且可調整

ASP.NET Core 十分適合雲端 (公用、私人、任何雲端)，因為記憶體用量低、輸送量高。 ASP.NET Core 應用程式占用的空間較小，意味您可以在同一硬體上裝載更多這些應用程式，並且在使用按用量付費之雲端裝載服務時支付較少的資源。 更高的輸送量，代表您可以在指定相同硬體的情況下為應用程式中為更多客戶提供服務，進一步降低投資於伺服器與裝載基礎結構的需求。

## <a name="cross-platform"></a>跨平台

ASP.NET Core 為跨平台，可以在 Linux、MacOS 以及 Windows 上執行。 這為使用 ASP.NET Core 建置之應用程式的開發和部署開啟了許多新選項。 現今通常執行於 Linux 的 Docker 容器，可以裝載 ASP.NET Core 應用程式，使其能夠利用[容器和微服務](../microservices-architecture/index.md)的優勢。

## <a name="modular-and-loosely-coupled"></a>模組化且鬆散結合

NuGet 套件是 .NET Core 中的頭等公民，而 ASP.NET Core 應用程式是透過 NuGet 的許多程式庫所組成。 此功能的細微性有助於確保應用程式僅依賴和部署實際所需的功能，從而減少其使用量和安全性弱點介面區。

ASP.NET Core 也完全支援內部和應用程式層級的相依性插入。 介面能擁有多個實作，可以視需要交換。 相依性插入允許應用程式鬆散偶合至這些介面，使其更容易擴充、維護及測試。

## <a name="easily-tested-with-automated-tests"></a>以自動化測試輕鬆進行測試

ASP.NET Core 應用程式支援單元測試；其鬆散結合和相依性插入使其可以輕鬆將基礎結構問題與假實作交換，以用於測試目的。 ASP.NET Core 也提供可用於在記憶體中裝載應用程式的 TestServer。 功能測試可以對此記憶體中的伺服器發出請求，執行完整的應用程式堆疊 (包含中介軟體、路由、模型繫結、篩選等) 與接收回應，只需要一小部分的時間來將應用程式裝載在實際伺服器上，並透過網路層級傳送要求。 這些測試對於在現代化 Web 應用程式中越來越重要的 API 來說，尤其易於撰寫且具有價值。

## <a name="traditional-and-spa-behaviors-supported"></a>支援傳統和 SPA 行為

傳統 Web 應用程式很少涉及用戶端行為，而是依賴伺服器進行應用程式可能需要的所有瀏覽、查詢和更新。 使用者建立的每個新作業都會轉換成新 Web 要求，從而在終端使用者的瀏覽器中重新載入整個頁面。 傳統模型檢視控制器 (MVC) 架構通常會遵循這種方式，每個新的要求對應至不同的控制器動作，而這會使用模型並傳回檢視。 使用 AJAX (非同步 JavaScript 和 XML) 功能可以增強指定頁面上的某些個別作業，但該應用程式的整體架構使用許多不同 MVC 檢視和 URL 端點。

相較之下，單頁應用程式 (SPA) 只涉及極少數動態產生的伺服器端頁面載入 (如有)。 許多 SPA 都是在靜態的 HTML 檔案中初始化，該檔案會載入必要的 JavaScript 程式庫以啟動並執行應用程式。 這些應用程式大量使用 Web API 來滿足其資料要求，並且可以提供更豐富的使用者體驗。

許多 Web 應用程式牽涉到傳統 Web 應用程式行為 (通常用於內容) 和 SPA (適用於互動功能) 的組合。 ASP.NET Core 在同一個應用程式中支援 MVC (檢視及/或 Razor Pages) 和 Web API，使用相同的工具組和基礎架構程式庫。

## <a name="simple-development-and-deployment"></a>簡單開發與部署

可以使用簡單的文字編輯器與命令列介面，或是完整的開發環境如 Visual Studio，來撰寫 ASP.NET Core 應用程式。 整合型應用程式通常會部署到單一端點。 作為持續整合 (CI) 與持續傳遞 (CD) 管道的一部分，部署可以輕鬆自動進行。 除了傳統的 CI/CD 工具之外，Windows Azure 還整合了對 Git 儲存機制的支援，並且可以在更新指定的 Git 分支或標記時自動部署更新。

## <a name="traditional-aspnet-and-web-forms"></a>傳統的 ASP.NET 和 Web Form

除了 ASP.NET Core 之外，傳統 ASP.NET 4.x 仍然是建置 Web 應用程式穩定且可靠的平台。 ASP.NET 支援 MVC 和 Web API 開發模型以及 Web Form，非常適合豐富的頁面型應用程式開發，且具有豐富的協力廠商元件生態系統。 Windows Azure 對 ASP.NET 4.x 應用程式有長期的支援，許多開發人員都熟悉此平台。

> ### <a name="references--modern-web-applications"></a>參考資料 – 現代化 Web 應用程式
>
> - **ASP.NET Core 簡介**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **ASP.NET Core 的六個主要優點使其與眾不同且更好**  
>   <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **ASP.NET Core 中的測試**  
>   <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
[上一頁](index.md)
[下一頁](choose-between-traditional-web-and-single-page-apps.md)
