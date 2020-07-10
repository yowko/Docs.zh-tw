---
title: 在傳統 Web 應用程式和單頁應用程式之間作選擇
description: 了解建置 Web 應用程式時，如何在傳統 Web 應用程式和單頁應用程式 (SPA) 之間作選擇。
author: ardalis
ms.author: wiwagn
no-loc:
- Blazor
- WebAssembly
ms.date: 12/04/2019
ms.openlocfilehash: 4fe889fe86d96a5b2ffa5bd879d2ec1801a3cf20
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174363"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a><span data-ttu-id="0fb0c-103">在傳統 Web 應用程式和單頁應用程式 (SPA) 之間作選擇</span><span class="sxs-lookup"><span data-stu-id="0fb0c-103">Choose Between Traditional Web Apps and Single Page Apps (SPAs)</span></span>

> <span data-ttu-id="0fb0c-104">「Atwood 定律：任何可以用 JavaScript 撰寫的應用程式，最後都將以 JavaScript 撰寫。」</span><span class="sxs-lookup"><span data-stu-id="0fb0c-104">"Atwood's Law: Any application that can be written in JavaScript, will eventually be written in JavaScript."</span></span>  
> <span data-ttu-id="0fb0c-105">_\-Jeff Atwood_</span><span class="sxs-lookup"><span data-stu-id="0fb0c-105">_\- Jeff Atwood_</span></span>

<span data-ttu-id="0fb0c-106">現在有兩種建置 Web 應用程式的通用方法：在伺服器上執行大多數應用程式邏輯的傳統 Web 應用程式，以及執行大多數使用者介面邏輯的單頁應用程式 (SPA)，主要使用 Web API 與 Web 伺服器通訊。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-106">There are two general approaches to building web applications today: traditional web applications that perform most of the application logic on the server, and single page applications (SPAs) that perform most of the user interface logic in a web browser, communicating with the web server primarily using web APIs.</span></span> <span data-ttu-id="0fb0c-107">混合式方法也是可行的，最簡單的方式是在較大型的傳統 web 應用程式中裝載一或多個類似 SPA 的 subapplications。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-107">A hybrid approach is also possible, the simplest being host one or more rich SPA-like subapplications within a larger traditional web application.</span></span>

<span data-ttu-id="0fb0c-108">使用傳統 web 應用程式的時機：</span><span class="sxs-lookup"><span data-stu-id="0fb0c-108">Use traditional web applications when:</span></span>

- <span data-ttu-id="0fb0c-109">應用程式用戶端的需求簡單或甚至是唯讀。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-109">Your application's client-side requirements are simple or even read-only.</span></span>

- <span data-ttu-id="0fb0c-110">應用程式需要在不支援 JavaScript 的瀏覽器中運作。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-110">Your application needs to function in browsers without JavaScript support.</span></span>

- <span data-ttu-id="0fb0c-111">您的小組不熟悉 JavaScript 或 TypeScript 開發技術。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-111">Your team is unfamiliar with JavaScript or TypeScript development techniques.</span></span>

<span data-ttu-id="0fb0c-112">使用 SPA 的時機：</span><span class="sxs-lookup"><span data-stu-id="0fb0c-112">Use a SPA when:</span></span>

- <span data-ttu-id="0fb0c-113">應用程式必須公開具有許多功能的豐富使用者介面。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-113">Your application must expose a rich user interface with many features.</span></span>

- <span data-ttu-id="0fb0c-114">您的小組熟悉 JavaScript 及/或 TypeScript 開發。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-114">Your team is familiar with JavaScript and/or TypeScript development.</span></span>

- <span data-ttu-id="0fb0c-115">您的應用程式必須已針對其他 (內部或公開) 用戶端公開 API。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-115">Your application must already expose an API for other (internal or public) clients.</span></span>

