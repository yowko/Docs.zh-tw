---
title: 應用程式啟動
description: 瞭解如何為您的應用程式定義啟動邏輯。
author: csharpfritz
ms.author: jefritz
ms.date: 02/25/2020
ms.openlocfilehash: 883f9a3fbe2d52cb7d0fbc5dfc94ce829a5d2bf3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158184"
---
# <a name="app-startup"></a><span data-ttu-id="be960-103">應用程式啟動</span><span class="sxs-lookup"><span data-stu-id="be960-103">App startup</span></span>

<span data-ttu-id="be960-104">針對 ASP.NET 撰寫的應用程式通常會有一個檔案，該檔案會 `global.asax.cs` 定義 `Application_Start` 控制哪些服務已設定並可供 HTML 轉譯和 .net 處理使用的事件。</span><span class="sxs-lookup"><span data-stu-id="be960-104">Applications that are written for ASP.NET typically have a `global.asax.cs` file that defines the `Application_Start` event that controls which services are configured and made available for both HTML rendering and .NET processing.</span></span> <span data-ttu-id="be960-105">本章探討 ASP.NET Core 和 Blazor Server 的內容有何不同。</span><span class="sxs-lookup"><span data-stu-id="be960-105">This chapter looks at how things are slightly different with ASP.NET Core and Blazor Server.</span></span>

## <a name="application_start-and-web-forms"></a><span data-ttu-id="be960-106">Application_Start 和 Web Form</span><span class="sxs-lookup"><span data-stu-id="be960-106">Application_Start and Web Forms</span></span>

<span data-ttu-id="be960-107">預設的 web form `Application_Start` 方法已有多年的成長，可處理許多設定工作。</span><span class="sxs-lookup"><span data-stu-id="be960-107">The default web forms `Application_Start` method has grown in purpose over years to handle many configuration tasks.</span></span>  <span data-ttu-id="be960-108">Visual Studio 2019 中預設範本的全新 web form 專案現在包含下列設定邏輯：</span><span class="sxs-lookup"><span data-stu-id="be960-108">A fresh web forms project with the default template in Visual Studio 2019 now contains the following configuration logic:</span></span>

- <span data-ttu-id="be960-109">`RouteConfig` -應用程式 URL 路由</span><span class="sxs-lookup"><span data-stu-id="be960-109">`RouteConfig` - Application URL routing</span></span>
- <span data-ttu-id="be960-110">`BundleConfig` -CSS 和 JavaScript 的組合和縮制</span><span class="sxs-lookup"><span data-stu-id="be960-110">`BundleConfig` - CSS and JavaScript bundling and minification</span></span>

<span data-ttu-id="be960-111">每個個別檔案都位於資料夾中 `App_Start` ，而且只會在應用程式啟動時執行一次。</span><span class="sxs-lookup"><span data-stu-id="be960-111">Each of these individual files reside in the `App_Start` folder and run only once at the start of our application.</span></span>  <span data-ttu-id="be960-112">`RouteConfig` 在 [預設專案] 範本中，加入 web form 的， `FriendlyUrlSettings` 以允許應用程式 url 省略 `.ASPX` 副檔名。</span><span class="sxs-lookup"><span data-stu-id="be960-112">`RouteConfig` in the default project template adds the `FriendlyUrlSettings` for web forms to allow application URLs to omit the `.ASPX` file extension.</span></span>  <span data-ttu-id="be960-113">預設範本也包含指示詞，此指示詞會將頁面的永久 HTTP 重新導向狀態碼 (HTTP 301) ， `.ASPX` 並以省略副檔名的檔案名提供易記 URL。</span><span class="sxs-lookup"><span data-stu-id="be960-113">The default template also contains a directive that provides permanent HTTP redirect status codes (HTTP 301) for the `.ASPX` pages to the friendly URL with the file name that omits the extension.</span></span>

