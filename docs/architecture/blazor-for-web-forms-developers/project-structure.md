---
title: 應用程式的專案結構 Blazor
description: 瞭解 ASP.NET Web Forms 和專案的專案結構如何 Blazor 進行比較。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: ba7113c88db728f30812821deaf7c06a80663d1f
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189085"
---
# <a name="project-structure-for-no-locblazor-apps"></a><span data-ttu-id="5fffb-103">應用程式的專案結構 Blazor</span><span class="sxs-lookup"><span data-stu-id="5fffb-103">Project structure for Blazor apps</span></span>

<span data-ttu-id="5fffb-104">雖然它們的專案結構差異很大，但 ASP.NET Web Forms 並 Blazor 共用許多相似的概念。</span><span class="sxs-lookup"><span data-stu-id="5fffb-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="5fffb-105">在這裡，我們將探討專案的結構 Blazor ，並將其與 ASP.NET Web Forms 專案進行比較。</span><span class="sxs-lookup"><span data-stu-id="5fffb-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="5fffb-106">若要建立您的第一個 Blazor 應用程式，請遵循[ Blazor 快速入門步驟](/aspnet/core/blazor/get-started)中的指示。</span><span class="sxs-lookup"><span data-stu-id="5fffb-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="5fffb-107">您可以依照指示，建立 Blazor 伺服器應用程式或裝載 Blazor WebAssembly 于 ASP.NET Core 中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fffb-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="5fffb-108">除了裝載模型特定邏輯之外，這兩個專案中的大部分程式碼都相同。</span><span class="sxs-lookup"><span data-stu-id="5fffb-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="5fffb-109">專案檔</span><span class="sxs-lookup"><span data-stu-id="5fffb-109">Project file</span></span>

<span data-ttu-id="5fffb-110">Blazor 伺服器應用程式是 .NET 專案。</span><span class="sxs-lookup"><span data-stu-id="5fffb-110">Blazor Server apps are .NET projects.</span></span> <span data-ttu-id="5fffb-111">Blazor伺服器應用程式的專案檔就像它可以取得的一樣簡單：</span><span class="sxs-lookup"><span data-stu-id="5fffb-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="5fffb-112">應用程式的專案檔 Blazor WebAssembly 看起來稍微多一點， (確切的版本號碼可能會) ：</span><span class="sxs-lookup"><span data-stu-id="5fffb-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

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

<span data-ttu-id="5fffb-113">BlazorWebAssembly專案目標， `Microsoft.NET.Sdk.BlazorWebAssembly` 而不是 `Microsoft.NET.Sdk.Web` sdk，因為它們會在以 .net 執行時間為基礎的瀏覽器中執行 WebAssembly 。</span><span class="sxs-lookup"><span data-stu-id="5fffb-113">Blazor WebAssembly project targets `Microsoft.NET.Sdk.BlazorWebAssembly` instead of `Microsoft.NET.Sdk.Web` sdk because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="5fffb-114">您無法將 .NET 安裝至網頁瀏覽器，就像在伺服器或開發人員電腦上一樣。</span><span class="sxs-lookup"><span data-stu-id="5fffb-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="5fffb-115">因此，專案會 Blazor 使用個別的套件參考來參考架構。</span><span class="sxs-lookup"><span data-stu-id="5fffb-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="5fffb-116">相較之下，預設的 ASP.NET Web Forms 專案在 *.csproj* 檔案中包含將近300行的 XML，其中大部分都是明確地列出專案中的各種程式碼和內容檔。</span><span class="sxs-lookup"><span data-stu-id="5fffb-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="5fffb-117">隨著 `.NET 5` `Blazor Server` 和應用程式的發行，您 `Blazor WebAssembly` 可以輕鬆地共用一個整合執行時間。</span><span class="sxs-lookup"><span data-stu-id="5fffb-117">With the release of `.NET 5` both `Blazor Server` and `Blazor WebAssembly` app can easily share one unified runtime.</span></span>

