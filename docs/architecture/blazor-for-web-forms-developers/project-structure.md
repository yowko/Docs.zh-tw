---
title: 應用程式的專案結構 Blazor
description: 瞭解 ASP.NET Web Forms 和專案的專案結構如何 Blazor 進行比較。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: 225ebbdd5e23516ae7d5465371e95c73c440c82b
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267772"
---
# <a name="project-structure-for-no-locblazor-apps"></a><span data-ttu-id="458fc-103">應用程式的專案結構 Blazor</span><span class="sxs-lookup"><span data-stu-id="458fc-103">Project structure for Blazor apps</span></span>

<span data-ttu-id="458fc-104">雖然它們的專案結構差異很大，但 ASP.NET Web Forms 並 Blazor 共用許多相似的概念。</span><span class="sxs-lookup"><span data-stu-id="458fc-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="458fc-105">在這裡，我們將探討專案的結構 Blazor ，並將其與 ASP.NET Web Forms 專案進行比較。</span><span class="sxs-lookup"><span data-stu-id="458fc-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="458fc-106">若要建立您的第一個 Blazor 應用程式，請遵循[ Blazor 快速入門步驟](/aspnet/core/blazor/get-started)中的指示。</span><span class="sxs-lookup"><span data-stu-id="458fc-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="458fc-107">您可以依照指示，建立 Blazor 伺服器應用程式或裝載 Blazor WebAssembly 于 ASP.NET Core 中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="458fc-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="458fc-108">除了裝載模型特定邏輯之外，這兩個專案中的大部分程式碼都相同。</span><span class="sxs-lookup"><span data-stu-id="458fc-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="458fc-109">專案檔</span><span class="sxs-lookup"><span data-stu-id="458fc-109">Project file</span></span>

<span data-ttu-id="458fc-110">Blazor 伺服器應用程式是 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="458fc-110">Blazor Server apps are .NET Core projects.</span></span> <span data-ttu-id="458fc-111">Blazor伺服器應用程式的專案檔就像它可以取得的一樣簡單：</span><span class="sxs-lookup"><span data-stu-id="458fc-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="458fc-112">應用程式的專案檔 Blazor WebAssembly 看起來稍微多一點， (確切的版本號碼可能會) ：</span><span class="sxs-lookup"><span data-stu-id="458fc-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

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

<span data-ttu-id="458fc-113">BlazorWebAssembly專案會以 .NET Standard 而非 .Net Core 為目標，因為它們會在以 .net 執行時間為基礎的瀏覽器中執行 WebAssembly 。</span><span class="sxs-lookup"><span data-stu-id="458fc-113">Blazor WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="458fc-114">您無法將 .NET 安裝至網頁瀏覽器，就像在伺服器或開發人員電腦上一樣。</span><span class="sxs-lookup"><span data-stu-id="458fc-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="458fc-115">因此，專案會 Blazor 使用個別的套件參考來參考架構。</span><span class="sxs-lookup"><span data-stu-id="458fc-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="458fc-116">相較之下，預設的 ASP.NET Web Forms 專案在 *.csproj* 檔案中包含將近300行的 XML，其中大部分都是明確地列出專案中的各種程式碼和內容檔。</span><span class="sxs-lookup"><span data-stu-id="458fc-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="458fc-117">.NET Core 和 .NET Standard 型專案中的許多簡化都來自于參考 SDK 所匯入的預設目標和屬性 `Microsoft.NET.Sdk.Web` ，通常只稱為 WEB SDK。</span><span class="sxs-lookup"><span data-stu-id="458fc-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="458fc-118">Web SDK 包含萬用字元和其他便利性，可簡化專案中包含程式碼和內容檔案的程式。</span><span class="sxs-lookup"><span data-stu-id="458fc-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="458fc-119">您不需要明確列出檔案。</span><span class="sxs-lookup"><span data-stu-id="458fc-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="458fc-120">以 .NET Core 為目標時，Web SDK 也會將架構參考新增至 .NET Core 和 ASP.NET Core 共用架構。</span><span class="sxs-lookup"><span data-stu-id="458fc-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="458fc-121">您可以從**Dependencies**  >  **Frameworks** **方案總管**視窗中的 [相依性架構] 節點看到這些架構。</span><span class="sxs-lookup"><span data-stu-id="458fc-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="458fc-122">共用架構是安裝 .NET Core 時安裝在電腦上的元件集合。</span><span class="sxs-lookup"><span data-stu-id="458fc-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="458fc-123">雖然支援它們，但在 .NET Core 專案中，個別的元件參考較不常見。</span><span class="sxs-lookup"><span data-stu-id="458fc-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="458fc-124">大部分的專案相依性都會以 NuGet 套件參考的形式來處理。</span><span class="sxs-lookup"><span data-stu-id="458fc-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="458fc-125">您只需要在 .NET Core 專案中參考最上層套件相依性。</span><span class="sxs-lookup"><span data-stu-id="458fc-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="458fc-126">可轉移的相依性會自動包含在內。</span><span class="sxs-lookup"><span data-stu-id="458fc-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="458fc-127">封裝參考會使用專案新增至專案檔，而不是使用 ASP.NET Web Forms 專案中通常會用來參考封裝的 *packages.config* 檔案 `<PackageReference>` 。</span><span class="sxs-lookup"><span data-stu-id="458fc-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="458fc-128">進入點</span><span class="sxs-lookup"><span data-stu-id="458fc-128">Entry point</span></span>

