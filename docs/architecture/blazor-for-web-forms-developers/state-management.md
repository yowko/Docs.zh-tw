---
title: 狀態管理
description: 瞭解在 ASP.NET Web Forms 和 Blazor 中管理狀態的不同方法。
author: csharpfritz
ms.author: jefritz
ms.date: 05/15/2020
ms.openlocfilehash: 2ca811f886c6a245ac16c2bd66a68ff16e5bfc44
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267720"
---
# <a name="state-management"></a><span data-ttu-id="339bb-103">狀態管理</span><span class="sxs-lookup"><span data-stu-id="339bb-103">State management</span></span>

<span data-ttu-id="339bb-104">狀態管理是 Web Form 應用程式的重要概念，可透過檢視狀態、會話狀態、應用程式狀態和回傳功能來提供。</span><span class="sxs-lookup"><span data-stu-id="339bb-104">State management is a key concept of Web Forms applications, facilitated through View State, Session State, Application State, and Postback features.</span></span> <span data-ttu-id="339bb-105">這些架構的可設定狀態功能有助於隱藏應用程式所需的狀態管理，並讓應用程式開發人員專注于提供其功能。</span><span class="sxs-lookup"><span data-stu-id="339bb-105">These stateful features of the framework helped to hide the state management required for an application and allow application developers to focus on delivering their functionality.</span></span> <span data-ttu-id="339bb-106">在 ASP.NET Core 和 Blazor 中，其中有些功能已重新放置，而且已完全移除部分功能。</span><span class="sxs-lookup"><span data-stu-id="339bb-106">With ASP.NET Core and Blazor, some of these features have been relocated and some have been removed altogether.</span></span> <span data-ttu-id="339bb-107">本章將探討如何使用 Blazor 中的新功能來維護狀態，並提供相同的功能。</span><span class="sxs-lookup"><span data-stu-id="339bb-107">This chapter reviews how to maintain state and deliver the same functionality with the new features in Blazor.</span></span>

## <a name="request-state-management-with-viewstate"></a><span data-ttu-id="339bb-108">使用 ViewState 的要求狀態管理</span><span class="sxs-lookup"><span data-stu-id="339bb-108">Request state management with ViewState</span></span>

<span data-ttu-id="339bb-109">在 Web Form 應用程式中討論狀態管理時，許多開發人員都會立即考慮 ViewState。</span><span class="sxs-lookup"><span data-stu-id="339bb-109">When discussing state management in Web Forms application, many developers will immediately think of ViewState.</span></span> <span data-ttu-id="339bb-110">在 Web Form 中，ViewState 會藉由將大型編碼的文字區塊來回傳送至瀏覽器，來管理 HTTP 要求之間的內容狀態。</span><span class="sxs-lookup"><span data-stu-id="339bb-110">In Web Forms, ViewState manages the state of the content between HTTP requests by sending a large encoded block of text back and forth to the browser.</span></span> <span data-ttu-id="339bb-111">ViewState 欄位可能會因為包含許多專案的頁面內容而淹沒，可能會擴充到數 mb 的大小。</span><span class="sxs-lookup"><span data-stu-id="339bb-111">The ViewState field could be overwhelmed with content from a page containing many elements, potentially expanding to several megabytes in size.</span></span>

<span data-ttu-id="339bb-112">使用 Blazor 伺服器時，應用程式會維持與伺服器的持續連線。</span><span class="sxs-lookup"><span data-stu-id="339bb-112">With Blazor Server, the app maintains an ongoing connection with the server.</span></span> <span data-ttu-id="339bb-113">當連接被視為使用中時，應用程式的狀態（稱為 *線路*）會保留在伺服器記憶體中。</span><span class="sxs-lookup"><span data-stu-id="339bb-113">The app's state, called a *circuit*, is held in server memory while the connection is considered active.</span></span> <span data-ttu-id="339bb-114">只有當使用者導覽離開應用程式或應用程式中的特定頁面時，才會處置狀態。</span><span class="sxs-lookup"><span data-stu-id="339bb-114">State will only be disposed when the user navigates away from the app or a particular page in the app.</span></span> <span data-ttu-id="339bb-115">使用中元件的所有成員都可以在與伺服器之間的互動之間使用。</span><span class="sxs-lookup"><span data-stu-id="339bb-115">All members of the active components are available between interactions with the server.</span></span>

<span data-ttu-id="339bb-116">這項功能有幾個優點：</span><span class="sxs-lookup"><span data-stu-id="339bb-116">There are several advantages of this feature:</span></span>

