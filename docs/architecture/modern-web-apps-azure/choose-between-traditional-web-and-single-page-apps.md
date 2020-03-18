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
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a><span data-ttu-id="f5667-103">在傳統 Web 應用程式和單頁應用程式 (SPA) 之間作選擇</span><span class="sxs-lookup"><span data-stu-id="f5667-103">Choose Between Traditional Web Apps and Single Page Apps (SPAs)</span></span>

> <span data-ttu-id="f5667-104">「Atwood 定律：任何可以用 JavaScript 撰寫的應用程式，最後都將以 JavaScript 撰寫。」</span><span class="sxs-lookup"><span data-stu-id="f5667-104">"Atwood's Law: Any application that can be written in JavaScript, will eventually be written in JavaScript."</span></span>  
> <span data-ttu-id="f5667-105">_\-傑夫·Atwood_</span><span class="sxs-lookup"><span data-stu-id="f5667-105">_\- Jeff Atwood_</span></span>

<span data-ttu-id="f5667-106">現在有兩種建置 Web 應用程式的通用方法：在伺服器上執行大多數應用程式邏輯的傳統 Web 應用程式，以及執行大多數使用者介面邏輯的單頁應用程式 (SPA)，主要使用 Web API 與 Web 伺服器通訊。</span><span class="sxs-lookup"><span data-stu-id="f5667-106">There are two general approaches to building web applications today: traditional web applications that perform most of the application logic on the server, and single page applications (SPAs) that perform most of the user interface logic in a web browser, communicating with the web server primarily using web APIs.</span></span> <span data-ttu-id="f5667-107">也可以採用混合方法，最簡單的方法是在大型傳統 Web 應用程式中託管一個或多個類似 SPA 的豐富子應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5667-107">A hybrid approach is also possible, the simplest being host one or more rich SPA-like subapplications within a larger traditional web application.</span></span>

<span data-ttu-id="f5667-108">在：</span><span class="sxs-lookup"><span data-stu-id="f5667-108">Use traditional web applications when:</span></span>

- <span data-ttu-id="f5667-109">應用程式用戶端的需求簡單或甚至是唯讀。</span><span class="sxs-lookup"><span data-stu-id="f5667-109">Your application's client-side requirements are simple or even read-only.</span></span>

- <span data-ttu-id="f5667-110">應用程式需要在不支援 JavaScript 的瀏覽器中運作。</span><span class="sxs-lookup"><span data-stu-id="f5667-110">Your application needs to function in browsers without JavaScript support.</span></span>

- <span data-ttu-id="f5667-111">您的小組不熟悉 JavaScript 或 TypeScript 開發技術。</span><span class="sxs-lookup"><span data-stu-id="f5667-111">Your team is unfamiliar with JavaScript or TypeScript development techniques.</span></span>

<span data-ttu-id="f5667-112">在：</span><span class="sxs-lookup"><span data-stu-id="f5667-112">Use a SPA when:</span></span>

- <span data-ttu-id="f5667-113">應用程式必須公開具有許多功能的豐富使用者介面。</span><span class="sxs-lookup"><span data-stu-id="f5667-113">Your application must expose a rich user interface with many features.</span></span>

- <span data-ttu-id="f5667-114">您的小組熟悉 JavaScript 及/或 TypeScript 開發。</span><span class="sxs-lookup"><span data-stu-id="f5667-114">Your team is familiar with JavaScript and/or TypeScript development.</span></span>

- <span data-ttu-id="f5667-115">您的應用程式必須已針對其他 (內部或公開) 用戶端公開 API。</span><span class="sxs-lookup"><span data-stu-id="f5667-115">Your application must already expose an API for other (internal or public) clients.</span></span>

