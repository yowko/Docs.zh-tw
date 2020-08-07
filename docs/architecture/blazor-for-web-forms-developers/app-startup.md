---
title: 應用程式啟動
description: 瞭解如何為您的應用程式定義啟動邏輯。
author: csharpfritz
ms.author: jefritz
ms.date: 02/25/2020
ms.openlocfilehash: 3d460750c36f64b8ad343755bd63b47af5c310d9
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87914876"
---
# <a name="app-startup"></a><span data-ttu-id="730cb-103">應用程式啟動</span><span class="sxs-lookup"><span data-stu-id="730cb-103">App startup</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="730cb-104">針對 ASP.NET 所撰寫的應用程式通常會有一個檔案，該檔案會 `global.asax.cs` 定義 `Application_Start` 事件來控制哪些服務已設定，並可供 HTML 轉譯和 .net 處理之用。</span><span class="sxs-lookup"><span data-stu-id="730cb-104">Applications that are written for ASP.NET typically have a `global.asax.cs` file that defines the `Application_Start` event that controls which services are configured and made available for both HTML rendering and .NET processing.</span></span> <span data-ttu-id="730cb-105">本章探討 ASP.NET Core 和 Blazor 伺服器之間有何不同。</span><span class="sxs-lookup"><span data-stu-id="730cb-105">This chapter looks at how things are slightly different with ASP.NET Core and Blazor Server.</span></span>

## <a name="application_start-and-web-forms"></a><span data-ttu-id="730cb-106">Application_Start 和 Web 表單</span><span class="sxs-lookup"><span data-stu-id="730cb-106">Application_Start and Web Forms</span></span>

<span data-ttu-id="730cb-107">預設 web form `Application_Start` 方法已隨著多年而增加，以處理許多設定工作。</span><span class="sxs-lookup"><span data-stu-id="730cb-107">The default web forms `Application_Start` method has grown in purpose over years to handle many configuration tasks.</span></span>  <span data-ttu-id="730cb-108">Visual Studio 2019 中具有預設範本的全新 web form 專案現在包含下列設定邏輯：</span><span class="sxs-lookup"><span data-stu-id="730cb-108">A fresh web forms project with the default template in Visual Studio 2019 now contains the following configuration logic:</span></span>

- <span data-ttu-id="730cb-109">`RouteConfig`-應用程式 URL 路由</span><span class="sxs-lookup"><span data-stu-id="730cb-109">`RouteConfig` - Application URL routing</span></span>
- <span data-ttu-id="730cb-110">`BundleConfig`-CSS 和 JavaScript 的捆綁和縮制</span><span class="sxs-lookup"><span data-stu-id="730cb-110">`BundleConfig` - CSS and JavaScript bundling and minification</span></span>

<span data-ttu-id="730cb-111">這些個別檔案都位於 `App_Start` 資料夾中，而且在應用程式開始時只會執行一次。</span><span class="sxs-lookup"><span data-stu-id="730cb-111">Each of these individual files reside in the `App_Start` folder and run only once at the start of our application.</span></span>  <span data-ttu-id="730cb-112">`RouteConfig`在 [預設專案] 範本中，新增 `FriendlyUrlSettings` for web forms 以允許應用程式 url 省略 `.ASPX` 副檔名。</span><span class="sxs-lookup"><span data-stu-id="730cb-112">`RouteConfig` in the default project template adds the `FriendlyUrlSettings` for web forms to allow application URLs to omit the `.ASPX` file extension.</span></span>  <span data-ttu-id="730cb-113">預設範本也包含指示詞，可為易記 URL 的頁面提供永久的 HTTP 重新導向狀態碼 (HTTP 301) ，其 `.ASPX` 檔案名會省略副檔名。</span><span class="sxs-lookup"><span data-stu-id="730cb-113">The default template also contains a directive that provides permanent HTTP redirect status codes (HTTP 301) for the `.ASPX` pages to the friendly URL with the file name that omits the extension.</span></span>

