---
title: 開發 ASP.NET Core MVC 應用程式
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | 開發 ASP.NET Core MVC 應用程式
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 51feb770e84af170bf31a6ba363a1d9e72616284
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373768"
---
# <a name="develop-aspnet-core-mvc-apps"></a>開發 ASP.NET Core MVC 應用程式

> 「沒必要第一次就做對。 最後做對才重要。」  
> _- Andrew Hunt 和 David Thomas_

ASP.NET Core 是跨平台的開放原始碼架構，適用於建置現代化的雲端最佳化 Web 應用程式。 ASP.NET Core 應用程式是輕量型且模組化的，並內建相依性插入支援，以提高可測試性和可維護性。 ASP.NET Core 是建置企業級 Web 應用程式的強大架構，其結合 MVC，除了檢視型應用程式，還支援建置現代化 Web API。

## <a name="mvc-and-razor-pages"></a>MVC 與 Razor Pages

ASP.NET Core MVC 提供許多實用功能，可用來建置 Web API 及應用程式。 MVC 一詞代表 "Model-View-Controller"，是將回應使用者要求的作業分解成幾部分來負責的 UI 模式。 除了遵循這個模式外，您也可以在 ASP.NET Core 應用程式中，以 Razor Pages 實作功能。 Razor Pages 建置於 ASP.NET Core MVC 中，並使用相同的功能來路由、繫結模型等。但是，Razor Pages 沒有針對控制器、檢視等的個別資料夾及檔案，也不使用以屬性為基礎的路由，而是位於單一資料夾 ("/Pages") 中，根據其在此資料夾中的相對位置傳送路由，而且使用處理常式而非控制器動作來處理要求。

當您在建立新的 ASP.NET Core 應用程式時，應該在心中計畫好所要建置的應用程式會是什麼樣子。 在 Visual Studio 中，您將從多個範本中選擇。 最常見的三個專案範本是 Web API、Web 應用程式及 Web 應用程式 (Model-View-Controller)。 雖然您只能在初次建立專案時做決定，但是該決定並非不可改變。 Web API 專案使用標準 Model-View-Controller 控制器，根據預設它只缺少檢視。 同樣地，預設 Web 應用程式範本使用 Razor Pages，因此它也缺少檢視資料夾。 您可以之後將檢視資料夾新增到這些專案，來支援以檢視為基礎的行為。 根據預設，Web API 及 Model-View-Controller 專案不含 Pages 資料夾，但是您可以之後新增該資料夾，來支援以 Razor Pages 為基礎的行為。 您可以將這三個範本視為支援三種不同的預設使用者互動：資料 (Web API)、以頁面為基礎及以檢視為基礎。 然而如果您想，您可以在單一專案中將其任意混合與配對。

### <a name="why-razor-pages"></a>為什麼要使用 Razor Pages？

Razor Pages 在 Visual Studio 中是新 Web 應用程式的預設方法。 Razor Pages 提供較簡易的方法來建置以頁面為基礎的應用程式功能，像是非 SPA 表單。 使用控制器及檢視，應用程式常會有非常大型的控制器與許多不同的相依性及檢視模型搭配運作，並傳回許多不同的檢視。 這會導致許多複雜情況，而且經常造成控制器無法有效遵循單一職責原則或開放封閉原則。 Razor Pages 透過使用其 Razor 標記，封裝 Web 應用程式中指定邏輯「頁面」的伺服器端邏輯，解決了這個問題。 沒有伺服器端邏輯的 Razor 頁面可以只由 Razor 檔案 (例如 "Index.cshtml") 構成。 然而，多數非一般的 Razor Pages 會有相關的頁面模型類別，命名方式照慣例與 Razor 檔案相同，副檔名為 ".cs" (例如 "Index.cshtml.cs")。

Razor 頁面的頁面模型會合併 MVC 控制器及檢視模型的責任。 不會使用控制器動作方法來處理要求，而是執行像是 "OnGet()" 這類的頁面模型處理常式，並根據預設轉譯其相關頁面。 Razor Pages 簡化了在 ASP.NET Core 應用程式中建置個別頁面的程序，同時仍提供 ASP.NET Core MVC 的所有架構功能。 對以頁面為基礎的新功能來說，它們是相當好的預設選擇。

### <a name="when-to-use-mvc"></a>MVC 的使用時機

如果您在建置 Web API，MVC 模式會比嘗試使用 Razor Pages 更適合。 如果您的專案只會公開 Web API 端點，理想情況下您應該從 Web API 專案範本開始，但在其他情況下，將控制器及相關 API 端點新增到任何 ASP.NET Core 應用程式相當容易。 如果您想以最輕鬆的方式，將現有的應用程式從 ASP.NET MVC 5 或更舊版本移轉至 ASP.NET Core MVC，您也應該使用以檢視為基礎的 MVC 方法。 當您進行了首次移轉後，便可以評估是否適合使用 Razor Pages 進行新功能或甚至大規模的移轉。

