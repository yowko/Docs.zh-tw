---
title: "開發 ASP.NET Core MVC 應用程式"
description: "使用 ASP.NET Core 和 Azure 的現代化 Web 應用程式架構設計人員 |開發 ASP.NET Core MVC 應用程式"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 54e7ed6fff9ac709e411d0ac1e345c63fd753201
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2017
---
# <a name="develop-aspnet-core-mvc-apps"></a>開發 ASP.NET Core MVC 應用程式

> 「 不重要拿第一次。 務必日漸拿最後一次。 」  
> _-Andrew 搜尋和 David Thomas_

## <a name="summary"></a>總結

ASP.NET Core 是跨平台、 開放原始碼的架構，用於建置現代化的雲端最佳化 web 應用程式。 ASP.NET Core 應用程式是輕量且模組化的與相依性插入，在更高的可測試性及可維護性中啟用內建支援。 結合 MVC、 支援建置現代化 web 應用程式開發介面，除了檢視架構的應用程式，ASP.NET Core 是功能強大的架構，用來建置企業 web 應用程式。

## <a name="mapping-requests-to-responses"></a>將要求對應至回應

本質上 ASP.NET Core 應用程式會將內送要求對應到傳出回應。 在低的層級，做法是使用中介軟體，及簡單的 ASP.NET Core 應用程式和 microservices 可能同時包含完全自訂的中介軟體。 當使用 ASP.NET Core MVC 時，您可以考慮的工作稍微高的層級，*路由*，*控制器*，和*動作*。 每個傳入要求與應用程式的路由表，而且如果找到相符的路由，相關聯的動作方法 （屬於 「 控制器 」） 呼叫來處理要求。 如果找到符合的路由時，會呼叫錯誤處理常式 （在此情況下，傳回找不到結果）。

ASP.NET Core MVC 應用程式可以使用傳統的路由、 屬性路由，或兩者。 程式碼中，指定路由中所定義的傳統路由*慣例*在下列範例中使用類似的語法：

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

已在此範例中，加入名為 「 預設 」 的路由，路由表。 它會定義路由範本使用預留位置*控制器*，*動作*，和*識別碼*。控制器和動作的預留位置已經指定預設值 (「 組織 」 和 「 索引 」，分別)，而且識別碼預留位置是選擇性 (憑藉"？"套用至它)。 慣例此處定義狀態要求的第一個部分應該對應至控制器，到動作中，第二個部分的名稱，然後視第三個部分會代表 id 參數。 傳統的路由通常被定義在一個地方應用程式，例如設定類別方法中啟動。

屬性路由會直接套用至控制器和動作而不是指定全域。 這樣做讓它們很容易找到有關當您正在查看的特定方法，但意思路由資訊不保留在應用程式中的一個位置的好處。 屬性路由，您可以輕鬆地指定多個路由是給定的動作，以及結合控制器與動作之間的路由。 例如: 

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

可以在 [HttpGet] 上指定的路由，並將類似的屬性，避免需要加入 [路由\]屬性。 屬性路由也可以使用語彙基元來減少重複控制器或動作名稱的需求，如下所示：

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

