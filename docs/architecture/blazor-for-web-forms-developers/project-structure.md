---
title: Blazor 應用程式的專案結構
description: 瞭解 ASP.NET Web Forms 和 Blazor 專案的專案結構如何比較。
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: f9af8f88008ef45438a9104374d766cdbf8cc9a0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183816"
---
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="23e86-103">Blazor 應用程式的專案結構</span><span class="sxs-lookup"><span data-stu-id="23e86-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="23e86-104">儘管其重要的專案結構有所差異，ASP.NET Web Forms 和 Blazor 也會共用許多類似的概念。</span><span class="sxs-lookup"><span data-stu-id="23e86-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="23e86-105">在這裡，我們將探討 Blazor 專案的結構，並將其與 ASP.NET 的 Web form 專案進行比較。</span><span class="sxs-lookup"><span data-stu-id="23e86-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="23e86-106">若要建立您的第一個 Blazor 應用程式，請遵循[Blazor 快速入門步驟](/aspnet/core/blazor/get-started)中的指示。</span><span class="sxs-lookup"><span data-stu-id="23e86-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="23e86-107">您可以遵循指示來建立 Blazor 伺服器應用程式，或裝載于 ASP.NET Core 中的 Blazor WebAssembly 應用程式。</span><span class="sxs-lookup"><span data-stu-id="23e86-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="23e86-108">除了裝載模型特定的邏輯之外，這兩個專案中的大部分程式碼都相同。</span><span class="sxs-lookup"><span data-stu-id="23e86-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="23e86-109">專案檔</span><span class="sxs-lookup"><span data-stu-id="23e86-109">Project file</span></span>

<span data-ttu-id="23e86-110">Blazor 伺服器應用程式是 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="23e86-110">Blazor Server apps are .NET Core projects.</span></span> <span data-ttu-id="23e86-111">Blazor 伺服器應用程式的專案檔就像它可以取得的一樣簡單：</span><span class="sxs-lookup"><span data-stu-id="23e86-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="23e86-112">Blazor WebAssembly 應用程式的專案檔看起來有點複雜（確切版本號碼可能會不同）：</span><span class="sxs-lookup"><span data-stu-id="23e86-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

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

<span data-ttu-id="23e86-113">Blazor WebAssembly projects 的目標是以 WebAssembly 為基礎的 .NET 執行時間在瀏覽器中執行，而不是 .NET Core .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="23e86-113">Blazor WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="23e86-114">您無法將 .NET 安裝到網頁瀏覽器中，就像您可以在伺服器或開發人員電腦上一樣。</span><span class="sxs-lookup"><span data-stu-id="23e86-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="23e86-115">因此，專案會使用個別的封裝參考來參考 Blazor 架構。</span><span class="sxs-lookup"><span data-stu-id="23e86-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="23e86-116">相較之下，預設的 ASP.NET Web form 專案在其 *.csproj*檔案中包含將近300行的 XML，其中大部分是明確列出專案中的各種程式碼和內容檔案。</span><span class="sxs-lookup"><span data-stu-id="23e86-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="23e86-117">.Net Core 和 .NET Standard 型專案中的許多簡化來自于參考`Microsoft.NET.Sdk.Web` SDK 所匯入的預設目標和屬性，通常稱為「Web SDK」。</span><span class="sxs-lookup"><span data-stu-id="23e86-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="23e86-118">Web SDK 包含萬用字元和其他便利，可簡化專案中的程式碼和內容檔案的加入。</span><span class="sxs-lookup"><span data-stu-id="23e86-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="23e86-119">您不需要明確列出檔案。</span><span class="sxs-lookup"><span data-stu-id="23e86-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="23e86-120">以 .NET Core 為目標時，Web SDK 也會同時將架構參考新增至 .NET Core 和 ASP.NET Core 共用架構。</span><span class="sxs-lookup"><span data-stu-id="23e86-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="23e86-121">您可以從 [**方案總管**] 視窗中的 [相依性架構 **]**  > **節點查看**架構。</span><span class="sxs-lookup"><span data-stu-id="23e86-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="23e86-122">共用架構是安裝 .NET Core 時安裝在電腦上的元件集合。</span><span class="sxs-lookup"><span data-stu-id="23e86-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="23e86-123">雖然它們受到支援，但在 .NET Core 專案中，個別元件參考較不常見。</span><span class="sxs-lookup"><span data-stu-id="23e86-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="23e86-124">大部分的專案相依性會當做 NuGet 套件參考來處理。</span><span class="sxs-lookup"><span data-stu-id="23e86-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="23e86-125">您只需要參考 .NET Core 專案中的最上層套件相依性。</span><span class="sxs-lookup"><span data-stu-id="23e86-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="23e86-126">可轉移的相依性會自動包含在內。</span><span class="sxs-lookup"><span data-stu-id="23e86-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="23e86-127">不使用通常在 ASP.NET Web form 專案中找到的封裝 *.config*檔案來參考封裝，而是使用`<PackageReference>`專案，將套件參考新增至專案檔。</span><span class="sxs-lookup"><span data-stu-id="23e86-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="23e86-128">進入點</span><span class="sxs-lookup"><span data-stu-id="23e86-128">Entry point</span></span>