<span data-ttu-id="458fc-129">Blazor伺服器應用程式的進入點是在*Program.cs*檔案中定義，如您在主控台應用程式中所見。</span><span class="sxs-lookup"><span data-stu-id="458fc-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="458fc-130">當應用程式執行時，它會使用 web apps 專屬的預設值來建立和執行 web 主控制項實例。</span><span class="sxs-lookup"><span data-stu-id="458fc-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="458fc-131">Web 主機會管理 Blazor 伺服器應用程式的生命週期，並設定主機層級的服務。</span><span class="sxs-lookup"><span data-stu-id="458fc-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="458fc-132">這類服務的範例包括設定、記錄、相依性插入和 HTTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="458fc-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="458fc-133">這段程式碼大多是重複的，而且通常保持不變。</span><span class="sxs-lookup"><span data-stu-id="458fc-133">This code is mostly boilerplate and is often left unchanged.</span></span>

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

<span data-ttu-id="458fc-134">BlazorWebAssembly應用程式也會在*Program.cs*中定義進入點。</span><span class="sxs-lookup"><span data-stu-id="458fc-134">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="458fc-135">程式碼看起來稍有不同。</span><span class="sxs-lookup"><span data-stu-id="458fc-135">The code looks slightly different.</span></span> <span data-ttu-id="458fc-136">程式碼很類似，因為它會設定應用程式主機，以提供相同的主機層級服務給應用程式。</span><span class="sxs-lookup"><span data-stu-id="458fc-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="458fc-137">WebAssembly但是，應用程式主機不會設定 HTTP 伺服器，因為它會直接在瀏覽器中執行。</span><span class="sxs-lookup"><span data-stu-id="458fc-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="458fc-138">Blazor 應用程式有一個 `Startup` 類別，而不是 *global.asax* 檔案，以定義應用程式的啟動邏輯。</span><span class="sxs-lookup"><span data-stu-id="458fc-138">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="458fc-139">`Startup`類別可用來設定應用程式和任何應用程式特定的服務。</span><span class="sxs-lookup"><span data-stu-id="458fc-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="458fc-140">在 Blazor 伺服器應用程式中， `Startup` 類別是用來設定 Blazor 用戶端瀏覽器與伺服器之間所使用之即時連接的端點。</span><span class="sxs-lookup"><span data-stu-id="458fc-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="458fc-141">在 Blazor WebAssembly 應用程式中， `Startup` 類別會定義應用程式的根元件，以及應該呈現的位置。</span><span class="sxs-lookup"><span data-stu-id="458fc-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="458fc-142">我們將進一步探討 `Startup` [應用程式啟動](./app-startup.md) 區段中的類別。</span><span class="sxs-lookup"><span data-stu-id="458fc-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="458fc-143">靜態檔案</span><span class="sxs-lookup"><span data-stu-id="458fc-143">Static files</span></span>