- <span data-ttu-id="339bb-117">元件狀態可立即使用，且不會在互動之間重建。</span><span class="sxs-lookup"><span data-stu-id="339bb-117">Component state is readily available and not rebuilt between interactions.</span></span>
- <span data-ttu-id="339bb-118">狀態不會傳送到瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="339bb-118">State isn't transmitted to the browser.</span></span>

<span data-ttu-id="339bb-119">不過，記憶體內部元件狀態持續性有一些缺點需要注意：</span><span class="sxs-lookup"><span data-stu-id="339bb-119">However, there are some disadvantages to in-memory component state persistence to be aware of:</span></span>

- <span data-ttu-id="339bb-120">如果伺服器在要求之間重新開機，則狀態會遺失。</span><span class="sxs-lookup"><span data-stu-id="339bb-120">If the server restarts between request, state is lost.</span></span>
- <span data-ttu-id="339bb-121">您的應用程式網頁伺服器負載平衡解決方案必須包含「粘滯話」，以確保來自相同瀏覽器的所有要求都會回到相同的伺服器。</span><span class="sxs-lookup"><span data-stu-id="339bb-121">Your application web server load-balancing solution must include sticky sessions to ensure that all requests from the same browser return to the same server.</span></span> <span data-ttu-id="339bb-122">如果要求移至不同的伺服器，狀態將會遺失。</span><span class="sxs-lookup"><span data-stu-id="339bb-122">If a request goes to a different server, state will be lost.</span></span>
- <span data-ttu-id="339bb-123">伺服器上的元件狀態持續性可能會導致 web 伺服器上的記憶體壓力。</span><span class="sxs-lookup"><span data-stu-id="339bb-123">Persistence of component state on the server can lead to memory pressure on the web server.</span></span>

<span data-ttu-id="339bb-124">基於上述原因，請不要只相依元件的狀態，以存放在伺服器的記憶體中。</span><span class="sxs-lookup"><span data-stu-id="339bb-124">For the preceding reasons, don't rely on just the state of the component to reside in-memory on the server.</span></span> <span data-ttu-id="339bb-125">您的應用程式也應該針對要求之間的資料包含一些支援資料存放區。</span><span class="sxs-lookup"><span data-stu-id="339bb-125">Your application should also include some backing data store for data between requests.</span></span> <span data-ttu-id="339bb-126">此策略的一些簡單範例：</span><span class="sxs-lookup"><span data-stu-id="339bb-126">Some simple examples of this strategy:</span></span>

- <span data-ttu-id="339bb-127">在購物車應用程式中，將新增至購物車的新專案內容保存在資料庫記錄中。</span><span class="sxs-lookup"><span data-stu-id="339bb-127">In a shopping cart application, persist the content of new items added to the cart in a database record.</span></span> <span data-ttu-id="339bb-128">如果伺服器上的狀態遺失，您可以從資料庫記錄重新組成。</span><span class="sxs-lookup"><span data-stu-id="339bb-128">If the state on the server is lost, you can reconstitute it from the database records.</span></span>
- <span data-ttu-id="339bb-129">在多部分的 web 表單中，您的使用者會預期您的應用程式會記住每個要求之間的值。</span><span class="sxs-lookup"><span data-stu-id="339bb-129">In a multi-part web form, your users will expect your application to remember values between each request.</span></span> <span data-ttu-id="339bb-130">將每個使用者的貼文之間的資料寫入資料存放區，以便在多部分表單完成時，將資料提取和組合成最終的表單回應結構。</span><span class="sxs-lookup"><span data-stu-id="339bb-130">Write the data between each of your user's posts to a data store so that they can be fetched and assembled into the final form response structure when the multi-part form is completed.</span></span>

<span data-ttu-id="339bb-131">如需在 Blazor apps 中管理狀態的其他詳細資料，請參閱 [ASP.NET Core Blazor 狀態管理](/aspnet/core/blazor/state-management)。</span><span class="sxs-lookup"><span data-stu-id="339bb-131">For additional details on managing state in Blazor apps, see [ASP.NET Core Blazor state management](/aspnet/core/blazor/state-management).</span></span>

## <a name="maintain-state-with-session"></a><span data-ttu-id="339bb-132">維護會話的狀態</span><span class="sxs-lookup"><span data-stu-id="339bb-132">Maintain state with Session</span></span>