<span data-ttu-id="730cb-114">有了 ASP.NET Core 和 Blazor，這些方法都可以簡化併合並至 `Startup` 類別中，或在使用一般 web 技術時予以排除。</span><span class="sxs-lookup"><span data-stu-id="730cb-114">With ASP.NET Core and Blazor, these methods are either simplified and consolidated into the `Startup` class or they are eliminated in favor of common web technologies.</span></span>

## <a name="blazor-server-startup-structure"></a><span data-ttu-id="730cb-115">Blazor 伺服器啟動結構</span><span class="sxs-lookup"><span data-stu-id="730cb-115">Blazor Server Startup Structure</span></span>

<span data-ttu-id="730cb-116">Blazor 伺服器應用程式位於 ASP.NET Core 3.0 或更新版本的應用程式之上。</span><span class="sxs-lookup"><span data-stu-id="730cb-116">Blazor Server applications reside on top of an ASP.NET Core 3.0 or later application.</span></span>  <span data-ttu-id="730cb-117">ASP.NET Core web 應用程式是透過 `Startup.cs` 應用程式根資料夾的類別中的一對方法來設定。</span><span class="sxs-lookup"><span data-stu-id="730cb-117">ASP.NET Core web applications are configured through a pair of methods in the `Startup.cs` class on the root folder of the application.</span></span>  <span data-ttu-id="730cb-118">啟動類別的預設內容列示如下</span><span class="sxs-lookup"><span data-stu-id="730cb-118">The Startup class's default content is listed below</span></span>

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

<span data-ttu-id="730cb-119">如同 ASP.NET Core 的其餘部分，啟動類別是使用相依性插入原則所建立。</span><span class="sxs-lookup"><span data-stu-id="730cb-119">Like the rest of ASP.NET Core, the Startup class is created with dependency injection principles.</span></span>  <span data-ttu-id="730cb-120">`IConfiguration`會提供給在公用屬性中的函式和隱藏，以供稍後在設定期間存取。</span><span class="sxs-lookup"><span data-stu-id="730cb-120">The `IConfiguration` is provided to the constructor and stashed in a public property for later access during configuration.</span></span>

<span data-ttu-id="730cb-121">`ConfigureServices`ASP.NET Core 中引進的方法可讓您針對架構的內建相依性插入容器設定各種 ASP.NET Core framework 服務。</span><span class="sxs-lookup"><span data-stu-id="730cb-121">The `ConfigureServices` method introduced in ASP.NET Core allows for the various ASP.NET Core framework services to be configured for the framework's built-in dependency injection container.</span></span>  <span data-ttu-id="730cb-122">各種 `services.Add*` 方法會新增服務，以啟用像是驗證、razor 頁面、MVC 控制器路由、SignalR 和 Blazor 伺服器之間互動等功能。</span><span class="sxs-lookup"><span data-stu-id="730cb-122">The various `services.Add*` methods add services that enable features such as authentication, razor pages, MVC controller routing, SignalR, and Blazor Server interactions among many others.</span></span>  <span data-ttu-id="730cb-123">在 web form 中不需要這個方法，因為在 web.config 的設定檔中參考 ASP.NET，以定義 ASPX、ASCX、ASHX 和 .ASMX 檔案的剖析和處理。</span><span class="sxs-lookup"><span data-stu-id="730cb-123">This method was not needed in web forms, as the parsing and handling of the ASPX, ASCX, ASHX, and ASMX files was defined by referencing ASP.NET in the web.config configuration file.</span></span>  <span data-ttu-id="730cb-124">如需有關 ASP.NET Core 中的相依性插入的詳細資訊，請[參閱線上檔](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)（英文）。</span><span class="sxs-lookup"><span data-stu-id="730cb-124">More information about dependency injection in ASP.NET Core is available in the [online documentation](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span></span>