<span data-ttu-id="458fc-144">不同于 ASP.NET Web Forms 專案，無法將專案中的所有檔案都 Blazor 要求為靜態檔案。</span><span class="sxs-lookup"><span data-stu-id="458fc-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="458fc-145">只有 [ *wwwroot* ] 資料夾中的檔案是 web 可定址的。</span><span class="sxs-lookup"><span data-stu-id="458fc-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="458fc-146">此資料夾稱為應用程式的「web 根目錄」。</span><span class="sxs-lookup"><span data-stu-id="458fc-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="458fc-147">應用程式 web 根目錄以外的任何程式都 *不是* web 可定址的。</span><span class="sxs-lookup"><span data-stu-id="458fc-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="458fc-148">這項設定可提供額外的安全性層級，以防止透過 web 意外公開專案檔。</span><span class="sxs-lookup"><span data-stu-id="458fc-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="458fc-149">組態</span><span class="sxs-lookup"><span data-stu-id="458fc-149">Configuration</span></span>

<span data-ttu-id="458fc-150">ASP.NET Web Forms 應用程式中的設定通常是使用一或多個 *web.config* 檔案來處理。</span><span class="sxs-lookup"><span data-stu-id="458fc-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="458fc-151">Blazor 應用程式通常不會有 *web.config* 的檔案。</span><span class="sxs-lookup"><span data-stu-id="458fc-151">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="458fc-152">如果有的話，該檔案只會用來設定 iis 上裝載的 IIS 特定設定。</span><span class="sxs-lookup"><span data-stu-id="458fc-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="458fc-153">相反地， Blazor 伺服器應用程式會使用 ASP.NET Core 設定抽象 (Blazor WebAssembly 應用程式目前不支援相同的設定抽象概念，但這可能是未來) 中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="458fc-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="458fc-154">例如，預設的 Blazor 伺服器應用程式會在 *appsettings.js*中儲存部分設定。</span><span class="sxs-lookup"><span data-stu-id="458fc-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="458fc-155">我們 [將在 [設定](./config.md) ] 區段中深入瞭解 ASP.NET Core 專案中的設定。</span><span class="sxs-lookup"><span data-stu-id="458fc-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="458fc-156">Razor 元件</span><span class="sxs-lookup"><span data-stu-id="458fc-156">Razor components</span></span>

<span data-ttu-id="458fc-157">專案中的大部分檔案 Blazor 都是 *razor* 檔案。</span><span class="sxs-lookup"><span data-stu-id="458fc-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="458fc-158">Razor 是以 HTML 和 c # 為基礎的範本化語言，可用來動態產生 web UI。</span><span class="sxs-lookup"><span data-stu-id="458fc-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="458fc-159">*Razor*檔案會定義構成應用程式 UI 的元件。</span><span class="sxs-lookup"><span data-stu-id="458fc-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="458fc-160">在大部分的情況下， Blazor 伺服器和 Blazor 應用程式的元件都是相同的 WebAssembly 。</span><span class="sxs-lookup"><span data-stu-id="458fc-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="458fc-161">中的元件 Blazor 類似于 ASP.NET Web Forms 中的使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="458fc-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="458fc-162">建立專案時，每個 Razor 元件檔都會編譯成 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="458fc-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="458fc-163">產生的類別會捕捉元件的狀態、轉譯邏輯、生命週期方法、事件處理常式和其他邏輯。</span><span class="sxs-lookup"><span data-stu-id="458fc-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="458fc-164">我們將在 [[建立可重複使用的 UI 元件 Blazor ](./components.md) ] 區段中查看撰寫元件。</span><span class="sxs-lookup"><span data-stu-id="458fc-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="458fc-165">*_Imports razor*檔案不是 razor 元件檔案。</span><span class="sxs-lookup"><span data-stu-id="458fc-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="458fc-166">相反地，它們會定義一組 Razor 指示詞，以匯入至相同資料夾和其子資料夾內的其他 *razor* 檔案。</span><span class="sxs-lookup"><span data-stu-id="458fc-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="458fc-167">例如， *_Imports razor* 檔案是新增常用命名空間之指示詞的傳統方式 `using` ：</span><span class="sxs-lookup"><span data-stu-id="458fc-167">For example, a *_Imports.razor* file is a conventional way to add `using` directives for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="458fc-168">頁面</span><span class="sxs-lookup"><span data-stu-id="458fc-168">Pages</span></span>

