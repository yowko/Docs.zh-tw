---
ms.openlocfilehash: d7a93cb539baee6a70f75d3afe52fd7546ac2399
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507069"
---
### <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a><span data-ttu-id="51714-101">擴充功能：套件參考變更會影響某些 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="51714-101">Extensions: Package reference changes affecting some NuGet packages</span></span>

<span data-ttu-id="51714-102">藉由將某些 `Microsoft.Extensions.*` NuGet 套件從 [dotnet/extensions](https://github.com/dotnet/extensions) 存放庫遷移至 [dotnet/運行](https://github.com/dotnet/runtime)時間（如 [aspnet/公告 # 411](https://github.com/aspnet/Announcements/issues/411)所述），封裝變更會套用至某些已遷移的封裝。</span><span class="sxs-lookup"><span data-stu-id="51714-102">With the migration of some `Microsoft.Extensions.*` NuGet packages from the [dotnet/extensions](https://github.com/dotnet/extensions) repository to [dotnet/runtime](https://github.com/dotnet/runtime), as described in [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), packaging changes are being applied to some of the migrated packages.</span></span> <span data-ttu-id="51714-103">如需此問題的討論，請參閱 [dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033)。</span><span class="sxs-lookup"><span data-stu-id="51714-103">For discussion on this issue, see [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="51714-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="51714-104">Version introduced</span></span>

<span data-ttu-id="51714-105">5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="51714-105">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="51714-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="51714-106">Old behavior</span></span>

<span data-ttu-id="51714-107">某些 `Microsoft.Extensions.*` 套件包含應用程式依賴之 api 的套件參考。</span><span class="sxs-lookup"><span data-stu-id="51714-107">Some `Microsoft.Extensions.*` packages included package references for APIs on which your app relied.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="51714-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="51714-108">New behavior</span></span>

<span data-ttu-id="51714-109">您的應用程式可能必須新增套件相依性 `Microsoft.Extensions.*` 。</span><span class="sxs-lookup"><span data-stu-id="51714-109">Your app may have to add `Microsoft.Extensions.*` package dependencies.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="51714-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="51714-110">Reason for change</span></span>

<span data-ttu-id="51714-111">封裝原則已更新，使其更符合 *dotnet/運行* 時間存放庫。</span><span class="sxs-lookup"><span data-stu-id="51714-111">Packaging policies were updated to better align with the *dotnet/runtime* repository.</span></span> <span data-ttu-id="51714-112">在新的原則下，未使用的封裝參考會在封裝期間從 *nupkg* 檔案中移除。</span><span class="sxs-lookup"><span data-stu-id="51714-112">Under the new policy, unused package references are removed from *.nupkg* files during packaging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="51714-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="51714-113">Recommended action</span></span>

<span data-ttu-id="51714-114">如果使用已移除套件相依性中的 Api，受影響套件的取用者應該在其專案中新增對已移除套件相依性的直接相依性。</span><span class="sxs-lookup"><span data-stu-id="51714-114">Consumers of the affected packages should add a direct dependency on the removed package dependency in their project if APIs from removed package dependency are used.</span></span> <span data-ttu-id="51714-115">下表列出受影響的封裝和對應的變更。</span><span class="sxs-lookup"><span data-stu-id="51714-115">The following table lists the affected packages and the corresponding changes.</span></span>

|<span data-ttu-id="51714-116">套件名稱</span><span class="sxs-lookup"><span data-stu-id="51714-116">Package name</span></span>|<span data-ttu-id="51714-117">變更描述</span><span class="sxs-lookup"><span data-stu-id="51714-117">Change description</span></span>|
|------------|------------------|
|[<span data-ttu-id="51714-118">Microsoft.Extensions.Configuration。粘結 劑</span><span class="sxs-lookup"><span data-stu-id="51714-118">Microsoft.Extensions.Configuration.Binder</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|<span data-ttu-id="51714-119">已移除參考 `Microsoft.Extensions.Configuration`</span><span class="sxs-lookup"><span data-stu-id="51714-119">Removed reference to `Microsoft.Extensions.Configuration`</span></span>|
|[<span data-ttu-id="51714-120">Microsoft.Extensions.Configuration.Js開啟</span><span class="sxs-lookup"><span data-stu-id="51714-120">Microsoft.Extensions.Configuration.Json</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |<span data-ttu-id="51714-121">已移除參考 `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="51714-121">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="51714-122">。抽象概念</span><span class="sxs-lookup"><span data-stu-id="51714-122">Microsoft.Extensions.Hosting.Abstractions</span></span>](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|<span data-ttu-id="51714-123">已移除參考 `Microsoft.Extensions.Logging.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="51714-123">Removed reference to `Microsoft.Extensions.Logging.Abstractions`</span></span>|
|[<span data-ttu-id="51714-124">Microsoft.Extensions.Logging</span><span class="sxs-lookup"><span data-stu-id="51714-124">Microsoft.Extensions.Logging</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |<span data-ttu-id="51714-125">已移除參考 `Microsoft.Extensions.Configuration.Binder`</span><span class="sxs-lookup"><span data-stu-id="51714-125">Removed reference to `Microsoft.Extensions.Configuration.Binder`</span></span>|
|<span data-ttu-id="51714-126">[[登入] 主控台](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)</span><span class="sxs-lookup"><span data-stu-id="51714-126">[Microsoft.Extensions.Logging.Console](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)</span></span>          |<span data-ttu-id="51714-127">已移除參考 `Microsoft.Extensions.Configuration.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="51714-127">Removed reference to `Microsoft.Extensions.Configuration.Abstractions`</span></span>|
|[<span data-ttu-id="51714-128">Microsoft 副檔名記錄檔。 EventLog</span><span class="sxs-lookup"><span data-stu-id="51714-128">Microsoft.Extensions.Logging.EventLog</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |<span data-ttu-id="51714-129">已移除 `System.Diagnostics.EventLog` .NET Framework 4.6.1 目標 Framework 標記的參考</span><span class="sxs-lookup"><span data-stu-id="51714-129">Removed reference to `System.Diagnostics.EventLog` for the .NET Framework 4.6.1 target framework moniker</span></span>|
|[<span data-ttu-id="51714-130">... 記錄檔 EventSource</span><span class="sxs-lookup"><span data-stu-id="51714-130">Microsoft.Extensions.Logging.EventSource</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |<span data-ttu-id="51714-131">已移除參考 `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="51714-131">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="51714-132">Microsoft. Extensions. 選項</span><span class="sxs-lookup"><span data-stu-id="51714-132">Microsoft.Extensions.Options</span></span>](https://nuget.org/packages/Microsoft.Extensions.Options)                          |<span data-ttu-id="51714-133">已移除參考 `System.ComponentModel.Annotations`</span><span class="sxs-lookup"><span data-stu-id="51714-133">Removed reference to `System.ComponentModel.Annotations`</span></span>|

<span data-ttu-id="51714-134">例如， `Microsoft.Extensions.Configuration` 已從移除的封裝參考 `Microsoft.Extensions.Configuration.Binder` 。</span><span class="sxs-lookup"><span data-stu-id="51714-134">For example, the package reference to `Microsoft.Extensions.Configuration` was removed from `Microsoft.Extensions.Configuration.Binder`.</span></span> <span data-ttu-id="51714-135">封裝中未使用相依性的 API。</span><span class="sxs-lookup"><span data-stu-id="51714-135">No API from the dependency was used in the package.</span></span> <span data-ttu-id="51714-136">相依于 `Microsoft.Extensions.Configuration.Binder` api 的使用者 `Microsoft.Extensions.Configuration` 應該在其專案中新增其直接參考。</span><span class="sxs-lookup"><span data-stu-id="51714-136">Users of `Microsoft.Extensions.Configuration.Binder` who depend on APIs from `Microsoft.Extensions.Configuration` should add a direct reference to it in their project.</span></span>

#### <a name="category"></a><span data-ttu-id="51714-137">類別</span><span class="sxs-lookup"><span data-stu-id="51714-137">Category</span></span>

<span data-ttu-id="51714-138">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="51714-138">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="51714-139">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="51714-139">Affected APIs</span></span>

<span data-ttu-id="51714-140">無</span><span class="sxs-lookup"><span data-stu-id="51714-140">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
