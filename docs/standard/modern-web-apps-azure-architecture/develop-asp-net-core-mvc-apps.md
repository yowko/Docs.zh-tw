---
title: 開發 ASP.NET Core MVC 應用程式
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | 開發 ASP.NET Core MVC 應用程式
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.openlocfilehash: 59f0d46dadb736ad55e53f6715b7ca1b62e9cec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592401"
---
# <a name="develop-aspnet-core-mvc-apps"></a><span data-ttu-id="80138-103">開發 ASP.NET Core MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="80138-103">Develop ASP.NET Core MVC Apps</span></span>

> <span data-ttu-id="80138-104">「沒必要第一次就做對。</span><span class="sxs-lookup"><span data-stu-id="80138-104">"It's not important to get it right the first time.</span></span> <span data-ttu-id="80138-105">最後做對才重要。」</span><span class="sxs-lookup"><span data-stu-id="80138-105">It's vitally important to get it right the last time."</span></span>  
> <span data-ttu-id="80138-106">_- Andrew Hunt 和 David Thomas_</span><span class="sxs-lookup"><span data-stu-id="80138-106">_- Andrew Hunt and David Thomas_</span></span>

## <a name="summary"></a><span data-ttu-id="80138-107">總結</span><span class="sxs-lookup"><span data-stu-id="80138-107">Summary</span></span>

<span data-ttu-id="80138-108">ASP.NET Core 是跨平台的開放原始碼架構，適用於建置現代化的雲端最佳化 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="80138-108">ASP.NET Core is a cross-platform, open-source framework for building modern cloud-optimized web applications.</span></span> <span data-ttu-id="80138-109">ASP.NET Core 應用程式是輕量型且模組化的，並內建相依性插入支援，以提高可測試性和可維護性。</span><span class="sxs-lookup"><span data-stu-id="80138-109">ASP.NET Core apps are lightweight and modular, with built-in support for dependency injection, enabling in greater testability and maintainability.</span></span> <span data-ttu-id="80138-110">ASP.NET Core 是建置企業級 Web 應用程式的強大架構，其結合 MVC，除了檢視型應用程式，還支援建置現代化 Web API。</span><span class="sxs-lookup"><span data-stu-id="80138-110">Combined with MVC, which supports building modern web APIs in addition to view-based apps, ASP.NET Core is a powerful framework with which to build enterprise web applications.</span></span>

## <a name="mapping-requests-to-responses"></a><span data-ttu-id="80138-111">將要求對應至回應</span><span class="sxs-lookup"><span data-stu-id="80138-111">Mapping Requests to Responses</span></span>

<span data-ttu-id="80138-112">ASP.NET Core 應用程式基本上會將傳入要求對應至傳出回應。</span><span class="sxs-lookup"><span data-stu-id="80138-112">At its heart, ASP.NET Core apps map incoming requests to outgoing responses.</span></span> <span data-ttu-id="80138-113">在低階，這會透過中介軟體來完成，而簡單的 ASP.NET Core 應用程式和微服務可能只包含自訂中介軟體。</span><span class="sxs-lookup"><span data-stu-id="80138-113">At a low level, this is done with middleware, and simple ASP.NET Core apps and microservices may be comprised solely of custom middleware.</span></span> <span data-ttu-id="80138-114">使用 ASP.NET Core MVC 時，您可以工作地更進階一些，從「路由」、「控制器」和「動作」的觀點來思考。</span><span class="sxs-lookup"><span data-stu-id="80138-114">When using ASP.NET Core MVC, you can work at a somewhat higher level, thinking in terms of *routes*, *controllers*, and *actions*.</span></span> <span data-ttu-id="80138-115">每個傳入要求會與應用程式的路由表進行比對，如果找到相符的路由，就會呼叫相關聯的動作方法 (屬於控制器) 來處理要求。</span><span class="sxs-lookup"><span data-stu-id="80138-115">Each incoming request is compared with the application's routing table, and if a matching route is found, the associated action method (belonging to a controller) is called to handle the request.</span></span> <span data-ttu-id="80138-116">如果找不到相符的路由，就會呼叫錯誤處理常式 (在此情況下會傳回 NotFound 結果)。</span><span class="sxs-lookup"><span data-stu-id="80138-116">If no matching route is found, an error handler (in this case, returning a NotFound result) is called.</span></span>

<span data-ttu-id="80138-117">ASP.NET Core MVC 應用程式可以使用慣例路由、屬性路由或兩者。</span><span class="sxs-lookup"><span data-stu-id="80138-117">ASP.NET Core MVC apps can use conventional routes, attribute routes, or both.</span></span> <span data-ttu-id="80138-118">慣例路由是在程式碼中定義，並使用如下列範例所示的語法來指定路由「慣例」：</span><span class="sxs-lookup"><span data-stu-id="80138-118">Conventional routes are defined in code, specifying routing *conventions* using syntax like in the example below:</span></span>

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="80138-119">在此範例中，已將名為 "default" 的路由新增至路由表。</span><span class="sxs-lookup"><span data-stu-id="80138-119">In this example, a route named "default" has been added to the routing table.</span></span> <span data-ttu-id="80138-120">它定義一個路由範本，其中包含 *controller*、*action* 和 *id* 的預留位置。controller 和 action 預留位置已指定預設值 (分別是 "Home" 和 "Index")，而 id 預留位置則是選擇性的 (由於已套用 "?")。</span><span class="sxs-lookup"><span data-stu-id="80138-120">It defines a route template with placeholders for *controller*, *action*, and *id*. The controller and action placeholders have default specified ("Home" and "Index", respectively), and the id placeholder is optional (by virtue of a "?" applied to it).</span></span> <span data-ttu-id="80138-121">此處定義的慣例指出要求的第一個部分應該對應至控制器的名稱，第二個部分對應至動作，而第三個部分 (如果需要) 則會代表 id 參數。</span><span class="sxs-lookup"><span data-stu-id="80138-121">The convention defined here states that the first part of a request should correspond to the name of the controller, the second part to the action, and then if necessary a third part will represent an id parameter.</span></span> <span data-ttu-id="80138-122">慣例路由通常是在應用程式的一個位置定義，例如在啟動類別的 Configure 方法中。</span><span class="sxs-lookup"><span data-stu-id="80138-122">Conventional routes are typically defined in one place for the application, such as in the Configure method in the Startup class.</span></span>

<span data-ttu-id="80138-123">屬性路由會直接套用至控制器和動作，而不是全域指定。</span><span class="sxs-lookup"><span data-stu-id="80138-123">Attribute routes are applied to controllers and actions directly, rather than specified globally.</span></span> <span data-ttu-id="80138-124">其優點在於當您想要查看特定方法時，會更容易搜尋到這些路由，但也表示路由資訊不會保留在應用程式的一個位置。</span><span class="sxs-lookup"><span data-stu-id="80138-124">This has the advantage of making them much more discoverable when you're looking at a particular method, but does mean that routing information is not kept in one place in the application.</span></span> <span data-ttu-id="80138-125">透過屬性路由，您可以輕鬆地為一個動作指定多個路由，並合併控制器與動作之間的路由。</span><span class="sxs-lookup"><span data-stu-id="80138-125">With attribute routes, you can easily specify multiple routes for a given action, as well as combine routes between controllers and actions.</span></span> <span data-ttu-id="80138-126">例如: </span><span class="sxs-lookup"><span data-stu-id="80138-126">For example:</span></span>

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

<span data-ttu-id="80138-127">您可以在 [HttpGet] 和類似屬性上指定路由，避免需要新增個別 [Route\] 屬性。</span><span class="sxs-lookup"><span data-stu-id="80138-127">Routes can be specified on [HttpGet] and similar attributes, avoiding the need to add separate [Route\] attributes.</span></span> <span data-ttu-id="80138-128">屬性路由也可以使用權杖，來減少重複控制器或動作名稱的需求，如下所示：</span><span class="sxs-lookup"><span data-stu-id="80138-128">Attribute routes can also use tokens to reduce the need to repeat controller or action names, as shown below:</span></span>

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

