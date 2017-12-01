---
title: "常見的用戶端端 web 技術"
description: "使用 ASP.NET Core 和 Azure 的現代化 Web 應用程式架構設計人員 |常見的用戶端端 web 技術"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 1084aee3d81a5df6ac99d6ec0e2ef647b4173c24
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2017
---
# <a name="common-client-side-web-technologies"></a>常見的用戶端端 Web 技術

> 「 網站應該能呈現最佳效果，從內部，和 out。 」  
> _-Paul Cookson_

## <a name="summary"></a>總結

ASP.NET Core 應用程式是 web 應用程式，它們通常依賴用戶端 web 技術，例如 HTML、 CSS 和 JavaScript。 藉由分隔的配置和樣式 (CSS) 和它的行為 （透過 JavaScript) 的頁面 (HTML) 內容，複雜的 web 應用程式可以利用分離的考量原則。 未來結構、 設計，或應用程式的行為可以變更多個輕鬆時不密不可分的這些問題。

HTML 和 CSS 相當穩定、 JavaScript、 透過應用程式架構和公用程式開發人員使用，來建置 web 應用程式，而會演變 breakneck 速度。 這一章探討一部分開發應用程式，因為提供的高階概觀 Angular 和回應的用戶端端程式庫的 web 開發人員會使用 JavaScript 的幾個方法。

## <a name="html"></a>HTML

HTML （超文字標記語言） 是用來建立網頁和 web 應用程式的標準標記語言。 其項目形成頁面，表示格式化的文字、 影像、 表單輸入和其他結構的建置組塊。 當瀏覽器至 URL，提出要求時是否提取的頁面或應用程式時，首先也就是傳回為 HTML 文件。 此 HTML 文件可能會參考或 CSS 或 JavaScript 表單中的行為的形式包含其外觀和版面配置的其他資訊。

## <a name="css"></a>CSS

CSS （階層式樣式表） 用來控制的外觀和版面配置的 HTML 項目。 CSS 樣式可以直接套用至 HTML 項目，分別定義在相同頁面上，或定義在個別的檔案，此網頁所參考。 根據選取指定的 HTML 元素的使用方式的樣式 cascade。 比方說，樣式可能會套用到整個文件，但將會套用到特定的項目樣式的被覆寫。 同樣地，會覆寫樣式套用至已套用至項目，接著會覆寫由目標為特定的執行個體 （透過其識別碼） 項目的樣式的 CSS 類別的特定元素的樣式。 圖 6-1

**圖 6-1。** CSS 明確性比較規則，順序。

![](./media/image6-1.png)

建議您最好保留樣式在自己獨立的樣式表檔案，並且將選取範圍以階層式實作一致且可重複使用的樣式，在應用程式中。 應避免將放在 HTML 中的樣式規則，而且將樣式套用至特定的個別項目 （而非整個類別的項目或有特定的 CSS 類別套用至它們的項目） 例外狀況，而不是規則。

### <a name="css-preprocessors"></a>CSS 前處理器

CSS 樣式表缺少條件邏輯、 變數和其他程式設計語言功能的支援。 因此，大型的樣式表通常包含大量的重複，當相同的色彩、 字型或其他設定會套用至 HTML 項目和 CSS 類別的許多不同的變化。 CSS 前處理器，可協助您遵循的樣式表[乾原則](http://deviq.com/don-t-repeat-yourself/)所加入的變數和邏輯的支援。

最熱門的 CSS 前處理器是 Sass 且小於。 這兩擴充 CSS 並回溯相容，這表示一般的 CSS 檔案有效的 Sass 或較少檔案。 Sass 是 Ruby 型小於 JavaScript 為基礎，且兩者通常做為您的本機開發程序的一部分執行。 兩者都有命令列執行這些工具可用，以及內建支援 Visual Studio 中的使用 Gulp 或 grunt 所完成的工作。

## <a name="javascript"></a>JavaScript

JavaScript 是動態、 解譯的程式設計語言標準化 ECMAScript 語言規格中。 它是 web 程式設計語言。 CSS，例如 JavaScript 可以定義為屬性的 HTML 項目，為指令碼 頁面上，或個別檔案中的區塊。 就像 CSS，通常建議您將 JavaScript 組織成不同的檔案，讓它維持在分隔盡可能從位於個別的網頁或應用程式檢視的 HTML。

當 web 應用程式中使用 JavaScript，有一些工作，您通常需要執行：

-   選取 HTML 項目並擷取及 （或) 更新其值