<span data-ttu-id="23e86-129">Blazor 伺服器應用程式的進入點是在*Program.cs*檔案中定義，如同您在主控台應用程式中所看到的。</span><span class="sxs-lookup"><span data-stu-id="23e86-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="23e86-130">當應用程式執行時，它會使用 web apps 特有的預設值來建立和執行 web 主機實例。</span><span class="sxs-lookup"><span data-stu-id="23e86-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="23e86-131">Web 主機會管理 Blazor 伺服器應用程式的生命週期，並設定主機層級服務。</span><span class="sxs-lookup"><span data-stu-id="23e86-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="23e86-132">這類服務的範例包括設定、記錄、相依性插入，以及 HTTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="23e86-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="23e86-133">這段程式碼大多是重複的，而且通常會保持不變。</span><span class="sxs-lookup"><span data-stu-id="23e86-133">This code is mostly boilerplate and is often left unchanged.</span></span>

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

<span data-ttu-id="23e86-134">Blazor WebAssembly apps 也會定義*Program.cs*中的進入點。</span><span class="sxs-lookup"><span data-stu-id="23e86-134">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="23e86-135">程式碼看起來稍有不同。</span><span class="sxs-lookup"><span data-stu-id="23e86-135">The code looks slightly different.</span></span> <span data-ttu-id="23e86-136">程式碼很類似，因為它會設定 app 主機，以提供相同的主機層級服務給應用程式。</span><span class="sxs-lookup"><span data-stu-id="23e86-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="23e86-137">不過，WebAssembly 應用程式主機不會設定 HTTP 伺服器，因為它會直接在瀏覽器中執行。</span><span class="sxs-lookup"><span data-stu-id="23e86-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="23e86-138">Blazor apps 具有`Startup`類別，而不是*global.asax*檔案，以定義應用程式的啟動邏輯。</span><span class="sxs-lookup"><span data-stu-id="23e86-138">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="23e86-139">`Startup`類別是用來設定應用程式和任何應用程式特定服務。</span><span class="sxs-lookup"><span data-stu-id="23e86-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="23e86-140">在 Blazor 伺服器應用程式中， `Startup`類別是用來針對用戶端瀏覽器與伺服器之間的 Blazor 所使用的即時連接設定端點。</span><span class="sxs-lookup"><span data-stu-id="23e86-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="23e86-141">在 Blazor WebAssembly 應用程式中， `Startup`類別會定義應用程式的根元件和應該呈現的位置。</span><span class="sxs-lookup"><span data-stu-id="23e86-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="23e86-142">我們將深入探討[應用程式啟動](./app-startup.md)一`Startup`節中的類別。</span><span class="sxs-lookup"><span data-stu-id="23e86-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="23e86-143">靜態檔案</span><span class="sxs-lookup"><span data-stu-id="23e86-143">Static files</span></span>

