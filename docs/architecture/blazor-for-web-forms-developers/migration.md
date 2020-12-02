---
title: 從 ASP.NET Web Forms 遷移至 Blazor
description: 瞭解如何將現有的 ASP.NET Web Forms 應用程式遷移至 Blazor 。
author: twsouthwick
ms.author: tasou
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: 893b6f851681ec540629fe160749b2622b6d5440
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509828"
---
# <a name="migrate-from-aspnet-web-forms-to-no-locblazor"></a>從 ASP.NET Web Forms 遷移至 Blazor

從 ASP.NET Web Forms 將程式碼基底遷移至 Blazor 需要規劃的耗時工作。 本章概述此程式。 可以簡化轉換的工作，是確保應用程式遵守多 *層式* 架構，在此案例中，應用程式模型 (，Web Form) 與商務邏輯不同。 圖層的這種邏輯分隔可讓您清楚瞭解需要移至 .NET Core 和 Blazor 。

在此範例中，會使用 [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) 上提供的 eShop 應用程式。 eShop 是一種目錄服務，可透過表單輸入和驗證提供 CRUD 功能。

為何要將工作中的應用程式遷移至 Blazor ？ 很多時候都不需要。 ASP.NET Web Forms 將持續支援許多年。 不過， Blazor 只有已遷移的應用程式才支援所提供的許多功能。 這類功能包括：

- 架構中的效能改進，例如 `Span<T>`
- 執行 as 的能力 WebAssembly
- Linux 和 macOS 的跨平臺支援
- 應用程式本機部署或共用架構部署，而不影響其他應用程式

如果這些或其他新功能的吸引力夠大，則遷移應用程式可能會有價值。 遷移可採用不同的圖形;它可以是整個應用程式，或只是需要變更的特定端點。 遷移決策最終是以開發人員要解決的商務問題為基礎。

## <a name="server-side-versus-client-side-hosting"></a>伺服器端與用戶端裝載

如 [裝載模型](hosting-models.md) 一章所述， Blazor 應用程式可以用兩種不同的方式裝載：伺服器端和用戶端。 伺服器端模型會在執行伺服器上的任何實際程式碼時，使用 ASP.NET Core SignalR 連接來管理 DOM 更新。 用戶端模型會在 WebAssembly 瀏覽器中執行，而不需要伺服器連接。 有一些差異會影響，最適合特定的應用程式：

- 執行 as WebAssembly 並不支援所有功能 (例如目前時間的執行緒) 
- 用戶端與伺服器之間的多對話通訊可能會導致伺服器端模式的延遲問題
- 存取資料庫和內部或受保護的服務時，需要使用用戶端裝載的個別服務

在撰寫本文時，伺服器端模型更為類似 Web Form。 本章大多著重于伺服器端裝載模型，因為它已準備好用於生產環境。

## <a name="create-a-new-project"></a>建立新專案

此初始遷移步驟是建立新專案。 此專案類型是以 .NET 的 SDK 樣式專案為基礎，可簡化先前的專案格式所使用的大部分重複專案。 如需詳細資訊，請參閱 [專案結構](project-structure.md)的章節。

建立專案之後，請安裝先前專案中使用的程式庫。 在較舊的 Web Form 專案中，您可能已使用 *packages.config* 檔案來列出所需的 NuGet 套件。 在新的 SDK 樣式專案中， *packages.config* 已取代為 `<PackageReference>` 專案檔中的元素。 這種方法的優點是所有相依性都是以可轉移的方式安裝的。 您只會列出您感興趣的最上層相依性。

您所使用的許多相依性都適用于 .NET，包括 Entity Framework 6 和 log4net。 如果沒有可用的 .NET 或 .NET Standard 版本，則通常可以使用 .NET Framework 版本。 您的里程可能會有所不同。 任何在 .NET 中無法使用的 API 都會導致執行階段錯誤。 Visual Studio 會通知您這類套件。 **方案總管** 中專案的 [**參考**] 節點上會出現黃色圖示。

在以 Blazor eShop 為基礎的專案中，您可以看到已安裝的封裝。 先前， *packages.config* 檔案會列出專案中使用的每個套件，而導致檔案的長度大約是50行。 *packages.config* 的程式碼片段為：

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

`<packages>`元素包含所有必要的相依性。 因為您需要這些封裝，所以很難找出其中包含哪些套件。 有些 `<package>` 元素只是為了滿足您需要的相依性需求而列出的。