<span data-ttu-id="5fffb-118">雖然支援它們，但在 .NET 專案中，個別的元件參考較不常見。</span><span class="sxs-lookup"><span data-stu-id="5fffb-118">Although they're supported, individual assembly references are less common in .NET projects.</span></span> <span data-ttu-id="5fffb-119">大部分的專案相依性都會以 NuGet 套件參考的形式來處理。</span><span class="sxs-lookup"><span data-stu-id="5fffb-119">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="5fffb-120">您只需要參考 .NET 專案中的最上層套件相依性。</span><span class="sxs-lookup"><span data-stu-id="5fffb-120">You only need to reference top-level package dependencies in .NET projects.</span></span> <span data-ttu-id="5fffb-121">可轉移的相依性會自動包含在內。</span><span class="sxs-lookup"><span data-stu-id="5fffb-121">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="5fffb-122">封裝參考會使用專案新增至專案檔，而不是使用 ASP.NET Web Forms 專案中通常會用來參考封裝的 *packages.config* 檔案 `<PackageReference>` 。</span><span class="sxs-lookup"><span data-stu-id="5fffb-122">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="5fffb-123">進入點</span><span class="sxs-lookup"><span data-stu-id="5fffb-123">Entry point</span></span>

<span data-ttu-id="5fffb-124">Blazor伺服器應用程式的進入點是在 *Program.cs* 檔案中定義，如您在主控台應用程式中所見。</span><span class="sxs-lookup"><span data-stu-id="5fffb-124">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="5fffb-125">當應用程式執行時，它會使用 web apps 專屬的預設值來建立和執行 web 主控制項實例。</span><span class="sxs-lookup"><span data-stu-id="5fffb-125">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="5fffb-126">Web 主機會管理 Blazor 伺服器應用程式的生命週期，並設定主機層級的服務。</span><span class="sxs-lookup"><span data-stu-id="5fffb-126">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="5fffb-127">這類服務的範例包括設定、記錄、相依性插入和 HTTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="5fffb-127">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="5fffb-128">這段程式碼大多是重複的，而且通常保持不變。</span><span class="sxs-lookup"><span data-stu-id="5fffb-128">This code is mostly boilerplate and is often left unchanged.</span></span>

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

<span data-ttu-id="5fffb-129">BlazorWebAssembly應用程式也會在 *Program.cs* 中定義進入點。</span><span class="sxs-lookup"><span data-stu-id="5fffb-129">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="5fffb-130">程式碼看起來稍有不同。</span><span class="sxs-lookup"><span data-stu-id="5fffb-130">The code looks slightly different.</span></span> <span data-ttu-id="5fffb-131">程式碼很類似，因為它會設定應用程式主機，以提供相同的主機層級服務給應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fffb-131">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="5fffb-132">WebAssembly但是，應用程式主機不會設定 HTTP 伺服器，因為它會直接在瀏覽器中執行。</span><span class="sxs-lookup"><span data-stu-id="5fffb-132">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="5fffb-133">Blazor 應用程式有一個 `Startup` 類別，而不是 *global.asax* 檔案，以定義應用程式的啟動邏輯。</span><span class="sxs-lookup"><span data-stu-id="5fffb-133">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="5fffb-134">`Startup`類別可用來設定應用程式和任何應用程式特定的服務。</span><span class="sxs-lookup"><span data-stu-id="5fffb-134">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="5fffb-135">在 Blazor 伺服器應用程式中， `Startup` 類別是用來設定 Blazor 用戶端瀏覽器與伺服器之間所使用之即時連接的端點。</span><span class="sxs-lookup"><span data-stu-id="5fffb-135">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="5fffb-136">在 Blazor WebAssembly 應用程式中， `Startup` 類別會定義應用程式的根元件，以及應該呈現的位置。</span><span class="sxs-lookup"><span data-stu-id="5fffb-136">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="5fffb-137">我們將進一步探討 `Startup` [應用程式啟動](./app-startup.md) 區段中的類別。</span><span class="sxs-lookup"><span data-stu-id="5fffb-137">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="5fffb-138">靜態檔案</span><span class="sxs-lookup"><span data-stu-id="5fffb-138">Static files</span></span>

<span data-ttu-id="5fffb-139">不同于 ASP.NET Web Forms 專案，無法將專案中的所有檔案都 Blazor 要求為靜態檔案。</span><span class="sxs-lookup"><span data-stu-id="5fffb-139">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="5fffb-140">只有 [ *wwwroot* ] 資料夾中的檔案是 web 可定址的。</span><span class="sxs-lookup"><span data-stu-id="5fffb-140">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="5fffb-141">此資料夾稱為應用程式的「web 根目錄」。</span><span class="sxs-lookup"><span data-stu-id="5fffb-141">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="5fffb-142">應用程式 web 根目錄以外的任何程式都 *不是* web 可定址的。</span><span class="sxs-lookup"><span data-stu-id="5fffb-142">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="5fffb-143">這項設定可提供額外的安全性層級，以防止透過 web 意外公開專案檔。</span><span class="sxs-lookup"><span data-stu-id="5fffb-143">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="5fffb-144">設定</span><span class="sxs-lookup"><span data-stu-id="5fffb-144">Configuration</span></span>