不論您選擇使用 Razor Pages 或 MVC 檢視來建置 Web 應用程式，您的應用程式都會有相似的效能，而且將內含針對相依性插入、篩選、模型繫結及驗證等的支援。

## <a name="mapping-requests-to-responses"></a>將要求對應至回應

ASP.NET Core 應用程式基本上會將傳入要求對應至傳出回應。 在低階，這會透過中介軟體來完成，而簡單的 ASP.NET Core 應用程式和微服務可能只包含自訂中介軟體。 使用 ASP.NET Core MVC 時，您可以工作地更進階一些，從「路由」、「控制器」和「動作」的觀點來思考。 每個傳入要求會與應用程式的路由表進行比對，如果找到相符的路由，就會呼叫相關聯的動作方法 (屬於控制器) 來處理要求。 如果找不到相符的路由，就會呼叫錯誤處理常式 (在此情況下會傳回 NotFound 結果)。

ASP.NET Core MVC 應用程式可以使用慣例路由、屬性路由或兩者。 慣例路由是在程式碼中定義，並使用如下列範例所示的語法來指定路由「慣例」：

```csharp
app.UseMvc(routes =>
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

在此範例中，已將名為 "default" 的路由新增至路由表。 它定義一個路由範本，其中包含 _controller_、_action_ 和 _id_ 的預留位置。controller 和 action 預留位置已指定預設值 (分別是 "Home" 和 "Index")，而 id 預留位置則是選擇性的 (由於已套用 "?")。 此處定義的慣例指出要求的第一個部分應該對應至控制器的名稱，第二個部分對應至動作，而第三個部分 (如果需要) 則會代表 id 參數。 慣例路由通常是在應用程式的一個位置定義，例如在啟動類別的 Configure 方法中。

屬性路由會直接套用至控制器和動作，而不是全域指定。 其優點在於當您想要查看特定方法時，會更容易搜尋到這些路由，但也表示路由資訊不會保留在應用程式的一個位置。 透過屬性路由，您可以輕鬆地為一個動作指定多個路由，並合併控制器與動作之間的路由。 例如：

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
}
```

您可以在 [HttpGet] 和類似屬性上指定路由，避免需要新增個別 [Route] 屬性。 屬性路由也可以使用權杖，來減少重複控制器或動作名稱的需求，如下所示：

