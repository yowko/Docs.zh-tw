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
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="7da7d-103">布拉佐應用程式的專案結構</span><span class="sxs-lookup"><span data-stu-id="7da7d-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="7da7d-104">儘管它們的專案結構存在顯著差異，但 Web 表單和 Blazor ASP.NET有許多類似的概念。</span><span class="sxs-lookup"><span data-stu-id="7da7d-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="7da7d-105">在這裡，我們將查看 Blazor 專案的結構，並將其與ASP.NET Web 表單專案進行比較。</span><span class="sxs-lookup"><span data-stu-id="7da7d-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="7da7d-106">要創建您的第一個 Blazor 應用程式，請按照[Blazor 入門步驟](/aspnet/core/blazor/get-started)中的說明進行操作。</span><span class="sxs-lookup"><span data-stu-id="7da7d-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="7da7d-107">您可以按照說明創建 Blazor Server 應用或託管在 ASP.NET 核心中的 Blazor WebAssembly 應用。</span><span class="sxs-lookup"><span data-stu-id="7da7d-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="7da7d-108">除了特定于宿主模型的邏輯之外，兩個專案中的大多數代碼都是相同的。</span><span class="sxs-lookup"><span data-stu-id="7da7d-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="7da7d-109">專案檔</span><span class="sxs-lookup"><span data-stu-id="7da7d-109">Project file</span></span>

<span data-ttu-id="7da7d-110">Blazor 伺服器應用程式是 .NET 核心專案。</span><span class="sxs-lookup"><span data-stu-id="7da7d-110">Blazor Server apps are .NET Core projects.</span></span> <span data-ttu-id="7da7d-111">Blazor Server 應用的專案檔案非常簡單，因為它可以得到：</span><span class="sxs-lookup"><span data-stu-id="7da7d-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="7da7d-112">Blazor WebAssembly 應用的專案檔案看起來更參與（確切的版本號可能有所不同）：</span><span class="sxs-lookup"><span data-stu-id="7da7d-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

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

<span data-ttu-id="7da7d-113">Blazor WebAssembly 專案的目標是 .NET 標準而不是 .NET Core，因為它們在基於 WebAssembly 的 .NET 運行時的瀏覽器中運行。</span><span class="sxs-lookup"><span data-stu-id="7da7d-113">Blazor WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="7da7d-114">不能像在伺服器或開發人員電腦上那樣將 .NET 安裝到 Web 瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="7da7d-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="7da7d-115">因此，該專案使用單個包引用引用 Blazor 框架。</span><span class="sxs-lookup"><span data-stu-id="7da7d-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="7da7d-116">相比之下，預設ASP.NET Web 表單專案在其 *.csproj*檔中包含近 300 行 XML，其中大多數顯式列出專案中的各種代碼和內容檔。</span><span class="sxs-lookup"><span data-stu-id="7da7d-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="7da7d-117">基於 .NET Core 和 .NET 標準專案中的許多簡化都來自通過引用`Microsoft.NET.Sdk.Web`SDK 導入的預設目標和屬性，通常簡稱為 Web SDK。</span><span class="sxs-lookup"><span data-stu-id="7da7d-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="7da7d-118">Web SDK 包括萬用字元和其他簡化專案中包含代碼和內容檔的便利。</span><span class="sxs-lookup"><span data-stu-id="7da7d-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="7da7d-119">您無需顯式列出檔。</span><span class="sxs-lookup"><span data-stu-id="7da7d-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="7da7d-120">在定位 .NET Core 時，Web SDK 還會添加對 .NET Core 和 ASP.NET核心共用框架的框架引用。</span><span class="sxs-lookup"><span data-stu-id="7da7d-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="7da7d-121">框架在**解決方案資源管理器**視窗中**的依賴項** > **框架**節點中可見。</span><span class="sxs-lookup"><span data-stu-id="7da7d-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="7da7d-122">共用框架是安裝 .NET Core 時安裝在電腦上的程式集的集合。</span><span class="sxs-lookup"><span data-stu-id="7da7d-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="7da7d-123">儘管它們受支援，但單個程式集引用在 .NET Core 專案中不太常見。</span><span class="sxs-lookup"><span data-stu-id="7da7d-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="7da7d-124">大多數專案依賴項都作為 NuGet 包引用處理。</span><span class="sxs-lookup"><span data-stu-id="7da7d-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="7da7d-125">您只需引用 .NET Core 專案中的頂級包依賴項。</span><span class="sxs-lookup"><span data-stu-id="7da7d-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="7da7d-126">自動包含傳遞依賴項。</span><span class="sxs-lookup"><span data-stu-id="7da7d-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="7da7d-127">套裝程式引用使用 元素添加到專案檔案中`<PackageReference>`，而不是使用 ASP.NET Web 表單專案中常見的*包.config*檔來引用包。</span><span class="sxs-lookup"><span data-stu-id="7da7d-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="7da7d-128">進入點</span><span class="sxs-lookup"><span data-stu-id="7da7d-128">Entry point</span></span>

