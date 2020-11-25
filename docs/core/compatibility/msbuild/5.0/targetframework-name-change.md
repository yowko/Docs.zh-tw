---
title: 重大變更： TargetFramework 從 netcoreapp 變更為 net
description: 瞭解在 .NET 5.0 中，MSBuild TargetFramework 屬性的值從 netcoreapp 3.1 變更為 NET 5.0 的重大變更。
ms.date: 10/17/2020
ms.openlocfilehash: c3b39a36548d58d6ed75fd8b1c84b0cccfc738f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760634"
---
# <a name="targetframework-change-from-netcoreapp-to-net"></a><span data-ttu-id="4c01a-103">TargetFramework 從 netcoreapp 變更為 net</span><span class="sxs-lookup"><span data-stu-id="4c01a-103">TargetFramework change from netcoreapp to net</span></span>

<span data-ttu-id="4c01a-104">MSBuild 屬性的值 `TargetFramework` 已從變更 `netcoreapp3.1` 為 `net5.0` 。</span><span class="sxs-lookup"><span data-stu-id="4c01a-104">The value for the MSBuild `TargetFramework` property changed from `netcoreapp3.1` to `net5.0`.</span></span> <span data-ttu-id="4c01a-105">這可能會中斷依賴剖析值的程式碼 `TargetFramework` 。</span><span class="sxs-lookup"><span data-stu-id="4c01a-105">This can break code that relies on parsing the value of `TargetFramework`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="4c01a-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="4c01a-106">Version introduced</span></span>

<span data-ttu-id="4c01a-107">5.0</span><span class="sxs-lookup"><span data-stu-id="4c01a-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="4c01a-108">變更描述</span><span class="sxs-lookup"><span data-stu-id="4c01a-108">Change description</span></span>

<span data-ttu-id="4c01a-109">在 .NET Core 1.0-3.1 中，MSBuild 屬性的值是以 `TargetFramework` `netcoreapp` `netcoreapp3.1` .net core 3.1 的應用程式為開頭，例如。</span><span class="sxs-lookup"><span data-stu-id="4c01a-109">In .NET Core 1.0 - 3.1, the value for the MSBuild `TargetFramework` property starts with `netcoreapp`, for example, `netcoreapp3.1` for apps that target .NET Core 3.1.</span></span> <span data-ttu-id="4c01a-110">從 .NET 5.0 開始，此值已簡化為只從 `net` .net 5.0 開始（例如） `net5.0` 。</span><span class="sxs-lookup"><span data-stu-id="4c01a-110">Starting in .NET 5.0, this value is simplified to just start with `net`, for example, `net5.0` for .NET 5.0.</span></span>

<span data-ttu-id="4c01a-111">如需詳細資訊，請參閱 .NET 5 的 .NET Standard 和[目標 framework 名稱](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md)[的未來](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/)。</span><span class="sxs-lookup"><span data-stu-id="4c01a-111">For more information, see [The future of .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) and [Target framework names in .NET 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="4c01a-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="4c01a-112">Reason for change</span></span>

- <span data-ttu-id="4c01a-113">簡化 `TargetFramework` 值。</span><span class="sxs-lookup"><span data-stu-id="4c01a-113">Simplifies the `TargetFramework` value.</span></span>
- <span data-ttu-id="4c01a-114">讓專案 `TargetPlatform` 在屬性中包含 `TargetFramework` 。</span><span class="sxs-lookup"><span data-stu-id="4c01a-114">Enables projects to include a `TargetPlatform` in the `TargetFramework` property.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4c01a-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="4c01a-115">Recommended action</span></span>

<span data-ttu-id="4c01a-116">如果您有剖析值的邏輯 `TargetFramework` ，您必須更新它。</span><span class="sxs-lookup"><span data-stu-id="4c01a-116">If you have logic that parses the value of `TargetFramework`, you'll need to update it.</span></span> <span data-ttu-id="4c01a-117">例如，下列 MSBuild 條件依賴的值 `TargetFramework` 。</span><span class="sxs-lookup"><span data-stu-id="4c01a-117">For example, the following MSBuild condition relies on the value of `TargetFramework`.</span></span>

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

<span data-ttu-id="4c01a-118">針對此需求，您可以更新程式碼來比較目標 framework 識別碼。</span><span class="sxs-lookup"><span data-stu-id="4c01a-118">For this requirement, you can update the code to compare the target framework identifier instead.</span></span>

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

## <a name="affected-apis"></a><span data-ttu-id="4c01a-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4c01a-119">Affected APIs</span></span>

<span data-ttu-id="4c01a-120">N/A</span><span class="sxs-lookup"><span data-stu-id="4c01a-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
