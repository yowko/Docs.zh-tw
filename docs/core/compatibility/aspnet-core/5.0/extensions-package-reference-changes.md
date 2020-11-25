---
title: 重大變更：延伸模組：套件參考變更會影響某些 NuGet 套件
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為延伸模組：影響某些 NuGet 套件的套件參考變更
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 4a525d9f7aad4409fd507fcf80c00968ff4b63d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760658"
---
# <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a><span data-ttu-id="23fd5-103">擴充功能：套件參考變更會影響某些 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="23fd5-103">Extensions: Package reference changes affecting some NuGet packages</span></span>

<span data-ttu-id="23fd5-104">藉由將某些 `Microsoft.Extensions.*` NuGet 套件從 [dotnet/extensions](https://github.com/dotnet/extensions) 存放庫遷移至 [dotnet/運行](https://github.com/dotnet/runtime)時間（如 [aspnet/公告 # 411](https://github.com/aspnet/Announcements/issues/411)所述），封裝變更會套用至某些已遷移的封裝。</span><span class="sxs-lookup"><span data-stu-id="23fd5-104">With the migration of some `Microsoft.Extensions.*` NuGet packages from the [dotnet/extensions](https://github.com/dotnet/extensions) repository to [dotnet/runtime](https://github.com/dotnet/runtime), as described in [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), packaging changes are being applied to some of the migrated packages.</span></span> <span data-ttu-id="23fd5-105">如需此問題的討論，請參閱 [dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033)。</span><span class="sxs-lookup"><span data-stu-id="23fd5-105">For discussion on this issue, see [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="23fd5-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="23fd5-106">Version introduced</span></span>

<span data-ttu-id="23fd5-107">5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="23fd5-107">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="23fd5-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="23fd5-108">Old behavior</span></span>

<span data-ttu-id="23fd5-109">某些 `Microsoft.Extensions.*` 套件包含應用程式依賴之 api 的套件參考。</span><span class="sxs-lookup"><span data-stu-id="23fd5-109">Some `Microsoft.Extensions.*` packages included package references for APIs on which your app relied.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="23fd5-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="23fd5-110">New behavior</span></span>

<span data-ttu-id="23fd5-111">您的應用程式可能必須新增套件相依性 `Microsoft.Extensions.*` 。</span><span class="sxs-lookup"><span data-stu-id="23fd5-111">Your app may have to add `Microsoft.Extensions.*` package dependencies.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="23fd5-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="23fd5-112">Reason for change</span></span>

<span data-ttu-id="23fd5-113">封裝原則已更新，使其更符合 *dotnet/運行* 時間存放庫。</span><span class="sxs-lookup"><span data-stu-id="23fd5-113">Packaging policies were updated to better align with the *dotnet/runtime* repository.</span></span> <span data-ttu-id="23fd5-114">在新的原則下，未使用的封裝參考會在封裝期間從 *nupkg* 檔案中移除。</span><span class="sxs-lookup"><span data-stu-id="23fd5-114">Under the new policy, unused package references are removed from *.nupkg* files during packaging.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="23fd5-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="23fd5-115">Recommended action</span></span>

<span data-ttu-id="23fd5-116">如果使用已移除套件相依性中的 Api，受影響套件的取用者應該在其專案中新增對已移除套件相依性的直接相依性。</span><span class="sxs-lookup"><span data-stu-id="23fd5-116">Consumers of the affected packages should add a direct dependency on the removed package dependency in their project if APIs from removed package dependency are used.</span></span> <span data-ttu-id="23fd5-117">下表列出受影響的封裝和對應的變更。</span><span class="sxs-lookup"><span data-stu-id="23fd5-117">The following table lists the affected packages and the corresponding changes.</span></span>

|<span data-ttu-id="23fd5-118">套件名稱</span><span class="sxs-lookup"><span data-stu-id="23fd5-118">Package name</span></span>|<span data-ttu-id="23fd5-119">變更描述</span><span class="sxs-lookup"><span data-stu-id="23fd5-119">Change description</span></span>|
|------------|------------------|
|[<span data-ttu-id="23fd5-120">Microsoft.Extensions.Configuration。粘結 劑</span><span class="sxs-lookup"><span data-stu-id="23fd5-120">Microsoft.Extensions.Configuration.Binder</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|<span data-ttu-id="23fd5-121">已移除參考 `Microsoft.Extensions.Configuration`</span><span class="sxs-lookup"><span data-stu-id="23fd5-121">Removed reference to `Microsoft.Extensions.Configuration`</span></span>|
|[<span data-ttu-id="23fd5-122">Microsoft.Extensions.Configuration.Js開啟</span><span class="sxs-lookup"><span data-stu-id="23fd5-122">Microsoft.Extensions.Configuration.Json</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |<span data-ttu-id="23fd5-123">已移除參考 `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="23fd5-123">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="23fd5-124">。抽象概念</span><span class="sxs-lookup"><span data-stu-id="23fd5-124">Microsoft.Extensions.Hosting.Abstractions</span></span>](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|<span data-ttu-id="23fd5-125">已移除參考 `Microsoft.Extensions.Logging.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="23fd5-125">Removed reference to `Microsoft.Extensions.Logging.Abstractions`</span></span>|
|[<span data-ttu-id="23fd5-126">Microsoft.Extensions.Logging</span><span class="sxs-lookup"><span data-stu-id="23fd5-126">Microsoft.Extensions.Logging</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |<span data-ttu-id="23fd5-127">已移除參考 `Microsoft.Extensions.Configuration.Binder`</span><span class="sxs-lookup"><span data-stu-id="23fd5-127">Removed reference to `Microsoft.Extensions.Configuration.Binder`</span></span>|
|<span data-ttu-id="23fd5-128">[[登入] 主控台](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)</span><span class="sxs-lookup"><span data-stu-id="23fd5-128">[Microsoft.Extensions.Logging.Console](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)</span></span>          |<span data-ttu-id="23fd5-129">已移除參考 `Microsoft.Extensions.Configuration.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="23fd5-129">Removed reference to `Microsoft.Extensions.Configuration.Abstractions`</span></span>|
|[<span data-ttu-id="23fd5-130">Microsoft 副檔名記錄檔。 EventLog</span><span class="sxs-lookup"><span data-stu-id="23fd5-130">Microsoft.Extensions.Logging.EventLog</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |<span data-ttu-id="23fd5-131">已移除 `System.Diagnostics.EventLog` .NET Framework 4.6.1 目標 Framework 標記的參考</span><span class="sxs-lookup"><span data-stu-id="23fd5-131">Removed reference to `System.Diagnostics.EventLog` for the .NET Framework 4.6.1 target framework moniker</span></span>|
|[<span data-ttu-id="23fd5-132">... 記錄檔 EventSource</span><span class="sxs-lookup"><span data-stu-id="23fd5-132">Microsoft.Extensions.Logging.EventSource</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |<span data-ttu-id="23fd5-133">已移除參考 `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="23fd5-133">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="23fd5-134">Microsoft. Extensions. 選項</span><span class="sxs-lookup"><span data-stu-id="23fd5-134">Microsoft.Extensions.Options</span></span>](https://nuget.org/packages/Microsoft.Extensions.Options)                          |<span data-ttu-id="23fd5-135">已移除參考 `System.ComponentModel.Annotations`</span><span class="sxs-lookup"><span data-stu-id="23fd5-135">Removed reference to `System.ComponentModel.Annotations`</span></span>|

<span data-ttu-id="23fd5-136">例如， `Microsoft.Extensions.Configuration` 已從移除的封裝參考 `Microsoft.Extensions.Configuration.Binder` 。</span><span class="sxs-lookup"><span data-stu-id="23fd5-136">For example, the package reference to `Microsoft.Extensions.Configuration` was removed from `Microsoft.Extensions.Configuration.Binder`.</span></span> <span data-ttu-id="23fd5-137">封裝中未使用相依性的 API。</span><span class="sxs-lookup"><span data-stu-id="23fd5-137">No API from the dependency was used in the package.</span></span> <span data-ttu-id="23fd5-138">相依于 `Microsoft.Extensions.Configuration.Binder` api 的使用者 `Microsoft.Extensions.Configuration` 應該在其專案中新增其直接參考。</span><span class="sxs-lookup"><span data-stu-id="23fd5-138">Users of `Microsoft.Extensions.Configuration.Binder` who depend on APIs from `Microsoft.Extensions.Configuration` should add a direct reference to it in their project.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="23fd5-139">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="23fd5-139">Affected APIs</span></span>

<span data-ttu-id="23fd5-140">None</span><span class="sxs-lookup"><span data-stu-id="23fd5-140">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
