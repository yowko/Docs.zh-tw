---
title: 應用程式的專案結構 Blazor
description: 瞭解 ASP.NET Web Forms 和專案的專案結構如何 Blazor 進行比較。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: d91430eb654ee16934408bf064803b34ca700640
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509802"
---
# <a name="project-structure-for-no-locblazor-apps"></a>應用程式的專案結構 Blazor

雖然它們的專案結構差異很大，但 ASP.NET Web Forms 並 Blazor 共用許多相似的概念。 在這裡，我們將探討專案的結構 Blazor ，並將其與 ASP.NET Web Forms 專案進行比較。

若要建立您的第一個 Blazor 應用程式，請遵循[ Blazor 快速入門步驟](/aspnet/core/blazor/get-started)中的指示。 您可以依照指示，建立 Blazor 伺服器應用程式或裝載 Blazor WebAssembly 于 ASP.NET Core 中的應用程式。 除了裝載模型特定邏輯之外，這兩個專案中的大部分程式碼都相同。

## <a name="project-file"></a>專案檔

Blazor 伺服器應用程式是 .NET 專案。 Blazor伺服器應用程式的專案檔就像它可以取得的一樣簡單：

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

應用程式的專案檔 Blazor WebAssembly 看起來稍微多一點， (確切的版本號碼可能會) ：

```xml
<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly" Version="5.0.0" />
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly.DevServer" Version="5.0.0" PrivateAssets="all" />
    <PackageReference Include="System.Net.Http.Json" Version="5.0.0" />
  </ItemGroup>

</Project>
```

BlazorWebAssembly專案目標， `Microsoft.NET.Sdk.BlazorWebAssembly` 而不是 `Microsoft.NET.Sdk.Web` sdk，因為它們會在以 .net 執行時間為基礎的瀏覽器中執行 WebAssembly 。 您無法將 .NET 安裝至網頁瀏覽器，就像在伺服器或開發人員電腦上一樣。 因此，專案會 Blazor 使用個別的套件參考來參考架構。

相較之下，預設的 ASP.NET Web Forms 專案在 *.csproj* 檔案中包含將近300行的 XML，其中大部分都是明確地列出專案中的各種程式碼和內容檔。 隨著 `.NET 5` `Blazor Server` 和應用程式的發行，您 `Blazor WebAssembly` 可以輕鬆地共用一個整合執行時間。

雖然支援它們，但在 .NET 專案中，個別的元件參考較不常見。 大部分的專案相依性都會以 NuGet 套件參考的形式來處理。 您只需要參考 .NET 專案中的最上層套件相依性。 可轉移的相依性會自動包含在內。 封裝參考會使用專案新增至專案檔，而不是使用 ASP.NET Web Forms 專案中通常會用來參考封裝的 *packages.config* 檔案 `<PackageReference>` 。

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>進入點

Blazor伺服器應用程式的進入點是在 *Program.cs* 檔案中定義，如您在主控台應用程式中所見。 當應用程式執行時，它會使用 web apps 專屬的預設值來建立和執行 web 主控制項實例。 Web 主機會管理 Blazor 伺服器應用程式的生命週期，並設定主機層級的服務。 這類服務的範例包括設定、記錄、相依性插入和 HTTP 伺服器。 這段程式碼大多是重複的，而且通常保持不變。

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

BlazorWebAssembly應用程式也會在 *Program.cs* 中定義進入點。 程式碼看起來稍有不同。 程式碼很類似，因為它會設定應用程式主機，以提供相同的主機層級服務給應用程式。 WebAssembly但是，應用程式主機不會設定 HTTP 伺服器，因為它會直接在瀏覽器中執行。

Blazor 應用程式有一個 `Startup` 類別，而不是 *global.asax* 檔案，以定義應用程式的啟動邏輯。 `Startup`類別可用來設定應用程式和任何應用程式特定的服務。 在 Blazor 伺服器應用程式中， `Startup` 類別是用來設定 Blazor 用戶端瀏覽器與伺服器之間所使用之即時連接的端點。 在 Blazor WebAssembly 應用程式中， `Startup` 類別會定義應用程式的根元件，以及應該呈現的位置。 我們將進一步探討 `Startup` [應用程式啟動](./app-startup.md) 區段中的類別。

