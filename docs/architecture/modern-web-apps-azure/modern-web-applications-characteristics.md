---
title: 現代化 Web 應用程式的特性
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | 現代化 Web 應用程式的特性
author: ardalis
ms.author: wiwagn
no-loc:
- Blazor
- WebAssembly
ms.date: 12/04/2019
ms.openlocfilehash: a4d7558039d64b21a2744f74d037369ea8c6c923
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539264"
---
# <a name="characteristics-of-modern-web-applications"></a>現代化 Web 應用程式的特性

> "… 有了適當的設計，功能即容易取得。 這種方法艱鉅，但會持續成功。」  
> _\- Dennis Ritchie_

現代化 Web 應用程式具有比以往更高的使用者期望和更高的需求。 現今的 Web 應用程式應該要在世界上的任何地方全天候可用，並可讓幾乎所有裝置或所有尺寸的螢幕使用。 Web 應用程式必須安全、靈活、可調整，以符合尖峰需求。 越來越複雜的案例應透過使用 JavaScript 建置在用戶端上豐富的使用者體驗來處理，並有效率地透過 Web API 進行通訊。

ASP.NET Core 已針對現代化 Web 應用程式和雲端式裝載案例最佳化。 其模組化設計可讓應用程式僅依賴於實際使用的功能，改善應用程式安全性和效能，並同時降低裝載資源需求。

## <a name="reference-application-eshoponweb"></a>參考應用程式：eShopOnWeb

本指南包含參考應用程式 _eShopOnWeb_ 來示範一些原則與建議。 該應用程式是一個簡單的線上商店，支援瀏覽上衣、咖啡馬克杯以及其他行銷商品目錄。 參考應用程式刻意簡單化，以便於理解。

![eShopOnWeb](./media/image2-1.png)

**圖2-1。** eShopOnWeb

> ### <a name="reference-application"></a>參考應用程式
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>雲端裝載且可調整

ASP.NET Core 十分適合雲端 (公用、私人、任何雲端)，因為記憶體用量低、輸送量高。 ASP.NET Core 應用程式的使用量較小，表示您可以在相同硬體上裝載更多應用程式，並在使用隨用隨付雲端主機服務時支付較少的資源。 更高的輸送量，代表您可以在指定相同硬體的情況下為應用程式中為更多客戶提供服務，進一步降低投資於伺服器與裝載基礎結構的需求。

## <a name="cross-platform"></a>跨平台

ASP.NET Core 可跨平台，能在 Linux、MacOS 及 Windows 上執行。 這會針對使用 ASP.NET Core 建立的應用程式，開啟許多新選項。 Linux 及 Windows 的 Docker 容器都可以裝載 ASP.NET Core 應用程式，使其能夠利用[容器和微服務](../microservices/index.md)的優勢。

## <a name="modular-and-loosely-coupled"></a>模組化且鬆散結合

NuGet 套件是 .NET Core 中的頭等公民，而 ASP.NET Core 應用程式是透過 NuGet 的許多程式庫所組成。 此功能的細微性有助於確保應用程式僅依賴和部署實際所需的功能，從而減少其使用量和安全性弱點介面區。