-   查詢資料的 Web 應用程式開發介面

-   將命令傳送到 Web API （和回應的回呼，以其結果）

-   執行驗證

您可以執行所有這些工作的 JavaScript，但許多程式庫存在簡化這些工作。 JQuery，仍然是簡化網頁上的這些工作的熱門選擇其中一個第一個和最成功這些程式庫。 對於單一頁面應用程式 (SPAs)，jQuery 不會提供許多 Angular 和 React 提供所需的功能。

### <a name="legacy-web-apps-with-jquery"></a>使用 jQuery 的傳統 Web 應用程式

雖然古代 JavaScript 架構標準，jQuery 仍然是相當常用的程式庫建置 AJAX 呼叫 web Api 的應用程式與使用 HTML/CSS。 不過，jQuery 瀏覽器文件物件模型 (DOM)，層級運作，且預設提供只執行必要的工作，而非宣告式模型。

例如，想像一下，是否文字方塊的值超過 10，頁面上的項目應該會看見。 在 jQuery，這通常實作撰寫事件處理常式程式碼會檢查文字方塊的值，並設定根據這個值的目標項目可見性。 這是命令性、 程式碼為基礎的方法。 另一個架構來以宣告方式將項目的可見性繫結至文字方塊的值，可能會改為使用資料繫結。 這不需要撰寫任何程式碼，但改為只需要而將資料繫結屬性的相關項目。 當用戶端行為成長更複雜時，資料繫結方法經常會導致較少的程式碼或條件式的複雜度更簡單的解決方案。

### <a name="jquery-vs-a-spa-framework"></a>jQuery vs SPA 架構

| **因素** | **jQuery** | **角度**|
|--------------------------|------------|-------------|
| 擷取 DOM | **是** | **是** |
| AJAX 支援 | **是** | **是** |
| 宣告式資料繫結 | **No** | **是** |
| MVC 樣式路由 | **No** | **是** |
| 樣板化 | **No** | **是** |
| 深層連結的路由 | **No** | **是** |

大部分的 jQuery 在本質上缺少的功能可以加入加上的其他程式庫。 不過，像 Angular SPA 架構提供更加整合的方式，這些功能，因為它從一開始記住它們設計。 此外，jQuery 是非常命令式的程式庫，這表示您需要執行任何動作與 jQuery 才能呼叫 jQuery 函式。 大部分的工作和 SPA 架構都可提供的功能可以透過以宣告方式，需要撰寫任何實際程式碼。

資料繫結是一個很好的範例。 在 jQuery，通常只需要一行程式碼來取得 DOM 元素的值，或設定項目的值。 不過，您必須撰寫此程式碼，每當您需要變更元素的值，有時候這會在頁面上的多個函式。 另一個常見範例是顯示/隱藏元素。 在 jQuery，可能會有許多不同的地方，您會撰寫程式碼來控制特定項目是否已顯示。 在這些情況下，使用資料繫結時，程式碼不需要寫入。 您將有問題的項目可見性的值直接繫結*viewmodel*上的頁面上，以及改變，viewmodel 會自動反映在繫結項目。

### <a name="angular-spas"></a>角度 SPAs