```csharp
[Route("[controller]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

Razor Pages 不會使用屬性路由。 您可以為 Razor 頁面指定其他路由範本資訊，作為其 `@page` 指示詞的一部份：

```csharp
@page "{id:int}"
```

在前一個範例中，問題中的頁面會將路由與整數 `id` 參數比對。 例如，位於 `/Pages` 根的 *Products.cshtml* 頁面會有下列路由：

```csharp
"/Products/123"
```

在指定的要求與路由經過比對之後，但呼叫動作方法之前，ASP.NET Core MVC 會在要求上執行[模型繫結](/aspnet/core/mvc/models/model-binding)和[模型驗證](/aspnet/core/mvc/models/validation)。 模型繫結會負責將傳入 HTTP 資料轉換成 .NET 類型，以指定為要呼叫之動作方法的參數。 例如，如果動作方法必須有 int id 參數，模型繫結會嘗試從要求隨附的值提供此參數。 若要這樣做，模型繫結會尋找以 POST 形式送出的值、路由本身中的值，以及查詢字串值。 假設找到 id 值，則會將它轉換成整數，再傳入動作方法。

在繫結模型之後，但呼叫動作方法之前，會進行模型驗證。 模型驗證會根據模型類型使用選用屬性，並可協助確保提供的模型物件符合特定資料需求。 某些值可能指定為必要，或限制為特定長度或數字範圍等等。如果指定了驗證屬性，但模型不符合其需求，則屬性 ModelState.IsValid 會是 false，而且會將失敗的驗證規則集傳送給提出要求的用戶端。

如果您使用模型驗證，請務必檢查模型是否有效，再執行任何狀態改變命令，以確保您的應用程式不會遭到無效資料損毀。 您可以使用[篩選條件](/aspnet/core/mvc/controllers/filters)，避免需要在每個動作中新增程式碼來執行此作業。 ASP.NET Core MVC 篩選條件可讓您攔截要求群組，以便可根據目標套用一般原則和跨領域關注。 您可以將篩選條件套用至個別動作、整個控制器，或針對應用程式全域套用。

對於 Web API，ASP.NET Core MVC 支援[「內容交涉」](/aspnet/core/mvc/models/formatting)，可讓要求指定回應的格式化方式。 根據要求中提供的標頭，傳回資料的動作會將回應格式化為 XML、JSON 或其他支援的格式。 這項功能可讓具有不同資料格式需求的多個用戶端使用相同的 API。

Web API 專案應該考慮使用 `[ApiController]` 屬性，該屬性可以套用到個別控制器、基底控制器類別或整個組件。 這個屬性會新增自動模型驗證檢查，任何無效模型的動作都將傳回附有驗證錯誤詳細資料的 BadRequest。 該屬性也要求所有動作都要有屬性路由，而非使用慣例路由，並會針對錯誤傳回更詳細的 ProblemDetails 資訊。

> ### <a name="references--mapping-requests-to-responses"></a>參考資料 - 將要求對應至回應
>
> - **路由至控制器動作**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **模型繫結**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - **模型驗證**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **篩選條件**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **ApiController 屬性**
 > <https://docs.microsoft.com/aspnet/core/web-api/?view=aspnetcore-2.2>

## <a name="working-with-dependencies"></a>使用相依性

ASP.NET Core 已內建支援，並在內部使用稱為[相依性插入](/aspnet/core/fundamentals/dependency-injection)的技術。 相依性插入是在應用程式的不同組件之間啟用鬆散結合的一項技術。 建議您啟用鬆散結合，因為它可讓您更輕鬆地隔離應用程式組件，以便進行測試或取代。 此外，變更應用程式的某個組件，也較不可能會對應用程式的其他地方造成非預期的影響。 相依性插入是以相依性反轉準則為基礎，而且通常是實現開啟/關閉準則的關鍵。 當您評估應用程式搭配其相依性的運作情況時，請注意[靜態黏貼](https://deviq.com/static-cling/)程式碼異味，並記住「[New 就是黏附](https://ardalis.com/new-is-glue)」此一箴言。

靜態黏貼發生於您的類別呼叫靜態方法或存取靜態屬性時，並對基礎結構具有副作用或相依性。 例如，如果您有一個方法呼叫靜態方法，而該方法接著寫入資料庫，則您的方法會與資料庫緊密結合。 任何中斷資料庫呼叫的項目都會中斷您的方法。 測試這類方法眾所周知很困難，因為這類測試需要商用模擬程式庫來模擬靜態呼叫，或只能透過適當的測試資料庫進行測試。 未相依於基礎結構的靜態呼叫 (特別是完全無狀態的呼叫) 可安心呼叫，不會影響結合或可測試性 (將程式碼結合到靜態呼叫本身除外)。

許多開發人員了解靜態黏貼和全域狀態的風險，但仍透過直接具現化將其程式碼緊密結合到特定實作。 「New 就是黏附」是為了提醒此結合，而不是一味譴責使用 `new` 關鍵字。 如同靜態方法呼叫，沒有外部相依性之類型的新執行個體，通常不會將程式碼緊密結合到實作詳細資料或讓測試更困難。 但每次具現化類別，請花點時間想一想，將該特定位置中的特定執行個體進行硬式編碼是否合理，還是最好設計成將執行個體當作相依性來要求。

### <a name="declare-your-dependencies"></a>宣告您的相依性

ASP.NET Core 的建置中心是讓方法和類別宣告其相依性，並以引數來要求這些相依性。 ASP.NET 應用程式通常是在啟動類別中設定，該類別本身已設定為支援多點相依性插入。 如果您的啟動類別具有建構函式，則可透過建構函式要求相依性，如下所示：

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

啟動類別有趣的是，它沒有明確的類型需求。 它不會繼承自特殊啟動基底類別，也不會實作任何特定介面。 您可以選擇是否要提供建構函式給它，並視需要在建構函式上指定許多參數。 當您為應用程式設定的 Web 主機啟動時，它會呼叫您指示它使用的啟動類別，並使用相依性插入來填入啟動類別所需的任何相依性。 當然，如果您要求 ASP.NET Core 所使用的服務容器中未設定的參數，您會收到例外狀況，但只要您堅持使用容器已知的相依性，您就可以要求任何想要的項目。

當您建立啟動執行個體時，您的 ASP.NET Core 應用程式從一開始就內建相依性插入。 啟動類別還不止於此。 您也可以在 Configure 方法中要求相依性：

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

此行為的例外是 ConfigureServices 方法；它只能接受 IServiceCollection 類型的一個參數。 它實際上不需要支援相依性插入，因為一方面它會負責將物件新增至服務容器，另一方面它可透過 IServiceCollection 參數存取目前所有已設定的服務。 因此，您可以透過要求所需的服務作為參數，或使用 ConfigureServices 中的 IServiceCollection，在啟動類別的每個部分使用 ASP.NET Core 服務集合中定義的相依性。

> [!NOTE]
> 如果您需要確保特定服務可供啟動類別使用，您可以使用 WebHostBuilder 及其 ConfigureServices 方法進行設定。

啟動類別是您應該如何建構 ASP.NET Core 應用程式之其他組件的模型，這些組件包括控制器、中介軟體、篩選條件到您自己的服務。 在每個案例中，您應該遵循[明確相依性準則](https://deviq.com/explicit-dependencies-principle/)，要求而不是直接建立相依性，並在您的應用程式中利用相依性插入。 對於您直接具現化實作的位置和方式請小心，特別是搭配基礎結構使用或具有副作用的服務和物件。 最好是使用您的應用程式核心中定義的抽象概念，並作為引數傳遞到特定實作類型的硬式編碼參考。

## <a name="structuring-the-application"></a>建構應用程式

整合型應用程式通常具有單一進入點。 在 ASP.NET Core Web 應用程式的案例中，此進入點會是 ASP.NET Core Web 專案。 不過，這並不表示方案應該只包含一個專案。 將應用程式分成不同的層級有助於遵循關注點分離。 一旦分成不同的層級，您就可以深入資料夾到個別專案，以協助達到更佳封裝。 使用 ASP.NET Core 應用程式達成這些目標的最佳方法，也就是第 5 章所討論的全新架構變化。 執行此方法之後，應用程式的方案將會包含 UI、基礎結構和 ApplicationCore 的個別程式庫。

除了這些專案，還會包含個別測試專案 (第 9 章中會討論測試)。

應用程式的物件模型和介面應該放在 ApplicationCore 專案中。 此專案會盡可能擁有很少的相依性，而且方案中的其他專案會參考它。 需要保存的商務實體是在 ApplicationCore 專案中定義，不直接相依於基礎結構的服務也是。

實作詳細資料 (例如持續性的執行方式或通知傳送給使用者的可能方式) 會保留在基礎結構專案中。 此專案會參考實作特定套件 (例如 Entity Framework Core)，但不應該公開專案以外的實作詳細資料。 基礎結構服務和儲存機制應該實作 ApplicationCore 專案中定義的介面，且其持續性實作會負責擷取及儲存 ApplicationCore 中定義的實體。

ASP.NET Core UI 專案會負責任何 UI 層級考量，但不應該包含商務邏輯或基礎結構詳細資料。 事實上，在理想情況下，它甚至不應該相依於基礎結構專案，如此將有助於確保不會意外引進兩個專案之間的相依性。 這可透過使用 Autofac 這類協力廠商 DI 容器來達成，該容器可讓您定義每個專案中模組類別內的 DI 規則。

另一個將應用程式與實作詳細資料分離的方法是，讓應用程式呼叫可能部署在個別 Docker 容器中的微服務。 這比在兩個專案之間利用 DI，提供甚至更佳的關注點分離和解耦，但複雜度也更高。

### <a name="feature-organization"></a>功能組織

根據預設，ASP.NET Core 應用程式組織其資料夾結構時會包含 Controllers 和 Views，通常也會包含 ViewModels。 支援這些伺服器端結構的用戶端程式碼通常會與 wwwroot 資料夾分開儲存。 不過，大型應用程式在使用此組織方式時可能會遇到問題，因為處理任何指定的功能通常需要在這些資料夾之間跳來跳去。 隨著每個資料夾中的檔案和子資料夾數目增加，這會變得越來越困難，而導致需要大幅捲動方案總管。 解決此問題的方法之一，是依「功能」而不是檔案類型來組織應用程式程式碼。 此組織樣式通常稱為功能資料夾或[功能分割](https://msdn.microsoft.com/magazine/mt763233.aspx) (另請參閱：[Vertical Slices](https://deviq.com/vertical-slices/) (垂直分割))。

基於此目的，ASP.NET Core MVC 會支援 Areas。 使用 Areas，您可以在每個 Areas 資料夾中建立不同的 Controllers 和 Views 資料夾集 (以及任何相關聯的模型)。 圖 7-1 顯示使用 Areas 的範例資料夾結構。

![範例區域組織](./media/image7-1.png)

**圖 7-1**. 範例區域組織

使用 Areas 時，您必須使用屬性以其所屬的區域名稱來裝飾控制器：

```csharp
[Area("Catalog")]
public class HomeController
{}
```

您也必須將區域支援新增至您的路由：

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

除了 Areas 的內建支援，您也可以使用自己的資料夾結構和慣例，來取代屬性和自訂路由。 這樣可讓您擁有不包含個別 Views、Controllers 等資料夾的功能資料夾，以保持更平面的階層架構，讓您可以更輕鬆地在單一位置查看每項功能的所有相關檔案。

ASP.NET Core 使用內建慣例類型來控制其行為。 您可以修改或取代這些慣例。 例如，您可以建立慣例，自動根據指定控制器的命名空間 (通常與控制器所在資料夾相互關聯) 取得其功能名稱：

```csharp
public class FeatureConvention : IControllerModelConvention
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