<span data-ttu-id="730cb-125">`Configure`方法會介紹要 ASP.NET Core 的 HTTP 管線概念。</span><span class="sxs-lookup"><span data-stu-id="730cb-125">The `Configure` method introduces the concept of the HTTP pipeline to ASP.NET Core.</span></span>  <span data-ttu-id="730cb-126">在此方法中，我們會從上到下宣告[中介軟體](middleware.md)，以處理傳送至應用程式的每個要求。</span><span class="sxs-lookup"><span data-stu-id="730cb-126">In this method, we declare from top to bottom the [Middleware](middleware.md) that will handle every request sent to our application.</span></span> <span data-ttu-id="730cb-127">這些預設設定中的大部分功能都散佈在 web form 設定檔中，而且現在已放在一個位置以方便參考。</span><span class="sxs-lookup"><span data-stu-id="730cb-127">Most of these features in the default configuration were scattered across the web forms configuration files and are now in one place for ease of reference.</span></span>

<span data-ttu-id="730cb-128">不會再設定放在檔案中的自訂錯誤頁面 `web.config` ，但現在已設定為一律會在應用程式環境未加上標籤時顯示 `Development` 。</span><span class="sxs-lookup"><span data-stu-id="730cb-128">No longer is the configuration of the custom error page placed in a `web.config` file, but now is configured to always be shown if the application environment is not labeled `Development`.</span></span>  <span data-ttu-id="730cb-129">此外，ASP.NET Core 的應用程式現在已設定為使用 TLS 搭配方法呼叫來提供安全頁面 `UseHttpsRedirection` 。</span><span class="sxs-lookup"><span data-stu-id="730cb-129">Additionally, ASP.NET Core applications are now configured to serve secure pages with TLS by default with the `UseHttpsRedirection` method call.</span></span>

<span data-ttu-id="730cb-130">接下來，會在中列出未預期的設定方法 `UseStaticFiles` 。</span><span class="sxs-lookup"><span data-stu-id="730cb-130">Next, an unexpected configuration method is listed to `UseStaticFiles`.</span></span>  <span data-ttu-id="730cb-131">在 ASP.NET Core 中，必須明確啟用靜態檔案的要求 (例如 JavaScript、CSS 和影像檔) ，而且只有應用程式的*wwwroot*資料夾中的檔案預設為可公開定址。</span><span class="sxs-lookup"><span data-stu-id="730cb-131">In ASP.NET Core, support for requests for static files (like JavaScript, CSS, and image files) must be explicitly enabled, and only files in the app's *wwwroot* folder are publicly addressable by default.</span></span>

<span data-ttu-id="730cb-132">下一行是從 web form 複寫其中一個設定選項的第一個程式碼： `UseRouting` 。</span><span class="sxs-lookup"><span data-stu-id="730cb-132">The next line is the first that replicates one of the configuration options from web forms: `UseRouting`.</span></span>  <span data-ttu-id="730cb-133">這個方法會將 ASP.NET Core 路由器新增至管線，而且可以在這裡或可以考慮路由傳送至的個別檔案中進行設定。</span><span class="sxs-lookup"><span data-stu-id="730cb-133">This method adds the ASP.NET Core router to the pipeline and it can be either configured here or in the individual files that it can consider routing to.</span></span>  <span data-ttu-id="730cb-134">路由設定的詳細資訊可在[路由一節](pages-routing-layouts.md)中找到。</span><span class="sxs-lookup"><span data-stu-id="730cb-134">More information about routing configuration can be found in the [Routing section](pages-routing-layouts.md).</span></span>