<span data-ttu-id="23e86-144">不同于 ASP.NET Web form 專案，Blazor 專案中的所有檔案都可以要求為靜態檔案。</span><span class="sxs-lookup"><span data-stu-id="23e86-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="23e86-145">只有*wwwroot*資料夾中的檔案可供 web 定址。</span><span class="sxs-lookup"><span data-stu-id="23e86-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="23e86-146">此資料夾稱為應用程式的「web 根目錄」。</span><span class="sxs-lookup"><span data-stu-id="23e86-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="23e86-147">應用程式的 web 根目錄以外的任何專案都*不是*web 可定址的。</span><span class="sxs-lookup"><span data-stu-id="23e86-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="23e86-148">此設定可提供額外的安全性等級，以防止透過 web 意外公開專案檔。</span><span class="sxs-lookup"><span data-stu-id="23e86-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="23e86-149">設定</span><span class="sxs-lookup"><span data-stu-id="23e86-149">Configuration</span></span>

<span data-ttu-id="23e86-150">ASP.NET Web Forms 應用程式中的設定通常會使用一或多個*web.config*檔案來處理。</span><span class="sxs-lookup"><span data-stu-id="23e86-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="23e86-151">Blazor 應用程式通常不會有*web.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="23e86-151">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="23e86-152">如果有的話，檔案只會在裝載于 IIS 上時用來設定 IIS 特定的設定。</span><span class="sxs-lookup"><span data-stu-id="23e86-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="23e86-153">相反地，Blazor 伺服器應用程式會使用 ASP.NET Core 設定抽象概念（Blazor WebAssembly 應用程式目前不支援相同的設定抽象概念，但這可能是未來新增的功能）。</span><span class="sxs-lookup"><span data-stu-id="23e86-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="23e86-154">例如，預設的 Blazor 伺服器應用程式會將某些設定儲存在*appsettings*中。</span><span class="sxs-lookup"><span data-stu-id="23e86-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="23e86-155">我們[將在設定一節](./config.md)中深入瞭解 ASP.NET Core 專案中的設定。</span><span class="sxs-lookup"><span data-stu-id="23e86-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="23e86-156">Razor 元件</span><span class="sxs-lookup"><span data-stu-id="23e86-156">Razor components</span></span>

<span data-ttu-id="23e86-157">Blazor projects 中的大部分檔案都是*razor*檔案。</span><span class="sxs-lookup"><span data-stu-id="23e86-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="23e86-158">Razor 是以 HTML C#為基礎的樣板化語言，可用來動態產生 web UI。</span><span class="sxs-lookup"><span data-stu-id="23e86-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="23e86-159">*Razor*檔案會定義構成應用程式 UI 的元件。</span><span class="sxs-lookup"><span data-stu-id="23e86-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="23e86-160">在大部分的情況下，Blazor 伺服器和 Blazor WebAssembly 應用程式的元件都相同。</span><span class="sxs-lookup"><span data-stu-id="23e86-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="23e86-161">Blazor 中的元件類似于 ASP.NET Web Forms 中的使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="23e86-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="23e86-162">建立專案時，每個 Razor 元件檔案都會編譯成 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="23e86-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="23e86-163">產生的類別會捕獲元件的狀態、呈現邏輯、生命週期方法、事件處理常式和其他邏輯。</span><span class="sxs-lookup"><span data-stu-id="23e86-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="23e86-164">我們將在[使用 Blazor 建立可重複使用的 UI 元件](./components.md)一節中探討撰寫元件。</span><span class="sxs-lookup"><span data-stu-id="23e86-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="23e86-165">*_Imports razor*檔案不是 razor 元件檔案。</span><span class="sxs-lookup"><span data-stu-id="23e86-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="23e86-166">相反地，它們會定義一組 Razor 指示詞，以匯入相同資料夾和其子資料夾內的其他*razor*檔案。</span><span class="sxs-lookup"><span data-stu-id="23e86-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="23e86-167">例如， *_Imports razor*檔案是新增`using`常用命名空間之語句的傳統方式：</span><span class="sxs-lookup"><span data-stu-id="23e86-167">For example, a *_Imports.razor* file is a conventional way to add `using` statements for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="23e86-168">頁面</span><span class="sxs-lookup"><span data-stu-id="23e86-168">Pages</span></span>

