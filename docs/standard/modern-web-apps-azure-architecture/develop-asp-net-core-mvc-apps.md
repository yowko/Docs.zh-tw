---
title: "開發 ASP.NET Core MVC 應用程式"
description: "使用 ASP.NET Core 和 Azure 的現代化 Web 應用程式架構設計人員 |開發 ASP.NET Core MVC 應用程式"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c10bf66dd37f0d99c038db7f95999d84986152fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="develop-aspnet-core-mvc-apps"></a><span data-ttu-id="e4a2e-103">開發 ASP.NET Core MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="e4a2e-103">Develop ASP.NET Core MVC Apps</span></span>

> <span data-ttu-id="e4a2e-104">「 不重要拿第一次。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-104">"It's not important to get it right the first time.</span></span> <span data-ttu-id="e4a2e-105">務必日漸拿最後一次。 」</span><span class="sxs-lookup"><span data-stu-id="e4a2e-105">It's vitally important to get it right the last time."</span></span>  
> <span data-ttu-id="e4a2e-106">_-Andrew 搜尋和 David Thomas_</span><span class="sxs-lookup"><span data-stu-id="e4a2e-106">_- Andrew Hunt and David Thomas_</span></span>

## <a name="summary"></a><span data-ttu-id="e4a2e-107">總結</span><span class="sxs-lookup"><span data-stu-id="e4a2e-107">Summary</span></span>

<span data-ttu-id="e4a2e-108">ASP.NET Core 是跨平台、 開放原始碼的架構，用於建置現代化的雲端最佳化 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-108">ASP.NET Core is a cross-platform, open-source framework for building modern cloud-optimized web applications.</span></span> <span data-ttu-id="e4a2e-109">ASP.NET Core 應用程式是輕量且模組化的與相依性插入，在更高的可測試性及可維護性中啟用內建支援。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-109">ASP.NET Core apps are lightweight and modular, with built-in support for dependency injection, enabling in greater testability and maintainability.</span></span> <span data-ttu-id="e4a2e-110">結合 MVC、 支援建置現代化 web 應用程式開發介面，除了檢視架構的應用程式，ASP.NET Core 是功能強大的架構，用來建置企業 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-110">Combined with MVC, which supports building modern web APIs in addition to view-based apps, ASP.NET Core is a powerful framework with which to build enterprise web applications.</span></span>

## <a name="mapping-requests-to-responses"></a><span data-ttu-id="e4a2e-111">將要求對應至回應</span><span class="sxs-lookup"><span data-stu-id="e4a2e-111">Mapping Requests to Responses</span></span>

<span data-ttu-id="e4a2e-112">本質上 ASP.NET Core 應用程式會將內送要求對應到傳出回應。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-112">At its heart, ASP.NET Core apps map incoming requests to outgoing responses.</span></span> <span data-ttu-id="e4a2e-113">在低的層級，做法是使用中介軟體，及簡單的 ASP.NET Core 應用程式和 microservices 可能同時包含完全自訂的中介軟體。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-113">At a low level, this is done with middleware, and simple ASP.NET Core apps and microservices may be comprised solely of custom middleware.</span></span> <span data-ttu-id="e4a2e-114">當使用 ASP.NET Core MVC 時，您可以考慮的工作稍微高的層級，*路由*，*控制器*，和*動作*。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-114">When using ASP.NET Core MVC, you can work at a somewhat higher level, thinking in terms of *routes*, *controllers*, and *actions*.</span></span> <span data-ttu-id="e4a2e-115">每個傳入要求與應用程式的路由表，而且如果找到相符的路由，相關聯的動作方法 （屬於 「 控制器 」） 呼叫來處理要求。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-115">Each incoming request is compared with the application's routing table, and if a matching route is found, the associated action method (belonging to a controller) is called to handle the request.</span></span> <span data-ttu-id="e4a2e-116">如果找到符合的路由時，會呼叫錯誤處理常式 （在此情況下，傳回找不到結果）。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-116">If no matching route is found, an error handler (in this case, returning a NotFound result) is called.</span></span>

<span data-ttu-id="e4a2e-117">ASP.NET Core MVC 應用程式可以使用傳統的路由、 屬性路由，或兩者。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-117">ASP.NET Core MVC apps can use conventional routes, attribute routes, or both.</span></span> <span data-ttu-id="e4a2e-118">程式碼中，指定路由中所定義的傳統路由*慣例*在下列範例中使用類似的語法：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-118">Conventional routes are defined in code, specifying routing *conventions* using syntax like in the example below:</span></span>

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="e4a2e-119">已在此範例中，加入名為 「 預設 」 的路由，路由表。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-119">In this example, a route named "default" has been added to the routing table.</span></span> <span data-ttu-id="e4a2e-120">它會定義路由範本使用預留位置*控制器*，*動作*，和*識別碼*。控制器和動作的預留位置已經指定預設值 (「 組織 」 和 「 索引 」，分別)，而且識別碼預留位置是選擇性 (憑藉"？"套用至它)。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-120">It defines a route template with placeholders for *controller*, *action*, and *id*. The controller and action placeholders have default specified ("Home" and "Index", respectively), and the id placeholder is optional (by virtue of a "?" applied to it).</span></span> <span data-ttu-id="e4a2e-121">慣例此處定義狀態要求的第一個部分應該對應至控制器，到動作中，第二個部分的名稱，然後視第三個部分會代表 id 參數。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-121">The convention defined here states that the first part of a request should correspond to the name of the controller, the second part to the action, and then if necessary a third part will represent an id parameter.</span></span> <span data-ttu-id="e4a2e-122">傳統的路由通常被定義在一個地方應用程式，例如設定類別方法中啟動。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-122">Conventional routes are typically defined in one place for the application, such as in the Configure method in the Startup class.</span></span>

<span data-ttu-id="e4a2e-123">屬性路由會直接套用至控制器和動作而不是指定全域。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-123">Attribute routes are applied to controllers and actions directly, rather than specified globally.</span></span> <span data-ttu-id="e4a2e-124">這樣做讓它們很容易找到有關當您正在查看的特定方法，但意思路由資訊不保留在應用程式中的一個位置的好處。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-124">This has the advantage of making them much more discoverable when you're looking at a particular method, but does mean that routing information is not kept in one place in the application.</span></span> <span data-ttu-id="e4a2e-125">屬性路由，您可以輕鬆地指定多個路由是給定的動作，以及結合控制器與動作之間的路由。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-125">With attribute routes, you can easily specify multiple routes for a given action, as well as combine routes between controllers and actions.</span></span> <span data-ttu-id="e4a2e-126">例如: </span><span class="sxs-lookup"><span data-stu-id="e4a2e-126">For example:</span></span>

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

<span data-ttu-id="e4a2e-127">可以在 [HttpGet] 上指定的路由，並將類似的屬性，避免需要加入 [路由\]屬性。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-127">Routes can be specified on [HttpGet] and similar attributes, avoiding the need to add separate [Route\] attributes.</span></span> <span data-ttu-id="e4a2e-128">屬性路由也可以使用語彙基元來減少重複控制器或動作名稱的需求，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-128">Attribute routes can also use tokens to reduce the need to repeat controller or action names, as shown below:</span></span>

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