AngularJS 很快就世界上最熱門的 JavaScript 架構的其中一個。 角度 2 中，小組會重建從頭 framework 向上 (使用[TypeScript](https://www.typescriptlang.org/)) 和 AngularJS 從品牌來只需角度。 目前在第 4 版上 Angular 仍然能夠繼續建立單一頁面應用程式穩固的架構。

從元件建置角度的應用程式。 元件 HTML 範本結合特殊物件和控制網頁的一部分。 Angular 的文件的簡單元件如下所示：

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

元件會定義使用@Componentdecorator 函式，其採用的元件相關的中繼資料中。 選取器屬性會識別此元件將會顯示在頁面上元素的識別碼。 [範本] 屬性是一個簡單的 HTML 範本，其中包含對應至元件的名稱屬性，定義的最後一行的預留位置。

使用的元件和範本，而不是 DOM 項目，以角度的應用程式可以在較高層級的抽象概念和較少比使用剛才 （也稱為 「 香草 JS"） 的 JavaScript 撰寫的應用程式的整體程式碼或 jQuery 運作。 角度也會為部分的順序來組織您的用戶端指令碼檔案的方式。 依照慣例，角度的應用程式，請使用應用程式資料夾中的模組和元件的指令碼檔案的通用資料夾結構。 角度的指令碼與建置、 部署和測試應用程式通常位於較高層級的資料夾中的。

角度也會很好的命令列介面 (CLI) 工具使用。 開始角度開發在本機 （假設您已經有 git 和 npm 安裝） 使用包含只需複製的儲存機制從 GitHub 和執行\`npm 安裝\`和\`npm 開始\`。 除此之外，Angular 隨附自己 CLI 工具 」 可以建立專案、 加入檔案，以及協助進行測試、 結合在一起，及部署工作。 此 CLI tooling 易懂性可讓 Angular 與 ASP.NET Core，也提供了絕佳的 CLI 支援特別相容。

Microsoft 開發了一個參考應用程式， [eShopOnContainers](http://aka.ms/MicroservicesArchitecture)，其中包括角度 SPA 實作。 這個應用程式包含 Angular 模組來管理線上商店購物籃、 載入和顯示項目從其類別目錄，和處理順序建立。 您可以檢視和下載範例應用程式從[GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA)。

### <a name="react"></a>回應

不同於 Angular，提供完整的模型-檢視-控制器模式實作，React 只關心的檢視。 不是架構，只要程式庫，因此若要建置 SPA 您必須利用額外的程式庫。

React 的最重要功能之一是它使用虛擬 DOM 虛擬 DOM React 提供幾項優點，包括 （虛擬 DOM 可以最佳化實際 DOM 的哪些部分需要更新） 的效能和可測試性 （不需要擁有要測試 React 和其虛擬 DOM 與它互動的瀏覽器）。

回應也是不尋常的 html 的運作方式。 此時並不需要嚴格隔離程式碼和標記 （具有參考 javascript 可能出現的 HTML 屬性中） 之間做出反應加入直接 HTML 中的 JavaScript 程式碼做為 JSX。 JSX 是 HTML 類似語法，可以向純 JavaScript 編譯。 例如: 

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

如果您已經知道 JavaScript，學習 React 應該很容易。 沒有任何幾乎一樣多的學習曲線或特殊的語法中所涉及 Angular 或其他常用的程式庫。

由於 React 不完整的 framework，您通常需要其他程式庫，以處理之類的路由、 web API 呼叫和相依性管理。 好處是，您可以挑選最佳的程式庫的每一種，但缺點是您要讓所有這些決定並確認您所選擇的文件庫的所有合作完成後。 如果您想很好的起點，您可以使用回應的 Slingshot，prepackages 相容的媒體櫃 React 以及一組類似的入門套件。

### <a name="choosing-a-spa-framework"></a>選擇 SPA 架構

當考量哪些廠商的 JavaScript 架構適合以支援您的選項時，請記住下列考量：

-   您的小組是否熟悉架構和其相依性 (在某些情況下包括 TypeScript)？

-   如何 opinionated 架構，以及您同意使用的動作，其預設的方法？

-   沒有 （或附屬程式庫） 包含的所有應用程式需要的功能嗎？

-   會完善記載嗎？

-   如何使用中是其社群？ 建立新的專案所建置的它嗎？

-   如何使用中是其核心小組？ 正在解析和新的版本問題定期傳送嗎？

JavaScript 架構持續改良 breakneck 速度。 使用上面所列，來協助降低風險的選擇感到稍後將後悔所依存的架構的考量。 如果您特別風險 averse，請考慮提供商業支援及/或大型企業所開發的架構。

> ### <a name="references--client-web-technologies"></a>參考 – 用戶端 Web 技術
> - **HTML 和 CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Vs sass 此類。較低**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **設定 ASP.NET Core 應用程式，以更少、 Sass 和實用的字型樣式**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **在 ASP.NET Core 的用戶端開發**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **角度**  
> <https://angular.io/>
> - **回應**  
> <https://facebook.github.io/react/>
> - **React Slingshot**  
> <https://github.com/coryhouse/react-slingshot>
> - **React vs 角度 2 比較**  
> <https://www.codementor.io/codementorteam/react-vs-angular-2-comparison-beginners-guide-lvz5710ha>
> - **5 的 2017年最佳的 JavaScript 架構**  
> <https://hackernoon.com/5-best-javascript-frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
[上一個](常見的 web 層應用程式-architectures.md) [下一步] (develop-asp-net-core-mvc-apps.md)