<span data-ttu-id="f5667-116">此外，SPA 架構需要更多的架構和安全性專業知識。</span><span class="sxs-lookup"><span data-stu-id="f5667-116">Additionally, SPA frameworks require greater architectural and security expertise.</span></span> <span data-ttu-id="f5667-117">由於頻繁的更新及新的架構，SPA 架構會經歷比傳統 Web 應用程式更大的變換。</span><span class="sxs-lookup"><span data-stu-id="f5667-117">They experience greater churn due to frequent updates and new frameworks than traditional web applications.</span></span> <span data-ttu-id="f5667-118">配置自動生成和部署過程以及利用容器等部署選項在 SPA 應用程式中可能比傳統 Web 應用程式更加困難。</span><span class="sxs-lookup"><span data-stu-id="f5667-118">Configuring automated build and deployment processes and utilizing deployment options like containers may be more difficult with SPA applications than traditional web apps.</span></span>

<span data-ttu-id="f5667-119">必須權衡 SPA 方法對使用者體驗的改進，並權衡這些注意事項。</span><span class="sxs-lookup"><span data-stu-id="f5667-119">Improvements in user experience made possible by the SPA approach must be weighed against these considerations.</span></span>

## <a name="blazor"></a><span data-ttu-id="f5667-120">Blazor</span><span class="sxs-lookup"><span data-stu-id="f5667-120">Blazor</span></span>