<span data-ttu-id="458fc-169">應用程式中的頁面在哪裡 Blazor ？</span><span class="sxs-lookup"><span data-stu-id="458fc-169">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="458fc-170">Blazor 不會為可定址的頁面定義個別的副檔名，例如 ASP.NET Web Forms apps 中的 *.aspx* 檔案。</span><span class="sxs-lookup"><span data-stu-id="458fc-170">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="458fc-171">相反地，頁面是藉由指派元件的路由來定義。</span><span class="sxs-lookup"><span data-stu-id="458fc-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="458fc-172">路由通常會使用 Razor 指示詞來指派 `@page` 。</span><span class="sxs-lookup"><span data-stu-id="458fc-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="458fc-173">例如， `Counter` *頁面/計數器 razor* 檔案中撰寫的元件會定義下列路由：</span><span class="sxs-lookup"><span data-stu-id="458fc-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="458fc-174">中的路由 Blazor 會在用戶端處理，而不是在伺服器上處理。</span><span class="sxs-lookup"><span data-stu-id="458fc-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="458fc-175">當使用者在瀏覽器中流覽時，會攔截流覽， Blazor 然後以相符的路由呈現元件。</span><span class="sxs-lookup"><span data-stu-id="458fc-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="458fc-176">元件的檔案位置目前不會推斷元件路由，像是使用 *.aspx* 頁面一樣。</span><span class="sxs-lookup"><span data-stu-id="458fc-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="458fc-177">未來可能會加入這項功能。</span><span class="sxs-lookup"><span data-stu-id="458fc-177">This feature may be added in the future.</span></span> <span data-ttu-id="458fc-178">您必須在元件上明確指定每個路由。</span><span class="sxs-lookup"><span data-stu-id="458fc-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="458fc-179">將可路由傳送的元件儲存在 *Pages* 資料夾中沒有特殊意義，而且純粹是慣例。</span><span class="sxs-lookup"><span data-stu-id="458fc-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="458fc-180">在 Blazor [ [頁面]、[路由] 和 [版面](./pages-routing-layouts.md) 配置] 區段中，我們將更詳細地查看路由。</span><span class="sxs-lookup"><span data-stu-id="458fc-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="458fc-181">Layout</span><span class="sxs-lookup"><span data-stu-id="458fc-181">Layout</span></span>

<span data-ttu-id="458fc-182">在 ASP.NET Web Forms 應用程式中，會使用主版 *頁面 (的*) 來處理常見的頁面配置。</span><span class="sxs-lookup"><span data-stu-id="458fc-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="458fc-183">在 Blazor 應用程式中，會使用版面配置元件 (*共用/MainLayout razor*) 來處理頁面配置。</span><span class="sxs-lookup"><span data-stu-id="458fc-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="458fc-184">版面配置元件將會在 [頁面] [、[路由] 和 [版面](./pages-routing-layouts.md) 配置] 區段中更詳細地討論。</span><span class="sxs-lookup"><span data-stu-id="458fc-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-no-locblazor"></a><span data-ttu-id="458fc-185">引導 Blazor</span><span class="sxs-lookup"><span data-stu-id="458fc-185">Bootstrap Blazor</span></span>

<span data-ttu-id="458fc-186">若要啟動 Blazor 程式，應用程式必須：</span><span class="sxs-lookup"><span data-stu-id="458fc-186">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="458fc-187">指定頁面上的根元件 (*應用程式的位置。 Razor*) 應該呈現。</span><span class="sxs-lookup"><span data-stu-id="458fc-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="458fc-188">新增對應的 Blazor 架構腳本。</span><span class="sxs-lookup"><span data-stu-id="458fc-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="458fc-189">在 Blazor 伺服器應用程式中，根元件的主機頁面會定義在 *_Host 的 cshtml* 檔案中。</span><span class="sxs-lookup"><span data-stu-id="458fc-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="458fc-190">此檔案會定義 Razor 頁面，而不是元件。</span><span class="sxs-lookup"><span data-stu-id="458fc-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="458fc-191">Razor Pages 使用 Razor 語法來定義伺服器可定址的頁面，非常類似 *.aspx* 頁面。</span><span class="sxs-lookup"><span data-stu-id="458fc-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="458fc-192">`Html.RenderComponentAsync<TComponent>(RenderMode)`方法是用來定義應呈現根層級元件的位置。</span><span class="sxs-lookup"><span data-stu-id="458fc-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="458fc-193">`RenderMode`選項表示元件的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="458fc-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="458fc-194">下表概述支援的 `RenderMode` 選項。</span><span class="sxs-lookup"><span data-stu-id="458fc-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="458fc-195">選項</span><span class="sxs-lookup"><span data-stu-id="458fc-195">Option</span></span>                        |<span data-ttu-id="458fc-196">描述</span><span class="sxs-lookup"><span data-stu-id="458fc-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="458fc-197">一旦建立與瀏覽器的連線之後，以互動方式轉譯</span><span class="sxs-lookup"><span data-stu-id="458fc-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="458fc-198">第一個資源清單，然後以互動方式轉譯</span><span class="sxs-lookup"><span data-stu-id="458fc-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="458fc-199">呈現為靜態內容</span><span class="sxs-lookup"><span data-stu-id="458fc-199">Rendered as static content</span></span>|