<span data-ttu-id="be960-114">有了 ASP.NET Core 和 Blazor，這些方法可以簡化併合並至 `Startup` 類別中，也可以排除在使用一般的 web 技術。</span><span class="sxs-lookup"><span data-stu-id="be960-114">With ASP.NET Core and Blazor, these methods are either simplified and consolidated into the `Startup` class or they are eliminated in favor of common web technologies.</span></span>

## <a name="blazor-server-startup-structure"></a><span data-ttu-id="be960-115">Blazor 伺服器啟動結構</span><span class="sxs-lookup"><span data-stu-id="be960-115">Blazor Server Startup Structure</span></span>

<span data-ttu-id="be960-116">Blazor 伺服器應用程式位於 ASP.NET Core 3.0 或更新版本的應用程式之上。</span><span class="sxs-lookup"><span data-stu-id="be960-116">Blazor Server applications reside on top of an ASP.NET Core 3.0 or later application.</span></span>  <span data-ttu-id="be960-117">ASP.NET Core web 應用程式是透過 `Startup.cs` 應用程式根資料夾中類別的一對方法來設定。</span><span class="sxs-lookup"><span data-stu-id="be960-117">ASP.NET Core web applications are configured through a pair of methods in the `Startup.cs` class on the root folder of the application.</span></span>  <span data-ttu-id="be960-118">Startup 類別的預設內容如下所示</span><span class="sxs-lookup"><span data-stu-id="be960-118">The Startup class's default content is listed below</span></span>

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

<span data-ttu-id="be960-119">和 ASP.NET Core 的其餘部分一樣，會使用相依性插入原則來建立啟動類別。</span><span class="sxs-lookup"><span data-stu-id="be960-119">Like the rest of ASP.NET Core, the Startup class is created with dependency injection principles.</span></span>  <span data-ttu-id="be960-120">`IConfiguration`會提供給函式，並在公用屬性中隱藏，以便稍後在設定期間進行存取。</span><span class="sxs-lookup"><span data-stu-id="be960-120">The `IConfiguration` is provided to the constructor and stashed in a public property for later access during configuration.</span></span>

<span data-ttu-id="be960-121">`ConfigureServices`ASP.NET Core 引進的方法可讓您針對架構的內建相依性插入容器設定各種 ASP.NET Core framework 服務。</span><span class="sxs-lookup"><span data-stu-id="be960-121">The `ConfigureServices` method introduced in ASP.NET Core allows for the various ASP.NET Core framework services to be configured for the framework's built-in dependency injection container.</span></span>  <span data-ttu-id="be960-122">不同的 `services.Add*` 方法會加入服務，以啟用驗證、razor 頁面、MVC 控制器路由、SignalR 和 Blazor 伺服器之間的互動等功能。</span><span class="sxs-lookup"><span data-stu-id="be960-122">The various `services.Add*` methods add services that enable features such as authentication, razor pages, MVC controller routing, SignalR, and Blazor Server interactions among many others.</span></span>  <span data-ttu-id="be960-123">Web form 中不需要這個方法，因為在 web.config 設定檔中參考 ASP.NET 來定義 .ASPX、.ASCX、ASHX 和 .ASMX 檔案的剖析和處理。</span><span class="sxs-lookup"><span data-stu-id="be960-123">This method was not needed in web forms, as the parsing and handling of the ASPX, ASCX, ASHX, and ASMX files was defined by referencing ASP.NET in the web.config configuration file.</span></span>  <span data-ttu-id="be960-124">有關 ASP.NET Core 中的相依性插入的詳細資訊，可在 [線上檔](/aspnet/core/fundamentals/dependency-injection)中取得。</span><span class="sxs-lookup"><span data-stu-id="be960-124">More information about dependency injection in ASP.NET Core is available in the [online documentation](/aspnet/core/fundamentals/dependency-injection).</span></span>

