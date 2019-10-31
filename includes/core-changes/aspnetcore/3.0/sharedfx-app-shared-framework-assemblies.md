---
ms.openlocfilehash: 8344fdedcff34f102b73f977b688abc15563bd4c
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198387"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="e30f0-101">共用架構：從 AspNetCore 移除的元件</span><span class="sxs-lookup"><span data-stu-id="e30f0-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="e30f0-102">從 ASP.NET Core 3.0 開始，ASP.NET Core 共用架構（`Microsoft.AspNetCore.App`）僅包含由 Microsoft 完全開發、支援及維護的第一方元件。</span><span class="sxs-lookup"><span data-stu-id="e30f0-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e30f0-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="e30f0-103">Change description</span></span>

<span data-ttu-id="e30f0-104">請將變更視為 ASP.NET Core 「平臺」的界限重新定義。</span><span class="sxs-lookup"><span data-stu-id="e30f0-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="e30f0-105">共用架構會[由任何人透過 GitHub 可建置](https://github.com/dotnet/source-build)，並會繼續為您的應用程式提供 .net Core 共用架構的現有優點。</span><span class="sxs-lookup"><span data-stu-id="e30f0-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="e30f0-106">其中一些優點包括較小的部署大小、集中式修補，以及更快速的啟動時間。</span><span class="sxs-lookup"><span data-stu-id="e30f0-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="e30f0-107">在變更過程中，`Microsoft.AspNetCore.App` 會引進一些值得注意的重大變更。</span><span class="sxs-lookup"><span data-stu-id="e30f0-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e30f0-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e30f0-108">Version introduced</span></span>

<span data-ttu-id="e30f0-109">3.0</span><span class="sxs-lookup"><span data-stu-id="e30f0-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e30f0-110">舊的行為</span><span class="sxs-lookup"><span data-stu-id="e30f0-110">Old behavior</span></span>

<span data-ttu-id="e30f0-111">專案會透過專案檔中的 `<PackageReference>` 元素 `Microsoft.AspNetCore.App` 參考。</span><span class="sxs-lookup"><span data-stu-id="e30f0-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="e30f0-112">此外，`Microsoft.AspNetCore.App` 包含下列子元件：</span><span class="sxs-lookup"><span data-stu-id="e30f0-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="e30f0-113">Json.NET （`Newtonsoft.Json`）</span><span class="sxs-lookup"><span data-stu-id="e30f0-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="e30f0-114">Entity Framework Core （前面加上 `Microsoft.EntityFrameworkCore.` 的元件）</span><span class="sxs-lookup"><span data-stu-id="e30f0-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="e30f0-115">Roslyn （`Microsoft.CodeAnalysis`）</span><span class="sxs-lookup"><span data-stu-id="e30f0-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e30f0-116">新的行為</span><span class="sxs-lookup"><span data-stu-id="e30f0-116">New behavior</span></span>