<span data-ttu-id="f5667-121">ASP.NET Core 3.0 推出了新的模型，用以建置豐富的互動式可組合 UI，該模型稱為 Blazor。</span><span class="sxs-lookup"><span data-stu-id="f5667-121">ASP.NET Core 3.0 introduces a new model for building rich, interactive, and composable UI called Blazor.</span></span> <span data-ttu-id="f5667-122">Blazor 伺服器端允許開發人員在伺服器上使用 Razor 構建 UI，並將此代碼傳遞到瀏覽器並使用[WebAssembly](https://webassembly.org/)執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="f5667-122">Blazor server-side allows developers to build UI with Razor on the server and for this code to be delivered to the browser and executed client-side using [WebAssembly](https://webassembly.org/).</span></span> <span data-ttu-id="f5667-123">Blazor 伺服器端現在可用於ASP.NET酷睿 3.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="f5667-123">Blazor server-side is available now with ASP.NET Core 3.0 or later.</span></span> <span data-ttu-id="f5667-124">Blazor 用戶端應在 2020 年推出。</span><span class="sxs-lookup"><span data-stu-id="f5667-124">Blazor client-side should be available in 2020.</span></span>

<span data-ttu-id="f5667-125">Blazor 提供了一個新的第三個選項，在評估是構建純伺服器呈現的 Web 應用程式還是 SPA 時需要考慮。</span><span class="sxs-lookup"><span data-stu-id="f5667-125">Blazor provides a new, third option to consider when evaluating whether to build a purely server-rendered web application or a SPA.</span></span> <span data-ttu-id="f5667-126">您可以使用 Blazor 構建豐富的類似 SPA 的用戶端行為，而無需進行重大的 JavaScript 開發。</span><span class="sxs-lookup"><span data-stu-id="f5667-126">You can build rich, SPA-like client-side behaviors using Blazor, without the need for a significant JavaScript development.</span></span> <span data-ttu-id="f5667-127">Blazor 應用程式可以調用 API 來請求資料或執行伺服器端操作。</span><span class="sxs-lookup"><span data-stu-id="f5667-127">Blazor applications can call APIs to request data or perform server-side operations.</span></span>

<span data-ttu-id="f5667-128">請考慮在以下時間使用 Blazor 構建 Web 應用程式：</span><span class="sxs-lookup"><span data-stu-id="f5667-128">Consider building your web application with Blazor when:</span></span>

- <span data-ttu-id="f5667-129">您的應用程式必須公開豐富的使用者介面</span><span class="sxs-lookup"><span data-stu-id="f5667-129">Your application must expose a rich user interface</span></span>

- <span data-ttu-id="f5667-130">與 JavaScript 或 TypeScript 開發相比，您的團隊對 .NET 開發更滿意</span><span class="sxs-lookup"><span data-stu-id="f5667-130">Your team is more comfortable with .NET development than JavaScript or TypeScript development</span></span>

<span data-ttu-id="f5667-131">如需 Blazor 的詳細資訊，請參閱[開始使用 Blazor](https://blazor.net/docs/get-started.html)。</span><span class="sxs-lookup"><span data-stu-id="f5667-131">For more information about Blazor, see [Get started with Blazor](https://blazor.net/docs/get-started.html).</span></span>

## <a name="when-to-choose-traditional-web-apps"></a><span data-ttu-id="f5667-132">選擇傳統 Web 應用程式的時機</span><span class="sxs-lookup"><span data-stu-id="f5667-132">When to choose traditional web apps</span></span>

<span data-ttu-id="f5667-133">以下將更詳盡說明前述挑選傳統 Web 應用程式的理由。</span><span class="sxs-lookup"><span data-stu-id="f5667-133">The following is a more detailed explanation of the previously stated reasons for picking traditional web applications.</span></span>

<span data-ttu-id="f5667-134">**您的應用程式具有簡單且可能是唯讀的用戶端需求**</span><span class="sxs-lookup"><span data-stu-id="f5667-134">**Your application has simple, possibly read-only, client-side requirements**</span></span>

<span data-ttu-id="f5667-135">許多 Web 應用程式主要以唯讀方式供絕大多數使用者使用。</span><span class="sxs-lookup"><span data-stu-id="f5667-135">Many web applications are primarily consumed in a read-only fashion by the vast majority of their users.</span></span> <span data-ttu-id="f5667-136">唯讀 (或主要為讀取) 的應用程式往往比維護和操作大量狀態的應用程式簡單許多。</span><span class="sxs-lookup"><span data-stu-id="f5667-136">Read-only (or read-mostly) applications tend to be much simpler than those that maintain and manipulate a great deal of state.</span></span> <span data-ttu-id="f5667-137">例如，搜尋引擎可能包含文字方塊的單一進入點，和用於顯示搜尋結果的第二個頁面。</span><span class="sxs-lookup"><span data-stu-id="f5667-137">For example, a search engine might consist of a single entry point with a textbox and a second page for displaying search results.</span></span> <span data-ttu-id="f5667-138">匿名使用者可以輕鬆發出要求，且幾乎不需要用戶端邏輯。</span><span class="sxs-lookup"><span data-stu-id="f5667-138">Anonymous users can easily make requests, and there is little need for client-side logic.</span></span> <span data-ttu-id="f5667-139">同樣地，部落格或內容管理系統的公開應用程式，通常主要由幾乎沒有用戶端行為的內容所組成。</span><span class="sxs-lookup"><span data-stu-id="f5667-139">Likewise, a blog or content management system's public-facing application usually consists mainly of content with little client-side behavior.</span></span> <span data-ttu-id="f5667-140">此類應用程式很容易構建為傳統的基於伺服器的 Web 應用程式，這些應用程式在 Web 服務器上執行邏輯並呈現要在瀏覽器中顯示的 HTML。</span><span class="sxs-lookup"><span data-stu-id="f5667-140">Such applications are easily built as traditional server-based web applications, which perform logic on the web server and render HTML to be displayed in the browser.</span></span> <span data-ttu-id="f5667-141">網站的每個獨特頁面都有自己的 URL，可透過搜尋引擎加上書籤並編製索引 (此為預設，不需另外將此新增為應用程式的個別功能)，在此情況下也是明顯的優勢。</span><span class="sxs-lookup"><span data-stu-id="f5667-141">The fact that each unique page of the site has its own URL that can be bookmarked and indexed by search engines (by default, without having to add this as a separate feature of the application) is also a clear benefit in such scenarios.</span></span>

<span data-ttu-id="f5667-142">**您的應用程式需要在沒有 JavaScript 支援的瀏覽器中運行**</span><span class="sxs-lookup"><span data-stu-id="f5667-142">**Your application needs to function in browsers without JavaScript support**</span></span>

<span data-ttu-id="f5667-143">需要在有限或不支援 JavaScript 之瀏覽器中運作的 Web 應用程式，應該使用傳統 Web 應用程式工作流程來撰寫 (或至少能夠改為使用這種行為)。</span><span class="sxs-lookup"><span data-stu-id="f5667-143">Web applications that need to function in browsers with limited or no JavaScript support should be written using traditional web app workflows (or at least be able to fall back to such behavior).</span></span> <span data-ttu-id="f5667-144">SPA 需要用戶端 JavaScript 才能運作；如果不可用，則 SPA 就不是好選擇。</span><span class="sxs-lookup"><span data-stu-id="f5667-144">SPAs require client-side JavaScript in order to function; if it's not available, SPAs are not a good choice.</span></span>

<span data-ttu-id="f5667-145">**您的團隊不熟悉 JavaScript 或 TypeScript 開發技術**</span><span class="sxs-lookup"><span data-stu-id="f5667-145">**Your team is unfamiliar with JavaScript or TypeScript development techniques**</span></span>

<span data-ttu-id="f5667-146">如果您的小組不熟悉 JavaScript 或 TypeScript 但熟悉伺服器端 Web 應用程式開發，那麼比起 SPA 應用程式，他們可能可以更快交付傳統 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5667-146">If your team is unfamiliar with JavaScript or TypeScript, but is familiar with server-side web application development, then they will probably be able to deliver a traditional web app more quickly than a SPA.</span></span> <span data-ttu-id="f5667-147">除非目標是學習編程 SPA 或是需要 SPA 提供的使用者體驗，否則對於已經熟悉建置傳統 Web 應用程式的小組而言，傳統 Web 應用程式是更具生產力的選擇。</span><span class="sxs-lookup"><span data-stu-id="f5667-147">Unless learning to program SPAs is a goal, or the user experience afforded by a SPA is required, traditional web apps are a more productive choice for teams who are already familiar with building them.</span></span>

## <a name="when-to-choose-spas"></a><span data-ttu-id="f5667-148">選擇 SPA 的時機</span><span class="sxs-lookup"><span data-stu-id="f5667-148">When to choose SPAs</span></span>

<span data-ttu-id="f5667-149">以下將詳細說明應何時為您的 Web 應用程式選擇單頁應用程式開發樣式。</span><span class="sxs-lookup"><span data-stu-id="f5667-149">The following is a more detailed explanation of when to choose a Single Page Applications style of development for your web app.</span></span>

<span data-ttu-id="f5667-150">**應用程式必須公開具有許多功能的豐富使用者介面**</span><span class="sxs-lookup"><span data-stu-id="f5667-150">**Your application must expose a rich user interface with many features**</span></span>

<span data-ttu-id="f5667-151">SPAs 可以支援豐富的用戶端功能，且當使用者採取動作或在應用程式各區域間巡覽時，也不需重新載入頁面。</span><span class="sxs-lookup"><span data-stu-id="f5667-151">SPAs can support rich client-side functionality that doesn't require reloading the page as users take actions or navigate between areas of the app.</span></span> <span data-ttu-id="f5667-152">SPA 可以更快速載入、在背景擷取資料、對個別使用者的動作回應更快，因為重新載入完整頁面的情況很少。</span><span class="sxs-lookup"><span data-stu-id="f5667-152">SPAs can load more quickly, fetching data in the background, and individual user actions are more responsive since full page reloads are rare.</span></span> <span data-ttu-id="f5667-153">SPA 可支援增量更新，不需使用者按一下按鈕來提交表單即可儲存部分完成的表單或文件。</span><span class="sxs-lookup"><span data-stu-id="f5667-153">SPAs can support incremental updates, saving partially completed forms or documents without the user having to click a button to submit a form.</span></span> <span data-ttu-id="f5667-154">SPA 比傳統應用程式更容易支援豐富的用戶端行為，例如拖放操作。</span><span class="sxs-lookup"><span data-stu-id="f5667-154">SPAs can support rich client-side behaviors, such as drag-and-drop, much more readily than traditional applications.</span></span> <span data-ttu-id="f5667-155">SPA 可以設計為以離線模式執行；對用戶端模型進行的更新在其重新建立連線之後，最終會同步回伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5667-155">SPAs can be designed to run in a disconnected mode, making updates to a client-side model that are eventually synchronized back to the server once a connection is re-established.</span></span> <span data-ttu-id="f5667-156">如果應用的要求包含超出典型 HTML 表單提供的豐富功能，請選擇 SPA 樣式的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5667-156">Choose a SPA-style application if your app's requirements include rich functionality that goes beyond what typical HTML forms offer.</span></span>

<span data-ttu-id="f5667-157">通常，SpA 需要實現內置到傳統 Web 應用中的功能，例如在網址列中顯示反映當前操作的有意義的 URL（以及允許使用者對此 URL 進行書簽或深層連結以返回到它）。</span><span class="sxs-lookup"><span data-stu-id="f5667-157">Frequently, SPAs need to implement features that are built in to traditional web apps, such as displaying a meaningful URL in the address bar reflecting the current operation (and allowing users to bookmark or deep link to this URL to return to it).</span></span> <span data-ttu-id="f5667-158">SPA 也應允許使用者使用瀏覽器的 [上一頁] 和 [下一頁] 按鈕，且不產生意外的結果。</span><span class="sxs-lookup"><span data-stu-id="f5667-158">SPAs also should allow users to use the browser's back and forward buttons with results that won't surprise them.</span></span>

<span data-ttu-id="f5667-159">**您的團隊熟悉 JavaScript 和/或 TypeScript 開發**</span><span class="sxs-lookup"><span data-stu-id="f5667-159">**Your team is familiar with JavaScript and/or TypeScript development**</span></span>

<span data-ttu-id="f5667-160">撰寫 SPA 需要熟悉 JavaScript 及/或 TypeScript，以及用戶端程式設計技術與程式庫。</span><span class="sxs-lookup"><span data-stu-id="f5667-160">Writing SPAs requires familiarity with JavaScript and/or TypeScript and client-side programming techniques and libraries.</span></span> <span data-ttu-id="f5667-161">您的小組應能夠使用 Angular 等 SPA 架構來撰寫現代化 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="f5667-161">Your team should be competent in writing modern JavaScript using a SPA framework like Angular.</span></span>

> ### <a name="references--spa-frameworks"></a><span data-ttu-id="f5667-162">參考資料 – SPA 架構</span><span class="sxs-lookup"><span data-stu-id="f5667-162">References – SPA Frameworks</span></span>
>
> - <span data-ttu-id="f5667-163">**Angular**</span><span class="sxs-lookup"><span data-stu-id="f5667-163">**Angular**</span></span>  
>   <https://angular.io>
> - <span data-ttu-id="f5667-164">**反應**
>   <https://reactjs.org/></span><span class="sxs-lookup"><span data-stu-id="f5667-164">**React**
<https://reactjs.org/></span></span>
> - <span data-ttu-id="f5667-165">**JavaScript 架構的比較**</span><span class="sxs-lookup"><span data-stu-id="f5667-165">**Comparison of JavaScript Frameworks**</span></span>  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

<span data-ttu-id="f5667-166">**您的應用程式必須已公開其他（內部或公共）用戶端的 API**</span><span class="sxs-lookup"><span data-stu-id="f5667-166">**Your application must already expose an API for other (internal or public) clients**</span></span>

<span data-ttu-id="f5667-167">如果您已經支援其他用戶端使用的 Web API，則建立利用這些 API 的 SPA 實作會較容易，不用重現伺服器端格式中的邏輯。</span><span class="sxs-lookup"><span data-stu-id="f5667-167">If you're already supporting a web API for use by other clients, it may require less effort to create a SPA implementation that leverages these APIs rather than reproducing the logic in server-side form.</span></span> <span data-ttu-id="f5667-168">當使用者與應用程式互動時，SPA 大量使用 Web API 來查詢及更新資料。</span><span class="sxs-lookup"><span data-stu-id="f5667-168">SPAs make extensive use of web APIs to query and update data as users interact with the application.</span></span>

## <a name="when-to-choose-blazor"></a><span data-ttu-id="f5667-169">何時選擇布拉佐爾</span><span class="sxs-lookup"><span data-stu-id="f5667-169">When to choose Blazor</span></span>

<span data-ttu-id="f5667-170">以下是何時為 Web 應用選擇 Blazor 的更詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="f5667-170">The following is a more detailed explanation of when to choose Blazor for your web app.</span></span>

<span data-ttu-id="f5667-171">**您的應用程式必須公開豐富的使用者介面**</span><span class="sxs-lookup"><span data-stu-id="f5667-171">**Your application must expose a rich user interface**</span></span>

<span data-ttu-id="f5667-172">與基於 JavaScript 的 SPA 一樣，Blazor 應用程式可以支援豐富的用戶端行為，而無需重新載入頁面。</span><span class="sxs-lookup"><span data-stu-id="f5667-172">Like JavaScript-based SPAs, Blazor applications can support rich client behavior without page reloads.</span></span> <span data-ttu-id="f5667-173">這些應用程式對使用者回應更快，僅獲取回應給定使用者交互所需的資料（或 HTML）。</span><span class="sxs-lookup"><span data-stu-id="f5667-173">These applications are more responsive to users, fetching only the data (or HTML) required to respond to a given user interaction.</span></span> <span data-ttu-id="f5667-174">設計得當，伺服器端 Blazor 應用可以配置為作為用戶端 Blazor 應用運行，一旦支援此功能，只需進行最少的更改即可運行。</span><span class="sxs-lookup"><span data-stu-id="f5667-174">Designed properly, server-side Blazor apps can be configured to run as client-side Blazor apps with minimal changes once this feature is supported.</span></span>

<span data-ttu-id="f5667-175">**與 JavaScript 或 TypeScript 開發相比，您的團隊對 .NET 開發更滿意**</span><span class="sxs-lookup"><span data-stu-id="f5667-175">**Your team is more comfortable with .NET development than JavaScript or TypeScript development**</span></span>

<span data-ttu-id="f5667-176">與 JavaScript 或 TypeScript 等用戶端語言相比，許多開發人員使用 .NET 和 Razor 工作效率更高。</span><span class="sxs-lookup"><span data-stu-id="f5667-176">Many developers are more productive with .NET and Razor than with client-side languages like JavaScript or TypeScript.</span></span> <span data-ttu-id="f5667-177">由於應用程式伺服器端已經使用 .NET 開發，因此使用 Blazor 可確保團隊中的每個 .NET 開發人員都能瞭解並可能構建應用程式前端的行為。</span><span class="sxs-lookup"><span data-stu-id="f5667-177">Since the server side of the application is already being developed with .NET, using Blazor ensures every .NET developer on the team can understand and potentially build the behavior of the front end of the application.</span></span>

## <a name="decision-table"></a><span data-ttu-id="f5667-178">決策表</span><span class="sxs-lookup"><span data-stu-id="f5667-178">Decision table</span></span>

<span data-ttu-id="f5667-179">下面的決策表總結了在傳統 Web 應用程式、SPA 或 Blazor 應用之間進行選擇時需要考慮的一些基本因素。</span><span class="sxs-lookup"><span data-stu-id="f5667-179">The following decision table summarizes some of the basic factors to consider when choosing between a traditional web application, a SPA, or a Blazor app.</span></span>

| <span data-ttu-id="f5667-180">**因數**</span><span class="sxs-lookup"><span data-stu-id="f5667-180">**Factor**</span></span>                                           | <span data-ttu-id="f5667-181">**傳統 Web 應用程式**</span><span class="sxs-lookup"><span data-stu-id="f5667-181">**Traditional Web App**</span></span> | <span data-ttu-id="f5667-182">**單頁應用程式**</span><span class="sxs-lookup"><span data-stu-id="f5667-182">**Single Page Application**</span></span> | <span data-ttu-id="f5667-183">**布拉佐爾應用程式**</span><span class="sxs-lookup"><span data-stu-id="f5667-183">**Blazor App**</span></span>  |
| ---------------------------------------------------- | ----------------------- | --------------------------- | --------------- |
| <span data-ttu-id="f5667-184">小組必須熟悉 JavaScript/TypeScript</span><span class="sxs-lookup"><span data-stu-id="f5667-184">Required Team Familiarity with JavaScript/TypeScript</span></span> | <span data-ttu-id="f5667-185">**最小**</span><span class="sxs-lookup"><span data-stu-id="f5667-185">**Minimal**</span></span>             | <span data-ttu-id="f5667-186">**必要**</span><span class="sxs-lookup"><span data-stu-id="f5667-186">**Required**</span></span>                | <span data-ttu-id="f5667-187">**最小**</span><span class="sxs-lookup"><span data-stu-id="f5667-187">**Minimal**</span></span>     |
| <span data-ttu-id="f5667-188">支援無指令碼的瀏覽器</span><span class="sxs-lookup"><span data-stu-id="f5667-188">Support Browsers without Scripting</span></span>                   | <span data-ttu-id="f5667-189">**支援**</span><span class="sxs-lookup"><span data-stu-id="f5667-189">**Supported**</span></span>           | <span data-ttu-id="f5667-190">**不支援**</span><span class="sxs-lookup"><span data-stu-id="f5667-190">**Not Supported**</span></span>           | <span data-ttu-id="f5667-191">**支援**</span><span class="sxs-lookup"><span data-stu-id="f5667-191">**Supported**</span></span>   |
| <span data-ttu-id="f5667-192">最少的用戶端應用程式行為</span><span class="sxs-lookup"><span data-stu-id="f5667-192">Minimal Client-Side Application Behavior</span></span>             | <span data-ttu-id="f5667-193">**適用**</span><span class="sxs-lookup"><span data-stu-id="f5667-193">**Well-Suited**</span></span>         | <span data-ttu-id="f5667-194">**大材小用**</span><span class="sxs-lookup"><span data-stu-id="f5667-194">**Overkill**</span></span>                | <span data-ttu-id="f5667-195">**可行**</span><span class="sxs-lookup"><span data-stu-id="f5667-195">**Viable**</span></span>      |
| <span data-ttu-id="f5667-196">內容豐富且複雜的使用者介面需求</span><span class="sxs-lookup"><span data-stu-id="f5667-196">Rich, Complex User Interface Requirements</span></span>            | <span data-ttu-id="f5667-197">**有限**</span><span class="sxs-lookup"><span data-stu-id="f5667-197">**Limited**</span></span>             | <span data-ttu-id="f5667-198">**適用**</span><span class="sxs-lookup"><span data-stu-id="f5667-198">**Well-Suited**</span></span>             | <span data-ttu-id="f5667-199">**適用**</span><span class="sxs-lookup"><span data-stu-id="f5667-199">**Well-Suited**</span></span> |

>[!div class="step-by-step"]
><span data-ttu-id="f5667-200">[上一個](modern-web-applications-characteristics.md)
>[下一個](architectural-principles.md)</span><span class="sxs-lookup"><span data-stu-id="f5667-200">[Previous](modern-web-applications-characteristics.md)
[Next](architectural-principles.md)</span></span>