<span data-ttu-id="23e86-169">Blazor apps 中的頁面在哪裡？</span><span class="sxs-lookup"><span data-stu-id="23e86-169">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="23e86-170">Blazor 不會為可定址頁面定義個別的副檔名，例如 ASP.NET Web Forms 應用程式中的 *.aspx*檔案。</span><span class="sxs-lookup"><span data-stu-id="23e86-170">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="23e86-171">相反地，頁面是藉由將路由指派給元件來定義。</span><span class="sxs-lookup"><span data-stu-id="23e86-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="23e86-172">通常會使用`@page` Razor 指示詞來指派路由。</span><span class="sxs-lookup"><span data-stu-id="23e86-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="23e86-173">例如，在`Counter` *Pages/Counter*檔案中撰寫的元件會定義下列路由：</span><span class="sxs-lookup"><span data-stu-id="23e86-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="23e86-174">Blazor 中的路由是在用戶端處理，而不是在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="23e86-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="23e86-175">當使用者在瀏覽器中導覽時，Blazor 會攔截導覽，然後以相符的路由呈現元件。</span><span class="sxs-lookup"><span data-stu-id="23e86-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span> 

<span data-ttu-id="23e86-176">元件路由目前不是由元件的檔案位置推斷，像是使用 *.aspx*頁面。</span><span class="sxs-lookup"><span data-stu-id="23e86-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="23e86-177">未來可能會加入這項功能。</span><span class="sxs-lookup"><span data-stu-id="23e86-177">This feature may be added in the future.</span></span> <span data-ttu-id="23e86-178">每個路由都必須在元件上明確指定。</span><span class="sxs-lookup"><span data-stu-id="23e86-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="23e86-179">將可路由的元件儲存在*Pages*資料夾中沒有特殊意義，而且純粹是慣例。</span><span class="sxs-lookup"><span data-stu-id="23e86-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="23e86-180">我們將在 [[頁面]、[路由及](./pages-routing-layouts.md)配置] 區段中的 [在 Blazor 中路由]，更詳細地查看。</span><span class="sxs-lookup"><span data-stu-id="23e86-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="23e86-181">配置</span><span class="sxs-lookup"><span data-stu-id="23e86-181">Layout</span></span>

<span data-ttu-id="23e86-182">在 ASP.NET Web Forms 應用程式中，會使用主版頁面（*網站. master*）來處理一般頁面配置。</span><span class="sxs-lookup"><span data-stu-id="23e86-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="23e86-183">在 Blazor apps 中，頁面配置是使用版面配置元件（*Shared/MainLayout*）來處理。</span><span class="sxs-lookup"><span data-stu-id="23e86-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="23e86-184">版面配置元件將在[頁面、路由和版面](./pages-routing-layouts.md)配置一節中更詳細地討論。</span><span class="sxs-lookup"><span data-stu-id="23e86-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="23e86-185">啟動程式 Blazor</span><span class="sxs-lookup"><span data-stu-id="23e86-185">Bootstrap Blazor</span></span>

<span data-ttu-id="23e86-186">若要啟動載入 Blazor，應用程式必須：</span><span class="sxs-lookup"><span data-stu-id="23e86-186">To bootstrap Blazor, the app must:</span></span>

* <span data-ttu-id="23e86-187">指定頁面上要呈現根元件（*Razor*）的位置。</span><span class="sxs-lookup"><span data-stu-id="23e86-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
* <span data-ttu-id="23e86-188">新增對應的 Blazor framework 腳本。</span><span class="sxs-lookup"><span data-stu-id="23e86-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="23e86-189">在 Blazor 伺服器應用程式中，根元件的 [主機] 頁面會定義在 *_Host*檔中。</span><span class="sxs-lookup"><span data-stu-id="23e86-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="23e86-190">這個檔案會定義 Razor 頁面，而不是元件。</span><span class="sxs-lookup"><span data-stu-id="23e86-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="23e86-191">Razor Pages 使用 Razor 語法定義伺服器可定址的頁面，非常類似于 *.aspx*頁面。</span><span class="sxs-lookup"><span data-stu-id="23e86-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="23e86-192">`Html.RenderComponentAsync<TComponent>(RenderMode)`方法是用來定義應該呈現根層級元件的位置。</span><span class="sxs-lookup"><span data-stu-id="23e86-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="23e86-193">`RenderMode`選項會指出元件的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="23e86-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="23e86-194">下表概述支援`RenderMode`的選項。</span><span class="sxs-lookup"><span data-stu-id="23e86-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="23e86-195">選項</span><span class="sxs-lookup"><span data-stu-id="23e86-195">Option</span></span>                        |<span data-ttu-id="23e86-196">描述</span><span class="sxs-lookup"><span data-stu-id="23e86-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="23e86-197">在建立與瀏覽器的連線之後，以互動方式呈現</span><span class="sxs-lookup"><span data-stu-id="23e86-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="23e86-198">先資源清單，然後以互動方式呈現</span><span class="sxs-lookup"><span data-stu-id="23e86-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="23e86-199">呈現為靜態內容</span><span class="sxs-lookup"><span data-stu-id="23e86-199">Rendered as static content</span></span>|