<span data-ttu-id="5fffb-145">ASP.NET Web Forms 應用程式中的設定通常是使用一或多個 *web.config* 檔案來處理。</span><span class="sxs-lookup"><span data-stu-id="5fffb-145">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="5fffb-146">Blazor 應用程式通常不會有 *web.config* 的檔案。</span><span class="sxs-lookup"><span data-stu-id="5fffb-146">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="5fffb-147">如果有的話，該檔案只會用來設定 iis 上裝載的 IIS 特定設定。</span><span class="sxs-lookup"><span data-stu-id="5fffb-147">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="5fffb-148">相反地， Blazor 伺服器應用程式會使用 ASP.NET Core 設定抽象 (Blazor WebAssembly 應用程式目前不支援相同的設定抽象概念，但這可能是未來) 中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="5fffb-148">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="5fffb-149">例如，預設的 Blazor 伺服器應用程式會在 *appsettings.js* 中儲存部分設定。</span><span class="sxs-lookup"><span data-stu-id="5fffb-149">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="5fffb-150">我們 [將在 [設定](./config.md) ] 區段中深入瞭解 ASP.NET Core 專案中的設定。</span><span class="sxs-lookup"><span data-stu-id="5fffb-150">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="5fffb-151">Razor 元件</span><span class="sxs-lookup"><span data-stu-id="5fffb-151">Razor components</span></span>

<span data-ttu-id="5fffb-152">專案中的大部分檔案 Blazor 都是 *razor* 檔案。</span><span class="sxs-lookup"><span data-stu-id="5fffb-152">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="5fffb-153">Razor 是以 HTML 和 c # 為基礎的範本化語言，可用來動態產生 web UI。</span><span class="sxs-lookup"><span data-stu-id="5fffb-153">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="5fffb-154">*Razor* 檔案會定義構成應用程式 UI 的元件。</span><span class="sxs-lookup"><span data-stu-id="5fffb-154">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="5fffb-155">在大部分的情況下， Blazor 伺服器和 Blazor 應用程式的元件都是相同的 WebAssembly 。</span><span class="sxs-lookup"><span data-stu-id="5fffb-155">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="5fffb-156">中的元件 Blazor 類似于 ASP.NET Web Forms 中的使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="5fffb-156">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="5fffb-157">建立專案時，每個 Razor 元件檔都會編譯成 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="5fffb-157">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="5fffb-158">產生的類別會捕捉元件的狀態、轉譯邏輯、生命週期方法、事件處理常式和其他邏輯。</span><span class="sxs-lookup"><span data-stu-id="5fffb-158">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="5fffb-159">我們將在 [[建立可重複使用的 UI 元件 Blazor ](./components.md) ] 區段中查看撰寫元件。</span><span class="sxs-lookup"><span data-stu-id="5fffb-159">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="5fffb-160">*_Imports razor* 檔案不是 razor 元件檔案。</span><span class="sxs-lookup"><span data-stu-id="5fffb-160">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="5fffb-161">相反地，它們會定義一組 Razor 指示詞，以匯入至相同資料夾和其子資料夾內的其他 *razor* 檔案。</span><span class="sxs-lookup"><span data-stu-id="5fffb-161">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="5fffb-162">例如， *_Imports razor* 檔案是新增常用命名空間之指示詞的傳統方式 `using` ：</span><span class="sxs-lookup"><span data-stu-id="5fffb-162">For example, a *_Imports.razor* file is a conventional way to add `using` directives for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="5fffb-163">頁面</span><span class="sxs-lookup"><span data-stu-id="5fffb-163">Pages</span></span>