<span data-ttu-id="339bb-133">Web Form 開發人員可以使用 dictionary 物件來維護目前作用中使用者的相關資訊 <xref:Microsoft.AspNetCore.Http.ISession?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="339bb-133">Web Forms developers could maintain information about the currently acting user with the <xref:Microsoft.AspNetCore.Http.ISession?displayProperty=nameWithType> dictionary object.</span></span> <span data-ttu-id="339bb-134">您可以使用字串索引鍵將物件加入至 `Session` ，並在使用者與應用程式互動時，稍後再使用該物件。</span><span class="sxs-lookup"><span data-stu-id="339bb-134">It's easy enough to add an object with a string key to the `Session`, and that object would be available at a later time during the user's interactions with the application.</span></span> <span data-ttu-id="339bb-135">在嘗試消除與 HTTP 互動的管理時， `Session` 物件讓您能夠輕鬆地維護狀態。</span><span class="sxs-lookup"><span data-stu-id="339bb-135">In an attempt to eliminate managing interacting with HTTP, the `Session` object made it easy to maintain state.</span></span>

<span data-ttu-id="339bb-136">.NET Framework 物件的簽章與 `Session` ASP.NET Core 物件不相同 `Session` 。</span><span class="sxs-lookup"><span data-stu-id="339bb-136">The signature of the .NET Framework `Session` object isn't the same as the ASP.NET Core `Session` object.</span></span> <span data-ttu-id="339bb-137">在決定遷移和使用新的會話狀態功能之前，請先考慮 [新 ASP.NET Core 會話的檔](/dotnet/api/microsoft.aspnetcore.http.isession) 。</span><span class="sxs-lookup"><span data-stu-id="339bb-137">Consider [the documentation for the new ASP.NET Core Session](/dotnet/api/microsoft.aspnetcore.http.isession) before deciding to migrate and use the new session state feature.</span></span>

<span data-ttu-id="339bb-138">會話可在 ASP.NET Core 和 Blazor Server 中使用，但不建議您在適當的情況下將資料儲存在資料存放庫中。</span><span class="sxs-lookup"><span data-stu-id="339bb-138">Session is available in ASP.NET Core and Blazor Server, but is discouraged from use in favor of storing data in a data repository appropriately.</span></span> <span data-ttu-id="339bb-139">如果訪客因隱私權考慮而拒絕在您的應用程式中使用 HTTP cookie，則會話狀態也無法運作。</span><span class="sxs-lookup"><span data-stu-id="339bb-139">Session state is also not functional if visitors decline the use HTTP cookies in your application due to privacy concerns.</span></span>

