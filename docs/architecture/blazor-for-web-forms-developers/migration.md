---
title: 從 ASP.NET Web Forms 遷移至 Blazor
description: 瞭解如何將現有的 ASP.NET Web Forms 應用程式遷移至 Blazor。
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 46e3335ec6fe5671da75a868d94ace1abf9098b6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183837"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a>從 ASP.NET Web Forms 遷移至 Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

將程式碼基底從 ASP.NET Web form 遷移至 Blazor 是一項耗時的工作，需要進行規劃。 本章將概述此程式。 可以簡化轉換的專案，是為了確保應用程式遵守多*層式*架構，其中應用程式模型（在此案例中為 Web form）與商務邏輯分開。 這種層級的邏輯區隔，讓它清楚需要移至 .NET Core 和 Blazor 的內容。

在此範例中，會使用[GitHub](https://github.com/dotnet-architecture/eShopOnBlazor)上提供的 eShop 應用程式。 eShop 是一種目錄服務，透過表單輸入和驗證提供 CRUD 功能。

為什麼工作中的應用程式應該遷移至 Blazor？ 許多時候都不需要。 ASP.NET Web Forms 將繼續支援多年。 不過，已遷移的應用程式只支援 Blazor 所提供的許多功能。 這類功能包括：

* 架構中的效能改進，例如`Span<T>`
* 能夠以 WebAssembly 的形式執行
* Linux 和 macOS 的跨平臺支援
* 應用程式本機部署或共用架構部署，而不會影響其他應用程式

如果這些或其他新功能很吸引人，則在遷移應用程式時可能會有價值。 遷移可以採用不同的圖形;它可以是整個應用程式，或只是需要變更的特定端點。 遷移的決策最終是以開發人員要解決的商務問題為基礎。

## <a name="server-side-versus-client-side-hosting"></a>伺服器端與用戶端裝載的比較

如[裝載模型](hosting-models.md)一章所述，Blazor 應用程式可透過兩種不同的方式來主控：伺服器端和用戶端。 伺服器端模型會使用 ASP.NET Core SignalR 連接來管理 DOM 更新，同時在伺服器上執行任何實際的程式碼。 用戶端模型會在瀏覽器中以 WebAssembly 的形式執行，而且不需要伺服器連接。 有一些可能影響特定應用程式最適合的差異：

* 以 WebAssembly 的身分執行仍在開發中，而且可能不支援目前時間的所有功能（例如執行緒）
* 用戶端與伺服器之間的多對話通訊可能會導致伺服器端模式的延遲問題
* 對資料庫和內部或受保護的服務的存取，需要具有用戶端裝載的個別服務

在撰寫本文時，伺服器端模型更類似于 Web Forms。 本章大多著重于伺服器端裝載模型，因為它已準備好用於生產環境。

## <a name="create-a-new-project"></a>建立新專案

此初始遷移步驟是建立新的專案。 此專案類型是以 .NET Core 的 SDK 樣式專案為基礎，並簡化了先前的專案格式中所使用的許多樣板。 如需詳細資訊，請參閱[專案結構](project-structure.md)的相關章節。

建立專案之後，請安裝先前專案中使用的程式庫。 在較舊的 Web form 專案中，您可能已經使用了*封裝 .config*檔案來列出所需的 NuGet 套件。 在新的 SDK 樣式專案中，已使用`<PackageReference>`專案檔中的元素取代了*套件 .config* 。 這種方法的優點是所有相依性都是以可轉移方式安裝。 您只會列出您關心的頂層相依性。

您所使用的許多相依性都適用于 .NET Core，包括 Entity Framework 6 和 log4net。 如果沒有 .NET Core 或 .NET Standard 版本可用，則通常會使用 .NET Framework 版本。 您的里程可能會有所不同。 任何在 .NET Core 中無法使用的 API 都會造成執行階段錯誤。 Visual Studio 會通知您這類封裝。 專案的 [**參考**] 節點上會出現黃色圖示**方案總管**。

在以 Blazor 為基礎的 eShop 專案中，您可以看到已安裝的封裝。 先前，package 檔案會列出專案中使用的每個套件，導致檔案的長度幾乎 50*行。* *封裝*的程式碼片段是：

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

`<packages>`元素包含所有必要的相依性。 因為您需要這些套件，所以很難以識別其中包含哪些封裝。 有些`<package>`元素只會列出，以滿足您所需的相依性需求。

Blazor 專案會在專案檔的`<ItemGroup>`元素中列出您需要的相依性：

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

[Windows 相容性套件](/dotnet/core/porting/windows-compat-pack)是一個可簡化 Web form 開發人員生命週期的 NuGet 套件。 雖然 .NET Core 是跨平臺的，但某些功能只能在 Windows 上使用。 藉由安裝相容性套件，可取得 Windows 特有的功能。 這類功能的範例包括登錄、WMI 和目錄服務。 套件增加了20000個 Api，並啟用許多您可能已經熟悉的服務。 EShop 專案不需要相容性套件;但是，如果您的專案使用 Windows 特有的功能，封裝就能減輕遷移的工作。

## <a name="enable-startup-process"></a>啟用啟動程式

Blazor 的啟動程式已從 Web Forms 變更，並遵循類似于其他 ASP.NET Core 服務的設定。 當主控伺服器端時，Blazor 元件會當做一般 ASP.NET Core 應用程式的一部分來執行。 當使用 WebAssembly 在瀏覽器中裝載時，Blazor 元件會使用類似的主控模型。 其差異在於，元件會以個別服務的方式，從任何後端進程執行。 不論是哪一種情況，啟動都很類似。

*Global.asax.cs*檔案是 Web Forms 專案的預設啟動頁面。 在 eShop 專案中，這個檔案會設定控制反轉（IoC）容器，並處理應用程式或要求的各種生命週期事件。 其中某些事件會使用中介軟體來處理（例如`Application_BeginRequest`）。 其他事件則需要透過相依性插入（DI）覆寫特定的服務。

藉由範例，eShop 的*Global.asax.cs*檔案包含下列程式碼：

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// http://docs.autofac.org/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

上述檔案會變成伺服器`Startup`端 Blazor 中的類別：

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

您可能會注意到 Web form 中的一項重大變更，就是 DI 的重要性。 DI 是 ASP.NET Core 設計的指導原則。 它支援對 ASP.NET Core framework 幾乎所有層面的自訂。 在許多情況下，您甚至可以使用內建的服務提供者。 如果需要更多自訂，則許多的社區專案都可以支援。 例如，您可以繼續執行協力廠商的 DI 程式庫投資。

在原始的 eShop 應用程式中，有一些會話管理設定。 由於伺服器端 Blazor 會使用 ASP.NET Core SignalR 進行通訊，因此不支援會話狀態，因為連線可能會與 HTTP 內容無關。 使用會話狀態的應用程式必須先重新架構，才能以 Blazor 應用程式的身分執行。

如需應用程式啟動的詳細資訊，請參閱[應用程式啟動](app-startup.md)。

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>將 HTTP 模組和處理常式遷移至中介軟體

HTTP 模組和處理常式是 Web Forms 中用來控制 HTTP 要求管線的常見模式。 執行`IHttpModule` 或`IHttpHandler`的類別可能會註冊並處理傳入的要求。 Web Forms 會*在 web.config 檔案*中設定模組和處理常式。 Web form 也是以應用程式生命週期事件處理為基礎。 ASP.NET Core 會改為使用中介軟體。 中介軟體是在`Startup`類別的`Configure`方法中註冊。 中介軟體執行順序取決於註冊順序。

在[啟用啟動](#enable-startup-process)程式一節中，Web form 會以`Application_BeginRequest`方法的形式引發生命週期事件。 ASP.NET Core 不提供此事件。 達成此行為的其中一種方式是執行中介軟體，如*Startup.cs*檔案範例中所示。 此中介軟體會執行相同的邏輯，然後將控制權轉移至中介軟體管線中的下一個處理常式。

如需有關遷移模組和處理常式的詳細資訊，請參閱[將 HTTP 處理常式和模組遷移至 ASP.NET Core 中介軟體](/aspnet/core/migration/http-modules)。

## <a name="migrate-static-files"></a>遷移靜態檔案

若要提供靜態檔案（例如 HTML、CSS、影像和 JavaScript），檔案必須由中介軟體公開。 `UseStaticFiles`呼叫方法可讓您從 web 根路徑提供靜態檔案。 預設的 web 根目錄是*wwwroot*，但可以自訂。 `Configure` 如`Startup` eShop 類別的方法所包含：

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

EShop 專案可讓您進行基本的靜態檔案存取。 有許多自訂可用於靜態檔案存取。 如需啟用預設檔案或檔案瀏覽器的詳細資訊，請參閱[ASP.NET Core 中的靜態](/aspnet/core/fundamentals/static-files)檔案。

## <a name="migrate-runtime-bundling-and-minification-setup"></a>遷移執行時間組合和縮制設定

配套和縮制是一種效能優化技術，可減少伺服器要求的數目和大小，以取得特定檔案類型。 JavaScript 和 CSS 通常會在傳送至用戶端之前，先進行某種形式的捆綁或縮制。 在 ASP.NET Web Forms 中，這些優化會在執行時間處理。 優化慣例會定義*App_Start/bundleconfig.json*檔案。 在 ASP.NET Core 中，採用了更具宣告性的方法。 檔案會列出要縮減的檔案，以及特定的縮制設定。

如需有關配套和縮制的詳細資訊，請參閱[ASP.NET Core 中的組合和縮小靜態資產](/aspnet/core/client-side/bundling-and-minification)。

## <a name="migrate-aspx-pages"></a>遷移 ASPX 頁面

Web Forms 應用程式中的頁面是副檔名為 *.aspx*的檔案。 Web form 頁面通常會對應至 Blazor 中的元件。 Blazor 元件是在副檔名為*razor*的檔案中撰寫。 針對 eShop 專案，會將五頁轉換成 Razor 頁面。

例如，詳細資料檢視是由 Web Forms 專案中的三個檔案所組成：*詳細資訊 .aspx*、 *Details.aspx.cs*和*Details.aspx.designer.cs*。 轉換成 Blazor 時，程式碼後置和標記會結合為*razor*。 Razor 編譯（相當於*designer.cs*檔案中的檔案）會儲存在*obj*目錄中，而且預設不會在**方案總管**中看到。 Web Forms 頁面包含下列標記：

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

上述標記的程式碼後置包含下列程式碼：

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

轉換成 Blazor 時，Web Forms 頁面會轉譯為下列程式碼：

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

請注意，程式碼和標記位於相同的檔案中。 所有必要的服務都可使用`@inject`屬性進行存取。 根據指示詞，可以`Catalog/Details/{id}`在路由存取此頁面。 `@page` 路由的`{id}`預留位置值已限制為整數。 如 [[路由](pages-routing-layouts.md)] 區段中所述，與 Web form 不同，Razor 元件會明確指出其路由和包含的任何參數。 許多 Web form 控制項在 Blazor 中可能不會有正確的對應專案。 通常會有一個對等的 HTML 程式碼片段，會提供相同的用途。 例如， `<asp:Label />`您可以將控制項取代為 HTML `<label>`元素。

### <a name="model-validation-in-blazor"></a>Blazor 中的模型驗證

如果您的 Web form 程式碼包含驗證，您幾乎不需要進行任何變更，就可以傳輸大部分的內容。 在 Blazor 中執行的好處是，您不需要自訂 JavaScript 就可以執行相同的驗證邏輯。 資料批註可讓您輕鬆進行模型驗證。

例如，*建立 .aspx*頁面的資料輸入表單具有驗證。 範例程式碼片段看起來像這樣：

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

在 Blazor 中，會在*建立 razor*檔案中提供對等的標記：

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>
    
    ...
</EditForm>
```

`EditForm`內容包含驗證支援，而且可以包裝在輸入前後。 資料批註是新增驗證的常見方式。 這類驗證支援可以透過`DataAnnotationsValidator`元件新增。 如需此機制的詳細資訊，請參閱[ASP.NET Core Blazor 表單和驗證](/aspnet/core/blazor/forms-validation)。

## <a name="migrate-built-in-web-forms-controls"></a>遷移內建的 Web Forms 控制項

*即將推出此內容。*

## <a name="migrate-configuration"></a>遷移設定

在 Web form 專案中，設定資料最常儲存*在 web.config 檔案*中。 設定資料可透過存取`ConfigurationManager`。 服務通常需要用來剖析物件。 透過 .NET Framework 4.7.2，複合性已透過新增至`ConfigurationBuilders`設定。 這些產生器可讓開發人員新增設定的各種來源，然後在執行時間撰寫以取得必要的值。

ASP.NET Core 引進了彈性的設定系統，可讓您定義應用程式和部署所使用的設定來源或來源。 您在 Web Forms 應用程式中使用的基礎結構，是在ASP.NETCore設定系統中所使用的概念之後進行模型化。`ConfigurationBuilder`

下列程式碼片段示範 Web Forms eShop 專案*如何使用 web.config*來儲存設定值：

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
```

秘密（例如資料庫連接字串）通常會儲存*在 web.config 中。* 秘密可避免保存在不安全的位置，例如原始檔控制。 在 ASP.NET Core 上使用 Blazor 時，先前以 XML 為基礎的設定會取代為下列 JSON：

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON 是預設的設定格式;不過，ASP.NET Core 支援許多其他的格式，包括 XML。 另外還有數個支援社區的格式。

Blazor 專案`Startup`類別中的函式`IConfiguration`會透過稱為「函式插入」的 DI 技術來接受實例：

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

根據預設，環境變數、JSON 檔案（*appsettings. json*和*appsettings. {環境}. json*），而命令列選項會在設定物件中註冊為有效的設定來源。 設定來源可透過存取`Configuration[key]`。 更先進的技術是使用選項模式將設定資料系結至物件。 如需設定和選項模式的詳細資訊，請分別參閱 ASP.NET Core 中的[ASP.NET Core](/aspnet/core/fundamentals/configuration/)和[選項模式](/aspnet/core/fundamentals/configuration/options)中的設定。

## <a name="migrate-data-access"></a>遷移資料存取

資料存取是任何應用程式的重要層面。 EShop 專案會將目錄資訊儲存在資料庫中，並使用 Entity Framework （EF）6來抓取資料。 由於 .NET Core 3.0 支援 EF 6，因此專案可以繼續使用它。

EShop 需要下列與 EF 相關的變更：

* 在 .NET Framework 中， `DbContext`物件會接受格式為*name = ConnectionString*的字串，並使用中`ConfigurationManager.AppSettings[ConnectionString]`的連接字串來連接。 在 .NET Core 中，這不受支援。 必須提供連接字串。
* 資料庫是以同步方式存取。 雖然這是可行的，但擴充性可能會受到影響。 這個邏輯應該移至非同步模式。

雖然資料集系結的原生支援並不相同，但 Blazor 會在 Razor C#頁面中提供其支援的彈性和能力。 例如，您可以執行計算並顯示結果。 如需 Blazor 中資料模式的詳細資訊，請參閱[資料存取](data.md)章節。

## <a name="architectural-changes"></a>架構變更

最後，在遷移至 Blazor 時，需要考慮一些重要的架構差異。 其中許多變更都適用于以 .NET Core 或 ASP.NET Core 為基礎的任何專案。

由於 Blazor 是以 .NET Core 為基礎，因此在確保 .NET Core 支援時有一些考慮。 其中一些主要變更包括移除下列功能：

* 多個 Appdomain
* 遠端處理
* 程式碼存取安全性 (CAS)
* 安全性透明度

如需有關可在 .NET Core 上執行的支援變更之技術的詳細資訊，請參閱[將您的程式碼從 .NET Framework 移植到 .Net core](/dotnet/core/porting)。

ASP.NET Core 是 ASP.NET 的重新發想版本，而且有一些可能不會在一開始就很明顯的變更。 主要變更如下：

* 沒有同步處理內容，這表示`HttpContext.Current`沒有、 `Thread.CurrentPrincipal`或其他靜態存取子
* 無陰影複製
* 沒有要求佇列

ASP.NET Core 中的許多作業都是非同步，這可讓您更輕鬆地關閉 i/o 系結工作的載入作業。 請務必不要使用`Task.Wait()`或`Task.GetResult()`來封鎖，這可能會快速耗盡執行緒集區資源。

## <a name="migration-conclusion"></a>遷移結論

此時，您已瞭解將 Web form 專案移至 Blazor 所需的許多範例。 如需完整範例，請參閱[eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor)專案。

>[!div class="step-by-step"]
>[上一步](security-authentication-authorization.md)
