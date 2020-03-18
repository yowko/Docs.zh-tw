---
title: 在傳統 Web 應用程式和單頁應用程式之間作選擇
description: 了解建置 Web 應用程式時，如何在傳統 Web 應用程式和單頁應用程式 (SPA) 之間作選擇。
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d4ed76455001c1a0b8e2e2f1bb90ce8715dd0052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450104"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>在傳統 Web 應用程式和單頁應用程式 (SPA) 之間作選擇

> 「Atwood 定律：任何可以用 JavaScript 撰寫的應用程式，最後都將以 JavaScript 撰寫。」  
> _\-傑夫·Atwood_

現在有兩種建置 Web 應用程式的通用方法：在伺服器上執行大多數應用程式邏輯的傳統 Web 應用程式，以及執行大多數使用者介面邏輯的單頁應用程式 (SPA)，主要使用 Web API 與 Web 伺服器通訊。 也可以採用混合方法，最簡單的方法是在大型傳統 Web 應用程式中託管一個或多個類似 SPA 的豐富子應用程式。

在：

- 應用程式用戶端的需求簡單或甚至是唯讀。

- 應用程式需要在不支援 JavaScript 的瀏覽器中運作。

- 您的小組不熟悉 JavaScript 或 TypeScript 開發技術。

在：

- 應用程式必須公開具有許多功能的豐富使用者介面。

- 您的小組熟悉 JavaScript 及/或 TypeScript 開發。

- 您的應用程式必須已針對其他 (內部或公開) 用戶端公開 API。

此外，SPA 架構需要更多的架構和安全性專業知識。 由於頻繁的更新及新的架構，SPA 架構會經歷比傳統 Web 應用程式更大的變換。 配置自動生成和部署過程以及利用容器等部署選項在 SPA 應用程式中可能比傳統 Web 應用程式更加困難。

必須權衡 SPA 方法對使用者體驗的改進，並權衡這些注意事項。

## <a name="blazor"></a>Blazor

