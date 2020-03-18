---
ms.openlocfilehash: a8146db1fb54d63d4716b879ce793f7d817cef59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937263"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="da1dd-101">共用框架：從 Microsoft 中刪除程式集. AspNetCore.App</span><span class="sxs-lookup"><span data-stu-id="da1dd-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="da1dd-102">從 ASP.NET Core 3.0 開始，ASP.NET核心`Microsoft.AspNetCore.App`共用框架 （ ） 僅包含由 Microsoft 完全開發、支援並可維修的第一方程式集。</span><span class="sxs-lookup"><span data-stu-id="da1dd-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="da1dd-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="da1dd-103">Change description</span></span>

<span data-ttu-id="da1dd-104">將更改視為重新定義ASP.NET核心"平臺"的邊界。</span><span class="sxs-lookup"><span data-stu-id="da1dd-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="da1dd-105">共用框架將由[任何人通過 GitHub 進行原始程式碼構建](https://github.com/dotnet/source-build)，並將繼續為您的應用提供 .NET Core 共用框架的現有優勢。</span><span class="sxs-lookup"><span data-stu-id="da1dd-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="da1dd-106">一些優勢包括較小的部署大小、集中式修補和更快的啟動時間。</span><span class="sxs-lookup"><span data-stu-id="da1dd-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="da1dd-107">作為變革的一部分，在 中`Microsoft.AspNetCore.App`引入了一些顯著的重大重大變革。</span><span class="sxs-lookup"><span data-stu-id="da1dd-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="da1dd-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="da1dd-108">Version introduced</span></span>

<span data-ttu-id="da1dd-109">3.0</span><span class="sxs-lookup"><span data-stu-id="da1dd-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="da1dd-110">舊的行為</span><span class="sxs-lookup"><span data-stu-id="da1dd-110">Old behavior</span></span>

<span data-ttu-id="da1dd-111">通過專案`Microsoft.AspNetCore.App`檔中`<PackageReference>`的元素引用的專案。</span><span class="sxs-lookup"><span data-stu-id="da1dd-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="da1dd-112">此外，`Microsoft.AspNetCore.App`包含以下子元件：</span><span class="sxs-lookup"><span data-stu-id="da1dd-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="da1dd-113">Json.NET`Newtonsoft.Json`（ ）</span><span class="sxs-lookup"><span data-stu-id="da1dd-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="da1dd-114">實體框架核心（與`Microsoft.EntityFrameworkCore.`的預綴程式集。</span><span class="sxs-lookup"><span data-stu-id="da1dd-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="da1dd-115">羅斯林`Microsoft.CodeAnalysis`（ ）</span><span class="sxs-lookup"><span data-stu-id="da1dd-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="da1dd-116">新的行為</span><span class="sxs-lookup"><span data-stu-id="da1dd-116">New behavior</span></span>

