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
# <a name="common-client-side-web-technologies"></a><span data-ttu-id="eac44-103">常見的用戶端 Web 技術</span><span class="sxs-lookup"><span data-stu-id="eac44-103">Common client-side web technologies</span></span>

> <span data-ttu-id="eac44-104">「網站應由內而外呈現最佳效果。」</span><span class="sxs-lookup"><span data-stu-id="eac44-104">"Websites should look good from the inside and out."</span></span>  
> <span data-ttu-id="eac44-105">_- Paul Cookson_</span><span class="sxs-lookup"><span data-stu-id="eac44-105">_- Paul Cookson_</span></span>

<span data-ttu-id="eac44-106">ASP.NET Core 應用程式是 Web 應用程式，通常依賴於如 HTML、CSS 和 JavaScript 等用戶端 Web 技術。</span><span class="sxs-lookup"><span data-stu-id="eac44-106">ASP.NET Core applications are web applications and they typically rely on client-side web technologies like HTML, CSS, and JavaScript.</span></span> <span data-ttu-id="eac44-107">藉由將頁面 (HTML) 的內容與其版面配置和樣式 (CSS) 分離開來，以及其行為 (透過 JavaScript)，複雜的 Web 應用程式可以利用關注點分離原則。</span><span class="sxs-lookup"><span data-stu-id="eac44-107">By separating the content of the page (the HTML) from its layout and styling (the CSS), and its behavior (via JavaScript), complex web apps can leverage the Separation of Concerns principle.</span></span> <span data-ttu-id="eac44-108">當這些問題並非密不可分時，未來對應用程式結構、設計或行為的變更，可以更容易進行。</span><span class="sxs-lookup"><span data-stu-id="eac44-108">Future changes to the structure, design, or behavior of the application can be made more easily when these concerns are not intertwined.</span></span>

<span data-ttu-id="eac44-109">雖然 HTML 和 CSS 相對穩定，但 JavaScript 透過開發人員使用應用程式架構和公用程式來建置 Web 型應用程式，正以驚人的速度發展。</span><span class="sxs-lookup"><span data-stu-id="eac44-109">While HTML and CSS are relatively stable, JavaScript, by means of the application frameworks and utilities developers work with to build web-based applications, is evolving at breakneck speed.</span></span> <span data-ttu-id="eac44-110">本章介紹了 Web 開發人員使用 JavaScript 的幾種方法，並提供了角和 React 用戶端庫的高級概述。</span><span class="sxs-lookup"><span data-stu-id="eac44-110">This chapter looks at a few ways that JavaScript is used by web developers and provides a high-level overview of the Angular and React client-side libraries.</span></span>

> [!NOTE]
> <span data-ttu-id="eac44-111">Blazor 提供了 JavaScript 框架的替代方案，用於構建豐富的互動式用戶端使用者介面。</span><span class="sxs-lookup"><span data-stu-id="eac44-111">Blazor provides an alternative to JavaScript frameworks for building rich, interactive client user interfaces.</span></span> <span data-ttu-id="eac44-112">用戶端 Blazor 支援仍處於預覽階段，因此現在已不是本章的範圍。</span><span class="sxs-lookup"><span data-stu-id="eac44-112">Client-side Blazor support is still in preview, so for now it's out of scope for this chapter.</span></span>

## <a name="html"></a><span data-ttu-id="eac44-113">HTML</span><span class="sxs-lookup"><span data-stu-id="eac44-113">HTML</span></span>

<span data-ttu-id="eac44-114">HTML 是用於創建網頁和 Web 應用程式的標準標記語言。</span><span class="sxs-lookup"><span data-stu-id="eac44-114">HTML is the standard markup language used to create web pages and web applications.</span></span> <span data-ttu-id="eac44-115">其項目形成頁面的建置組塊、表示格式化的文字、影像、表單輸入和其他結構。</span><span class="sxs-lookup"><span data-stu-id="eac44-115">Its elements form the building blocks of pages, representing formatted text, images, form inputs, and other structures.</span></span> <span data-ttu-id="eac44-116">當瀏覽器向 URL 提出要求時，無論是擷取頁面或應用程式，傳回的第一件事都是 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="eac44-116">When a browser makes a request to a URL, whether fetching a page or an application, the first thing that is returned is an HTML document.</span></span> <span data-ttu-id="eac44-117">此 HTML 文件可能會以 CSS 的形式參考或包含其外觀和版面配置的其他資訊，或以 JavaScript 的形式表現行為。</span><span class="sxs-lookup"><span data-stu-id="eac44-117">This HTML document may reference or include additional information about its look and layout in the form of CSS, or behavior in the form of JavaScript.</span></span>

## <a name="css"></a><span data-ttu-id="eac44-118">CSS</span><span class="sxs-lookup"><span data-stu-id="eac44-118">CSS</span></span>

