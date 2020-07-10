---
title: 通用用戶端 Web 技術
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 |一般用戶端 web 技術
author: ardalis
ms.author: wiwagn
no-loc:
- Blazor
ms.date: 12/04/2019
ms.openlocfilehash: e8ea035c491fad39d2932572255a19c7c1493418
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174350"
---
# <a name="common-client-side-web-technologies"></a><span data-ttu-id="68731-103">通用用戶端 Web 技術</span><span class="sxs-lookup"><span data-stu-id="68731-103">Common client-side web technologies</span></span>

> <span data-ttu-id="68731-104">「網站應由內而外呈現最佳效果。」</span><span class="sxs-lookup"><span data-stu-id="68731-104">"Websites should look good from the inside and out."</span></span>  
> <span data-ttu-id="68731-105">_- Paul Cookson_</span><span class="sxs-lookup"><span data-stu-id="68731-105">_- Paul Cookson_</span></span>

<span data-ttu-id="68731-106">ASP.NET Core 應用程式是 Web 應用程式，通常依賴於如 HTML、CSS 和 JavaScript 等用戶端 Web 技術。</span><span class="sxs-lookup"><span data-stu-id="68731-106">ASP.NET Core applications are web applications and they typically rely on client-side web technologies like HTML, CSS, and JavaScript.</span></span> <span data-ttu-id="68731-107">藉由將頁面 (HTML) 的內容與其版面配置和樣式 (CSS) 分離開來，以及其行為 (透過 JavaScript)，複雜的 Web 應用程式可以利用關注點分離原則。</span><span class="sxs-lookup"><span data-stu-id="68731-107">By separating the content of the page (the HTML) from its layout and styling (the CSS), and its behavior (via JavaScript), complex web apps can leverage the Separation of Concerns principle.</span></span> <span data-ttu-id="68731-108">當這些問題並非密不可分時，未來對應用程式結構、設計或行為的變更，可以更容易進行。</span><span class="sxs-lookup"><span data-stu-id="68731-108">Future changes to the structure, design, or behavior of the application can be made more easily when these concerns are not intertwined.</span></span>

<span data-ttu-id="68731-109">雖然 HTML 和 CSS 相對穩定，但 JavaScript 透過開發人員使用應用程式架構和公用程式來建置 Web 型應用程式，正以驚人的速度發展。</span><span class="sxs-lookup"><span data-stu-id="68731-109">While HTML and CSS are relatively stable, JavaScript, by means of the application frameworks and utilities developers work with to build web-based applications, is evolving at breakneck speed.</span></span> <span data-ttu-id="68731-110">本章探討 網頁程式開發人員使用 JavaScript 的幾種方式，並提供角度和回應用戶端程式庫的高階總覽。</span><span class="sxs-lookup"><span data-stu-id="68731-110">This chapter looks at a few ways that JavaScript is used by web developers and provides a high-level overview of the Angular and React client-side libraries.</span></span>

> [!NOTE]
> Blazor<span data-ttu-id="68731-111">提供 JavaScript 架構的替代方案，以建立豐富的互動式用戶端使用者介面。</span><span class="sxs-lookup"><span data-stu-id="68731-111"> provides an alternative to JavaScript frameworks for building rich, interactive client user interfaces.</span></span> <span data-ttu-id="68731-112">用戶端 Blazor 支援仍處於預覽狀態，因此現在已超出本章節的範圍。</span><span class="sxs-lookup"><span data-stu-id="68731-112">Client-side Blazor support is still in preview, so for now it's out of scope for this chapter.</span></span>

## <a name="html"></a><span data-ttu-id="68731-113">HTML</span><span class="sxs-lookup"><span data-stu-id="68731-113">HTML</span></span>

<span data-ttu-id="68731-114">HTML 是用來建立網頁和 web 應用程式的標準標記語言。</span><span class="sxs-lookup"><span data-stu-id="68731-114">HTML is the standard markup language used to create web pages and web applications.</span></span> <span data-ttu-id="68731-115">其項目形成頁面的建置組塊、表示格式化的文字、影像、表單輸入和其他結構。</span><span class="sxs-lookup"><span data-stu-id="68731-115">Its elements form the building blocks of pages, representing formatted text, images, form inputs, and other structures.</span></span> <span data-ttu-id="68731-116">當瀏覽器向 URL 提出要求時，無論是擷取頁面或應用程式，傳回的第一件事都是 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="68731-116">When a browser makes a request to a URL, whether fetching a page or an application, the first thing that is returned is an HTML document.</span></span> <span data-ttu-id="68731-117">此 HTML 文件可能會以 CSS 的形式參考或包含其外觀和版面配置的其他資訊，或以 JavaScript 的形式表現行為。</span><span class="sxs-lookup"><span data-stu-id="68731-117">This HTML document may reference or include additional information about its look and layout in the form of CSS, or behavior in the form of JavaScript.</span></span>

## <a name="css"></a><span data-ttu-id="68731-118">CSS</span><span class="sxs-lookup"><span data-stu-id="68731-118">CSS</span></span>

