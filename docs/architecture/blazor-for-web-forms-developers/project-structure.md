---
title: 布拉佐應用程式的專案結構
description: 瞭解ASP.NET Web 表單和 Blazor 專案的專案結構比較情況。
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 2c383e86ff22f5a3460476998992b66e9417cc11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401575"
---
# <a name="project-structure-for-blazor-apps"></a>布拉佐應用程式的專案結構

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

儘管它們的專案結構存在顯著差異，但 Web 表單和 Blazor ASP.NET有許多類似的概念。 在這裡，我們將查看 Blazor 專案的結構，並將其與ASP.NET Web 表單專案進行比較。

要創建您的第一個 Blazor 應用程式，請按照[Blazor 入門步驟](/aspnet/core/blazor/get-started)中的說明進行操作。 您可以按照說明創建 Blazor Server 應用或託管在 ASP.NET 核心中的 Blazor WebAssembly 應用。 除了特定于宿主模型的邏輯之外，兩個專案中的大多數代碼都是相同的。

## <a name="project-file"></a>專案檔

Blazor 伺服器應用程式是 .NET 核心專案。 Blazor Server 應用的專案檔案非常簡單，因為它可以得到：

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Blazor WebAssembly 應用的專案檔案看起來更參與（確切的版本號可能有所不同）：

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <RazorLangVersion>3.0</RazorLangVersion>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Blazor" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.Build" Version="3.1.0" PrivateAssets="all" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.HttpClient" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.DevServer" Version="3.1.0" PrivateAssets="all" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\Shared\BlazorWebAssemblyApp1.Shared.csproj" />
  </ItemGroup>

</Project>
```

Blazor WebAssembly 專案的目標是 .NET 標準而不是 .NET Core，因為它們在基於 WebAssembly 的 .NET 運行時的瀏覽器中運行。 不能像在伺服器或開發人員電腦上那樣將 .NET 安裝到 Web 瀏覽器中。 因此，該專案使用單個包引用引用 Blazor 框架。

相比之下，預設ASP.NET Web 表單專案在其 *.csproj*檔中包含近 300 行 XML，其中大多數顯式列出專案中的各種代碼和內容檔。 基於 .NET Core 和 .NET 標準專案中的許多簡化都來自通過引用`Microsoft.NET.Sdk.Web`SDK 導入的預設目標和屬性，通常簡稱為 Web SDK。 Web SDK 包括萬用字元和其他簡化專案中包含代碼和內容檔的便利。 您無需顯式列出檔。 在定位 .NET Core 時，Web SDK 還會添加對 .NET Core 和 ASP.NET核心共用框架的框架引用。 框架在**解決方案資源管理器**視窗中**的依賴項** > **框架**節點中可見。 共用框架是安裝 .NET Core 時安裝在電腦上的程式集的集合。

儘管它們受支援，但單個程式集引用在 .NET Core 專案中不太常見。 大多數專案依賴項都作為 NuGet 包引用處理。 您只需引用 .NET Core 專案中的頂級包依賴項。 自動包含傳遞依賴項。 套裝程式引用使用 元素添加到專案檔案中`<PackageReference>`，而不是使用 ASP.NET Web 表單專案中常見的*包.config*檔來引用包。

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>進入點

Blazor Server 應用的進入點在*Program.cs*檔中定義，正如您在主控台應用中看到的。 應用執行時，它使用特定于 Web 應用的預設值創建並運行 Web 主機實例。 Web 主機管理 Blazor Server 應用的生命週期並設置主機級服務。 此類服務的示例包括配置、日誌記錄、依賴項注入和 HTTP 伺服器。 此代碼大部分是樣板，通常保持不變。

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

Blazor WebAssembly 應用程式還在*Program.cs*中定義了進入點。 代碼看起來略有不同。 代碼類似，因為它正在設置應用主機以向應用提供相同的主機級服務。 但是，WebAssembly 應用主機不會設置 HTTP 伺服器，因為它直接在瀏覽器中執行。

Blazor 應用具有`Startup`一個類而不是*全域.asax*檔來定義應用程式的啟動邏輯。 該`Startup`類用於配置應用和任何特定于應用的服務。 在 Blazor Server 應用中`Startup`，類用於設置 Blazor 在用戶端瀏覽器和伺服器之間使用的即時連接的終結點。 在 Blazor WebAssembly 應用中`Startup`，類定義應用的根元件以及應呈現這些元件的位置。 我們將更深入地瞭解`Startup`[應用啟動](./app-startup.md)部分中的類。

## <a name="static-files"></a>靜態檔案

與 web 表單專案ASP.NET不同，並非所有 Blazor 專案中的檔都可以請求作為靜態檔。 只有*wwwroot*資料夾中的檔是 Web 位址定址的。 此資料夾將引用到應用程式的"Web 根"。 應用 Web 根之外的任何內容*都無法*Web 定址。 此設置提供了額外的安全級別，可防止意外在 Web 上公開專案檔案。

## <a name="configuration"></a>組態

ASP.NET Web 表單應用中的配置通常使用一個或多個*Web.config 檔*進行處理。 Blazor 應用程式通常沒有*Web.config*檔。 如果這樣做，則該檔僅用於在 IIS 上託管時配置特定于 IIS 的設置。 相反，Blazor Server 應用使用ASP.NET核心配置抽象（Blazor WebAssembly 應用目前不支援相同的配置抽象，但這可能是將來添加的功能）。 例如，預設的 Blazor Server 應用程式將某些*設置存儲在 appsettings.json*中。

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

我們將在"配置"部分中瞭解有關ASP.NET核心專案中[的配置](./config.md)。

## <a name="razor-components"></a>剃刀元件

布拉佐專案中的大多數檔都是 *.razor*檔。 Razor 是基於 HTML 和 C# 的範本化語言，用於動態生成 Web UI。 *.razor*檔定義構成應用 UI 的元件。 在大多數情況下，布拉佐伺服器和 Blazor WebAssembly 應用的元件都是相同的。 Blazor 中的元件類似于ASP.NET Web 表單中的使用者控制項。

生成專案時，每個 Razor 元件檔都會編譯為 .NET 類。 生成的類捕獲元件的狀態、呈現邏輯、生命週期方法、事件處理常式和其他邏輯。 我們將介紹使用 Blazor 部分構建[可重用 UI 元件](./components.md)的創作元件。

*_Imports.Razor*檔不是 Razor 元件檔。 相反，它們定義了一組 Razor 指令，以導入到同一資料夾中及其子資料夾中的其他 *.razor*檔中。 例如 *，_Imports.razor*檔是添加`using`常用命名空間語句的傳統方法：

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a>頁面

Blazor 應用程式中的頁面在哪裡？ Blazor 不會為可定址頁面定義單獨的檔副檔名，如 ASP.NET Web 表單應用中的 *.aspx*檔。 相反，頁面是通過為元件分配路由來定義的。 路由通常使用`@page`Razor 指令分配。 例如，`Counter`在*Pages/Counter.razor*檔中創作的元件定義了以下路由：

```razor
@page "/counter"
```

Blazor 中的路由是用戶端處理的，而不是伺服器上的。 當使用者在瀏覽器中導航時，Blazor 會攔截導航，然後使用匹配的路由呈現元件。

元件路由當前未像使用 *.aspx*頁一樣由元件的檔位置推斷。 此功能將來可能會添加。 必須在元件上顯式指定每個路由。 在*Pages*資料夾中存儲可路由元件沒有特殊含義，純屬慣例。

我們將在["頁面"、路由和佈局](./pages-routing-layouts.md)部分更詳細地介紹 Blazor 中的路由。

## <a name="layout"></a>版面配置

在ASP.NET Web 表單應用中，使用母版頁 *（Site.Master*） 處理常見頁面配置。 在 Blazor 應用中，頁面配置使用佈局元件 （*共用/MainLayout.razor）* 處理。 佈局元件將在[頁面、路由和佈局](./pages-routing-layouts.md)部分中詳細討論。

## <a name="bootstrap-blazor"></a>靴子布拉佐爾

要引導 Blazor，應用程式必須：

- 指定在頁面上應呈現根元件 （*App.Razor*） 的位置。
- 添加相應的 Blazor 框架腳本。

在 Blazor Server 應用中，根元件的主機頁在 *_Host.cshtml*檔中定義。 此檔定義剃刀頁，而不是元件。 Razor 頁面使用 Razor 語法來定義伺服器可定址頁面，非常類似于 *.aspx*頁面。 該方法`Html.RenderComponentAsync<TComponent>(RenderMode)`用於定義應呈現根級元件的位置。 該`RenderMode`選項指示元件的呈現方式。 下表概述了支援`RenderMode`的選項。

|選項                        |描述       |
|------------------------------|------------------|
|`RenderMode.Server`           |建立與瀏覽器的連接後以對話模式呈現|
|`RenderMode.ServerPrerendered`|首先預渲染，然後以對話模式呈現|
|`RenderMode.Static`           |呈現為靜態內容|

對 *_framework/blazor.server.js*的腳本引用建立與伺服器的即時連接，然後處理所有使用者交互和 UI 更新。

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

在 Blazor WebAssembly 應用程式中，主機頁是*wwwroot/index.html*下的簡單靜態 HTML 檔案。 該`<app>`元素用於指示應呈現根元件的位置。

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>Loading...</app>

    <script src="_framework/blazor.webassembly.js"></script>
</body>
</html>
```

