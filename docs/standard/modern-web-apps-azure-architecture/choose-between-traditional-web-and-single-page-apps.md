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
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a><span data-ttu-id="be7f1-103">傳統 Web 應用程式和單一頁面應用程式 (SPAs) 之間選擇</span><span class="sxs-lookup"><span data-stu-id="be7f1-103">Choose Between Traditional Web Apps and Single Page Apps (SPAs)</span></span>

> <span data-ttu-id="be7f1-104">「 Atwood 的法律： 任何應用程式都可以撰寫在 JavaScript 中，最後將以 JavaScript 撰寫。 」</span><span class="sxs-lookup"><span data-stu-id="be7f1-104">"Atwood's Law: Any application that can be written in JavaScript, will eventually be written in JavaScript."</span></span>  
> <span data-ttu-id="be7f1-105">_\-Jeff Atwood_</span><span class="sxs-lookup"><span data-stu-id="be7f1-105">_\- Jeff Atwood_</span></span>

## <a name="summary"></a><span data-ttu-id="be7f1-106">總結</span><span class="sxs-lookup"><span data-stu-id="be7f1-106">Summary</span></span>

<span data-ttu-id="be7f1-107">有兩種一般的方法，來建置 web 應用程式現在： server 和網頁瀏覽器中執行大部分的使用者介面邏輯的單一頁面應用程式 (SPAs) 執行應用程式邏輯的大部分的傳統 web 應用程式與主要使用 web 應用程式開發介面的 web 伺服器通訊。</span><span class="sxs-lookup"><span data-stu-id="be7f1-107">There are two general approaches to building web applications today: traditional web applications that perform most of the application logic on the server, and single page applications (SPAs) that perform most of the user interface logic in a web browser, communicating with the web server primarily using web APIs.</span></span> <span data-ttu-id="be7f1-108">混合式方法，您也可以，最簡單的裝載一或多個豐富 SPA 類似子應用程式在較大的傳統 web 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="be7f1-108">A hybrid approach is also possible, the simplest being host one or more rich SPA-like sub-applications within a larger traditional web application.</span></span>

<span data-ttu-id="be7f1-109">您應該使用傳統 web 應用程式時：</span><span class="sxs-lookup"><span data-stu-id="be7f1-109">You should use traditional web applications when:</span></span>

-   <span data-ttu-id="be7f1-110">您的應用程式用戶端需求是簡單或甚至是唯讀。</span><span class="sxs-lookup"><span data-stu-id="be7f1-110">Your application's client-side requirements are simple or even read-only.</span></span>

-   <span data-ttu-id="be7f1-111">您的應用程式中不支援 JavaScript 瀏覽器運作所需。</span><span class="sxs-lookup"><span data-stu-id="be7f1-111">Your application needs to function in browsers without JavaScript support.</span></span>

-   <span data-ttu-id="be7f1-112">您的小組不熟悉使用 JavaScript 或 TypeScript 的開發技巧。</span><span class="sxs-lookup"><span data-stu-id="be7f1-112">Your team is unfamiliar with JavaScript or TypeScript development techniques.</span></span>

<span data-ttu-id="be7f1-113">您應該使用 SPA 時：</span><span class="sxs-lookup"><span data-stu-id="be7f1-113">You should use a SPA when:</span></span>

-   <span data-ttu-id="be7f1-114">您的應用程式必須公開透過許多功能豐富的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="be7f1-114">Your application must expose a rich user interface with many features.</span></span>

-   <span data-ttu-id="be7f1-115">您的團隊已熟悉 JavaScript 和/或 TypeScript 開發。</span><span class="sxs-lookup"><span data-stu-id="be7f1-115">Your team is familiar with JavaScript and/or TypeScript development.</span></span>

-   <span data-ttu-id="be7f1-116">您的應用程式必須已公開其他 （內部或公用） 的用戶端應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="be7f1-116">Your application must already expose an API for other (internal or public) clients.</span></span>

