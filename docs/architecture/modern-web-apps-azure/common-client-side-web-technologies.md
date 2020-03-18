---
title: 常見的用戶端 Web 技術
description: 使用核心和 Azure 構建ASP.NET現代 Web 應用程式 |常見的用戶端 Web 技術
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 2809c8539b42e8e2250039dceed1389b3cbdcd8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449370"
---
# <a name="common-client-side-web-technologies"></a>常見的用戶端 Web 技術

> 「網站應由內而外呈現最佳效果。」  
> _- Paul Cookson_

ASP.NET Core 應用程式是 Web 應用程式，通常依賴於如 HTML、CSS 和 JavaScript 等用戶端 Web 技術。 藉由將頁面 (HTML) 的內容與其版面配置和樣式 (CSS) 分離開來，以及其行為 (透過 JavaScript)，複雜的 Web 應用程式可以利用關注點分離原則。 當這些問題並非密不可分時，未來對應用程式結構、設計或行為的變更，可以更容易進行。

雖然 HTML 和 CSS 相對穩定，但 JavaScript 透過開發人員使用應用程式架構和公用程式來建置 Web 型應用程式，正以驚人的速度發展。 本章介紹了 Web 開發人員使用 JavaScript 的幾種方法，並提供了角和 React 用戶端庫的高級概述。

> [!NOTE]
> Blazor 提供了 JavaScript 框架的替代方案，用於構建豐富的互動式用戶端使用者介面。 用戶端 Blazor 支援仍處於預覽階段，因此現在已不是本章的範圍。

## <a name="html"></a>HTML

HTML 是用於創建網頁和 Web 應用程式的標準標記語言。 其項目形成頁面的建置組塊、表示格式化的文字、影像、表單輸入和其他結構。 當瀏覽器向 URL 提出要求時，無論是擷取頁面或應用程式，傳回的第一件事都是 HTML 文件。 此 HTML 文件可能會以 CSS 的形式參考或包含其外觀和版面配置的其他資訊，或以 JavaScript 的形式表現行為。

## <a name="css"></a>CSS

CSS (階層式樣式表) 用來控制 HTML 項目的外觀和版面配置。 CSS 樣式可直接套用至 HTML 項目，在同一頁面上個別定義或在不同的檔案中定義，並由頁面所參考。 樣式串聯基於如何用於選擇指定的 HTML 項目。 比方說，樣式可能適用於整個文件，但套用於特定項目的樣式可能會將其覆寫。 同樣，特定于元素的樣式將被應用於應用於該元素的 CSS 類的樣式覆蓋，而該樣式又會由針對該元素的特定實例（通過其 ID）的樣式覆蓋該樣式。 圖 6-1

![CSS 特異性規則](./media/image6-1.png)

**圖 6-1。** CSS 精確性規則，按順序。

建議您保留樣式於各自的樣式表檔案中，並且使用基於選取範圍的串聯，來實作應用程式中一致且可重複使用的樣式。 應避免在 HTML 中放置樣式規則；並且將樣式套用於特定的單個項目 (而不是整個項目類別或套用特定 CSS 類別的項目) 應屬例外情況，而非規則。

### <a name="css-preprocessors"></a>CSS 前置處理器