<span data-ttu-id="0fb0c-116">此外，SPA 架構需要更多的架構和安全性專業知識。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-116">Additionally, SPA frameworks require greater architectural and security expertise.</span></span> <span data-ttu-id="0fb0c-117">由於頻繁的更新及新的架構，SPA 架構會經歷比傳統 Web 應用程式更大的變換。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-117">They experience greater churn due to frequent updates and new frameworks than traditional web applications.</span></span> <span data-ttu-id="0fb0c-118">與傳統 web 應用程式相比，設定自動化的組建和部署程式，以及使用容器之類的部署選項，可能會比較棘手的 SPA。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-118">Configuring automated build and deployment processes and utilizing deployment options like containers may be more difficult with SPA applications than traditional web apps.</span></span>

<span data-ttu-id="0fb0c-119">SPA 方法的使用者經驗改善，必須根據這些考慮來進行權衡。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-119">Improvements in user experience made possible by the SPA approach must be weighed against these considerations.</span></span>

## Blazor

<span data-ttu-id="0fb0c-120">ASP.NET Core 3.0 引進了新的模型，可讓您建立名為的豐富、互動式且可組合的 UI Blazor 。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-120">ASP.NET Core 3.0 introduces a new model for building rich, interactive, and composable UI called Blazor.</span></span> Blazor<span data-ttu-id="0fb0c-121">伺服器端可以讓開發人員在伺服器上使用 c # 和 Razor 建立 UI，並使用持續的 SignalR 連接，以互動方式即時連線至瀏覽器的 UI。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-121"> server-side allows developers to build UI with C# and Razor on the server and for the UI to be interactively connected to the browser in real-time using a persistent SignalR connection.</span></span>

Blazor<span data-ttu-id="0fb0c-122">WebAssembly引進應用程式的另一個選項 Blazor ，讓他們能夠使用在瀏覽器中執行 WebAssembly 。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-122"> WebAssembly introduces another option for Blazor apps, allowing them to run in the browser using WebAssembly.</span></span> <span data-ttu-id="0fb0c-123">因為它是在上執行的實際 .NET WebAssembly ，所以您可以從應用程式的伺服器端部分重複使用程式碼和程式庫。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-123">Because it's real .NET running on WebAssembly, you can re-use code and libraries from server-side parts of your application.</span></span>

Blazor<span data-ttu-id="0fb0c-124">提供新的第三個選項，可在評估是否要建立單純伺服器呈現的 web 應用程式或 SPA 時考慮。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-124"> provides a new, third option to consider when evaluating whether to build a purely server-rendered web application or a SPA.</span></span> <span data-ttu-id="0fb0c-125">您可以使用建立豐富、SPA 類似的用戶端行為 Blazor ，而不需要進行重要的 JavaScript 開發。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-125">You can build rich, SPA-like client-side behaviors using Blazor, without the need for a significant JavaScript development.</span></span> Blazor<span data-ttu-id="0fb0c-126">應用程式可以呼叫 Api 來要求資料或執行伺服器端作業。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-126"> applications can call APIs to request data or perform server-side operations.</span></span>

<span data-ttu-id="0fb0c-127">在下列情況中，請考慮建立您的 web 應用程式 Blazor ：</span><span class="sxs-lookup"><span data-stu-id="0fb0c-127">Consider building your web application with Blazor when:</span></span>

- <span data-ttu-id="0fb0c-128">您的應用程式必須公開豐富的使用者介面</span><span class="sxs-lookup"><span data-stu-id="0fb0c-128">Your application must expose a rich user interface</span></span>

- <span data-ttu-id="0fb0c-129">您的小組比 JavaScript 或 TypeScript 開發更熟悉 .NET 開發</span><span class="sxs-lookup"><span data-stu-id="0fb0c-129">Your team is more comfortable with .NET development than JavaScript or TypeScript development</span></span>