<span data-ttu-id="be7f1-117">此外，SPA 架構需要大於架構和安全性的專業知識。</span><span class="sxs-lookup"><span data-stu-id="be7f1-117">Additionally, SPA frameworks require greater architectural and security expertise.</span></span> <span data-ttu-id="be7f1-118">在發生因為頻繁的更新及新的架構更高的變換比傳統 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="be7f1-118">They experience greater churn due to frequent updates and new frameworks than traditional web applications.</span></span> <span data-ttu-id="be7f1-119">設定自動化的建置和部署程序，以及使用類似的容器部署選項是使用 SPA 應用程式比傳統 web 應用程式更困難。</span><span class="sxs-lookup"><span data-stu-id="be7f1-119">Configuring automated build and deployment processes and utilizing deployment options like containers are more difficult with SPA applications than traditional web apps.</span></span>

<span data-ttu-id="be7f1-120">改善使用者體驗即可進行 SPA 模型必須權衡這些考量。</span><span class="sxs-lookup"><span data-stu-id="be7f1-120">Improvements in user experience made possible by SPA model must be weighed against these considerations.</span></span>

## <a name="when-to-choose-traditional-web-apps"></a><span data-ttu-id="be7f1-121">選擇傳統 web 應用程式的時機</span><span class="sxs-lookup"><span data-stu-id="be7f1-121">When to choose traditional web apps</span></span>

<span data-ttu-id="be7f1-122">以下是更詳細的說明的先前所述原因挑選傳統 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="be7f1-122">The following is a more detailed explanation of the previously-stated reasons for picking traditional web applications.</span></span>

<span data-ttu-id="be7f1-123">**您的應用程式有簡單、 可能是唯讀、 用戶端需求**</span><span class="sxs-lookup"><span data-stu-id="be7f1-123">**Your application has simple, possibly read-only, client-side requirements**</span></span>

<span data-ttu-id="be7f1-124">許多 web 應用程式主要被供以唯讀方式大部分的使用者。</span><span class="sxs-lookup"><span data-stu-id="be7f1-124">Many web applications are primarily consumed in a read-only fashion by the vast majority of their users.</span></span> <span data-ttu-id="be7f1-125">唯讀 （或主要為讀取） 的應用程式通常比維護和操作狀態的極簡單許多。</span><span class="sxs-lookup"><span data-stu-id="be7f1-125">Read-only (or read-mostly) applications tend to be much simpler than those that maintain and manipulate a great deal of state.</span></span> <span data-ttu-id="be7f1-126">例如，搜尋引擎可能包含文字方塊與用於顯示搜尋結果的第二個頁面的單一進入點。</span><span class="sxs-lookup"><span data-stu-id="be7f1-126">For example, a search engine might consist of a single entry point with a textbox and a second page for displaying search results.</span></span> <span data-ttu-id="be7f1-127">匿名使用者可以輕鬆地進行要求，而且幾乎不需要用戶端邏輯。</span><span class="sxs-lookup"><span data-stu-id="be7f1-127">Anonymous users can easily make requests, and there is little need for client-side logic.</span></span> <span data-ttu-id="be7f1-128">同樣地，部落格或內容管理系統的公開應用程式通常包含主要是個很少用戶端行為的內容。</span><span class="sxs-lookup"><span data-stu-id="be7f1-128">Likewise, a blog or content management system's public-facing application usually consists mainly of content with little client-side behavior.</span></span> <span data-ttu-id="be7f1-129">這類應用程式輕鬆地建立以伺服器為基礎的傳統 web 應用程式 web 伺服器上執行的邏輯，並呈現在瀏覽器中顯示的 HTML。</span><span class="sxs-lookup"><span data-stu-id="be7f1-129">Such applications are easily built as traditional server-based web applications which perform logic on the web server and render HTML to be displayed in the browser.</span></span> <span data-ttu-id="be7f1-130">站台的每個唯一頁面都有自己的 URL，可以設為書籤，並以搜尋引擎 （依預設，而不必個別功能的應用程式加入此） 編製索引的事實也是明顯的好處，在這種情況。</span><span class="sxs-lookup"><span data-stu-id="be7f1-130">The fact that each unique page of the site has its own URL that can be bookmarked and indexed by search engines (by default, without having to add this as a separate feature of the application) is also a clear benefit in such scenarios.</span></span>