<span data-ttu-id="eac44-119">CSS (階層式樣式表) 用來控制 HTML 項目的外觀和版面配置。</span><span class="sxs-lookup"><span data-stu-id="eac44-119">CSS (Cascading Style Sheets) is used to control the look and layout of HTML elements.</span></span> <span data-ttu-id="eac44-120">CSS 樣式可直接套用至 HTML 項目，在同一頁面上個別定義或在不同的檔案中定義，並由頁面所參考。</span><span class="sxs-lookup"><span data-stu-id="eac44-120">CSS styles can be applied directly to an HTML element, defined separately on the same page, or defined in a separate file and referenced by the page.</span></span> <span data-ttu-id="eac44-121">樣式串聯基於如何用於選擇指定的 HTML 項目。</span><span class="sxs-lookup"><span data-stu-id="eac44-121">Styles cascade based on how they are used to select a given HTML element.</span></span> <span data-ttu-id="eac44-122">比方說，樣式可能適用於整個文件，但套用於特定項目的樣式可能會將其覆寫。</span><span class="sxs-lookup"><span data-stu-id="eac44-122">For instance, a style might apply to an entire document, but would be overridden by a style that applied to a particular element.</span></span> <span data-ttu-id="eac44-123">同樣，特定于元素的樣式將被應用於應用於該元素的 CSS 類的樣式覆蓋，而該樣式又會由針對該元素的特定實例（通過其 ID）的樣式覆蓋該樣式。</span><span class="sxs-lookup"><span data-stu-id="eac44-123">Likewise, an element-specific style would be overridden by a style that applied to a CSS class that was applied to the element, which in turn would be overridden by a style targeting a specific instance of that element (via its ID).</span></span> <span data-ttu-id="eac44-124">圖 6-1</span><span class="sxs-lookup"><span data-stu-id="eac44-124">Figure 6-1</span></span>

![CSS 特異性規則](./media/image6-1.png)

<span data-ttu-id="eac44-126">**圖 6-1。**</span><span class="sxs-lookup"><span data-stu-id="eac44-126">**Figure 6-1.**</span></span> <span data-ttu-id="eac44-127">CSS 精確性規則，按順序。</span><span class="sxs-lookup"><span data-stu-id="eac44-127">CSS Specificity rules, in order.</span></span>

<span data-ttu-id="eac44-128">建議您保留樣式於各自的樣式表檔案中，並且使用基於選取範圍的串聯，來實作應用程式中一致且可重複使用的樣式。</span><span class="sxs-lookup"><span data-stu-id="eac44-128">It's best to keep styles in their own separate stylesheet files, and to use selection-based cascading to implement consistent and reusable styles within the application.</span></span> <span data-ttu-id="eac44-129">應避免在 HTML 中放置樣式規則；並且將樣式套用於特定的單個項目 (而不是整個項目類別或套用特定 CSS 類別的項目) 應屬例外情況，而非規則。</span><span class="sxs-lookup"><span data-stu-id="eac44-129">Placing style rules within HTML should be avoided, and applying styles to specific individual elements (rather than whole classes of elements, or elements that have had a particular CSS class applied to them) should be the exception, not the rule.</span></span>

### <a name="css-preprocessors"></a><span data-ttu-id="eac44-130">CSS 前置處理器</span><span class="sxs-lookup"><span data-stu-id="eac44-130">CSS preprocessors</span></span>