<span data-ttu-id="23e86-200">*_Framework/blazor*的腳本參考會建立與伺服器的即時連接，然後處理所有使用者互動和 UI 更新。</span><span class="sxs-lookup"><span data-stu-id="23e86-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="23e86-201">在 Blazor WebAssembly 應用程式中，[主機] 頁面是*wwwroot/index.html*底下的簡單靜態 HTML 檔案。</span><span class="sxs-lookup"><span data-stu-id="23e86-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="23e86-202">`<app>`元素是用來指出應該呈現根元件的位置。</span><span class="sxs-lookup"><span data-stu-id="23e86-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

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

<span data-ttu-id="23e86-203">要呈現的特定元件是在應用程式的`Startup.Configure`方法中，使用對應的 CSS 選取器來設定，以指出應該呈現元件的位置。</span><span class="sxs-lookup"><span data-stu-id="23e86-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

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

## <a name="build-output"></a><span data-ttu-id="23e86-204">組建輸出</span><span class="sxs-lookup"><span data-stu-id="23e86-204">Build output</span></span>

<span data-ttu-id="23e86-205">建立 Blazor 專案時，會將所有 Razor 元件和程式碼檔案編譯成單一元件。</span><span class="sxs-lookup"><span data-stu-id="23e86-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="23e86-206">不同于 ASP.NET Web Forms 專案，Blazor 不支援 UI 邏輯的執行時間編譯。</span><span class="sxs-lookup"><span data-stu-id="23e86-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="23e86-207">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="23e86-207">Run the app</span></span>

<span data-ttu-id="23e86-208">若要執行 Blazor 伺服器應用程式， `F5`請按 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="23e86-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="23e86-209">Blazor apps 不支援執行時間編譯。</span><span class="sxs-lookup"><span data-stu-id="23e86-209">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="23e86-210">若要查看程式碼和元件標記變更的結果，請重建並重新啟動已附加偵錯工具的應用程式。</span><span class="sxs-lookup"><span data-stu-id="23e86-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="23e86-211">如果您在未附加偵錯工具的`Ctrl+F5`情況下執行（），Visual Studio 會監看檔案變更，並在進行變更時重新開機應用程式。</span><span class="sxs-lookup"><span data-stu-id="23e86-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="23e86-212">您會在進行變更時手動重新整理瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="23e86-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="23e86-213">若要執行 Blazor WebAssembly 應用程式，請選擇下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="23e86-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

* <span data-ttu-id="23e86-214">直接使用開發伺服器來執行用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="23e86-214">Run the client project directly using the development server.</span></span>
* <span data-ttu-id="23e86-215">使用 ASP.NET Core 裝載應用程式時，執行伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="23e86-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="23e86-216">Blazor WebAssembly apps 不支援使用 Visual Studio 進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="23e86-216">Blazor WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="23e86-217">若要執行應用程式， `Ctrl+F5`請使用`F5`，而不是。</span><span class="sxs-lookup"><span data-stu-id="23e86-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="23e86-218">您可以改為直接在瀏覽器中調試 Blazor WebAssembly 應用程式。</span><span class="sxs-lookup"><span data-stu-id="23e86-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="23e86-219">如需詳細資訊，請參閱[Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) 。</span><span class="sxs-lookup"><span data-stu-id="23e86-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="23e86-220">[上一頁](hosting-models.md)
>[下一頁](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="23e86-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