<span data-ttu-id="5fffb-164">應用程式中的頁面在哪裡 Blazor ？</span><span class="sxs-lookup"><span data-stu-id="5fffb-164">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="5fffb-165">Blazor 不會為可定址的頁面定義個別的副檔名，例如 ASP.NET Web Forms apps 中的 *.aspx* 檔案。</span><span class="sxs-lookup"><span data-stu-id="5fffb-165">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="5fffb-166">相反地，頁面是藉由指派元件的路由來定義。</span><span class="sxs-lookup"><span data-stu-id="5fffb-166">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="5fffb-167">路由通常會使用 Razor 指示詞來指派 `@page` 。</span><span class="sxs-lookup"><span data-stu-id="5fffb-167">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="5fffb-168">例如， `Counter` *頁面/計數器 razor* 檔案中撰寫的元件會定義下列路由：</span><span class="sxs-lookup"><span data-stu-id="5fffb-168">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="5fffb-169">中的路由 Blazor 會在用戶端處理，而不是在伺服器上處理。</span><span class="sxs-lookup"><span data-stu-id="5fffb-169">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="5fffb-170">當使用者在瀏覽器中流覽時，會攔截流覽， Blazor 然後以相符的路由呈現元件。</span><span class="sxs-lookup"><span data-stu-id="5fffb-170">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="5fffb-171">元件的檔案位置目前不會推斷元件路由，像是使用 *.aspx* 頁面一樣。</span><span class="sxs-lookup"><span data-stu-id="5fffb-171">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="5fffb-172">未來可能會加入這項功能。</span><span class="sxs-lookup"><span data-stu-id="5fffb-172">This feature may be added in the future.</span></span> <span data-ttu-id="5fffb-173">您必須在元件上明確指定每個路由。</span><span class="sxs-lookup"><span data-stu-id="5fffb-173">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="5fffb-174">將可路由傳送的元件儲存在 *Pages* 資料夾中沒有特殊意義，而且純粹是慣例。</span><span class="sxs-lookup"><span data-stu-id="5fffb-174">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="5fffb-175">在 Blazor [ [頁面]、[路由] 和 [版面](./pages-routing-layouts.md) 配置] 區段中，我們將更詳細地查看路由。</span><span class="sxs-lookup"><span data-stu-id="5fffb-175">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="5fffb-176">Layout</span><span class="sxs-lookup"><span data-stu-id="5fffb-176">Layout</span></span>

<span data-ttu-id="5fffb-177">在 ASP.NET Web Forms 應用程式中，會使用主版 *頁面 (的*) 來處理常見的頁面配置。</span><span class="sxs-lookup"><span data-stu-id="5fffb-177">In ASP.NET Web Forms apps, a common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="5fffb-178">在 Blazor 應用程式中，會使用版面配置元件 (*共用/MainLayout razor*) 來處理頁面配置。</span><span class="sxs-lookup"><span data-stu-id="5fffb-178">In Blazor apps, the page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="5fffb-179">版面配置元件將會在 [頁面] [、[路由] 和 [版面](./pages-routing-layouts.md) 配置] 區段中更詳細地討論。</span><span class="sxs-lookup"><span data-stu-id="5fffb-179">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-no-locblazor"></a><span data-ttu-id="5fffb-180">引導 Blazor</span><span class="sxs-lookup"><span data-stu-id="5fffb-180">Bootstrap Blazor</span></span>

<span data-ttu-id="5fffb-181">若要啟動 Blazor 程式，應用程式必須：</span><span class="sxs-lookup"><span data-stu-id="5fffb-181">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="5fffb-182">指定頁面上的根元件 (*應用程式的位置。 Razor*) 應該呈現。</span><span class="sxs-lookup"><span data-stu-id="5fffb-182">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="5fffb-183">新增對應的 Blazor 架構腳本。</span><span class="sxs-lookup"><span data-stu-id="5fffb-183">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="5fffb-184">在 Blazor 伺服器應用程式中，根元件的主機頁面會定義在 *_Host 的 cshtml* 檔案中。</span><span class="sxs-lookup"><span data-stu-id="5fffb-184">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="5fffb-185">此檔案會定義 Razor 頁面，而不是元件。</span><span class="sxs-lookup"><span data-stu-id="5fffb-185">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="5fffb-186">Razor Pages 使用 Razor 語法來定義伺服器可定址的頁面，非常類似 *.aspx* 頁面。</span><span class="sxs-lookup"><span data-stu-id="5fffb-186">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="5fffb-187">`Html.RenderComponentAsync<TComponent>(RenderMode)`方法是用來定義應呈現根層級元件的位置。</span><span class="sxs-lookup"><span data-stu-id="5fffb-187">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="5fffb-188">`RenderMode`選項表示元件的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="5fffb-188">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="5fffb-189">下表概述支援的 `RenderMode` 選項。</span><span class="sxs-lookup"><span data-stu-id="5fffb-189">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="5fffb-190">選項</span><span class="sxs-lookup"><span data-stu-id="5fffb-190">Option</span></span>                        |<span data-ttu-id="5fffb-191">Description</span><span class="sxs-lookup"><span data-stu-id="5fffb-191">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="5fffb-192">一旦建立與瀏覽器的連線之後，以互動方式轉譯</span><span class="sxs-lookup"><span data-stu-id="5fffb-192">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="5fffb-193">第一個資源清單，然後以互動方式轉譯</span><span class="sxs-lookup"><span data-stu-id="5fffb-193">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="5fffb-194">呈現為靜態內容</span><span class="sxs-lookup"><span data-stu-id="5fffb-194">Rendered as static content</span></span>|