<span data-ttu-id="339bb-140">ASP.NET Core 和會話狀態的設定可在 [ASP.NET Core 文章的會話和狀態管理](/aspnet/core/fundamentals/app-state#session-state)中取得。</span><span class="sxs-lookup"><span data-stu-id="339bb-140">Configuration for ASP.NET Core and Session state is available in the [Session and state management in ASP.NET Core article](/aspnet/core/fundamentals/app-state#session-state).</span></span>

## <a name="application-state"></a><span data-ttu-id="339bb-141">應用程式狀態</span><span class="sxs-lookup"><span data-stu-id="339bb-141">Application state</span></span>

<span data-ttu-id="339bb-142">`Application`Web Form 架構中的物件提供大量、跨要求的存放庫，可與應用程式範圍設定和狀態進行互動。</span><span class="sxs-lookup"><span data-stu-id="339bb-142">The `Application` object in the Web Forms framework provides a massive, cross-request repository for interacting with application-scope configuration and state.</span></span> <span data-ttu-id="339bb-143">應用程式狀態是儲存各種應用程式設定屬性的理想位置，所有要求都會參考這些屬性，不論提出要求的使用者為何。</span><span class="sxs-lookup"><span data-stu-id="339bb-143">Application state was an ideal place to store various application configuration properties that would be referenced by all requests, regardless of the user making the request.</span></span> <span data-ttu-id="339bb-144">物件的問題 `Application` 在於，資料不會跨多個伺服器保存。</span><span class="sxs-lookup"><span data-stu-id="339bb-144">The problem with the `Application` object was that data didn't persist across multiple servers.</span></span> <span data-ttu-id="339bb-145">重新開機之間的應用程式物件狀態已遺失。</span><span class="sxs-lookup"><span data-stu-id="339bb-145">The state of the application object was lost between restarts.</span></span>

<span data-ttu-id="339bb-146">如同 `Session` ，建議將資料移至可供多個伺服器實例存取的持續性備份存放區。</span><span class="sxs-lookup"><span data-stu-id="339bb-146">As with `Session`, it's recommended that data move to a persistent backing store that could be accessed by multiple server instances.</span></span> <span data-ttu-id="339bb-147">如果有您想要能夠跨要求和使用者存取的變動性資料，您可以輕鬆地將它儲存在單一服務中，以插入需要此資訊或互動的元件中。</span><span class="sxs-lookup"><span data-stu-id="339bb-147">If there is volatile data that you would like to be able to access across requests and users, you could easily store it in a singleton service that can be injected into components that require this information or interaction.</span></span>

<span data-ttu-id="339bb-148">用來維護應用程式狀態和其耗用量的物件結構，可能類似于下列實作為：</span><span class="sxs-lookup"><span data-stu-id="339bb-148">The construction of an object to maintain application state and its consumption could resemble the following implementation:</span></span>

```csharp
public class MyApplicationState
{
    public int VisitorCounter { get; private set; } = 0;

    public void IncrementCounter() => VisitorCounter += 1;
}
```

```csharp
app.AddSingleton<MyApplicationState>();
```

```razor
@inject MyApplicationState AppState

<label>Total Visitors: @AppState.VisitorCounter</label>
```

<span data-ttu-id="339bb-149">`MyApplicationState`物件只會在伺服器上建立一次，而且 `VisitorCounter` 會提取值並在元件的標籤中輸出。</span><span class="sxs-lookup"><span data-stu-id="339bb-149">The `MyApplicationState` object is created only once on the server, and the value `VisitorCounter` is fetched and output in the component's label.</span></span> <span data-ttu-id="339bb-150">`VisitorCounter`值應該保存並從支援資料存放區中抓取，以提供持久性和擴充性。</span><span class="sxs-lookup"><span data-stu-id="339bb-150">The `VisitorCounter` value should be persisted and retrieved from a backing data store for durability and scalability.</span></span>

## <a name="in-the-browser"></a><span data-ttu-id="339bb-151">在瀏覽器中</span><span class="sxs-lookup"><span data-stu-id="339bb-151">In the browser</span></span>

<span data-ttu-id="339bb-152">應用程式資料也可以儲存在使用者裝置上的用戶端，以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="339bb-152">Application data can also be stored client-side on the user's device so that is available later.</span></span> <span data-ttu-id="339bb-153">有兩種瀏覽器功能可在使用者瀏覽器的不同範圍中保存資料：</span><span class="sxs-lookup"><span data-stu-id="339bb-153">There are two browser features that allow for persistence of data in different scopes of the user's browser:</span></span>

- <span data-ttu-id="339bb-154">`localStorage` -範圍限定于使用者的整個瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="339bb-154">`localStorage` - scoped to the user's entire browser.</span></span> <span data-ttu-id="339bb-155">如果頁面已重載，則會關閉並重新開啟瀏覽器，或使用相同的 URL 開啟另一個索引標籤，而 `localStorage` 瀏覽器會提供相同的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="339bb-155">If the page is reloaded, the browser is closed and reopened, or another tab is opened with the same URL then the same `localStorage` is provided by the browser</span></span>
- <span data-ttu-id="339bb-156">`sessionStorage` -範圍設定為使用者目前的瀏覽器索引標籤。如果重載索引標籤，則狀態會持續存在。</span><span class="sxs-lookup"><span data-stu-id="339bb-156">`sessionStorage` - scoped to the user's current browser tab. If the tab is reloaded, the state persists.</span></span> <span data-ttu-id="339bb-157">不過，如果使用者對您的應用程式開啟另一個索引標籤，或關閉並重新開啟瀏覽器，則狀態會遺失。</span><span class="sxs-lookup"><span data-stu-id="339bb-157">However, if the user opens another tab to your application or closes and reopens the browser the state is lost.</span></span>

<span data-ttu-id="339bb-158">您可以撰寫一些自訂 JavaScript 程式碼來與這些功能互動，或有許多可供您使用的 NuGet 套件，以提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="339bb-158">You can write some custom JavaScript code to interact with these features, or there are a number of NuGet packages that you can use that provide this functionality.</span></span> <span data-ttu-id="339bb-159">其中一個這類套件是 [AspNetCore. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.ProtectedBrowserStorage)。</span><span class="sxs-lookup"><span data-stu-id="339bb-159">One such package is [Microsoft.AspNetCore.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.ProtectedBrowserStorage).</span></span>

<span data-ttu-id="339bb-160">如需使用此封裝來與和互動的指示 `localStorage` `sessionStorage` ，請參閱 [Blazor 狀態管理](/aspnet/core/blazor/state-management#protected-browser-storage-experimental-package) 文章。</span><span class="sxs-lookup"><span data-stu-id="339bb-160">For instructions on utilizing this package to interact with `localStorage` and `sessionStorage`, see the [Blazor State Management](/aspnet/core/blazor/state-management#protected-browser-storage-experimental-package) article.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="339bb-161">[上一個](pages-routing-layouts.md) 
>[下一步](forms-validation.md)</span><span class="sxs-lookup"><span data-stu-id="339bb-161">[Previous](pages-routing-layouts.md)
[Next](forms-validation.md)</span></span>