<span data-ttu-id="68731-119">CSS (階層式樣式表) 用來控制 HTML 項目的外觀和版面配置。</span><span class="sxs-lookup"><span data-stu-id="68731-119">CSS (Cascading Style Sheets) is used to control the look and layout of HTML elements.</span></span> <span data-ttu-id="68731-120">CSS 樣式可直接套用至 HTML 項目，在同一頁面上個別定義或在不同的檔案中定義，並由頁面所參考。</span><span class="sxs-lookup"><span data-stu-id="68731-120">CSS styles can be applied directly to an HTML element, defined separately on the same page, or defined in a separate file and referenced by the page.</span></span> <span data-ttu-id="68731-121">樣式串聯基於如何用於選擇指定的 HTML 項目。</span><span class="sxs-lookup"><span data-stu-id="68731-121">Styles cascade based on how they are used to select a given HTML element.</span></span> <span data-ttu-id="68731-122">比方說，樣式可能適用於整個文件，但套用於特定項目的樣式可能會將其覆寫。</span><span class="sxs-lookup"><span data-stu-id="68731-122">For instance, a style might apply to an entire document, but would be overridden by a style that applied to a particular element.</span></span> <span data-ttu-id="68731-123">同樣地，專案專屬的樣式會被套用至已套用至專案之 CSS 類別的樣式所覆寫，而這會由以該元素的特定實例為目標的樣式加以覆寫， (透過其識別碼) 。</span><span class="sxs-lookup"><span data-stu-id="68731-123">Likewise, an element-specific style would be overridden by a style that applied to a CSS class that was applied to the element, which in turn would be overridden by a style targeting a specific instance of that element (via its ID).</span></span> <span data-ttu-id="68731-124">圖 6-1</span><span class="sxs-lookup"><span data-stu-id="68731-124">Figure 6-1</span></span>

![CSS 的明確規則](./media/image6-1.png)

<span data-ttu-id="68731-126">**圖6-1。**</span><span class="sxs-lookup"><span data-stu-id="68731-126">**Figure 6-1.**</span></span> <span data-ttu-id="68731-127">CSS 精確性規則，按順序。</span><span class="sxs-lookup"><span data-stu-id="68731-127">CSS Specificity rules, in order.</span></span>

<span data-ttu-id="68731-128">建議您保留樣式於各自的樣式表檔案中，並且使用基於選取範圍的串聯，來實作應用程式中一致且可重複使用的樣式。</span><span class="sxs-lookup"><span data-stu-id="68731-128">It's best to keep styles in their own separate stylesheet files, and to use selection-based cascading to implement consistent and reusable styles within the application.</span></span> <span data-ttu-id="68731-129">應避免在 HTML 中放置樣式規則；並且將樣式套用於特定的單個項目 (而不是整個項目類別或套用特定 CSS 類別的項目) 應屬例外情況，而非規則。</span><span class="sxs-lookup"><span data-stu-id="68731-129">Placing style rules within HTML should be avoided, and applying styles to specific individual elements (rather than whole classes of elements, or elements that have had a particular CSS class applied to them) should be the exception, not the rule.</span></span>

### <a name="css-preprocessors"></a><span data-ttu-id="68731-130">CSS 前置處理器</span><span class="sxs-lookup"><span data-stu-id="68731-130">CSS preprocessors</span></span>