<span data-ttu-id="458fc-200">*_Framework/blazor.server.js*的腳本參考會建立與伺服器的即時連接，然後處理所有使用者互動和 UI 更新。</span><span class="sxs-lookup"><span data-stu-id="458fc-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="458fc-201">在 Blazor WebAssembly 應用程式中，主機頁面是 *wwwroot/index.html*下的簡單靜態 HTML 檔。</span><span class="sxs-lookup"><span data-stu-id="458fc-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="458fc-202">`<app>`元素可用來指出應該呈現根元件的位置。</span><span class="sxs-lookup"><span data-stu-id="458fc-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

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

<span data-ttu-id="458fc-203">要轉譯的特定元件是在應用程式的方法中設定， `Startup.Configure` 並使用對應的 CSS 選取器來指出應該呈現元件的位置。</span><span class="sxs-lookup"><span data-stu-id="458fc-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

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

## <a name="build-output"></a><span data-ttu-id="458fc-204">建置輸出</span><span class="sxs-lookup"><span data-stu-id="458fc-204">Build output</span></span>

<span data-ttu-id="458fc-205">Blazor建立專案時，會將所有 Razor 元件和程式碼檔案編譯成單一元件。</span><span class="sxs-lookup"><span data-stu-id="458fc-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="458fc-206">不同于 ASP.NET Web Forms 專案， Blazor 不支援 UI 邏輯的執行時間編譯。</span><span class="sxs-lookup"><span data-stu-id="458fc-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="458fc-207">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="458fc-207">Run the app</span></span>

<span data-ttu-id="458fc-208">若要執行 Blazor 伺服器應用程式，請 `F5` 在 Visual Studio 中按。</span><span class="sxs-lookup"><span data-stu-id="458fc-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="458fc-209">Blazor 應用程式不支援執行時間編譯。</span><span class="sxs-lookup"><span data-stu-id="458fc-209">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="458fc-210">若要查看程式碼和元件標記變更的結果，請使用附加的偵錯工具重建並重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="458fc-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="458fc-211">如果您在未附加偵錯工具 (`Ctrl+F5`) 上執行，Visual Studio 會監看檔案變更，並在進行變更時重新開機應用程式。</span><span class="sxs-lookup"><span data-stu-id="458fc-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="458fc-212">您可以在進行變更時手動重新整理瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="458fc-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="458fc-213">若要執行 Blazor WebAssembly 應用程式，請選擇下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="458fc-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="458fc-214">使用開發伺服器直接執行用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="458fc-214">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="458fc-215">使用 ASP.NET Core 來裝載應用程式時，請執行伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="458fc-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="458fc-216">BlazorWebAssembly應用程式不支援使用 Visual Studio 的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="458fc-216">Blazor WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="458fc-217">若要執行應用程式，請使用 `Ctrl+F5` 而不是 `F5` 。</span><span class="sxs-lookup"><span data-stu-id="458fc-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="458fc-218">您可以改 Blazor WebAssembly 為直接在瀏覽器中進行應用程式的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="458fc-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="458fc-219">請參閱[Debug Blazor ASP.NET Core](/aspnet/core/blazor/debug)以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="458fc-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="458fc-220">[上一個](hosting-models.md) 
>[下一步](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="458fc-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
