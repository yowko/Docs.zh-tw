---
title: 應用程式啟動
description: 瞭解如何為您的應用程式定義啟動邏輯。
author: csharpfritz
ms.author: jefritz
ms.date: 02/25/2020
ms.openlocfilehash: ea2ea458011d8351a834aa12db02e5d2bac2dc65
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267694"
---
# <a name="app-startup"></a>應用程式啟動

針對 ASP.NET 撰寫的應用程式通常會有一個檔案，該檔案會 `global.asax.cs` 定義 `Application_Start` 控制哪些服務已設定並可供 HTML 轉譯和 .net 處理使用的事件。 本章探討 ASP.NET Core 和 Blazor Server 的內容有何不同。

## <a name="application_start-and-web-forms"></a>Application_Start 和 Web Form

預設的 web form `Application_Start` 方法已有多年的成長，可處理許多設定工作。  Visual Studio 2019 中預設範本的全新 web form 專案現在包含下列設定邏輯：

- `RouteConfig` -應用程式 URL 路由
- `BundleConfig` -CSS 和 JavaScript 的組合和縮制

每個個別檔案都位於資料夾中 `App_Start` ，而且只會在應用程式啟動時執行一次。  `RouteConfig` 在 [預設專案] 範本中，加入 web form 的， `FriendlyUrlSettings` 以允許應用程式 url 省略 `.ASPX` 副檔名。  預設範本也包含指示詞，此指示詞會將頁面的永久 HTTP 重新導向狀態碼 (HTTP 301) ， `.ASPX` 並以省略副檔名的檔案名提供易記 URL。

有了 ASP.NET Core 和 Blazor，這些方法可以簡化併合並至 `Startup` 類別中，也可以排除在使用一般的 web 技術。

## <a name="blazor-server-startup-structure"></a>Blazor 伺服器啟動結構

Blazor 伺服器應用程式位於 ASP.NET Core 3.0 或更新版本的應用程式之上。  ASP.NET Core web 應用程式是透過 `Startup.cs` 應用程式根資料夾中類別的一對方法來設定。  Startup 類別的預設內容如下所示

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

和 ASP.NET Core 的其餘部分一樣，會使用相依性插入原則來建立啟動類別。  `IConfiguration`會提供給函式，並在公用屬性中隱藏，以便稍後在設定期間進行存取。

`ConfigureServices`ASP.NET Core 引進的方法可讓您針對架構的內建相依性插入容器設定各種 ASP.NET Core framework 服務。  不同的 `services.Add*` 方法會加入服務，以啟用驗證、razor 頁面、MVC 控制器路由、SignalR 和 Blazor 伺服器之間的互動等功能。  Web form 中不需要這個方法，因為在 web.config 設定檔中參考 ASP.NET 來定義 .ASPX、.ASCX、ASHX 和 .ASMX 檔案的剖析和處理。  有關 ASP.NET Core 中的相依性插入的詳細資訊，可在 [線上檔](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)中取得。

`Configure`方法會介紹要 ASP.NET Core 之 HTTP 管線的概念。  在此方法中，我們會從上到下宣告 [中介軟體](middleware.md) ，以處理傳送至應用程式的每個要求。 在預設設定中，大部分的功能都散佈在 web form 設定檔中，現在已在一個位置方便您參考。

您不再需要在檔案中設定自訂錯誤頁面 `web.config` ，但現在設定為在應用程式環境未標記時一律顯示 `Development` 。  此外，ASP.NET Core 的應用程式現在已設定為使用 TLS 搭配方法呼叫來提供安全的頁面 `UseHttpsRedirection` 。

接下來，會列出未預期的設定方法 `UseStaticFiles` 。  在 ASP.NET Core 中，支援靜態檔案的要求 (例如 JavaScript、CSS 和影像檔案) 必須明確啟用，而且預設只有應用程式 *wwwroot* 資料夾中的檔案可公開定址。

下一行是從 web forms 複製其中一個設定選項的第一行： `UseRouting` 。  這個方法會將 ASP.NET Core 路由器新增至管線，並可在這裡或在可考慮路由傳送的個別檔案中進行設定。  路由設定的詳細資訊可在 [路由] [區段](pages-routing-layouts.md)中找到。

此方法中的最後一個語句會定義 ASP.NET Core 正在接聽的端點。  這些是可供您在 web 伺服器上存取的 web 可存取位置，並接收由 .NET 處理並傳回給您的一些內容。  第一個專案會設定 SignalR 中樞，以用於 `MapBlazorHub` 提供處理 Blazor 元件之狀態和轉譯之伺服器的即時和持續連接。  `MapFallbackToPage`方法呼叫表示網頁的可存取位置，該頁面會啟動 Blazor 應用程式，同時也會設定應用程式以處理來自用戶端的深層連結要求。  如果您開啟瀏覽器，並在應用程式中直接流覽至 Blazor 處理的路由，例如 `/counter` 在預設專案範本中，您將會看到這項功能正在運作。 要求是由 *_Host 的 cshtml* 回溯頁面處理，然後執行 Blazor 路由器並轉譯計數器頁面。

## <a name="upgrading-the-bundleconfig-process"></a>升級 >bundleconfig.cs 流程

結合 CSS 樣式表單和 JavaScript 檔案等資產的技術已大幅演進，其他技術則提供快速演進的工具和技術來管理這些資源。  至此，我們建議使用節點命令列工具（例如 Grunt/Gulp/WebPack）來封裝您的靜態資產。

您可以將 Grunt、Gulp 和 WebPack 命令列工具與其相關聯的設定新增至您的應用程式，ASP.NET Core 將會在應用程式建立程式期間以安靜的情況忽略這些檔案。  您可以新增呼叫來執行其工作，方法是在 `Target` 您的專案檔中加入專案，並使用類似下面的語法來觸發 gulp 腳本和該 `min` 腳本內的目標

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

如需管理 CSS 和 JavaScript 檔案的兩個策略的詳細資料，請參閱套件組合 [和縮短靜態資產中的 ASP.NET Core](https://docs.microsoft.com/aspnet/core/client-side/bundling-and-minification) 檔。

>[!div class="step-by-step"]
>[上一個](project-structure.md) 
>[下一步](components.md)