<span data-ttu-id="7da7d-129">Blazor Server 應用的進入點在*Program.cs*檔中定義，正如您在主控台應用中看到的。</span><span class="sxs-lookup"><span data-stu-id="7da7d-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="7da7d-130">應用執行時，它使用特定于 Web 應用的預設值創建並運行 Web 主機實例。</span><span class="sxs-lookup"><span data-stu-id="7da7d-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="7da7d-131">Web 主機管理 Blazor Server 應用的生命週期並設置主機級服務。</span><span class="sxs-lookup"><span data-stu-id="7da7d-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="7da7d-132">此類服務的示例包括配置、日誌記錄、依賴項注入和 HTTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="7da7d-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="7da7d-133">此代碼大部分是樣板，通常保持不變。</span><span class="sxs-lookup"><span data-stu-id="7da7d-133">This code is mostly boilerplate and is often left unchanged.</span></span>

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

<span data-ttu-id="7da7d-134">Blazor WebAssembly 應用程式還在*Program.cs*中定義了進入點。</span><span class="sxs-lookup"><span data-stu-id="7da7d-134">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="7da7d-135">代碼看起來略有不同。</span><span class="sxs-lookup"><span data-stu-id="7da7d-135">The code looks slightly different.</span></span> <span data-ttu-id="7da7d-136">代碼類似，因為它正在設置應用主機以向應用提供相同的主機級服務。</span><span class="sxs-lookup"><span data-stu-id="7da7d-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="7da7d-137">但是，WebAssembly 應用主機不會設置 HTTP 伺服器，因為它直接在瀏覽器中執行。</span><span class="sxs-lookup"><span data-stu-id="7da7d-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="7da7d-138">Blazor 應用具有`Startup`一個類而不是*全域.asax*檔來定義應用程式的啟動邏輯。</span><span class="sxs-lookup"><span data-stu-id="7da7d-138">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="7da7d-139">該`Startup`類用於配置應用和任何特定于應用的服務。</span><span class="sxs-lookup"><span data-stu-id="7da7d-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="7da7d-140">在 Blazor Server 應用中`Startup`，類用於設置 Blazor 在用戶端瀏覽器和伺服器之間使用的即時連接的終結點。</span><span class="sxs-lookup"><span data-stu-id="7da7d-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="7da7d-141">在 Blazor WebAssembly 應用中`Startup`，類定義應用的根元件以及應呈現這些元件的位置。</span><span class="sxs-lookup"><span data-stu-id="7da7d-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="7da7d-142">我們將更深入地瞭解`Startup`[應用啟動](./app-startup.md)部分中的類。</span><span class="sxs-lookup"><span data-stu-id="7da7d-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="7da7d-143">靜態檔案</span><span class="sxs-lookup"><span data-stu-id="7da7d-143">Static files</span></span>

<span data-ttu-id="7da7d-144">與 web 表單專案ASP.NET不同，並非所有 Blazor 專案中的檔都可以請求作為靜態檔。</span><span class="sxs-lookup"><span data-stu-id="7da7d-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="7da7d-145">只有*wwwroot*資料夾中的檔是 Web 位址定址的。</span><span class="sxs-lookup"><span data-stu-id="7da7d-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="7da7d-146">此資料夾將引用到應用程式的"Web 根"。</span><span class="sxs-lookup"><span data-stu-id="7da7d-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="7da7d-147">應用 Web 根之外的任何內容*都無法*Web 定址。</span><span class="sxs-lookup"><span data-stu-id="7da7d-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="7da7d-148">此設置提供了額外的安全級別，可防止意外在 Web 上公開專案檔案。</span><span class="sxs-lookup"><span data-stu-id="7da7d-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="7da7d-149">組態</span><span class="sxs-lookup"><span data-stu-id="7da7d-149">Configuration</span></span>