CSS 樣式表缺少對條件邏輯、變數和其他程式設計語言功能的支援。 因此，大型樣式表通常包含相當多的重複，因為相同的顏色、字體或其他設置應用於 HTML 元素和 CSS 類的許多不同變體。 透過新增對變數和邏輯的支援，CSS 前置處理器可以幫助您的樣式表遵循 [DRY Principle](https://deviq.com/don-t-repeat-yourself/) (DRY 準則)。

最熱門的 CSS 前置處理器是 Sass 和 LESS。 兩者都擴充 CSS 並回溯相容，這表示一般的 CSS 檔案即為有效的 Sass 或 LESS 檔案。 Sass 基於 Ruby，LESS 基於 JavaScript，而兩者通常都是作為本機開發程序的一部分執行。 兩者都具有可用的命令列工具，以及在 Visual Studio 中內置支援使用 Gulp 或 Grunt 任務運行這些工具。

## <a name="javascript"></a>JavaScript

JavaScript 是一種動態、解譯的程式設計語言，已在 ECMAScript 語言規格中進行標準化。 其為 Web 程式設計語言。 與 CSS 一樣，JavaScript 可以在 HTML 項目中 (如同頁面內的指令碼區塊) 或在個別的檔案中定義為屬性。 與 CSS 一樣，建議將 JavaScript 組織到單獨的檔中，盡可能將其與單個網頁或應用程式視圖中的 HTML 分開。

在 Web 應用程式中使用 JavaScript 時，您通常需要執行幾項工作：

- 選取 HTML 項目並擷取及/或更新其值。

- 查詢 Web API 以取得資料。

- 將命令傳送至 Web API (並回應回呼及其結果)。

- 執行驗證。

您可以使用 JavaScript 來單獨執行所有這些工作，但有許多程式庫能使這些工作更容易。 這些程式庫中第一個也最成功的一個是 jQuery，持續成為在網頁上簡化這些工作的熱門選擇。 對於單頁應用程式 (SPA)，jQuery 並不提供許多 Angular 和 React 能提供的所需功能。

### <a name="legacy-web-apps-with-jquery"></a>使用 jQuery 的傳統 Web 應用程式

儘管 JQuery 採用 JavaScript 框架標準是古老的，但它仍然是一個常用的庫，用於處理 HTML/CSS 和構建對 Web API 進行 AJAX 調用的應用程式。 然而，jQuery 在瀏覽器文件物件模型 (DOM) 層級上運作，且預設只提供命令式模型，而非宣告式模型。

例如，假設文字方塊的值超過 10，則頁面上的項目應該可見。 在 jQuery 中，這通常是透過撰寫事件處理常式來實作，其程式碼會檢查文字方塊的值，並根據該值設定目標項目的可見性。 這是基於程式碼的命令式方法。 另一個架構則可能會使用資料繫結，以宣告方式將項目可見性繫結於文字方塊的值。 這不需要撰寫任何程式碼，而只需要修飾與資料繫結屬性有關的項目。 隨著用戶端行為變得越來越複雜，資料繫結方法通常會導致更簡單的解決方案，而代碼和條件複雜性也更少。

### <a name="jquery-vs-a-spa-framework"></a>jQuery vs SPA 架構

| **因數** | **Jquery** | **Angular**|
|--------------------------|------------|-------------|
| 提取 DOM | **是** | **是** |
| AJAX 支援 | **是** | **是** |
| 宣告式資料繫結 | **否** | **是** |
| MVC 樣式路由 | **否** | **是** |
| 範本化 | **否** | **是** |
| 深層連結路由 | **否** | **是** |

jQuery 本身缺少的大部分功能，都可以藉由新增其他程式庫來新增。 然而，像 Angular 這樣的 SPA 架構能以更加整合的方式提供這些功能，因為從一開始就是為這些功能而設計的。 此外，jQuery 是一個命令庫，這意味著您需要調用 jQuery 函數才能對 jQuery 執行任何操作。 SPA 框架提供的大部分工作和功能都可以透過宣告方式完成，而不需要撰寫實際的程式碼。

資料繫結是一個很好的範例。 在 jQuery 中，通常只需要一行代碼即可獲取 DOM 元素的值或設置元素的值。 但是，每當需要更改元素的值時，必須編寫此代碼，有時這將發生在頁面上的多個函數中。 另一個常見範例是項目可見性。 在 jQuery 中，您可能在許多不同的位置編寫代碼來控制某些元素是否可見。 在這些情況下，使用資料繫結時，不需要撰寫程式碼。 您只需將相關元素的值或可見度綁定到頁面上的*視圖模型*，對該視圖模型的更改將自動反映在繫結元素中。

### <a name="angular-spas"></a>Angular SPA

Angular 仍然是世界上最受歡迎的 JavaScript 框架之一。 自角 2 以來，團隊從零開始（使用[TypeScript）](https://www.typescriptlang.org/)重建了框架，並將該框架從原來的 AngularJS 名稱重命名為"角角"。 重新設計的 Angular 現已成為構建單頁應用程式的強大框架。該框架已有多年曆史。

Angular 應用程式是由元件所建置。 這些元件將 HTML 範本與特殊物件組合，並控制頁面的一部分。 Angular 文件的簡單元件如下所示：

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

元件使用 @Component 裝飾項目函式進行定義，該函式採用關於元件的中繼資料。 選擇器屬性標識顯示此元件的頁面上元素的 ID。 範本屬性是一個簡單的 HTML 範本，其中包含一個在最後一行定義、與元件名稱屬性對應的預留位置。

透過使用元件和範本，而不是 DOM 項目，Angular 應用程式可以在較高的抽象層次上運作，並且與僅使用 JavaScript (也稱為 "vanilla JS") 或使用 jQuery 撰寫的應用程式相比，整體程式碼更少。 Angular 也會對您如何組織用戶端指令檔施加一些順序。 按照慣例，Angular 應用程式使用通用資料夾結構，而模組和元件指令檔則位於應用程式資料夾中。 有關建置、部署和測試應用程式的 Angular 指令碼通常位於較高層級的資料夾中。

您可以使用 CLI 開發角度應用。 在本機開始 Angular 開發 (假設您已經安裝了 git 和 npm)，只需從 GitHub 複製一個存放庫並執行 `npm install` 和 `npm start` 即可。 除此之外，Angular 會自行提供 CLI，它可以創建專案、添加檔以及協助測試、捆綁和部署任務。 這種 CLI 友好性使 Angular 特別相容ASP.NET核心，這也具有出色的 CLI 支援功能。

Microsoft 開發了一個參考應用程式 [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)，其中包含一個 Angular SPA 實作。 這個應用程式包含 Angular 模組來管理線上商店的購物籃、從其目錄中載入和顯示項目，以及處理訂單建立。 您可以從 [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA) 檢視和下載範例應用程式。

### <a name="react"></a>React

與 Angular 提供完整的模型檢視控制器模式實作不同，React只關注檢視。 React 並不是一個架構，只是一個程式庫，所以若要建置 SPA 則需要利用額外的程式庫。 有許多庫被設計為與 React 一起使用，以生成豐富的單頁應用程式。

React 最重要的功能之一是使用虛擬 DOM。 虛擬 DOM 為 React 提供了幾項優勢，包括效能 (虛擬 DOM 可最佳化實際 DOM 的哪些部分需要更新) 和可測試性 (無需使用瀏覽器測試 React 及其與虛擬 DOM 的互動)。

React 在 HTML 的工作方式上也很獨特。 在程式碼和標記之間沒有嚴格的分隔 (或許是出現於 HTML 屬性中的 JavaScript 參考)，React 直接在 JavaScript 程式碼中新增 HTML 作為 JSX。 JSX 是 HTML 的類似語法，可以編譯成純 JavaScript。 例如：

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

如果您已經了解 JavaScript，學習 React 應該很容易。 與 Angular 或其他熱門的程式庫相較之下，學習曲線或涉及的特殊語法非常少。

由於 React 不是完整的架構，所以通常需要其他程式庫來處理路由、Web API 呼叫和相依性管理等事項。 好處是您可以挑選最適合的程式庫，但缺點是您需要做出所有決策，並在完成後驗證所有選定的程式庫能夠順利協作。 如果您想要好的起步，可以使用 React Slingshot 之類可以將一組相容程式庫與 React 一起預先封裝的入門套件。

### <a name="vue"></a>Vue

入門指南"Vue 是構建使用者介面的漸進式框架。 與其他單片框架不同，Vue 從一開始設計為可增量採用。 核心庫僅專注于視圖層，並且易於拾取並與其他庫或現有專案集成。 另一方面，當與現代工具和支援函式庫結合使用時，Vue 完全有能力為複雜的單頁應用程式提供動力。

開始使用 Vue 只需要將其腳本包含在 HTML 檔案中：

```html
<!-- development version, includes helpful console warnings -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

添加了框架後，您可以使用 Vue 的直截了當的範本化語法以聲明性方式將資料呈現給 DOM：

```html
<div id="app">
  {{ message }}
</div>
```

然後添加以下腳本：

```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

這足以渲染"你好Vue！ 在頁面上。 但是請注意，Vue 並不是簡單地將消息呈現給 div 一次。 它支援資料繫結和動態更新，因此，如果`message`更改的值，`<div>`將立即更新 中的值以反映它。

當然，這只能劃傷Vue能夠的表面。 在過去幾年裡，它獲得了很大的知名度，並且擁有龐大的社區。 有大量[且不斷增長的支援元件和庫，這些元件和庫](https://github.com/vuejs/awesome-vue#redux)與 Vue 配合擴展。 如果您希望向 Web 應用程式添加用戶端行為或考慮構建完整的 SPA，Vue 值得研究。

### <a name="choosing-a-spa-framework"></a>選擇 SPA 架構

在考量哪種 JavaScript 架構最適合支援您的 SPA 時，請記住下列考量：

- 您的小組是否熟悉該架構和其相依性 (在某些情況下包括 TypeScript)？

- 該架構是否專斷，以及您是否同意其預設的運作方式？

- 該架構 (或附屬程式庫) 是否包含您應用程式所需的全部功能？

- 有據可查嗎？

- 在社群中有多活躍？ 新專案正在建嗎？

- 其核心小組有多活躍？ 問題是否得到解決、新版本是否定期發出？

JavaScript 架構持續以驚人的速度改良。 使用上面列出的考量，來協助減輕選擇架構時，可能造成日後後悔對其依賴的風險。 如果您特別注重風險，請考慮提供商業支援及/或 由大型企業開發的架構。

> ### <a name="references--client-web-technologies"></a>參考資料 – 用戶端 Web 技術
>
> - **HTML 和 CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass vs. LESS**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **以 LESS、Sass 和 Font Awesome 設定樣式**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **ASP.NET核心中的用戶端開發**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **Jquery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://reactjs.org/>
> - **Vue**  
> <https://vuejs.org/>
> - **角與反應 vs Vue：2020 年選擇哪個框架**
> <https://www.codeinwp.com/blog/angular-vs-vue-vs-react/>
> - **2020 年前端開發的頂級 JavaScript 框架**  
> <https://www.freecodecamp.org/news/complete-guide-for-front-end-developers-javascript-frameworks-2019/>

>[!div class="step-by-step"]
>[上一個](common-web-application-architectures.md)
>[下一個](develop-asp-net-core-mvc-apps.md)