當您在 ConfigureServices 中將 MVC 支援新增至應用程式時，您可以接著指定此慣例作為選項：

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC 也會使用慣例來尋找檢視。 您可以使用自訂慣例將它覆寫，讓檢視位於功能資料夾中 (使用上述 FeatureConvention 提供的功能名稱)。 您可以從 MSDN 文章 [Feature Slices for ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx) (ASP.NET Core MVC 的功能分割)，深入了解此方法及下載工作範例。

### <a name="cross-cutting-concerns"></a>跨領域關注

隨著應用程式成長，排除跨領域關注因素對於去除重複和維持一致性會變得越來越重要。 ASP.NET Core 應用程式中的一些跨領域關注範例包括驗證 (authentication)、模型驗證 (validation) 規則、輸出快取和錯誤處理，還有許多其他範例。 ASP.NET Core MVC [篩選條件](/aspnet/core/mvc/controllers/filters)可讓您在要求處理管線的特定步驟之前或之後執行程式碼。 例如，您可以在模型繫結前後、動作前後或動作結果前後執行篩選條件。 您也可以使用授權篩選條件來控制管線其餘部分的存取。 圖 7-2 顯示如何透過篩選條件 (如已設定) 要求執行流程。

![要求處理會歷經授權篩選條件、資源篩選條件、模型繫結、動作篩選條件、動作執行和動作結果轉換、例外狀況篩選條件、結果篩選條件，以及結果執行。 在送出的過程，要求只會經過結果篩選條件和資源篩選條件的處理，然後便成為傳送至用戶端的回應。](./media/image7-2.png)