ASP.NET Core 3.0 推出了新的模型，用以建置豐富的互動式可組合 UI，該模型稱為 Blazor。 Blazor 伺服器端允許開發人員在伺服器上使用 Razor 構建 UI，並將此代碼傳遞到瀏覽器並使用[WebAssembly](https://webassembly.org/)執行用戶端。 Blazor 伺服器端現在可用於ASP.NET酷睿 3.0 或更高版本。 Blazor 用戶端應在 2020 年推出。

Blazor 提供了一個新的第三個選項，在評估是構建純伺服器呈現的 Web 應用程式還是 SPA 時需要考慮。 您可以使用 Blazor 構建豐富的類似 SPA 的用戶端行為，而無需進行重大的 JavaScript 開發。 Blazor 應用程式可以調用 API 來請求資料或執行伺服器端操作。

請考慮在以下時間使用 Blazor 構建 Web 應用程式：

- 您的應用程式必須公開豐富的使用者介面

- 與 JavaScript 或 TypeScript 開發相比，您的團隊對 .NET 開發更滿意

如需 Blazor 的詳細資訊，請參閱[開始使用 Blazor](https://blazor.net/docs/get-started.html)。

## <a name="when-to-choose-traditional-web-apps"></a>選擇傳統 Web 應用程式的時機

以下將更詳盡說明前述挑選傳統 Web 應用程式的理由。

**您的應用程式具有簡單且可能是唯讀的用戶端需求**

許多 Web 應用程式主要以唯讀方式供絕大多數使用者使用。 唯讀 (或主要為讀取) 的應用程式往往比維護和操作大量狀態的應用程式簡單許多。 例如，搜尋引擎可能包含文字方塊的單一進入點，和用於顯示搜尋結果的第二個頁面。 匿名使用者可以輕鬆發出要求，且幾乎不需要用戶端邏輯。 同樣地，部落格或內容管理系統的公開應用程式，通常主要由幾乎沒有用戶端行為的內容所組成。 此類應用程式很容易構建為傳統的基於伺服器的 Web 應用程式，這些應用程式在 Web 服務器上執行邏輯並呈現要在瀏覽器中顯示的 HTML。 網站的每個獨特頁面都有自己的 URL，可透過搜尋引擎加上書籤並編製索引 (此為預設，不需另外將此新增為應用程式的個別功能)，在此情況下也是明顯的優勢。

**您的應用程式需要在沒有 JavaScript 支援的瀏覽器中運行**

需要在有限或不支援 JavaScript 之瀏覽器中運作的 Web 應用程式，應該使用傳統 Web 應用程式工作流程來撰寫 (或至少能夠改為使用這種行為)。 SPA 需要用戶端 JavaScript 才能運作；如果不可用，則 SPA 就不是好選擇。

**您的團隊不熟悉 JavaScript 或 TypeScript 開發技術**

如果您的小組不熟悉 JavaScript 或 TypeScript 但熟悉伺服器端 Web 應用程式開發，那麼比起 SPA 應用程式，他們可能可以更快交付傳統 Web 應用程式。 除非目標是學習編程 SPA 或是需要 SPA 提供的使用者體驗，否則對於已經熟悉建置傳統 Web 應用程式的小組而言，傳統 Web 應用程式是更具生產力的選擇。

## <a name="when-to-choose-spas"></a>選擇 SPA 的時機

以下將詳細說明應何時為您的 Web 應用程式選擇單頁應用程式開發樣式。

**應用程式必須公開具有許多功能的豐富使用者介面**

SPAs 可以支援豐富的用戶端功能，且當使用者採取動作或在應用程式各區域間巡覽時，也不需重新載入頁面。 SPA 可以更快速載入、在背景擷取資料、對個別使用者的動作回應更快，因為重新載入完整頁面的情況很少。 SPA 可支援增量更新，不需使用者按一下按鈕來提交表單即可儲存部分完成的表單或文件。 SPA 比傳統應用程式更容易支援豐富的用戶端行為，例如拖放操作。 SPA 可以設計為以離線模式執行；對用戶端模型進行的更新在其重新建立連線之後，最終會同步回伺服器。 如果應用的要求包含超出典型 HTML 表單提供的豐富功能，請選擇 SPA 樣式的應用程式。

通常，SpA 需要實現內置到傳統 Web 應用中的功能，例如在網址列中顯示反映當前操作的有意義的 URL（以及允許使用者對此 URL 進行書簽或深層連結以返回到它）。 SPA 也應允許使用者使用瀏覽器的 [上一頁] 和 [下一頁] 按鈕，且不產生意外的結果。

**您的團隊熟悉 JavaScript 和/或 TypeScript 開發**

撰寫 SPA 需要熟悉 JavaScript 及/或 TypeScript，以及用戶端程式設計技術與程式庫。 您的小組應能夠使用 Angular 等 SPA 架構來撰寫現代化 JavaScript。

> ### <a name="references--spa-frameworks"></a>參考資料 – SPA 架構
>
> - **Angular**  
>   <https://angular.io>
> - **反應**
>   <https://reactjs.org/>
> - **JavaScript 架構的比較**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**您的應用程式必須已公開其他（內部或公共）用戶端的 API**

如果您已經支援其他用戶端使用的 Web API，則建立利用這些 API 的 SPA 實作會較容易，不用重現伺服器端格式中的邏輯。 當使用者與應用程式互動時，SPA 大量使用 Web API 來查詢及更新資料。

## <a name="when-to-choose-blazor"></a>何時選擇布拉佐爾

以下是何時為 Web 應用選擇 Blazor 的更詳細的說明。

**您的應用程式必須公開豐富的使用者介面**

與基於 JavaScript 的 SPA 一樣，Blazor 應用程式可以支援豐富的用戶端行為，而無需重新載入頁面。 這些應用程式對使用者回應更快，僅獲取回應給定使用者交互所需的資料（或 HTML）。 設計得當，伺服器端 Blazor 應用可以配置為作為用戶端 Blazor 應用運行，一旦支援此功能，只需進行最少的更改即可運行。

**與 JavaScript 或 TypeScript 開發相比，您的團隊對 .NET 開發更滿意**

與 JavaScript 或 TypeScript 等用戶端語言相比，許多開發人員使用 .NET 和 Razor 工作效率更高。 由於應用程式伺服器端已經使用 .NET 開發，因此使用 Blazor 可確保團隊中的每個 .NET 開發人員都能瞭解並可能構建應用程式前端的行為。

## <a name="decision-table"></a>決策表

下面的決策表總結了在傳統 Web 應用程式、SPA 或 Blazor 應用之間進行選擇時需要考慮的一些基本因素。

| **因數**                                           | **傳統 Web 應用程式** | **單頁應用程式** | **布拉佐爾應用程式**  |
| ---------------------------------------------------- | ----------------------- | --------------------------- | --------------- |
| 小組必須熟悉 JavaScript/TypeScript | **最小**             | **必要**                | **最小**     |
| 支援無指令碼的瀏覽器                   | **支援**           | **不支援**           | **支援**   |
| 最少的用戶端應用程式行為             | **適用**         | **大材小用**                | **可行**      |
| 內容豐富且複雜的使用者介面需求            | **有限**             | **適用**             | **適用** |

>[!div class="step-by-step"]
>[上一個](modern-web-applications-characteristics.md)
>[下一個](architectural-principles.md)