<span data-ttu-id="68731-131">CSS 樣式表缺少對條件邏輯、變數和其他程式設計語言功能的支援。</span><span class="sxs-lookup"><span data-stu-id="68731-131">CSS stylesheets lack support for conditional logic, variables, and other programming language features.</span></span> <span data-ttu-id="68731-132">因此，大型樣式表單通常會包含相當多的重複專案，因為相同的色彩、字型或其他設定會套用至 HTML 專案和 CSS 類別的許多不同變化。</span><span class="sxs-lookup"><span data-stu-id="68731-132">Thus, large stylesheets often include quite a bit of repetition, as the same color, font, or other setting is applied to many different variations of HTML elements and CSS classes.</span></span> <span data-ttu-id="68731-133">透過新增對變數和邏輯的支援，CSS 前置處理器可以幫助您的樣式表遵循 [DRY Principle](https://deviq.com/don-t-repeat-yourself/) (DRY 準則)。</span><span class="sxs-lookup"><span data-stu-id="68731-133">CSS preprocessors can help your stylesheets follow the [DRY principle](https://deviq.com/don-t-repeat-yourself/) by adding support for variables and logic.</span></span>

<span data-ttu-id="68731-134">最熱門的 CSS 前置處理器是 Sass 和 LESS。</span><span class="sxs-lookup"><span data-stu-id="68731-134">The most popular CSS preprocessors are Sass and LESS.</span></span> <span data-ttu-id="68731-135">兩者都擴充 CSS 並回溯相容，這表示一般的 CSS 檔案即為有效的 Sass 或 LESS 檔案。</span><span class="sxs-lookup"><span data-stu-id="68731-135">Both extend CSS and are backward compatible with it, meaning that a plain CSS file is a valid Sass or LESS file.</span></span> <span data-ttu-id="68731-136">Sass 基於 Ruby，LESS 基於 JavaScript，而兩者通常都是作為本機開發程序的一部分執行。</span><span class="sxs-lookup"><span data-stu-id="68731-136">Sass is Ruby-based and LESS is JavaScript based, and both typically run as part of your local development process.</span></span> <span data-ttu-id="68731-137">兩者都有可用的命令列工具，以及使用 Gulp 或 Grunt 工作來執行 Visual Studio 的內建支援。</span><span class="sxs-lookup"><span data-stu-id="68731-137">Both have command-line tools available, as well as built-in support in Visual Studio for running them using Gulp or Grunt tasks.</span></span>

## <a name="javascript"></a><span data-ttu-id="68731-138">JavaScript</span><span class="sxs-lookup"><span data-stu-id="68731-138">JavaScript</span></span>

<span data-ttu-id="68731-139">JavaScript 是一種動態、解譯的程式設計語言，已在 ECMAScript 語言規格中進行標準化。</span><span class="sxs-lookup"><span data-stu-id="68731-139">JavaScript is a dynamic, interpreted programming language that has been standardized in the ECMAScript language specification.</span></span> <span data-ttu-id="68731-140">其為 Web 程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="68731-140">It is the programming language of the web.</span></span> <span data-ttu-id="68731-141">與 CSS 一樣，JavaScript 可以在 HTML 項目中 (如同頁面內的指令碼區塊) 或在個別的檔案中定義為屬性。</span><span class="sxs-lookup"><span data-stu-id="68731-141">Like CSS, JavaScript can be defined as attributes within HTML elements, as blocks of script within a page, or in separate files.</span></span> <span data-ttu-id="68731-142">就像 CSS 一樣，建議您將 JavaScript 組織成不同的檔案，讓它盡可能地根據個別網頁或應用程式視圖上找到的 HTML 加以分隔。</span><span class="sxs-lookup"><span data-stu-id="68731-142">Just like CSS, it's recommended to organize JavaScript into separate files, keeping it separated as much as possible from the HTML found on individual web pages or application views.</span></span>

<span data-ttu-id="68731-143">在 Web 應用程式中使用 JavaScript 時，您通常需要執行幾項工作：</span><span class="sxs-lookup"><span data-stu-id="68731-143">When working with JavaScript in your web application, there are a few tasks that you'll commonly need to perform:</span></span>

- <span data-ttu-id="68731-144">選取 HTML 項目並擷取及/或更新其值。</span><span class="sxs-lookup"><span data-stu-id="68731-144">Selecting an HTML element and retrieving and/or updating its value.</span></span>

- <span data-ttu-id="68731-145">查詢 Web API 以取得資料。</span><span class="sxs-lookup"><span data-stu-id="68731-145">Querying a Web API for data.</span></span>

- <span data-ttu-id="68731-146">將命令傳送至 Web API (並回應回呼及其結果)。</span><span class="sxs-lookup"><span data-stu-id="68731-146">Sending a command to a Web API (and responding to a callback with its result).</span></span>

- <span data-ttu-id="68731-147">執行驗證。</span><span class="sxs-lookup"><span data-stu-id="68731-147">Performing validation.</span></span>

<span data-ttu-id="68731-148">您可以使用 JavaScript 來單獨執行所有這些工作，但有許多程式庫能使這些工作更容易。</span><span class="sxs-lookup"><span data-stu-id="68731-148">You can perform all of these tasks with JavaScript alone, but many libraries exist to make these tasks easier.</span></span> <span data-ttu-id="68731-149">這些程式庫中第一個也最成功的一個是 jQuery，持續成為在網頁上簡化這些工作的熱門選擇。</span><span class="sxs-lookup"><span data-stu-id="68731-149">One of the first and most successful of these libraries is jQuery, which continues to be a popular choice for simplifying these tasks on web pages.</span></span> <span data-ttu-id="68731-150">對於單頁應用程式 (SPA)，jQuery 並不提供許多 Angular 和 React 能提供的所需功能。</span><span class="sxs-lookup"><span data-stu-id="68731-150">For Single Page Applications (SPAs), jQuery doesn't provide many of the desired features that Angular and React offer.</span></span>

### <a name="legacy-web-apps-with-jquery"></a><span data-ttu-id="68731-151">使用 jQuery 的傳統 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="68731-151">Legacy web apps with jQuery</span></span>

<span data-ttu-id="68731-152">雖然古的 JavaScript 架構標準，jQuery 仍然是常用的程式庫，用於使用 HTML/CSS，以及建立對 web Api 進行 AJAX 呼叫的應用程式。</span><span class="sxs-lookup"><span data-stu-id="68731-152">Although ancient by JavaScript framework standards, jQuery continues to be a commonly used library for working with HTML/CSS and building applications that make AJAX calls to web APIs.</span></span> <span data-ttu-id="68731-153">然而，jQuery 在瀏覽器文件物件模型 (DOM) 層級上運作，且預設只提供命令式模型，而非宣告式模型。</span><span class="sxs-lookup"><span data-stu-id="68731-153">However, jQuery operates at the level of the browser document object model (DOM), and by default offers only an imperative, rather than declarative, model.</span></span>

<span data-ttu-id="68731-154">例如，假設文字方塊的值超過 10，則頁面上的項目應該可見。</span><span class="sxs-lookup"><span data-stu-id="68731-154">For example, imagine that if a textbox's value exceeds 10, an element on the page should be made visible.</span></span> <span data-ttu-id="68731-155">在 jQuery 中，這通常是透過撰寫事件處理常式來實作，其程式碼會檢查文字方塊的值，並根據該值設定目標項目的可見性。</span><span class="sxs-lookup"><span data-stu-id="68731-155">In jQuery, this would typically be implemented by writing an event handler with code that would inspect the textbox's value and set the visibility of the target element based on that value.</span></span> <span data-ttu-id="68731-156">這是基於程式碼的命令式方法。</span><span class="sxs-lookup"><span data-stu-id="68731-156">This is an imperative, code-based approach.</span></span> <span data-ttu-id="68731-157">另一個架構則可能會使用資料繫結，以宣告方式將項目可見性繫結於文字方塊的值。</span><span class="sxs-lookup"><span data-stu-id="68731-157">Another framework might instead use databinding to bind the visibility of the element to the value of the textbox declaratively.</span></span> <span data-ttu-id="68731-158">這不需要撰寫任何程式碼，而只需要修飾與資料繫結屬性有關的項目。</span><span class="sxs-lookup"><span data-stu-id="68731-158">This would not require writing any code, but instead only requires decorating the elements involved with data binding attributes.</span></span> <span data-ttu-id="68731-159">隨著用戶端的行為變得越來越複雜，資料系結方法經常會產生較少程式碼和條件式複雜性的較簡單解決方案。</span><span class="sxs-lookup"><span data-stu-id="68731-159">As client-side behaviors grow more complex, data binding approaches frequently result in simpler solutions with less code and conditional complexity.</span></span>

### <a name="jquery-vs-a-spa-framework"></a><span data-ttu-id="68731-160">jQuery vs SPA 架構</span><span class="sxs-lookup"><span data-stu-id="68731-160">jQuery vs a SPA Framework</span></span>

| <span data-ttu-id="68731-161">**因素**</span><span class="sxs-lookup"><span data-stu-id="68731-161">**Factor**</span></span> | <span data-ttu-id="68731-162">**jQuery**</span><span class="sxs-lookup"><span data-stu-id="68731-162">**jQuery**</span></span> | <span data-ttu-id="68731-163">**Angular**</span><span class="sxs-lookup"><span data-stu-id="68731-163">**Angular**</span></span>|
|--------------------------|------------|-------------|
| <span data-ttu-id="68731-164">提取 DOM</span><span class="sxs-lookup"><span data-stu-id="68731-164">Abstracts the DOM</span></span> | <span data-ttu-id="68731-165">**是**</span><span class="sxs-lookup"><span data-stu-id="68731-165">**Yes**</span></span> | <span data-ttu-id="68731-166">**是**</span><span class="sxs-lookup"><span data-stu-id="68731-166">**Yes**</span></span> |
| <span data-ttu-id="68731-167">AJAX 支援</span><span class="sxs-lookup"><span data-stu-id="68731-167">AJAX Support</span></span> | <span data-ttu-id="68731-168">**是**</span><span class="sxs-lookup"><span data-stu-id="68731-168">**Yes**</span></span> | <span data-ttu-id="68731-169">**是**</span><span class="sxs-lookup"><span data-stu-id="68731-169">**Yes**</span></span> |
| <span data-ttu-id="68731-170">宣告式資料繫結</span><span class="sxs-lookup"><span data-stu-id="68731-170">Declarative Data Binding</span></span> | <span data-ttu-id="68731-171">**否**</span><span class="sxs-lookup"><span data-stu-id="68731-171">**No**</span></span> | <span data-ttu-id="68731-172">**是**</span><span class="sxs-lookup"><span data-stu-id="68731-172">**Yes**</span></span> |
| <span data-ttu-id="68731-173">MVC 樣式路由</span><span class="sxs-lookup"><span data-stu-id="68731-173">MVC-style Routing</span></span> | <span data-ttu-id="68731-174">**否**</span><span class="sxs-lookup"><span data-stu-id="68731-174">**No**</span></span> | <span data-ttu-id="68731-175">**是**</span><span class="sxs-lookup"><span data-stu-id="68731-175">**Yes**</span></span> |
| <span data-ttu-id="68731-176">範本化</span><span class="sxs-lookup"><span data-stu-id="68731-176">Templating</span></span> | <span data-ttu-id="68731-177">**否**</span><span class="sxs-lookup"><span data-stu-id="68731-177">**No**</span></span> | <span data-ttu-id="68731-178">**是**</span><span class="sxs-lookup"><span data-stu-id="68731-178">**Yes**</span></span> |
| <span data-ttu-id="68731-179">深層連結路由</span><span class="sxs-lookup"><span data-stu-id="68731-179">Deep-Link Routing</span></span> | <span data-ttu-id="68731-180">**否**</span><span class="sxs-lookup"><span data-stu-id="68731-180">**No**</span></span> | <span data-ttu-id="68731-181">**是**</span><span class="sxs-lookup"><span data-stu-id="68731-181">**Yes**</span></span> |

<span data-ttu-id="68731-182">jQuery 本身缺少的大部分功能，都可以藉由新增其他程式庫來新增。</span><span class="sxs-lookup"><span data-stu-id="68731-182">Most of the features jQuery lacks intrinsically can be added with the addition of other libraries.</span></span> <span data-ttu-id="68731-183">然而，像 Angular 這樣的 SPA 架構能以更加整合的方式提供這些功能，因為從一開始就是為這些功能而設計的。</span><span class="sxs-lookup"><span data-stu-id="68731-183">However, a SPA framework like Angular provides these features in a more integrated fashion, since it's been designed with all of them in mind from the start.</span></span> <span data-ttu-id="68731-184">此外，jQuery 是命令式程式庫，這表示您必須呼叫 jQuery 函式，才能使用 jQuery 執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="68731-184">Also, jQuery is an imperative library, meaning that you need to call jQuery functions in order to do anything with jQuery.</span></span> <span data-ttu-id="68731-185">SPA 框架提供的大部分工作和功能都可以透過宣告方式完成，而不需要撰寫實際的程式碼。</span><span class="sxs-lookup"><span data-stu-id="68731-185">Much of the work and functionality that SPA frameworks provide can be done declaratively, requiring no actual code to be written.</span></span>

<span data-ttu-id="68731-186">資料繫結是一個很好的範例。</span><span class="sxs-lookup"><span data-stu-id="68731-186">Data binding is a great example of this.</span></span> <span data-ttu-id="68731-187">在 jQuery 中，通常只會使用一行程式碼來取得 DOM 元素的值，或設定元素的值。</span><span class="sxs-lookup"><span data-stu-id="68731-187">In jQuery, it usually only takes one line of code to get the value of a DOM element or to set an element's value.</span></span> <span data-ttu-id="68731-188">不過，每當您需要變更元素的值時，都必須撰寫此程式碼，有時這會發生在頁面上的多個函式中。</span><span class="sxs-lookup"><span data-stu-id="68731-188">However, you have to write this code anytime you need to change the value of the element, and sometimes this will occur in multiple functions on a page.</span></span> <span data-ttu-id="68731-189">另一個常見範例是項目可見性。</span><span class="sxs-lookup"><span data-stu-id="68731-189">Another common example is element visibility.</span></span> <span data-ttu-id="68731-190">在 jQuery 中，您可能會有許多不同的位置，讓您撰寫程式碼來控制是否顯示特定元素。</span><span class="sxs-lookup"><span data-stu-id="68731-190">In jQuery, there might be many different places where you'd write code to control whether certain elements were visible.</span></span> <span data-ttu-id="68731-191">在這些情況下，使用資料繫結時，不需要撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="68731-191">In each of these cases, when using data binding, no code would need to be written.</span></span> <span data-ttu-id="68731-192">您只要將有問題的元素值或可見度系結至頁面上的*viewmodel* ，該 viewmodel 的變更就會自動反映在繫結項目中。</span><span class="sxs-lookup"><span data-stu-id="68731-192">You'd simply bind the value or visibility of the elements in question to a *viewmodel* on the page, and changes to that viewmodel would automatically be reflected in the bound elements.</span></span>

### <a name="angular-spas"></a><span data-ttu-id="68731-193">Angular SPA</span><span class="sxs-lookup"><span data-stu-id="68731-193">Angular SPAs</span></span>

<span data-ttu-id="68731-194">角度仍然是全球最受歡迎的 JavaScript 架構之一。</span><span class="sxs-lookup"><span data-stu-id="68731-194">Angular remains one of the world's most popular JavaScript frameworks.</span></span> <span data-ttu-id="68731-195">由於角度2，小組從頭開始重建架構 (使用[TypeScript](https://www.typescriptlang.org/)) 並從原始 AngularJS 名稱更名到單純的角度。</span><span class="sxs-lookup"><span data-stu-id="68731-195">Since Angular 2, the team rebuilt the framework from the ground up (using [TypeScript](https://www.typescriptlang.org/)) and rebranded from the original AngularJS name to simply Angular.</span></span> <span data-ttu-id="68731-196">過去幾年來，重新設計的角度仍然是建立單一頁面應用程式的強大架構。</span><span class="sxs-lookup"><span data-stu-id="68731-196">Now several years old, the redesigned Angular continues to be a robust framework for building Single Page Applications.</span></span>

<span data-ttu-id="68731-197">Angular 應用程式是由元件所建置。</span><span class="sxs-lookup"><span data-stu-id="68731-197">Angular applications are built from components.</span></span> <span data-ttu-id="68731-198">這些元件將 HTML 範本與特殊物件組合，並控制頁面的一部分。</span><span class="sxs-lookup"><span data-stu-id="68731-198">Components combine HTML templates with special objects and control a portion of the page.</span></span> <span data-ttu-id="68731-199">Angular 文件的簡單元件如下所示：</span><span class="sxs-lookup"><span data-stu-id="68731-199">A simple component from Angular's docs is shown here:</span></span>

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

<span data-ttu-id="68731-200">元件使用 @Component 裝飾項目函式進行定義，該函式採用關於元件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="68731-200">Components are defined using the @Component decorator function, which takes in metadata about the component.</span></span> <span data-ttu-id="68731-201">選取器屬性會識別要顯示此元件之頁面上的專案識別碼。</span><span class="sxs-lookup"><span data-stu-id="68731-201">The selector property identifies the ID of the element on the page where this component will be displayed.</span></span> <span data-ttu-id="68731-202">範本屬性是一個簡單的 HTML 範本，其中包含一個在最後一行定義、與元件名稱屬性對應的預留位置。</span><span class="sxs-lookup"><span data-stu-id="68731-202">The template property is a simple HTML template that includes a placeholder that corresponds to the component's name property, defined on the last line.</span></span>

<span data-ttu-id="68731-203">透過使用元件和範本，而不是 DOM 項目，Angular 應用程式可以在較高的抽象層次上運作，並且與僅使用 JavaScript (也稱為 "vanilla JS") 或使用 jQuery 撰寫的應用程式相比，整體程式碼更少。</span><span class="sxs-lookup"><span data-stu-id="68731-203">By working with components and templates, instead of DOM elements, Angular apps can operate at a higher level of abstraction and with less overall code than apps written using just JavaScript (also called "vanilla JS") or with jQuery.</span></span> <span data-ttu-id="68731-204">Angular 也會對您如何組織用戶端指令檔施加一些順序。</span><span class="sxs-lookup"><span data-stu-id="68731-204">Angular also imposes some order on how you organize your client-side script files.</span></span> <span data-ttu-id="68731-205">按照慣例，Angular 應用程式使用通用資料夾結構，而模組和元件指令檔則位於應用程式資料夾中。</span><span class="sxs-lookup"><span data-stu-id="68731-205">By convention, Angular apps use a common folder structure, with module and component script files located in an app folder.</span></span> <span data-ttu-id="68731-206">有關建置、部署和測試應用程式的 Angular 指令碼通常位於較高層級的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="68731-206">Angular scripts concerned with building, deploying, and testing the app are typically located in a higher-level folder.</span></span>

<span data-ttu-id="68731-207">您可以使用 CLI 開發角度應用程式。</span><span class="sxs-lookup"><span data-stu-id="68731-207">You can develop Angular apps by using a CLI.</span></span> <span data-ttu-id="68731-208">在本機開始 Angular 開發 (假設您已經安裝了 git 和 npm)，只需從 GitHub 複製一個存放庫並執行 `npm install` 和 `npm start` 即可。</span><span class="sxs-lookup"><span data-stu-id="68731-208">Getting started with Angular development locally (assuming you already have git and npm installed) consists of simply cloning a repo from GitHub and running `npm install` and `npm start`.</span></span> <span data-ttu-id="68731-209">除此之外，角度會產生自己的 CLI，它可以建立專案、新增檔案，以及協助測試、組合和部署工作。</span><span class="sxs-lookup"><span data-stu-id="68731-209">Beyond this, Angular ships its own CLI, which can create projects, add files, and assist with testing, bundling, and deployment tasks.</span></span> <span data-ttu-id="68731-210">此 CLI 易懂性使角度特別與 ASP.NET Core 相容，這也提供絕佳的 CLI 支援。</span><span class="sxs-lookup"><span data-stu-id="68731-210">This CLI friendliness makes Angular especially compatible with ASP.NET Core, which also features great CLI support.</span></span>

<span data-ttu-id="68731-211">Microsoft 開發了一個參考應用程式 [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)，其中包含一個 Angular SPA 實作。</span><span class="sxs-lookup"><span data-stu-id="68731-211">Microsoft has developed a reference application, [eShopOnContainers](https://aka.ms/MicroservicesArchitecture), which includes an Angular SPA implementation.</span></span> <span data-ttu-id="68731-212">這個應用程式包含 Angular 模組來管理線上商店的購物籃、從其目錄中載入和顯示項目，以及處理訂單建立。</span><span class="sxs-lookup"><span data-stu-id="68731-212">This app includes Angular modules to manage the online store's shopping basket, load and display items from its catalog, and handling order creation.</span></span> <span data-ttu-id="68731-213">您可以從 [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA) 檢視和下載範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="68731-213">You can view and download the sample application from [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).</span></span>

### <a name="react"></a><span data-ttu-id="68731-214">React</span><span class="sxs-lookup"><span data-stu-id="68731-214">React</span></span>

<span data-ttu-id="68731-215">與 Angular 提供完整的模型檢視控制器模式實作不同，React只關注檢視。</span><span class="sxs-lookup"><span data-stu-id="68731-215">Unlike Angular, which offers a full Model-View-Controller pattern implementation, React is only concerned with views.</span></span> <span data-ttu-id="68731-216">React 並不是一個架構，只是一個程式庫，所以若要建置 SPA 則需要利用額外的程式庫。</span><span class="sxs-lookup"><span data-stu-id="68731-216">It's not a framework, just a library, so to build a SPA you'll need to leverage additional libraries.</span></span> <span data-ttu-id="68731-217">有一些程式庫是設計用來回應產生豐富的單一頁面應用程式。</span><span class="sxs-lookup"><span data-stu-id="68731-217">There are a number of libraries that are designed to be used with React to produce rich single page applications.</span></span>

<span data-ttu-id="68731-218">React 最重要的功能之一是使用虛擬 DOM。</span><span class="sxs-lookup"><span data-stu-id="68731-218">One of React's most important features is its use of a virtual DOM.</span></span> <span data-ttu-id="68731-219">虛擬 DOM 為 React 提供了幾項優勢，包括效能 (虛擬 DOM 可最佳化實際 DOM 的哪些部分需要更新) 和可測試性 (無需使用瀏覽器測試 React 及其與虛擬 DOM 的互動)。</span><span class="sxs-lookup"><span data-stu-id="68731-219">The virtual DOM provides React with several advantages, including performance (the virtual DOM can optimize which parts of the actual DOM need to be updated) and testability (no need to have a browser to test React and its interactions with its virtual DOM).</span></span>

<span data-ttu-id="68731-220">React 在 HTML 的工作方式上也很獨特。</span><span class="sxs-lookup"><span data-stu-id="68731-220">React is also unusual in how it works with HTML.</span></span> <span data-ttu-id="68731-221">在程式碼和標記之間沒有嚴格的分隔 (或許是出現於 HTML 屬性中的 JavaScript 參考)，React 直接在 JavaScript 程式碼中新增 HTML 作為 JSX。</span><span class="sxs-lookup"><span data-stu-id="68731-221">Rather than having a strict separation between code and markup (with references to JavaScript appearing in HTML attributes perhaps), React adds HTML directly within its JavaScript code as JSX.</span></span> <span data-ttu-id="68731-222">JSX 是 HTML 的類似語法，可以編譯成純 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="68731-222">JSX is HTML-like syntax that can compile down to pure JavaScript.</span></span> <span data-ttu-id="68731-223">例如︰</span><span class="sxs-lookup"><span data-stu-id="68731-223">For example:</span></span>

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

<span data-ttu-id="68731-224">如果您已經了解 JavaScript，學習 React 應該很容易。</span><span class="sxs-lookup"><span data-stu-id="68731-224">If you already know JavaScript, learning React should be easy.</span></span> <span data-ttu-id="68731-225">與 Angular 或其他熱門的程式庫相較之下，學習曲線或涉及的特殊語法非常少。</span><span class="sxs-lookup"><span data-stu-id="68731-225">There isn't nearly as much learning curve or special syntax involved as with Angular or other popular libraries.</span></span>

<span data-ttu-id="68731-226">由於 React 不是完整的架構，所以通常需要其他程式庫來處理路由、Web API 呼叫和相依性管理等事項。</span><span class="sxs-lookup"><span data-stu-id="68731-226">Because React isn't a full framework, you'll typically want other libraries to handle things like routing, web API calls, and dependency management.</span></span> <span data-ttu-id="68731-227">好處是您可以挑選最適合的程式庫，但缺點是您需要做出所有決策，並在完成後驗證所有選定的程式庫能夠順利協作。</span><span class="sxs-lookup"><span data-stu-id="68731-227">The nice thing is, you can pick the best library for each of these, but the disadvantage is that you need to make all of these decisions and verify all of your chosen libraries work well together when you're done.</span></span> <span data-ttu-id="68731-228">如果您想要好的起步，可以使用 React Slingshot 之類可以將一組相容程式庫與 React 一起預先封裝的入門套件。</span><span class="sxs-lookup"><span data-stu-id="68731-228">If you want a good starting point, you can use a starter kit like React Slingshot, which prepackages a set of compatible libraries together with React.</span></span>

### <a name="vue"></a><span data-ttu-id="68731-229">Vue</span><span class="sxs-lookup"><span data-stu-id="68731-229">Vue</span></span>

<span data-ttu-id="68731-230">《使用者入門指南》中的 < Vue 是用來建立使用者介面的漸進式架構。</span><span class="sxs-lookup"><span data-stu-id="68731-230">From its getting started guide, "Vue is a progressive framework for building user interfaces.</span></span> <span data-ttu-id="68731-231">與其他整合型架構不同的是，Vue 是從頭開始設計，以累加方式 adoptable。</span><span class="sxs-lookup"><span data-stu-id="68731-231">Unlike other monolithic frameworks, Vue is designed from the ground up to be incrementally adoptable.</span></span> <span data-ttu-id="68731-232">核心程式庫僅著重于 view 圖層，而且很容易就能拾取並與其他程式庫或現有專案整合。</span><span class="sxs-lookup"><span data-stu-id="68731-232">The core library is focused on the view layer only, and is easy to pick up and integrate with other libraries or existing projects.</span></span> <span data-ttu-id="68731-233">另一方面，Vue 與現代化工具和支援程式庫搭配使用時，能夠提供精密的單一頁面應用程式。」</span><span class="sxs-lookup"><span data-stu-id="68731-233">On the other hand, Vue is perfectly capable of powering sophisticated Single-Page Applications when used in combination with modern tooling and supporting libraries."</span></span>

<span data-ttu-id="68731-234">開始使用 Vue 只需要在 HTML 檔案中包含其腳本即可：</span><span class="sxs-lookup"><span data-stu-id="68731-234">Getting started with Vue simply requires including its script within an HTML file:</span></span>

```html
<!-- development version, includes helpful console warnings -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

<span data-ttu-id="68731-235">加入架構之後，您就可以使用 Vue 的直接樣板化語法，以宣告的方式將資料轉譯至 DOM：</span><span class="sxs-lookup"><span data-stu-id="68731-235">With the framework added, you're then able to declaratively render data to the DOM using Vue's straightforward templating syntax:</span></span>

```html
<div id="app">
  {{ message }}
</div>
```

<span data-ttu-id="68731-236">然後新增下列腳本：</span><span class="sxs-lookup"><span data-stu-id="68731-236">and then adding the following script:</span></span>

```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

<span data-ttu-id="68731-237">這就足以呈現 "Hello Vue！"</span><span class="sxs-lookup"><span data-stu-id="68731-237">This is enough to render "Hello Vue!"</span></span> <span data-ttu-id="68731-238">在頁面上。</span><span class="sxs-lookup"><span data-stu-id="68731-238">on the page.</span></span> <span data-ttu-id="68731-239">不過要注意的是，Vue 不只是將訊息轉譯成 div 一次。</span><span class="sxs-lookup"><span data-stu-id="68731-239">Note, however, that Vue isn't simply rendering the message to the div once.</span></span> <span data-ttu-id="68731-240">它支援資料系結和動態更新，因此如果變更的值 `message` ，中的值 `<div>` 會立即更新以反映它。</span><span class="sxs-lookup"><span data-stu-id="68731-240">It supports databinding and dynamic updates such that if the value of `message` changes, the value in the `<div>` is immediately updated to reflect it.</span></span>

<span data-ttu-id="68731-241">當然，這只會將 Vue 的功能呈現在表面上。</span><span class="sxs-lookup"><span data-stu-id="68731-241">Of course, this only scratches the surface of what Vue is capable of.</span></span> <span data-ttu-id="68731-242">在過去幾年來，有很多熱門的經驗，而且有大型的社區。</span><span class="sxs-lookup"><span data-stu-id="68731-242">It's gained a great deal of popularity in the last several years and has a large community.</span></span> <span data-ttu-id="68731-243">有一份[龐大且持續成長的支援元件和程式庫清單](https://github.com/vuejs/awesome-vue#redux)，可搭配 Vue 來進行擴充。</span><span class="sxs-lookup"><span data-stu-id="68731-243">There's a [huge and growing list of supporting components and libraries](https://github.com/vuejs/awesome-vue#redux) that work with Vue to extend it as well.</span></span> <span data-ttu-id="68731-244">如果您想要在 web 應用程式中新增用戶端行為，或考慮建立完整的 SPA，Vue 就值得進行調查。</span><span class="sxs-lookup"><span data-stu-id="68731-244">If you're looking to add client-side behavior to your web application or considering building a full SPA, Vue is worth investigating.</span></span>

### <a name="choosing-a-spa-framework"></a><span data-ttu-id="68731-245">選擇 SPA 架構</span><span class="sxs-lookup"><span data-stu-id="68731-245">Choosing a SPA Framework</span></span>

<span data-ttu-id="68731-246">在考量哪種 JavaScript 架構最適合支援您的 SPA 時，請記住下列考量：</span><span class="sxs-lookup"><span data-stu-id="68731-246">When considering which JavaScript framework will work best to support your SPA, keep in mind the following considerations:</span></span>

- <span data-ttu-id="68731-247">您的小組是否熟悉該架構和其相依性 (在某些情況下包括 TypeScript)？</span><span class="sxs-lookup"><span data-stu-id="68731-247">Is your team familiar with the framework and its dependencies (including TypeScript in some cases)?</span></span>

- <span data-ttu-id="68731-248">該架構是否專斷，以及您是否同意其預設的運作方式？</span><span class="sxs-lookup"><span data-stu-id="68731-248">How opinionated is the framework, and do you agree with its default way of doing things?</span></span>

- <span data-ttu-id="68731-249">該架構 (或附屬程式庫) 是否包含您應用程式所需的全部功能？</span><span class="sxs-lookup"><span data-stu-id="68731-249">Does it (or a companion library) include all of the features your app requires?</span></span>

- <span data-ttu-id="68731-250">是否妥善記載？</span><span class="sxs-lookup"><span data-stu-id="68731-250">Is it well documented?</span></span>

- <span data-ttu-id="68731-251">在社群中有多活躍？</span><span class="sxs-lookup"><span data-stu-id="68731-251">How active is its community?</span></span> <span data-ttu-id="68731-252">新專案是以它建立的嗎？</span><span class="sxs-lookup"><span data-stu-id="68731-252">Are new projects being built with it?</span></span>

- <span data-ttu-id="68731-253">其核心小組有多活躍？</span><span class="sxs-lookup"><span data-stu-id="68731-253">How active is its core team?</span></span> <span data-ttu-id="68731-254">問題是否得到解決、新版本是否定期發出？</span><span class="sxs-lookup"><span data-stu-id="68731-254">Are issues being resolved and new versions shipped regularly?</span></span>

<span data-ttu-id="68731-255">JavaScript 架構持續以驚人的速度改良。</span><span class="sxs-lookup"><span data-stu-id="68731-255">JavaScript frameworks continue to evolve with breakneck speed.</span></span> <span data-ttu-id="68731-256">使用上面列出的考量，來協助減輕選擇架構時，可能造成日後後悔對其依賴的風險。</span><span class="sxs-lookup"><span data-stu-id="68731-256">Use the considerations listed above to help mitigate the risk of choosing a framework you'll later regret being dependent upon.</span></span> <span data-ttu-id="68731-257">如果您特別注重風險，請考慮提供商業支援及/或 由大型企業開發的架構。</span><span class="sxs-lookup"><span data-stu-id="68731-257">If you're particularly risk-averse, consider a framework that offers commercial support and/or is being developed by a large enterprise.</span></span>

> ### <a name="references--client-web-technologies"></a><span data-ttu-id="68731-258">參考資料 – 用戶端 Web 技術</span><span class="sxs-lookup"><span data-stu-id="68731-258">References – Client Web Technologies</span></span>
>
> - <span data-ttu-id="68731-259">**HTML 和 CSS**</span><span class="sxs-lookup"><span data-stu-id="68731-259">**HTML and CSS**</span></span>  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - <span data-ttu-id="68731-260">**Sass 與 LESS 比較**</span><span class="sxs-lookup"><span data-stu-id="68731-260">**Sass vs. LESS**</span></span>  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - <span data-ttu-id="68731-261">**以 LESS、Sass 和 Font Awesome 設定樣式**</span><span class="sxs-lookup"><span data-stu-id="68731-261">**Styling ASP.NET Core Apps with LESS, Sass, and Font Awesome**</span></span>  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - <span data-ttu-id="68731-262">**ASP.NET Core 中的用戶端開發**</span><span class="sxs-lookup"><span data-stu-id="68731-262">**Client-Side Development in ASP.NET Core**</span></span>  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - <span data-ttu-id="68731-263">**jQuery**</span><span class="sxs-lookup"><span data-stu-id="68731-263">**jQuery**</span></span>  
> <https://jquery.com/>
> - <span data-ttu-id="68731-264">**jQuery vs AngularJS**</span><span class="sxs-lookup"><span data-stu-id="68731-264">**jQuery vs AngularJS**</span></span>  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - <span data-ttu-id="68731-265">**Angular**</span><span class="sxs-lookup"><span data-stu-id="68731-265">**Angular**</span></span>  
> <https://angular.io/>
> - <span data-ttu-id="68731-266">**React**</span><span class="sxs-lookup"><span data-stu-id="68731-266">**React**</span></span>  
> <https://reactjs.org/>
> - <span data-ttu-id="68731-267">**Vue**</span><span class="sxs-lookup"><span data-stu-id="68731-267">**Vue**</span></span>  
> <https://vuejs.org/>
> - <span data-ttu-id="68731-268">**角度與反應 vs Vue：要在2020中選擇哪一種架構**
> <https://www.codeinwp.com/blog/angular-vs-vue-vs-react/></span><span class="sxs-lookup"><span data-stu-id="68731-268">**Angular vs React vs Vue: Which Framework to Choose in 2020**
<https://www.codeinwp.com/blog/angular-vs-vue-vs-react/></span></span>
> - <span data-ttu-id="68731-269">**2020中前端開發的最佳 JavaScript 架構**</span><span class="sxs-lookup"><span data-stu-id="68731-269">**The Top JavaScript Frameworks for Front-End Development in 2020**</span></span>  
> <https://www.freecodecamp.org/news/complete-guide-for-front-end-developers-javascript-frameworks-2019/>

>[!div class="step-by-step"]
><span data-ttu-id="68731-270">[上一個](common-web-application-architectures.md) 
>[下一步](develop-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="68731-270">[Previous](common-web-application-architectures.md)
[Next](develop-asp-net-core-mvc-apps.md)</span></span>