<span data-ttu-id="da1dd-117">對`Microsoft.AspNetCore.App`不再需要專案檔案中的元素`<PackageReference>`的引用。</span><span class="sxs-lookup"><span data-stu-id="da1dd-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="da1dd-118">.NET 核心 SDK 支援一個名為`<FrameworkReference>`的新元素，它取代了`<PackageReference>`的使用。</span><span class="sxs-lookup"><span data-stu-id="da1dd-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="da1dd-119">有關詳細資訊，請參閱[點網/阿斯平核心#3612](https://github.com/dotnet/aspnetcore/issues/3612)。</span><span class="sxs-lookup"><span data-stu-id="da1dd-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="da1dd-120">實體框架核心作為 NuGet 包提供。</span><span class="sxs-lookup"><span data-stu-id="da1dd-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="da1dd-121">此更改使發貨模型與 .NET 上的所有其他資料訪問庫對齊。</span><span class="sxs-lookup"><span data-stu-id="da1dd-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="da1dd-122">它為實體框架核心提供了最簡單的路徑，以繼續創新，同時支援各種 .NET 平臺。</span><span class="sxs-lookup"><span data-stu-id="da1dd-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="da1dd-123">實體框架核心從共用框架中移出不會影響其作為 Microsoft 開發、支援和服務庫的狀態。</span><span class="sxs-lookup"><span data-stu-id="da1dd-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="da1dd-124">[.NET 核心支援策略](https://www.microsoft.com/net/platform/support-policy)繼續涵蓋它。</span><span class="sxs-lookup"><span data-stu-id="da1dd-124">The [.NET Core support policy](https://www.microsoft.com/net/platform/support-policy) continues to cover it.</span></span>

<span data-ttu-id="da1dd-125">Json.NET和實體框架核心繼續與ASP.NET核心合作。</span><span class="sxs-lookup"><span data-stu-id="da1dd-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="da1dd-126">但是，它們不會包含在共用框架中。</span><span class="sxs-lookup"><span data-stu-id="da1dd-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="da1dd-127">有關詳細資訊，請參閱[.NET 核心 3.0 中的 JSON 的未來](https://github.com/dotnet/announcements/issues/90)。</span><span class="sxs-lookup"><span data-stu-id="da1dd-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="da1dd-128">另請參閱從共用框架中刪除[的二進位檔案的完整清單](https://github.com/dotnet/aspnetcore/issues/3755)。</span><span class="sxs-lookup"><span data-stu-id="da1dd-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="da1dd-129">更改原因</span><span class="sxs-lookup"><span data-stu-id="da1dd-129">Reason for change</span></span>

<span data-ttu-id="da1dd-130">此更改簡化了 NuGet`Microsoft.AspNetCore.App`包和共用框架之間的使用並減少了重複。</span><span class="sxs-lookup"><span data-stu-id="da1dd-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="da1dd-131">有關此更改的動機的詳細資訊，請參閱[此博客文章](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)。</span><span class="sxs-lookup"><span data-stu-id="da1dd-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="da1dd-132">建議的動作</span><span class="sxs-lookup"><span data-stu-id="da1dd-132">Recommended action</span></span>

<span data-ttu-id="da1dd-133">專案無需`Microsoft.AspNetCore.App`將程式集用作 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="da1dd-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="da1dd-134">為了簡化ASP.NET核心共用框架的定位和使用，不再生產自ASP.NET Core 1.0 以來發貨的許多 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="da1dd-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="da1dd-135">這些包提供的 API 仍可用於應用使用`<FrameworkReference>`。 `Microsoft.AspNetCore.App`</span><span class="sxs-lookup"><span data-stu-id="da1dd-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="da1dd-136">常見的 API 示例包括 Kestrel、MVC 和 Razor。</span><span class="sxs-lookup"><span data-stu-id="da1dd-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="da1dd-137">此更改不適用於通過`Microsoft.AspNetCore.App`ASP.NET Core 2.x 中引用的所有二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="da1dd-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="da1dd-138">值得注意的例外包括：</span><span class="sxs-lookup"><span data-stu-id="da1dd-138">Notable exceptions include:</span></span>

- <span data-ttu-id="da1dd-139">`Microsoft.Extensions`繼續以 .NET 標準為目標的庫將作為 NuGet 包提供（https://github.com/dotnet/extensions)請參閱 ）。</span><span class="sxs-lookup"><span data-stu-id="da1dd-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see https://github.com/dotnet/extensions).</span></span>
- <span data-ttu-id="da1dd-140">由不屬於 的ASP.NET核心團隊生成的`Microsoft.AspNetCore.App`API。</span><span class="sxs-lookup"><span data-stu-id="da1dd-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="da1dd-141">例如，以下元件可作為 NuGet 包提供：</span><span class="sxs-lookup"><span data-stu-id="da1dd-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="da1dd-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="da1dd-142">Entity Framework Core</span></span>
  - <span data-ttu-id="da1dd-143">提供協力廠商集成的 API</span><span class="sxs-lookup"><span data-stu-id="da1dd-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="da1dd-144">實驗性功能</span><span class="sxs-lookup"><span data-stu-id="da1dd-144">Experimental features</span></span>
  - <span data-ttu-id="da1dd-145">具有無法滿足[共用框架中要求](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)的依賴項的 API</span><span class="sxs-lookup"><span data-stu-id="da1dd-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="da1dd-146">MVC 的擴展，用於維護對Json.NET的支援。</span><span class="sxs-lookup"><span data-stu-id="da1dd-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="da1dd-147">API 將作為 NuGet 包提供，以支援使用Json.NET和 MVC。</span><span class="sxs-lookup"><span data-stu-id="da1dd-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="da1dd-148">SignalR .NET 用戶端將繼續支援 .NET 標準，並作為 NuGet 包發貨。</span><span class="sxs-lookup"><span data-stu-id="da1dd-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="da1dd-149">它適用于許多 .NET 運行時，如 Xamarin 和 UWP。</span><span class="sxs-lookup"><span data-stu-id="da1dd-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="da1dd-150">有關詳細資訊，請參閱[停止在 3.0 中為共用框架程式集生成包](https://github.com/dotnet/aspnetcore/issues/3756)。</span><span class="sxs-lookup"><span data-stu-id="da1dd-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="da1dd-151">有關討論，請參閱[點網/阿斯平核心#3757](https://github.com/dotnet/aspnetcore/issues/3757)。</span><span class="sxs-lookup"><span data-stu-id="da1dd-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="da1dd-152">類別</span><span class="sxs-lookup"><span data-stu-id="da1dd-152">Category</span></span>

<span data-ttu-id="da1dd-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="da1dd-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da1dd-154">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="da1dd-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