<span data-ttu-id="e30f0-117">`Microsoft.AspNetCore.App` 的參考不再需要專案檔中的 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="e30f0-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="e30f0-118">.NET Core SDK 支援稱為 `<FrameworkReference>` 的新專案，這會取代 `<PackageReference>` 的用法。</span><span class="sxs-lookup"><span data-stu-id="e30f0-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="e30f0-119">如需詳細資訊，請參閱[aspnet/AspNetCore # 3612](https://github.com/aspnet/AspNetCore/issues/3612)。</span><span class="sxs-lookup"><span data-stu-id="e30f0-119">For more information, see [aspnet/AspNetCore#3612](https://github.com/aspnet/AspNetCore/issues/3612).</span></span>

<span data-ttu-id="e30f0-120">Entity Framework Core 隨附為 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="e30f0-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="e30f0-121">這種變更會將出貨模型與 .NET 上的所有其他資料存取程式庫對齊。</span><span class="sxs-lookup"><span data-stu-id="e30f0-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="e30f0-122">它提供 Entity Framework Core 最簡單的途徑來繼續進行創新，同時支援各種不同的 .NET 平臺。</span><span class="sxs-lookup"><span data-stu-id="e30f0-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="e30f0-123">從共用架構移出 Entity Framework Core 不會影響其狀態，因為它是 Microsoft 開發、支援及可維護的程式庫。</span><span class="sxs-lookup"><span data-stu-id="e30f0-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="e30f0-124">[.Net Core 支援原則](https://www.microsoft.com/net/platform/support-policy)會繼續加以涵蓋。</span><span class="sxs-lookup"><span data-stu-id="e30f0-124">The [.NET Core support policy](https://www.microsoft.com/net/platform/support-policy) continues to cover it.</span></span>

<span data-ttu-id="e30f0-125">Json.NET 和 Entity Framework Core 會繼續與 ASP.NET Core 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="e30f0-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="e30f0-126">不過，它們不會包含在共用架構中。</span><span class="sxs-lookup"><span data-stu-id="e30f0-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="e30f0-127">如需詳細資訊，請參閱[.Net Core 3.0 中的 JSON 未來](https://github.com/dotnet/announcements/issues/90)。</span><span class="sxs-lookup"><span data-stu-id="e30f0-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="e30f0-128">另請參閱已從共用架構移除的[完整二進位檔清單](https://github.com/aspnet/AspNetCore/issues/3755)。</span><span class="sxs-lookup"><span data-stu-id="e30f0-128">Also see [the complete list of binaries](https://github.com/aspnet/AspNetCore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e30f0-129">變更的原因</span><span class="sxs-lookup"><span data-stu-id="e30f0-129">Reason for change</span></span>

<span data-ttu-id="e30f0-130">這項變更可簡化 `Microsoft.AspNetCore.App` 的耗用量，並減少 NuGet 套件和共用架構之間的重複。</span><span class="sxs-lookup"><span data-stu-id="e30f0-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="e30f0-131">如需這種變更動機的詳細資訊，請參閱[這篇 blog 文章](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0)。</span><span class="sxs-lookup"><span data-stu-id="e30f0-131">For more information on the motivation for this change, see [this blog post](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e30f0-132">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e30f0-132">Recommended action</span></span>

<span data-ttu-id="e30f0-133">專案不需要使用 `Microsoft.AspNetCore.App` 中的元件做為 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="e30f0-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="e30f0-134">為了簡化 ASP.NET Core 共用架構的目標和使用，已不再產生許多自 ASP.NET Core 1.0 所隨附的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="e30f0-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="e30f0-135">這些套件提供的 Api 仍然可供應用程式使用，`<FrameworkReference>` 到 `Microsoft.AspNetCore.App`。</span><span class="sxs-lookup"><span data-stu-id="e30f0-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="e30f0-136">常見的 API 範例包括 Kestrel、MVC 和 Razor。</span><span class="sxs-lookup"><span data-stu-id="e30f0-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="e30f0-137">這項變更不適用於透過 ASP.NET Core 2.x 中的 `Microsoft.AspNetCore.App` 所參考的所有二進位檔。</span><span class="sxs-lookup"><span data-stu-id="e30f0-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="e30f0-138">值得注意的例外狀況包括：</span><span class="sxs-lookup"><span data-stu-id="e30f0-138">Notable exceptions include:</span></span>

- <span data-ttu-id="e30f0-139">繼續以 .NET Standard 為目標的 `Microsoft.Extensions` 程式庫會以 NuGet 套件的形式提供（請參閱 https://github.com/aspnet/Extensions) 。</span><span class="sxs-lookup"><span data-stu-id="e30f0-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see https://github.com/aspnet/Extensions).</span></span>
- <span data-ttu-id="e30f0-140">不屬於 `Microsoft.AspNetCore.App` 的 ASP.NET Core 小組所產生的 Api。</span><span class="sxs-lookup"><span data-stu-id="e30f0-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="e30f0-141">例如，下列元件會以 NuGet 套件的形式提供：</span><span class="sxs-lookup"><span data-stu-id="e30f0-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="e30f0-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="e30f0-142">Entity Framework Core</span></span>
  - <span data-ttu-id="e30f0-143">提供協力廠商整合的 Api</span><span class="sxs-lookup"><span data-stu-id="e30f0-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="e30f0-144">實驗性功能</span><span class="sxs-lookup"><span data-stu-id="e30f0-144">Experimental features</span></span>
  - <span data-ttu-id="e30f0-145">相依性無法[滿足共用架構中的需求](https://github.com/aspnet/AspNetCore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)的 api</span><span class="sxs-lookup"><span data-stu-id="e30f0-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/aspnet/AspNetCore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="e30f0-146">維護 Json.NET 支援的 MVC 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e30f0-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="e30f0-147">API 會以 NuGet 套件形式提供，以支援使用 Json.NET 和 MVC。</span><span class="sxs-lookup"><span data-stu-id="e30f0-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="e30f0-148">SignalR .NET 用戶端將繼續支援 .NET Standard 並以 NuGet 套件形式出貨。</span><span class="sxs-lookup"><span data-stu-id="e30f0-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="e30f0-149">其目的是要用於許多 .NET 執行時間，例如 Xamarin 和 UWP。</span><span class="sxs-lookup"><span data-stu-id="e30f0-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="e30f0-150">如需詳細資訊，請參閱[在3.0 中停止產生共用架構元件的封裝](https://github.com/aspnet/AspNetCore/issues/3756)。</span><span class="sxs-lookup"><span data-stu-id="e30f0-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/aspnet/AspNetCore/issues/3756).</span></span> <span data-ttu-id="e30f0-151">如需討論，請參閱[aspnet/AspNetCore # 3757](https://github.com/aspnet/AspNetCore/issues/3757)。</span><span class="sxs-lookup"><span data-stu-id="e30f0-151">For discussion, see [aspnet/AspNetCore#3757](https://github.com/aspnet/AspNetCore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="e30f0-152">Category</span><span class="sxs-lookup"><span data-stu-id="e30f0-152">Category</span></span>

<span data-ttu-id="e30f0-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e30f0-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e30f0-154">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e30f0-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
