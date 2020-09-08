---
title: 在傳統 Web 應用程式和單頁應用程式之間作選擇
description: 了解建置 Web 應用程式時，如何在傳統 Web 應用程式和單頁應用程式 (SPA) 之間作選擇。
author: ardalis
ms.author: wiwagn
no-loc:
- Blazor
- WebAssembly
ms.date: 07/27/2020
ms.openlocfilehash: f04de5c350dfead4dad8c37eece7f16c9a9e00bc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515815"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>在傳統 Web 應用程式和單頁應用程式 (SPA) 之間作選擇

> 「Atwood 定律：任何可以用 JavaScript 撰寫的應用程式，最後都將以 JavaScript 撰寫。」  
> _\- Jeff Atwood_

現在有兩種建置 Web 應用程式的通用方法：在伺服器上執行大多數應用程式邏輯的傳統 Web 應用程式，以及執行大多數使用者介面邏輯的單頁應用程式 (SPA)，主要使用 Web API 與 Web 伺服器通訊。 您也可以使用混合式方法，最簡單的方式就是在較大型的傳統 web 應用程式中裝載一或多個豐富的 SPA subapplications。

使用傳統 web 應用程式的時機：

- 應用程式用戶端的需求簡單或甚至是唯讀。

- 應用程式需要在不支援 JavaScript 的瀏覽器中運作。

- 您的小組不熟悉 JavaScript 或 TypeScript 開發技術。

使用 SPA 的時機：

- 應用程式必須公開具有許多功能的豐富使用者介面。

- 您的小組熟悉 JavaScript、TypeScript 或 Blazor WebAssembly 開發。

- 您的應用程式必須已針對其他 (內部或公開) 用戶端公開 API。

此外，SPA 架構需要更多的架構和安全性專業知識。 由於頻繁的更新及新的架構，SPA 架構會經歷比傳統 Web 應用程式更大的變換。 使用與傳統 web 應用程式不同的 SPA 應用程式，設定自動化的組建和部署程式，並利用容器之類的部署選項可能更困難。

SPA 方法所能實現的使用者經驗改善，必須考慮這些考慮。

## Blazor

ASP.NET Core 包含一個模型，可用於建立豐富、互動式且可組合的使用者介面，稱為 Blazor 。 Blazor 伺服器端可讓開發人員在伺服器上使用 c # 和 Razor 建立 UI，並使用持續性 SignalR 連線，以互動方式將 UI 以互動方式連接到瀏覽器。 BlazorWebAssembly為應用程式導入了另一個選項 Blazor ，可讓他們使用在瀏覽器中執行 WebAssembly 。 由於它是實際在上執行的 .NET WebAssembly ，因此您可以從應用程式的伺服器端部分重複使用程式碼和程式庫。

Blazor 提供新的第三個選項，在評估是否要建立純伺服器呈現的 web 應用程式或 SPA 時考慮。 您可以使用建立豐富的 SPA 用戶端行為 Blazor ，而不需要進行重大的 JavaScript 開發。 Blazor 應用程式可以呼叫 Api 來要求資料或執行伺服器端作業。 他們可以在必要時與 JavaScript 交互操作，以利用 JavaScript 程式庫和架構。

請考慮在下列情況中建立您的 web 應用程式 Blazor ：

- 您的應用程式必須公開豐富的使用者介面

- 您的小組比 JavaScript 或 TypeScript 開發更熟悉 .NET 開發

如果您有想要遷移至 .NET Core 的現有 web form 應用程式，您可能會想要複習免費的電子書， [ Blazor 讓 Web Form 開發人員](../blazor-for-web-forms-developers/index.md)瞭解是否合理考慮將其遷移至 Blazor 。

