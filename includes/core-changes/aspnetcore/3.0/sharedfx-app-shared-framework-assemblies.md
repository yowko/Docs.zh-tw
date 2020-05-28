---
ms.openlocfilehash: d598d8d3203e804e5e935c3564b0053f9fc2e9a6
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144958"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="dcefa-101">共用架構：從 AspNetCore 移除的元件</span><span class="sxs-lookup"><span data-stu-id="dcefa-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="dcefa-102">從 ASP.NET Core 3.0 開始，ASP.NET Core 共用架構（ `Microsoft.AspNetCore.App` ）只包含由 Microsoft 完全開發、支援及維護的第一方元件。</span><span class="sxs-lookup"><span data-stu-id="dcefa-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="dcefa-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="dcefa-103">Change description</span></span>

<span data-ttu-id="dcefa-104">請將變更視為 ASP.NET Core 「平臺」的界限重新定義。</span><span class="sxs-lookup"><span data-stu-id="dcefa-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="dcefa-105">共用架構會[由任何人透過 GitHub 可建置](https://github.com/dotnet/source-build)，並會繼續為您的應用程式提供 .net Core 共用架構的現有優點。</span><span class="sxs-lookup"><span data-stu-id="dcefa-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="dcefa-106">其中一些優點包括較小的部署大小、集中式修補，以及更快速的啟動時間。</span><span class="sxs-lookup"><span data-stu-id="dcefa-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="dcefa-107">在變更過程中，會引進一些值得注意的重大變更 `Microsoft.AspNetCore.App` 。</span><span class="sxs-lookup"><span data-stu-id="dcefa-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dcefa-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="dcefa-108">Version introduced</span></span>

<span data-ttu-id="dcefa-109">3.0</span><span class="sxs-lookup"><span data-stu-id="dcefa-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="dcefa-110">舊的行為</span><span class="sxs-lookup"><span data-stu-id="dcefa-110">Old behavior</span></span>

<span data-ttu-id="dcefa-111">透過 `Microsoft.AspNetCore.App` 專案檔中的元素所參考的專案 `<PackageReference>` 。</span><span class="sxs-lookup"><span data-stu-id="dcefa-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="dcefa-112">此外，還 `Microsoft.AspNetCore.App` 包含下列子元件：</span><span class="sxs-lookup"><span data-stu-id="dcefa-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="dcefa-113">Json.NET （ `Newtonsoft.Json` ）</span><span class="sxs-lookup"><span data-stu-id="dcefa-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="dcefa-114">Entity Framework Core （前面加上的元件 `Microsoft.EntityFrameworkCore.` ）</span><span class="sxs-lookup"><span data-stu-id="dcefa-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="dcefa-115">Roslyn （ `Microsoft.CodeAnalysis` ）</span><span class="sxs-lookup"><span data-stu-id="dcefa-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="dcefa-116">新的行為</span><span class="sxs-lookup"><span data-stu-id="dcefa-116">New behavior</span></span>