一旦已路由，以比對給定的要求，但動作之前，呼叫方法，將會執行 ASP.NET Core MVC[模型繫結](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding)和[模型驗證](https://docs.microsoft.com/aspnet/core/mvc/models/validation)在要求上。 模型繫結會負責將傳入的 HTTP 資料轉換為.NET 型別指定為動作方法的參數來呼叫。 例如，如果動作方法預期 int id 參數，模型繫結會提供這個參數要求中提供的值。 若要這樣做，模型繫結會尋找已張貼的表單中的值、 路由本身中的值和查詢字串值。 假設找到 id 值，它會轉換成整數傳遞至動作方法之前。

繫結模型之後，但在呼叫動作方法之前，就會發生模型驗證。 模型驗證模型型別，會使用選用的屬性，並可協助確保提供的模型物件符合特定的資料需求。 某些值可指定為必要，或限制為特定長度或數字範圍，等等。如果驗證屬性會指定，但是模型不符合其需求，屬性 ModelState.IsValid 會是 false，並無法驗證規則集將可傳送到提出要求的用戶端。

如果您使用的模型驗證，您應該一律請檢查模型有效，然後再執行任何狀態改變命令，以確保您的應用程式未正確的資料損毀。 您可以使用[篩選](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters)避免需要此加入程式碼中的每個動作。 ASP.NET Core MVC 篩選條件提供一種攔截的要求，群組，以便一般原則與跨領域考量可以套用以目標為基礎。 篩選可以套用到個別的動作，整個控制站，或全域應用程式。

針對 web 應用程式開發介面，支援 ASP.NET Core MVC [*內容交涉*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting)，允許以指定應如何格式化回應要求。 根據要求中提供的標頭，傳回資料的動作，將會格式化 XML、 JSON 或另一種支援的格式的回應。 這項功能可讓相同的 API 以供不同的資料格式需求的多個用戶端。

> ### <a name="references--mapping-requests-to-responses"></a>參考 – 對應至回應的要求
> - **路由至控制器動作**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **模型繫結**https://docs.microsoft.com/aspnet/core/mvc/models/model-binding
> - **模型驗證**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **篩選**https://docs.microsoft.com/aspnet/core/mvc/controllers/filters

## <a name="working-with-dependencies"></a>處理的相依性

ASP.NET Core 已內建支援，並在內部使用 ant colony optimization[相依性插入](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)。 相依性插入是啟用的應用程式的不同部分之間的鬆散偶合的技術。 鬆散偶合是合理的因為它可更輕鬆地隔離的應用程式，以便進行測試或取代組件。 您也可以比較不可能的應用程式的一個部分中的變更將會有非預期的影響應用程式中其他地方。 相依性插入為基礎的相依性反向原則，和通常是達到的開啟/關閉的原則機碼。 當評估您的應用程式具其相依性的運作方式，請注意[靜態黏貼](http://deviq.com/static-cling/)程式碼嗅覺並記住 aphorism"[新是黏附](http://ardalis.com/new-is-glue)。 」

您的類別呼叫靜態方法，或存取靜態屬性，它有副作用或相依性基礎結構時，就會發生靜態黏貼。 例如，如果您有個方法，呼叫靜態方法，後者接著寫入資料庫，您的方法資料庫緊密結合。 任何項目會中斷該資料庫的呼叫將會中斷您的方法。 因為這類測試需要模擬商業文件庫模擬靜態的呼叫，或只可使用測試資料庫中進行測試，測試這種方法很難。 靜態沒有基礎結構，特別是那些會完全無狀態，任何相依性的呼叫是呼叫，並結合或可測試性 （除了結合靜態呼叫本身的程式碼） 上不會影響正常的。

許多開發人員了解的風險靜態黏貼 」 以及 「 全域狀態，但將仍緊密結合透過直接具現化的特定實作的程式碼。 「 新 」 黏附是提醒的這個結合，並不使用新的關鍵字，使用一般 condemnation。 就如同處理靜態方法呼叫時，通常沒有任何外部的相依性的類型的新執行個體執行不緊密結合程式碼來實作詳細資料或讓測試更困難。 但是類別具現化，每次需要只長的時間是否合理硬式編碼至該特定執行個體的特定位置，或如果可能更好的設計，以要求該執行個體做為相依性的考量。

### <a name="declare-your-dependencies"></a>宣告相依性

ASP.NET Core 建置周圍有方法和類別宣告它們的相依性，要求它們做為引數。 ASP.NET 應用程式通常設定在啟動類別中，而其本身設定為支援數個時間點的相依性插入。 如果您啟動的類別建構函式，它可以要求相依性，透過建構函式，如下所示：

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

啟動類別有趣的是，因為它沒有明確的型別需求。 它不會繼承特殊的啟動基底類別，也不會實作任何特定的介面。 您可以提供給它的建構函式，而且可以指定您想要多個建構函式參數。 您已設定您的應用程式的 web 主機啟動時，它會呼叫您告知它使用，請啟動類別，並會使用相依性插入來填入啟動類別需要任何相依性。 當然，如果您要求不會設定 ASP.NET Core 所使用的服務容器中的參數，您會得到例外狀況，但只要您從相依性容器知道，您可以要求您想要的任何項目。

相依性插入是內建您的 ASP.NET Core 應用程式，從一開始，當您建立啟動的執行個體。 它不會那里停止啟動類別。 您也可以要求中設定方法的相依性：

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

ConfigureServices 方法是以這種行為; 例外狀況它必須採取別的 IServiceCollection 只有一個參數。 它實際上不需要支援相依性插入，因為它會負責將物件加入至服務容器，一方面，而且在另有存取所有目前設定的服務，透過 IServiceCollection 參數。 因此，您可以使用啟動類別，做為參數所需的服務要求，或在 ConfigureServices IServiceCollection 所使用的每個組件中的 ASP.NET Core services 集合中定義的相依性。

> [!NOTE]
> 如果您需要確保可啟動類別的特定服務，您可以設定它們使用 WebHostBuilder 和其 ConfigureServices 方法。

啟動類別是您如何結構 ASP.NET Core 應用程式，控制站，以篩選器，以您自己的服務中介軟體的其他部分的模型。 在每個案例中，您應該遵循[明確的相依性原則](http://deviq.com/explicit-dependencies-principle/)、 要求相依性而不是直接建立它們，以及利用整個應用程式的相依性插入。 請小心的位置和方式您直接具現化實作中，特別是 「 服務 」 和 「 使用基礎結構，或具有副作用的物件。 偏好使用定義在您的應用程式的核心，而且在做為引數傳遞給特定的實作類型的硬式編碼參考的抽象概念。

## <a name="structuring-the-application"></a>結構化應用程式

整合應用程式通常具有單一進入點。 在 ASP.NET Core web 應用程式的進入點將會是 ASP.NET Core web 專案。 不過，這不表示方案應包含只在單一專案中。 它是用於切割有所依循的重要性分離到不同的圖層的應用程式。 一旦分解為圖層，就很有幫助超越資料夾，以不同的專案，可以協助您達成更好的封裝。 最好的方法來達成這些目標與 ASP.NET Core 應用程式是架構的一種全新中第 5 章討論。 這個方法時，下列應用程式的方案會組成個別的程式庫 UI、 基礎結構，和 ApplicationCore。

除了這些專案中，個別的測試專案也包含 （在第 9 章討論測試）。

應用程式的物件模型和介面應該放在 ApplicationCore 專案。 這個專案將會較少的相依性越好，而方案中的其他專案會參考它。 需要保存的商務實體會定義於 ApplicationCore 專案，因為不直接相依於基礎結構的服務。

實作詳細資料，例如持續性的執行方式，或如何可能會傳送通知給使用者，會保留在基礎結構專案。 這個專案會參考 Entity Framework Core，例如實作特定封裝，但是不應該公開有關這些專案以外的其他實作詳細資料。 基礎結構服務和儲存機制，則應該實作 ApplicationCore 專案中所定義的介面和其持續性實作會負責擷取和儲存 ApplicationCore 中定義的實體。

ASP.NET Core 專案本身會負責任何 UI 層級的考量，但不是應包含商務邏輯或基礎結構詳細資料。 事實上，在理想情況下它不應該甚至有相依性基礎結構專案中，將有助於確保不小心引入兩個專案之間沒有相依性。 這可以使用第三方 DI 容器像 StructureMap，可讓您定義 DI 規則中每個專案中的登錄類別來達成。

若要減少應用程式的實作詳細資料的另一種方法是讓應用程式呼叫 microservices，可能是部署在個別的 Docker 容器中。 這提供更佳的考量，比利用 DI 兩個專案之間的去耦合分隔，但具有額外的複雜性。

### <a name="feature-organization"></a>功能的組織

根據預設，ASP.NET Core 應用程式會組織包含控制器和檢視，和經常 ViewModels 及其資料夾結構。 用戶端程式碼來支援這些伺服器端結構通常會儲存個別的 wwwroot 資料夾中。 不過，大型應用程式可能會遇到向此組織中，問題，因為通常使用任何特定功能需要這些資料夾間跳躍。 這會取得越來越多的每個資料夾中檔案和資料夾數目增加時，導致大量的方案總管 中捲動困難。 這個問題的其中一個解決方案是將應用程式程式碼的組織*功能*而不是由檔案類型。 此組織樣式通常稱為資料夾功能或功能配量 (請參閱：[垂直配量](http://deviq.com/vertical-slices/))。

ASP.NET Core MVC 支援針對此用途的區域。 使用區域，您可以建立不同的控制器和檢視資料夾 （以及任何相關聯的模型） 中每個區域的資料夾集。 圖 7-1 顯示使用區域的範例資料夾結構。

![](./media/image7-1.png)

圖 7-1 範例區域組織

當使用區域，您必須使用屬性裝飾的控制站與它們所隸屬之區域的名稱：

```csharp
[Area("Catalog")]
public class HomeController
{}
```

您也需要將區域支援加入至您的路由：

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

除了區域的內建支援，您也可以使用自己的資料夾結構和慣例，來取代屬性和自訂路由。 這樣可讓您能夠檢視、 控制站等，保留更平面的階層架構，更輕鬆查看所有相關的每項功能在單一位置的檔案未包含不同的資料夾的功能資料夾。

ASP.NET Core 使用內建的慣例類型，來控制其行為。 您可以修改或取代這些慣例。 例如，您可以建立會自動收到根據命名空間 （這通常相互關聯控制站所在的資料夾） 指定之控制器的功能名稱的慣例：

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

您再指定此慣例做為選項的 MVC 支援加入應用程式中 ConfigureServices 時：

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC 也使用的慣例，來找出檢視。 您可以覆寫它以自訂的慣例，以便檢視會位於功能資料夾 （使用上面 FeatureConvention 所提供的功能名稱）。 您可以深入了解這種方法，並從 MSDN 文章中，下載工作範例[功能配量的 ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx)。

### <a name="cross-cutting-concerns"></a>跨領域考量

當應用程式成長時，會變得越來越重要分離出來跨領域考量，以消除重複，並維持一致性。 跨領域考量 ASP.NET Core 應用程式中的一些範例是驗證、 模型的驗證規則、 輸出快取和錯誤處理，雖然還有許多其他。 ASP.NET Core MVC[篩選](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters)可讓您執行程式碼之前或之後要求處理管線中的特定步驟。 例如，篩選可以執行之前和之後模型繫結、 之前和之後的動作，或之前和之後的動作結果。 您也可以使用授權篩選條件來控制存取其餘的管線。 如果設定數字 7-2 會顯示如何篩選器，透過要求執行流程。

![要求會透過授權篩選條件、 資源篩選器、 模型繫結、 動作篩選條件、 動作執行和動作結果轉換、 例外狀況篩選條件、 結果篩選條件，以及結果執行處理。 外的方式，是只處理要求結果篩選條件和資源的篩選條件才能成為傳送至用戶端的回應。](./media/image7-2.png)

圖 7-2 要求執行透過篩選器和要求管線。

篩選條件通常實作為屬性，以便您可以套用它們控制器或動作。 當以這種方式，在動作層級覆寫或組建控制器層級上指定的篩選器時指定的篩選條件加入本身的覆寫全域篩選。 例如，\[路由\]屬性可以用來建置控制器和動作之間的路由。 同樣地，授權可以在控制器層級設定，然後覆寫個別的動作，如下列範例所示：

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

第一個方法，也就是登入，會使用 AllowAnonymous 篩選條件 （屬性），來覆寫在控制器層級設定的授權篩選。 ForgotPassword 動作 （和沒有 AllowAnonymous 屬性的類別中的任何其他動作），將需要已驗證的要求。

可以使用篩選器，以消除重複的常見的錯誤處理原則的應用程式開發介面的形式。 比方說，一般的 API 原則會傳回找不到回應要求參考索引鍵不存在，並不正確的要求回應，如果模型驗證失敗。 下列範例會示範這些動作中的兩個原則：

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

不允許您的動作方法，就會散布與條件式程式碼如下。 相反地，提取到可以做為所需的基礎套用的篩選條件的原則。 在此範例中，模型的驗證檢查，應該將命令傳送給 API 的任何時間，可能會取代下列屬性：

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

同樣地，篩選可以用來檢查記錄是否存在，且之前執行的動作，因而不須執行這些檢查的動作中傳回 404。 拉出一般慣例並組織您的解決方案基礎結構程式碼和商務邏輯分開 UI 之後，應該是極精簡您的 MVC 動作方法：

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

閱讀更多有關執行篩選器與 MSDN 文章中，從下載的工作範例[真實世界 ASP.NET Core MVC 篩選條件](https://msdn.microsoft.com/magazine/mt767699.aspx)。

> ### <a name="references--structuring-applications"></a>參考 – 建構應用程式
> - **區域**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN – 適用於 ASP.NET Core MVC 功能配量**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **篩選**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN – 真實世界 ASP.NET Core MVC 篩選條件**  
> <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>安全性

保護 web 應用程式是大型的主題中，但許多考量。 在其最基本的層級安全性牽涉到確保您知道誰給定的要求是來自，，然後確保該要求只具有其應有的資源的存取權。 驗證是比較使用受信任的資料存放區中的要求，請參閱是否要求應該被視為來自已知的實體提供認證的程序。 授權是限制存取特定資源，根據使用者識別的程序。 第三個安全性問題從第三方，其至少應該竊聽保護要求[確保您的應用程式使用 SSL](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl)。

### <a name="authentication"></a>驗證

您可以使用來支援您的應用程式的登入功能的成員資格系統 ASP.NET Core 識別。 它具有支援本機使用者帳戶以及外部登入提供者支援的提供者的 Microsoft 帳戶、 Twitter、 Facebook、 Google、 等等。 除了 ASP.NET Core 身分識別，您的應用程式可以使用 windows 驗證，或協力廠商身分識別提供者喜歡[Identity Server](https://github.com/IdentityServer/IdentityServer4)。

如果選取個別的使用者帳戶選項時，ASP.NET Core 識別隨附於新專案範本。 此範本包含註冊、 登入、 外部登入、 忘記密碼和其他功能的支援。

![](./media/image7-3.png)

圖 7-3 選取個別使用者帳戶，才能有預先設定的身分識別。

識別身分支援設定於啟動時，在 ConfigureServices 和設定：

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

請務必 UseIdentity 出現之前 UseMvc 設定方法中。 在設定時識別 ConfigureServices，您會發現 AddDefaultTokenProviders 呼叫。 這會有與語彙基元可用於安全 web 通訊，但改為建立可傳送給透過 SMS 或電子郵件中，以確認其身分的使用者提示的提供者是指無關。

您可以深入了解[設定雙因素驗證](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)和[啟用外部登入提供者](https://docs.microsoft.com/aspnet/core/security/authentication/social/)從官方 ASP.NET Core 文件。

### <a name="authorization"></a>授權

授權的最簡單形式牽涉到限制匿名使用者存取。 這可藉由將只要套用\[授權\]屬性到特定的控制器或動作。 如果角色正在使用中，屬性可以進一步擴充使用者屬於特定角色，限制存取，如下所示：

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

在此情況下，屬於 HRManager 或財務角色 （或兩者） 的使用者將會讓 SalaryController 存取。 若要要求使用者屬於多個角色 （不只是其中幾個），您可以套用的屬性多次，每次指定必要的角色。

指定組特定的角色，因為在許多不同的控制器和動作的字串會導致非預期的重複。 您可以設定授權原則，封裝授權規則，，然後在套用時指定的原則，而不是個別角色\[授權\]屬性：

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

使用原則，如此一來，您可以分隔的一種限制從特定角色或套用至該規則的動作。 稍後，如果您建立新的角色必須要有特定資源的存取權，您可以只更新原則，而不是更新角色的每個清單上每個\[授權\]屬性。

#### <a name="claims"></a>宣告

宣告是使用者的名稱/值組代表屬性的已驗證。 例如，您可能會宣告的形式儲存使用者的員工數目。 宣告可用做為授權原則的一部分。 您可以建立稱為 「 EmployeeOnly 」 原則，需要有的宣告，稱為 「 EmployeeNumber"，如本範例所示：

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

這個原則無法再搭配\[授權\]來保護任何控制器和/或動作，如上面所述的屬性。

#### <a name="securing-web-apis"></a>保護 Web 應用程式開發介面

大部分 web 應用程式開發介面應該實作權杖為基礎的驗證系統。 無狀態而設計，可調整權杖驗證。 在權杖為基礎的驗證系統中，用戶端必須先通過驗證的驗證提供者。 如果成功，用戶端會發出的權杖，只是密碼編譯方面有意義的字元字串。 當用戶端再需要發出要求，應用程式開發介面時，它會做為要求標頭加入這個語彙基元。 伺服器接著會驗證之前完成要求，要求標頭中找到的語彙基元。 圖 7-4 將示範此程序。

![TokenAuth](./media/image7-4.png)

**圖 7-4。** Web api 的權杖型驗證。

> ### <a name="references--security"></a>參考 – 安全性
> - **安全性文件概觀**  
> https://docs.microsoft.com/aspnet/core/security/
> - **強制執行的 ASP.NET Core 應用程式中的 SSL**  
> <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **身分識別簡介**  
> <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **授權簡介**  
> <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **在 Azure App Service API 應用程式的驗證和授權**  
> <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>

## <a name="client-communication"></a>用戶端通訊

除了網頁和 web 應用程式開發介面透過資料的要求回應，ASP.NET Core 應用程式可以直接與連線的用戶端通訊。 此輸出的通訊都可以使用各種傳輸技術，最常見的是 WebSockets。 ASP.NET Core SignalR 是程式庫，可簡化種類的應用程式伺服器到用戶端上的通訊功能。 SignalR 支援各種不同的傳輸技術，包括 WebSockets，並將實作細節，從開發人員抽離多抽象化出來。

ASP.NET Core SignalR 目前正在進行程式開發，並將可在 ASP.NET Core 的下一個版本。 不過，其他[開啟原始碼 WebSockets 程式庫](https://github.com/radu-matei/websocket-manager)目前可用。

即時的用戶端通訊，是否使用 WebSockets 直接或其他技術，可用於各種不同的應用程式案例。 其中某些範例包括：

-   聊天室的即時應用程式

-   監視應用程式

-   工作進度更新

-   通知

-   互動式 forms 應用程式

當建置到應用程式的用戶端通訊時，是通常兩個元件：

-   伺服器端連接管理員 （SignalR 中樞，WebSocketManager WebSocketHandler）

-   用戶端程式庫

用戶端並不限於瀏覽器 – 行動裝置應用程式、 主控台應用程式和其他原生應用程式也可以使用 SignalR/WebSockets 來通訊。 下列簡單程式會回應所有內容傳送到交談應用程式主控台中，做為 WebSocketManager 範例應用程式的一部分：

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

請考慮的方式應用程式直接與用戶端應用程式，並考慮是否即時通訊將會提升應用程式的使用者體驗。

> ### <a name="references--client-communication"></a>參考 – 用戶端通訊
> - **ASP.NET Core SignalR**  
> <https://github.com/aspnet/SignalR>
> - **WebSocket 管理員**  
> https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>網域導向設計 – 應該套用嗎？

網域導向設計 (DDD) 是建置軟體強調將焦點放在敏捷式軟體開發方法*商務網域*。 就會將重點通訊以及與商務網域 expert(s) 者可以與開發人員提供實際系統的運作方式的互動。 比方說，如果您正在建置處理股票交易系統，您的網域專家可能經驗豐富的內建 broker。 DDD 設計來處理大型、 複雜的商務問題，且通常不適合更小、 更簡單的應用程式，因為了解與模型化的網域中的投資不值得這樣做。

您的小組 （包括非技術性的專案關係人和參與者） 建置軟體遵循 DDD 方法時，應該開發*通用語言*問題空間。 也就是相同的術語應用於真實世界概念正在模型化、 軟體對等項目，以及可能存在保存概念 （例如，資料庫資料表） 的任何結構。 因此，通用語言中所述的概念應該會促使您*網域模型*。

網域模型被組成之間的互動來代表系統的行為的物件。 這些物件可能會分成下列類別：

-   [實體](http://deviq.com/entity/)，代表與身分識別的執行緒的物件。 實體通常儲存在持續性索引鍵，它們可以稍後擷取。

-   [彙總](http://deviq.com/aggregate-pattern/)，代表應該保存做為一個單位的物件群組。

-   [值物件](http://deviq.com/value-object/)，代表可以根據其屬性值的總和比較的概念。 例如，DateRange 組成的開始和結束日期。

-   [網域事件](https://martinfowler.com/eaaDev/DomainEvent.html)，這表示系統中發生的情況有興趣系統其他部分。

請注意 DDD 網域模型，應該將封裝複雜的模型中的行為。 實體，特別是，不只是應該屬性的集合。 當網域模型缺少行為，而且只是代表系統的狀態時，它會稱為[anemic 模型](http://deviq.com/anemic-model/)，也就是 DDD，不需要。

除了這些模型型別，DDD，通常採用各種不同的模式：

-   [儲存機制](http://deviq.com/repository-pattern/)，抽象持續性的詳細資料。

-   [Factory](https://en.wikipedia.org/wiki/Factory_method_pattern)，封裝建立複雜的物件。

-   網域事件，如分離相依觸發行為的行為。

-   [服務](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)、 封裝複雜的行為和 （或） 基礎結構的實作詳細資料。

-   [命令](https://en.wikipedia.org/wiki/Command_pattern)、 的分離發出命令，以及執行命令本身。

-   [規格](http://deviq.com/specification-pattern/)，封裝查詢詳細資料。

DDD 也建議使用全新的架構上文所述，允許鬆散偶合、 封裝 （encapsulation） 或驗證程式碼可以輕鬆地使用單元測試。

### <a name="when-should-you-apply-ddd"></a>當您將應該套用 DDD

DDD 是具備相當適合 （不會有只的技術） 的重要商務複雜的大型應用程式。 應用程式應該需要網域專家知識。 在網域模型本身，表示商務規則和互動，只是儲存和擷取從資料存放區的目前狀態的各種記錄之外，應該要有重要行為。

### <a name="when-shouldnt-you-apply-ddd"></a>當您不應該套用 DDD

DDD 牽涉到投資模型、 架構和可能不會發生的狀況的較小的應用程式或基本上就是只會執行 CRUD （建立/讀取/更新/刪除） 的應用程式的通訊。 如果您選擇接近您的應用程式遵循 DDD，但發現您的網域有使用任何行為 anemic 模型，您可能需要重新思考的方法。 您的應用程式可能不需要 DDD，或是您可能需要其他協助重構您的應用程式封裝在網域模型中，而不是在資料庫或使用者介面中的商務邏輯。

混合式方法就是只使用 DDD，交易式或更複雜應用程式的區域，但不是能用於簡單 CRUD 或唯讀狀態的應用程式部分。 比方說，您核對有彙總的條件約束，如果您要查詢的資料來顯示報表或儀表板的資料視覺化。 是完全可接受具有這類需求的個別、 簡單讀取的模型。

> ### <a name="references--domain-driven-design"></a>參考 – 網域導向設計
> - **DDD 以純文字的英文 (StackOverflow Answer)**  
> <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>部署

有幾個步驟部署您的 ASP.NET Core 應用程式，不論裝載的過程。 第一個步驟是發行應用程式，即可使用 dotnet 發行 CLI 命令。 這將會編譯應用程式，並將所有指定的資料夾中執行應用程式所需的檔案。 當您從 Visual Studio 部署時，則會自動為您執行此步驟。 發行資料夾包含應用程式和其相依性的.exe 和.dll 檔案。 獨立應用程式也會包含.NET 執行階段版本。 組態檔、 靜態用戶端資產和 MVC 檢視，也會包含 ASP.NET Core 應用程式。

ASP.NET Core 應用程式是主控台應用程式，必須先啟動時開機伺服器，並重新啟動，如果應用程式 （或伺服器） 損毀。 程序管理員可用來自動化此程序。 適用於 ASP.NET Core 最常見的程序管理員是 Nginx 和 Apache Linux 和 IIS 上的或在 Windows 上的 Windows 服務。

程序管理員，除了 Kestrel web 伺服器中裝載的 ASP.NET Core 應用程式必須使用反向 proxy 伺服器。 反向 proxy 伺服器會從網際網路接收 HTTP 要求，並轉送至 Kestrel 後一些初步處理。 反向 proxy 伺服器，則應用程式提供安全性層級和邊緣部署 （公開流量從網際網路） 所需。 Kestrel 相對較新且尚未提供特定攻擊的防禦。 Kestrel 也不支援裝載多個應用程式相同的連接埠，因此技術，如 主機標頭不能與它可以讓裝載在相同的連接埠和 IP 位址上的多個應用程式。

![網際網路 kestrel](./media/image7-5.png)

圖 7-5 Kestrel 中裝載的反向 proxy 伺服器後方的 ASP.NET

反向 proxy 可以是很有幫助的另一個案例是安全使用 SSL/HTTPS 的多個應用程式。 在此情況下，只有反向 proxy 需要設定 SSL。 反向 proxy 伺服器與 Kestrel 之間的通訊無法進行透過 HTTP，如圖 7-6 所示。

![](./media/image7-6.png)

圖 7-6 裝載 HTTPS 保護反向 proxy 伺服器後方的 ASP.NET

逐漸普及的一種方法是裝載 ASP.NET Core 應用程式在 Docker 容器中，然後可以裝載在本機或雲端裝載部署至 Azure。 Docker 容器可能包含 Kestrel 上, 執行您應用程式程式碼，並將部署在反向 proxy 伺服器後方，如上所示。

如果您正在裝載您在 Azure 上的應用程式，您可以為專用的虛擬應用裝置中使用 Microsoft Azure 應用程式閘道提供數個服務。 除了做為個別的應用程式的反向 proxy 時，應用程式閘道也可以提供下列功能：

-   HTTP 負載平衡

-   SSL 卸載 (SSL，只為網際網路)

-   端對端 SSL

-   多站台的路由 （合併在單一應用程式閘道上的最多 20 個站台）

-   Web 應用程式防火牆

-   Websocket 支援

-   進階的診斷

*深入了解章 10 中的 Azure 部署選項。*

> ### <a name="references--deployment"></a>參考 – 部署
> - **裝載和部署概觀**  
> <https://docs.microsoft.com/aspnet/core/publishing/>
> - **使用 Kestrel 透過反向 proxy 的時機**  
> <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **在 Docker 主機 ASP.NET Core 應用程式**  
> <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **介紹 Azure 應用程式閘道**  
> <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
[上一個](常見的用戶端-側邊-web-technologies.md) [下一步] (work-with-data-in-asp-net-core-apps.md)