Blazor專案會在專案檔的專案中列出您需要的相依性 `<ItemGroup>` ：

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.4.4" />
    <PackageReference Include="log4net" Version="2.0.12" />
    <PackageReference Include="Microsoft.Extensions.Logging.Log4Net.AspNetCore" Version="2.2.12" />
</ItemGroup>
```

其中一個可簡化 Web Form 開發人員生命週期的 NuGet 套件是 [Windows 相容性套件](../../core/porting/windows-compat-pack.md)。 雖然 .NET 是跨平臺的，但某些功能只能在 Windows 上使用。 藉由安裝相容性套件，可取得 Windows 特定功能。 這類功能的範例包括登錄、WMI 和目錄服務。 套件會新增 20000 Api，並啟用您可能已經熟悉的許多服務。 EShop 專案不需要相容性套件;但是，如果您的專案使用 Windows 特定功能，則套件會簡化遷移工作。

## <a name="enable-startup-process"></a>啟用啟動進程

的啟動程式 Blazor 從 Web Form 變更，並遵循其他 ASP.NET Core 服務的類似設定。 裝載伺服器端時， Blazor 元件會作為一般 ASP.NET Core 應用程式的一部分來執行。 當裝載于瀏覽器時 WebAssembly ， Blazor 元件會使用類似的裝載模型。 不同之處在于元件是以不同于任何後端進程的服務來執行。 無論何種方式，啟動都很類似。

*Global.asax.cs* 檔案是 Web Form 專案的預設啟動頁面。 在 eShop 專案中，此檔案會設定反轉 (IoC) 容器的控制權，並處理應用程式或要求的各種生命週期事件。 其中有些事件是使用中介軟體 (（例如) ）來處理 `Application_BeginRequest` 。 其他事件則需要透過相依性插入 (DI) 覆寫特定的服務。

例如，eShop 的 *Global.asax.cs* 檔案包含下列程式碼：

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
    /// https://autofaccn.readthedocs.io/en/latest/integration/webforms.html
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

先前的檔案會變成 `Startup` 伺服器端中的類別 Blazor ：

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

您可能會注意到 Web Form 的一項重大變更，就是 DI 的優點。 DI 是 ASP.NET Core 設計中的指導準則。 它支援 ASP.NET Core framework 幾乎所有層面的自訂。 甚至有內建的服務提供者可以用於許多案例。 如果需要更多自訂，許多的社區專案都可以支援。 例如，您可以將協力廠商 DI 程式庫投資轉寄。

在原始的 eShop 應用程式中，有一些會話管理的設定。 由於伺服器端 Blazor 使用 ASP.NET Core SignalR 來進行通訊，因此不支援會話狀態，因為連接可能會在 HTTP 內容以外的情況下發生。 使用會話狀態的應用程式必須先重新架構，才能以應用程式的形式執行 Blazor 。

如需應用程式啟動的詳細資訊，請參閱 [應用程式啟動](app-startup.md)。

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>將 HTTP 模組和處理常式遷移至中介軟體

HTTP 模組和處理常式是 Web Form 中常見的模式，可控制 HTTP 要求管線。 實 `IHttpModule` `IHttpHandler` 作為或可註冊並處理傳入要求的類別。 Web Form 設定 *web.config* 檔案中的模組和處理常式。 Web Form 也會隨著應用程式生命週期事件處理而有很大的依據。 ASP.NET Core 會改為使用中介軟體。 中介軟體是在類別的方法中註冊 `Configure` `Startup` 。 中介軟體執行順序取決於註冊順序。

在 [ [啟用啟動進程](#enable-startup-process) ] 區段中，Web Form 引發生命週期事件做為 `Application_BeginRequest` 方法。 ASP.NET Core 中無法使用此事件。 達成此行為的其中一種方式是執行中介軟體，如 *Startup.cs* 檔範例所示。 此中介軟體會執行相同的邏輯，然後將控制權傳輸至中介軟體管線中的下一個處理常式。

如需有關遷移模組和處理常式的詳細資訊，請參閱 [將 HTTP 處理常式和模組遷移至 ASP.NET Core 中介軟體](/aspnet/core/migration/http-modules)。

## <a name="migrate-static-files"></a>遷移靜態檔案

為了提供靜態檔案 (例如 HTML、CSS、影像和 JavaScript) ，檔案必須由中介軟體公開。 呼叫 `UseStaticFiles` 方法可從 web 根路徑提供靜態檔案。 預設的 web 根目錄是 *wwwroot*，但可以自訂。 如同 `Configure` eShop 類別的方法所包含 `Startup` ：

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

EShop 專案會啟用基本的靜態檔案存取。 有許多自訂可用於靜態檔案存取。 如需啟用預設檔案或檔案瀏覽器的詳細資訊，請參閱 [ASP.NET Core 中的靜態](/aspnet/core/fundamentals/static-files)檔案。

## <a name="migrate-runtime-bundling-and-minification-setup"></a>遷移執行時間包裝和縮制設定

組合和縮制是一種效能優化技術，可減少伺服器要求的數目和大小，以抓取特定檔案類型。 JavaScript 和 CSS 通常會在傳送至用戶端之前，先進行某種形式的組合或縮制。 在 ASP.NET Web Forms 中，會在執行時間處理這些優化。 優化慣例是定義 *App_Start/bundleconfig.cs* 檔。 在 ASP.NET Core 中，採用了更宣告的方法。 檔案會列出要縮減的檔案，以及特定的縮制設定。

如需有關組合和縮制的詳細資訊，請參閱 [ASP.NET Core 中的配套和縮短靜態資產](/aspnet/core/client-side/bundling-and-minification)。

## <a name="migrate-aspx-pages"></a>遷移 ASPX 頁面

Web Form 應用程式中的頁面是具有 *.aspx* 副檔名的檔案。 Web Form 頁面通常可以對應到中的元件 Blazor 。 Blazor元件是以 *razor* 副檔名的檔案撰寫的。 針對 eShop 專案，會將五個頁面轉換成 Razor 頁面。

例如，詳細資料檢視包含 Web Form 專案中的三個檔案： *default.aspx*、 *Details.aspx.cs* 和 *Details.aspx.designer.cs*。 轉換為時 Blazor ，程式碼後端和標記會合並成 *詳細資料。 razor*。 Razor 編譯 (相當於 *designer.cs* 檔案) 儲存在 *obj* 目錄中，而且預設不會在 **方案總管** 中看到。 Web Form] 頁面包含下列標記：

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

上述標記的程式碼後端包含下列程式碼：

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

當轉換為時 Blazor ，Web Form 頁面會轉譯成下列程式碼：

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

請注意，程式碼和標記都在相同的檔案中。 所有必要的服務都可透過屬性來存取 `@inject` 。 每個指示詞 `@page` 可以在路由存取此頁面 `Catalog/Details/{id}` 。 路由的預留位置值已 `{id}` 限制為整數。 如 [路由](pages-routing-layouts.md) 區段中所述，與 Web Form 不同的是，Razor 元件會明確指出其路由和包含的任何參數。 許多 Web Form 控制項在中可能沒有確切的對應專案 Blazor 。 通常會有同等的 HTML 程式碼片段，以提供相同的用途。 例如， `<asp:Label />` 控制項可以取代為 HTML 專案 `<label>` 。

### <a name="model-validation-in-no-locblazor"></a>中的模型驗證 Blazor

如果您的 Web Form 程式碼包含驗證，您可以傳輸大部分的內容，而且幾乎不會有任何變更。 在中執行的好處在於，您 Blazor 可以在不需要自訂 JavaScript 的情況下執行相同的驗證邏輯。 資料批註可讓您輕鬆地驗證模型。

例如， *建立 .aspx* 頁面的資料輸入表單具有驗證。 範例程式碼片段看起來像這樣：

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

在中 Blazor ，會在 *Create razor* 檔案中提供對等的標記：

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

`EditForm`內容包含驗證支援，而且可以包裝在輸入周圍。 資料批註是新增驗證的常見方式。 這類驗證支援可透過元件加入 `DataAnnotationsValidator` 。 如需此機制的詳細資訊，請參閱 [ASP.NET Core Blazor 表單和驗證](/aspnet/core/blazor/forms-validation)。

## <a name="migrate-configuration"></a>移轉組態

在 Web Form 專案中，設定資料最常儲存在 *web.config* 檔案中。 使用存取設定資料 `ConfigurationManager` 。 服務通常需要剖析物件。 使用 .NET Framework 4.7.2，會透過將可組合性新增至設定 `ConfigurationBuilders` 。 這些產生器可讓開發人員加入設定的各種來源，然後在執行時間撰寫這些來源，以取得必要的值。

ASP.NET Core 引進了彈性的設定系統，可讓您定義應用程式和部署所使用的設定來源或來源。 `ConfigurationBuilder`您可能會在 Web Form 應用程式中使用的基礎結構，是在 ASP.NET Core 設定系統中使用的概念之後進行模型化。

下列程式碼片段示範 Web Form eShop 專案如何使用 *web.config* 來儲存設定值：

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
</configuration>
```