如需的詳細資訊 Blazor ，請參閱[開始 Blazor 使用](https://blazor.net/docs/get-started.html)。

## <a name="when-to-choose-traditional-web-apps"></a>選擇傳統 Web 應用程式的時機

以下將更詳盡說明前述挑選傳統 Web 應用程式的理由。

**您的應用程式具有簡單且可能是唯讀的用戶端需求**

許多 Web 應用程式主要以唯讀方式供絕大多數使用者使用。 唯讀 (或主要為讀取) 的應用程式往往比維護和操作大量狀態的應用程式簡單許多。 例如，搜尋引擎可能包含文字方塊的單一進入點，和用於顯示搜尋結果的第二個頁面。 匿名使用者可以輕鬆發出要求，且幾乎不需要用戶端邏輯。 同樣地，部落格或內容管理系統的公開應用程式，通常主要由幾乎沒有用戶端行為的內容所組成。 這類應用程式很容易建立為傳統的伺服器 web 應用程式，可在 web 伺服器上執行邏輯，並且轉譯要在瀏覽器中顯示的 HTML。 網站的每個獨特頁面都有自己的 URL，可透過搜尋引擎加上書籤並編製索引 (此為預設，不需另外將此新增為應用程式的個別功能)，在此情況下也是明顯的優勢。

**您的應用程式必須在瀏覽器中運作，而不支援 JavaScript**

需要在有限或不支援 JavaScript 之瀏覽器中運作的 Web 應用程式，應該使用傳統 Web 應用程式工作流程來撰寫 (或至少能夠改為使用這種行為)。 SPA 需要用戶端 JavaScript 才能運作；如果不可用，則 SPA 就不是好選擇。

**您的小組不熟悉 JavaScript 或 TypeScript 開發技術**

如果您的小組不熟悉 JavaScript 或 TypeScript 但熟悉伺服器端 Web 應用程式開發，那麼比起 SPA 應用程式，他們可能可以更快交付傳統 Web 應用程式。 除非目標是學習編程 SPA 或是需要 SPA 提供的使用者體驗，否則對於已經熟悉建置傳統 Web 應用程式的小組而言，傳統 Web 應用程式是更具生產力的選擇。

## <a name="when-to-choose-spas"></a>選擇 SPA 的時機

以下將詳細說明應何時為您的 Web 應用程式選擇單頁應用程式開發樣式。

**應用程式必須公開具有許多功能的豐富使用者介面**

SPAs 可以支援豐富的用戶端功能，且當使用者採取動作或在應用程式各區域間巡覽時，也不需重新載入頁面。 SPA 可以更快速載入、在背景擷取資料、對個別使用者的動作回應更快，因為重新載入完整頁面的情況很少。 SPA 可支援增量更新，不需使用者按一下按鈕來提交表單即可儲存部分完成的表單或文件。 SPA 比傳統應用程式更容易支援豐富的用戶端行為，例如拖放操作。 SPA 可以設計為以離線模式執行；對用戶端模型進行的更新在其重新建立連線之後，最終會同步回伺服器。 如果您的應用程式需求包含超越一般 HTML 表單所提供的豐富功能，請選擇 SPA 樣式的應用程式。

通常，Spa 需要執行傳統 web 應用程式內建的功能，例如在網址列中顯示有意義的 URL，以反映目前的作業 (並允許使用者將此 URL 的書簽或深層連結傳回到其) 。 SPA 也應允許使用者使用瀏覽器的 [上一頁] 和 [下一頁] 按鈕，且不產生意外的結果。

**您的小組熟悉 JavaScript 及/或 TypeScript 開發**

撰寫 SPA 需要熟悉 JavaScript 及/或 TypeScript，以及用戶端程式設計技術與程式庫。 您的小組應能夠使用 Angular 等 SPA 架構來撰寫現代化 JavaScript。

> ### <a name="references--spa-frameworks"></a>參考資料 – SPA 架構
>
> - **Angular**  
>   <https://angular.io>
> - **反應**
>   <https://reactjs.org/>
> - **JavaScript 架構的比較**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**您的應用程式必須已公開其他 (內部或公用) 用戶端的 API**

如果您已經支援其他用戶端使用的 Web API，則建立利用這些 API 的 SPA 實作會較容易，不用重現伺服器端格式中的邏輯。 當使用者與應用程式互動時，SPA 大量使用 Web API 來查詢及更新資料。

## <a name="when-to-choose-no-locblazor"></a>選擇時機 Blazor

以下是 Blazor 針對 web 應用程式選擇的時機更詳細的說明。

**您的應用程式必須公開豐富的使用者介面**

如同以 JavaScript 為基礎的 Spa， Blazor 應用程式可以支援豐富的用戶端行為，而不需要重新載入頁面。 這些應用程式對使用者的回應速度更快，只會取得回應指定使用者互動所需的資料 (或 HTML) 。 伺服器端 Blazor 應用程式可設定為以用戶端應用程式的形式執行，只要 Blazor 支援這項功能，就能進行少量的變更。

**您的小組比 JavaScript 或 TypeScript 開發更熟悉 .NET 開發**

許多開發人員使用 .NET 和 Razor 比用戶端語言（例如 JavaScript 或 TypeScript）更具生產力。 由於應用程式的伺服器端已經使用 .NET 進行開發，因此使用 Blazor 可確保小組的每個 .net 開發人員都能瞭解並可能建立應用程式前端的行為。

## <a name="decision-table"></a>決策表

下列決策表摘要說明在傳統 web 應用程式、SPA 或應用程式之間進行選擇時，所要考慮的一些基本因素 Blazor 。

| **因素**                                           | **傳統 Web 應用程式** | **單一頁面應用程式** | **Blazor 應用程式**  |
| ---------------------------------------------------- | ----------------------- | --------------------------- | --------------- |
| 小組必須熟悉 JavaScript/TypeScript | **最低限度**             | **必要**                | **最低限度**     |
| 支援無指令碼的瀏覽器                   | **支援**           | **不支援**           | **支援**   |
| 最少的用戶端應用程式行為             | **適用**         | **大材小用**                | **可行**      |
| 內容豐富且複雜的使用者介面需求            | **有限**             | **適用**             | **適用** |

>[!div class="step-by-step"]
>[上一個](modern-web-applications-characteristics.md) 
>[下一步](architectural-principles.md)