## <a name="static-files"></a>靜態檔案

不同于 ASP.NET Web Forms 專案，無法將專案中的所有檔案都 Blazor 要求為靜態檔案。 只有 [ *wwwroot* ] 資料夾中的檔案是 web 可定址的。 此資料夾稱為應用程式的「web 根目錄」。 應用程式 web 根目錄以外的任何程式都 *不是* web 可定址的。 這項設定可提供額外的安全性層級，以防止透過 web 意外公開專案檔。

## <a name="configuration"></a>設定

ASP.NET Web Forms 應用程式中的設定通常是使用一或多個 *web.config* 檔案來處理。 Blazor 應用程式通常不會有 *web.config* 的檔案。 如果有的話，該檔案只會用來設定 iis 上裝載的 IIS 特定設定。 相反地， Blazor 伺服器應用程式會使用 ASP.NET Core 設定抽象 (Blazor WebAssembly 應用程式目前不支援相同的設定抽象概念，但這可能是未來) 中新增的功能。 例如，預設的 Blazor 伺服器應用程式會在 *appsettings.js* 中儲存部分設定。

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

我們 [將在 [設定](./config.md) ] 區段中深入瞭解 ASP.NET Core 專案中的設定。

## <a name="razor-components"></a>Razor 元件

專案中的大部分檔案 Blazor 都是 *razor* 檔案。 Razor 是以 HTML 和 c # 為基礎的範本化語言，可用來動態產生 web UI。 *Razor* 檔案會定義構成應用程式 UI 的元件。 在大部分的情況下， Blazor 伺服器和 Blazor 應用程式的元件都是相同的 WebAssembly 。 中的元件 Blazor 類似于 ASP.NET Web Forms 中的使用者控制項。

建立專案時，每個 Razor 元件檔都會編譯成 .NET 類別。 產生的類別會捕捉元件的狀態、轉譯邏輯、生命週期方法、事件處理常式和其他邏輯。 我們將在 [[建立可重複使用的 UI 元件 Blazor ](./components.md) ] 區段中查看撰寫元件。

*_Imports razor* 檔案不是 razor 元件檔案。 相反地，它們會定義一組 Razor 指示詞，以匯入至相同資料夾和其子資料夾內的其他 *razor* 檔案。 例如， *_Imports razor* 檔案是新增常用命名空間之指示詞的傳統方式 `using` ：

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

應用程式中的頁面在哪裡 Blazor ？ Blazor 不會為可定址的頁面定義個別的副檔名，例如 ASP.NET Web Forms apps 中的 *.aspx* 檔案。 相反地，頁面是藉由指派元件的路由來定義。 路由通常會使用 Razor 指示詞來指派 `@page` 。 例如， `Counter` *頁面/計數器 razor* 檔案中撰寫的元件會定義下列路由：

```razor
@page "/counter"
```

中的路由 Blazor 會在用戶端處理，而不是在伺服器上處理。 當使用者在瀏覽器中流覽時，會攔截流覽， Blazor 然後以相符的路由呈現元件。

元件的檔案位置目前不會推斷元件路由，像是使用 *.aspx* 頁面一樣。 未來可能會加入這項功能。 您必須在元件上明確指定每個路由。 將可路由傳送的元件儲存在 *Pages* 資料夾中沒有特殊意義，而且純粹是慣例。

在 Blazor [ [頁面]、[路由] 和 [版面](./pages-routing-layouts.md) 配置] 區段中，我們將更詳細地查看路由。

## <a name="layout"></a>配置

在 ASP.NET Web Forms 應用程式中，會使用主版 *頁面 (的*) 來處理常見的頁面配置。 在 Blazor 應用程式中，會使用版面配置元件 (*共用/MainLayout razor*) 來處理頁面配置。 版面配置元件將會在 [頁面] [、[路由] 和 [版面](./pages-routing-layouts.md) 配置] 區段中更詳細地討論。