<span data-ttu-id="7da7d-150">ASP.NET Web 表單應用中的配置通常使用一個或多個*Web.config 檔*進行處理。</span><span class="sxs-lookup"><span data-stu-id="7da7d-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="7da7d-151">Blazor 應用程式通常沒有*Web.config*檔。</span><span class="sxs-lookup"><span data-stu-id="7da7d-151">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="7da7d-152">如果這樣做，則該檔僅用於在 IIS 上託管時配置特定于 IIS 的設置。</span><span class="sxs-lookup"><span data-stu-id="7da7d-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="7da7d-153">相反，Blazor Server 應用使用ASP.NET核心配置抽象（Blazor WebAssembly 應用目前不支援相同的配置抽象，但這可能是將來添加的功能）。</span><span class="sxs-lookup"><span data-stu-id="7da7d-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="7da7d-154">例如，預設的 Blazor Server 應用程式將某些*設置存儲在 appsettings.json*中。</span><span class="sxs-lookup"><span data-stu-id="7da7d-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="7da7d-155">我們將在"配置"部分中瞭解有關ASP.NET核心專案中[的配置](./config.md)。</span><span class="sxs-lookup"><span data-stu-id="7da7d-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="7da7d-156">剃刀元件</span><span class="sxs-lookup"><span data-stu-id="7da7d-156">Razor components</span></span>

<span data-ttu-id="7da7d-157">布拉佐專案中的大多數檔都是 *.razor*檔。</span><span class="sxs-lookup"><span data-stu-id="7da7d-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="7da7d-158">Razor 是基於 HTML 和 C# 的範本化語言，用於動態生成 Web UI。</span><span class="sxs-lookup"><span data-stu-id="7da7d-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="7da7d-159">*.razor*檔定義構成應用 UI 的元件。</span><span class="sxs-lookup"><span data-stu-id="7da7d-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="7da7d-160">在大多數情況下，布拉佐伺服器和 Blazor WebAssembly 應用的元件都是相同的。</span><span class="sxs-lookup"><span data-stu-id="7da7d-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="7da7d-161">Blazor 中的元件類似于ASP.NET Web 表單中的使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="7da7d-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="7da7d-162">生成專案時，每個 Razor 元件檔都會編譯為 .NET 類。</span><span class="sxs-lookup"><span data-stu-id="7da7d-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="7da7d-163">生成的類捕獲元件的狀態、呈現邏輯、生命週期方法、事件處理常式和其他邏輯。</span><span class="sxs-lookup"><span data-stu-id="7da7d-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="7da7d-164">我們將介紹使用 Blazor 部分構建[可重用 UI 元件](./components.md)的創作元件。</span><span class="sxs-lookup"><span data-stu-id="7da7d-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="7da7d-165">*_Imports.Razor*檔不是 Razor 元件檔。</span><span class="sxs-lookup"><span data-stu-id="7da7d-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="7da7d-166">相反，它們定義了一組 Razor 指令，以導入到同一資料夾中及其子資料夾中的其他 *.razor*檔中。</span><span class="sxs-lookup"><span data-stu-id="7da7d-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="7da7d-167">例如 *，_Imports.razor*檔是添加`using`常用命名空間語句的傳統方法：</span><span class="sxs-lookup"><span data-stu-id="7da7d-167">For example, a *_Imports.razor* file is a conventional way to add `using` statements for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="7da7d-168">頁面</span><span class="sxs-lookup"><span data-stu-id="7da7d-168">Pages</span></span>