<span data-ttu-id="730cb-135">這個方法中的最後一個語句會定義 ASP.NET Core 正在接聽的端點。</span><span class="sxs-lookup"><span data-stu-id="730cb-135">The final statement in this method defines the endpoints that ASP.NET Core is listening on.</span></span>  <span data-ttu-id="730cb-136">這些是您可以在網頁伺服器上存取的 web 可存取位置，並會接收由 .NET 處理並傳回給您的一些內容。</span><span class="sxs-lookup"><span data-stu-id="730cb-136">These are the web accessible locations that you can access on the web server and receive some content handled by .NET and returned to you.</span></span>  <span data-ttu-id="730cb-137">第一個專案 `MapBlazorHub` 會設定 SignalR 中樞，以便在處理 Blazor 元件狀態和呈現的伺服器時，提供即時且持續的連接。</span><span class="sxs-lookup"><span data-stu-id="730cb-137">The first entry, `MapBlazorHub` configures a SignalR hub for use in providing the real-time and persistent connection to the server where the state and rendering of Blazor components is handled.</span></span>  <span data-ttu-id="730cb-138">`MapFallbackToPage`方法呼叫會指出啟動 Blazor 應用程式之網頁的 web 可存取位置，也會設定應用程式以處理來自用戶端的深層連結要求。</span><span class="sxs-lookup"><span data-stu-id="730cb-138">The `MapFallbackToPage` method call indicates the web-accessible location of the page that starts the Blazor application and also configures the application to handle deep-linking requests from the client-side.</span></span>  <span data-ttu-id="730cb-139">如果您開啟瀏覽器，並直接流覽至應用程式中 Blazor 已處理的路由（例如， `/counter` 在預設專案範本中），您就會看到這項功能在工作中。</span><span class="sxs-lookup"><span data-stu-id="730cb-139">You will see this feature at work if you open a browser and navigate directly to Blazor handled route in your application, such as `/counter` in the default project template.</span></span> <span data-ttu-id="730cb-140">要求會由 *_Host. cshtml* fallback 頁面處理，然後執行 Blazor 路由器並呈現計數器頁面。</span><span class="sxs-lookup"><span data-stu-id="730cb-140">The request gets handled by the *_Host.cshtml* fallback page, which then runs the Blazor router and renders the counter page.</span></span>

## <a name="upgrading-the-bundleconfig-process"></a><span data-ttu-id="730cb-141">升級 Bundleconfig.json 流程</span><span class="sxs-lookup"><span data-stu-id="730cb-141">Upgrading the BundleConfig Process</span></span>

<span data-ttu-id="730cb-142">結合 CSS 樣式表單和 JavaScript 檔案這類資產的技術已大幅演變，還有其他技術可提供快速進化的工具和技術來管理這些資源。</span><span class="sxs-lookup"><span data-stu-id="730cb-142">Technologies for bundling assets like CSS stylesheets and JavaScript files have evolved significantly, with other technologies providing quickly evolving tools and techniques for managing these resources.</span></span>  <span data-ttu-id="730cb-143">為此，我們建議您使用節點命令列工具（例如 Grunt/Gulp/WebPack）來封裝您的靜態資產。</span><span class="sxs-lookup"><span data-stu-id="730cb-143">To this end, we recommend using a Node command-line tool such as Grunt / Gulp / WebPack to package your static assets.</span></span>

<span data-ttu-id="730cb-144">Grunt、Gulp 和 WebPack 命令列工具及其相關設定可以新增至您的應用程式，ASP.NET Core 會在應用程式建立過程中，以不理會的模式略過這些檔案。</span><span class="sxs-lookup"><span data-stu-id="730cb-144">The Grunt, Gulp, and WebPack command-line tools and their associated configurations can be added to your application and ASP.NET Core will quietly ignore those files during the application build process.</span></span>  <span data-ttu-id="730cb-145">您可以新增呼叫來執行其工作，方法是在 `Target` 專案檔中加入，並使用類似下列的語法來觸發 gulp 腳本和 `min` 該腳本內的目標</span><span class="sxs-lookup"><span data-stu-id="730cb-145">You can add a call to run their tasks by adding a `Target` inside your project file with syntax similar to the following that would trigger a gulp script and the `min` target inside that script</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

<span data-ttu-id="730cb-146">如需有關管理 CSS 和 JavaScript 檔案的兩個策略的詳細資訊，請參閱 ASP.NET Core 檔中的組合[和縮小靜態資產](https://docs.microsoft.com/aspnet/core/client-side/bundling-and-minification)。</span><span class="sxs-lookup"><span data-stu-id="730cb-146">More details about both strategies to manage your CSS and JavaScript files are available in the [Bundle and minify static assets in ASP.NET Core](https://docs.microsoft.com/aspnet/core/client-side/bundling-and-minification) documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="730cb-147">[上一個](project-structure.md) 
>[下一步](components.md)</span><span class="sxs-lookup"><span data-stu-id="730cb-147">[Previous](project-structure.md)
[Next](components.md)</span></span>