<span data-ttu-id="be7f1-131">**您的應用程式中不支援 JavaScript 瀏覽器運作所需**</span><span class="sxs-lookup"><span data-stu-id="be7f1-131">**Your application needs to function in browsers without JavaScript support**</span></span>

<span data-ttu-id="be7f1-132">需要在有限或不支援 JavaScript 的瀏覽器中運作的 web 應用程式應該使用傳統 web 應用程式工作流程中寫入 （或至少能夠改為使用這類行為）。</span><span class="sxs-lookup"><span data-stu-id="be7f1-132">Web applications that need to function in browsers with limited or no JavaScript support should be written using traditional web app workflows (or at least be able to fall back to such behavior).</span></span> <span data-ttu-id="be7f1-133">SPAs 需要用戶端 JavaScript，才能運作。如果無法使用，SPAs 不是很不錯的選擇。</span><span class="sxs-lookup"><span data-stu-id="be7f1-133">SPAs require client-side JavaScript in order to function; if it's not available, SPAs are not a good choice.</span></span>

<span data-ttu-id="be7f1-134">**您的小組不熟悉與 JavaScript 或 TypeScript 開發技術**</span><span class="sxs-lookup"><span data-stu-id="be7f1-134">**Your team is unfamiliar with JavaScript or TypeScript development techniques**</span></span>

<span data-ttu-id="be7f1-135">如果您的小組不熟悉與 JavaScript 或 TypeScript，但熟悉伺服器端 web 應用程式開發，然後它們可能會比 SPA 更快速地提供傳統 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="be7f1-135">If your team is unfamiliar with JavaScript or TypeScript, but is familiar with server-side web application development, then they will probably be able to deliver a traditional web app more quickly than a SPA.</span></span> <span data-ttu-id="be7f1-136">學習程式 SPAs 目標，或 SPA 所提供的使用者體驗有必要，除非傳統 web 應用程式是已熟悉建置它們的小組是更具生產力的選擇。</span><span class="sxs-lookup"><span data-stu-id="be7f1-136">Unless learning to program SPAs is a goal, or the user experience afforded by a SPA is required, traditional web apps are a more productive choice for teams who are already familiar with building them.</span></span>

## <a name="when-to-choose-spas"></a><span data-ttu-id="be7f1-137">當選擇 SPAs</span><span class="sxs-lookup"><span data-stu-id="be7f1-137">When to choose SPAs</span></span>

<span data-ttu-id="be7f1-138">以下是更詳細的說明何時選擇開發 web 應用程式的單一頁面應用程式樣式。</span><span class="sxs-lookup"><span data-stu-id="be7f1-138">The following is a more detailed explanation of when to choose a Single Page Applications style of development for your web app.</span></span>

<span data-ttu-id="be7f1-139">**您的應用程式必須公開透過許多功能豐富的使用者介面**</span><span class="sxs-lookup"><span data-stu-id="be7f1-139">**Your application must expose a rich user interface with many features**</span></span>

<span data-ttu-id="be7f1-140">SPAs 可以支援豐富的用戶端功能，不需要重新載入該頁面，當使用者採取動作或應用程式的區域之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="be7f1-140">SPAs can support rich client-side functionality that doesn't require reloading the page as users take actions or navigate between areas of the app.</span></span> <span data-ttu-id="be7f1-141">SPAs 可以擷取資料，在背景中，更快速地載入並個別使用者的動作是更能有效回應，因為完整頁面重新載入的情況很少見。</span><span class="sxs-lookup"><span data-stu-id="be7f1-141">SPAs can load more quickly, fetching data in the background, and individual user actions are more responsive since full page reloads are rare.</span></span> <span data-ttu-id="be7f1-142">SPAs 可以支援累加式更新，使用者不必按滑鼠按鈕送出表單不儲存部分完成的表單或文件。</span><span class="sxs-lookup"><span data-stu-id="be7f1-142">SPAs can support incremental updates, saving partially completed forms or documents without the user having to click a button to submit a form.</span></span> <span data-ttu-id="be7f1-143">SPAs 可以支援豐富的用戶端行為，例如拖放，隨時會比傳統應用程式。</span><span class="sxs-lookup"><span data-stu-id="be7f1-143">SPAs can support rich client-side behaviors, such as drag-and-drop, much more readily than traditional applications.</span></span> <span data-ttu-id="be7f1-144">SPAs 為了在中斷連線的模式中，進行更新至用戶端模型最終同步處理至伺服器之後重新建立連接時執行。</span><span class="sxs-lookup"><span data-stu-id="be7f1-144">SPAs can be designed to run in a disconnected mode, making updates to a client-side model that are eventually synchronized back to the server once a connection is re-established.</span></span> <span data-ttu-id="be7f1-145">如果您的應用程式需求包含超過一般的 HTML 表單所提供的豐富功能，您應該選擇 SPA 樣式的應用程式。</span><span class="sxs-lookup"><span data-stu-id="be7f1-145">You should choose a SPA style application if your app's requirements include rich functionality that goes beyond what typical HTML forms offer.</span></span>