<span data-ttu-id="7da7d-169">Blazor 應用程式中的頁面在哪裡？</span><span class="sxs-lookup"><span data-stu-id="7da7d-169">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="7da7d-170">Blazor 不會為可定址頁面定義單獨的檔副檔名，如 ASP.NET Web 表單應用中的 *.aspx*檔。</span><span class="sxs-lookup"><span data-stu-id="7da7d-170">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="7da7d-171">相反，頁面是通過為元件分配路由來定義的。</span><span class="sxs-lookup"><span data-stu-id="7da7d-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="7da7d-172">路由通常使用`@page`Razor 指令分配。</span><span class="sxs-lookup"><span data-stu-id="7da7d-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="7da7d-173">例如，`Counter`在*Pages/Counter.razor*檔中創作的元件定義了以下路由：</span><span class="sxs-lookup"><span data-stu-id="7da7d-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="7da7d-174">Blazor 中的路由是用戶端處理的，而不是伺服器上的。</span><span class="sxs-lookup"><span data-stu-id="7da7d-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="7da7d-175">當使用者在瀏覽器中導航時，Blazor 會攔截導航，然後使用匹配的路由呈現元件。</span><span class="sxs-lookup"><span data-stu-id="7da7d-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="7da7d-176">元件路由當前未像使用 *.aspx*頁一樣由元件的檔位置推斷。</span><span class="sxs-lookup"><span data-stu-id="7da7d-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="7da7d-177">此功能將來可能會添加。</span><span class="sxs-lookup"><span data-stu-id="7da7d-177">This feature may be added in the future.</span></span> <span data-ttu-id="7da7d-178">必須在元件上顯式指定每個路由。</span><span class="sxs-lookup"><span data-stu-id="7da7d-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="7da7d-179">在*Pages*資料夾中存儲可路由元件沒有特殊含義，純屬慣例。</span><span class="sxs-lookup"><span data-stu-id="7da7d-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="7da7d-180">我們將在["頁面"、路由和佈局](./pages-routing-layouts.md)部分更詳細地介紹 Blazor 中的路由。</span><span class="sxs-lookup"><span data-stu-id="7da7d-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="7da7d-181">版面配置</span><span class="sxs-lookup"><span data-stu-id="7da7d-181">Layout</span></span>

<span data-ttu-id="7da7d-182">在ASP.NET Web 表單應用中，使用母版頁 *（Site.Master*） 處理常見頁面配置。</span><span class="sxs-lookup"><span data-stu-id="7da7d-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="7da7d-183">在 Blazor 應用中，頁面配置使用佈局元件 （*共用/MainLayout.razor）* 處理。</span><span class="sxs-lookup"><span data-stu-id="7da7d-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="7da7d-184">佈局元件將在[頁面、路由和佈局](./pages-routing-layouts.md)部分中詳細討論。</span><span class="sxs-lookup"><span data-stu-id="7da7d-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="7da7d-185">靴子布拉佐爾</span><span class="sxs-lookup"><span data-stu-id="7da7d-185">Bootstrap Blazor</span></span>

<span data-ttu-id="7da7d-186">要引導 Blazor，應用程式必須：</span><span class="sxs-lookup"><span data-stu-id="7da7d-186">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="7da7d-187">指定在頁面上應呈現根元件 （*App.Razor*） 的位置。</span><span class="sxs-lookup"><span data-stu-id="7da7d-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="7da7d-188">添加相應的 Blazor 框架腳本。</span><span class="sxs-lookup"><span data-stu-id="7da7d-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="7da7d-189">在 Blazor Server 應用中，根元件的主機頁在 *_Host.cshtml*檔中定義。</span><span class="sxs-lookup"><span data-stu-id="7da7d-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="7da7d-190">此檔定義剃刀頁，而不是元件。</span><span class="sxs-lookup"><span data-stu-id="7da7d-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="7da7d-191">Razor 頁面使用 Razor 語法來定義伺服器可定址頁面，非常類似于 *.aspx*頁面。</span><span class="sxs-lookup"><span data-stu-id="7da7d-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="7da7d-192">該方法`Html.RenderComponentAsync<TComponent>(RenderMode)`用於定義應呈現根級元件的位置。</span><span class="sxs-lookup"><span data-stu-id="7da7d-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="7da7d-193">該`RenderMode`選項指示元件的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="7da7d-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="7da7d-194">下表概述了支援`RenderMode`的選項。</span><span class="sxs-lookup"><span data-stu-id="7da7d-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="7da7d-195">選項</span><span class="sxs-lookup"><span data-stu-id="7da7d-195">Option</span></span>                        |<span data-ttu-id="7da7d-196">描述</span><span class="sxs-lookup"><span data-stu-id="7da7d-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="7da7d-197">建立與瀏覽器的連接後以對話模式呈現</span><span class="sxs-lookup"><span data-stu-id="7da7d-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="7da7d-198">首先預渲染，然後以對話模式呈現</span><span class="sxs-lookup"><span data-stu-id="7da7d-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="7da7d-199">呈現為靜態內容</span><span class="sxs-lookup"><span data-stu-id="7da7d-199">Rendered as static content</span></span>|