**圖 7-2**. 透過篩選準則和要求管線來執行要求。

篩選通常會實作為屬性，以便您將其套用至控制器或動作 (甚至是全域)。 以此方式新增時，在動作層級指定的篩選條件會覆寫在控制器層級指定的篩選條件或建置在其上，而後者本身會覆寫全域篩選條件。 例如，\[Route\] 屬性可用來建置控制器與動作之間的路由。 同樣地，授權可在控制器層級設定，然後由個別動作覆寫，如下列範例所示：

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous] // overrides the Authorize attribute
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

第一個方法 Login 使用 AllowAnonymous 篩選條件 (屬性)，來覆寫在控制器層級設定的 Authorize 篩選條件。 ForgotPassword 動作 (及不包含 AllowAnonymous 屬性之類別中的任何其他動作) 會需要已驗證的要求。

篩選條件可用來去除 API 之常見錯誤處理原則形式中的重複情況。 例如，一般 API 原則是在要求不存在的參考索引鍵時，傳回 NotFound 回應；如果模型驗證失敗，則傳回 BadRequest 回應。 下列範例將示範這兩個原則的運作方式：

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

請勿讓您的動作方法因為類似的條件程式碼而變得很雜亂。 相反地，請將原則提取到可視需要套用的篩選條件中。 在此範例中，任何時候將命令傳送至 API，都應該進行模型驗證檢查，該檢查可取代為下列屬性：

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

