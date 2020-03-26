---
title: 從ASP.NET Web 表單遷移到布拉佐爾
description: 瞭解如何處理將現有ASP.NET Web 表單應用遷移到 Blazor 的方法。
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 0a10a9a3d5ab32e16cb59a68da57116e20c53e49
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134083"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a>從ASP.NET Web 表單遷移到布拉佐爾

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

將代碼庫從ASP.NET Web 表單遷移到 Blazor 是一項耗時的任務，需要規劃。 本章概述了該過程。 可以簡化轉換的是確保應用遵循*N 層*體系結構，其中應用模型（在本例中為 Web 表單）與業務邏輯分開。 這種層的邏輯分離可以清楚地說明需要遷移到 .NET Core 和 Blazor 的內容。

在此示例中，使用[GitHub](https://github.com/dotnet-architecture/eShopOnBlazor)上可用的 eShop 應用。 eShop 是一種目錄服務，通過表單輸入和驗證提供 CRUD 功能。

為什麼工作應用應遷移到 Blazor？ 很多時候，沒有必要。 ASP.NET Web 表單將繼續支援多年。 但是，Blazor 提供的許多功能僅在遷移的應用上受支援。 這些功能包括：

- 框架中的性能改進，例如`Span<T>`
- 能夠以 Web 程式集身份運行
- 對 Linux 和 macOS 的跨平臺支援
- 應用本地部署或共用框架部署，不影響其他應用

如果這些或其他新功能足夠吸引人，則遷移應用可能具有價值。 遷移可以採用不同的形狀;它可以是整個應用，也可以只是需要更改的某些終結點。 遷移的決定最終基於開發人員要解決的業務問題。

## <a name="server-side-versus-client-side-hosting"></a>伺服器端與用戶端託管

如[託管模型](hosting-models.md)章節所述，Blazor 應用可以通過兩種不同的方式託管：伺服器端和用戶端。 伺服器端模型使用ASP.NET核心信號R連接來管理 DOM 更新，同時在伺服器上運行任何實際代碼。 用戶端模型在瀏覽器中作為 WebAssembly 運行，不需要伺服器連接。 有許多差異可能會影響特定應用：

- 以 WebAssembly 身份運行仍處於開發階段，當前可能不支援所有功能（如執行緒）
- 用戶端和伺服器之間的聊天通信可能會導致伺服器端模式下的延遲問題
- 訪問資料庫和內部或受保護服務需要使用用戶端託管提供單獨的服務

在編寫本文時，伺服器端模型更像 Web 表單。 本章的大部分重點介紹伺服器端託管模型，因為它已做好生產準備。

## <a name="create-a-new-project"></a>建立新專案

此初始遷移步驟是創建新專案。 此專案類型基於 .NET Core 的 SDK 樣式專案，並簡化了以前專案格式中使用的許多樣板。 有關詳細資訊，請參閱有關[專案結構](project-structure.md)的章節。

創建專案後，安裝上一個專案中使用的庫。 在較舊的 Web 表單專案中，您可能已使用*包.config*檔列出所需的 NuGet 包。 在新的 SDK 樣式專案中，*包.config*已替換為`<PackageReference>`專案檔案中的元素。 此方法的一個好處是，所有依賴項都是以過渡方式安裝的。 您只列出您關心的頂級依賴項。

您正在使用的許多依賴項可用於 .NET Core，包括實體框架 6 和 log4net。 如果沒有可用的 .NET Core 或 .NET 標準版本，則經常使用 .NET 框架版本。 您的里程可能會有所不同。 .NET Core 中不可用的任何 API 都會導致執行階段錯誤。 Visual Studio 會通知您此類套餐。 在**解決方案資源管理器**中的專案的**參考節點**上會出現一個黃色圖示。

在基於 Blazor 的 eShop 專案中，您可以看到已安裝的套裝軟體。 以前 *，package.config*檔列出了專案中使用的每個包，導致檔近 50 行長。 *包段. 配置*是：

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

該`<packages>`元素包括所有必要的依賴項。 很難確定其中哪些包包含，因為您需要它們。 某些`<package>`元素的列出只是為了滿足您需要的依賴項的需求。

Blazor 專案列出了專案檔案中`<ItemGroup>`的元素中所需的依賴項：

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

一個NuGet包，簡化了Web表單開發人員的生活是[Windows相容性包](../../core/porting/windows-compat-pack.md)。 儘管 .NET Core 是跨平臺的，但某些功能僅在 Windows 上可用。 通過安裝相容性包，可以獲得特定于 Windows 的功能。 此類功能的示例包括註冊表、WMI 和目錄服務。 該套裝軟體添加了大約 20，000 個 API，並啟動了許多您可能已經熟悉的服務。 eShop 專案不需要相容性包;因此，eShop 專案不需要相容性包。但是，如果專案使用特定于 Windows 的功能，則該包可簡化遷移工作。

## <a name="enable-startup-process"></a>啟用啟動過程

Blazor 的啟動過程從 Web 表單更改，並遵循其他ASP.NET核心服務的類似設置。 當託管伺服器端時，Blazor 元件作為正常ASP.NET核心應用的一部分運行。 當使用 WebAssembly 在瀏覽器中託管時，Blazor 元件使用類似的託管模型。 區別在於元件作為獨立于任何後端進程的服務運行。 無論哪種方式，啟動都是類似的。

*Global.asax.cs*檔是 Web 表單專案的預設啟動頁。 在 eShop 專案中，此檔配置"控制反轉 （IoC）"容器，並處理應用或請求的各種生命週期事件。 其中一些事件使用中介軟體（如`Application_BeginRequest`）處理。 其他事件需要通過依賴項注入 （DI） 重寫特定服務。

例如，eShop *Global.asax.cs*檔包含以下代碼：

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

前面的檔將成為伺服器端`Startup`Blazor 中的類：

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

您可能會從 Web 表單中注意到的一個重要變化是 DI 的突出性。 DI 一直是 ASP.NET核心設計的指導原則。 它支援自訂ASP.NET核心框架的幾乎所有方面。 甚至還有一個內置的服務提供者，可用於許多方案。 如果需要更多自訂，許多社區專案可以支援它。 例如，您可以進行協力廠商 DI 庫投資。

在原始的 eShop 應用中，有一些用於會話管理的配置。 由於伺服器端 Blazor 使用ASP.NET核心信號R進行通信，因此不支援會話狀態，因為連接可能獨立于 HTTP 上下文進行。 使用會話狀態的應用需要在作為 Blazor 應用運行之前重新構建。

有關應用啟動的詳細資訊，請參閱[應用啟動](app-startup.md)。

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>將 HTTP 模組和處理常式遷移到中介軟體

HTTP 模組和處理常式是 Web 表單中用於控制 HTTP 要求管道的常見模式。 實現`IHttpModule`或`IHttpHandler`可以註冊和處理傳入請求的類。 Web 表單在*Web.config 檔中*配置模組和處理常式。 Web 表單還在很大程度上基於應用生命週期事件處理。 ASP.NET核心使用中介軟體代替。 中介軟體在`Configure``Startup`類的方法中註冊。 中介軟體執行順序由註冊訂單確定。

在[啟用啟動過程](#enable-startup-process)部分中，Web 表單提出了生命週期事件作為`Application_BeginRequest`方法。 此事件在 ASP.NET 酷中不可用。 實現此行為的一個方法是實現中介軟體，如*Startup.cs*檔示例中所示。 此中介軟體執行相同的邏輯，然後將控制權傳輸到中介軟體管道中的下一個處理常式。

有關遷移模組和處理常式的詳細資訊，請參閱將 HTTP[處理常式和模組遷移到ASP.NET核心中介軟體](/aspnet/core/migration/http-modules)。

## <a name="migrate-static-files"></a>遷移靜態檔

要提供靜態檔（例如，HTML、CSS、圖像和 JavaScript），必須通過中介軟體公開這些檔。 調用`UseStaticFiles`該方法可以從 Web 根路徑提供靜態檔。 預設 Web 根目錄是*wwwroot，* 但可以自訂。 如 eShop `Configure` `Startup`類的方法中包含的：

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

eShop 專案支援基本的靜態檔訪問。 有許多自訂可用於靜態檔訪問。 有關啟用預設檔或檔瀏覽器的資訊，請參閱[ASP.NET 酷睿 中的靜態檔](/aspnet/core/fundamentals/static-files)。

## <a name="migrate-runtime-bundling-and-minification-setup"></a>遷移運行時捆綁和最小化設置

捆綁和分量化是性能優化技術，用於減少檢索某些檔案類型的伺服器請求的數量和大小。 在發送到用戶端之前，JavaScript 和 CSS 通常會經歷某種形式的捆綁或小化。 在 web 表單ASP.NET，這些優化在運行時處理。 優化約定定義為*App_Start/BundleConfig.cs*檔。 在ASP.NET核心中，採用了一種更具聲明性的方法。 檔列出了要進行挖掘的檔以及特定的小化設置。

有關捆綁和最小化的詳細資訊，請參閱 ASP.NET[酷中捆綁和小化靜態資產](/aspnet/core/client-side/bundling-and-minification)。

## <a name="migrate-aspx-pages"></a>遷移 ASPX 頁面

Web 表單應用中的頁面是具有 *.aspx*副檔名的檔。 Web 表單頁通常可以映射到 Blazor 中的元件。 Blazor 元件創作在具有 *.razor*副檔名的檔中。 對於 eShop 專案，五個頁面將轉換為 Razor 頁面。

例如，詳細資訊視圖由 Web 表單專案中的三個檔組成：*詳細資訊.aspx、Details.aspx.cs**Details.aspx.cs*和*Details.aspx.designer.cs*。 轉換為 Blazor 時，代碼後面和標記將合併為*詳細資訊。* Razor 編譯（等效于 *.designer.cs*檔中的內容）存儲在*obj*目錄中，預設情況下無法在**解決方案資源管理器**中查看。 "Web 表單"頁由以下標記組成：

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

前面的標記代碼後面包括以下代碼：

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

轉換為 Blazor 後，Web 表單頁將轉換為以下代碼：

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

請注意，代碼和標記位於同一檔中。 使用 屬性`@inject`可以訪問任何必需的服務。 根據`@page`指令，可以在`Catalog/Details/{id}`路由上訪問此頁面。 路由`{id}`預留位置的值已限制為整數。 如[路由](pages-routing-layouts.md)部分所述，與 Web 表單不同，Razor 元件顯式表示其路由和包含的任何參數。 許多 Web 表單控制項在 Blazor 中可能沒有確切的對應控制項。 通常有一個等效的 HTML 程式碼片段將服務于相同的目的。 例如，`<asp:Label />`控制項可以替換為 HTML`<label>`元素。

### <a name="model-validation-in-blazor"></a>布拉佐中的模型驗證

如果 Web 表單代碼包含驗證，則可以通過很少對無的更改傳輸大部分內容。 在 Blazor 中運行的一個好處是，無需自訂 JavaScript 即可運行相同的驗證邏輯。 資料注釋支援簡單的模型驗證。

例如 *，Create.aspx*頁具有具有驗證的資料輸入表單。 示例程式碼片段如下所示：

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

在 Blazor 中，等效標記在*Create.razor*檔中提供：

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

上下文`EditForm`包括驗證支援，可以環繞輸入。 資料注釋是添加驗證的常見方法。 此類驗證支援可通過`DataAnnotationsValidator`元件添加。 有關此機制的詳細資訊，請參閱[ASP.NET核心 Blazor 表單和驗證](/aspnet/core/blazor/forms-validation)。

## <a name="migrate-built-in-web-forms-controls"></a>遷移內置 Web 表單控制項

*此內容即將推出。*

## <a name="migrate-configuration"></a>移轉組態

在 Web 表單專案中，配置資料通常存儲在*Web.config 檔中*。 配置資料與 訪問一起`ConfigurationManager`。 分析物件通常需要服務。 使用 .NET 框架 4.7.2，通過 將可組合`ConfigurationBuilders`性添加到配置中。 這些產生器允許開發人員添加各種配置源，然後在運行時組成這些源以檢索必要的值。

ASP.NET Core 引入了一個靈活的配置系統，允許您定義應用和部署使用的配置源或源。 在`ConfigurationBuilder`Web 表單應用中可能使用的基礎結構是仿ASP.NET核心配置系統中使用的概念建模的。

以下程式碼片段演示了 Web 表單 eShop 專案如何使用*Web.config*來存儲配置值：

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

機密（如資料庫連接字串）通常存儲在*Web.config*中。機密不可避免地在不安全的位置（如原始程式碼管理）中持續存在。 在ASP.NET核心上的 Blazor 上，前面基於 XML 的配置將替換為以下 JSON：

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON 是預設配置格式;但是，ASP.NET酷睿支援許多其他格式，包括 XML。 還有幾種社區支援的格式。

Blazor 類中的建構函式通過稱為構造`Startup`函數注入的`IConfiguration`DI 技術接受實例：

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

預設情況下，環境變數、JSON 檔（*應用設置.json*和應用*設置。環境\.json*）和命令列選項在設定物件中註冊為有效的配置源。 可通過 訪問配置源`Configuration[key]`。 更高級的技術是使用選項模式將配置資料繫結到物件。 有關配置和選項模式的詳細資訊，請參閱 ASP.NET[核心中ASP.NET核心](/aspnet/core/fundamentals/configuration/)和[選項模式中的](/aspnet/core/fundamentals/configuration/options)配置。

## <a name="migrate-data-access"></a>遷移資料訪問

資料訪問是任何應用的一個重要方面。 eShop 專案將目錄資訊存儲在資料庫中，並使用實體框架 （EF） 6 檢索資料。 由於 .NET Core 3.0 中支援 EF 6，因此專案可以繼續使用它。

eShop 需要進行以下與 EF 相關的更改：

- 在 .NET 框架`DbContext`中，物件接受表單*名稱_ConnectString*的字串，並使用 中的`ConfigurationManager.AppSettings[ConnectionString]`連接字串進行連接。 在 .NET Core 中，不支援此功能。 必須提供連接字串。
- 以同步方式訪問資料庫。 雖然這行得通，但可擴充性可能會受到影響。 此邏輯應移動到非同步模式。

儘管對資料集綁定的本機支援不同，但 Blazor 在 Razor 頁面中提供了靈活性和功能，其 C# 支援。 例如，您可以執行計算並顯示結果。 有關 Blazor 中資料模式的詳細資訊，請參閱[資料訪問](data.md)章節。

## <a name="architectural-changes"></a>體系結構更改

最後，在遷移到 Blazor 時需要考慮一些重要的體系結構差異。 其中許多更改適用于基於 .NET Core 或 ASP.NET核心的任何更改。

由於 Blazor 建立在 .NET Core 上，因此在確保對 .NET Core 的支援時需要考慮。 一些主要更改包括刪除以下功能：

- 多個應用域
- 遠端
- 程式碼存取安全性 (CAS)
- 安全性透明度

有關識別支援在 .NET Core 上運行的必要更改的技術的詳細資訊，請參閱[將代碼從 .NET 框架移植到 .NET Core](/dotnet/core/porting)。

ASP.NET核心是ASP.NET的重新構想版本，並且有一些最初看起來並不明顯的更改。 主要更改包括：

- 沒有同步上下文，這意味著沒有`HttpContext.Current`、`Thread.CurrentPrincipal`或其他靜態訪問器
- 無陰影複製
- 無請求佇列

ASP.NET Core 中的許多操作都是非同步，這允許更輕鬆地卸載 I/O 綁定的任務。 請務必不要使用`Task.Wait()`或`Task.GetResult()`阻止，這可以快速耗盡執行緒池資源。

## <a name="migration-conclusion"></a>遷移結論

此時，您已經看到許多示例，說明將 Web 表單專案移動到 Blazor 需要什麼。 有關完整示例，請參閱[eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor)專案。

>[!div class="step-by-step"]
>[上一步](security-authentication-authorization.md)