<span data-ttu-id="7da7d-200">對 *_framework/blazor.server.js*的腳本引用建立與伺服器的即時連接，然後處理所有使用者交互和 UI 更新。</span><span class="sxs-lookup"><span data-stu-id="7da7d-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="7da7d-201">在 Blazor WebAssembly 應用程式中，主機頁是*wwwroot/index.html*下的簡單靜態 HTML 檔案。</span><span class="sxs-lookup"><span data-stu-id="7da7d-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="7da7d-202">該`<app>`元素用於指示應呈現根元件的位置。</span><span class="sxs-lookup"><span data-stu-id="7da7d-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

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

<span data-ttu-id="7da7d-203">要呈現的特定元件在應用`Startup.Configure`的方法中配置，並帶有相應的 CSS 選取器，指示應呈現元件的位置。</span><span class="sxs-lookup"><span data-stu-id="7da7d-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

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

## <a name="build-output"></a><span data-ttu-id="7da7d-204">建置輸出</span><span class="sxs-lookup"><span data-stu-id="7da7d-204">Build output</span></span>

<span data-ttu-id="7da7d-205">生成 Blazor 專案時，所有 Razor 元件和代碼檔都編譯到單個程式集中。</span><span class="sxs-lookup"><span data-stu-id="7da7d-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="7da7d-206">與web表單專案ASP.NET不同，Blazor 不支援 UI 邏輯的運行時編譯。</span><span class="sxs-lookup"><span data-stu-id="7da7d-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="7da7d-207">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="7da7d-207">Run the app</span></span>

<span data-ttu-id="7da7d-208">要運行 Blazor 伺服器應用，`F5`請按視覺化工作室。</span><span class="sxs-lookup"><span data-stu-id="7da7d-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="7da7d-209">Blazor 應用不支援運行時編譯。</span><span class="sxs-lookup"><span data-stu-id="7da7d-209">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="7da7d-210">要查看代碼和元件標記更改的結果，請重新生成並重新啟動應用，並附加調試器。</span><span class="sxs-lookup"><span data-stu-id="7da7d-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="7da7d-211">如果在未附加調試器的情況下運行 （），Visual`Ctrl+F5`Studio 會監視檔更改，並在進行更改時重新開機應用。</span><span class="sxs-lookup"><span data-stu-id="7da7d-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="7da7d-212">在進行更改時，您可以手動刷新瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="7da7d-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="7da7d-213">要運行 Blazor WebAssembly 應用，請選擇以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="7da7d-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="7da7d-214">直接使用開發伺服器運行用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="7da7d-214">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="7da7d-215">使用 ASP.NET 核心託管應用時運行伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="7da7d-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="7da7d-216">Blazor WebAssembly 應用不支援使用視覺化工作室進行調試。</span><span class="sxs-lookup"><span data-stu-id="7da7d-216">Blazor WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="7da7d-217">要運行應用，請使用`Ctrl+F5`而不是`F5`。</span><span class="sxs-lookup"><span data-stu-id="7da7d-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="7da7d-218">您可以直接在瀏覽器中調試 Blazor WebAssembly 應用。</span><span class="sxs-lookup"><span data-stu-id="7da7d-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="7da7d-219">有關詳細資訊[，請參閱調試ASP.NET核心布拉佐爾](/aspnet/core/blazor/debug)。</span><span class="sxs-lookup"><span data-stu-id="7da7d-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7da7d-220">[上一個](hosting-models.md)
>[下一個](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="7da7d-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
