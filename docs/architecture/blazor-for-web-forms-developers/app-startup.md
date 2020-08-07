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
# <a name="app-startup"></a>應用程式啟動

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

針對 ASP.NET 所撰寫的應用程式通常會有一個檔案，該檔案會 `global.asax.cs` 定義 `Application_Start` 事件來控制哪些服務已設定，並可供 HTML 轉譯和 .net 處理之用。 本章探討 ASP.NET Core 和 Blazor 伺服器之間有何不同。

## <a name="application_start-and-web-forms"></a>Application_Start 和 Web 表單

預設 web form `Application_Start` 方法已隨著多年而增加，以處理許多設定工作。  Visual Studio 2019 中具有預設範本的全新 web form 專案現在包含下列設定邏輯：

- `RouteConfig`-應用程式 URL 路由
- `BundleConfig`-CSS 和 JavaScript 的捆綁和縮制

這些個別檔案都位於 `App_Start` 資料夾中，而且在應用程式開始時只會執行一次。  `RouteConfig`在 [預設專案] 範本中，新增 `FriendlyUrlSettings` for web forms 以允許應用程式 url 省略 `.ASPX` 副檔名。  預設範本也包含指示詞，可為易記 URL 的頁面提供永久的 HTTP 重新導向狀態碼 (HTTP 301) ，其 `.ASPX` 檔案名會省略副檔名。

有了 ASP.NET Core 和 Blazor，這些方法都可以簡化併合並至 `Startup` 類別中，或在使用一般 web 技術時予以排除。

## <a name="blazor-server-startup-structure"></a>Blazor 伺服器啟動結構

Blazor 伺服器應用程式位於 ASP.NET Core 3.0 或更新版本的應用程式之上。  ASP.NET Core web 應用程式是透過 `Startup.cs` 應用程式根資料夾的類別中的一對方法來設定。  啟動類別的預設內容列示如下

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

如同 ASP.NET Core 的其餘部分，啟動類別是使用相依性插入原則所建立。  `IConfiguration`會提供給在公用屬性中的函式和隱藏，以供稍後在設定期間存取。

`ConfigureServices`ASP.NET Core 中引進的方法可讓您針對架構的內建相依性插入容器設定各種 ASP.NET Core framework 服務。  各種 `services.Add*` 方法會新增服務，以啟用像是驗證、razor 頁面、MVC 控制器路由、SignalR 和 Blazor 伺服器之間互動等功能。  在 web form 中不需要這個方法，因為在 web.config 的設定檔中參考 ASP.NET，以定義 ASPX、ASCX、ASHX 和 .ASMX 檔案的剖析和處理。  如需有關 ASP.NET Core 中的相依性插入的詳細資訊，請[參閱線上檔](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)（英文）。

`Configure`方法會介紹要 ASP.NET Core 的 HTTP 管線概念。  在此方法中，我們會從上到下宣告[中介軟體](middleware.md)，以處理傳送至應用程式的每個要求。 這些預設設定中的大部分功能都散佈在 web form 設定檔中，而且現在已放在一個位置以方便參考。

不會再設定放在檔案中的自訂錯誤頁面 `web.config` ，但現在已設定為一律會在應用程式環境未加上標籤時顯示 `Development` 。  此外，ASP.NET Core 的應用程式現在已設定為使用 TLS 搭配方法呼叫來提供安全頁面 `UseHttpsRedirection` 。

接下來，會在中列出未預期的設定方法 `UseStaticFiles` 。  在 ASP.NET Core 中，必須明確啟用靜態檔案的要求 (例如 JavaScript、CSS 和影像檔) ，而且只有應用程式的*wwwroot*資料夾中的檔案預設為可公開定址。

下一行是從 web form 複寫其中一個設定選項的第一個程式碼： `UseRouting` 。  這個方法會將 ASP.NET Core 路由器新增至管線，而且可以在這裡或可以考慮路由傳送至的個別檔案中進行設定。  路由設定的詳細資訊可在[路由一節](pages-routing-layouts.md)中找到。

這個方法中的最後一個語句會定義 ASP.NET Core 正在接聽的端點。  這些是您可以在網頁伺服器上存取的 web 可存取位置，並會接收由 .NET 處理並傳回給您的一些內容。  第一個專案 `MapBlazorHub` 會設定 SignalR 中樞，以便在處理 Blazor 元件狀態和呈現的伺服器時，提供即時且持續的連接。  `MapFallbackToPage`方法呼叫會指出啟動 Blazor 應用程式之網頁的 web 可存取位置，也會設定應用程式以處理來自用戶端的深層連結要求。  如果您開啟瀏覽器，並直接流覽至應用程式中 Blazor 已處理的路由（例如， `/counter` 在預設專案範本中），您就會看到這項功能在工作中。 要求會由 *_Host. cshtml* fallback 頁面處理，然後執行 Blazor 路由器並呈現計數器頁面。

## <a name="upgrading-the-bundleconfig-process"></a>升級 Bundleconfig.json 流程

結合 CSS 樣式表單和 JavaScript 檔案這類資產的技術已大幅演變，還有其他技術可提供快速進化的工具和技術來管理這些資源。  為此，我們建議您使用節點命令列工具（例如 Grunt/Gulp/WebPack）來封裝您的靜態資產。

Grunt、Gulp 和 WebPack 命令列工具及其相關設定可以新增至您的應用程式，ASP.NET Core 會在應用程式建立過程中，以不理會的模式略過這些檔案。  您可以新增呼叫來執行其工作，方法是在 `Target` 專案檔中加入，並使用類似下列的語法來觸發 gulp 腳本和 `min` 該腳本內的目標

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

如需有關管理 CSS 和 JavaScript 檔案的兩個策略的詳細資訊，請參閱 ASP.NET Core 檔中的組合[和縮小靜態資產](https://docs.microsoft.com/aspnet/core/client-side/bundling-and-minification)。

>[!div class="step-by-step"]
>[上一個](project-structure.md) 
>[下一步](components.md)