<span data-ttu-id="eac44-131">CSS 樣式表缺少對條件邏輯、變數和其他程式設計語言功能的支援。</span><span class="sxs-lookup"><span data-stu-id="eac44-131">CSS stylesheets lack support for conditional logic, variables, and other programming language features.</span></span> <span data-ttu-id="eac44-132">因此，大型樣式表通常包含相當多的重複，因為相同的顏色、字體或其他設置應用於 HTML 元素和 CSS 類的許多不同變體。</span><span class="sxs-lookup"><span data-stu-id="eac44-132">Thus, large stylesheets often include quite a bit of repetition, as the same color, font, or other setting is applied to many different variations of HTML elements and CSS classes.</span></span> <span data-ttu-id="eac44-133">透過新增對變數和邏輯的支援，CSS 前置處理器可以幫助您的樣式表遵循 [DRY Principle](https://deviq.com/don-t-repeat-yourself/) (DRY 準則)。</span><span class="sxs-lookup"><span data-stu-id="eac44-133">CSS preprocessors can help your stylesheets follow the [DRY principle](https://deviq.com/don-t-repeat-yourself/) by adding support for variables and logic.</span></span>

<span data-ttu-id="eac44-134">最熱門的 CSS 前置處理器是 Sass 和 LESS。</span><span class="sxs-lookup"><span data-stu-id="eac44-134">The most popular CSS preprocessors are Sass and LESS.</span></span> <span data-ttu-id="eac44-135">兩者都擴充 CSS 並回溯相容，這表示一般的 CSS 檔案即為有效的 Sass 或 LESS 檔案。</span><span class="sxs-lookup"><span data-stu-id="eac44-135">Both extend CSS and are backward compatible with it, meaning that a plain CSS file is a valid Sass or LESS file.</span></span> <span data-ttu-id="eac44-136">Sass 基於 Ruby，LESS 基於 JavaScript，而兩者通常都是作為本機開發程序的一部分執行。</span><span class="sxs-lookup"><span data-stu-id="eac44-136">Sass is Ruby-based and LESS is JavaScript based, and both typically run as part of your local development process.</span></span> <span data-ttu-id="eac44-137">兩者都具有可用的命令列工具，以及在 Visual Studio 中內置支援使用 Gulp 或 Grunt 任務運行這些工具。</span><span class="sxs-lookup"><span data-stu-id="eac44-137">Both have command-line tools available, as well as built-in support in Visual Studio for running them using Gulp or Grunt tasks.</span></span>

## <a name="javascript"></a><span data-ttu-id="eac44-138">JavaScript</span><span class="sxs-lookup"><span data-stu-id="eac44-138">JavaScript</span></span>

<span data-ttu-id="eac44-139">JavaScript 是一種動態、解譯的程式設計語言，已在 ECMAScript 語言規格中進行標準化。</span><span class="sxs-lookup"><span data-stu-id="eac44-139">JavaScript is a dynamic, interpreted programming language that has been standardized in the ECMAScript language specification.</span></span> <span data-ttu-id="eac44-140">其為 Web 程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="eac44-140">It is the programming language of the web.</span></span> <span data-ttu-id="eac44-141">與 CSS 一樣，JavaScript 可以在 HTML 項目中 (如同頁面內的指令碼區塊) 或在個別的檔案中定義為屬性。</span><span class="sxs-lookup"><span data-stu-id="eac44-141">Like CSS, JavaScript can be defined as attributes within HTML elements, as blocks of script within a page, or in separate files.</span></span> <span data-ttu-id="eac44-142">與 CSS 一樣，建議將 JavaScript 組織到單獨的檔中，盡可能將其與單個網頁或應用程式視圖中的 HTML 分開。</span><span class="sxs-lookup"><span data-stu-id="eac44-142">Just like CSS, it's recommended to organize JavaScript into separate files, keeping it separated as much as possible from the HTML found on individual web pages or application views.</span></span>

<span data-ttu-id="eac44-143">在 Web 應用程式中使用 JavaScript 時，您通常需要執行幾項工作：</span><span class="sxs-lookup"><span data-stu-id="eac44-143">When working with JavaScript in your web application, there are a few tasks that you'll commonly need to perform:</span></span>

- <span data-ttu-id="eac44-144">選取 HTML 項目並擷取及/或更新其值。</span><span class="sxs-lookup"><span data-stu-id="eac44-144">Selecting an HTML element and retrieving and/or updating its value.</span></span>

- <span data-ttu-id="eac44-145">查詢 Web API 以取得資料。</span><span class="sxs-lookup"><span data-stu-id="eac44-145">Querying a Web API for data.</span></span>

- <span data-ttu-id="eac44-146">將命令傳送至 Web API (並回應回呼及其結果)。</span><span class="sxs-lookup"><span data-stu-id="eac44-146">Sending a command to a Web API (and responding to a callback with its result).</span></span>

- <span data-ttu-id="eac44-147">執行驗證。</span><span class="sxs-lookup"><span data-stu-id="eac44-147">Performing validation.</span></span>

<span data-ttu-id="eac44-148">您可以使用 JavaScript 來單獨執行所有這些工作，但有許多程式庫能使這些工作更容易。</span><span class="sxs-lookup"><span data-stu-id="eac44-148">You can perform all of these tasks with JavaScript alone, but many libraries exist to make these tasks easier.</span></span> <span data-ttu-id="eac44-149">這些程式庫中第一個也最成功的一個是 jQuery，持續成為在網頁上簡化這些工作的熱門選擇。</span><span class="sxs-lookup"><span data-stu-id="eac44-149">One of the first and most successful of these libraries is jQuery, which continues to be a popular choice for simplifying these tasks on web pages.</span></span> <span data-ttu-id="eac44-150">對於單頁應用程式 (SPA)，jQuery 並不提供許多 Angular 和 React 能提供的所需功能。</span><span class="sxs-lookup"><span data-stu-id="eac44-150">For Single Page Applications (SPAs), jQuery doesn't provide many of the desired features that Angular and React offer.</span></span>

### <a name="legacy-web-apps-with-jquery"></a><span data-ttu-id="eac44-151">使用 jQuery 的傳統 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="eac44-151">Legacy web apps with jQuery</span></span>

<span data-ttu-id="eac44-152">儘管 JQuery 採用 JavaScript 框架標準是古老的，但它仍然是一個常用的庫，用於處理 HTML/CSS 和構建對 Web API 進行 AJAX 調用的應用程式。</span><span class="sxs-lookup"><span data-stu-id="eac44-152">Although ancient by JavaScript framework standards, jQuery continues to be a commonly used library for working with HTML/CSS and building applications that make AJAX calls to web APIs.</span></span> <span data-ttu-id="eac44-153">然而，jQuery 在瀏覽器文件物件模型 (DOM) 層級上運作，且預設只提供命令式模型，而非宣告式模型。</span><span class="sxs-lookup"><span data-stu-id="eac44-153">However, jQuery operates at the level of the browser document object model (DOM), and by default offers only an imperative, rather than declarative, model.</span></span>

<span data-ttu-id="eac44-154">例如，假設文字方塊的值超過 10，則頁面上的項目應該可見。</span><span class="sxs-lookup"><span data-stu-id="eac44-154">For example, imagine that if a textbox's value exceeds 10, an element on the page should be made visible.</span></span> <span data-ttu-id="eac44-155">在 jQuery 中，這通常是透過撰寫事件處理常式來實作，其程式碼會檢查文字方塊的值，並根據該值設定目標項目的可見性。</span><span class="sxs-lookup"><span data-stu-id="eac44-155">In jQuery, this would typically be implemented by writing an event handler with code that would inspect the textbox's value and set the visibility of the target element based on that value.</span></span> <span data-ttu-id="eac44-156">這是基於程式碼的命令式方法。</span><span class="sxs-lookup"><span data-stu-id="eac44-156">This is an imperative, code-based approach.</span></span> <span data-ttu-id="eac44-157">另一個架構則可能會使用資料繫結，以宣告方式將項目可見性繫結於文字方塊的值。</span><span class="sxs-lookup"><span data-stu-id="eac44-157">Another framework might instead use databinding to bind the visibility of the element to the value of the textbox declaratively.</span></span> <span data-ttu-id="eac44-158">這不需要撰寫任何程式碼，而只需要修飾與資料繫結屬性有關的項目。</span><span class="sxs-lookup"><span data-stu-id="eac44-158">This would not require writing any code, but instead only requires decorating the elements involved with data binding attributes.</span></span> <span data-ttu-id="eac44-159">隨著用戶端行為變得越來越複雜，資料繫結方法通常會導致更簡單的解決方案，而代碼和條件複雜性也更少。</span><span class="sxs-lookup"><span data-stu-id="eac44-159">As client-side behaviors grow more complex, data binding approaches frequently result in simpler solutions with less code and conditional complexity.</span></span>

### <a name="jquery-vs-a-spa-framework"></a><span data-ttu-id="eac44-160">jQuery vs SPA 架構</span><span class="sxs-lookup"><span data-stu-id="eac44-160">jQuery vs a SPA Framework</span></span>

| <span data-ttu-id="eac44-161">**因數**</span><span class="sxs-lookup"><span data-stu-id="eac44-161">**Factor**</span></span> | <span data-ttu-id="eac44-162">**Jquery**</span><span class="sxs-lookup"><span data-stu-id="eac44-162">**jQuery**</span></span> | <span data-ttu-id="eac44-163">**Angular**</span><span class="sxs-lookup"><span data-stu-id="eac44-163">**Angular**</span></span>|
|--------------------------|------------|-------------|
| <span data-ttu-id="eac44-164">提取 DOM</span><span class="sxs-lookup"><span data-stu-id="eac44-164">Abstracts the DOM</span></span> | <span data-ttu-id="eac44-165">**是**</span><span class="sxs-lookup"><span data-stu-id="eac44-165">**Yes**</span></span> | <span data-ttu-id="eac44-166">**是**</span><span class="sxs-lookup"><span data-stu-id="eac44-166">**Yes**</span></span> |
| <span data-ttu-id="eac44-167">AJAX 支援</span><span class="sxs-lookup"><span data-stu-id="eac44-167">AJAX Support</span></span> | <span data-ttu-id="eac44-168">**是**</span><span class="sxs-lookup"><span data-stu-id="eac44-168">**Yes**</span></span> | <span data-ttu-id="eac44-169">**是**</span><span class="sxs-lookup"><span data-stu-id="eac44-169">**Yes**</span></span> |
| <span data-ttu-id="eac44-170">宣告式資料繫結</span><span class="sxs-lookup"><span data-stu-id="eac44-170">Declarative Data Binding</span></span> | <span data-ttu-id="eac44-171">**否**</span><span class="sxs-lookup"><span data-stu-id="eac44-171">**No**</span></span> | <span data-ttu-id="eac44-172">**是**</span><span class="sxs-lookup"><span data-stu-id="eac44-172">**Yes**</span></span> |
| <span data-ttu-id="eac44-173">MVC 樣式路由</span><span class="sxs-lookup"><span data-stu-id="eac44-173">MVC-style Routing</span></span> | <span data-ttu-id="eac44-174">**否**</span><span class="sxs-lookup"><span data-stu-id="eac44-174">**No**</span></span> | <span data-ttu-id="eac44-175">**是**</span><span class="sxs-lookup"><span data-stu-id="eac44-175">**Yes**</span></span> |
| <span data-ttu-id="eac44-176">範本化</span><span class="sxs-lookup"><span data-stu-id="eac44-176">Templating</span></span> | <span data-ttu-id="eac44-177">**否**</span><span class="sxs-lookup"><span data-stu-id="eac44-177">**No**</span></span> | <span data-ttu-id="eac44-178">**是**</span><span class="sxs-lookup"><span data-stu-id="eac44-178">**Yes**</span></span> |
| <span data-ttu-id="eac44-179">深層連結路由</span><span class="sxs-lookup"><span data-stu-id="eac44-179">Deep-Link Routing</span></span> | <span data-ttu-id="eac44-180">**否**</span><span class="sxs-lookup"><span data-stu-id="eac44-180">**No**</span></span> | <span data-ttu-id="eac44-181">**是**</span><span class="sxs-lookup"><span data-stu-id="eac44-181">**Yes**</span></span> |

<span data-ttu-id="eac44-182">jQuery 本身缺少的大部分功能，都可以藉由新增其他程式庫來新增。</span><span class="sxs-lookup"><span data-stu-id="eac44-182">Most of the features jQuery lacks intrinsically can be added with the addition of other libraries.</span></span> <span data-ttu-id="eac44-183">然而，像 Angular 這樣的 SPA 架構能以更加整合的方式提供這些功能，因為從一開始就是為這些功能而設計的。</span><span class="sxs-lookup"><span data-stu-id="eac44-183">However, a SPA framework like Angular provides these features in a more integrated fashion, since it's been designed with all of them in mind from the start.</span></span> <span data-ttu-id="eac44-184">此外，jQuery 是一個命令庫，這意味著您需要調用 jQuery 函數才能對 jQuery 執行任何操作。</span><span class="sxs-lookup"><span data-stu-id="eac44-184">Also, jQuery is an imperative library, meaning that you need to call jQuery functions in order to do anything with jQuery.</span></span> <span data-ttu-id="eac44-185">SPA 框架提供的大部分工作和功能都可以透過宣告方式完成，而不需要撰寫實際的程式碼。</span><span class="sxs-lookup"><span data-stu-id="eac44-185">Much of the work and functionality that SPA frameworks provide can be done declaratively, requiring no actual code to be written.</span></span>

<span data-ttu-id="eac44-186">資料繫結是一個很好的範例。</span><span class="sxs-lookup"><span data-stu-id="eac44-186">Data binding is a great example of this.</span></span> <span data-ttu-id="eac44-187">在 jQuery 中，通常只需要一行代碼即可獲取 DOM 元素的值或設置元素的值。</span><span class="sxs-lookup"><span data-stu-id="eac44-187">In jQuery, it usually only takes one line of code to get the value of a DOM element or to set an element's value.</span></span> <span data-ttu-id="eac44-188">但是，每當需要更改元素的值時，必須編寫此代碼，有時這將發生在頁面上的多個函數中。</span><span class="sxs-lookup"><span data-stu-id="eac44-188">However, you have to write this code anytime you need to change the value of the element, and sometimes this will occur in multiple functions on a page.</span></span> <span data-ttu-id="eac44-189">另一個常見範例是項目可見性。</span><span class="sxs-lookup"><span data-stu-id="eac44-189">Another common example is element visibility.</span></span> <span data-ttu-id="eac44-190">在 jQuery 中，您可能在許多不同的位置編寫代碼來控制某些元素是否可見。</span><span class="sxs-lookup"><span data-stu-id="eac44-190">In jQuery, there might be many different places where you'd write code to control whether certain elements were visible.</span></span> <span data-ttu-id="eac44-191">在這些情況下，使用資料繫結時，不需要撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="eac44-191">In each of these cases, when using data binding, no code would need to be written.</span></span> <span data-ttu-id="eac44-192">您只需將相關元素的值或可見度綁定到頁面上的*視圖模型*，對該視圖模型的更改將自動反映在繫結元素中。</span><span class="sxs-lookup"><span data-stu-id="eac44-192">You'd simply bind the value or visibility of the elements in question to a *viewmodel* on the page, and changes to that viewmodel would automatically be reflected in the bound elements.</span></span>

### <a name="angular-spas"></a><span data-ttu-id="eac44-193">Angular SPA</span><span class="sxs-lookup"><span data-stu-id="eac44-193">Angular SPAs</span></span>

<span data-ttu-id="eac44-194">Angular 仍然是世界上最受歡迎的 JavaScript 框架之一。</span><span class="sxs-lookup"><span data-stu-id="eac44-194">Angular remains one of the world's most popular JavaScript frameworks.</span></span> <span data-ttu-id="eac44-195">自角 2 以來，團隊從零開始（使用[TypeScript）](https://www.typescriptlang.org/)重建了框架，並將該框架從原來的 AngularJS 名稱重命名為"角角"。</span><span class="sxs-lookup"><span data-stu-id="eac44-195">Since Angular 2, the team rebuilt the framework from the ground up (using [TypeScript](https://www.typescriptlang.org/)) and rebranded from the original AngularJS name to simply Angular.</span></span> <span data-ttu-id="eac44-196">重新設計的 Angular 現已成為構建單頁應用程式的強大框架。該框架已有多年曆史。</span><span class="sxs-lookup"><span data-stu-id="eac44-196">Now several years old, the redesigned Angular continues to be a robust framework for building Single Page Applications.</span></span>

<span data-ttu-id="eac44-197">Angular 應用程式是由元件所建置。</span><span class="sxs-lookup"><span data-stu-id="eac44-197">Angular applications are built from components.</span></span> <span data-ttu-id="eac44-198">這些元件將 HTML 範本與特殊物件組合，並控制頁面的一部分。</span><span class="sxs-lookup"><span data-stu-id="eac44-198">Components combine HTML templates with special objects and control a portion of the page.</span></span> <span data-ttu-id="eac44-199">Angular 文件的簡單元件如下所示：</span><span class="sxs-lookup"><span data-stu-id="eac44-199">A simple component from Angular's docs is shown here:</span></span>

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

<span data-ttu-id="eac44-200">元件使用 @Component 裝飾項目函式進行定義，該函式採用關於元件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="eac44-200">Components are defined using the @Component decorator function, which takes in metadata about the component.</span></span> <span data-ttu-id="eac44-201">選擇器屬性標識顯示此元件的頁面上元素的 ID。</span><span class="sxs-lookup"><span data-stu-id="eac44-201">The selector property identifies the ID of the element on the page where this component will be displayed.</span></span> <span data-ttu-id="eac44-202">範本屬性是一個簡單的 HTML 範本，其中包含一個在最後一行定義、與元件名稱屬性對應的預留位置。</span><span class="sxs-lookup"><span data-stu-id="eac44-202">The template property is a simple HTML template that includes a placeholder that corresponds to the component's name property, defined on the last line.</span></span>

<span data-ttu-id="eac44-203">透過使用元件和範本，而不是 DOM 項目，Angular 應用程式可以在較高的抽象層次上運作，並且與僅使用 JavaScript (也稱為 "vanilla JS") 或使用 jQuery 撰寫的應用程式相比，整體程式碼更少。</span><span class="sxs-lookup"><span data-stu-id="eac44-203">By working with components and templates, instead of DOM elements, Angular apps can operate at a higher level of abstraction and with less overall code than apps written using just JavaScript (also called "vanilla JS") or with jQuery.</span></span> <span data-ttu-id="eac44-204">Angular 也會對您如何組織用戶端指令檔施加一些順序。</span><span class="sxs-lookup"><span data-stu-id="eac44-204">Angular also imposes some order on how you organize your client-side script files.</span></span> <span data-ttu-id="eac44-205">按照慣例，Angular 應用程式使用通用資料夾結構，而模組和元件指令檔則位於應用程式資料夾中。</span><span class="sxs-lookup"><span data-stu-id="eac44-205">By convention, Angular apps use a common folder structure, with module and component script files located in an app folder.</span></span> <span data-ttu-id="eac44-206">有關建置、部署和測試應用程式的 Angular 指令碼通常位於較高層級的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="eac44-206">Angular scripts concerned with building, deploying, and testing the app are typically located in a higher-level folder.</span></span>

<span data-ttu-id="eac44-207">您可以使用 CLI 開發角度應用。</span><span class="sxs-lookup"><span data-stu-id="eac44-207">You can develop Angular apps by using a CLI.</span></span> <span data-ttu-id="eac44-208">在本機開始 Angular 開發 (假設您已經安裝了 git 和 npm)，只需從 GitHub 複製一個存放庫並執行 `npm install` 和 `npm start` 即可。</span><span class="sxs-lookup"><span data-stu-id="eac44-208">Getting started with Angular development locally (assuming you already have git and npm installed) consists of simply cloning a repo from GitHub and running `npm install` and `npm start`.</span></span> <span data-ttu-id="eac44-209">除此之外，Angular 會自行提供 CLI，它可以創建專案、添加檔以及協助測試、捆綁和部署任務。</span><span class="sxs-lookup"><span data-stu-id="eac44-209">Beyond this, Angular ships its own CLI, which can create projects, add files, and assist with testing, bundling, and deployment tasks.</span></span> <span data-ttu-id="eac44-210">這種 CLI 友好性使 Angular 特別相容ASP.NET核心，這也具有出色的 CLI 支援功能。</span><span class="sxs-lookup"><span data-stu-id="eac44-210">This CLI friendliness makes Angular especially compatible with ASP.NET Core, which also features great CLI support.</span></span>

<span data-ttu-id="eac44-211">Microsoft 開發了一個參考應用程式 [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)，其中包含一個 Angular SPA 實作。</span><span class="sxs-lookup"><span data-stu-id="eac44-211">Microsoft has developed a reference application, [eShopOnContainers](https://aka.ms/MicroservicesArchitecture), which includes an Angular SPA implementation.</span></span> <span data-ttu-id="eac44-212">這個應用程式包含 Angular 模組來管理線上商店的購物籃、從其目錄中載入和顯示項目，以及處理訂單建立。</span><span class="sxs-lookup"><span data-stu-id="eac44-212">This app includes Angular modules to manage the online store's shopping basket, load and display items from its catalog, and handling order creation.</span></span> <span data-ttu-id="eac44-213">您可以從 [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA) 檢視和下載範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="eac44-213">You can view and download the sample application from [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).</span></span>

### <a name="react"></a><span data-ttu-id="eac44-214">React</span><span class="sxs-lookup"><span data-stu-id="eac44-214">React</span></span>

<span data-ttu-id="eac44-215">與 Angular 提供完整的模型檢視控制器模式實作不同，React只關注檢視。</span><span class="sxs-lookup"><span data-stu-id="eac44-215">Unlike Angular, which offers a full Model-View-Controller pattern implementation, React is only concerned with views.</span></span> <span data-ttu-id="eac44-216">React 並不是一個架構，只是一個程式庫，所以若要建置 SPA 則需要利用額外的程式庫。</span><span class="sxs-lookup"><span data-stu-id="eac44-216">It's not a framework, just a library, so to build a SPA you'll need to leverage additional libraries.</span></span> <span data-ttu-id="eac44-217">有許多庫被設計為與 React 一起使用，以生成豐富的單頁應用程式。</span><span class="sxs-lookup"><span data-stu-id="eac44-217">There are a number of libraries that are designed to be used with React to produce rich single page applications.</span></span>

<span data-ttu-id="eac44-218">React 最重要的功能之一是使用虛擬 DOM。</span><span class="sxs-lookup"><span data-stu-id="eac44-218">One of React's most important features is its use of a virtual DOM.</span></span> <span data-ttu-id="eac44-219">虛擬 DOM 為 React 提供了幾項優勢，包括效能 (虛擬 DOM 可最佳化實際 DOM 的哪些部分需要更新) 和可測試性 (無需使用瀏覽器測試 React 及其與虛擬 DOM 的互動)。</span><span class="sxs-lookup"><span data-stu-id="eac44-219">The virtual DOM provides React with several advantages, including performance (the virtual DOM can optimize which parts of the actual DOM need to be updated) and testability (no need to have a browser to test React and its interactions with its virtual DOM).</span></span>

<span data-ttu-id="eac44-220">React 在 HTML 的工作方式上也很獨特。</span><span class="sxs-lookup"><span data-stu-id="eac44-220">React is also unusual in how it works with HTML.</span></span> <span data-ttu-id="eac44-221">在程式碼和標記之間沒有嚴格的分隔 (或許是出現於 HTML 屬性中的 JavaScript 參考)，React 直接在 JavaScript 程式碼中新增 HTML 作為 JSX。</span><span class="sxs-lookup"><span data-stu-id="eac44-221">Rather than having a strict separation between code and markup (with references to JavaScript appearing in HTML attributes perhaps), React adds HTML directly within its JavaScript code as JSX.</span></span> <span data-ttu-id="eac44-222">JSX 是 HTML 的類似語法，可以編譯成純 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="eac44-222">JSX is HTML-like syntax that can compile down to pure JavaScript.</span></span> <span data-ttu-id="eac44-223">例如：</span><span class="sxs-lookup"><span data-stu-id="eac44-223">For example:</span></span>

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

<span data-ttu-id="eac44-224">如果您已經了解 JavaScript，學習 React 應該很容易。</span><span class="sxs-lookup"><span data-stu-id="eac44-224">If you already know JavaScript, learning React should be easy.</span></span> <span data-ttu-id="eac44-225">與 Angular 或其他熱門的程式庫相較之下，學習曲線或涉及的特殊語法非常少。</span><span class="sxs-lookup"><span data-stu-id="eac44-225">There isn't nearly as much learning curve or special syntax involved as with Angular or other popular libraries.</span></span>

<span data-ttu-id="eac44-226">由於 React 不是完整的架構，所以通常需要其他程式庫來處理路由、Web API 呼叫和相依性管理等事項。</span><span class="sxs-lookup"><span data-stu-id="eac44-226">Because React isn't a full framework, you'll typically want other libraries to handle things like routing, web API calls, and dependency management.</span></span> <span data-ttu-id="eac44-227">好處是您可以挑選最適合的程式庫，但缺點是您需要做出所有決策，並在完成後驗證所有選定的程式庫能夠順利協作。</span><span class="sxs-lookup"><span data-stu-id="eac44-227">The nice thing is, you can pick the best library for each of these, but the disadvantage is that you need to make all of these decisions and verify all of your chosen libraries work well together when you're done.</span></span> <span data-ttu-id="eac44-228">如果您想要好的起步，可以使用 React Slingshot 之類可以將一組相容程式庫與 React 一起預先封裝的入門套件。</span><span class="sxs-lookup"><span data-stu-id="eac44-228">If you want a good starting point, you can use a starter kit like React Slingshot, which prepackages a set of compatible libraries together with React.</span></span>

### <a name="vue"></a><span data-ttu-id="eac44-229">Vue</span><span class="sxs-lookup"><span data-stu-id="eac44-229">Vue</span></span>

<span data-ttu-id="eac44-230">入門指南"Vue 是構建使用者介面的漸進式框架。</span><span class="sxs-lookup"><span data-stu-id="eac44-230">From its getting started guide, "Vue is a progressive framework for building user interfaces.</span></span> <span data-ttu-id="eac44-231">與其他單片框架不同，Vue 從一開始設計為可增量採用。</span><span class="sxs-lookup"><span data-stu-id="eac44-231">Unlike other monolithic frameworks, Vue is designed from the ground up to be incrementally adoptable.</span></span> <span data-ttu-id="eac44-232">核心庫僅專注于視圖層，並且易於拾取並與其他庫或現有專案集成。</span><span class="sxs-lookup"><span data-stu-id="eac44-232">The core library is focused on the view layer only, and is easy to pick up and integrate with other libraries or existing projects.</span></span> <span data-ttu-id="eac44-233">另一方面，當與現代工具和支援函式庫結合使用時，Vue 完全有能力為複雜的單頁應用程式提供動力。</span><span class="sxs-lookup"><span data-stu-id="eac44-233">On the other hand, Vue is perfectly capable of powering sophisticated Single-Page Applications when used in combination with modern tooling and supporting libraries."</span></span>

<span data-ttu-id="eac44-234">開始使用 Vue 只需要將其腳本包含在 HTML 檔案中：</span><span class="sxs-lookup"><span data-stu-id="eac44-234">Getting started with Vue simply requires including its script within an HTML file:</span></span>

```html
<!-- development version, includes helpful console warnings -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

<span data-ttu-id="eac44-235">添加了框架後，您可以使用 Vue 的直截了當的範本化語法以聲明性方式將資料呈現給 DOM：</span><span class="sxs-lookup"><span data-stu-id="eac44-235">With the framework added, you're then able to declaratively render data to the DOM using Vue's straightforward templating syntax:</span></span>

```html
<div id="app">
  {{ message }}
</div>
```

<span data-ttu-id="eac44-236">然後添加以下腳本：</span><span class="sxs-lookup"><span data-stu-id="eac44-236">and then adding the following script:</span></span>

```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

<span data-ttu-id="eac44-237">這足以渲染"你好Vue！</span><span class="sxs-lookup"><span data-stu-id="eac44-237">This is enough to render "Hello Vue!"</span></span> <span data-ttu-id="eac44-238">在頁面上。</span><span class="sxs-lookup"><span data-stu-id="eac44-238">on the page.</span></span> <span data-ttu-id="eac44-239">但是請注意，Vue 並不是簡單地將消息呈現給 div 一次。</span><span class="sxs-lookup"><span data-stu-id="eac44-239">Note, however, that Vue isn't simply rendering the message to the div once.</span></span> <span data-ttu-id="eac44-240">它支援資料繫結和動態更新，因此，如果`message`更改的值，`<div>`將立即更新 中的值以反映它。</span><span class="sxs-lookup"><span data-stu-id="eac44-240">It supports databinding and dynamic updates such that if the value of `message` changes, the value in the `<div>` is immediately updated to reflect it.</span></span>

<span data-ttu-id="eac44-241">當然，這只能劃傷Vue能夠的表面。</span><span class="sxs-lookup"><span data-stu-id="eac44-241">Of course, this only scratches the surface of what Vue is capable of.</span></span> <span data-ttu-id="eac44-242">在過去幾年裡，它獲得了很大的知名度，並且擁有龐大的社區。</span><span class="sxs-lookup"><span data-stu-id="eac44-242">It's gained a great deal of popularity in the last several years and has a large community.</span></span> <span data-ttu-id="eac44-243">有大量[且不斷增長的支援元件和庫，這些元件和庫](https://github.com/vuejs/awesome-vue#redux)與 Vue 配合擴展。</span><span class="sxs-lookup"><span data-stu-id="eac44-243">There's a [huge and growing list of supporting components and libraries](https://github.com/vuejs/awesome-vue#redux) that work with Vue to extend it as well.</span></span> <span data-ttu-id="eac44-244">如果您希望向 Web 應用程式添加用戶端行為或考慮構建完整的 SPA，Vue 值得研究。</span><span class="sxs-lookup"><span data-stu-id="eac44-244">If you're looking to add client-side behavior to your web application or considering building a full SPA, Vue is worth investigating.</span></span>

### <a name="choosing-a-spa-framework"></a><span data-ttu-id="eac44-245">選擇 SPA 架構</span><span class="sxs-lookup"><span data-stu-id="eac44-245">Choosing a SPA Framework</span></span>

<span data-ttu-id="eac44-246">在考量哪種 JavaScript 架構最適合支援您的 SPA 時，請記住下列考量：</span><span class="sxs-lookup"><span data-stu-id="eac44-246">When considering which JavaScript framework will work best to support your SPA, keep in mind the following considerations:</span></span>

- <span data-ttu-id="eac44-247">您的小組是否熟悉該架構和其相依性 (在某些情況下包括 TypeScript)？</span><span class="sxs-lookup"><span data-stu-id="eac44-247">Is your team familiar with the framework and its dependencies (including TypeScript in some cases)?</span></span>

- <span data-ttu-id="eac44-248">該架構是否專斷，以及您是否同意其預設的運作方式？</span><span class="sxs-lookup"><span data-stu-id="eac44-248">How opinionated is the framework, and do you agree with its default way of doing things?</span></span>

- <span data-ttu-id="eac44-249">該架構 (或附屬程式庫) 是否包含您應用程式所需的全部功能？</span><span class="sxs-lookup"><span data-stu-id="eac44-249">Does it (or a companion library) include all of the features your app requires?</span></span>

- <span data-ttu-id="eac44-250">有據可查嗎？</span><span class="sxs-lookup"><span data-stu-id="eac44-250">Is it well documented?</span></span>

- <span data-ttu-id="eac44-251">在社群中有多活躍？</span><span class="sxs-lookup"><span data-stu-id="eac44-251">How active is its community?</span></span> <span data-ttu-id="eac44-252">新專案正在建嗎？</span><span class="sxs-lookup"><span data-stu-id="eac44-252">Are new projects being built with it?</span></span>

- <span data-ttu-id="eac44-253">其核心小組有多活躍？</span><span class="sxs-lookup"><span data-stu-id="eac44-253">How active is its core team?</span></span> <span data-ttu-id="eac44-254">問題是否得到解決、新版本是否定期發出？</span><span class="sxs-lookup"><span data-stu-id="eac44-254">Are issues being resolved and new versions shipped regularly?</span></span>

<span data-ttu-id="eac44-255">JavaScript 架構持續以驚人的速度改良。</span><span class="sxs-lookup"><span data-stu-id="eac44-255">JavaScript frameworks continue to evolve with breakneck speed.</span></span> <span data-ttu-id="eac44-256">使用上面列出的考量，來協助減輕選擇架構時，可能造成日後後悔對其依賴的風險。</span><span class="sxs-lookup"><span data-stu-id="eac44-256">Use the considerations listed above to help mitigate the risk of choosing a framework you'll later regret being dependent upon.</span></span> <span data-ttu-id="eac44-257">如果您特別注重風險，請考慮提供商業支援及/或 由大型企業開發的架構。</span><span class="sxs-lookup"><span data-stu-id="eac44-257">If you're particularly risk-averse, consider a framework that offers commercial support and/or is being developed by a large enterprise.</span></span>

> ### <a name="references--client-web-technologies"></a><span data-ttu-id="eac44-258">參考資料 – 用戶端 Web 技術</span><span class="sxs-lookup"><span data-stu-id="eac44-258">References – Client Web Technologies</span></span>
>
> - <span data-ttu-id="eac44-259">**HTML 和 CSS**</span><span class="sxs-lookup"><span data-stu-id="eac44-259">**HTML and CSS**</span></span>  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - <span data-ttu-id="eac44-260">**Sass vs. LESS**</span><span class="sxs-lookup"><span data-stu-id="eac44-260">**Sass vs. LESS**</span></span>  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - <span data-ttu-id="eac44-261">**以 LESS、Sass 和 Font Awesome 設定樣式**</span><span class="sxs-lookup"><span data-stu-id="eac44-261">**Styling ASP.NET Core Apps with LESS, Sass, and Font Awesome**</span></span>  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - <span data-ttu-id="eac44-262">**ASP.NET核心中的用戶端開發**</span><span class="sxs-lookup"><span data-stu-id="eac44-262">**Client-Side Development in ASP.NET Core**</span></span>  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - <span data-ttu-id="eac44-263">**Jquery**</span><span class="sxs-lookup"><span data-stu-id="eac44-263">**jQuery**</span></span>  
> <https://jquery.com/>
> - <span data-ttu-id="eac44-264">**jQuery vs AngularJS**</span><span class="sxs-lookup"><span data-stu-id="eac44-264">**jQuery vs AngularJS**</span></span>  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - <span data-ttu-id="eac44-265">**Angular**</span><span class="sxs-lookup"><span data-stu-id="eac44-265">**Angular**</span></span>  
> <https://angular.io/>
> - <span data-ttu-id="eac44-266">**React**</span><span class="sxs-lookup"><span data-stu-id="eac44-266">**React**</span></span>  
> <https://reactjs.org/>
> - <span data-ttu-id="eac44-267">**Vue**</span><span class="sxs-lookup"><span data-stu-id="eac44-267">**Vue**</span></span>  
> <https://vuejs.org/>
> - <span data-ttu-id="eac44-268">**角與反應 vs Vue：2020 年選擇哪個框架**
> <https://www.codeinwp.com/blog/angular-vs-vue-vs-react/></span><span class="sxs-lookup"><span data-stu-id="eac44-268">**Angular vs React vs Vue: Which Framework to Choose in 2020**
<https://www.codeinwp.com/blog/angular-vs-vue-vs-react/></span></span>
> - <span data-ttu-id="eac44-269">**2020 年前端開發的頂級 JavaScript 框架**</span><span class="sxs-lookup"><span data-stu-id="eac44-269">**The Top JavaScript Frameworks for Front-End Development in 2020**</span></span>  
> <https://www.freecodecamp.org/news/complete-guide-for-front-end-developers-javascript-frameworks-2019/>

>[!div class="step-by-step"]
><span data-ttu-id="eac44-270">[上一個](common-web-application-architectures.md)
>[下一個](develop-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="eac44-270">[Previous](common-web-application-architectures.md)
[Next](develop-asp-net-core-mvc-apps.md)</span></span>