要呈現的特定元件在應用`Startup.Configure`的方法中配置，並帶有相應的 CSS 選取器，指示應呈現元件的位置。

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IComponentsApplicationBuilder app)
    {
        app.AddComponent<App>("app");
    }
}
```

## <a name="build-output"></a>建置輸出

生成 Blazor 專案時，所有 Razor 元件和代碼檔都編譯到單個程式集中。 與web表單專案ASP.NET不同，Blazor 不支援 UI 邏輯的運行時編譯。

## <a name="run-the-app"></a>執行應用程式

要運行 Blazor 伺服器應用，`F5`請按視覺化工作室。 Blazor 應用不支援運行時編譯。 要查看代碼和元件標記更改的結果，請重新生成並重新啟動應用，並附加調試器。 如果在未附加調試器的情況下運行 （），Visual`Ctrl+F5`Studio 會監視檔更改，並在進行更改時重新開機應用。 在進行更改時，您可以手動刷新瀏覽器。

要運行 Blazor WebAssembly 應用，請選擇以下方法之一：

- 直接使用開發伺服器運行用戶端專案。
- 使用 ASP.NET 核心託管應用時運行伺服器專案。

Blazor WebAssembly 應用不支援使用視覺化工作室進行調試。 要運行應用，請使用`Ctrl+F5`而不是`F5`。 您可以直接在瀏覽器中調試 Blazor WebAssembly 應用。 有關詳細資訊[，請參閱調試ASP.NET核心布拉佐爾](/aspnet/core/blazor/debug)。

>[!div class="step-by-step"]
>[上一個](hosting-models.md)
>[下一個](app-startup.md)