<span data-ttu-id="80138-129">在指定的要求與路由經過比對之後，但呼叫動作方法之前，ASP.NET Core MVC 會在要求上執行[模型繫結](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding)和[模型驗證](https://docs.microsoft.com/aspnet/core/mvc/models/validation)。</span><span class="sxs-lookup"><span data-stu-id="80138-129">Once a given request has been matched to a route, but before the action method is called, ASP.NET Core MVC will perform [model binding](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) and [model validation](https://docs.microsoft.com/aspnet/core/mvc/models/validation) on the request.</span></span> <span data-ttu-id="80138-130">模型繫結會負責將傳入 HTTP 資料轉換成 .NET 類型，以指定為要呼叫之動作方法的參數。</span><span class="sxs-lookup"><span data-stu-id="80138-130">Model binding is responsible for converting incoming HTTP data into the .NET types specified as parameters of the action method to be called.</span></span> <span data-ttu-id="80138-131">例如，如果動作方法必須有 int id 參數，模型繫結會嘗試從要求隨附的值提供此參數。</span><span class="sxs-lookup"><span data-stu-id="80138-131">For example, if the action method expects an int id parameter, model binding will attempt to provide this parameter from a value provided as part of the request.</span></span> <span data-ttu-id="80138-132">若要這樣做，模型繫結會尋找以 POST 形式送出的值、路由本身中的值，以及查詢字串值。</span><span class="sxs-lookup"><span data-stu-id="80138-132">To do so, model binding looks for values in a posted form, values in the route itself, and query string values.</span></span> <span data-ttu-id="80138-133">假設找到 id 值，則會將它轉換成整數，再傳入動作方法。</span><span class="sxs-lookup"><span data-stu-id="80138-133">Assuming an id value is found, it will be converted to an integer before being passed into the action method.</span></span>

<span data-ttu-id="80138-134">在繫結模型之後，但呼叫動作方法之前，會進行模型驗證。</span><span class="sxs-lookup"><span data-stu-id="80138-134">After binding the model but before calling the action method, model validation occurs.</span></span> <span data-ttu-id="80138-135">模型驗證會根據模型類型使用選用屬性，並可協助確保提供的模型物件符合特定資料需求。</span><span class="sxs-lookup"><span data-stu-id="80138-135">Model validation uses optional attributes on the model type, and can help ensure that the provided model object conforms to certain data requirements.</span></span> <span data-ttu-id="80138-136">某些值可能指定為必要，或限制為特定長度或數字範圍等等。如果指定了驗證屬性，但模型不符合其需求，則屬性 ModelState.IsValid 會是 false，而且會將失敗的驗證規則集傳送給提出要求的用戶端。</span><span class="sxs-lookup"><span data-stu-id="80138-136">Certain values may be specified as required, or limited to a certain length or numeric range, etc. If validation attributes are specified but the model does not conform to their requirements, the property ModelState.IsValid will be false, and the set of failing validation rules will be available to send to the client making the request.</span></span>

<span data-ttu-id="80138-137">如果您使用模型驗證，請務必檢查模型是否有效，再執行任何狀態改變命令，以確保您的應用程式不會遭到無效資料損毀。</span><span class="sxs-lookup"><span data-stu-id="80138-137">If you are using model validation, you should be sure to always check that the model is valid before performing any state-altering commands, to ensure your app is not corrupted by invalid data.</span></span> <span data-ttu-id="80138-138">您可以使用[篩選條件](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters)，避免需要在每個動作中新增程式碼來執行此作業。</span><span class="sxs-lookup"><span data-stu-id="80138-138">You can use a [filter](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) to avoid the need to add code for this in every action.</span></span> <span data-ttu-id="80138-139">ASP.NET Core MVC 篩選條件可讓您攔截要求群組，以便可根據目標套用一般原則和跨領域關注。</span><span class="sxs-lookup"><span data-stu-id="80138-139">ASP.NET Core MVC filters offer a way of intercepting groups of requests, so that common policies and cross-cutting concerns can be applied on a targeted basis.</span></span> <span data-ttu-id="80138-140">您可以將篩選條件套用至個別動作、整個控制器，或針對應用程式全域套用。</span><span class="sxs-lookup"><span data-stu-id="80138-140">Filters can be applied to individual actions, whole controllers, or globally for an application.</span></span>

<span data-ttu-id="80138-141">對於 Web API，ASP.NET Core MVC 支援[「內容交涉」](https://docs.microsoft.com/aspnet/core/mvc/models/formatting)，可讓要求指定回應的格式化方式。</span><span class="sxs-lookup"><span data-stu-id="80138-141">For web APIs, ASP.NET Core MVC supports [*content negotiation*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), allowing requests to specify how responses should be formatted.</span></span> <span data-ttu-id="80138-142">根據要求中提供的標頭，傳回資料的動作會將回應格式化為 XML、JSON 或其他支援的格式。</span><span class="sxs-lookup"><span data-stu-id="80138-142">Based on headers provided in the request, actions returning data will format the response in XML, JSON, or another supported format.</span></span> <span data-ttu-id="80138-143">這項功能可讓具有不同資料格式需求的多個用戶端使用相同的 API。</span><span class="sxs-lookup"><span data-stu-id="80138-143">This feature enables the same API to be used by multiple clients with different data format requirements.</span></span>

> ### <a name="references--mapping-requests-to-responses"></a><span data-ttu-id="80138-144">參考資料 - 將要求對應至回應</span><span class="sxs-lookup"><span data-stu-id="80138-144">References – Mapping Requests to Responses</span></span>
> - <span data-ttu-id="80138-145">**路由至控制器動作**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span><span class="sxs-lookup"><span data-stu-id="80138-145">**Routing to Controller Actions**
<https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span></span>
> - <span data-ttu-id="80138-146">**模型繫結**https://docs.microsoft.com/aspnet/core/mvc/models/model-binding</span><span class="sxs-lookup"><span data-stu-id="80138-146">**Model Binding** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding</span></span>
> - <span data-ttu-id="80138-147">**模型驗證**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation></span><span class="sxs-lookup"><span data-stu-id="80138-147">**Model Validation**
<https://docs.microsoft.com/aspnet/core/mvc/models/validation></span></span>
> - <span data-ttu-id="80138-148">**篩選條件**https://docs.microsoft.com/aspnet/core/mvc/controllers/filters</span><span class="sxs-lookup"><span data-stu-id="80138-148">**Filters** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters</span></span>

## <a name="working-with-dependencies"></a><span data-ttu-id="80138-149">使用相依性</span><span class="sxs-lookup"><span data-stu-id="80138-149">Working with Dependencies</span></span>

<span data-ttu-id="80138-150">ASP.NET Core 已內建支援，並在內部使用稱為[相依性插入](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)的技術。</span><span class="sxs-lookup"><span data-stu-id="80138-150">ASP.NET Core has built-in support for and internally makes use of a technique known as [dependency injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="80138-151">相依性插入是在應用程式的不同組件之間啟用鬆散結合的一項技術。</span><span class="sxs-lookup"><span data-stu-id="80138-151">Dependency injection is a technique that enabled loose coupling between different parts of an application.</span></span> <span data-ttu-id="80138-152">建議您啟用鬆散結合，因為它可讓您更輕鬆地隔離應用程式組件，以便進行測試或取代。</span><span class="sxs-lookup"><span data-stu-id="80138-152">Looser coupling is desirable because it makes it easier to isolate parts of the application, allowing for testing or replacement.</span></span> <span data-ttu-id="80138-153">此外，變更應用程式的某個組件，也較不可能會對應用程式的其他地方造成非預期的影響。</span><span class="sxs-lookup"><span data-stu-id="80138-153">It also makes it less likely that a change in one part of the application will have an unexpected impact somewhere else in the application.</span></span> <span data-ttu-id="80138-154">相依性插入是以相依性反轉準則為基礎，而且通常是實現開啟/關閉準則的關鍵。</span><span class="sxs-lookup"><span data-stu-id="80138-154">Dependency injection is based on the dependency inversion principle, and is often key to achieving the open/closed principle.</span></span> <span data-ttu-id="80138-155">當您評估應用程式搭配其相依性的運作情況時，請注意[靜態黏貼](http://deviq.com/static-cling/)程式碼異味，並記住「[New 就是黏附](https://ardalis.com/new-is-glue)」此一箴言。</span><span class="sxs-lookup"><span data-stu-id="80138-155">When evaluating how your application works with its dependencies, beware of the [static cling](http://deviq.com/static-cling/) code smell, and remember the aphorism "[new is glue](https://ardalis.com/new-is-glue)."</span></span>

<span data-ttu-id="80138-156">靜態黏貼發生於您的類別呼叫靜態方法或存取靜態屬性時，並對基礎結構具有副作用或相依性。</span><span class="sxs-lookup"><span data-stu-id="80138-156">Static cling occurs when your classes make calls to static methods, or access static properties, which have side effects or dependencies on infrastructure.</span></span> <span data-ttu-id="80138-157">例如，如果您有一個方法呼叫靜態方法，而該方法接著寫入資料庫，則您的方法會與資料庫緊密結合。</span><span class="sxs-lookup"><span data-stu-id="80138-157">For example, if you have a method that calls a static method, which in turn writes to a database, your method is tightly coupled to the database.</span></span> <span data-ttu-id="80138-158">任何中斷資料庫呼叫的項目都會中斷您的方法。</span><span class="sxs-lookup"><span data-stu-id="80138-158">Anything that breaks that database call will break your method.</span></span> <span data-ttu-id="80138-159">測試這類方法眾所周知很困難，因為這類測試需要商用模擬程式庫來模擬靜態呼叫，或只能透過適當的測試資料庫進行測試。</span><span class="sxs-lookup"><span data-stu-id="80138-159">Testing such methods is notoriously difficult, since such tests either require commercial mocking libraries to mock the static calls, or can only be tested with a test database in place.</span></span> <span data-ttu-id="80138-160">未相依於基礎結構的靜態呼叫 (特別是完全無狀態的呼叫) 可安心呼叫，不會影響結合或可測試性 (將程式碼結合到靜態呼叫本身除外)。</span><span class="sxs-lookup"><span data-stu-id="80138-160">Static calls that don't have any dependence on infrastructure, especially those that are completely stateless, are fine to call and have no impact on coupling or testability (beyond coupling code to the static call itself).</span></span>

<span data-ttu-id="80138-161">許多開發人員了解靜態黏貼和全域狀態的風險，但仍透過直接具現化將其程式碼緊密結合到特定實作。</span><span class="sxs-lookup"><span data-stu-id="80138-161">Many developers understand the risks of static cling and global state, but will still tightly couple their code to specific implementations through direct instantiation.</span></span> <span data-ttu-id="80138-162">「New 就是黏附」是為了提醒此結合，而不是一味譴責使用 New 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="80138-162">"New is glue" is meant to be a reminder of this coupling, and not a general condemnation of the use of the new keyword.</span></span> <span data-ttu-id="80138-163">如同靜態方法呼叫，沒有外部相依性之類型的新執行個體，通常不會將程式碼緊密結合到實作詳細資料或讓測試更困難。</span><span class="sxs-lookup"><span data-stu-id="80138-163">Just as with static method calls, new instances of types that have no external dependencies typically do not tightly couple code to implementation details or make testing more difficult.</span></span> <span data-ttu-id="80138-164">但每次具現化類別，請花點時間想一想，將該特定位置中的特定執行個體進行硬式編碼是否合理，還是最好設計成將執行個體當作相依性來要求。</span><span class="sxs-lookup"><span data-stu-id="80138-164">But each time a class is instantiated, take just a brief moment to consider whether it makes sense to hard-code that specific instance in that particular location, or if it would be a better design to request that instance as a dependency.</span></span>

### <a name="declare-your-dependencies"></a><span data-ttu-id="80138-165">宣告您的相依性</span><span class="sxs-lookup"><span data-stu-id="80138-165">Declare Your Dependencies</span></span>

<span data-ttu-id="80138-166">ASP.NET Core 的建置中心是讓方法和類別宣告其相依性，並以引數來要求這些相依性。</span><span class="sxs-lookup"><span data-stu-id="80138-166">ASP.NET Core is built around having methods and classes declare their dependencies, requesting them as arguments.</span></span> <span data-ttu-id="80138-167">ASP.NET 應用程式通常是在啟動類別中設定，該類別本身已設定為支援多點相依性插入。</span><span class="sxs-lookup"><span data-stu-id="80138-167">ASP.NET applications are typically set up in a Startup class, which itself is configured to support dependency injection at several points.</span></span> <span data-ttu-id="80138-168">如果您的啟動類別具有建構函式，則可透過建構函式要求相依性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="80138-168">If your Startup class has a constructor, it can request dependencies through the constructor, like so:</span></span>

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

<span data-ttu-id="80138-169">啟動類別有趣的是，它沒有明確的類型需求。</span><span class="sxs-lookup"><span data-stu-id="80138-169">The Startup class is interesting in that there are no explicit type requirements for it.</span></span> <span data-ttu-id="80138-170">它不會繼承自特殊啟動基底類別，也不會實作任何特定介面。</span><span class="sxs-lookup"><span data-stu-id="80138-170">It doesn't inherit from a special Startup base class, nor does it implement any particular interface.</span></span> <span data-ttu-id="80138-171">您可以選擇是否要提供建構函式給它，並視需要在建構函式上指定許多參數。</span><span class="sxs-lookup"><span data-stu-id="80138-171">You can give it a constructor, or not, and you can specify as many parameters on the constructor as you want.</span></span> <span data-ttu-id="80138-172">當您為應用程式設定的 Web 主機啟動時，它會呼叫您指示它使用的啟動類別，並使用相依性插入來填入啟動類別所需的任何相依性。</span><span class="sxs-lookup"><span data-stu-id="80138-172">When the web host you've configured for your application starts, it will call the Startup class you've told it to use, and will use dependency injection to populate any dependencies the Startup class requires.</span></span> <span data-ttu-id="80138-173">當然，如果您要求 ASP.NET Core 所使用的服務容器中未設定的參數，您會收到例外狀況，但只要您堅持使用容器已知的相依性，您就可以要求任何想要的項目。</span><span class="sxs-lookup"><span data-stu-id="80138-173">Of course, if you request parameters that aren't configured in the services container used by ASP.NET Core, you'll get an exception, but as long as you stick to dependencies the container knows about, you can request anything you want.</span></span>

<span data-ttu-id="80138-174">當您建立啟動執行個體時，您的 ASP.NET Core 應用程式從一開始就內建相依性插入。</span><span class="sxs-lookup"><span data-stu-id="80138-174">Dependency injection is built into your ASP.NET Core apps right from the start, when you create the Startup instance.</span></span> <span data-ttu-id="80138-175">啟動類別還不止於此。</span><span class="sxs-lookup"><span data-stu-id="80138-175">It doesn't stop there for the Startup class.</span></span> <span data-ttu-id="80138-176">您也可以在 Configure 方法中要求相依性：</span><span class="sxs-lookup"><span data-stu-id="80138-176">You can also request dependencies in the Configure method:</span></span>

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

<span data-ttu-id="80138-177">此行為的例外是 ConfigureServices 方法；它只能接受 IServiceCollection 類型的一個參數。</span><span class="sxs-lookup"><span data-stu-id="80138-177">The ConfigureServices method is the exception to this behavior; it must take just one parameter of type IServiceCollection.</span></span> <span data-ttu-id="80138-178">它實際上不需要支援相依性插入，因為一方面它會負責將物件新增至服務容器，另一方面它可透過 IServiceCollection 參數存取目前所有已設定的服務。</span><span class="sxs-lookup"><span data-stu-id="80138-178">It doesn't really need to support dependency injection, since on the one hand it is responsible for adding objects to the services container, and on the other it has access to all currently configured services via the IServiceCollection parameter.</span></span> <span data-ttu-id="80138-179">因此，您可以透過要求所需的服務作為參數，或使用 ConfigureServices 中的 IServiceCollection，在啟動類別的每個部分使用 ASP.NET Core 服務集合中定義的相依性。</span><span class="sxs-lookup"><span data-stu-id="80138-179">Thus, you can work with dependencies defined in the ASP.NET Core services collection in every part of the Startup class, either by requesting the needed service as a parameter or by working with the IServiceCollection in ConfigureServices.</span></span>

> [!NOTE]
> <span data-ttu-id="80138-180">如果您需要確保特定服務可供啟動類別使用，您可以使用 WebHostBuilder 及其 ConfigureServices 方法進行設定。</span><span class="sxs-lookup"><span data-stu-id="80138-180">If you need to ensure certain services are available to your Startup class, you can configure them using WebHostBuilder and its ConfigureServices method.</span></span>

<span data-ttu-id="80138-181">啟動類別是您應該如何建構 ASP.NET Core 應用程式之其他組件的模型，這些組件包括控制器、中介軟體、篩選條件到您自己的服務。</span><span class="sxs-lookup"><span data-stu-id="80138-181">The Startup class is a model for how you should structure other parts of your ASP.NET Core application, from Controllers to Middleware to Filters to your own Services.</span></span> <span data-ttu-id="80138-182">在每個案例中，您應該遵循[明確相依性準則](http://deviq.com/explicit-dependencies-principle/)，要求而不是直接建立相依性，並在您的應用程式中利用相依性插入。</span><span class="sxs-lookup"><span data-stu-id="80138-182">In each case, you should follow the [Explicit Dependencies Principle](http://deviq.com/explicit-dependencies-principle/), requesting your dependencies rather than directly creating them, and leveraging dependency injection throughout your application.</span></span> <span data-ttu-id="80138-183">對於您直接具現化實作的位置和方式請小心，特別是搭配基礎結構使用或具有副作用的服務和物件。</span><span class="sxs-lookup"><span data-stu-id="80138-183">Be careful of where and how you directly instantiate implementations, especially services and objects that work with infrastructure or have side effects.</span></span> <span data-ttu-id="80138-184">最好是使用您的應用程式核心中定義的抽象概念，並作為引數傳遞到特定實作類型的硬式編碼參考。</span><span class="sxs-lookup"><span data-stu-id="80138-184">Prefer working with abstractions defined in your application core and passed in as arguments to hardcoding references to specific implementation types.</span></span>

## <a name="structuring-the-application"></a><span data-ttu-id="80138-185">建構應用程式</span><span class="sxs-lookup"><span data-stu-id="80138-185">Structuring the Application</span></span>

<span data-ttu-id="80138-186">整合型應用程式通常具有單一進入點。</span><span class="sxs-lookup"><span data-stu-id="80138-186">Monolithic applications typically have a single entry point.</span></span> <span data-ttu-id="80138-187">在 ASP.NET Core Web 應用程式的案例中，此進入點會是 ASP.NET Core Web 專案。</span><span class="sxs-lookup"><span data-stu-id="80138-187">In the case of an ASP.NET Core web application, the entry point will be the ASP.NET Core web project.</span></span> <span data-ttu-id="80138-188">不過，這並不表示方案應該只包含一個專案。</span><span class="sxs-lookup"><span data-stu-id="80138-188">However, that doesn't mean the solution should consist of just a single project.</span></span> <span data-ttu-id="80138-189">將應用程式分成不同的層級有助於遵循關注點分離。</span><span class="sxs-lookup"><span data-stu-id="80138-189">It's useful to break up the application into different layers in order to follow separation of concerns.</span></span> <span data-ttu-id="80138-190">一旦分成不同的層級，您就可以深入資料夾到個別專案，以協助達到更佳封裝。</span><span class="sxs-lookup"><span data-stu-id="80138-190">Once broken up into layers, it's helpful to go beyond folders to separate projects, which can help achieve better encapsulation.</span></span> <span data-ttu-id="80138-191">使用 ASP.NET Core 應用程式達成這些目標的最佳方法，也就是第 5 章所討論的全新架構變化。</span><span class="sxs-lookup"><span data-stu-id="80138-191">The best approach to achieve these goals with an ASP.NET Core application is a variation of the Clean Architecture discussed in chapter 5.</span></span> <span data-ttu-id="80138-192">執行此方法之後，應用程式的方案將會包含 UI、基礎結構和 ApplicationCore 的個別程式庫。</span><span class="sxs-lookup"><span data-stu-id="80138-192">Following this approach, the application's solution will be comprised of separate libraries for the UI, Infrastructure, and ApplicationCore.</span></span>

<span data-ttu-id="80138-193">除了這些專案，還會包含個別測試專案 (第 9 章中會討論測試)。</span><span class="sxs-lookup"><span data-stu-id="80138-193">In addition to these projects, separate test projects are included as well (Testing is discussed in Chapter 9).</span></span>

<span data-ttu-id="80138-194">應用程式的物件模型和介面應該放在 ApplicationCore 專案中。</span><span class="sxs-lookup"><span data-stu-id="80138-194">The application's object model and interfaces should be placed in the ApplicationCore project.</span></span> <span data-ttu-id="80138-195">此專案會盡可能擁有很少的相依性，而且方案中的其他專案會參考它。</span><span class="sxs-lookup"><span data-stu-id="80138-195">This project will have as few dependencies as possible, and the other projects in the solution will reference it.</span></span> <span data-ttu-id="80138-196">需要保存的商務實體是在 ApplicationCore 專案中定義，不直接相依於基礎結構的服務也是。</span><span class="sxs-lookup"><span data-stu-id="80138-196">Business entities that need to be persisted are defined in the ApplicationCore project, as are services that do not directly depend on infrastructure.</span></span>

<span data-ttu-id="80138-197">實作詳細資料 (例如持續性的執行方式或通知傳送給使用者的可能方式) 會保留在基礎結構專案中。</span><span class="sxs-lookup"><span data-stu-id="80138-197">Implementation details, such as how persistence is performed or how notifications might be sent to a user, are kept in the Infrastructure project.</span></span> <span data-ttu-id="80138-198">此專案會參考實作特定套件 (例如 Entity Framework Core)，但不應該公開專案以外的實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="80138-198">This project will reference implementation-specific packages such as Entity Framework Core, but should not expose details about these implementations outside of the project.</span></span> <span data-ttu-id="80138-199">基礎結構服務和儲存機制應該實作 ApplicationCore 專案中定義的介面，且其持續性實作會負責擷取及儲存 ApplicationCore 中定義的實體。</span><span class="sxs-lookup"><span data-stu-id="80138-199">Infrastructure services and repositories should implement interfaces that are defined in the ApplicationCore project, and its persistence implementations are responsible for retrieving and storing entities defined in ApplicationCore.</span></span>

<span data-ttu-id="80138-200">ASP.NET Core UI 專案會負責任何 UI 層級考量，但不應該包含商務邏輯或基礎結構詳細資料。</span><span class="sxs-lookup"><span data-stu-id="80138-200">The ASP.NET Core UI project is responsible for any UI level concerns, but should not include business logic or infrastructure details.</span></span> <span data-ttu-id="80138-201">事實上，在理想情況下，它甚至不應該相依於基礎結構專案，如此將有助於確保不會意外引進兩個專案之間的相依性。</span><span class="sxs-lookup"><span data-stu-id="80138-201">In fact, ideally it shouldn't even have a dependency on the Infrastructure project, which will help ensure no dependency between the two projects is introduced accidentally.</span></span> <span data-ttu-id="80138-202">這可透過使用 StructureMap 等協力廠商 DI 容器來達成，該容器可讓您定義每個專案之登錄類別中的 DI 規則。</span><span class="sxs-lookup"><span data-stu-id="80138-202">This can be achieved using a third-party DI container like StructureMap, which allows you to define DI rules in Registry classes in each project.</span></span>

<span data-ttu-id="80138-203">另一個將應用程式與實作詳細資料分離的方法是，讓應用程式呼叫可能部署在個別 Docker 容器中的微服務。</span><span class="sxs-lookup"><span data-stu-id="80138-203">Another approach to decoupling the application from implementation details is to have the application call microservices, perhaps deployed in individual Docker containers.</span></span> <span data-ttu-id="80138-204">這比在兩個專案之間利用 DI，提供甚至更佳的關注點分離和解耦，但複雜度也更高。</span><span class="sxs-lookup"><span data-stu-id="80138-204">This provides even greater separation of concerns and decoupling than leveraging DI between two projects, but has additional complexity.</span></span>

### <a name="feature-organization"></a><span data-ttu-id="80138-205">功能組織</span><span class="sxs-lookup"><span data-stu-id="80138-205">Feature Organization</span></span>

<span data-ttu-id="80138-206">根據預設，ASP.NET Core 應用程式組織其資料夾結構時會包含 Controllers 和 Views，通常也會包含 ViewModels。</span><span class="sxs-lookup"><span data-stu-id="80138-206">By default, ASP.NET Core applications organize their folder structure to include Controllers and Views, and frequently ViewModels.</span></span> <span data-ttu-id="80138-207">支援這些伺服器端結構的用戶端程式碼通常會與 wwwroot 資料夾分開儲存。</span><span class="sxs-lookup"><span data-stu-id="80138-207">Client-side code to support these server-side structures is typically stored separately in the wwwroot folder.</span></span> <span data-ttu-id="80138-208">不過，大型應用程式在使用此組織方式時可能會遇到問題，因為處理任何指定的功能通常需要在這些資料夾之間跳來跳去。</span><span class="sxs-lookup"><span data-stu-id="80138-208">However, large applications may encounter problems with this organization, since working on any given feature often requires jumping between these folders.</span></span> <span data-ttu-id="80138-209">隨著每個資料夾中的檔案和子資料夾數目增加，這會變得越來越困難，而導致需要大幅捲動方案總管。</span><span class="sxs-lookup"><span data-stu-id="80138-209">This gets more and more difficult as the number of files and subfolders in each folder grows, resulting in a great deal of scrolling through Solution Explorer.</span></span> <span data-ttu-id="80138-210">解決此問題的方法之一，是依「功能」而不是檔案類型來組織應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="80138-210">One solution to this problem is to organize application code by *feature* instead of by file type.</span></span> <span data-ttu-id="80138-211">此組織樣式通常稱為功能資料夾或功能分割 (請參閱：[Vertical Slices](http://deviq.com/vertical-slices/) (垂直分割))。</span><span class="sxs-lookup"><span data-stu-id="80138-211">This organizational style is typically referred to as feature folders or feature slices (see also: [Vertical Slices](http://deviq.com/vertical-slices/)).</span></span>

<span data-ttu-id="80138-212">基於此目的，ASP.NET Core MVC 會支援 Areas。</span><span class="sxs-lookup"><span data-stu-id="80138-212">ASP.NET Core MVC supports Areas for this purpose.</span></span> <span data-ttu-id="80138-213">使用 Areas，您可以在每個 Areas 資料夾中建立不同的 Controllers 和 Views 資料夾集 (以及任何相關聯的模型)。</span><span class="sxs-lookup"><span data-stu-id="80138-213">Using areas, you can create separate sets of Controllers and Views folders (as well as any associated models) in each Area folder.</span></span> <span data-ttu-id="80138-214">圖 7-1 顯示使用 Areas 的範例資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="80138-214">Figure 7-1 shows an example folder structure, using Areas.</span></span>

![](./media/image7-1.png)

<span data-ttu-id="80138-215">圖 7-1：範例 Areas 組織</span><span class="sxs-lookup"><span data-stu-id="80138-215">Figure 7-1 Sample Area Organization</span></span>

<span data-ttu-id="80138-216">使用 Areas 時，您必須使用屬性以其所屬的區域名稱來裝飾控制器：</span><span class="sxs-lookup"><span data-stu-id="80138-216">When using Areas, you must use attributes to decorate your controllers with the name of the area to which they belong:</span></span>

```csharp
[Area("Catalog")]
public class HomeController
{}
```

<span data-ttu-id="80138-217">您也必須將區域支援新增至您的路由：</span><span class="sxs-lookup"><span data-stu-id="80138-217">You also need to add area support to your routes:</span></span>

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

<span data-ttu-id="80138-218">除了 Areas 的內建支援，您也可以使用自己的資料夾結構和慣例，來取代屬性和自訂路由。</span><span class="sxs-lookup"><span data-stu-id="80138-218">In addition to the built-in support for Areas, you can also use your own folder structure, and conventions in place of attributes and custom routes.</span></span> <span data-ttu-id="80138-219">這樣可讓您擁有不包含個別 Views、Controllers 等資料夾的功能資料夾，以保持更平面的階層架構，讓您可以更輕鬆地在單一位置查看每項功能的所有相關檔案。</span><span class="sxs-lookup"><span data-stu-id="80138-219">This would allow you to have feature folders that didn't include separate folders for Views, Controllers, etc., keeping the hierarchy flatter and making it easier to see all related files in a single place for each feature.</span></span>

<span data-ttu-id="80138-220">ASP.NET Core 使用內建慣例類型來控制其行為。</span><span class="sxs-lookup"><span data-stu-id="80138-220">ASP.NET Core uses built-in convention types to control its behavior.</span></span> <span data-ttu-id="80138-221">您可以修改或取代這些慣例。</span><span class="sxs-lookup"><span data-stu-id="80138-221">You can modify or replace these conventions.</span></span> <span data-ttu-id="80138-222">例如，您可以建立慣例，自動根據指定控制器的命名空間 (通常與控制器所在資料夾相互關聯) 取得其功能名稱：</span><span class="sxs-lookup"><span data-stu-id="80138-222">For example, you can create a convention that will automatically get the feature name for a given controller based on its namespace (which typically correlates to the folder in which the controller is located):</span></span>

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

<span data-ttu-id="80138-223">當您在 ConfigureServices 中將 MVC 支援新增至應用程式時，您可以接著指定此慣例作為選項：</span><span class="sxs-lookup"><span data-stu-id="80138-223">You then specify this convention as an option when you add support for MVC to your application in ConfigureServices:</span></span>

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

<span data-ttu-id="80138-224">ASP.NET Core MVC 也會使用慣例來尋找檢視。</span><span class="sxs-lookup"><span data-stu-id="80138-224">ASP.NET Core MVC also uses a convention to locate views.</span></span> <span data-ttu-id="80138-225">您可以使用自訂慣例將它覆寫，讓檢視位於功能資料夾中 (使用上述 FeatureConvention 提供的功能名稱)。</span><span class="sxs-lookup"><span data-stu-id="80138-225">You can override it with a custom convention so that views will be located in your feature folders (using the feature name provided by the FeatureConvention, above).</span></span> <span data-ttu-id="80138-226">您可以從 MSDN 文章 [Feature Slices for ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx) (ASP.NET Core MVC 的功能分割)，深入了解此方法及下載工作範例。</span><span class="sxs-lookup"><span data-stu-id="80138-226">You can learn more about this approach and download a working sample from the MSDN article, [Feature Slices for ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span></span>

### <a name="cross-cutting-concerns"></a><span data-ttu-id="80138-227">跨領域關注</span><span class="sxs-lookup"><span data-stu-id="80138-227">Cross-Cutting Concerns</span></span>

<span data-ttu-id="80138-228">隨著應用程式成長，排除跨領域關注因素對於去除重複和維持一致性會變得越來越重要。</span><span class="sxs-lookup"><span data-stu-id="80138-228">As applications grow, it becomes increasingly important to factor out cross-cutting concerns to eliminate duplication and maintain consistency.</span></span> <span data-ttu-id="80138-229">ASP.NET Core 應用程式中的一些跨領域關注範例包括驗證 (authentication)、模型驗證 (validation) 規則、輸出快取和錯誤處理，還有許多其他範例。</span><span class="sxs-lookup"><span data-stu-id="80138-229">Some examples of cross-cutting concerns in ASP.NET Core applications are authentication, model validation rules, output caching, and error handling, though there are many others.</span></span> <span data-ttu-id="80138-230">ASP.NET Core MVC [篩選條件](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters)可讓您在要求處理管線的特定步驟之前或之後執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="80138-230">ASP.NET Core MVC [filters](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) allow you to run code before or after certain steps in the request processing pipeline.</span></span> <span data-ttu-id="80138-231">例如，您可以在模型繫結前後、動作前後或動作結果前後執行篩選條件。</span><span class="sxs-lookup"><span data-stu-id="80138-231">For instance, a filter can run before and after model binding, before and after an action, or before and after an action's result.</span></span> <span data-ttu-id="80138-232">您也可以使用授權篩選條件來控制管線其餘部分的存取。</span><span class="sxs-lookup"><span data-stu-id="80138-232">You can also use an authorization filter to control access to the rest of the pipeline.</span></span> <span data-ttu-id="80138-233">圖 7-2 顯示如何透過篩選條件 (如已設定) 要求執行流程。</span><span class="sxs-lookup"><span data-stu-id="80138-233">Figures 7-2 shows how request execution flows through filters, if configured.</span></span>

![要求處理會歷經授權篩選條件、資源篩選條件、模型繫結、動作篩選條件、動作執行和動作結果轉換、例外狀況篩選條件、結果篩選條件，以及結果執行。](./media/image7-2.png)

<span data-ttu-id="80138-236">圖 7-2：透過篩選條件和要求管線執行要求</span><span class="sxs-lookup"><span data-stu-id="80138-236">Figure 7-2 Request execution through filters and request pipeline.</span></span>

<span data-ttu-id="80138-237">篩選條件通常會實作為屬性，以便您套用至控制器或動作。</span><span class="sxs-lookup"><span data-stu-id="80138-237">Filters are usually implemented as attributes, so you can apply them controllers or actions.</span></span> <span data-ttu-id="80138-238">以此方式新增時，在動作層級指定的篩選條件會覆寫在控制器層級指定的篩選條件或建置在其上，而後者本身會覆寫全域篩選條件。</span><span class="sxs-lookup"><span data-stu-id="80138-238">When added in this fashion, filters specified at the action level override or build upon filters specified at the controller level, which themselves override global filters.</span></span> <span data-ttu-id="80138-239">例如，\[Route\] 屬性可用來建置控制器與動作之間的路由。</span><span class="sxs-lookup"><span data-stu-id="80138-239">For example, the \[Route\] attribute can be used to build up routes between controllers and actions.</span></span> <span data-ttu-id="80138-240">同樣地，授權可在控制器層級設定，然後由個別動作覆寫，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="80138-240">Likewise, authorization can be configured at the controller level, and then overridden by individual actions, as the following sample demonstrates:</span></span>

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

<span data-ttu-id="80138-241">第一個方法 Login 使用 AllowAnonymous 篩選條件 (屬性)，來覆寫在控制器層級設定的 Authorize 篩選條件。</span><span class="sxs-lookup"><span data-stu-id="80138-241">The first method, Login, uses the AllowAnonymous filter (attribute) to override the Authorize filter set at the controller level.</span></span> <span data-ttu-id="80138-242">ForgotPassword 動作 (及不包含 AllowAnonymous 屬性之類別中的任何其他動作) 會需要已驗證的要求。</span><span class="sxs-lookup"><span data-stu-id="80138-242">The ForgotPassword action (and any other action in the class that doesn't have an AllowAnonymous attribute) will require an authenticated request.</span></span>

<span data-ttu-id="80138-243">篩選條件可用來去除 API 之常見錯誤處理原則形式中的重複情況。</span><span class="sxs-lookup"><span data-stu-id="80138-243">Filters can be used to eliminate duplication in the form of common error handling policies for APIs.</span></span> <span data-ttu-id="80138-244">例如，一般 API 原則是在要求不存在的參考索引鍵時，傳回 NotFound 回應；如果模型驗證失敗，則傳回 BadRequest 回應。</span><span class="sxs-lookup"><span data-stu-id="80138-244">For example, a typical API policy is to return a NotFound response to requests referencing keys that do not exist, and a BadRequest response if model validation fails.</span></span> <span data-ttu-id="80138-245">下列範例將示範這兩個原則的運作方式：</span><span class="sxs-lookup"><span data-stu-id="80138-245">The following example demonstrates these two policies in action:</span></span>

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

<span data-ttu-id="80138-246">請勿讓您的動作方法因為類似的條件程式碼而變得很雜亂。</span><span class="sxs-lookup"><span data-stu-id="80138-246">Don't allow your action methods to become cluttered with conditional code like this.</span></span> <span data-ttu-id="80138-247">相反地，請將原則提取到可視需要套用的篩選條件中。</span><span class="sxs-lookup"><span data-stu-id="80138-247">Instead, pull the policies into filters that can be applied on an as-needed basis.</span></span> <span data-ttu-id="80138-248">在此範例中，任何時候將命令傳送至 API，都應該進行模型驗證檢查，該檢查可取代為下列屬性：</span><span class="sxs-lookup"><span data-stu-id="80138-248">In this example, the model validation check, which should occur any time a command is sent to the API, can be replaced by the following attribute:</span></span>

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

<span data-ttu-id="80138-249">同樣地，篩選條件可用來檢查記錄是否存在，並先傳回 404 再執行動作，因此不需要在動作中執行這些檢查。</span><span class="sxs-lookup"><span data-stu-id="80138-249">Likewise, a filter can be used to check if a record exists and return a 404 before the action is executed, eliminating the need to perform these checks in the action.</span></span> <span data-ttu-id="80138-250">一旦您取出一般慣例並組織方案，將基礎結構程式碼和商務邏輯與 UI 分隔開來之後，您的 MVC 動作方法應該會非常精簡：</span><span class="sxs-lookup"><span data-stu-id="80138-250">Once you've pulled out common conventions and organized your solution to separate infrastructure code and business logic from your UI, your MVC action methods should be extremely thin:</span></span>

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

<span data-ttu-id="80138-251">您可以從 MSDN 文章 [Real World ASP.NET Core MVC Filters](https://msdn.microsoft.com/magazine/mt767699.aspx) (真實世界的 ASP.NET Core MVC 篩選條件)，深入了解如何實作篩選條件及下載工作範例。</span><span class="sxs-lookup"><span data-stu-id="80138-251">You can read more about implementing filters and download a working sample from the MSDN article, [Real World ASP.NET Core MVC Filters](https://msdn.microsoft.com/magazine/mt767699.aspx).</span></span>

> ### <a name="references--structuring-applications"></a><span data-ttu-id="80138-252">參考資料 - 建構應用程式</span><span class="sxs-lookup"><span data-stu-id="80138-252">References – Structuring Applications</span></span>
> - <span data-ttu-id="80138-253">**區域**</span><span class="sxs-lookup"><span data-stu-id="80138-253">**Areas**</span></span>  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - <span data-ttu-id="80138-254">**MSDN – Feature Slices for ASP.NET Core MVC**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx> (MSDN – ASP.NET Core MVC 的功能分區)</span><span class="sxs-lookup"><span data-stu-id="80138-254">**MSDN – Feature Slices for ASP.NET Core MVC**
<https://msdn.microsoft.com/magazine/mt763233.aspx></span></span>
> - <span data-ttu-id="80138-255">**篩選**</span><span class="sxs-lookup"><span data-stu-id="80138-255">**Filters**</span></span>  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - <span data-ttu-id="80138-256">**MSDN - Real World ASP.NET Core MVC Filters (真實世界的 ASP.NET Core MVC 篩選條件)**</span><span class="sxs-lookup"><span data-stu-id="80138-256">**MSDN – Real World ASP.NET Core MVC Filters**</span></span>  
> <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a><span data-ttu-id="80138-257">安全性</span><span class="sxs-lookup"><span data-stu-id="80138-257">Security</span></span>

<span data-ttu-id="80138-258">保護 Web 應用程式是很龐大的主題，其中包含許多考量。</span><span class="sxs-lookup"><span data-stu-id="80138-258">Securing web applications is a large topic, with many considerations.</span></span> <span data-ttu-id="80138-259">最基本的安全性層級牽涉到確保您知道指定要求的來源，以及確保該要求只具有其應有的資源存取權。</span><span class="sxs-lookup"><span data-stu-id="80138-259">At its most basic level, security involves ensuring you know who a given request is coming from, and then ensuring that that request only has access to resources it should.</span></span> <span data-ttu-id="80138-260">驗證是比較要求隨附的認證與受信任資料存放區中的認證，來查看是否應該將要求視為來自已知實體的程序。</span><span class="sxs-lookup"><span data-stu-id="80138-260">Authentication is the process of comparing credentials provided with a request to those in a trusted data store, to see if the request should be treated as coming from a known entity.</span></span> <span data-ttu-id="80138-261">授權是根據使用者身分識別限制特定資源存取權的程序。</span><span class="sxs-lookup"><span data-stu-id="80138-261">Authorization is the process of restricting access to certain resources based on user identity.</span></span> <span data-ttu-id="80138-262">第三個安全性考量是防止第三方竊聽要求，您應該至少[確保應用程式使用 SSL](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl)。</span><span class="sxs-lookup"><span data-stu-id="80138-262">A third security concern is protecting requests from eavesdropping by third parties, for which you should at least [ensure that SSL is used by your application](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).</span></span>

### <a name="authentication"></a><span data-ttu-id="80138-263">驗證</span><span class="sxs-lookup"><span data-stu-id="80138-263">Authentication</span></span>

<span data-ttu-id="80138-264">ASP.NET Core Identity 是可用來支援應用程式登入功能的會員系統。</span><span class="sxs-lookup"><span data-stu-id="80138-264">ASP.NET Core Identity is a membership system you can use to support login functionality for your application.</span></span> <span data-ttu-id="80138-265">它具備本機使用者帳戶支援，以及來自 Microsoft 帳戶、Twitter、Facebook、Google 等提供者的外部登入提供者支援。</span><span class="sxs-lookup"><span data-stu-id="80138-265">It has support for local user accounts as well as external login provider support from providers like Microsoft Account, Twitter, Facebook, Google, and more.</span></span> <span data-ttu-id="80138-266">除了 ASP.NET Core Identity，您的應用程式也可以使用 Windows 驗證，或 [Identity Server](https://github.com/IdentityServer/IdentityServer4) 等協力廠商身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="80138-266">In addition to ASP.NET Core Identity, your application can use windows authentication, or a third-party identity provider like [Identity Server](https://github.com/IdentityServer/IdentityServer4).</span></span>

<span data-ttu-id="80138-267">如果選取 [個別使用者帳戶] 選項，ASP.NET Core Identity 會隨附於新的專案範本。</span><span class="sxs-lookup"><span data-stu-id="80138-267">ASP.NET Core Identity is included in new project templates if the Individual User Accounts option is selected.</span></span> <span data-ttu-id="80138-268">此範本包括註冊、登入、外部登入、忘記密碼和其他功能的支援。</span><span class="sxs-lookup"><span data-stu-id="80138-268">This template includes support for registration, login, external logins, forgotten passwords, and additional functionality.</span></span>

![](./media/image7-3.png)

<span data-ttu-id="80138-269">圖 7-3：選取 [個別使用者帳戶] 來預先設定身分識別</span><span class="sxs-lookup"><span data-stu-id="80138-269">Figure 7-3 Select Individual User Accounts to have Identity preconfigured.</span></span>

<span data-ttu-id="80138-270">身分識別是在啟動的 ConfigureServices 和 Configure 中設定：</span><span class="sxs-lookup"><span data-stu-id="80138-270">Identity support is configured in Startup, both in ConfigureServices and Configure:</span></span>

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

<span data-ttu-id="80138-271">在 Configure 方法中，UseIdentity 必須在 UseMvc 之前出現。</span><span class="sxs-lookup"><span data-stu-id="80138-271">It's important that UseIdentity appear before UseMvc in the Configure method.</span></span> <span data-ttu-id="80138-272">在 ConfigureServices 中設定身分識別時，您會注意到對 AddDefaultTokenProviders 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="80138-272">When configuring Identity in ConfigureServices, you'll notice a call to AddDefaultTokenProviders.</span></span> <span data-ttu-id="80138-273">這與可用來保護 Web 通訊的權杖無關，而是指建立提示的提供者，這些提示可透過簡訊或電子郵件傳送給使用者，以確認其身分識別。</span><span class="sxs-lookup"><span data-stu-id="80138-273">This has nothing to do with tokens that may be used to secure web communications, but instead refers to providers that create prompts that can be sent to users via SMS or email in order for them to confirm their identity.</span></span>

<span data-ttu-id="80138-274">您可以從官方 ASP.NET Core 文件，深入了解如何[設定雙因素驗證](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)和[啟用外部登入提供者](https://docs.microsoft.com/aspnet/core/security/authentication/social/)。</span><span class="sxs-lookup"><span data-stu-id="80138-274">You can learn more about [configuring two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) and [enabling external login providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) from the official ASP.NET Core docs.</span></span>

### <a name="authorization"></a><span data-ttu-id="80138-275">授權</span><span class="sxs-lookup"><span data-stu-id="80138-275">Authorization</span></span>

<span data-ttu-id="80138-276">授權的最簡單形式牽涉到限制匿名使用者的存取。</span><span class="sxs-lookup"><span data-stu-id="80138-276">The simplest form of authorization involves restricting access to anonymous users.</span></span> <span data-ttu-id="80138-277">只要將 \[Authorize\] 屬性套用至特定控制器或動作，即可達成此目的。</span><span class="sxs-lookup"><span data-stu-id="80138-277">This can be achieved by simply applying the \[Authorize\] attribute to certain controllers or actions.</span></span> <span data-ttu-id="80138-278">如果角色正在使用中，您可以進一步擴充屬性，限制屬於特定角色之使用者的存取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="80138-278">If roles are being used, the attribute can be further extended to restrict access to users who belong to certain roles, as shown:</span></span>

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

<span data-ttu-id="80138-279">在本例中，屬於 HRManager 或 Finance 角色 (或兩者) 的使用者可存取 SalaryController。</span><span class="sxs-lookup"><span data-stu-id="80138-279">In this case, users belonging to either the HRManager or Finance roles (or both) would have access to the SalaryController.</span></span> <span data-ttu-id="80138-280">如果使用者必須屬於多個角色 (而不只是數個角色之一)，您可以套用屬性多次，並每次指定必要的角色。</span><span class="sxs-lookup"><span data-stu-id="80138-280">To require that a user belong to multiple roles (not just one of several), you can apply the attribute multiple times, specifying a required role each time.</span></span>

<span data-ttu-id="80138-281">將特定角色集指定為許多不同控制器和動作中的字串，可能會導致不想要的重複。</span><span class="sxs-lookup"><span data-stu-id="80138-281">Specifying certain sets of roles as strings in many different controllers and actions can lead to undesirable repetition.</span></span> <span data-ttu-id="80138-282">您可以設定封裝授權規則的授權原則，然後在套用 \[Authorize\] 屬性時指定原則，而不是個別角色：</span><span class="sxs-lookup"><span data-stu-id="80138-282">You can configure authorization policies, which encapsulate authorization rules, and then specify the policy instead of individual roles when applying the \[Authorize\] attribute:</span></span>

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

<span data-ttu-id="80138-283">以此方式使用原則，您就可以分隔特定角色限制使用的動作類型，或對其套用的規則。</span><span class="sxs-lookup"><span data-stu-id="80138-283">Using policies in this way, you can separate the kinds of actions being restricted from the specific roles or rules that apply to it.</span></span> <span data-ttu-id="80138-284">稍後，如果您建立需要存取特定資源的新角色，您只要更新原則即可，而不需要在每個 \[Authorize\] 屬性上更新每個角色清單。</span><span class="sxs-lookup"><span data-stu-id="80138-284">Later, if you create a new role that needs to have access to certain resources, you can just update a policy, rather than updating every list of roles on every \[Authorize\] attribute.</span></span>

#### <a name="claims"></a><span data-ttu-id="80138-285">宣告</span><span class="sxs-lookup"><span data-stu-id="80138-285">Claims</span></span>

<span data-ttu-id="80138-286">宣告是成對的名稱和數值，代表已驗證使用者的屬性。</span><span class="sxs-lookup"><span data-stu-id="80138-286">Claims are name value pairs that represent properties of an authenticated user.</span></span> <span data-ttu-id="80138-287">例如，您可以將使用者的員工編號儲存為宣告。</span><span class="sxs-lookup"><span data-stu-id="80138-287">For example, you might store users' employee number as a claim.</span></span> <span data-ttu-id="80138-288">宣告可接著作為授權原則的一部分使用。</span><span class="sxs-lookup"><span data-stu-id="80138-288">Claims can then be used as part of authorization policies.</span></span> <span data-ttu-id="80138-289">您可以建立稱為 "EmployeeOnly" 的原則，該原則需要有稱為 "EmployeeNumber" 的宣告，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="80138-289">You could create a policy called "EmployeeOnly" that requires the existence of a claim called "EmployeeNumber", as shown in this example:</span></span>

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

<span data-ttu-id="80138-290">此原則可接著搭配 \[Authorize\] 屬性使用，以保護任何控制器及/或動作，如上所述。</span><span class="sxs-lookup"><span data-stu-id="80138-290">This policy could then be used with the \[Authorize\] attribute to protect any controller and/or action, as described above.</span></span>

#### <a name="securing-web-apis"></a><span data-ttu-id="80138-291">保護 Web API</span><span class="sxs-lookup"><span data-stu-id="80138-291">Securing Web APIs</span></span>

<span data-ttu-id="80138-292">大多數 Web API 應該實作權杖型驗證系統。</span><span class="sxs-lookup"><span data-stu-id="80138-292">Most web APIs should implement a token-based authentication system.</span></span> <span data-ttu-id="80138-293">權杖驗證為無狀態並設計成可調整。</span><span class="sxs-lookup"><span data-stu-id="80138-293">Token authentication is stateless and designed to be scalable.</span></span> <span data-ttu-id="80138-294">在權杖型驗證系統中，用戶端必須先向驗證提供者進行驗證。</span><span class="sxs-lookup"><span data-stu-id="80138-294">In a token-based authentication system, the client must first authenticate with the authentication provider.</span></span> <span data-ttu-id="80138-295">如果成功，則會向用戶端發出權杖，這只是密碼編譯方面有意義的字元字串。</span><span class="sxs-lookup"><span data-stu-id="80138-295">If successful, the client is issued a token, which is simply a cryptographically meaningful string of characters.</span></span> <span data-ttu-id="80138-296">接著，當用戶端需要發出 API 要求時，就會新增此權杖作為要求的標頭。</span><span class="sxs-lookup"><span data-stu-id="80138-296">When the client then needs to issue a request to an API, it adds this token as a header on the request.</span></span> <span data-ttu-id="80138-297">伺服器接著會驗證要求標頭中找到的權杖，再完成要求。</span><span class="sxs-lookup"><span data-stu-id="80138-297">The server then validates the token found in the request header before completing the request.</span></span> <span data-ttu-id="80138-298">圖 7-4 示範此程序。</span><span class="sxs-lookup"><span data-stu-id="80138-298">Figure 7-4 demonstrates this process.</span></span>

![TokenAuth](./media/image7-4.png)

<span data-ttu-id="80138-300">**圖 7-4**：</span><span class="sxs-lookup"><span data-stu-id="80138-300">**Figure 7-4.**</span></span> <span data-ttu-id="80138-301">Web API 的權杖型驗證</span><span class="sxs-lookup"><span data-stu-id="80138-301">Token-based authentication for Web APIs.</span></span>

> ### <a name="references--security"></a><span data-ttu-id="80138-302">參考資料 - 安全性</span><span class="sxs-lookup"><span data-stu-id="80138-302">References – Security</span></span>
> - <span data-ttu-id="80138-303">**安全性文件概觀**</span><span class="sxs-lookup"><span data-stu-id="80138-303">**Security Docs Overview**</span></span>  
> https://docs.microsoft.com/aspnet/core/security/
> - <span data-ttu-id="80138-304">**Enforcing SSL in an ASP.NET Core App** (在 ASP.NET Core 應用程式中強制執行 SSL)</span><span class="sxs-lookup"><span data-stu-id="80138-304">**Enforcing SSL in an ASP.NET Core App**</span></span>  
> <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - <span data-ttu-id="80138-305">**身分識別簡介**</span><span class="sxs-lookup"><span data-stu-id="80138-305">**Introduction to Identity**</span></span>  
> <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - <span data-ttu-id="80138-306">**授權簡介**</span><span class="sxs-lookup"><span data-stu-id="80138-306">**Introduction to Authorization**</span></span>  
> <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - <span data-ttu-id="80138-307">**Azure App Service 之 API Apps 的驗證和授權**</span><span class="sxs-lookup"><span data-stu-id="80138-307">**Authentication and Authorization for API Apps in Azure App Service**</span></span>  
> <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>

## <a name="client-communication"></a><span data-ttu-id="80138-308">用戶端通訊</span><span class="sxs-lookup"><span data-stu-id="80138-308">Client Communication</span></span>

<span data-ttu-id="80138-309">除了透過 Web API 提供頁面及回應資料要求，ASP.NET Core 應用程式還可以直接與連線的用戶端通訊。</span><span class="sxs-lookup"><span data-stu-id="80138-309">In addition to serving pages and responding to requests for data via web APIs, ASP.NET Core apps can communicate directly with connected clients.</span></span> <span data-ttu-id="80138-310">此輸出通訊可以使用各種傳輸技術，最常見的是 WebSockets。</span><span class="sxs-lookup"><span data-stu-id="80138-310">This outbound communication can use a variety of transport technologies, the most common being WebSockets.</span></span> <span data-ttu-id="80138-311">ASP.NET Core SignalR 是一種程式庫，可讓您簡單地將即時伺服器對用戶端通訊功能新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="80138-311">ASP.NET Core SignalR is a library that makes it simple to add real-time server-to-client communication functionality to your applications.</span></span> <span data-ttu-id="80138-312">SignalR 支援各種傳輸技術 (包括 WebSockets)，並從開發人員擷取許多實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="80138-312">SignalR supports a variety of transport technologies, including WebSockets, and abstracts away many of the implementation details from the developer.</span></span>

<span data-ttu-id="80138-313">ASP.NET Core SignalR 目前正在開發中，下一版 ASP.NET Core 將會提供使用。</span><span class="sxs-lookup"><span data-stu-id="80138-313">ASP.NET Core SignalR is currently under development, and will be available in the next release of ASP.NET Core.</span></span> <span data-ttu-id="80138-314">不過，目前有其他[開放原始碼 WebSockets 程式庫](https://github.com/radu-matei/websocket-manager)可用。</span><span class="sxs-lookup"><span data-stu-id="80138-314">However, other [open source WebSockets libraries](https://github.com/radu-matei/websocket-manager) are currently available.</span></span>

<span data-ttu-id="80138-315">即時用戶端通訊 (不論是直接使用 WebSockets 或其他技術) 在許多不同的應用程式案例中都很有用。</span><span class="sxs-lookup"><span data-stu-id="80138-315">Real-time client communication, whether using WebSockets directly or other techniques, are useful in a variety of application scenarios.</span></span> <span data-ttu-id="80138-316">其中某些範例包括：</span><span class="sxs-lookup"><span data-stu-id="80138-316">Some examples include:</span></span>

-   <span data-ttu-id="80138-317">即時聊天室應用程式</span><span class="sxs-lookup"><span data-stu-id="80138-317">Live chat room applications</span></span>

-   <span data-ttu-id="80138-318">監控應用程式</span><span class="sxs-lookup"><span data-stu-id="80138-318">Monitoring applications</span></span>

-   <span data-ttu-id="80138-319">工作進度更新</span><span class="sxs-lookup"><span data-stu-id="80138-319">Job progress updates</span></span>

-   <span data-ttu-id="80138-320">通知</span><span class="sxs-lookup"><span data-stu-id="80138-320">Notifications</span></span>

-   <span data-ttu-id="80138-321">互動式論壇應用程式</span><span class="sxs-lookup"><span data-stu-id="80138-321">Interactive forms applications</span></span>

<span data-ttu-id="80138-322">在應用程式中內建用戶端通訊時，通常有兩個元件：</span><span class="sxs-lookup"><span data-stu-id="80138-322">When building client communication into your applications, there are typically two components:</span></span>

-   <span data-ttu-id="80138-323">伺服器端連線管理員 (SignalR 中樞、WebSocketManager、WebSocketHandler)</span><span class="sxs-lookup"><span data-stu-id="80138-323">Server-side connection manager (SignalR Hub, WebSocketManager WebSocketHandler)</span></span>

-   <span data-ttu-id="80138-324">用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="80138-324">Client-side library</span></span>

<span data-ttu-id="80138-325">用戶端不僅限於瀏覽器，行動裝置應用程式、主控台應用程式和其他原生應用程式也可以使用 SignalR/WebSockets 來通訊。</span><span class="sxs-lookup"><span data-stu-id="80138-325">Clients are not limited to browsers – mobile apps, console apps, and other native apps can also communicate using SignalR/WebSockets.</span></span> <span data-ttu-id="80138-326">下列簡單程式會將所有傳送至交談應用程式的內容回應到主控台，以作為 WebSocketManager 範例應用程式的一部分：</span><span class="sxs-lookup"><span data-stu-id="80138-326">The following simple program echoes all content sent to a chat application to the console, as part of a WebSocketManager sample application:</span></span>

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

<span data-ttu-id="80138-327">請考慮您的應用程式直接與用戶端應用程式通訊的方式，並考慮即時通訊是否會改善應用程式的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="80138-327">Consider ways in which your applications communicate directly with client applications, and consider whether real-time communication would improve your app's user experience.</span></span>

> ### <a name="references--client-communication"></a><span data-ttu-id="80138-328">參考資料 - 用戶端通訊</span><span class="sxs-lookup"><span data-stu-id="80138-328">References – Client Communication</span></span>
> - <span data-ttu-id="80138-329">**ASP.NET Core SignalR**</span><span class="sxs-lookup"><span data-stu-id="80138-329">**ASP.NET Core SignalR**</span></span>  
> <https://github.com/aspnet/SignalR>
> - <span data-ttu-id="80138-330">**WebSocket Manager**</span><span class="sxs-lookup"><span data-stu-id="80138-330">**WebSocket Manager**</span></span>  
> https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a><span data-ttu-id="80138-331">領域驅動設計 - 是否應該套用？</span><span class="sxs-lookup"><span data-stu-id="80138-331">Domain-Driven Design – Should You Apply It?</span></span>

<span data-ttu-id="80138-332">領域驅動設計 (DDD) 是建置軟體的敏捷式方法，重點強調「商務領域」。</span><span class="sxs-lookup"><span data-stu-id="80138-332">Domain-Driven Design (DDD) is an agile approach to building software that emphasizes focusing on the *business domain*.</span></span> <span data-ttu-id="80138-333">它相當重視與商務領域專家的溝通和互動，這些專家會向開發人員說明真實世界系統的運作方式。</span><span class="sxs-lookup"><span data-stu-id="80138-333">It places a heavy emphasis on communication and interaction with business domain expert(s) who can relate to the developers how the real-world system works.</span></span> <span data-ttu-id="80138-334">例如，如果您想要建置處理股票交易的系統，您的領域專家可能會是經驗豐富的股票交易員。</span><span class="sxs-lookup"><span data-stu-id="80138-334">For example, if you're building a system that handles stock trades, your domain expert might be an experienced stock broker.</span></span> <span data-ttu-id="80138-335">DDD 是專為處理複雜的大型商務問題所設計，通常不適用於較小、較簡單的應用程式，因為不值得投資了解領域及建立領域模型。</span><span class="sxs-lookup"><span data-stu-id="80138-335">DDD is designed to address large, complex business problems, and is often not appropriate for smaller, simpler applications, as the investment in understanding and modeling the domain is not worth it.</span></span>

<span data-ttu-id="80138-336">建置採用 DDD 方法的軟體時，您的小組 (包括非技術性專案關係人和參與者) 應該針對問題空間開發「通用語言」。</span><span class="sxs-lookup"><span data-stu-id="80138-336">When building software following a DDD approach, your team (including non-technical stakeholders and contributors) should develop a *ubiquitous language* for the problem space.</span></span> <span data-ttu-id="80138-337">換句話說，您應該針對要模型化的真實世界概念、對等軟體，以及為了保存概念而可能存在的任何結構 (例如資料庫資料表) 使用相同的用語。</span><span class="sxs-lookup"><span data-stu-id="80138-337">That is, the same terminology should be used for the real-world concept being modeled, the software equivalent, and any structures that might exist to persist the concept (for example, database tables).</span></span> <span data-ttu-id="80138-338">因此，通用語言中所述的概念應該會形成「領域模型」的基礎。</span><span class="sxs-lookup"><span data-stu-id="80138-338">Thus, the concepts described in the ubiquitous language should form the basis for your *domain model*.</span></span>

<span data-ttu-id="80138-339">您的領域模型會包含彼此互動以代表系統行為的物件。</span><span class="sxs-lookup"><span data-stu-id="80138-339">Your domain model is comprised of objects that interact with one another to represent the behavior of the system.</span></span> <span data-ttu-id="80138-340">這些物件的分類如下：</span><span class="sxs-lookup"><span data-stu-id="80138-340">These objects may fall into the following categories:</span></span>

-   <span data-ttu-id="80138-341">[實體](http://deviq.com/entity/)，代表具有身分識別執行緒的物件。</span><span class="sxs-lookup"><span data-stu-id="80138-341">[Entities](http://deviq.com/entity/), which represent objects with a thread of identity.</span></span> <span data-ttu-id="80138-342">實體通常會儲存在使用金鑰的持續性儲存區中，稍後可予以擷取。</span><span class="sxs-lookup"><span data-stu-id="80138-342">Entities are typically stored in persistence with a key by which they can later be retrieved.</span></span>

-   <span data-ttu-id="80138-343">[彙總](http://deviq.com/aggregate-pattern/)，代表應該當作一個單位保存的物件群組。</span><span class="sxs-lookup"><span data-stu-id="80138-343">[Aggregates](http://deviq.com/aggregate-pattern/), which represent groups of objects that should be persisted as a unit.</span></span>

-   <span data-ttu-id="80138-344">[值物件](http://deviq.com/value-object/)，代表可根據其屬性值的總和比較的概念。</span><span class="sxs-lookup"><span data-stu-id="80138-344">[Value objects](http://deviq.com/value-object/), which represent concepts that can be compared on the basis of the sum of their property values.</span></span> <span data-ttu-id="80138-345">例如，由開始和結束日期組成的 DateRange。</span><span class="sxs-lookup"><span data-stu-id="80138-345">For example, DateRange consisting of a start and end date.</span></span>

-   <span data-ttu-id="80138-346">[領域事件](https://martinfowler.com/eaaDev/DomainEvent.html)，代表系統內發生的事件，系統的其他組件對這些事件會有興趣。</span><span class="sxs-lookup"><span data-stu-id="80138-346">[Domain events](https://martinfowler.com/eaaDev/DomainEvent.html), which represent things happening within the system that are of interest to other parts of the system.</span></span>

<span data-ttu-id="80138-347">請注意，DDD 領域模型應該將複雜行為封裝在模型內。</span><span class="sxs-lookup"><span data-stu-id="80138-347">Note that a DDD domain model should encapsulate complex behavior within the model.</span></span> <span data-ttu-id="80138-348">特別是實體，不應該只是屬性集合。</span><span class="sxs-lookup"><span data-stu-id="80138-348">Entities, in particular, should not merely be collections of properties.</span></span> <span data-ttu-id="80138-349">當領域模型缺少行為且只代表系統的狀態時，即為 [Anemic 模型](http://deviq.com/anemic-model/)，DDD 中並不需要此模型。</span><span class="sxs-lookup"><span data-stu-id="80138-349">When the domain model lacks behavior and merely represents the state of the system, it is said to be an [anemic model](http://deviq.com/anemic-model/), which is undesirable in DDD.</span></span>

<span data-ttu-id="80138-350">除了這些模型類型，DDD 通常還會採用多種模式：</span><span class="sxs-lookup"><span data-stu-id="80138-350">In addition to these model types, DDD typically employs a variety of patterns:</span></span>

-   <span data-ttu-id="80138-351">[儲存機制](http://deviq.com/repository-pattern/)，用於抽象化持續性詳細資料。</span><span class="sxs-lookup"><span data-stu-id="80138-351">[Repository](http://deviq.com/repository-pattern/), for abstracting persistence details.</span></span>

-   <span data-ttu-id="80138-352">[Factory](https://en.wikipedia.org/wiki/Factory_method_pattern)，用於封裝複雜的物件建立。</span><span class="sxs-lookup"><span data-stu-id="80138-352">[Factory](https://en.wikipedia.org/wiki/Factory_method_pattern), for encapsulating complex object creation.</span></span>

-   <span data-ttu-id="80138-353">領域事件，用於分離相依行為與觸發行為。</span><span class="sxs-lookup"><span data-stu-id="80138-353">Domain events, for decoupling dependent behavior from triggering behavior.</span></span>

-   <span data-ttu-id="80138-354">[服務](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)，用於封裝複雜行為及/或基礎結構實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="80138-354">[Services](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), for encapsulating complex behavior and/or infrastructure implementation details.</span></span>

-   <span data-ttu-id="80138-355">[命令](https://en.wikipedia.org/wiki/Command_pattern)，用於分離發出命令與執行命令本身。</span><span class="sxs-lookup"><span data-stu-id="80138-355">[Command](https://en.wikipedia.org/wiki/Command_pattern), for decoupling issuing commands and executing the command itself.</span></span>

-   <span data-ttu-id="80138-356">[規格](http://deviq.com/specification-pattern/)，用於封裝查詢詳細資料。</span><span class="sxs-lookup"><span data-stu-id="80138-356">[Specification](http://deviq.com/specification-pattern/), for encapsulating query details.</span></span>

<span data-ttu-id="80138-357">DDD 也建議使用上述的全新架構，允許鬆散結合、封裝，以及可使用單元測試輕鬆驗證的程式碼。</span><span class="sxs-lookup"><span data-stu-id="80138-357">DDD also recommends the use of the Clean Architecture discussed previously, allowing for loose coupling, encapsulation, and code that can easily be verified using unit tests.</span></span>

### <a name="when-should-you-apply-ddd"></a><span data-ttu-id="80138-358">何時應該套用 DDD</span><span class="sxs-lookup"><span data-stu-id="80138-358">When Should You Apply DDD</span></span>

<span data-ttu-id="80138-359">DDD 相當適合商務 (不只是技術) 複雜度明顯很高的大型應用程式。</span><span class="sxs-lookup"><span data-stu-id="80138-359">DDD is well-suited to large applications with significant business (not just technical) complexity.</span></span> <span data-ttu-id="80138-360">該應用程式需要有領域專家的知識。</span><span class="sxs-lookup"><span data-stu-id="80138-360">The application should require the knowledge of domain experts.</span></span> <span data-ttu-id="80138-361">領域模型本身應該有代表商務規則和互動的明顯行為，而不只是在資料存放區中儲存及擷取各種記錄的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="80138-361">There should be significant behavior in the domain model itself, representing business rules and interactions beyond simply storing and retrieving the current state of various records from data stores.</span></span>

### <a name="when-shouldnt-you-apply-ddd"></a><span data-ttu-id="80138-362">何時不應該套用 DDD</span><span class="sxs-lookup"><span data-stu-id="80138-362">When Shouldn't You Apply DDD</span></span>

<span data-ttu-id="80138-363">DDD 牽涉到投資模型、架構和通訊，這對較小型的應用程式，或基本上只有 CRUD (建立/讀取/更新/刪除) 的應用程式，可能並不需要。</span><span class="sxs-lookup"><span data-stu-id="80138-363">DDD involves investments in modeling, architecture, and communication that may not be warranted for smaller applications or applications that are essentially just CRUD (create/read/update/delete).</span></span> <span data-ttu-id="80138-364">如果您選擇讓應用程式採用 DDD，但發現您的領域具有不含任何行為的 Anemic 模型，您可能需要重新思考做法。</span><span class="sxs-lookup"><span data-stu-id="80138-364">If you choose to approach your application following DDD, but find that your domain has an anemic model with no behavior, you may need to rethink your approach.</span></span> <span data-ttu-id="80138-365">您的應用程式可能不需要 DDD，或者您可能需要協助來重構應用程式，將商務邏輯封裝在領域模型中，而不是資料庫或使用者介面中。</span><span class="sxs-lookup"><span data-stu-id="80138-365">Either your application may not need DDD, or you may need assistance refactoring your application to encapsulate business logic in the domain model, rather than in your database or user interface.</span></span>

<span data-ttu-id="80138-366">混合式方法只會將 DDD 用於應用程式的異動或較複雜區域，而不會用於較簡單的 CRUD 或應用程式的唯讀部分。</span><span class="sxs-lookup"><span data-stu-id="80138-366">A hybrid approach would be to only use DDD for the transactional or more complex areas of the application, but not for simpler CRUD or read-only portions of the application.</span></span> <span data-ttu-id="80138-367">例如，如果您想要查詢資料來顯示報表或視覺化儀表板的資料，則不需要有彙總的條件約束。</span><span class="sxs-lookup"><span data-stu-id="80138-367">For instance, you needn't have the constraints of an Aggregate if you're querying data to display a report or to visualize data for a dashboard.</span></span> <span data-ttu-id="80138-368">針對這類需求，最好是使用個別且較簡單的讀取模型。</span><span class="sxs-lookup"><span data-stu-id="80138-368">It's perfectly acceptable to have a separate, simpler read model for such requirements.</span></span>

> ### <a name="references--domain-driven-design"></a><span data-ttu-id="80138-369">參考資料 - 領域驅動設計</span><span class="sxs-lookup"><span data-stu-id="80138-369">References – Domain-Driven Design</span></span>
> - <span data-ttu-id="80138-370">**DDD 簡單說明 (StackOverflow 解答)**</span><span class="sxs-lookup"><span data-stu-id="80138-370">**DDD in Plain English (StackOverflow Answer)**</span></span>  
> <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a><span data-ttu-id="80138-371">部署</span><span class="sxs-lookup"><span data-stu-id="80138-371">Deployment</span></span>

<span data-ttu-id="80138-372">不論應用程式的裝載位置，部署 ASP.NET Core 應用程式的程序都包含幾個步驟。</span><span class="sxs-lookup"><span data-stu-id="80138-372">There are a few steps involved in the process of deploying your ASP.NET Core application, regardless of where it will be hosted.</span></span> <span data-ttu-id="80138-373">第一個步驟是發佈應用程式，可透過 dotnet publish CLI 命令來完成。</span><span class="sxs-lookup"><span data-stu-id="80138-373">The first step is to publish the application, which can be done using the dotnet publish CLI command.</span></span> <span data-ttu-id="80138-374">這會編譯應用程式，並將執行應用程式所需的所有檔案都放在指定的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="80138-374">This will compile the application and place all of the files needed to run the application into a designated folder.</span></span> <span data-ttu-id="80138-375">當您從 Visual Studio 部署時，則會自動為您執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="80138-375">When you deploy from Visual Studio, this step is performed for you automatically.</span></span> <span data-ttu-id="80138-376">publish 資料夾包含應用程式及其相依性的 .exe 和 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="80138-376">The publish folder contains .exe and .dll files for the application and its dependencies.</span></span> <span data-ttu-id="80138-377">獨立應用程式還會包含 .NET 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="80138-377">A self-contained application will also include a version of the .NET runtime.</span></span> <span data-ttu-id="80138-378">ASP.NET Core 應用程式也會包含組態檔、靜態用戶端資產和 MVC 檢視。</span><span class="sxs-lookup"><span data-stu-id="80138-378">ASP.NET Core applications will also include configuration files, static client assets, and MVC views.</span></span>

<span data-ttu-id="80138-379">ASP.NET Core 應用程式是主控台應用程式，必須在伺服器開機時啟動，並在應用程式 (或伺服器) 損毀時重新啟動。</span><span class="sxs-lookup"><span data-stu-id="80138-379">ASP.NET Core applications are console applications that must be started when the server boots and restarted if the application (or server) crashes.</span></span> <span data-ttu-id="80138-380">您可以使用處理序管理員來自動化此程序。</span><span class="sxs-lookup"><span data-stu-id="80138-380">A process manager can be used to automate this process.</span></span> <span data-ttu-id="80138-381">ASP.NET Core 最常見的處理序管理員是 Linux 上的 Nginx 和 Apache，以及 Windows 上的 IIS 或 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="80138-381">The most common process managers for ASP.NET Core are Nginx and Apache on Linux and IIS or Windows Service on Windows.</span></span>

<span data-ttu-id="80138-382">除了處理序管理員，裝載於 Kestrel 網頁伺服器的 ASP.NET Core 應用程式必須使用反向 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="80138-382">In addition to a process manager, ASP.NET Core applications hosted in the Kestrel web server must use a reverse proxy server.</span></span> <span data-ttu-id="80138-383">反向 Proxy 伺服器會從網際網路接收 HTTP 要求，並在進行一些初步處理後，將其轉送至 Kestrel。</span><span class="sxs-lookup"><span data-stu-id="80138-383">A reverse proxy server receives HTTP requests from the internet and forwards them to Kestrel after some preliminary handling.</span></span> <span data-ttu-id="80138-384">反向 Proxy 伺服器為應用程式提供一層安全性，而且需要這些伺服器才能進行邊緣部署 (對網際網路流量公開)。</span><span class="sxs-lookup"><span data-stu-id="80138-384">Reverse proxy servers provide a layer of security for the application, and are required for edge deployments (exposed to traffic from the Internet).</span></span> <span data-ttu-id="80138-385">Kestrel 相對較新且尚未提供特定攻擊的防禦。</span><span class="sxs-lookup"><span data-stu-id="80138-385">Kestrel is relatively new and does not yet offer defenses against certain attacks.</span></span> <span data-ttu-id="80138-386">Kestrel 也不支援在相同的連接埠上裝載多個應用程式，因此無法搭配使用主機標頭等技術，以允許在相同的連接埠和 IP 位址上裝載多個應用程式。</span><span class="sxs-lookup"><span data-stu-id="80138-386">Kestrel also doesn't support hosting multiple applications on the same port, so techniques like host headers cannot be used with it to enable hosting multiple applications on the same port and IP address.</span></span>

![Kestrel 到網際網路](./media/image7-5.png)

<span data-ttu-id="80138-388">圖 7-5：裝載於 Kestrel 中反向 Proxy 伺服器後方的 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="80138-388">Figure 7-5 ASP.NET hosted in Kestrel behind a reverse proxy server</span></span>

<span data-ttu-id="80138-389">在另一個案例中，反向 Proxy 可能有助於使用 SSL/HTTPS 來保護多個應用程式。</span><span class="sxs-lookup"><span data-stu-id="80138-389">Another scenario in which a reverse proxy can be helpful is to secure multiple applications using SSL/HTTPS.</span></span> <span data-ttu-id="80138-390">在此情況下，只有反向 Proxy 需要設定 SSL。</span><span class="sxs-lookup"><span data-stu-id="80138-390">In this case, only the reverse proxy would need to have SSL configured.</span></span> <span data-ttu-id="80138-391">反向 Proxy 伺服器與 Kestrel 之間的通訊可透過 HTTP 進行，如圖 7-6 所示。</span><span class="sxs-lookup"><span data-stu-id="80138-391">Communication between the reverse proxy server and Kestrel could take place over HTTP, as shown in Figure 7-6.</span></span>

![](./media/image7-6.png)

<span data-ttu-id="80138-392">圖 7-6：裝載於受 HTTPS 保護之反向 Proxy 伺服器後方的 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="80138-392">Figure 7-6 ASP.NET hosted behind an HTTPS-secured reverse proxy server</span></span>

<span data-ttu-id="80138-393">一個越來越普及的方法，是將 ASP.NET Core 應用程式裝載於 Docker 容器，該容器接著可在本機裝載或部署至 Azure 進行雲端式裝載。</span><span class="sxs-lookup"><span data-stu-id="80138-393">An increasingly popular approach is to host your ASP.NET Core application in a Docker container, which then can be hosted locally or deployed to Azure for cloud-based hosting.</span></span> <span data-ttu-id="80138-394">Docker 容器可能會包含您的應用程式程式碼，該程式碼會在 Kestrel 上執行，並部署在反向 Proxy 伺服器後方，如上所示。</span><span class="sxs-lookup"><span data-stu-id="80138-394">The Docker container could contain your application code, running on Kestrel, and would be deployed behind a reverse proxy server, as shown above.</span></span>

<span data-ttu-id="80138-395">如果您在 Azure 上裝載應用程式，您可以使用 Microsoft Azure 應用程式閘道作為專用虛擬設備來提供數項服務。</span><span class="sxs-lookup"><span data-stu-id="80138-395">If you're hosting your application on Azure, you can use Microsoft Azure Application Gateway as a dedicated virtual appliance to provide several services.</span></span> <span data-ttu-id="80138-396">除了作為個別應用程式的反向 Proxy，應用程式閘道也可能提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="80138-396">In addition to acting as a reverse proxy for individual applications, Application Gateway can also offer the following features:</span></span>

-   <span data-ttu-id="80138-397">HTTP 負載平衡</span><span class="sxs-lookup"><span data-stu-id="80138-397">HTTP load balancing</span></span>

-   <span data-ttu-id="80138-398">SSL 卸載 (SSL 僅限網際網路)</span><span class="sxs-lookup"><span data-stu-id="80138-398">SSL offload (SSL only to Internet)</span></span>

-   <span data-ttu-id="80138-399">端對端 SSL</span><span class="sxs-lookup"><span data-stu-id="80138-399">End to End SSL</span></span>

-   <span data-ttu-id="80138-400">多網站路由 (單一應用程式閘道上最多可合併 20 個網站)</span><span class="sxs-lookup"><span data-stu-id="80138-400">Multi-site routing (consolidate up to 20 sites on a single Application Gateway)</span></span>

-   <span data-ttu-id="80138-401">Web 應用程式防火牆</span><span class="sxs-lookup"><span data-stu-id="80138-401">Web application firewall</span></span>

-   <span data-ttu-id="80138-402">WebSocket 支援</span><span class="sxs-lookup"><span data-stu-id="80138-402">Websocket support</span></span>

-   <span data-ttu-id="80138-403">進階診斷</span><span class="sxs-lookup"><span data-stu-id="80138-403">Advanced diagnostics</span></span>

<span data-ttu-id="80138-404">*如需 Azure 部署選項的詳細資訊，請參閱第 10 章。*</span><span class="sxs-lookup"><span data-stu-id="80138-404">*Learn more about Azure deployment options in Chapter 10.*</span></span>

> ### <a name="references--deployment"></a><span data-ttu-id="80138-405">參考資料 - 部署</span><span class="sxs-lookup"><span data-stu-id="80138-405">References – Deployment</span></span>
> - <span data-ttu-id="80138-406">**裝載和部署概觀**</span><span class="sxs-lookup"><span data-stu-id="80138-406">**Hosting and Deployment Overview**</span></span>  
> <https://docs.microsoft.com/aspnet/core/publishing/>
> - <span data-ttu-id="80138-407">**何時搭配使用 Kestrel 與反向 Proxy**</span><span class="sxs-lookup"><span data-stu-id="80138-407">**When to use Kestrel with a reverse proxy**</span></span>  
> <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - <span data-ttu-id="80138-408">**在 Docker 中裝載 ASP.NET Core 應用程式**</span><span class="sxs-lookup"><span data-stu-id="80138-408">**Host ASP.NET Core apps in Docker**</span></span>  
> <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - <span data-ttu-id="80138-409">**Azure 應用程式閘道簡介**</span><span class="sxs-lookup"><span data-stu-id="80138-409">**Introducing Azure Application Gateway**</span></span>  
> <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
<span data-ttu-id="80138-410">[上一頁] (common-client-side-web-technologies.md) [下一頁] (work-with-data-in-asp-net-core-apps.md)</span><span class="sxs-lookup"><span data-stu-id="80138-410">[Previous] (common-client-side-web-technologies.md) [Next] (work-with-data-in-asp-net-core-apps.md)</span></span>