<span data-ttu-id="be960-125">`Configure`方法會介紹要 ASP.NET Core 之 HTTP 管線的概念。</span><span class="sxs-lookup"><span data-stu-id="be960-125">The `Configure` method introduces the concept of the HTTP pipeline to ASP.NET Core.</span></span>  <span data-ttu-id="be960-126">在此方法中，我們會從上到下宣告 [中介軟體](middleware.md) ，以處理傳送至應用程式的每個要求。</span><span class="sxs-lookup"><span data-stu-id="be960-126">In this method, we declare from top to bottom the [Middleware](middleware.md) that will handle every request sent to our application.</span></span> <span data-ttu-id="be960-127">在預設設定中，大部分的功能都散佈在 web form 設定檔中，現在已在一個位置方便您參考。</span><span class="sxs-lookup"><span data-stu-id="be960-127">Most of these features in the default configuration were scattered across the web forms configuration files and are now in one place for ease of reference.</span></span>

<span data-ttu-id="be960-128">您不再需要在檔案中設定自訂錯誤頁面 `web.config` ，但現在設定為在應用程式環境未標記時一律顯示 `Development` 。</span><span class="sxs-lookup"><span data-stu-id="be960-128">No longer is the configuration of the custom error page placed in a `web.config` file, but now is configured to always be shown if the application environment is not labeled `Development`.</span></span>  <span data-ttu-id="be960-129">此外，ASP.NET Core 的應用程式現在已設定為使用 TLS 搭配方法呼叫來提供安全的頁面 `UseHttpsRedirection` 。</span><span class="sxs-lookup"><span data-stu-id="be960-129">Additionally, ASP.NET Core applications are now configured to serve secure pages with TLS by default with the `UseHttpsRedirection` method call.</span></span>

<span data-ttu-id="be960-130">接下來，會列出未預期的設定方法 `UseStaticFiles` 。</span><span class="sxs-lookup"><span data-stu-id="be960-130">Next, an unexpected configuration method is listed to `UseStaticFiles`.</span></span>  <span data-ttu-id="be960-131">在 ASP.NET Core 中，支援靜態檔案的要求 (例如 JavaScript、CSS 和影像檔案) 必須明確啟用，而且預設只有應用程式 *wwwroot* 資料夾中的檔案可公開定址。</span><span class="sxs-lookup"><span data-stu-id="be960-131">In ASP.NET Core, support for requests for static files (like JavaScript, CSS, and image files) must be explicitly enabled, and only files in the app's *wwwroot* folder are publicly addressable by default.</span></span>

<span data-ttu-id="be960-132">下一行是從 web forms 複製其中一個設定選項的第一行： `UseRouting` 。</span><span class="sxs-lookup"><span data-stu-id="be960-132">The next line is the first that replicates one of the configuration options from web forms: `UseRouting`.</span></span>  <span data-ttu-id="be960-133">這個方法會將 ASP.NET Core 路由器新增至管線，並可在這裡或在可考慮路由傳送的個別檔案中進行設定。</span><span class="sxs-lookup"><span data-stu-id="be960-133">This method adds the ASP.NET Core router to the pipeline and it can be either configured here or in the individual files that it can consider routing to.</span></span>  <span data-ttu-id="be960-134">路由設定的詳細資訊可在 [路由] [區段](pages-routing-layouts.md)中找到。</span><span class="sxs-lookup"><span data-stu-id="be960-134">More information about routing configuration can be found in the [Routing section](pages-routing-layouts.md).</span></span>