ASP.NET Core 也完全支援在內部和應用層級的相依性 [插入](https://deviq.com/dependency-injection/)。 介面能擁有多個實作，可以視需要交換。 相依性插入可讓應用程式與這些介面 (而非特定實作) 鬆散結合，使其更易於擴充、維護及測試。

## <a name="easily-tested-with-automated-tests"></a>以自動化測試輕鬆進行測試

ASP.NET Core 應用程式支援單元測試，其鬆散結合程度和相依性插入的支援使其可以輕鬆將基礎結構問題與假實作交換，以用於測試目的。 ASP.NET Core 也隨附 TestServer，可用來將應用程式裝載在記憶體中。 功能測試可以對此記憶體中的伺服器發出請求，執行完整的應用程式堆疊 (包含中介軟體、路由、模型繫結、篩選等) 與接收回應，只需要一小部分的時間來將應用程式裝載在實際伺服器上，並透過網路層級傳送要求。 這些測試對於在現代化 Web 應用程式中越來越重要的 API 來說，尤其易於撰寫且具有價值。

## <a name="traditional-and-spa-behaviors-supported"></a>支援傳統和 SPA 行為

傳統 Web 應用程式很少涉及用戶端行為，而是依賴伺服器進行應用程式可能需要的所有瀏覽、查詢和更新。 使用者建立的每個新作業都會轉換成新 Web 要求，從而在終端使用者的瀏覽器中重新載入整個頁面。 傳統模型檢視控制器 (MVC) 架構通常會遵循這種方式，每個新的要求對應至不同的控制器動作，而這會使用模型並傳回檢視。 使用 AJAX (非同步 JavaScript 和 XML) 功能可以增強指定頁面上的某些個別作業，但該應用程式的整體架構使用許多不同 MVC 檢視和 URL 端點。 此外，ASP.NET Core MVC 也支援 Razor Pages，這是組織 MVC 樣式頁面較簡單的方式。

相較之下，單頁應用程式 (SPA) 只涉及極少數動態產生的伺服器端頁面載入 (如有)。 許多 SPA 都是在靜態的 HTML 檔案中初始化，該檔案會載入必要的 JavaScript 程式庫來啟動並執行應用程式。 這些應用程式大量使用 Web API 來滿足其資料需求，並且可以提供更豐富的使用者體驗。

許多 Web 應用程式牽涉到傳統 Web 應用程式行為 (通常用於內容) 和 SPA (適用於互動功能) 的組合。 ASP.NET Core 使用同一組工具和基礎架構程式庫，在同一個應用程式中同時支援 MVC (以檢視或頁面為基礎) 和 Web API。

## <a name="simple-development-and-deployment"></a>簡單開發與部署

您可以使用簡單的文字編輯器和命令列介面來撰寫 ASP.NET Core 的應用程式，或是以功能完整的開發環境（例如 Visual Studio）來撰寫。 整合型應用程式通常會部署到單一端點。 作為持續整合 (CI) 與持續傳遞 (CD) 管道的一部分，部署可以輕鬆自動進行。 除了傳統的 CI/CD 工具之外，Microsoft Azure 還整合了 git 儲存機制的支援，而且可以在對指定的 git 分支或標記進行更新時，自動部署更新。 Azure DevOps 提供完整功能的 CI/CD 組建和部署管線，GitHub Actions 為裝載于該處的專案提供另一個選項。

## <a name="traditional-aspnet-and-web-forms"></a>傳統的 ASP.NET 和 Web Form

除了 ASP.NET Core 之外，傳統 ASP.NET 4.x 仍然是建置 Web 應用程式穩定且可靠的平台。 ASP.NET 支援 MVC 和 Web API 開發模型，以及 Web Form，其非常適合以頁面為基礎的豐富應用程式開發，並且具有豐富的協力廠商元件生態系統。 Microsoft Azure 對於 ASP.NET 4.x 應用程式有絕佳的長期以來非常支援，許多開發人員都熟悉這個平臺。

## Blazor

Blazor 隨附于 ASP.NET Core 3.0 和更新版本中。 它提供新的機制，可讓您使用 Razor、c # 和 ASP.NET Core 來建立豐富的互動式 web 用戶端應用程式。 在開發新式 web 應用程式時，它會提供另一個要考慮的解決方案。 有兩個 Blazor 要考慮的版本：伺服器端和用戶端。

伺服器端 Blazor 已在2019中發行，ASP.NET Core 3.0。 顧名思義，它會在伺服器上執行，並透過網路將用戶端檔的變更呈現回瀏覽器。 伺服器端 Blazor 提供豐富的用戶端體驗，而不需要用戶端 JavaScript，且不需要個別的頁面載入以進行每個用戶端頁面互動。 載入的頁面中的變更會由伺服器要求並處理，然後使用 SignalR 傳送回用戶端。

Blazor2020 年5月發行的用戶端不需要在伺服器上呈現變更。 相反地，它會利用在 WebAssembly 用戶端中執行 .net 程式碼。 如果需要要求資料時，用戶端仍可以對伺服器進行 API 呼叫，但是所有主要瀏覽器都已支援用戶端的所有行為， WebAssembly 而且所有主要瀏覽器都已支援它，而且只是 JAVAscript 程式庫。

> ### <a name="references--modern-web-applications"></a>參考資料 – 現代化 Web 應用程式
>
> - **ASP.NET Core 簡介**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **ASP.NET Core 中的測試**  
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Blazor -開始**  
>   <https://blazor.net/docs/get-started.html>

>[!div class="step-by-step"]
>[上一個](index.md) 
>[下一步](choose-between-traditional-web-and-single-page-apps.md)
