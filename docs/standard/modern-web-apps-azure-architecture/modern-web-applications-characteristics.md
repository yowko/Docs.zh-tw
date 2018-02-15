---
title: "現代化 web 應用程式的特性"
description: "使用 ASP.NET Core 和 Azure 的現代化 Web 應用程式架構設計人員 |現代化 web 應用程式的特性"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ecef23870ac547f4b4066628da71f8af98c91b27
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="characteristics-of-modern-web-applications"></a>現代化 Web 應用程式的特性

> "… 使用適當的設計功能廉價地有。 這種方法是棘手，但會繼續成功 」。  
> _\- Dennis Ritchie_

## <a name="summary"></a>總結

現代化 web 應用程式有較高使用者期望和比以往更高的要求。 現今的 web 應用程式應該要使用 24/7 從任何地方在世界中，並可從幾乎任何裝置或螢幕大小。 Web 應用程式必須是安全、 彈性且可調整以符合尖峰需求。 現在越來越複雜的案例中處理的方式使用 JavaScript，並有效率地透過 web 應用程式開發介面進行通訊的用戶端上建置豐富的使用者體驗。

ASP.NET Core 最適合用於現代化 web 應用程式和以雲端為基礎的託管案例。 它的模組化設計可讓應用程式實際使用，改善應用程式的安全性和效能，同時降低裝載的資源需求的功能而定。

## <a name="reference-application-eshoponweb"></a>參考應用程式： eShopOnWeb

本指南包含參考應用程式， *eShopOnWeb*，示範一些原則與建議。 應用程式是簡單的線上存放區可支援瀏覽的上衣、 咖啡馬克及其他行銷目的目錄。 參考應用程式是故意簡單化以使其更容易了解。

**圖 2-1。** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>參考應用程式
> - **eShopOnWeb**  
> <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>雲端裝載及擴充

ASP.NET Core 最適合雲端 （公用雲端、 私人雲端、 任何雲端），因為它是低記憶體及高輸送量。 ASP.NET Core 應用程式的較小的足跡表示您可以主控多個相同的硬體上，而且當使用付款-做為您的雲端代管服務支付較少的資源。 高輸送量表示您可以做進一步降低需要投資在伺服器與裝載基礎結構中從指定的相同硬體的應用程式更多的客戶。

## <a name="cross-platform"></a>跨平台

ASP.NET Core 是跨平台，並可以在 Linux 和 MacOS，以及 Windows 上執行。 這會開啟許多新的開發和部署的應用程式以 ASP.NET Core 建置選項。 Docker 容器，通常今天執行 Linux，可以主控 ASP.NET Core 應用程式，讓他們可以運用的優點[容器和 microservices](../microservices-architecture/index.md)。

## <a name="modular-and-loosely-coupled"></a>模組化且鬆散偶合

NuGet 封裝會在.NET Core 的首要和 ASP.NET Core 應用程式以透過 NuGet 許多程式庫所組成。 此資料粒度的功能可協助確保應用程式只取決於和部署它們實際所需的功能，減少其耗用量和安全性弱點介面區。

ASP.NET Core 也完全支援相依性插入內部和應用程式層級。 介面可以擁有多個可以視需要空出的實作。 相依性插入允許鬆散結合這些介面，讓它們更容易擴充、 維護及測試應用程式。

## <a name="easily-tested-with-automated-tests"></a>輕鬆地測試自動化測試

ASP.NET Core 應用程式支援單元測試，和其鬆散偶合和相依性資料隱碼攻擊的支援方便交換基礎結構顧慮假的實作，基於測試目的。 ASP.NET Core 也提供了可用於在記憶體中的主機應用程式 TestServer。 功能測試然後可以對此記憶體中伺服器上，執行完整的應用程式堆疊 （包含中介軟體、 路由、 模型繫結、 篩選等） 提出要求並接收回應時，在大部分的時間花費裝載在實際伺服器上的應用程式以透過網路層級的要求。 這些測試特別容易撰寫，而重要的應用程式開發介面是越來越重要現代化 web 應用程式中。

## <a name="traditional-and-spa-behaviors-supported"></a>傳統和支援 SPA 行為

傳統 web 應用程式有很少用戶端行為，但已改為依賴瀏覽、 查詢和應用程式可能需要進行的更新的伺服器。 每個新使用者進行的作業會轉譯成新的 web 要求，正在重新載入完整的頁面，在終端使用者的瀏覽器中的結果。 傳統的模型檢視控制器 (MVC) 架構通常會遵循這種方式，與每個新的要求對應至不同的控制器動作，而後者會使用模型和傳回的檢視。 指定的頁面中的某些個別作業可能會增強 AJAX （非同步 JavaScript 和 XML） 功能，但整體架構的應用程式使用許多不同的 MVC 檢視和 URL 端點。

單一頁面應用程式 (SPAs)，相較之下，涉及極少數的動態產生的伺服器端頁面載入 （如果有的話）。 許多 SPAs 是靜態的 HTML 檔案載入必要的 JavaScript 程式庫，以啟動並執行應用程式內初始化。 這些應用程式進行的 web 應用程式開發介面，其滿足資料要求，使用量，而且可以提供更豐富的使用者體驗。

許多 web 應用程式牽涉到傳統 web 應用程式行為 （通常用於內容） 和 SPAs （適用於互動功能） 的組合。 ASP.NET Core 支援 MVC 和 web 應用程式開發介面中相同的應用程式使用同一組工具和基礎架構程式庫。

## <a name="simple-development-and-deployment"></a>簡單開發和部署

ASP.NET Core 應用程式可以使用簡單的文字編輯器與命令列介面或完整的開發環境，例如 Visual Studio 來撰寫。 整合應用程式通常會部署到單一的端點。 可以輕鬆地自動化部署，以持續整合 (CI) 和持續傳遞 (CD) 管線的過程中發生。 除了傳統的 CI/CD 工具，Windows Azure 擁有其整合式 git 儲存機制的支援和自動部署更新，因為它們會對指定的 git 分支或標記。

## <a name="traditional-aspnet-and-web-forms"></a>傳統的 ASP.NET 和 Web Form

除了 ASP.NET Core，傳統 ASP.NET 4.x 仍然是穩定且可靠的平台，建置 web 應用程式。 ASP.NET 支援 MVC 和 Web API 的開發模型，以及 Web Form，這非常適合用來開發豐富的網頁應用程式和功能豐富的協力廠商元件生態系統。 Windows Azure 絕佳傳統 ASP.NET 4.x 應用程式，支援與許多開發人員熟悉此平台。

> ### <a name="references--modern-web-applications"></a>參考 – 現代化 Web 應用程式
> - **ASP.NET Core 簡介**  
> <https://docs.microsoft.com/aspnet/core/>
> - **六個索引鍵優點的 ASP.NET Core 使不同且更好的**  
> <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **在 ASP.NET Core 中測試**  
> <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
[上一個](index.md) [下一步] (choose-between-traditional-web-and-single-page-apps.md)