您可以藉由包含 [Ardalis.ValidateModel](https://www.nuget.org/packages/Ardalis.ValidateModel) 套件，來將 `ValidateModelAttribute` 新增到您的專案作為 NuGet 相依性。 針對 API，您可以使用 `ApiController` 屬性，在不需要個別 `ValidateModel` 篩選的情況下強制執行此行為。

同樣地，篩選條件可用來檢查記錄是否存在，並先傳回 404 再執行動作，因此不需要在動作中執行這些檢查。 一旦您取出一般慣例並組織方案，將基礎結構程式碼和商務邏輯與 UI 分隔開來之後，您的 MVC 動作方法應該會非常精簡：

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

您可以從 MSDN 文章 [Real World ASP.NET Core MVC Filters](https://msdn.microsoft.com/magazine/mt767699.aspx) (真實世界的 ASP.NET Core MVC 篩選條件)，深入了解如何實作篩選條件及下載工作範例。

> ### <a name="references--structuring-applications"></a>參考資料 - 建構應用程式
>
> - **區域**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN Magazine - Feature Slices for ASP.NET Core MVC (MSDN Magazine - ASP.NET Core MVC 的功能分區)**  
>   <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **篩選**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN - Real World ASP.NET Core MVC Filters (真實世界的 ASP.NET Core MVC 篩選條件)**  
>   <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>安全性

保護 Web 應用程式是很龐大的主題，其中包含許多考量。 最基本的安全性層級牽涉到確保您知道指定要求的來源，以及確保該要求只具有其應有的資源存取權。 驗證是比較要求隨附的認證與受信任資料存放區中的認證，來查看是否應該將要求視為來自已知實體的程序。 授權是根據使用者身分識別限制特定資源存取權的程序。 第三個安全性考量是防止第三方竊聽要求，您應該至少[確保應用程式使用 SSL](/aspnet/core/security/enforcing-ssl)。

### <a name="authentication"></a>驗證

ASP.NET Core Identity 是可用來支援應用程式登入功能的會員系統。 它具備本機使用者帳戶支援，以及來自 Microsoft 帳戶、Twitter、Facebook、Google 等提供者的外部登入提供者支援。 除了 ASP.NET Core Identity，您的應用程式也可以使用 Windows 驗證，或 [Identity Server](https://github.com/IdentityServer/IdentityServer4) 等協力廠商身分識別提供者。

如果選取 [個別使用者帳戶] 選項，ASP.NET Core Identity 會隨附於新的專案範本。 此範本包括註冊、登入、外部登入、忘記密碼和其他功能的支援。

![選取要預先設定身分識別的個別使用者帳戶](./media/image7-3.png)

**圖 7-3**. 選取 [個別使用者帳戶]，以預先設定身分識別。

身分識別是在啟動的 ConfigureServices 和 Configure 中設定：

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

在 Configure 方法中，UseIdentity 必須在 UseMvc 之前出現。 在 ConfigureServices 中設定身分識別時，您會注意到對 AddDefaultTokenProviders 的呼叫。 這與可用來保護 Web 通訊的權杖無關，而是指建立提示的提供者，這些提示可透過簡訊或電子郵件傳送給使用者，以確認其身分識別。

您可以從官方 ASP.NET Core 文件，深入了解如何[設定雙因素驗證](/aspnet/core/security/authentication/2fa)和[啟用外部登入提供者](/aspnet/core/security/authentication/social/)。

### <a name="authorization"></a>Authorization

授權的最簡單形式牽涉到限制匿名使用者的存取。 只要將 \[Authorize\] 屬性套用至特定控制器或動作，即可達成此目的。 如果角色正在使用中，您可以進一步擴充屬性，限制屬於特定角色之使用者的存取，如下所示：

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

在本例中，屬於 HRManager 或 Finance 角色 (或兩者) 的使用者可存取 SalaryController。 如果使用者必須屬於多個角色 (而不只是數個角色之一)，您可以套用屬性多次，並每次指定必要的角色。

將特定角色集指定為許多不同控制器和動作中的字串，可能會導致不想要的重複。 您可以設定封裝授權規則的授權原則，然後在套用 \[Authorize\] 屬性時指定原則，而不是個別角色：

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

以此方式使用原則，您就可以分隔特定角色限制使用的動作類型，或對其套用的規則。 稍後，如果您建立需要存取特定資源的新角色，您只要更新原則即可，而不需要在每個 \[Authorize\] 屬性上更新每個角色清單。

#### <a name="claims"></a>宣告

宣告是成對的名稱和數值，代表已驗證使用者的屬性。 例如，您可以將使用者的員工編號儲存為宣告。 宣告可接著作為授權原則的一部分使用。 您可以建立稱為 "EmployeeOnly" 的原則，該原則需要有稱為 "EmployeeNumber" 的宣告，如下列範例所示：

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

此原則可接著搭配 \[Authorize\] 屬性使用，以保護任何控制器及/或動作，如上所述。

#### <a name="securing-web-apis"></a>保護 Web API

大多數 Web API 應該實作權杖型驗證系統。 權杖驗證為無狀態並設計成可調整。 在權杖型驗證系統中，用戶端必須先向驗證提供者進行驗證。 如果成功，則會向用戶端發出權杖，這只是密碼編譯方面有意義的字元字串。 接著，當用戶端需要發出 API 要求時，就會新增此權杖作為要求的標頭。 伺服器接著會驗證要求標頭中找到的權杖，再完成要求。 圖 7-4 示範此程序。

![TokenAuth](./media/image7-4.png)

**圖 7-4**： Web API 的權杖型驗證

您可以使用像 [IdentityServer](https://github.com/IdentityServer) 這類開放原始碼工具，來建立自己的驗證服務、與 Azure AD 及 OAuth 整合，或實作服務。

#### <a name="custom-security"></a>自訂安全性

請特別小心加密、使用者成員資格或權杖產生系統的「自行」實作。 可供使用的商業及開放原始碼替代方案非常多，幾乎肯定會比自訂實作更安全。

> ### <a name="references--security"></a>參考資料 - 安全性
>
> - **安全性文件概觀**  
>   https://docs.microsoft.com/aspnet/core/security/
> - **Enforcing SSL in an ASP.NET Core App** (在 ASP.NET Core 應用程式中強制執行 SSL)  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **身分識別簡介**  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **授權簡介**  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Azure App Service 之 API Apps 的驗證和授權**  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>
> - **Identity Server**  
>   <https://github.com/IdentityServer>

## <a name="client-communication"></a>用戶端通訊

除了透過 Web API 提供頁面及回應資料要求，ASP.NET Core 應用程式還可以直接與連線的用戶端通訊。 此輸出通訊可以使用各種傳輸技術，最常見的是 WebSockets。 ASP.NET Core SignalR 是一種程式庫，可讓您簡單地將即時伺服器對用戶端通訊功能新增至應用程式。 SignalR 支援各種傳輸技術 (包括 WebSockets)，並從開發人員擷取許多實作詳細資料。

自 ASP.NET Core 版本 2.1 開始，已可使用 ASP.NET Core SignalR。

即時用戶端通訊 (不論是直接使用 WebSockets 或其他技術) 在許多不同的應用程式案例中都很有用。 其中某些範例包括：

- 即時聊天室應用程式

- 監控應用程式

- 工作進度更新

- 通知

- 互動式論壇應用程式

在應用程式中內建用戶端通訊時，通常有兩個元件：

- 伺服器端連線管理員 (SignalR 中樞、WebSocketManager、WebSocketHandler)

- 用戶端程式庫

用戶端不僅限於瀏覽器，行動裝置應用程式、主控台應用程式和其他原生應用程式也可以使用 SignalR/WebSockets 來通訊。 下列簡單程式會將所有傳送至交談應用程式的內容回應到主控台，以作為 WebSocketManager 範例應用程式的一部分：

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>
        {
            Console.WriteLine($"{arguments[0]} said: {arguments[1]}");
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
}
```

請考慮您的應用程式直接與用戶端應用程式通訊的方式，並考慮即時通訊是否會改善應用程式的使用者體驗。

> ### <a name="references--client-communication"></a>參考資料 - 用戶端通訊
>
> - **ASP.NET Core SignalR**  
>   <https://github.com/aspnet/SignalR>
> - **WebSocket Manager**  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>領域驅動設計 - 是否應該套用？

領域驅動設計 (DDD) 是建置軟體的敏捷式方法，重點強調「商務領域」。 它相當重視與商務領域專家的溝通和互動，這些專家會向開發人員說明真實世界系統的運作方式。 例如，如果您想要建置處理股票交易的系統，您的領域專家可能會是經驗豐富的股票交易員。 DDD 是專為處理複雜的大型商務問題所設計，通常不適用於較小、較簡單的應用程式，因為不值得投資了解領域及建立領域模型。

建置採用 DDD 方法的軟體時，您的小組 (包括非技術性專案關係人和參與者) 應該針對問題空間開發「通用語言」。 換句話說，您應該針對要模型化的真實世界概念、對等軟體，以及為了保存概念而可能存在的任何結構 (例如資料庫資料表) 使用相同的用語。 因此，通用語言中所述的概念應該會形成「領域模型」的基礎。

您的領域模型會包含彼此互動以代表系統行為的物件。 這些物件的分類如下：

- [實體](https://deviq.com/entity/)，代表具有身分識別執行緒的物件。 實體通常會儲存在使用金鑰的持續性儲存區中，稍後可予以擷取。

- [彙總](https://deviq.com/aggregate-pattern/)，代表應該當作一個單位保存的物件群組。

- [值物件](https://deviq.com/value-object/)，代表可根據其屬性值的總和比較的概念。 例如，由開始和結束日期組成的 DateRange。

- [領域事件](https://martinfowler.com/eaaDev/DomainEvent.html)，代表系統內發生的事件，系統的其他組件對這些事件會有興趣。

請注意，DDD 領域模型應該將複雜行為封裝在模型內。 特別是實體，不應該只是屬性集合。 當領域模型缺少行為且只代表系統的狀態時，即為 [Anemic 模型](https://deviq.com/anemic-model/)，DDD 中並不需要此模型。

除了這些模型類型，DDD 通常還會採用多種模式：

- [儲存機制](https://deviq.com/repository-pattern/)，用於抽象化持續性詳細資料。

- [Factory](https://en.wikipedia.org/wiki/Factory_method_pattern)，用於封裝複雜的物件建立。

- 領域事件，用於分離相依行為與觸發行為。

- [服務](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)，用於封裝複雜行為及/或基礎結構實作詳細資料。

- [命令](https://en.wikipedia.org/wiki/Command_pattern)，用於分離發出命令與執行命令本身。

- [規格](https://deviq.com/specification-pattern/)，用於封裝查詢詳細資料。

DDD 也建議使用上述的全新架構，允許鬆散結合、封裝，以及可使用單元測試輕鬆驗證的程式碼。

### <a name="when-should-you-apply-ddd"></a>何時應該套用 DDD

DDD 相當適合商務 (不只是技術) 複雜度明顯很高的大型應用程式。 該應用程式需要有領域專家的知識。 領域模型本身應該有代表商務規則和互動的明顯行為，而不只是在資料存放區中儲存及擷取各種記錄的目前狀態。

### <a name="when-shouldnt-you-apply-ddd"></a>何時不應該套用 DDD

DDD 牽涉到投資模型、架構和通訊，這對較小型的應用程式，或基本上只有 CRUD (建立/讀取/更新/刪除) 的應用程式，可能並不需要。 如果您選擇讓應用程式採用 DDD，但發現您的領域具有不含任何行為的 Anemic 模型，您可能需要重新思考做法。 您的應用程式可能不需要 DDD，或者您可能需要協助來重構應用程式，將商務邏輯封裝在領域模型中，而不是資料庫或使用者介面中。

混合式方法只會將 DDD 用於應用程式的異動或較複雜區域，而不會用於較簡單的 CRUD 或應用程式的唯讀部分。 例如，如果您想要查詢資料來顯示報表或視覺化儀表板的資料，則不需要有彙總的條件約束。 針對這類需求，最好是使用個別且較簡單的讀取模型。

> ### <a name="references--domain-driven-design"></a>參考資料 - 領域驅動設計
>
> - **DDD 簡單說明 (StackOverflow 解答)**  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>部署

不論應用程式的裝載位置，部署 ASP.NET Core 應用程式的程序都包含幾個步驟。 第一個步驟是發佈應用程式，可透過 dotnet publish CLI 命令來完成。 這會編譯應用程式，並將執行應用程式所需的所有檔案都放在指定的資料夾中。 當您從 Visual Studio 部署時，則會自動為您執行此步驟。 publish 資料夾包含應用程式及其相依性的 .exe 和 .dll 檔案。 獨立應用程式還會包含 .NET 執行階段版本。 ASP.NET Core 應用程式也會包含組態檔、靜態用戶端資產和 MVC 檢視。

ASP.NET Core 應用程式是主控台應用程式，必須在伺服器開機時啟動，並在應用程式 (或伺服器) 損毀時重新啟動。 您可以使用處理序管理員來自動化此程序。 ASP.NET Core 最常見的處理序管理員是 Linux 上的 Nginx 和 Apache，以及 Windows 上的 IIS 或 Windows 服務。

除了處理序管理員，裝載於 Kestrel 網頁伺服器的 ASP.NET Core 應用程式必須使用反向 Proxy 伺服器。 反向 Proxy 伺服器會從網際網路接收 HTTP 要求，並在進行一些初步處理後，將其轉送至 Kestrel。 反向 Proxy 伺服器為應用程式提供一層安全性，而且需要這些伺服器才能進行邊緣部署 (對網際網路流量公開)。 Kestrel 相對較新且尚未提供特定攻擊的防禦。 Kestrel 也不支援在相同的連接埠上裝載多個應用程式，因此無法搭配使用主機標頭等技術，以允許在相同的連接埠和 IP 位址上裝載多個應用程式。

![Kestrel 到網際網路](./media/image7-5.png)

**圖 7-5**。 ASP.NET 裝載于反向 proxy 伺服器後方的 Kestrel 中

在另一個案例中，反向 Proxy 可能有助於使用 SSL/HTTPS 來保護多個應用程式。 在此情況下，只有反向 Proxy 需要設定 SSL。 反向 Proxy 伺服器與 Kestrel 之間的通訊可透過 HTTP 進行，如圖 7-6 所示。

![裝載于受 HTTPS 保護之反向 proxy 伺服器後方的 ASP.NET](./media/image7-6.png)

**圖 7-6**。 裝載于受 HTTPS 保護之反向 proxy 伺服器後方的 ASP.NET

一個越來越普及的方法，是將 ASP.NET Core 應用程式裝載於 Docker 容器，該容器接著可在本機裝載或部署至 Azure 進行雲端式裝載。 Docker 容器可能會包含您的應用程式程式碼，該程式碼會在 Kestrel 上執行，並部署在反向 Proxy 伺服器後方，如上所示。

如果您在 Azure 上裝載應用程式，您可以使用 Microsoft Azure 應用程式閘道作為專用虛擬設備來提供數項服務。 除了作為個別應用程式的反向 Proxy，應用程式閘道也可能提供下列功能：

- HTTP 負載平衡

- SSL 卸載 (SSL 僅限網際網路)

- 端對端 SSL

- 多網站路由 (單一應用程式閘道上最多可合併 20 個網站)

- Web 應用程式防火牆

- WebSocket 支援

- 進階診斷

_如需 Azure 部署選項的詳細資訊，請參閱[第 10 章](development-process-for-azure.md)。_

> ### <a name="references--deployment"></a>參考資料 - 部署
>
> - **裝載和部署概觀**  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - **何時搭配使用 Kestrel 與反向 Proxy**  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **在 Docker 中裝載 ASP.NET Core 應用程式**  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Azure 應用程式閘道簡介**  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
>[上一頁](common-client-side-web-technologies.md)
>[下一頁](work-with-data-in-asp-net-core-apps.md)
