---
title: 在傳統 Web 應用程式和單頁應用程式之間作選擇
description: 了解建置 Web 應用程式時，如何在傳統 Web 應用程式和單頁應用程式 (SPA) 之間作選擇。
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: d68c167dce791a31eeb5ca5729b50ec22c64f9b0
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331603"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>在傳統 Web 應用程式和單頁應用程式 (SPA) 之間作選擇

> 「Atwood 定律：任何可以用 JavaScript 撰寫的應用程式，最後都將以 JavaScript 撰寫。」  
> _\- Jeff Atwood_

現在有兩種建置 Web 應用程式的通用方法：在伺服器上執行大多數應用程式邏輯的傳統 Web 應用程式，以及執行大多數使用者介面邏輯的單頁應用程式 (SPA)，主要使用 Web API 與 Web 伺服器通訊。 混合式方法也是可能的，最簡單方法為在較大的傳統 Web 應用程式中，裝載一或多個豐富、類似 SPA 的子應用程式。

您應該使用傳統 Web 應用程式的時機：

- 應用程式用戶端的需求簡單或甚至是唯讀。

- 應用程式需要在不支援 JavaScript 的瀏覽器中運作。

- 您的小組不熟悉 JavaScript 或 TypeScript 開發技術。

您應該使用 SPA 的時機：

- 應用程式必須公開具有許多功能的豐富使用者介面。

- 您的小組熟悉 JavaScript 及/或 TypeScript 開發。

- 您的應用程式必須已針對其他 (內部或公開) 用戶端公開 API。

此外，SPA 架構需要更多的架構和安全性專業知識。 由於頻繁的更新及新的架構，SPA 架構會經歷比傳統 Web 應用程式更大的變換。 設定自動化的建置和部署程序、使用容器等部署選項，比傳統 Web 應用程式更難用於 SPA 應用程式。

基於這些考量，必須權衡 SPA 模型使用者體驗的改善。

## <a name="blazor"></a>Blazor

ASP.NET Core 3.0 推出了新的模型，用以建置豐富的互動式可組合 UI，該模型稱為 Blazor。 Blazor 伺服器端可讓開發人員在伺服器上使用 Razor 建置 UI，並使用 JavaScript 程式庫 WebAssembly 讓該程式碼傳遞至瀏覽器和執行的用戶端。 ASP.NET Core 3.0 仍在開發，但您將會在此電子書的 3.0 更新中看到這項技術的更多功能。 如需 Blazor 的詳細資訊，請參閱[開始使用 Blazor](https://blazor.net/docs/get-started.html)。

## <a name="when-to-choose-traditional-web-apps"></a>選擇傳統 Web 應用程式的時機

以下將更詳盡說明前述挑選傳統 Web 應用程式的理由。

**您的應用程式具有簡單且可能是唯讀的用戶端需求**

許多 Web 應用程式主要以唯讀方式供絕大多數使用者使用。 唯讀 (或主要為讀取) 的應用程式往往比維護和操作大量狀態的應用程式簡單許多。 例如，搜尋引擎可能包含文字方塊的單一進入點，和用於顯示搜尋結果的第二個頁面。 匿名使用者可以輕鬆發出要求，且幾乎不需要用戶端邏輯。 同樣地，部落格或內容管理系統的公開應用程式，通常主要由幾乎沒有用戶端行為的內容所組成。 這類應用程式很容易建立為伺服器型的傳統 Web 應用程式；在 Web 伺服器上執行邏輯並轉譯 HTML 使其顯示於瀏覽器中。 網站的每個獨特頁面都有自己的 URL，可透過搜尋引擎加上書籤並編製索引 (此為預設，不需另外將此新增為應用程式的個別功能)，在此情況下也是明顯的優勢。

**應用程式需要在不支援 JavaScript 的瀏覽器中運作**

需要在有限或不支援 JavaScript 之瀏覽器中運作的 Web 應用程式，應該使用傳統 Web 應用程式工作流程來撰寫 (或至少能夠改為使用這種行為)。 SPA 需要用戶端 JavaScript 才能運作；如果不可用，則 SPA 就不是好選擇。

**您的小組不熟悉 JavaScript 或 TypeScript 開發技術**

如果您的小組不熟悉 JavaScript 或 TypeScript 但熟悉伺服器端 Web 應用程式開發，那麼比起 SPA 應用程式，他們可能可以更快交付傳統 Web 應用程式。 除非目標是學習編程 SPA 或是需要 SPA 提供的使用者體驗，否則對於已經熟悉建置傳統 Web 應用程式的小組而言，傳統 Web 應用程式是更具生產力的選擇。

## <a name="when-to-choose-spas"></a>選擇 SPA 的時機

以下將詳細說明應何時為您的 Web 應用程式選擇單頁應用程式開發樣式。

**應用程式必須公開具有許多功能的豐富使用者介面**

SPAs 可以支援豐富的用戶端功能，且當使用者採取動作或在應用程式各區域間巡覽時，也不需重新載入頁面。 SPA 可以更快速載入、在背景擷取資料、對個別使用者的動作回應更快，因為重新載入完整頁面的情況很少。 SPA 可支援增量更新，不需使用者按一下按鈕來提交表單即可儲存部分完成的表單或文件。 SPA 比傳統應用程式更容易支援豐富的用戶端行為，例如拖放操作。 SPA 可以設計為以離線模式執行；對用戶端模型進行的更新在其重新建立連線之後，最終會同步回伺服器。 如果您的應用程式需要包含豐富的功能，超出了典型 HTML 表單能提供的範圍，則應選擇 SPA 樣式的應用程式。

請注意，SPA 經常需要實作內建於傳統 Web 應用程式的功能，例如在反映目前作業之網址列中顯示有意義的 URL (允許使用者將此 URL 加上書籤或深層連結以返回至此 URL)。 SPA 也應允許使用者使用瀏覽器的 [上一頁] 和 [下一頁] 按鈕，且不產生意外的結果。

**您的小組熟悉 JavaScript 及/或 TypeScript 開發**

撰寫 SPA 需要熟悉 JavaScript 及/或 TypeScript，以及用戶端程式設計技術與程式庫。 您的小組應能夠使用 Angular 等 SPA 架構來撰寫現代化 JavaScript。

> ### <a name="references--spa-frameworks"></a>參考資料 – SPA 架構
>
> - **Angular**  
>   <https://angular.io>
> - **JavaScript 架構的比較**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**您的應用程式必須已針對其他 (內部或公開) 用戶端公開 API**

如果您已經支援其他用戶端使用的 Web API，則建立利用這些 API 的 SPA 實作會較容易，不用重現伺服器端格式中的邏輯。 當使用者與應用程式互動時，SPA 大量使用 Web API 來查詢及更新資料。

## <a name="decision-table--traditional-web-or-spa"></a>決策表 – 傳統 Web 或 SPA

下列決策表摘要列出在傳統 Web 應用程式和 SPA 之間作選擇時需要考慮的一些基本因素。

| **因素**                                           | **傳統 Web 應用程式** | **單一頁面應用程式** |
| ---------------------------------------------------- | ----------------------- | --------------------------- |
| 小組必須熟悉 JavaScript/TypeScript | **最少**             | **必要**                |
| 支援無指令碼的瀏覽器                   | **支援**           | **不支援**           |
| 最少的用戶端應用程式行為             | **適用**         | **大材小用**                |
| 內容豐富且複雜的使用者介面需求            | **有限**             | **適用**             |

>[!div class="step-by-step"]
>[上一頁](modern-web-applications-characteristics.md)
>[下一頁](architectural-principles.md)