<span data-ttu-id="be960-135">此方法中的最後一個語句會定義 ASP.NET Core 正在接聽的端點。</span><span class="sxs-lookup"><span data-stu-id="be960-135">The final statement in this method defines the endpoints that ASP.NET Core is listening on.</span></span>  <span data-ttu-id="be960-136">這些是可供您在 web 伺服器上存取的 web 可存取位置，並接收由 .NET 處理並傳回給您的一些內容。</span><span class="sxs-lookup"><span data-stu-id="be960-136">These are the web accessible locations that you can access on the web server and receive some content handled by .NET and returned to you.</span></span>  <span data-ttu-id="be960-137">第一個專案會設定 SignalR 中樞，以用於 `MapBlazorHub` 提供處理 Blazor 元件之狀態和轉譯之伺服器的即時和持續連接。</span><span class="sxs-lookup"><span data-stu-id="be960-137">The first entry, `MapBlazorHub` configures a SignalR hub for use in providing the real-time and persistent connection to the server where the state and rendering of Blazor components is handled.</span></span>  <span data-ttu-id="be960-138">`MapFallbackToPage`方法呼叫表示網頁的可存取位置，該頁面會啟動 Blazor 應用程式，同時也會設定應用程式以處理來自用戶端的深層連結要求。</span><span class="sxs-lookup"><span data-stu-id="be960-138">The `MapFallbackToPage` method call indicates the web-accessible location of the page that starts the Blazor application and also configures the application to handle deep-linking requests from the client-side.</span></span>  <span data-ttu-id="be960-139">如果您開啟瀏覽器，並在應用程式中直接流覽至 Blazor 處理的路由，例如 `/counter` 在預設專案範本中，您將會看到這項功能正在運作。</span><span class="sxs-lookup"><span data-stu-id="be960-139">You will see this feature at work if you open a browser and navigate directly to Blazor handled route in your application, such as `/counter` in the default project template.</span></span> <span data-ttu-id="be960-140">要求是由 *_Host 的 cshtml* 回溯頁面處理，然後執行 Blazor 路由器並轉譯計數器頁面。</span><span class="sxs-lookup"><span data-stu-id="be960-140">The request gets handled by the *_Host.cshtml* fallback page, which then runs the Blazor router and renders the counter page.</span></span>

## <a name="upgrading-the-bundleconfig-process"></a><span data-ttu-id="be960-141">升級 >bundleconfig.cs 流程</span><span class="sxs-lookup"><span data-stu-id="be960-141">Upgrading the BundleConfig Process</span></span>

<span data-ttu-id="be960-142">結合 CSS 樣式表單和 JavaScript 檔案等資產的技術已大幅演進，其他技術則提供快速演進的工具和技術來管理這些資源。</span><span class="sxs-lookup"><span data-stu-id="be960-142">Technologies for bundling assets like CSS stylesheets and JavaScript files have evolved significantly, with other technologies providing quickly evolving tools and techniques for managing these resources.</span></span>  <span data-ttu-id="be960-143">至此，我們建議使用節點命令列工具（例如 Grunt/Gulp/WebPack）來封裝您的靜態資產。</span><span class="sxs-lookup"><span data-stu-id="be960-143">To this end, we recommend using a Node command-line tool such as Grunt / Gulp / WebPack to package your static assets.</span></span>

<span data-ttu-id="be960-144">您可以將 Grunt、Gulp 和 WebPack 命令列工具與其相關聯的設定新增至您的應用程式，ASP.NET Core 將會在應用程式建立程式期間以安靜的情況忽略這些檔案。</span><span class="sxs-lookup"><span data-stu-id="be960-144">The Grunt, Gulp, and WebPack command-line tools and their associated configurations can be added to your application and ASP.NET Core will quietly ignore those files during the application build process.</span></span>  <span data-ttu-id="be960-145">您可以新增呼叫來執行其工作，方法是在 `Target` 您的專案檔中加入專案，並使用類似下面的語法來觸發 gulp 腳本和該 `min` 腳本內的目標</span><span class="sxs-lookup"><span data-stu-id="be960-145">You can add a call to run their tasks by adding a `Target` inside your project file with syntax similar to the following that would trigger a gulp script and the `min` target inside that script</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

<span data-ttu-id="be960-146">如需管理 CSS 和 JavaScript 檔案的兩個策略的詳細資料，請參閱套件組合 [和縮短靜態資產中的 ASP.NET Core](/aspnet/core/client-side/bundling-and-minification) 檔。</span><span class="sxs-lookup"><span data-stu-id="be960-146">More details about both strategies to manage your CSS and JavaScript files are available in the [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification) documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="be960-147">[上一個](project-structure.md) 
>[下一步](components.md)</span><span class="sxs-lookup"><span data-stu-id="be960-147">[Previous](project-structure.md)
[Next](components.md)</span></span>
