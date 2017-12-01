---
title: "傳統 web 應用程式和單一頁面應用程式之間選擇"
description: "使用 ASP.NET Core 和 Microsoft Azure 的架構設計人員現代化 web 應用程式"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 5bae77fc4e0df9d0bc7fecfad25adfcee2419084
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2017
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>傳統 Web 應用程式和單一頁面應用程式 (SPAs) 之間選擇

> 「 Atwood 的法律： 任何應用程式都可以撰寫在 JavaScript 中，最後將以 JavaScript 撰寫。 」  
> _\-Jeff Atwood_

## <a name="summary"></a>總結

有兩種一般的方法，來建置 web 應用程式現在： server 和網頁瀏覽器中執行大部分的使用者介面邏輯的單一頁面應用程式 (SPAs) 執行應用程式邏輯的大部分的傳統 web 應用程式與主要使用 web 應用程式開發介面的 web 伺服器通訊。 混合式方法，您也可以，最簡單的裝載一或多個豐富 SPA 類似子應用程式在較大的傳統 web 應用程式中。

您應該使用傳統 web 應用程式時：

-   您的應用程式用戶端需求是簡單或甚至是唯讀。

-   您的應用程式中不支援 JavaScript 瀏覽器運作所需。

-   您的小組不熟悉使用 JavaScript 或 TypeScript 的開發技巧。

您應該使用 SPA 時：

-   您的應用程式必須公開透過許多功能豐富的使用者介面。

-   您的團隊已熟悉 JavaScript 和/或 TypeScript 開發。

-   您的應用程式必須已公開其他 （內部或公用） 的用戶端應用程式開發介面。

此外，SPA 架構需要大於架構和安全性的專業知識。 在發生因為頻繁的更新及新的架構更高的變換比傳統 web 應用程式。 設定自動化的建置和部署程序，以及使用類似的容器部署選項是使用 SPA 應用程式比傳統 web 應用程式更困難。

改善使用者體驗即可進行 SPA 模型必須權衡這些考量。

## <a name="when-to-choose-traditional-web-apps"></a>選擇傳統 web 應用程式的時機

以下是更詳細的說明的先前所述原因挑選傳統 web 應用程式。

**您的應用程式有簡單、 可能是唯讀、 用戶端需求**

許多 web 應用程式主要被供以唯讀方式大部分的使用者。 唯讀 （或主要為讀取） 的應用程式通常比維護和操作狀態的極簡單許多。 例如，搜尋引擎可能包含文字方塊與用於顯示搜尋結果的第二個頁面的單一進入點。 匿名使用者可以輕鬆地進行要求，而且幾乎不需要用戶端邏輯。 同樣地，部落格或內容管理系統的公開應用程式通常包含主要是個很少用戶端行為的內容。 這類應用程式輕鬆地建立以伺服器為基礎的傳統 web 應用程式 web 伺服器上執行的邏輯，並呈現在瀏覽器中顯示的 HTML。 站台的每個唯一頁面都有自己的 URL，可以設為書籤，並以搜尋引擎 （依預設，而不必個別功能的應用程式加入此） 編製索引的事實也是明顯的好處，在這種情況。

**您的應用程式中不支援 JavaScript 瀏覽器運作所需**

需要在有限或不支援 JavaScript 的瀏覽器中運作的 web 應用程式應該使用傳統 web 應用程式工作流程中寫入 （或至少能夠改為使用這類行為）。 SPAs 需要用戶端 JavaScript，才能運作。如果無法使用，SPAs 不是很不錯的選擇。

**您的小組不熟悉與 JavaScript 或 TypeScript 開發技術**

如果您的小組不熟悉與 JavaScript 或 TypeScript，但熟悉伺服器端 web 應用程式開發，然後它們可能會比 SPA 更快速地提供傳統 web 應用程式。 學習程式 SPAs 目標，或 SPA 所提供的使用者體驗有必要，除非傳統 web 應用程式是已熟悉建置它們的小組是更具生產力的選擇。

## <a name="when-to-choose-spas"></a>當選擇 SPAs

以下是更詳細的說明何時選擇開發 web 應用程式的單一頁面應用程式樣式。

**您的應用程式必須公開透過許多功能豐富的使用者介面**

SPAs 可以支援豐富的用戶端功能，不需要重新載入該頁面，當使用者採取動作或應用程式的區域之間巡覽。 SPAs 可以擷取資料，在背景中，更快速地載入並個別使用者的動作是更能有效回應，因為完整頁面重新載入的情況很少見。 SPAs 可以支援累加式更新，使用者不必按滑鼠按鈕送出表單不儲存部分完成的表單或文件。 SPAs 可以支援豐富的用戶端行為，例如拖放，隨時會比傳統應用程式。 SPAs 為了在中斷連線的模式中，進行更新至用戶端模型最終同步處理至伺服器之後重新建立連接時執行。 如果您的應用程式需求包含超過一般的 HTML 表單所提供的豐富功能，您應該選擇 SPA 樣式的應用程式。

請注意，SPAs 經常需要實作功能所內建於傳統 web 應用程式，例如在位址列中反映目前的作業 （允許使用者書籤或深層連結至此 url 回到） 顯示的有意義的 URL。 SPAs 也應該允許使用者使用瀏覽器的上一頁及下一頁按鈕將不會意外的結果。

**您的團隊已熟悉 JavaScript 和/或 TypeScript 程式開發**

撰寫 SPAs 需要熟悉 JavaScript 和/或 TypeScript 和用戶端程式設計技術和程式庫。 您的小組應該是令人撰寫使用 SPA Angular 現代 JavaScript。

> ### <a name="references--spa-frameworks"></a>參考 – SPA 架構
> - **AngularJS**  
> <https://angularjs.org/>
> - **4 受歡迎的 JavaScript 架構的比較**  
> <https://www.developereconomics.com/feature-comparison-of-4-popular-js-mv-frameworks>

**您的應用程式必須已公開其他 （內部或公用） 的用戶端應用程式開發介面**

如果您已經支援的 web API 以供其他用戶端，它可能需要較輕鬆，若要建立一個 SPA 實作，可以利用這些 Api，而不是重現伺服器端格式中的邏輯。 SPAs 對查詢及更新的資料進行廣泛使用的 web 應用程式開發介面，當使用者與應用程式互動。

## <a name="decision-table--traditional-web-or-spa"></a>決策表 – 傳統 Web 或 SPA

下列的決策表摘要列出一些基本 SPA 傳統 web 應用程式之間選擇時要考慮的因素。

  | **因素** | **傳統 Web 應用程式** | **單一頁面應用程式** |
  |---|---|---|
  | 必要的小組熟悉 JavaScript/TypeScript | **最小** | **必要** |
  | 支援的瀏覽器不編寫指令碼 | **支援** | **不支援** |
  | 最小的用戶端應用程式行為 | **適用於** | **大材小用** |
  | 內容豐富且複雜的使用者介面需求 | **限制** | **適用於** |

>[!div class="step-by-step"]
[上一個](現代的 web 層應用程式-characteristics.md)[下一步](architectural-principles.md)