<span data-ttu-id="dcefa-117">的參考不再 `Microsoft.AspNetCore.App` 需要 `<PackageReference>` 專案檔中的元素。</span><span class="sxs-lookup"><span data-stu-id="dcefa-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="dcefa-118">.NET Core SDK 支援名為的新專案 `<FrameworkReference>` ，它會取代的使用 `<PackageReference>` 。</span><span class="sxs-lookup"><span data-stu-id="dcefa-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="dcefa-119">如需詳細資訊，請參閱[dotnet/aspnetcore # 3612](https://github.com/dotnet/aspnetcore/issues/3612)。</span><span class="sxs-lookup"><span data-stu-id="dcefa-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="dcefa-120">Entity Framework Core 隨附為 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="dcefa-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="dcefa-121">這種變更會將出貨模型與 .NET 上的所有其他資料存取程式庫對齊。</span><span class="sxs-lookup"><span data-stu-id="dcefa-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="dcefa-122">它提供 Entity Framework Core 最簡單的途徑來繼續進行創新，同時支援各種不同的 .NET 平臺。</span><span class="sxs-lookup"><span data-stu-id="dcefa-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="dcefa-123">從共用架構移出 Entity Framework Core 不會影響其狀態，因為它是 Microsoft 開發、支援及可維護的程式庫。</span><span class="sxs-lookup"><span data-stu-id="dcefa-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="dcefa-124">[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)會繼續加以涵蓋。</span><span class="sxs-lookup"><span data-stu-id="dcefa-124">The [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) continues to cover it.</span></span>

<span data-ttu-id="dcefa-125">Json.NET 和 Entity Framework Core 會繼續與 ASP.NET Core 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="dcefa-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="dcefa-126">不過，它們不會包含在共用架構中。</span><span class="sxs-lookup"><span data-stu-id="dcefa-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="dcefa-127">如需詳細資訊，請參閱[.Net Core 3.0 中的 JSON 未來](https://github.com/dotnet/announcements/issues/90)。</span><span class="sxs-lookup"><span data-stu-id="dcefa-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="dcefa-128">另請參閱已從共用架構移除的[完整二進位檔清單](https://github.com/dotnet/aspnetcore/issues/3755)。</span><span class="sxs-lookup"><span data-stu-id="dcefa-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="dcefa-129">變更的原因</span><span class="sxs-lookup"><span data-stu-id="dcefa-129">Reason for change</span></span>

<span data-ttu-id="dcefa-130">這項變更可簡化的耗用量 `Microsoft.AspNetCore.App` ，並減少 NuGet 套件與共享架構之間的重複。</span><span class="sxs-lookup"><span data-stu-id="dcefa-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="dcefa-131">如需這種變更動機的詳細資訊，請參閱[這篇 blog 文章](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)。</span><span class="sxs-lookup"><span data-stu-id="dcefa-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dcefa-132">建議的動作</span><span class="sxs-lookup"><span data-stu-id="dcefa-132">Recommended action</span></span>

<span data-ttu-id="dcefa-133">專案不需要使用中的元件 `Microsoft.AspNetCore.App` 做為 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="dcefa-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="dcefa-134">為了簡化 ASP.NET Core 共用架構的目標和使用，已不再產生許多自 ASP.NET Core 1.0 所隨附的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="dcefa-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="dcefa-135">這些套件提供的 Api 仍然可供應用程式使用 `<FrameworkReference>` `Microsoft.AspNetCore.App` 。</span><span class="sxs-lookup"><span data-stu-id="dcefa-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="dcefa-136">常見的 API 範例包括 Kestrel、MVC 和 Razor。</span><span class="sxs-lookup"><span data-stu-id="dcefa-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="dcefa-137">這項變更不適用於透過 ASP.NET Core 2.x 參考的所有二進位檔 `Microsoft.AspNetCore.App` 。</span><span class="sxs-lookup"><span data-stu-id="dcefa-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="dcefa-138">值得注意的例外狀況包括：</span><span class="sxs-lookup"><span data-stu-id="dcefa-138">Notable exceptions include:</span></span>

- <span data-ttu-id="dcefa-139">`Microsoft.Extensions`繼續以 .NET Standard 為目標的程式庫會以 NuGet 套件的形式提供（請參閱 <https://github.com/dotnet/extensions> ）。</span><span class="sxs-lookup"><span data-stu-id="dcefa-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see <https://github.com/dotnet/extensions>).</span></span>
- <span data-ttu-id="dcefa-140">不屬於的 ASP.NET Core 小組所產生的 Api `Microsoft.AspNetCore.App` 。</span><span class="sxs-lookup"><span data-stu-id="dcefa-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="dcefa-141">例如，下列元件會以 NuGet 套件的形式提供：</span><span class="sxs-lookup"><span data-stu-id="dcefa-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="dcefa-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="dcefa-142">Entity Framework Core</span></span>
  - <span data-ttu-id="dcefa-143">提供協力廠商整合的 Api</span><span class="sxs-lookup"><span data-stu-id="dcefa-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="dcefa-144">實驗性功能</span><span class="sxs-lookup"><span data-stu-id="dcefa-144">Experimental features</span></span>
  - <span data-ttu-id="dcefa-145">相依性無法[滿足共用架構中的需求](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)的 api</span><span class="sxs-lookup"><span data-stu-id="dcefa-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="dcefa-146">維護 Json.NET 支援的 MVC 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="dcefa-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="dcefa-147">API 會以 NuGet 套件形式提供，以支援使用 Json.NET 和 MVC。</span><span class="sxs-lookup"><span data-stu-id="dcefa-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="dcefa-148">SignalR .NET 用戶端將繼續支援 .NET Standard 並以 NuGet 套件形式出貨。</span><span class="sxs-lookup"><span data-stu-id="dcefa-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="dcefa-149">其目的是要用於許多 .NET 執行時間，例如 Xamarin 和 UWP。</span><span class="sxs-lookup"><span data-stu-id="dcefa-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="dcefa-150">如需詳細資訊，請參閱[在3.0 中停止產生共用架構元件的封裝](https://github.com/dotnet/aspnetcore/issues/3756)。</span><span class="sxs-lookup"><span data-stu-id="dcefa-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="dcefa-151">如需討論，請參閱[dotnet/aspnetcore # 3757](https://github.com/dotnet/aspnetcore/issues/3757)。</span><span class="sxs-lookup"><span data-stu-id="dcefa-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="dcefa-152">類別</span><span class="sxs-lookup"><span data-stu-id="dcefa-152">Category</span></span>

<span data-ttu-id="dcefa-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dcefa-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dcefa-154">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="dcefa-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