<span data-ttu-id="e4a2e-129">一旦已路由，以比對給定的要求，但動作之前，呼叫方法，將會執行 ASP.NET Core MVC[模型繫結](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding)和[模型驗證](https://docs.microsoft.com/aspnet/core/mvc/models/validation)在要求上。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-129">Once a given request has been matched to a route, but before the action method is called, ASP.NET Core MVC will perform [model binding](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) and [model validation](https://docs.microsoft.com/aspnet/core/mvc/models/validation) on the request.</span></span> <span data-ttu-id="e4a2e-130">模型繫結會負責將傳入的 HTTP 資料轉換為.NET 型別指定為動作方法的參數來呼叫。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-130">Model binding is responsible for converting incoming HTTP data into the .NET types specified as parameters of the action method to be called.</span></span> <span data-ttu-id="e4a2e-131">例如，如果動作方法預期 int id 參數，模型繫結會提供這個參數要求中提供的值。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-131">For example, if the action method expects an int id parameter, model binding will attempt to provide this parameter from a value provided as part of the request.</span></span> <span data-ttu-id="e4a2e-132">若要這樣做，模型繫結會尋找已張貼的表單中的值、 路由本身中的值和查詢字串值。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-132">To do so, model binding looks for values in a posted form, values in the route itself, and query string values.</span></span> <span data-ttu-id="e4a2e-133">假設找到 id 值，它會轉換成整數傳遞至動作方法之前。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-133">Assuming an id value is found, it will be converted to an integer before being passed into the action method.</span></span>

<span data-ttu-id="e4a2e-134">繫結模型之後，但在呼叫動作方法之前，就會發生模型驗證。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-134">After binding the model but before calling the action method, model validation occurs.</span></span> <span data-ttu-id="e4a2e-135">模型驗證模型型別，會使用選用的屬性，並可協助確保提供的模型物件符合特定的資料需求。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-135">Model validation uses optional attributes on the model type, and can help ensure that the provided model object conforms to certain data requirements.</span></span> <span data-ttu-id="e4a2e-136">某些值可指定為必要，或限制為特定長度或數字範圍，等等。如果驗證屬性會指定，但是模型不符合其需求，屬性 ModelState.IsValid 會是 false，並無法驗證規則集將可傳送到提出要求的用戶端。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-136">Certain values may be specified as required, or limited to a certain length or numeric range, etc. If validation attributes are specified but the model does not conform to their requirements, the property ModelState.IsValid will be false, and the set of failing validation rules will be available to send to the client making the request.</span></span>

<span data-ttu-id="e4a2e-137">如果您使用的模型驗證，您應該一律請檢查模型有效，然後再執行任何狀態改變命令，以確保您的應用程式未正確的資料損毀。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-137">If you are using model validation, you should be sure to always check that the model is valid before performing any state-altering commands, to ensure your app is not corrupted by invalid data.</span></span> <span data-ttu-id="e4a2e-138">您可以使用[篩選](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters)避免需要此加入程式碼中的每個動作。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-138">You can use a [filter](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) to avoid the need to add code for this in every action.</span></span> <span data-ttu-id="e4a2e-139">ASP.NET Core MVC 篩選條件提供一種攔截的要求，群組，以便一般原則與跨領域考量可以套用以目標為基礎。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-139">ASP.NET Core MVC filters offer a way of intercepting groups of requests, so that common policies and cross-cutting concerns can be applied on a targeted basis.</span></span> <span data-ttu-id="e4a2e-140">篩選可以套用到個別的動作，整個控制站，或全域應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-140">Filters can be applied to individual actions, whole controllers, or globally for an application.</span></span>

<span data-ttu-id="e4a2e-141">針對 web 應用程式開發介面，支援 ASP.NET Core MVC [*內容交涉*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting)，允許以指定應如何格式化回應要求。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-141">For web APIs, ASP.NET Core MVC supports [*content negotiation*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), allowing requests to specify how responses should be formatted.</span></span> <span data-ttu-id="e4a2e-142">根據要求中提供的標頭，傳回資料的動作，將會格式化 XML、 JSON 或另一種支援的格式的回應。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-142">Based on headers provided in the request, actions returning data will format the response in XML, JSON, or another supported format.</span></span> <span data-ttu-id="e4a2e-143">這項功能可讓相同的 API 以供不同的資料格式需求的多個用戶端。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-143">This feature enables the same API to be used by multiple clients with different data format requirements.</span></span>

> ### <a name="references--mapping-requests-to-responses"></a><span data-ttu-id="e4a2e-144">參考 – 對應至回應的要求</span><span class="sxs-lookup"><span data-stu-id="e4a2e-144">References – Mapping Requests to Responses</span></span>
> - <span data-ttu-id="e4a2e-145">**路由至控制器動作**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span><span class="sxs-lookup"><span data-stu-id="e4a2e-145">**Routing to Controller Actions**
<https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span></span>
> - <span data-ttu-id="e4a2e-146">**模型繫結**https://docs.microsoft.com/aspnet/core/mvc/models/model-binding</span><span class="sxs-lookup"><span data-stu-id="e4a2e-146">**Model Binding** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding</span></span>
> - <span data-ttu-id="e4a2e-147">**模型驗證**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation></span><span class="sxs-lookup"><span data-stu-id="e4a2e-147">**Model Validation**
<https://docs.microsoft.com/aspnet/core/mvc/models/validation></span></span>
> - <span data-ttu-id="e4a2e-148">**Filters** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters</span><span class="sxs-lookup"><span data-stu-id="e4a2e-148">**Filters** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters</span></span>

## <a name="working-with-dependencies"></a><span data-ttu-id="e4a2e-149">處理的相依性</span><span class="sxs-lookup"><span data-stu-id="e4a2e-149">Working with Dependencies</span></span>

<span data-ttu-id="e4a2e-150">ASP.NET Core 已內建支援，並在內部使用 ant colony optimization[相依性插入](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-150">ASP.NET Core has built-in support for and internally makes use of a technique known as [dependency injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="e4a2e-151">相依性插入是啟用的應用程式的不同部分之間的鬆散偶合的技術。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-151">Dependency injection is a technique that enabled loose coupling between different parts of an application.</span></span> <span data-ttu-id="e4a2e-152">鬆散偶合是合理的因為它可更輕鬆地隔離的應用程式，以便進行測試或取代組件。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-152">Looser coupling is desirable because it makes it easier to isolate parts of the application, allowing for testing or replacement.</span></span> <span data-ttu-id="e4a2e-153">您也可以比較不可能的應用程式的一個部分中的變更將會有非預期的影響應用程式中其他地方。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-153">It also makes it less likely that a change in one part of the application will have an unexpected impact somewhere else in the application.</span></span> <span data-ttu-id="e4a2e-154">相依性插入為基礎的相依性反向原則，和通常是達到的開啟/關閉的原則機碼。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-154">Dependency injection is based on the dependency inversion principle, and is often key to achieving the open/closed principle.</span></span> <span data-ttu-id="e4a2e-155">當評估您的應用程式具其相依性的運作方式，請注意[靜態黏貼](http://deviq.com/static-cling/)程式碼嗅覺並記住 aphorism"[新是黏附](http://ardalis.com/new-is-glue)。 」</span><span class="sxs-lookup"><span data-stu-id="e4a2e-155">When evaluating how your application works with its dependencies, beware of the [static cling](http://deviq.com/static-cling/) code smell, and remember the aphorism "[new is glue](http://ardalis.com/new-is-glue)."</span></span>

<span data-ttu-id="e4a2e-156">您的類別呼叫靜態方法，或存取靜態屬性，它有副作用或相依性基礎結構時，就會發生靜態黏貼。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-156">Static cling occurs when your classes make calls to static methods, or access static properties, which have side effects or dependencies on infrastructure.</span></span> <span data-ttu-id="e4a2e-157">例如，如果您有個方法，呼叫靜態方法，後者接著寫入資料庫，您的方法資料庫緊密結合。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-157">For example, if you have a method that calls a static method, which in turn writes to a database, your method is tightly coupled to the database.</span></span> <span data-ttu-id="e4a2e-158">任何項目會中斷該資料庫的呼叫將會中斷您的方法。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-158">Anything that breaks that database call will break your method.</span></span> <span data-ttu-id="e4a2e-159">因為這類測試需要模擬商業文件庫模擬靜態的呼叫，或只可使用測試資料庫中進行測試，測試這種方法很難。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-159">Testing such methods is notoriously difficult, since such tests either require commercial mocking libraries to mock the static calls, or can only be tested with a test database in place.</span></span> <span data-ttu-id="e4a2e-160">靜態沒有基礎結構，特別是那些會完全無狀態，任何相依性的呼叫是呼叫，並結合或可測試性 （除了結合靜態呼叫本身的程式碼） 上不會影響正常的。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-160">Static calls that don't have any dependence on infrastructure, especially those that are completely stateless, are fine to call and have no impact on coupling or testability (beyond coupling code to the static call itself).</span></span>

<span data-ttu-id="e4a2e-161">許多開發人員了解的風險靜態黏貼 」 以及 「 全域狀態，但將仍緊密結合透過直接具現化的特定實作的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-161">Many developers understand the risks of static cling and global state, but will still tightly couple their code to specific implementations through direct instantiation.</span></span> <span data-ttu-id="e4a2e-162">「 新 」 黏附是提醒的這個結合，並不使用新的關鍵字，使用一般 condemnation。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-162">"New is glue" is meant to be a reminder of this coupling, and not a general condemnation of the use of the new keyword.</span></span> <span data-ttu-id="e4a2e-163">就如同處理靜態方法呼叫時，通常沒有任何外部的相依性的類型的新執行個體執行不緊密結合程式碼來實作詳細資料或讓測試更困難。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-163">Just as with static method calls, new instances of types that have no external dependencies typically do not tightly couple code to implementation details or make testing more difficult.</span></span> <span data-ttu-id="e4a2e-164">但是類別具現化，每次需要只長的時間是否合理硬式編碼至該特定執行個體的特定位置，或如果可能更好的設計，以要求該執行個體做為相依性的考量。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-164">But each time a class is instantiated, take just a brief moment to consider whether it makes sense to hard-code that specific instance in that particular location, or if it would be a better design to request that instance as a dependency.</span></span>

### <a name="declare-your-dependencies"></a><span data-ttu-id="e4a2e-165">宣告相依性</span><span class="sxs-lookup"><span data-stu-id="e4a2e-165">Declare Your Dependencies</span></span>

<span data-ttu-id="e4a2e-166">ASP.NET Core 建置周圍有方法和類別宣告它們的相依性，要求它們做為引數。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-166">ASP.NET Core is built around having methods and classes declare their dependencies, requesting them as arguments.</span></span> <span data-ttu-id="e4a2e-167">ASP.NET 應用程式通常設定在啟動類別中，而其本身設定為支援數個時間點的相依性插入。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-167">ASP.NET applications are typically set up in a Startup class, which itself is configured to support dependency injection at several points.</span></span> <span data-ttu-id="e4a2e-168">如果您啟動的類別建構函式，它可以要求相依性，透過建構函式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-168">If your Startup class has a constructor, it can request dependencies through the constructor, like so:</span></span>

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile(\$"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

<span data-ttu-id="e4a2e-169">啟動類別有趣的是，因為它沒有明確的型別需求。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-169">The Startup class is interesting in that there are no explicit type requirements for it.</span></span> <span data-ttu-id="e4a2e-170">它不會繼承特殊的啟動基底類別，也不會實作任何特定的介面。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-170">It doesn't inherit from a special Startup base class, nor does it implement any particular interface.</span></span> <span data-ttu-id="e4a2e-171">您可以提供給它的建構函式，而且可以指定您想要多個建構函式參數。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-171">You can give it a constructor, or not, and you can specify as many parameters on the constructor as you want.</span></span> <span data-ttu-id="e4a2e-172">您已設定您的應用程式的 web 主機啟動時，它會呼叫您告知它使用，請啟動類別，並會使用相依性插入來填入啟動類別需要任何相依性。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-172">When the web host you've configured for your application starts, it will call the Startup class you've told it to use, and will use dependency injection to populate any dependencies the Startup class requires.</span></span> <span data-ttu-id="e4a2e-173">當然，如果您要求不會設定 ASP.NET Core 所使用的服務容器中的參數，您會得到例外狀況，但只要您從相依性容器知道，您可以要求您想要的任何項目。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-173">Of course, if you request parameters that aren't configured in the services container used by ASP.NET Core, you'll get an exception, but as long as you stick to dependencies the container knows about, you can request anything you want.</span></span>

<span data-ttu-id="e4a2e-174">相依性插入是內建您的 ASP.NET Core 應用程式，從一開始，當您建立啟動的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-174">Dependency injection is built into your ASP.NET Core apps right from the start, when you create the Startup instance.</span></span> <span data-ttu-id="e4a2e-175">它不會那里停止啟動類別。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-175">It doesn't stop there for the Startup class.</span></span> <span data-ttu-id="e4a2e-176">您也可以要求中設定方法的相依性：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-176">You can also request dependencies in the Configure method:</span></span>

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

<span data-ttu-id="e4a2e-177">ConfigureServices 方法是以這種行為; 例外狀況它必須採取別的 IServiceCollection 只有一個參數。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-177">The ConfigureServices method is the exception to this behavior; it must take just one parameter of type IServiceCollection.</span></span> <span data-ttu-id="e4a2e-178">它實際上不需要支援相依性插入，因為它會負責將物件加入至服務容器，一方面，而且在另有存取所有目前設定的服務，透過 IServiceCollection 參數。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-178">It doesn't really need to support dependency injection, since on the one hand it is responsible for adding objects to the services container, and on the other it has access to all currently configured services via the IServiceCollection parameter.</span></span> <span data-ttu-id="e4a2e-179">因此，您可以使用啟動類別，做為參數所需的服務要求，或在 ConfigureServices IServiceCollection 所使用的每個組件中的 ASP.NET Core services 集合中定義的相依性。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-179">Thus, you can work with dependencies defined in the ASP.NET Core services collection in every part of the Startup class, either by requesting the needed service as a parameter or by working with the IServiceCollection in ConfigureServices.</span></span>

> [!NOTE]
> <span data-ttu-id="e4a2e-180">如果您需要確保可啟動類別的特定服務，您可以設定它們使用 WebHostBuilder 和其 ConfigureServices 方法。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-180">If you need to ensure certain services are available to your Startup class, you can configure them using WebHostBuilder and its ConfigureServices method.</span></span>

<span data-ttu-id="e4a2e-181">啟動類別是您如何結構 ASP.NET Core 應用程式，控制站，以篩選器，以您自己的服務中介軟體的其他部分的模型。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-181">The Startup class is a model for how you should structure other parts of your ASP.NET Core application, from Controllers to Middleware to Filters to your own Services.</span></span> <span data-ttu-id="e4a2e-182">在每個案例中，您應該遵循[明確的相依性原則](http://deviq.com/explicit-dependencies-principle/)、 要求相依性而不是直接建立它們，以及利用整個應用程式的相依性插入。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-182">In each case, you should follow the [Explicit Dependencies Principle](http://deviq.com/explicit-dependencies-principle/), requesting your dependencies rather than directly creating them, and leveraging dependency injection throughout your application.</span></span> <span data-ttu-id="e4a2e-183">請小心的位置和方式您直接具現化實作中，特別是 「 服務 」 和 「 使用基礎結構，或具有副作用的物件。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-183">Be careful of where and how you directly instantiate implementations, especially services and objects that work with infrastructure or have side effects.</span></span> <span data-ttu-id="e4a2e-184">偏好使用定義在您的應用程式的核心，而且在做為引數傳遞給特定的實作類型的硬式編碼參考的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-184">Prefer working with abstractions defined in your application core and passed in as arguments to hardcoding references to specific implementation types.</span></span>

## <a name="structuring-the-application"></a><span data-ttu-id="e4a2e-185">結構化應用程式</span><span class="sxs-lookup"><span data-stu-id="e4a2e-185">Structuring the Application</span></span>

<span data-ttu-id="e4a2e-186">整合應用程式通常具有單一進入點。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-186">Monolithic applications typically have a single entry point.</span></span> <span data-ttu-id="e4a2e-187">在 ASP.NET Core web 應用程式的進入點將會是 ASP.NET Core web 專案。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-187">In the case of an ASP.NET Core web application, the entry point will be the ASP.NET Core web project.</span></span> <span data-ttu-id="e4a2e-188">不過，這不表示方案應包含只在單一專案中。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-188">However, that doesn't mean the solution should consist of just a single project.</span></span> <span data-ttu-id="e4a2e-189">它是用於切割有所依循的重要性分離到不同的圖層的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-189">It's useful to break up the application into different layers in order to follow separation of concerns.</span></span> <span data-ttu-id="e4a2e-190">一旦分解為圖層，就很有幫助超越資料夾，以不同的專案，可以協助您達成更好的封裝。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-190">Once broken up into layers, it's helpful to go beyond folders to separate projects, which can help achieve better encapsulation.</span></span> <span data-ttu-id="e4a2e-191">最好的方法來達成這些目標與 ASP.NET Core 應用程式是架構的一種全新中第 5 章討論。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-191">The best approach to achieve these goals with an ASP.NET Core application is a variation of the Clean Architecture discussed in chapter 5.</span></span> <span data-ttu-id="e4a2e-192">這個方法時，下列應用程式的方案會組成個別的程式庫 UI、 基礎結構，和 ApplicationCore。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-192">Following this approach, the application's solution will be comprised of separate libraries for the UI, Infrastructure, and ApplicationCore.</span></span>

<span data-ttu-id="e4a2e-193">除了這些專案中，個別的測試專案也包含 （在第 9 章討論測試）。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-193">In addition to these projects, separate test projects are included as well (Testing is discussed in Chapter 9).</span></span>

<span data-ttu-id="e4a2e-194">應用程式的物件模型和介面應該放在 ApplicationCore 專案。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-194">The application's object model and interfaces should be placed in the ApplicationCore project.</span></span> <span data-ttu-id="e4a2e-195">這個專案將會較少的相依性越好，而方案中的其他專案會參考它。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-195">This project will have as few dependencies as possible, and the other projects in the solution will reference it.</span></span> <span data-ttu-id="e4a2e-196">需要保存的商務實體會定義於 ApplicationCore 專案，因為不直接相依於基礎結構的服務。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-196">Business entities that need to be persisted are defined in the ApplicationCore project, as are services that do not directly depend on infrastructure.</span></span>

<span data-ttu-id="e4a2e-197">實作詳細資料，例如持續性的執行方式，或如何可能會傳送通知給使用者，會保留在基礎結構專案。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-197">Implementation details, such as how persistence is performed or how notifications might be sent to a user, are kept in the Infrastructure project.</span></span> <span data-ttu-id="e4a2e-198">這個專案會參考 Entity Framework Core，例如實作特定封裝，但是不應該公開有關這些專案以外的其他實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-198">This project will reference implementation-specific packages such as Entity Framework Core, but should not expose details about these implementations outside of the project.</span></span> <span data-ttu-id="e4a2e-199">基礎結構服務和儲存機制，則應該實作 ApplicationCore 專案中所定義的介面和其持續性實作會負責擷取和儲存 ApplicationCore 中定義的實體。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-199">Infrastructure services and repositories should implement interfaces that are defined in the ApplicationCore project, and its persistence implementations are responsible for retrieving and storing entities defined in ApplicationCore.</span></span>

<span data-ttu-id="e4a2e-200">ASP.NET Core 專案本身會負責任何 UI 層級的考量，但不是應包含商務邏輯或基礎結構詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-200">The ASP.NET Core project itself is responsible for any UI level concerns, but should not include business logic or infrastructure details.</span></span> <span data-ttu-id="e4a2e-201">事實上，在理想情況下它不應該甚至有相依性基礎結構專案中，將有助於確保不小心引入兩個專案之間沒有相依性。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-201">In fact, ideally it shouldn't even have a dependency on the Infrastructure project, which will help ensure no dependency between the two projects is introduced accidentally.</span></span> <span data-ttu-id="e4a2e-202">這可以使用第三方 DI 容器像 StructureMap，可讓您定義 DI 規則中每個專案中的登錄類別來達成。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-202">This can be achieved using a third-party DI container like StructureMap, which allows you to define DI rules in Registry classes in each project.</span></span>

<span data-ttu-id="e4a2e-203">若要減少應用程式的實作詳細資料的另一種方法是讓應用程式呼叫 microservices，可能是部署在個別的 Docker 容器中。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-203">Another approach to decoupling the application from implementation details is to have the application call microservices, perhaps deployed in individual Docker containers.</span></span> <span data-ttu-id="e4a2e-204">這提供更佳的考量，比利用 DI 兩個專案之間的去耦合分隔，但具有額外的複雜性。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-204">This provides even greater separation of concerns and decoupling than leveraging DI between two projects, but has additional complexity.</span></span>

### <a name="feature-organization"></a><span data-ttu-id="e4a2e-205">功能的組織</span><span class="sxs-lookup"><span data-stu-id="e4a2e-205">Feature Organization</span></span>

<span data-ttu-id="e4a2e-206">根據預設，ASP.NET Core 應用程式會組織包含控制器和檢視，和經常 ViewModels 及其資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-206">By default, ASP.NET Core applications organize their folder structure to include Controllers and Views, and frequently ViewModels.</span></span> <span data-ttu-id="e4a2e-207">用戶端程式碼來支援這些伺服器端結構通常會儲存個別的 wwwroot 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-207">Client-side code to support these server-side structures is typically stored separately in the wwwroot folder.</span></span> <span data-ttu-id="e4a2e-208">不過，大型應用程式可能會遇到向此組織中，問題，因為通常使用任何特定功能需要這些資料夾間跳躍。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-208">However, large applications may encounter problems with this organization, since working on any given feature often requires jumping between these folders.</span></span> <span data-ttu-id="e4a2e-209">這會取得越來越多的每個資料夾中檔案和資料夾數目增加時，導致大量的方案總管 中捲動困難。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-209">This gets more and more difficult as the number of files and subfolders in each folder grows, resulting in a great deal of scrolling through Solution Explorer.</span></span> <span data-ttu-id="e4a2e-210">這個問題的其中一個解決方案是將應用程式程式碼的組織*功能*而不是由檔案類型。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-210">One solution to this problem is to organize application code by *feature* instead of by file type.</span></span> <span data-ttu-id="e4a2e-211">此組織樣式通常稱為資料夾功能或功能配量 (請參閱：[垂直配量](http://deviq.com/vertical-slices/))。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-211">This organizational style is typically referred to as feature folders or feature slices (see also: [Vertical Slices](http://deviq.com/vertical-slices/)).</span></span>

<span data-ttu-id="e4a2e-212">ASP.NET Core MVC 支援針對此用途的區域。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-212">ASP.NET Core MVC supports Areas for this purpose.</span></span> <span data-ttu-id="e4a2e-213">使用區域，您可以建立不同的控制器和檢視資料夾 （以及任何相關聯的模型） 中每個區域的資料夾集。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-213">Using areas, you can create separate sets of Controllers and Views folders (as well as any associated models) in each Area folder.</span></span> <span data-ttu-id="e4a2e-214">圖 7-1 顯示使用區域的範例資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-214">Figure 7-1 shows an example folder structure, using Areas.</span></span>

![](./media/image7-1.png)

<span data-ttu-id="e4a2e-215">圖 7-1 範例區域組織</span><span class="sxs-lookup"><span data-stu-id="e4a2e-215">Figure 7-1 Sample Area Organization</span></span>

<span data-ttu-id="e4a2e-216">當使用區域，您必須使用屬性裝飾的控制站與它們所隸屬之區域的名稱：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-216">When using Areas, you must use attributes to decorate your controllers with the name of the area to which they belong:</span></span>

```csharp
[Area("Catalog")]
public class HomeController
{}
```

<span data-ttu-id="e4a2e-217">您也需要將區域支援加入至您的路由：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-217">You also need to add area support to your routes:</span></span>

```csharp
app.UseMvc(routes =>
{
    // Areas support
    routes.MapRoute(
    name: "areaRoute",
    template: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    routes.MapRoute(
    name: "default",
    template: "{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="e4a2e-218">除了區域的內建支援，您也可以使用自己的資料夾結構和慣例，來取代屬性和自訂路由。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-218">In addition to the built-in support for Areas, you can also use your own folder structure, and conventions in place of attributes and custom routes.</span></span> <span data-ttu-id="e4a2e-219">這樣可讓您能夠檢視、 控制站等，保留更平面的階層架構，更輕鬆查看所有相關的每項功能在單一位置的檔案未包含不同的資料夾的功能資料夾。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-219">This would allow you to have feature folders that didn't include separate folders for Views, Controllers, etc., keeping the hierarchy flatter and making it easier to see all related files in a single place for each feature.</span></span>

<span data-ttu-id="e4a2e-220">ASP.NET Core 使用內建的慣例類型，來控制其行為。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-220">ASP.NET Core uses built-in convention types to control its behavior.</span></span> <span data-ttu-id="e4a2e-221">您可以修改或取代這些慣例。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-221">You can modify or replace these conventions.</span></span> <span data-ttu-id="e4a2e-222">例如，您可以建立會自動收到根據命名空間 （這通常相互關聯控制站所在的資料夾） 指定之控制器的功能名稱的慣例：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-222">For example, you can create a convention that will automatically get the feature name for a given controller based on its namespace (which typically correlates to the folder in which the controller is located):</span></span>

```csharp
FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

<span data-ttu-id="e4a2e-223">您再指定此慣例做為選項的 MVC 支援加入應用程式中 ConfigureServices 時：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-223">You then specify this convention as an option when you add support for MVC to your application in ConfigureServices:</span></span>

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

<span data-ttu-id="e4a2e-224">ASP.NET Core MVC 也使用的慣例，來找出檢視。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-224">ASP.NET Core MVC also uses a convention to locate views.</span></span> <span data-ttu-id="e4a2e-225">您可以覆寫它以自訂的慣例，以便檢視會位於功能資料夾 （使用上面 FeatureConvention 所提供的功能名稱）。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-225">You can override it with a custom convention so that views will be located in your feature folders (using the feature name provided by the FeatureConvention, above).</span></span> <span data-ttu-id="e4a2e-226">您可以深入了解這種方法，並從 MSDN 文章中，下載工作範例[功能配量的 ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-226">You can learn more about this approach and download a working sample from the MSDN article, [Feature Slices for ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span></span>

### <a name="cross-cutting-concerns"></a><span data-ttu-id="e4a2e-227">跨領域關注</span><span class="sxs-lookup"><span data-stu-id="e4a2e-227">Cross-Cutting Concerns</span></span>

<span data-ttu-id="e4a2e-228">當應用程式成長時，會變得越來越重要分離出來跨領域考量，以消除重複，並維持一致性。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-228">As applications grow, it becomes increasingly important to factor out cross-cutting concerns to eliminate duplication and maintain consistency.</span></span> <span data-ttu-id="e4a2e-229">跨領域考量 ASP.NET Core 應用程式中的一些範例是驗證、 模型的驗證規則、 輸出快取和錯誤處理，雖然還有許多其他。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-229">Some examples of cross-cutting concerns in ASP.NET Core applications are authentication, model validation rules, output caching, and error handling, though there are many others.</span></span> <span data-ttu-id="e4a2e-230">ASP.NET Core MVC[篩選](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters)可讓您執行程式碼之前或之後要求處理管線中的特定步驟。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-230">ASP.NET Core MVC [filters](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) allow you to run code before or after certain steps in the request processing pipeline.</span></span> <span data-ttu-id="e4a2e-231">例如，篩選可以執行之前和之後模型繫結、 之前和之後的動作，或之前和之後的動作結果。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-231">For instance, a filter can run before and after model binding, before and after an action, or before and after an action's result.</span></span> <span data-ttu-id="e4a2e-232">您也可以使用授權篩選條件來控制存取其餘的管線。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-232">You can also use an authorization filter to control access to the rest of the pipeline.</span></span> <span data-ttu-id="e4a2e-233">如果設定數字 7-2 會顯示如何篩選器，透過要求執行流程。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-233">Figures 7-2 shows how request execution flows through filters, if configured.</span></span>

![要求處理會歷經授權篩選條件、資源篩選條件、模型繫結、動作篩選條件、動作執行和動作結果轉換、例外狀況篩選條件、結果篩選條件，以及結果執行。](./media/image7-2.png)

<span data-ttu-id="e4a2e-236">圖 7-2 要求執行透過篩選器和要求管線。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-236">Figure 7-2 Request execution through filters and request pipeline.</span></span>

<span data-ttu-id="e4a2e-237">篩選條件通常實作為屬性，以便您可以套用它們控制器或動作。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-237">Filters are usually implemented as attributes, so you can apply them controllers or actions.</span></span> <span data-ttu-id="e4a2e-238">當以這種方式，在動作層級覆寫或組建控制器層級上指定的篩選器時指定的篩選條件加入本身的覆寫全域篩選。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-238">When added in this fashion, filters specified at the action level override or build upon filters specified at the controller level, which themselves override global filters.</span></span> <span data-ttu-id="e4a2e-239">例如，\[路由\]屬性可以用來建置控制器和動作之間的路由。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-239">For example, the \[Route\] attribute can be used to build up routes between controllers and actions.</span></span> <span data-ttu-id="e4a2e-240">同樣地，授權可以在控制器層級設定，然後覆寫個別的動作，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-240">Likewise, authorization can be configured at the controller level, and then overridden by individual actions, as the following sample demonstrates:</span></span>

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

<span data-ttu-id="e4a2e-241">第一個方法，也就是登入，會使用 AllowAnonymous 篩選條件 （屬性），來覆寫在控制器層級設定的授權篩選。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-241">The first method, Login, uses the AllowAnonymous filter (attribute) to override the Authorize filter set at the controller level.</span></span> <span data-ttu-id="e4a2e-242">ForgotPassword 動作 （和沒有 AllowAnonymous 屬性的類別中的任何其他動作），將需要已驗證的要求。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-242">The ForgotPassword action (and any other action in the class that doesn't have an AllowAnonymous attribute) will require an authenticated request.</span></span>

<span data-ttu-id="e4a2e-243">可以使用篩選器，以消除重複的常見的錯誤處理原則的應用程式開發介面的形式。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-243">Filters can be used to eliminate duplication in the form of common error handling policies for APIs.</span></span> <span data-ttu-id="e4a2e-244">比方說，一般的 API 原則會傳回找不到回應要求參考索引鍵不存在，並不正確的要求回應，如果模型驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-244">For example, a typical API policy is to return a NotFound response to requests referencing keys that do not exist, and a BadRequest response if model validation fails.</span></span> <span data-ttu-id="e4a2e-245">下列範例會示範這些動作中的兩個原則：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-245">The following example demonstrates these two policies in action:</span></span>

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="e4a2e-246">不允許您的動作方法，就會散布與條件式程式碼如下。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-246">Don't allow your action methods to become cluttered with conditional code like this.</span></span> <span data-ttu-id="e4a2e-247">相反地，提取到可以做為所需的基礎套用的篩選條件的原則。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-247">Instead, pull the policies into filters that can be applied on an as-needed basis.</span></span> <span data-ttu-id="e4a2e-248">在此範例中，模型的驗證檢查，應該將命令傳送給 API 的任何時間，可能會取代下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-248">In this example, the model validation check, which should occur any time a command is sent to the API, can be replaced by the following attribute:</span></span>

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

<span data-ttu-id="e4a2e-249">同樣地，篩選可以用來檢查記錄是否存在，且之前執行的動作，因而不須執行這些檢查的動作中傳回 404。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-249">Likewise, a filter can be used to check if a record exists and return a 404 before the action is executed, eliminating the need to perform these checks in the action.</span></span> <span data-ttu-id="e4a2e-250">拉出一般慣例並組織您的解決方案基礎結構程式碼和商務邏輯分開 UI 之後，應該是極精簡您的 MVC 動作方法：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-250">Once you've pulled out common conventions and organized your solution to separate infrastructure code and business logic from your UI, your MVC action methods should be extremely thin:</span></span>

```csharp
// PUT api/authors/2/5
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="e4a2e-251">閱讀更多有關執行篩選器與 MSDN 文章中，從下載的工作範例[真實世界 ASP.NET Core MVC 篩選條件](https://msdn.microsoft.com/magazine/mt767699.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-251">You can read more about implementing filters and download a working sample from the MSDN article, [Real World ASP.NET Core MVC Filters](https://msdn.microsoft.com/magazine/mt767699.aspx).</span></span>

> ### <a name="references--structuring-applications"></a><span data-ttu-id="e4a2e-252">參考 – 建構應用程式</span><span class="sxs-lookup"><span data-stu-id="e4a2e-252">References – Structuring Applications</span></span>
> - <span data-ttu-id="e4a2e-253">**區域**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-253">**Areas**</span></span>  
> <span data-ttu-id="e4a2e-254"><https://docs.microsoft.com/aspnet/core/mvc/controllers/areas></span><span class="sxs-lookup"><span data-stu-id="e4a2e-254"><https://docs.microsoft.com/aspnet/core/mvc/controllers/areas></span></span>
> - <span data-ttu-id="e4a2e-255">**MSDN – 適用於 ASP.NET Core MVC 功能配量**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx></span><span class="sxs-lookup"><span data-stu-id="e4a2e-255">**MSDN – Feature Slices for ASP.NET Core MVC**
<https://msdn.microsoft.com/magazine/mt763233.aspx></span></span>
> - <span data-ttu-id="e4a2e-256">**篩選**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-256">**Filters**</span></span>  
> <span data-ttu-id="e4a2e-257"><https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span><span class="sxs-lookup"><span data-stu-id="e4a2e-257"><https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span></span>
> - <span data-ttu-id="e4a2e-258">**MSDN – 真實世界 ASP.NET Core MVC 篩選條件**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-258">**MSDN – Real World ASP.NET Core MVC Filters**</span></span>  
> <span data-ttu-id="e4a2e-259"><https://msdn.microsoft.com/magazine/mt767699.aspx></span><span class="sxs-lookup"><span data-stu-id="e4a2e-259"><https://msdn.microsoft.com/magazine/mt767699.aspx></span></span>

## <a name="security"></a><span data-ttu-id="e4a2e-260">安全性</span><span class="sxs-lookup"><span data-stu-id="e4a2e-260">Security</span></span>

<span data-ttu-id="e4a2e-261">保護 web 應用程式是大型的主題中，但許多考量。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-261">Securing web applications is a large topic, with many considerations.</span></span> <span data-ttu-id="e4a2e-262">在其最基本的層級安全性牽涉到確保您知道誰給定的要求是來自，，然後確保該要求只具有其應有的資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-262">At its most basic level, security involves ensuring you know who a given request is coming from, and then ensuring that that request only has access to resources it should.</span></span> <span data-ttu-id="e4a2e-263">驗證是比較使用受信任的資料存放區中的要求，請參閱是否要求應該被視為來自已知的實體提供認證的程序。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-263">Authentication is the process of comparing credentials provided with a request to those in a trusted data store, to see if the request should be treated as coming from a known entity.</span></span> <span data-ttu-id="e4a2e-264">授權是限制存取特定資源，根據使用者識別的程序。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-264">Authorization is the process of restricting access to certain resources based on user identity.</span></span> <span data-ttu-id="e4a2e-265">第三個安全性問題從第三方，其至少應該竊聽保護要求[確保您的應用程式使用 SSL](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl)。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-265">A third security concern is protecting requests from eavesdropping by third parties, for which you should at least [ensure that SSL is used by your application](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).</span></span>

### <a name="authentication"></a><span data-ttu-id="e4a2e-266">驗證</span><span class="sxs-lookup"><span data-stu-id="e4a2e-266">Authentication</span></span>

<span data-ttu-id="e4a2e-267">您可以使用來支援您的應用程式的登入功能的成員資格系統 ASP.NET Core 識別。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-267">ASP.NET Core Identity is a membership system you can use to support login functionality for your application.</span></span> <span data-ttu-id="e4a2e-268">它具有支援本機使用者帳戶以及外部登入提供者支援的提供者的 Microsoft 帳戶、 Twitter、 Facebook、 Google、 等等。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-268">It has support for local user accounts as well as external login provider support from providers like Microsoft Account, Twitter, Facebook, Google, and more.</span></span> <span data-ttu-id="e4a2e-269">除了 ASP.NET Core 身分識別，您的應用程式可以使用 windows 驗證，或協力廠商身分識別提供者喜歡[Identity Server](https://github.com/IdentityServer/IdentityServer4)。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-269">In addition to ASP.NET Core Identity, your application can use windows authentication, or a third-party identity provider like [Identity Server](https://github.com/IdentityServer/IdentityServer4).</span></span>

<span data-ttu-id="e4a2e-270">如果選取個別的使用者帳戶選項時，ASP.NET Core 識別隨附於新專案範本。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-270">ASP.NET Core Identity is included in new project templates if the Individual User Accounts option is selected.</span></span> <span data-ttu-id="e4a2e-271">此範本包含註冊、 登入、 外部登入、 忘記密碼和其他功能的支援。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-271">This template includes support for registration, login, external logins, forgotten passwords, and additional functionality.</span></span>

![](./media/image7-3.png)

<span data-ttu-id="e4a2e-272">圖 7-3 選取個別使用者帳戶，才能有預先設定的身分識別。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-272">Figure 7-3 Select Individual User Accounts to have Identity preconfigured.</span></span>

<span data-ttu-id="e4a2e-273">識別身分支援設定於啟動時，在 ConfigureServices 和設定：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-273">Identity support is configured in Startup, both in ConfigureServices and Configure:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>()
    .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

<span data-ttu-id="e4a2e-274">請務必 UseIdentity 出現之前 UseMvc 設定方法中。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-274">It's important that UseIdentity appear before UseMvc in the Configure method.</span></span> <span data-ttu-id="e4a2e-275">在設定時識別 ConfigureServices，您會發現 AddDefaultTokenProviders 呼叫。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-275">When configuring Identity in ConfigureServices, you'll notice a call to AddDefaultTokenProviders.</span></span> <span data-ttu-id="e4a2e-276">這會有與語彙基元可用於安全 web 通訊，但改為建立可傳送給透過 SMS 或電子郵件中，以確認其身分的使用者提示的提供者是指無關。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-276">This has nothing to do with tokens that may be used to secure web communications, but instead refers to providers that create prompts that can be sent to users via SMS or email in order for them to confirm their identity.</span></span>

<span data-ttu-id="e4a2e-277">您可以深入了解[設定雙因素驗證](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)和[啟用外部登入提供者](https://docs.microsoft.com/aspnet/core/security/authentication/social/)從官方 ASP.NET Core 文件。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-277">You can learn more about [configuring two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) and [enabling external login providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) from the official ASP.NET Core docs.</span></span>

### <a name="authorization"></a><span data-ttu-id="e4a2e-278">授權</span><span class="sxs-lookup"><span data-stu-id="e4a2e-278">Authorization</span></span>

<span data-ttu-id="e4a2e-279">授權的最簡單形式牽涉到限制匿名使用者存取。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-279">The simplest form of authorization involves restricting access to anonymous users.</span></span> <span data-ttu-id="e4a2e-280">這可藉由將只要套用\[授權\]屬性到特定的控制器或動作。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-280">This can be achieved by simply applying the \[Authorize\] attribute to certain controllers or actions.</span></span> <span data-ttu-id="e4a2e-281">如果角色正在使用中，屬性可以進一步擴充使用者屬於特定角色，限制存取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-281">If roles are being used, the attribute can be further extended to restrict access to users who belong to certain roles, as shown:</span></span>

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

<span data-ttu-id="e4a2e-282">在此情況下，屬於 HRManager 或財務角色 （或兩者） 的使用者將會讓 SalaryController 存取。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-282">In this case, users belonging to either the HRManager or Finance roles (or both) would have access to the SalaryController.</span></span> <span data-ttu-id="e4a2e-283">若要要求使用者屬於多個角色 （不只是其中幾個），您可以套用的屬性多次，每次指定必要的角色。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-283">To require that a user belong to multiple roles (not just one of several), you can apply the attribute multiple times, specifying a required role each time.</span></span>

<span data-ttu-id="e4a2e-284">指定組特定的角色，因為在許多不同的控制器和動作的字串會導致非預期的重複。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-284">Specifying certain sets of roles as strings in many different controllers and actions can lead to undesirable repetition.</span></span> <span data-ttu-id="e4a2e-285">您可以設定授權原則，封裝授權規則，，然後在套用時指定的原則，而不是個別角色\[授權\]屬性：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-285">You can configure authorization policies, which encapsulate authorization rules, and then specify the policy instead of individual roles when applying the \[Authorize\] attribute:</span></span>

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

<span data-ttu-id="e4a2e-286">使用原則，如此一來，您可以分隔的一種限制從特定角色或套用至該規則的動作。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-286">Using policies in this way, you can separate the kinds of actions being restricted from the specific roles or rules that apply to it.</span></span> <span data-ttu-id="e4a2e-287">稍後，如果您建立新的角色必須要有特定資源的存取權，您可以只更新原則，而不是更新角色的每個清單上每個\[授權\]屬性。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-287">Later, if you create a new role that needs to have access to certain resources, you can just update a policy, rather than updating every list of roles on every \[Authorize\] attribute.</span></span>

#### <a name="claims"></a><span data-ttu-id="e4a2e-288">宣告</span><span class="sxs-lookup"><span data-stu-id="e4a2e-288">Claims</span></span>

<span data-ttu-id="e4a2e-289">宣告是使用者的名稱/值組代表屬性的已驗證。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-289">Claims are name value pairs that represent properties of an authenticated user.</span></span> <span data-ttu-id="e4a2e-290">例如，您可能會宣告的形式儲存使用者的員工數目。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-290">For example, you might store users' employee number as a claim.</span></span> <span data-ttu-id="e4a2e-291">宣告可用做為授權原則的一部分。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-291">Claims can then be used as part of authorization policies.</span></span> <span data-ttu-id="e4a2e-292">您可以建立稱為 「 EmployeeOnly 」 原則，需要有的宣告，稱為 「 EmployeeNumber"，如本範例所示：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-292">You could create a policy called "EmployeeOnly" that requires the existence of a claim called "EmployeeNumber", as shown in this example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

<span data-ttu-id="e4a2e-293">這個原則無法再搭配\[授權\]來保護任何控制器和/或動作，如上面所述的屬性。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-293">This policy could then be used with the \[Authorize\] attribute to protect any controller and/or action, as described above.</span></span>

#### <a name="securing-web-apis"></a><span data-ttu-id="e4a2e-294">保護 Web 應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="e4a2e-294">Securing Web APIs</span></span>

<span data-ttu-id="e4a2e-295">大部分 web 應用程式開發介面應該實作權杖為基礎的驗證系統。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-295">Most web APIs should implement a token-based authentication system.</span></span> <span data-ttu-id="e4a2e-296">無狀態而設計，可調整權杖驗證。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-296">Token authentication is stateless and designed to be scalable.</span></span> <span data-ttu-id="e4a2e-297">在權杖為基礎的驗證系統中，用戶端必須先通過驗證的驗證提供者。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-297">In a token-based authentication system, the client must first authenticate with the authentication provider.</span></span> <span data-ttu-id="e4a2e-298">如果成功，用戶端會發出的權杖，只是密碼編譯方面有意義的字元字串。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-298">If successful, the client is issued a token, which is simply a cryptographically meaningful string of characters.</span></span> <span data-ttu-id="e4a2e-299">當用戶端再需要發出要求，應用程式開發介面時，它會做為要求標頭加入這個語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-299">When the client then needs to issue a request to an API, it adds this token as a header on the request.</span></span> <span data-ttu-id="e4a2e-300">伺服器接著會驗證之前完成要求，要求標頭中找到的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-300">The server then validates the token found in the request header before completing the request.</span></span> <span data-ttu-id="e4a2e-301">圖 7-4 將示範此程序。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-301">Figure 7-4 demonstrates this process.</span></span>

![TokenAuth](./media/image7-4.png)

<span data-ttu-id="e4a2e-303">**圖 7-4。**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-303">**Figure 7-4.**</span></span> <span data-ttu-id="e4a2e-304">Web api 的權杖型驗證。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-304">Token-based authentication for Web APIs.</span></span>

> ### <a name="references--security"></a><span data-ttu-id="e4a2e-305">參考 – 安全性</span><span class="sxs-lookup"><span data-stu-id="e4a2e-305">References – Security</span></span>
> - <span data-ttu-id="e4a2e-306">**安全性文件概觀**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-306">**Security Docs Overview**</span></span>  
> <span data-ttu-id="e4a2e-307">https://docs.microsoft.com/aspnet/core/security/</span><span class="sxs-lookup"><span data-stu-id="e4a2e-307">https://docs.microsoft.com/aspnet/core/security/</span></span>
> - <span data-ttu-id="e4a2e-308">**強制執行的 ASP.NET Core 應用程式中的 SSL**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-308">**Enforcing SSL in an ASP.NET Core App**</span></span>  
> <span data-ttu-id="e4a2e-309"><https://docs.microsoft.com/aspnet/core/security/enforcing-ssl></span><span class="sxs-lookup"><span data-stu-id="e4a2e-309"><https://docs.microsoft.com/aspnet/core/security/enforcing-ssl></span></span>
> - <span data-ttu-id="e4a2e-310">**身分識別簡介**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-310">**Introduction to Identity**</span></span>  
> <span data-ttu-id="e4a2e-311"><https://docs.microsoft.com/aspnet/core/security/authentication/identity></span><span class="sxs-lookup"><span data-stu-id="e4a2e-311"><https://docs.microsoft.com/aspnet/core/security/authentication/identity></span></span>
> - <span data-ttu-id="e4a2e-312">**授權簡介**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-312">**Introduction to Authorization**</span></span>  
> <span data-ttu-id="e4a2e-313"><https://docs.microsoft.com/aspnet/core/security/authorization/introduction></span><span class="sxs-lookup"><span data-stu-id="e4a2e-313"><https://docs.microsoft.com/aspnet/core/security/authorization/introduction></span></span>
> - <span data-ttu-id="e4a2e-314">**在 Azure App Service API 應用程式的驗證和授權**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-314">**Authentication and Authorization for API Apps in Azure App Service**</span></span>  
> <span data-ttu-id="e4a2e-315"><https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication></span><span class="sxs-lookup"><span data-stu-id="e4a2e-315"><https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication></span></span>

## <a name="client-communication"></a><span data-ttu-id="e4a2e-316">用戶端通訊</span><span class="sxs-lookup"><span data-stu-id="e4a2e-316">Client Communication</span></span>

<span data-ttu-id="e4a2e-317">除了網頁和 web 應用程式開發介面透過資料的要求回應，ASP.NET Core 應用程式可以直接與連線的用戶端通訊。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-317">In addition to serving pages and responding to requests for data via web APIs, ASP.NET Core apps can communicate directly with connected clients.</span></span> <span data-ttu-id="e4a2e-318">此輸出的通訊都可以使用各種傳輸技術，最常見的是 WebSockets。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-318">This outbound communication can use a variety of transport technologies, the most common being WebSockets.</span></span> <span data-ttu-id="e4a2e-319">ASP.NET Core SignalR 是程式庫，可簡化種類的應用程式伺服器到用戶端上的通訊功能。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-319">ASP.NET Core SignalR is a library that makes it simple to kind of real-time server-to-client communication functionality to your applications.</span></span> <span data-ttu-id="e4a2e-320">SignalR 支援各種不同的傳輸技術，包括 WebSockets，並將實作細節，從開發人員抽離多抽象化出來。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-320">SignalR supports a variety of transport technologies, including WebSockets, and abstracts away many of the implementation details from the developer.</span></span>

<span data-ttu-id="e4a2e-321">ASP.NET Core SignalR 目前正在進行程式開發，並將可在 ASP.NET Core 的下一個版本。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-321">ASP.NET Core SignalR is currently under development, and will be available in the next release of ASP.NET Core.</span></span> <span data-ttu-id="e4a2e-322">不過，其他[開啟原始碼 WebSockets 程式庫](https://github.com/radu-matei/websocket-manager)目前可用。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-322">However, other [open source WebSockets libraries](https://github.com/radu-matei/websocket-manager) are currently available.</span></span>

<span data-ttu-id="e4a2e-323">即時的用戶端通訊，是否使用 WebSockets 直接或其他技術，可用於各種不同的應用程式案例。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-323">Real-time client communication, whether using WebSockets directly or other techniques, are useful in a variety of application scenarios.</span></span> <span data-ttu-id="e4a2e-324">其中某些範例包括：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-324">Some examples include:</span></span>

-   <span data-ttu-id="e4a2e-325">聊天室的即時應用程式</span><span class="sxs-lookup"><span data-stu-id="e4a2e-325">Live chat room applications</span></span>

-   <span data-ttu-id="e4a2e-326">監視應用程式</span><span class="sxs-lookup"><span data-stu-id="e4a2e-326">Monitoring applications</span></span>

-   <span data-ttu-id="e4a2e-327">工作進度更新</span><span class="sxs-lookup"><span data-stu-id="e4a2e-327">Job progress updates</span></span>

-   <span data-ttu-id="e4a2e-328">通知</span><span class="sxs-lookup"><span data-stu-id="e4a2e-328">Notifications</span></span>

-   <span data-ttu-id="e4a2e-329">互動式 forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="e4a2e-329">Interactive forms applications</span></span>

<span data-ttu-id="e4a2e-330">當建置到應用程式的用戶端通訊時，是通常兩個元件：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-330">When building client communication into your applications, there are typically two components:</span></span>

-   <span data-ttu-id="e4a2e-331">伺服器端連接管理員 （SignalR 中樞，WebSocketManager WebSocketHandler）</span><span class="sxs-lookup"><span data-stu-id="e4a2e-331">Server-side connection manager (SignalR Hub, WebSocketManager WebSocketHandler)</span></span>

-   <span data-ttu-id="e4a2e-332">用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="e4a2e-332">Client-side library</span></span>

<span data-ttu-id="e4a2e-333">用戶端並不限於瀏覽器 – 行動裝置應用程式、 主控台應用程式和其他原生應用程式也可以使用 SignalR/WebSockets 來通訊。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-333">Clients are not limited to browsers – mobile apps, console apps, and other native apps can also communicate using SignalR/WebSockets.</span></span> <span data-ttu-id="e4a2e-334">下列簡單程式會回應所有內容傳送到交談應用程式主控台中，做為 WebSocketManager 範例應用程式的一部分：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-334">The following simple program echoes all content sent to a chat application to the console, as part of a WebSocketManager sample application:</span></span>

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>;
        {
            Console.WriteLine(\$"{arguments\[0\]} said: {arguments\[1\]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }
    
    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }
    
    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
```

<span data-ttu-id="e4a2e-335">請考慮的方式應用程式直接與用戶端應用程式，並考慮是否即時通訊將會提升應用程式的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-335">Consider ways in which your applications communicate directly with client applications, and consider whether real-time communication would improve your app's user experience.</span></span>

> ### <a name="references--client-communication"></a><span data-ttu-id="e4a2e-336">參考 – 用戶端通訊</span><span class="sxs-lookup"><span data-stu-id="e4a2e-336">References – Client Communication</span></span>
> - <span data-ttu-id="e4a2e-337">**ASP.NET Core SignalR**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-337">**ASP.NET Core SignalR**</span></span>  
> <span data-ttu-id="e4a2e-338"><https://github.com/aspnet/SignalR></span><span class="sxs-lookup"><span data-stu-id="e4a2e-338"><https://github.com/aspnet/SignalR></span></span>
> - <span data-ttu-id="e4a2e-339">**WebSocket Manager**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-339">**WebSocket Manager**</span></span>  
> <span data-ttu-id="e4a2e-340">https://github.com/radu-matei/websocket-manager</span><span class="sxs-lookup"><span data-stu-id="e4a2e-340">https://github.com/radu-matei/websocket-manager</span></span>

## <a name="domain-driven-design--should-you-apply-it"></a><span data-ttu-id="e4a2e-341">網域導向設計 – 應該套用嗎？</span><span class="sxs-lookup"><span data-stu-id="e4a2e-341">Domain-Driven Design – Should You Apply It?</span></span>

<span data-ttu-id="e4a2e-342">網域導向設計 (DDD) 是建置軟體強調將焦點放在敏捷式軟體開發方法*商務網域*。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-342">Domain-Driven Design (DDD) is an agile approach to building software that emphasizes focusing on the *business domain*.</span></span> <span data-ttu-id="e4a2e-343">就會將重點通訊以及與商務網域 expert(s) 者可以與開發人員提供實際系統的運作方式的互動。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-343">It places a heavy emphasis on communication and interaction with business domain expert(s) who can relate to the developers how the real-world system works.</span></span> <span data-ttu-id="e4a2e-344">比方說，如果您正在建置處理股票交易系統，您的網域專家可能經驗豐富的內建 broker。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-344">For example, if you're building a system that handles stock trades, your domain expert might be an experienced stock broker.</span></span> <span data-ttu-id="e4a2e-345">DDD 設計來處理大型、 複雜的商務問題，且通常不適合更小、 更簡單的應用程式，因為了解與模型化的網域中的投資不值得這樣做。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-345">DDD is designed to address large, complex business problems, and is often not appropriate for smaller, simpler applications, as the investment in understanding and modeling the domain is not worth it.</span></span>

<span data-ttu-id="e4a2e-346">您的小組 （包括非技術性的專案關係人和參與者） 建置軟體遵循 DDD 方法時，應該開發*通用語言*問題空間。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-346">When building software following a DDD approach, your team (including non-technical stakeholders and contributors) should develop a *ubiquitous language* for the problem space.</span></span> <span data-ttu-id="e4a2e-347">也就是相同的術語應用於真實世界概念正在模型化、 軟體對等項目，以及可能存在保存概念 （例如，資料庫資料表） 的任何結構。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-347">That is, the same terminology should be used for the real-world concept being modeled, the software equivalent, and any structures that might exist to persist the concept (for example, database tables).</span></span> <span data-ttu-id="e4a2e-348">因此，通用語言中所述的概念應該會促使您*網域模型*。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-348">Thus, the concepts described in the ubiquitous language should form the basis for your *domain model*.</span></span>

<span data-ttu-id="e4a2e-349">網域模型被組成之間的互動來代表系統的行為的物件。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-349">Your domain model is comprised of objects that interact with one another to represent the behavior of the system.</span></span> <span data-ttu-id="e4a2e-350">這些物件可能會分成下列類別：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-350">These objects may fall into the following categories:</span></span>

-   <span data-ttu-id="e4a2e-351">[實體](http://deviq.com/entity/)，代表與身分識別的執行緒的物件。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-351">[Entities](http://deviq.com/entity/), which represent objects with a thread of identity.</span></span> <span data-ttu-id="e4a2e-352">實體通常儲存在持續性索引鍵，它們可以稍後擷取。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-352">Entities are typically stored in persistence with a key by which they can later be retrieved.</span></span>

-   <span data-ttu-id="e4a2e-353">[彙總](http://deviq.com/aggregate-pattern/)，代表應該保存做為一個單位的物件群組。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-353">[Aggregates](http://deviq.com/aggregate-pattern/), which represent groups of objects that should be persisted as a unit.</span></span>

-   <span data-ttu-id="e4a2e-354">[值物件](http://deviq.com/value-object/)，代表可以根據其屬性值的總和比較的概念。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-354">[Value objects](http://deviq.com/value-object/), which represent concepts that can be compared on the basis of the sum of their property values.</span></span> <span data-ttu-id="e4a2e-355">例如，DateRange 組成的開始和結束日期。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-355">For example, DateRange consisting of a start and end date.</span></span>

-   <span data-ttu-id="e4a2e-356">[網域事件](https://martinfowler.com/eaaDev/DomainEvent.html)，這表示系統中發生的情況有興趣系統其他部分。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-356">[Domain events](https://martinfowler.com/eaaDev/DomainEvent.html), which represent things happening within the system that are of interest to other parts of the system.</span></span>

<span data-ttu-id="e4a2e-357">請注意 DDD 網域模型，應該將封裝複雜的模型中的行為。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-357">Note that a DDD domain model should encapsulate complex behavior within the model.</span></span> <span data-ttu-id="e4a2e-358">實體，特別是，不只是應該屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-358">Entities, in particular, should not merely be collections of properties.</span></span> <span data-ttu-id="e4a2e-359">當網域模型缺少行為，而且只是代表系統的狀態時，它會稱為[anemic 模型](http://deviq.com/anemic-model/)，也就是 DDD，不需要。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-359">When the domain model lacks behavior and merely represents the state of the system, it is said to be an [anemic model](http://deviq.com/anemic-model/), which is undesirable in DDD.</span></span>

<span data-ttu-id="e4a2e-360">除了這些模型型別，DDD，通常採用各種不同的模式：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-360">In addition to these model types, DDD typically employs a variety of patterns:</span></span>

-   <span data-ttu-id="e4a2e-361">[儲存機制](http://deviq.com/repository-pattern/)，抽象持續性的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-361">[Repository](http://deviq.com/repository-pattern/), for abstracting persistence details.</span></span>

-   <span data-ttu-id="e4a2e-362">[Factory](https://en.wikipedia.org/wiki/Factory_method_pattern)，封裝建立複雜的物件。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-362">[Factory](https://en.wikipedia.org/wiki/Factory_method_pattern), for encapsulating complex object creation.</span></span>

-   <span data-ttu-id="e4a2e-363">網域事件，如分離相依觸發行為的行為。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-363">Domain events, for decoupling dependent behavior from triggering behavior.</span></span>

-   <span data-ttu-id="e4a2e-364">[服務](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)、 封裝複雜的行為和 （或） 基礎結構的實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-364">[Services](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), for encapsulating complex behavior and/or infrastructure implementation details.</span></span>

-   <span data-ttu-id="e4a2e-365">[命令](https://en.wikipedia.org/wiki/Command_pattern)、 的分離發出命令，以及執行命令本身。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-365">[Command](https://en.wikipedia.org/wiki/Command_pattern), for decoupling issuing commands and executing the command itself.</span></span>

-   <span data-ttu-id="e4a2e-366">[規格](http://deviq.com/specification-pattern/)，封裝查詢詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-366">[Specification](http://deviq.com/specification-pattern/), for encapsulating query details.</span></span>

<span data-ttu-id="e4a2e-367">DDD 也建議使用全新的架構上文所述，允許鬆散偶合、 封裝 （encapsulation） 或驗證程式碼可以輕鬆地使用單元測試。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-367">DDD also recommends the use of the Clean Architecture discussed previously, allowing for loose coupling, encapsulation, and code that can easily be verified using unit tests.</span></span>

### <a name="when-should-you-apply-ddd"></a><span data-ttu-id="e4a2e-368">當您將應該套用 DDD</span><span class="sxs-lookup"><span data-stu-id="e4a2e-368">When Should You Apply DDD</span></span>

<span data-ttu-id="e4a2e-369">DDD 是具備相當適合 （不會有只的技術） 的重要商務複雜的大型應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-369">DDD is well-suited to large applications with significant business (not just technical) complexity.</span></span> <span data-ttu-id="e4a2e-370">應用程式應該需要網域專家知識。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-370">The application should require the knowledge of domain experts.</span></span> <span data-ttu-id="e4a2e-371">在網域模型本身，表示商務規則和互動，只是儲存和擷取從資料存放區的目前狀態的各種記錄之外，應該要有重要行為。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-371">There should be significant behavior in the domain model itself, representing business rules and interactions beyond simply storing and retrieving the current state of various records from data stores.</span></span>

### <a name="when-shouldnt-you-apply-ddd"></a><span data-ttu-id="e4a2e-372">當您不應該套用 DDD</span><span class="sxs-lookup"><span data-stu-id="e4a2e-372">When Shouldn't You Apply DDD</span></span>

<span data-ttu-id="e4a2e-373">DDD 牽涉到投資模型、 架構和可能不會發生的狀況的較小的應用程式或基本上就是只會執行 CRUD （建立/讀取/更新/刪除） 的應用程式的通訊。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-373">DDD involves investments in modeling, architecture, and communication that may not be warranted for smaller applications or applications that are essentially just CRUD (create/read/update/delete).</span></span> <span data-ttu-id="e4a2e-374">如果您選擇接近您的應用程式遵循 DDD，但發現您的網域有使用任何行為 anemic 模型，您可能需要重新思考的方法。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-374">If you choose to approach your application following DDD, but find that your domain has an anemic model with no behavior, you may need to rethink your approach.</span></span> <span data-ttu-id="e4a2e-375">您的應用程式可能不需要 DDD，或是您可能需要其他協助重構您的應用程式封裝在網域模型中，而不是在資料庫或使用者介面中的商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-375">Either your application may not need DDD, or you may need assistance refactoring your application to encapsulate business logic in the domain model, rather than in your database or user interface.</span></span>

<span data-ttu-id="e4a2e-376">混合式方法就是只使用 DDD，交易式或更複雜應用程式的區域，但不是能用於簡單 CRUD 或唯讀狀態的應用程式部分。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-376">A hybrid approach would be to only use DDD for the transactional or more complex areas of the application, but not for simpler CRUD or read-only portions of the application.</span></span> <span data-ttu-id="e4a2e-377">比方說，您核對有彙總的條件約束，如果您要查詢的資料來顯示報表或儀表板的資料視覺化。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-377">For instance, you needn't have the constraints of an Aggregate if you're querying data to display a report or to visualize data for a dashboard.</span></span> <span data-ttu-id="e4a2e-378">是完全可接受具有這類需求的個別、 簡單讀取的模型。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-378">It's perfectly acceptable to have a separate, simpler read model for such requirements.</span></span>

> ### <a name="references--domain-driven-design"></a><span data-ttu-id="e4a2e-379">參考 – 網域導向設計</span><span class="sxs-lookup"><span data-stu-id="e4a2e-379">References – Domain-Driven Design</span></span>
> - <span data-ttu-id="e4a2e-380">**DDD 以純文字的英文 (StackOverflow Answer)**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-380">**DDD in Plain English (StackOverflow Answer)**</span></span>  
> <span data-ttu-id="e4a2e-381"><https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488></span><span class="sxs-lookup"><span data-stu-id="e4a2e-381"><https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488></span></span>

## <a name="deployment"></a><span data-ttu-id="e4a2e-382">部署</span><span class="sxs-lookup"><span data-stu-id="e4a2e-382">Deployment</span></span>

<span data-ttu-id="e4a2e-383">有幾個步驟部署您的 ASP.NET Core 應用程式，不論裝載的過程。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-383">There are a few steps involved in the process of deploying your ASP.NET Core application, regardless of where it will be hosted.</span></span> <span data-ttu-id="e4a2e-384">第一個步驟是發行應用程式，即可使用 dotnet 發行 CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-384">The first step is to publish the application, which can be done using the dotnet publish CLI command.</span></span> <span data-ttu-id="e4a2e-385">這將會編譯應用程式，並將所有指定的資料夾中執行應用程式所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-385">This will compile the application and place all of the files needed to run the application into a designated folder.</span></span> <span data-ttu-id="e4a2e-386">當您從 Visual Studio 部署時，則會自動為您執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-386">When you deploy from Visual Studio, this step is performed for you automatically.</span></span> <span data-ttu-id="e4a2e-387">發行資料夾包含應用程式和其相依性的.exe 和.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-387">The publish folder contains .exe and .dll files for the application and its dependencies.</span></span> <span data-ttu-id="e4a2e-388">獨立應用程式也會包含.NET 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-388">A self-contained application will also include a version of the .NET runtime.</span></span> <span data-ttu-id="e4a2e-389">組態檔、 靜態用戶端資產和 MVC 檢視，也會包含 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-389">ASP.NET Core applications will also include configuration files, static client assets, and MVC views.</span></span>

<span data-ttu-id="e4a2e-390">ASP.NET Core 應用程式是主控台應用程式，必須先啟動時開機伺服器，並重新啟動，如果應用程式 （或伺服器） 損毀。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-390">ASP.NET Core applications are console applications that must be started when the server boots and restarted if the application (or server) crashes.</span></span> <span data-ttu-id="e4a2e-391">程序管理員可用來自動化此程序。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-391">A process manager can be used to automate this process.</span></span> <span data-ttu-id="e4a2e-392">適用於 ASP.NET Core 最常見的程序管理員是 Nginx 和 Apache Linux 和 IIS 上的或在 Windows 上的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-392">The most common process managers for ASP.NET Core are Nginx and Apache on Linux and IIS or Windows Service on Windows.</span></span>

<span data-ttu-id="e4a2e-393">程序管理員，除了 Kestrel web 伺服器中裝載的 ASP.NET Core 應用程式必須使用反向 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-393">In addition to a process manager, ASP.NET Core applications hosted in the Kestrel web server must use a reverse proxy server.</span></span> <span data-ttu-id="e4a2e-394">反向 proxy 伺服器會從網際網路接收 HTTP 要求，並轉送至 Kestrel 後一些初步處理。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-394">A reverse proxy server receives HTTP requests from the internet and forwards them to Kestrel after some preliminary handling.</span></span> <span data-ttu-id="e4a2e-395">反向 proxy 伺服器，則應用程式提供安全性層級和邊緣部署 （公開流量從網際網路） 所需。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-395">Reverse proxy servers provide a layer of security for the application, and are required for edge deployments (exposed to traffic from the Internet).</span></span> <span data-ttu-id="e4a2e-396">Kestrel 相對較新且尚未提供特定攻擊的防禦。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-396">Kestrel is relatively new and does not yet offer defenses against certain attacks.</span></span> <span data-ttu-id="e4a2e-397">Kestrel 也不支援裝載多個應用程式相同的連接埠，因此技術，如 主機標頭不能與它可以讓裝載在相同的連接埠和 IP 位址上的多個應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-397">Kestrel also doesn't support hosting multiple applications on the same port, so techniques like host headers cannot be used with it to enable hosting multiple applications on the same port and IP address.</span></span>

![網際網路 kestrel](./media/image7-5.png)

<span data-ttu-id="e4a2e-399">圖 7-5 Kestrel 中裝載的反向 proxy 伺服器後方的 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e4a2e-399">Figure 7-5 ASP.NET hosted in Kestrel behind a reverse proxy server</span></span>

<span data-ttu-id="e4a2e-400">反向 proxy 可以是很有幫助的另一個案例是安全使用 SSL/HTTPS 的多個應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-400">Another scenario in which a reverse proxy can be helpful is to secure multiple applications using SSL/HTTPS.</span></span> <span data-ttu-id="e4a2e-401">在此情況下，只有反向 proxy 需要設定 SSL。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-401">In this case, only the reverse proxy would need to have SSL configured.</span></span> <span data-ttu-id="e4a2e-402">反向 proxy 伺服器與 Kestrel 之間的通訊無法進行透過 HTTP，如圖 7-6 所示。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-402">Communication between the reverse proxy server and Kestrel could take place over HTTP, as shown in Figure 7-6.</span></span>

![](./media/image7-6.png)

<span data-ttu-id="e4a2e-403">圖 7-6 裝載 HTTPS 保護反向 proxy 伺服器後方的 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e4a2e-403">Figure 7-6 ASP.NET hosted behind an HTTPS-secured reverse proxy server</span></span>

<span data-ttu-id="e4a2e-404">逐漸普及的一種方法是裝載 ASP.NET Core 應用程式在 Docker 容器中，然後可以裝載在本機或雲端裝載部署至 Azure。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-404">An increasingly popular approach is to host your ASP.NET Core application in a Docker container, which then can be hosted locally or deployed to Azure for cloud-based hosting.</span></span> <span data-ttu-id="e4a2e-405">Docker 容器可能包含 Kestrel 上, 執行您應用程式程式碼，並將部署在反向 proxy 伺服器後方，如上所示。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-405">The Docker container could contain your application code, running on Kestrel, and would be deployed behind a reverse proxy server, as shown above.</span></span>

<span data-ttu-id="e4a2e-406">如果您正在裝載您在 Azure 上的應用程式，您可以為專用的虛擬應用裝置中使用 Microsoft Azure 應用程式閘道提供數個服務。</span><span class="sxs-lookup"><span data-stu-id="e4a2e-406">If you're hosting your application on Azure, you can use Microsoft Azure Application Gateway as a dedicated virtual appliance to provide several services.</span></span> <span data-ttu-id="e4a2e-407">除了做為個別的應用程式的反向 proxy 時，應用程式閘道也可以提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="e4a2e-407">In addition to acting as a reverse proxy for individual applications, Application Gateway can also offer the following features:</span></span>

-   <span data-ttu-id="e4a2e-408">HTTP 負載平衡</span><span class="sxs-lookup"><span data-stu-id="e4a2e-408">HTTP load balancing</span></span>

-   <span data-ttu-id="e4a2e-409">SSL 卸載 (SSL，只為網際網路)</span><span class="sxs-lookup"><span data-stu-id="e4a2e-409">SSL offload (SSL only to Internet)</span></span>

-   <span data-ttu-id="e4a2e-410">端對端 SSL</span><span class="sxs-lookup"><span data-stu-id="e4a2e-410">End to End SSL</span></span>

-   <span data-ttu-id="e4a2e-411">多站台的路由 （合併在單一應用程式閘道上的最多 20 個站台）</span><span class="sxs-lookup"><span data-stu-id="e4a2e-411">Multi-site routing (consolidate up to 20 sites on a single Application Gateway)</span></span>

-   <span data-ttu-id="e4a2e-412">Web 應用程式防火牆</span><span class="sxs-lookup"><span data-stu-id="e4a2e-412">Web application firewall</span></span>

-   <span data-ttu-id="e4a2e-413">Websocket 支援</span><span class="sxs-lookup"><span data-stu-id="e4a2e-413">Websocket support</span></span>

-   <span data-ttu-id="e4a2e-414">進階的診斷</span><span class="sxs-lookup"><span data-stu-id="e4a2e-414">Advanced diagnostics</span></span>

<span data-ttu-id="e4a2e-415">*深入了解章 10 中的 Azure 部署選項。*</span><span class="sxs-lookup"><span data-stu-id="e4a2e-415">*Learn more about Azure deployment options in Chapter 10.*</span></span>

> ### <a name="references--deployment"></a><span data-ttu-id="e4a2e-416">參考 – 部署</span><span class="sxs-lookup"><span data-stu-id="e4a2e-416">References – Deployment</span></span>
> - <span data-ttu-id="e4a2e-417">**裝載和部署概觀**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-417">**Hosting and Deployment Overview**</span></span>  
> <span data-ttu-id="e4a2e-418"><https://docs.microsoft.com/aspnet/core/publishing/></span><span class="sxs-lookup"><span data-stu-id="e4a2e-418"><https://docs.microsoft.com/aspnet/core/publishing/></span></span>
> - <span data-ttu-id="e4a2e-419">使用 Kestrel 透過反向 proxy 的時機</span><span class="sxs-lookup"><span data-stu-id="e4a2e-419">**When to use Kestrel with a reverse proxy**</span></span>  
> <span data-ttu-id="e4a2e-420"><https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy></span><span class="sxs-lookup"><span data-stu-id="e4a2e-420"><https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy></span></span>
> - <span data-ttu-id="e4a2e-421">**在 Docker 主機 ASP.NET Core 應用程式**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-421">**Host ASP.NET Core apps in Docker**</span></span>  
> <span data-ttu-id="e4a2e-422"><https://docs.microsoft.com/aspnet/core/publishing/docker></span><span class="sxs-lookup"><span data-stu-id="e4a2e-422"><https://docs.microsoft.com/aspnet/core/publishing/docker></span></span>
> - <span data-ttu-id="e4a2e-423">**介紹 Azure 應用程式閘道**</span><span class="sxs-lookup"><span data-stu-id="e4a2e-423">**Introducing Azure Application Gateway**</span></span>  
> <span data-ttu-id="e4a2e-424"><https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction></span><span class="sxs-lookup"><span data-stu-id="e4a2e-424"><https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="e4a2e-425">[上一個](常見的用戶端-側邊-web-technologies.md) [下一步] (work-with-data-in-asp-net-core-apps.md)</span><span class="sxs-lookup"><span data-stu-id="e4a2e-425">[Previous] (common-client-side-web-technologies.md) [Next] (work-with-data-in-asp-net-core-apps.md)</span></span>
