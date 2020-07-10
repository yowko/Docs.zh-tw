---
title: 應用程式的專案結構 Blazor
description: 瞭解 ASP.NET Web form 和專案的專案結構 Blazor 比較。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: 473b708a9b58fa88844bc6f79a898943d5a7db71
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173038"
---
# <a name="project-structure-for-blazor-apps"></a>應用程式的專案結構 Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

雖然其重要的專案結構有所差異，但 ASP.NET Web form 並 Blazor 分享許多類似的概念。 在這裡，我們將探討專案的結構 Blazor ，並將它與 ASP.NET Web form 專案進行比較。

若要建立您 Blazor 的第一個應用程式，請遵循[ Blazor 快速入門步驟](/aspnet/core/blazor/get-started)中的指示。 您可以遵循指示來建立 Blazor 伺服器應用程式或裝載 Blazor WebAssembly 于 ASP.NET Core 中的應用程式。 除了裝載模型特定的邏輯之外，這兩個專案中的大部分程式碼都相同。

## <a name="project-file"></a>專案檔

Blazor伺服器應用程式是 .NET Core 專案。 Blazor伺服器應用程式的專案檔就像它可以取得的一樣簡單：

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

應用程式的專案檔 Blazor WebAssembly 看起來有點複雜 (確切的版本號碼可能會) 不同：

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

BlazorWebAssembly專案會以 .NET Standard 而非 .Net Core 為目標，因為它們會在 .net 執行時間的瀏覽器中執行 WebAssembly 。 您無法將 .NET 安裝到網頁瀏覽器中，就像您可以在伺服器或開發人員電腦上一樣。 因此，專案會 Blazor 使用個別的封裝參考來參考架構。

相較之下，預設的 ASP.NET Web form 專案在其 *.csproj*檔案中包含將近300行的 XML，其中大部分是明確列出專案中的各種程式碼和內容檔案。 .NET Core 和 .NET Standard 型專案中的許多簡化來自于參考 SDK 所匯入的預設目標和屬性 `Microsoft.NET.Sdk.Web` ，通常稱為「WEB SDK」。 Web SDK 包含萬用字元和其他便利，可簡化專案中的程式碼和內容檔案的加入。 您不需要明確列出檔案。 以 .NET Core 為目標時，Web SDK 也會同時將架構參考新增至 .NET Core 和 ASP.NET Core 共用架構。 您可以從 [ **Dependencies**  >  **Frameworks** **方案總管**] 視窗中的 [相依性架構] 節點查看架構。 共用架構是安裝 .NET Core 時安裝在電腦上的元件集合。

雖然它們受到支援，但在 .NET Core 專案中，個別元件參考較不常見。 大部分的專案相依性會當做 NuGet 套件參考來處理。 您只需要參考 .NET Core 專案中的最上層套件相依性。 可轉移的相依性會自動包含在內。 不使用通常在 ASP.NET Web Forms 專案中找到的*packages.config*檔案來參考封裝，而是使用專案，將套件參考新增至專案檔 `<PackageReference>` 。

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>進入點

Blazor伺服器應用程式的進入點是在*Program.cs*檔案中定義，如同您在主控台應用程式中所看到的。 當應用程式執行時，它會使用 web apps 特有的預設值來建立和執行 web 主機實例。 Web 主機會管理 Blazor 伺服器應用程式的生命週期，並設定主機層級的服務。 這類服務的範例包括設定、記錄、相依性插入，以及 HTTP 伺服器。 這段程式碼大多是重複的，而且通常會保持不變。

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

BlazorWebAssembly應用程式也會在*Program.cs*中定義進入點。 程式碼看起來稍有不同。 程式碼很類似，因為它會設定 app 主機，以提供相同的主機層級服務給應用程式。 WebAssembly不過，應用程式主機不會設定 HTTP 伺服器，因為它會直接在瀏覽器中執行。

Blazor應用程式有一個 `Startup` 類別，而不是*global.asax*檔案，以定義應用程式的啟動邏輯。 `Startup`類別是用來設定應用程式和任何應用程式特定服務。 在 Blazor 伺服器應用程式中， `Startup` 類別是用來設定 Blazor 用戶端瀏覽器與伺服器之間所使用之即時連接的端點。 在 Blazor WebAssembly 應用程式中， `Startup` 類別會定義應用程式的根元件和應該呈現的位置。 我們將深入探討 `Startup` [應用程式啟動](./app-startup.md)一節中的類別。

## <a name="static-files"></a>靜態檔案

不同于 ASP.NET Web form 專案，專案中的所有檔案都 Blazor 可以要求為靜態檔案。 只有*wwwroot*資料夾中的檔案可供 web 定址。 此資料夾稱為應用程式的「web 根目錄」。 應用程式的 web 根目錄以外的任何專案都*不是*web 可定址的。 此設定可提供額外的安全性等級，以防止透過 web 意外公開專案檔。

## <a name="configuration"></a>設定

ASP.NET Web Forms 應用程式中的設定通常會使用一或多個*web.config*檔案進行處理。 Blazor應用程式通常不會有*web.config*檔案。 如果有的話，檔案只會在裝載于 IIS 上時用來設定 IIS 特定的設定。 相反地， Blazor 伺服器應用程式會使用 ASP.NET Core 設定抽象概念 (Blazor WebAssembly 應用程式目前不支援相同的設定抽象概念，但這可能是未來) 中新增的功能。 例如，預設的 Blazor 伺服器應用程式會在*appsettings.js*中儲存一些設定。

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

我們[將在設定一節](./config.md)中深入瞭解 ASP.NET Core 專案中的設定。

## <a name="razor-components"></a>Razor 元件