在 *web.config* 中儲存秘密（例如資料庫連接字串）是很常見的。秘密可避免保存在不安全的位置，例如原始檔控制。 Blazor在 ASP.NET Core 上，上述以 XML 為基礎的設定會以下列 JSON 取代：

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON 是預設的設定格式;不過，ASP.NET Core 支援許多其他格式，包括 XML。 另外還有數個支援社區的格式。

專案類別中的函 Blazor 式會 `Startup` 透過稱為「函式插入」 `IConfiguration` 的 DI 技術來接受實例：

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

根據預設，環境變數、JSON 檔案 (*appsettings.json* 和 *appsettings。環境}. json*) ，而且命令列選項會在設定物件中註冊為有效的設定來源。 您可以透過存取設定來源 `Configuration[key]` 。 更先進的技術是使用選項模式將設定資料系結至物件。 如需設定和選項模式的詳細資訊，請分別參閱 ASP.NET Core 中的 [ASP.NET Core](/aspnet/core/fundamentals/configuration/) 和 [選項模式](/aspnet/core/fundamentals/configuration/options)設定。

## <a name="migrate-data-access"></a>遷移資料存取

資料存取是任何應用程式的重要層面。 EShop 專案會將目錄資訊儲存在資料庫中，並使用 Entity Framework (EF) 6 來抓取資料。 因為 .NET 5.0 支援 EF 6，所以專案可以繼續使用。