<span data-ttu-id="be7f1-146">請注意，SPAs 經常需要實作功能所內建於傳統 web 應用程式，例如在位址列中反映目前的作業 （允許使用者書籤或深層連結至此 url 回到） 顯示的有意義的 URL。</span><span class="sxs-lookup"><span data-stu-id="be7f1-146">Note that frequently SPAs need to implement features that are built-in to traditional web apps, such as displaying a meaningful URL in the address bar reflecting the current operation (and allowing users to bookmark or deep link to this URL to return to it).</span></span> <span data-ttu-id="be7f1-147">SPAs 也應該允許使用者使用瀏覽器的上一頁及下一頁按鈕將不會意外的結果。</span><span class="sxs-lookup"><span data-stu-id="be7f1-147">SPAs also should allow users to use the browser's back and forward buttons with results that won't surprise them.</span></span>

<span data-ttu-id="be7f1-148">**您的團隊已熟悉 JavaScript 和/或 TypeScript 程式開發**</span><span class="sxs-lookup"><span data-stu-id="be7f1-148">**Your team is familiar with JavaScript and/or TypeScript development**</span></span>

<span data-ttu-id="be7f1-149">撰寫 SPAs 需要熟悉 JavaScript 和/或 TypeScript 和用戶端程式設計技術和程式庫。</span><span class="sxs-lookup"><span data-stu-id="be7f1-149">Writing SPAs requires familiarity with JavaScript and/or TypeScript and client-side programming techniques and libraries.</span></span> <span data-ttu-id="be7f1-150">您的小組應該是令人撰寫使用 SPA Angular 現代 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="be7f1-150">Your team should be competent in writing modern JavaScript using a SPA framework like Angular.</span></span>

> ### <a name="references--spa-frameworks"></a><span data-ttu-id="be7f1-151">參考 – SPA 架構</span><span class="sxs-lookup"><span data-stu-id="be7f1-151">References – SPA Frameworks</span></span>
> - <span data-ttu-id="be7f1-152">**AngularJS**</span><span class="sxs-lookup"><span data-stu-id="be7f1-152">**AngularJS**</span></span>  
> <span data-ttu-id="be7f1-153"><https://angularjs.org/></span><span class="sxs-lookup"><span data-stu-id="be7f1-153"><https://angularjs.org/></span></span>
> - <span data-ttu-id="be7f1-154">**4 受歡迎的 JavaScript 架構的比較**</span><span class="sxs-lookup"><span data-stu-id="be7f1-154">**Comparison of 4 Popular JavaScript Frameworks**</span></span>  
> <span data-ttu-id="be7f1-155"><https://www.developereconomics.com/feature-comparison-of-4-popular-js-mv-frameworks></span><span class="sxs-lookup"><span data-stu-id="be7f1-155"><https://www.developereconomics.com/feature-comparison-of-4-popular-js-mv-frameworks></span></span>

<span data-ttu-id="be7f1-156">**您的應用程式必須已公開其他 （內部或公用） 的用戶端應用程式開發介面**</span><span class="sxs-lookup"><span data-stu-id="be7f1-156">**Your application must already expose an API for other (internal or public) clients**</span></span>