<span data-ttu-id="5fffb-195">*_Framework/blazor.server.js* 的腳本參考會建立與伺服器的即時連接，然後處理所有使用者互動和 UI 更新。</span><span class="sxs-lookup"><span data-stu-id="5fffb-195">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="5fffb-196">在 Blazor WebAssembly 應用程式中，主機頁面是 *wwwroot/index.html* 下的簡單靜態 HTML 檔。</span><span class="sxs-lookup"><span data-stu-id="5fffb-196">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="5fffb-197">識別碼為的 `<div>` 元素 `app` 可用來指出應該呈現根元件的位置。</span><span class="sxs-lookup"><span data-stu-id="5fffb-197">The `<div>` element with id named `app` is used to indicate where the root component should be rendered.</span></span>

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

<span data-ttu-id="5fffb-198">要轉譯的根元件是在應用程式的方法中指定， `Program.Main` 並具有可透過相依性插入來註冊服務的彈性。</span><span class="sxs-lookup"><span data-stu-id="5fffb-198">The root component to render is specified in the app's `Program.Main` method with the flexibility to register services through dependency injection.</span></span> <span data-ttu-id="5fffb-199">如需詳細資訊，請參閱 ASP.NET Core 相依性 [ Blazor 插入](/aspnet/core/blazor/fundamentals/dependency-injection?pivots=webassembly)。</span><span class="sxs-lookup"><span data-stu-id="5fffb-199">For more information, see [ASP.NET Core Blazor dependency injection](/aspnet/core/blazor/fundamentals/dependency-injection?pivots=webassembly).</span></span>

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

## <a name="build-output"></a><span data-ttu-id="5fffb-200">建置輸出</span><span class="sxs-lookup"><span data-stu-id="5fffb-200">Build output</span></span>

<span data-ttu-id="5fffb-201">Blazor建立專案時，會將所有 Razor 元件和程式碼檔案編譯成單一元件。</span><span class="sxs-lookup"><span data-stu-id="5fffb-201">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="5fffb-202">不同于 ASP.NET Web Forms 專案， Blazor 不支援 UI 邏輯的執行時間編譯。</span><span class="sxs-lookup"><span data-stu-id="5fffb-202">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="5fffb-203">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="5fffb-203">Run the app</span></span>

<span data-ttu-id="5fffb-204">若要執行 Blazor 伺服器應用程式，請 `F5` 在 Visual Studio 中按。</span><span class="sxs-lookup"><span data-stu-id="5fffb-204">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="5fffb-205">Blazor 應用程式不支援執行時間編譯。</span><span class="sxs-lookup"><span data-stu-id="5fffb-205">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="5fffb-206">若要查看程式碼和元件標記變更的結果，請使用附加的偵錯工具重建並重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fffb-206">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="5fffb-207">如果您在未附加偵錯工具 (`Ctrl+F5`) 上執行，Visual Studio 會監看檔案變更，並在進行變更時重新開機應用程式。</span><span class="sxs-lookup"><span data-stu-id="5fffb-207">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="5fffb-208">您可以在進行變更時手動重新整理瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="5fffb-208">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="5fffb-209">若要執行 Blazor WebAssembly 應用程式，請選擇下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="5fffb-209">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="5fffb-210">使用開發伺服器直接執行用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="5fffb-210">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="5fffb-211">使用 ASP.NET Core 來裝載應用程式時，請執行伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="5fffb-211">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="5fffb-212">BlazorWebAssembly應用程式可以在瀏覽器和 Visual Studio 中進行偵錯工具。如需詳細資料，請參閱[Debug ASP.NET Core Blazor WebAssembly ](/aspnet/core/blazor/debug) 。</span><span class="sxs-lookup"><span data-stu-id="5fffb-212">Blazor WebAssembly apps can be debugged in both browser and Visual Studio.See [Debug ASP.NET Core Blazor WebAssembly](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5fffb-213">[上一個](hosting-models.md) 
>[下一步](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="5fffb-213">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