EShop 需要下列 EF 相關變更：

- 在 .NET Framework 中， `DbContext` 物件會接受表單 *Name = ConnectionString* 的字串，並使用中的連接字串 `ConfigurationManager.AppSettings[ConnectionString]` 來連接。 在 .NET Core 中不支援此功能。 必須提供連接字串。
- 資料庫是以同步方式存取。 雖然這是可行的，但是擴充性可能會受到影響。 此邏輯應移至非同步模式。

雖然資料集系結沒有相同的原生支援，但 Blazor 在 Razor 頁面中提供其 c # 支援的彈性和能力。 例如，您可以執行計算並顯示結果。 如需有關中資料模式的詳細資訊 Blazor ，請參閱 [資料存取](data.md) 章節。

## <a name="architectural-changes"></a>架構變更

最後，在遷移至時，需要考慮一些重要的架構差異 Blazor 。 其中許多變更都適用于以 .NET Core 或 ASP.NET Core 為基礎的任何變更。

因為 Blazor 是以 .Net core 為基礎，所以在確定 .Net core 支援時有一些考慮。 部分主要變更包括移除下列功能：

- 多個 Appdomain
- 遠端
- 程式碼存取安全性 (CAS)
- 安全性透明度

如需有關可在 .NET Core 上執行的支援所需變更之技術的詳細資訊，請參閱將 [您的程式碼從 .NET Framework 移植到 .Net core](../../core/porting/index.md)。

ASP.NET Core 是 ASP.NET 的重新發想版本，而且有一些可能不會很明顯的變更。 主要變更如下：

- 沒有同步處理內容，這表示沒有 `HttpContext.Current` 、 `Thread.CurrentPrincipal` 或其他靜態存取子
- 無陰影複製
- 沒有要求佇列

ASP.NET Core 中的許多作業都是非同步，可讓您更輕鬆地關閉 i/o 系結工作的載入作業。 絕對不要使用或來封鎖 `Task.Wait()` `Task.GetResult()` ，這樣可以快速耗盡執行緒集區資源。

## <a name="migration-conclusion"></a>遷移結論

到目前為止，您已瞭解將 Web Form 專案移至的許多範例 Blazor 。 如需完整範例，請參閱[eShopOn Blazor ](https://github.com/dotnet-architecture/eShopOnBlazor)專案。

>[!div class="step-by-step"]
>[[上一步]](security-authentication-authorization.md)