專案中的大部分檔案 Blazor 都是*razor*檔案。 Razor 是以 HTML 和 c # 為基礎的樣板化語言，用來動態產生 web UI。 *Razor*檔案會定義構成應用程式 UI 的元件。 在大部分的情況下， Blazor 伺服器和 Blazor 應用程式的元件都相同 WebAssembly 。 中的元件 Blazor 類似于 ASP.NET Web Forms 中的使用者控制項。

建立專案時，每個 Razor 元件檔案都會編譯成 .NET 類別。 產生的類別會捕獲元件的狀態、呈現邏輯、生命週期方法、事件處理常式和其他邏輯。 我們將在[建立可重複使用的 UI 元件 Blazor ](./components.md)一節中探討如何撰寫元件。

*_Imports razor*檔案不是 razor 元件檔案。 相反地，它們會定義一組 Razor 指示詞，以匯入相同資料夾和其子資料夾內的其他*razor*檔案。 例如， *_Imports razor*檔案是新增常用命名空間之指示詞的傳統方式 `using` ：

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

## <a name="pages"></a>Pages

應用程式中的頁面在哪裡 Blazor ？ Blazor不會為可定址頁面定義個別的副檔名，例如 ASP.NET Web Forms 應用程式中的 *.aspx*檔案。 相反地，頁面是藉由將路由指派給元件來定義。 通常會使用 Razor 指示詞來指派路由 `@page` 。 例如， `Counter` 在*Pages/Counter*檔案中撰寫的元件會定義下列路由：

```razor
@page "/counter"
```

中的路由 Blazor 是在用戶端處理，而不是在伺服器上。 當使用者在瀏覽器中導覽時，會 Blazor 攔截導覽，然後以相符的路由呈現元件。

元件路由目前不是由元件的檔案位置推斷，像是使用 *.aspx*頁面。 未來可能會加入這項功能。 每個路由都必須在元件上明確指定。 將可路由的元件儲存在*Pages*資料夾中沒有特殊意義，而且純粹是慣例。

我們將在 Blazor [頁面、路由和版面](./pages-routing-layouts.md)配置一節的路由中，更詳細地查看。

## <a name="layout"></a>配置

在 ASP.NET Web Forms 應用程式中，會使用主版頁面 (*網站*) 來處理一般頁面配置。 在 Blazor 應用程式中，頁面配置是使用版面配置元件 (*Shared/MainLayout. razor*) 來處理。 版面配置元件將在[頁面、路由和版面](./pages-routing-layouts.md)配置一節中更詳細地討論。

## <a name="bootstrap-blazor"></a>從中Blazor

若要啟動載入 Blazor ，應用程式必須：

- 指定要在頁面上放置根元件 (*應用程式。 Razor*) 應該呈現的位置。
- 新增對應的 Blazor 架構腳本。

在 Blazor 伺服器應用程式中，根元件的 [主機] 頁面會定義在 *_Host 的 cshtml*檔案中。 這個檔案會定義 Razor 頁面，而不是元件。 Razor Pages 使用 Razor 語法定義伺服器可定址的頁面，非常類似于 *.aspx*頁面。 `Html.RenderComponentAsync<TComponent>(RenderMode)`方法是用來定義應該呈現根層級元件的位置。 `RenderMode`選項會指出元件的呈現方式。 下表概述支援的 `RenderMode` 選項。

|選項                        |描述       |
|------------------------------|------------------|
|`RenderMode.Server`           |在建立與瀏覽器的連線之後，以互動方式呈現|
|`RenderMode.ServerPrerendered`|先資源清單，然後以互動方式呈現|
|`RenderMode.Static`           |呈現為靜態內容|

*_Framework/blazor.server.js*的腳本參考會建立與伺服器的即時連接，然後處理所有使用者互動和 UI 更新。

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

在 Blazor WebAssembly 應用程式中，[主機] 頁面是*wwwroot/index.html*底下簡單的靜態 HTML 檔案。 `<app>`元素是用來指出應該呈現根元件的位置。

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

要呈現的特定元件是在應用程式的方法中， `Startup.Configure` 使用對應的 CSS 選取器來設定，以指出應該呈現元件的位置。

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

Blazor建立專案時，會將所有 Razor 元件和程式碼檔案編譯成單一元件。 不同于 ASP.NET Web Forms 專案， Blazor 不支援 UI 邏輯的執行時間編譯。

## <a name="run-the-app"></a>執行應用程式

若要執行 Blazor 伺服器應用程式，請按 `F5` Visual Studio。 Blazor應用程式不支援執行時間編譯。 若要查看程式碼和元件標記變更的結果，請重建並重新啟動已附加偵錯工具的應用程式。 如果您在未附加偵錯工具的情況下執行 (`Ctrl+F5`) ，Visual Studio 會監看檔案變更，並在進行變更時重新開機應用程式。 您會在進行變更時手動重新整理瀏覽器。

若要執行 Blazor WebAssembly 應用程式，請選擇下列其中一種方法：

- 直接使用開發伺服器來執行用戶端專案。
- 使用 ASP.NET Core 裝載應用程式時，執行伺服器專案。

BlazorWebAssembly應用程式不支援使用 Visual Studio 進行調試。 若要執行應用程式，請使用， `Ctrl+F5` 而不是 `F5` 。 您可以改 Blazor WebAssembly 為直接在瀏覽器中偵錯工具。 如需詳細資訊，請參閱[Debug ASP.NET Core Blazor ](/aspnet/core/blazor/debug) 。

>[!div class="step-by-step"]
>[上一個](hosting-models.md) 
>[下一步](app-startup.md)