<span data-ttu-id="be7f1-157">如果您已經支援的 web API 以供其他用戶端，它可能需要較輕鬆，若要建立一個 SPA 實作，可以利用這些 Api，而不是重現伺服器端格式中的邏輯。</span><span class="sxs-lookup"><span data-stu-id="be7f1-157">If you're already supporting a web API for use by other clients, it may require less effort to create a SPA implementation that leverages these APIs rather than reproducing the logic in server-side form.</span></span> <span data-ttu-id="be7f1-158">SPAs 對查詢及更新的資料進行廣泛使用的 web 應用程式開發介面，當使用者與應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="be7f1-158">SPAs make extensive use of web APIs to query and update data as users interact with the application.</span></span>

## <a name="decision-table--traditional-web-or-spa"></a><span data-ttu-id="be7f1-159">決策表 – 傳統 Web 或 SPA</span><span class="sxs-lookup"><span data-stu-id="be7f1-159">Decision table – Traditional Web or SPA</span></span>

<span data-ttu-id="be7f1-160">下列的決策表摘要列出一些基本 SPA 傳統 web 應用程式之間選擇時要考慮的因素。</span><span class="sxs-lookup"><span data-stu-id="be7f1-160">The following decision table summarizes some of the basic factors to consider when choosing between a traditional web application and a SPA.</span></span>

  | <span data-ttu-id="be7f1-161">**因素**</span><span class="sxs-lookup"><span data-stu-id="be7f1-161">**Factor**</span></span> | <span data-ttu-id="be7f1-162">**傳統 Web 應用程式**</span><span class="sxs-lookup"><span data-stu-id="be7f1-162">**Traditional Web App**</span></span> | <span data-ttu-id="be7f1-163">**單一頁面應用程式**</span><span class="sxs-lookup"><span data-stu-id="be7f1-163">**Single Page Application**</span></span> |
  |---|---|---|
  | <span data-ttu-id="be7f1-164">必要的小組熟悉 JavaScript/TypeScript</span><span class="sxs-lookup"><span data-stu-id="be7f1-164">Required Team Familiarity with JavaScript/TypeScript</span></span> | <span data-ttu-id="be7f1-165">**最小**</span><span class="sxs-lookup"><span data-stu-id="be7f1-165">**Minimal**</span></span> | <span data-ttu-id="be7f1-166">**必要**</span><span class="sxs-lookup"><span data-stu-id="be7f1-166">**Required**</span></span> |
  | <span data-ttu-id="be7f1-167">支援的瀏覽器不編寫指令碼</span><span class="sxs-lookup"><span data-stu-id="be7f1-167">Support Browsers without Scripting</span></span> | <span data-ttu-id="be7f1-168">**支援**</span><span class="sxs-lookup"><span data-stu-id="be7f1-168">**Supported**</span></span> | <span data-ttu-id="be7f1-169">**不支援**</span><span class="sxs-lookup"><span data-stu-id="be7f1-169">**Not Supported**</span></span> |
  | <span data-ttu-id="be7f1-170">最小的用戶端應用程式行為</span><span class="sxs-lookup"><span data-stu-id="be7f1-170">Minimal Client-Side Application Behavior</span></span> | <span data-ttu-id="be7f1-171">**適用於**</span><span class="sxs-lookup"><span data-stu-id="be7f1-171">**Well-Suited**</span></span> | <span data-ttu-id="be7f1-172">**大材小用**</span><span class="sxs-lookup"><span data-stu-id="be7f1-172">**Overkill**</span></span> |
  | <span data-ttu-id="be7f1-173">內容豐富且複雜的使用者介面需求</span><span class="sxs-lookup"><span data-stu-id="be7f1-173">Rich, Complex User Interface Requirements</span></span> | <span data-ttu-id="be7f1-174">**限制**</span><span class="sxs-lookup"><span data-stu-id="be7f1-174">**Limited**</span></span> | <span data-ttu-id="be7f1-175">**適用於**</span><span class="sxs-lookup"><span data-stu-id="be7f1-175">**Well-Suited**</span></span> |

>[!div class="step-by-step"]
<span data-ttu-id="be7f1-176">[上一個](現代的 web 層應用程式-characteristics.md)[下一步](architectural-principles.md)</span><span class="sxs-lookup"><span data-stu-id="be7f1-176">[Previous] (modern-web-applications-characteristics.md) [Next](architectural-principles.md)</span></span>