## <a name="bootstrap-no-locblazor"></a>引導 Blazor

若要啟動 Blazor 程式，應用程式必須：

- 指定頁面上的根元件 (*應用程式的位置。 Razor*) 應該呈現。
- 新增對應的 Blazor 架構腳本。

在 Blazor 伺服器應用程式中，根元件的主機頁面會定義在 *_Host 的 cshtml* 檔案中。 此檔案會定義 Razor 頁面，而不是元件。 Razor Pages 使用 Razor 語法來定義伺服器可定址的頁面，非常類似 *.aspx* 頁面。 `Html.RenderComponentAsync<TComponent>(RenderMode)`方法是用來定義應呈現根層級元件的位置。 `RenderMode`選項表示元件的呈現方式。 下表概述支援的 `RenderMode` 選項。

|選項                        |說明       |
|------------------------------|------------------|
|`RenderMode.Server`           |一旦建立與瀏覽器的連線之後，以互動方式轉譯|
|`RenderMode.ServerPrerendered`|第一個資源清單，然後以互動方式轉譯|
|`RenderMode.Static`           |呈現為靜態內容|

*_Framework/blazor.server.js* 的腳本參考會建立與伺服器的即時連接，然後處理所有使用者互動和 UI 更新。

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

在 Blazor WebAssembly 應用程式中，主機頁面是 *wwwroot/index.html* 下的簡單靜態 HTML 檔。 識別碼為的 `<div>` 元素 `app` 可用來指出應該呈現根元件的位置。

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/app.css" rel="stylesheet" />
    <link href="blazor-web.styles.css" rel="stylesheet" />
</head>

<body>
    <div id="app">Loading...</div>

    <div id="blazor-error-ui">
        An unhandled error has occurred.
        <a href="" class="reload">Reload</a>
        <a class="dismiss">🗙</a>
    </div>
    <script src="_framework/blazor.webassembly.js"></script>
</body>

</html>

```

要轉譯的根元件是在應用程式的方法中設定， `Program.Main` 並具有可透過相依性插入來註冊不同服務的彈性。您可以參考將服務新增至應用程式[ Blazor WebAssembly ](https://docs.microsoft.com/aspnet/core/blazor/fundamentals/dependency-injection?view=aspnetcore-5.0#blazor-webassembly)

```csharp
public class Program
{
    public static async Task Main(string[] args)
    {
        var builder = WebAssemblyHostBuilder.CreateDefault(args);
        builder.RootComponents.Add<App>("#app");

        ....
        ....
    }
}
```

## <a name="build-output"></a>建置輸出

Blazor建立專案時，會將所有 Razor 元件和程式碼檔案編譯成單一元件。 不同于 ASP.NET Web Forms 專案， Blazor 不支援 UI 邏輯的執行時間編譯。

## <a name="run-the-app"></a>執行應用程式

若要執行 Blazor 伺服器應用程式，請 `F5` 在 Visual Studio 中按。 Blazor 應用程式不支援執行時間編譯。 若要查看程式碼和元件標記變更的結果，請使用附加的偵錯工具重建並重新啟動應用程式。 如果您在未附加偵錯工具 (`Ctrl+F5`) 上執行，Visual Studio 會監看檔案變更，並在進行變更時重新開機應用程式。 您可以在進行變更時手動重新整理瀏覽器。

若要執行 Blazor WebAssembly 應用程式，請選擇下列其中一種方法：

- 使用開發伺服器直接執行用戶端專案。
- 使用 ASP.NET Core 來裝載應用程式時，請執行伺服器專案。

BlazorWebAssembly應用程式可以在瀏覽器和 Visual Studio 中進行偵錯工具。如需詳細資料，請參閱[Debug ASP.NET Core Blazor WebAssembly ](/aspnet/core/blazor/debug) 。

>[!div class="step-by-step"]
>[上一個](hosting-models.md) 
>[下一步](app-startup.md)