<span data-ttu-id="0fb0c-130">如需的詳細資訊 Blazor ，請參閱[開始 Blazor 使用](https://blazor.net/docs/get-started.html)。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-130">For more information about Blazor, see [Get started with Blazor](https://blazor.net/docs/get-started.html).</span></span>

## <a name="when-to-choose-traditional-web-apps"></a><span data-ttu-id="0fb0c-131">選擇傳統 Web 應用程式的時機</span><span class="sxs-lookup"><span data-stu-id="0fb0c-131">When to choose traditional web apps</span></span>

<span data-ttu-id="0fb0c-132">以下將更詳盡說明前述挑選傳統 Web 應用程式的理由。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-132">The following is a more detailed explanation of the previously stated reasons for picking traditional web applications.</span></span>

<span data-ttu-id="0fb0c-133">**您的應用程式具有簡單且可能是唯讀的用戶端需求**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-133">**Your application has simple, possibly read-only, client-side requirements**</span></span>

<span data-ttu-id="0fb0c-134">許多 Web 應用程式主要以唯讀方式供絕大多數使用者使用。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-134">Many web applications are primarily consumed in a read-only fashion by the vast majority of their users.</span></span> <span data-ttu-id="0fb0c-135">唯讀 (或主要為讀取) 的應用程式往往比維護和操作大量狀態的應用程式簡單許多。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-135">Read-only (or read-mostly) applications tend to be much simpler than those that maintain and manipulate a great deal of state.</span></span> <span data-ttu-id="0fb0c-136">例如，搜尋引擎可能包含文字方塊的單一進入點，和用於顯示搜尋結果的第二個頁面。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-136">For example, a search engine might consist of a single entry point with a textbox and a second page for displaying search results.</span></span> <span data-ttu-id="0fb0c-137">匿名使用者可以輕鬆發出要求，且幾乎不需要用戶端邏輯。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-137">Anonymous users can easily make requests, and there is little need for client-side logic.</span></span> <span data-ttu-id="0fb0c-138">同樣地，部落格或內容管理系統的公開應用程式，通常主要由幾乎沒有用戶端行為的內容所組成。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-138">Likewise, a blog or content management system's public-facing application usually consists mainly of content with little client-side behavior.</span></span> <span data-ttu-id="0fb0c-139">這類應用程式很容易建立為傳統的伺服器型 web 應用程式，它會在 web 伺服器上執行邏輯，並呈現 HTML 以顯示在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-139">Such applications are easily built as traditional server-based web applications, which perform logic on the web server and render HTML to be displayed in the browser.</span></span> <span data-ttu-id="0fb0c-140">網站的每個獨特頁面都有自己的 URL，可透過搜尋引擎加上書籤並編製索引 (此為預設，不需另外將此新增為應用程式的個別功能)，在此情況下也是明顯的優勢。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-140">The fact that each unique page of the site has its own URL that can be bookmarked and indexed by search engines (by default, without having to add this as a separate feature of the application) is also a clear benefit in such scenarios.</span></span>

<span data-ttu-id="0fb0c-141">**您的應用程式需要在不支援 JavaScript 的瀏覽器中運作**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-141">**Your application needs to function in browsers without JavaScript support**</span></span>

<span data-ttu-id="0fb0c-142">需要在有限或不支援 JavaScript 之瀏覽器中運作的 Web 應用程式，應該使用傳統 Web 應用程式工作流程來撰寫 (或至少能夠改為使用這種行為)。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-142">Web applications that need to function in browsers with limited or no JavaScript support should be written using traditional web app workflows (or at least be able to fall back to such behavior).</span></span> <span data-ttu-id="0fb0c-143">SPA 需要用戶端 JavaScript 才能運作；如果不可用，則 SPA 就不是好選擇。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-143">SPAs require client-side JavaScript in order to function; if it's not available, SPAs are not a good choice.</span></span>

<span data-ttu-id="0fb0c-144">**您的小組不熟悉 JavaScript 或 TypeScript 開發技術**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-144">**Your team is unfamiliar with JavaScript or TypeScript development techniques**</span></span>

<span data-ttu-id="0fb0c-145">如果您的小組不熟悉 JavaScript 或 TypeScript 但熟悉伺服器端 Web 應用程式開發，那麼比起 SPA 應用程式，他們可能可以更快交付傳統 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-145">If your team is unfamiliar with JavaScript or TypeScript, but is familiar with server-side web application development, then they will probably be able to deliver a traditional web app more quickly than a SPA.</span></span> <span data-ttu-id="0fb0c-146">除非目標是學習編程 SPA 或是需要 SPA 提供的使用者體驗，否則對於已經熟悉建置傳統 Web 應用程式的小組而言，傳統 Web 應用程式是更具生產力的選擇。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-146">Unless learning to program SPAs is a goal, or the user experience afforded by a SPA is required, traditional web apps are a more productive choice for teams who are already familiar with building them.</span></span>

## <a name="when-to-choose-spas"></a><span data-ttu-id="0fb0c-147">選擇 SPA 的時機</span><span class="sxs-lookup"><span data-stu-id="0fb0c-147">When to choose SPAs</span></span>

<span data-ttu-id="0fb0c-148">以下將詳細說明應何時為您的 Web 應用程式選擇單頁應用程式開發樣式。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-148">The following is a more detailed explanation of when to choose a Single Page Applications style of development for your web app.</span></span>

<span data-ttu-id="0fb0c-149">**應用程式必須公開具有許多功能的豐富使用者介面**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-149">**Your application must expose a rich user interface with many features**</span></span>

<span data-ttu-id="0fb0c-150">SPAs 可以支援豐富的用戶端功能，且當使用者採取動作或在應用程式各區域間巡覽時，也不需重新載入頁面。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-150">SPAs can support rich client-side functionality that doesn't require reloading the page as users take actions or navigate between areas of the app.</span></span> <span data-ttu-id="0fb0c-151">SPA 可以更快速載入、在背景擷取資料、對個別使用者的動作回應更快，因為重新載入完整頁面的情況很少。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-151">SPAs can load more quickly, fetching data in the background, and individual user actions are more responsive since full page reloads are rare.</span></span> <span data-ttu-id="0fb0c-152">SPA 可支援增量更新，不需使用者按一下按鈕來提交表單即可儲存部分完成的表單或文件。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-152">SPAs can support incremental updates, saving partially completed forms or documents without the user having to click a button to submit a form.</span></span> <span data-ttu-id="0fb0c-153">SPA 比傳統應用程式更容易支援豐富的用戶端行為，例如拖放操作。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-153">SPAs can support rich client-side behaviors, such as drag-and-drop, much more readily than traditional applications.</span></span> <span data-ttu-id="0fb0c-154">SPA 可以設計為以離線模式執行；對用戶端模型進行的更新在其重新建立連線之後，最終會同步回伺服器。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-154">SPAs can be designed to run in a disconnected mode, making updates to a client-side model that are eventually synchronized back to the server once a connection is re-established.</span></span> <span data-ttu-id="0fb0c-155">如果您的應用程式需求包含超越一般 HTML 表單所提供的豐富功能，請選擇 SPA 樣式的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-155">Choose a SPA-style application if your app's requirements include rich functionality that goes beyond what typical HTML forms offer.</span></span>

<span data-ttu-id="0fb0c-156">Spa 通常需要實作為傳統 web 應用程式的內建功能，例如在反映目前作業 (的網址列中顯示有意義的 URL，並允許使用者將此 URL 加入書簽或深層連結，以回到) 。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-156">Frequently, SPAs need to implement features that are built in to traditional web apps, such as displaying a meaningful URL in the address bar reflecting the current operation (and allowing users to bookmark or deep link to this URL to return to it).</span></span> <span data-ttu-id="0fb0c-157">SPA 也應允許使用者使用瀏覽器的 [上一頁] 和 [下一頁] 按鈕，且不產生意外的結果。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-157">SPAs also should allow users to use the browser's back and forward buttons with results that won't surprise them.</span></span>

<span data-ttu-id="0fb0c-158">**您的小組熟悉 JavaScript 及/或 TypeScript 開發**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-158">**Your team is familiar with JavaScript and/or TypeScript development**</span></span>

<span data-ttu-id="0fb0c-159">撰寫 SPA 需要熟悉 JavaScript 及/或 TypeScript，以及用戶端程式設計技術與程式庫。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-159">Writing SPAs requires familiarity with JavaScript and/or TypeScript and client-side programming techniques and libraries.</span></span> <span data-ttu-id="0fb0c-160">您的小組應能夠使用 Angular 等 SPA 架構來撰寫現代化 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-160">Your team should be competent in writing modern JavaScript using a SPA framework like Angular.</span></span>

> ### <a name="references--spa-frameworks"></a><span data-ttu-id="0fb0c-161">參考資料 – SPA 架構</span><span class="sxs-lookup"><span data-stu-id="0fb0c-161">References – SPA Frameworks</span></span>
>
> - <span data-ttu-id="0fb0c-162">**Angular**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-162">**Angular**</span></span>  
>   <https://angular.io>
> - <span data-ttu-id="0fb0c-163">**反應**
>   <https://reactjs.org/></span><span class="sxs-lookup"><span data-stu-id="0fb0c-163">**React**
<https://reactjs.org/></span></span>
> - <span data-ttu-id="0fb0c-164">**JavaScript 架構的比較**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-164">**Comparison of JavaScript Frameworks**</span></span>  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

<span data-ttu-id="0fb0c-165">**您的應用程式必須已針對其他 (內部或公用) 用戶端公開 API**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-165">**Your application must already expose an API for other (internal or public) clients**</span></span>

<span data-ttu-id="0fb0c-166">如果您已經支援其他用戶端使用的 Web API，則建立利用這些 API 的 SPA 實作會較容易，不用重現伺服器端格式中的邏輯。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-166">If you're already supporting a web API for use by other clients, it may require less effort to create a SPA implementation that leverages these APIs rather than reproducing the logic in server-side form.</span></span> <span data-ttu-id="0fb0c-167">當使用者與應用程式互動時，SPA 大量使用 Web API 來查詢及更新資料。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-167">SPAs make extensive use of web APIs to query and update data as users interact with the application.</span></span>

## <a name="when-to-choose-blazor"></a><span data-ttu-id="0fb0c-168">選擇時機Blazor</span><span class="sxs-lookup"><span data-stu-id="0fb0c-168">When to choose Blazor</span></span>

<span data-ttu-id="0fb0c-169">以下是為 Blazor 您的 web 應用程式選擇時機的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-169">The following is a more detailed explanation of when to choose Blazor for your web app.</span></span>

<span data-ttu-id="0fb0c-170">**您的應用程式必須公開豐富的使用者介面**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-170">**Your application must expose a rich user interface**</span></span>

<span data-ttu-id="0fb0c-171">如同以 JavaScript 為基礎的 Spa， Blazor 應用程式可以在沒有頁面重載的情況下支援豐富的用戶端行為。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-171">Like JavaScript-based SPAs, Blazor applications can support rich client behavior without page reloads.</span></span> <span data-ttu-id="0fb0c-172">這些應用程式對使用者的回應速度更快，只會取得回應指定使用者互動所需的資料 (或 HTML) 。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-172">These applications are more responsive to users, fetching only the data (or HTML) required to respond to a given user interaction.</span></span> <span data-ttu-id="0fb0c-173">伺服器端 Blazor 應用程式的設計正確，可設定為以用戶端應用程式的身分執行，只要 Blazor 支援這項功能即可進行最少的變更。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-173">Designed properly, server-side Blazor apps can be configured to run as client-side Blazor apps with minimal changes once this feature is supported.</span></span>

<span data-ttu-id="0fb0c-174">**您的小組比 JavaScript 或 TypeScript 開發更熟悉 .NET 開發**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-174">**Your team is more comfortable with .NET development than JavaScript or TypeScript development**</span></span>

<span data-ttu-id="0fb0c-175">許多開發人員使用 .NET 和 Razor 比使用 JavaScript 或 TypeScript 之類的用戶端語言更具生產力。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-175">Many developers are more productive with .NET and Razor than with client-side languages like JavaScript or TypeScript.</span></span> <span data-ttu-id="0fb0c-176">由於應用程式的伺服器端已使用 .NET 進行開發，因此使用 Blazor 可確保小組中的每個 .net 開發人員都能瞭解並可能建立應用程式前端的行為。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-176">Since the server side of the application is already being developed with .NET, using Blazor ensures every .NET developer on the team can understand and potentially build the behavior of the front end of the application.</span></span>

## <a name="decision-table"></a><span data-ttu-id="0fb0c-177">決策表</span><span class="sxs-lookup"><span data-stu-id="0fb0c-177">Decision table</span></span>

<span data-ttu-id="0fb0c-178">下列決策表摘要說明在傳統 web 應用程式、SPA 或應用程式之間進行選擇時，所要考慮的一些基本因素 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="0fb0c-178">The following decision table summarizes some of the basic factors to consider when choosing between a traditional web application, a SPA, or a Blazor app.</span></span>

| <span data-ttu-id="0fb0c-179">**因素**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-179">**Factor**</span></span>                                           | <span data-ttu-id="0fb0c-180">**傳統 Web 應用程式**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-180">**Traditional Web App**</span></span> | <span data-ttu-id="0fb0c-181">**單一頁面應用程式**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-181">**Single Page Application**</span></span> | <span data-ttu-id="0fb0c-182">**Blazor相關**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-182">**Blazor App**</span></span>  |
| ---------------------------------------------------- | ----------------------- | --------------------------- | --------------- |
| <span data-ttu-id="0fb0c-183">小組必須熟悉 JavaScript/TypeScript</span><span class="sxs-lookup"><span data-stu-id="0fb0c-183">Required Team Familiarity with JavaScript/TypeScript</span></span> | <span data-ttu-id="0fb0c-184">**最低限度**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-184">**Minimal**</span></span>             | <span data-ttu-id="0fb0c-185">**必要**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-185">**Required**</span></span>                | <span data-ttu-id="0fb0c-186">**最低限度**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-186">**Minimal**</span></span>     |
| <span data-ttu-id="0fb0c-187">支援無指令碼的瀏覽器</span><span class="sxs-lookup"><span data-stu-id="0fb0c-187">Support Browsers without Scripting</span></span>                   | <span data-ttu-id="0fb0c-188">**支援**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-188">**Supported**</span></span>           | <span data-ttu-id="0fb0c-189">**不受支援**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-189">**Not Supported**</span></span>           | <span data-ttu-id="0fb0c-190">**支援**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-190">**Supported**</span></span>   |
| <span data-ttu-id="0fb0c-191">最少的用戶端應用程式行為</span><span class="sxs-lookup"><span data-stu-id="0fb0c-191">Minimal Client-Side Application Behavior</span></span>             | <span data-ttu-id="0fb0c-192">**適用**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-192">**Well-Suited**</span></span>         | <span data-ttu-id="0fb0c-193">**大材小用**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-193">**Overkill**</span></span>                | <span data-ttu-id="0fb0c-194">**有效**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-194">**Viable**</span></span>      |
| <span data-ttu-id="0fb0c-195">內容豐富且複雜的使用者介面需求</span><span class="sxs-lookup"><span data-stu-id="0fb0c-195">Rich, Complex User Interface Requirements</span></span>            | <span data-ttu-id="0fb0c-196">**局限性**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-196">**Limited**</span></span>             | <span data-ttu-id="0fb0c-197">**適用**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-197">**Well-Suited**</span></span>             | <span data-ttu-id="0fb0c-198">**適用**</span><span class="sxs-lookup"><span data-stu-id="0fb0c-198">**Well-Suited**</span></span> |

>[!div class="step-by-step"]
><span data-ttu-id="0fb0c-199">[上一個](modern-web-applications-characteristics.md) 
>[下一步](architectural-principles.md)</span><span class="sxs-lookup"><span data-stu-id="0fb0c-199">[Previous](modern-web-applications-characteristics.md)
[Next](architectural-principles.md)</span></span>
