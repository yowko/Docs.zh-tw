---
title: 重大變更：當地語系化：已移除 ResourceManagerWithCultureStringLocalizer 類別和 WithCulture 介面成員
description: 瞭解 ASP.NET Core 5.0 的重大變更，其標題為當地語系化：已移除 ResourceManagerWithCultureStringLocalizer 類別和 WithCulture 介面成員
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: cba8458f20bad77ad6c125448f192939387ba405
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760756"
---
# <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a><span data-ttu-id="c3064-103">當地語系化：已移除 ResourceManagerWithCultureStringLocalizer 類別和 WithCulture 介面成員</span><span class="sxs-lookup"><span data-stu-id="c3064-103">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>

<span data-ttu-id="c3064-104">[ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)類別和[WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)方法已在 .net 5.0 Preview 1 中移除。</span><span class="sxs-lookup"><span data-stu-id="c3064-104">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were removed in .NET 5.0 Preview 1.</span></span>

<span data-ttu-id="c3064-105">如需相關內容，請參閱 [aspnet/公告 # 346](https://github.com/aspnet/Announcements/issues/346) 和 [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324)。</span><span class="sxs-lookup"><span data-stu-id="c3064-105">For context, see [aspnet/Announcements#346](https://github.com/aspnet/Announcements/issues/346) and [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="c3064-106">如需此變更的討論，請參閱 [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756)。</span><span class="sxs-lookup"><span data-stu-id="c3064-106">For discussion on this change, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c3064-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c3064-107">Version introduced</span></span>

<span data-ttu-id="c3064-108">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="c3064-108">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="c3064-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="c3064-109">Old behavior</span></span>

<span data-ttu-id="c3064-110">`ResourceManagerWithCultureStringLocalizer`類別和 `ResourceManagerStringLocalizer.WithCulture` 方法[在 .Net Core 3.0 Preview 3 和更新版本中已淘汰](../../../../core/compatibility/2.2-3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)。</span><span class="sxs-lookup"><span data-stu-id="c3064-110">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method are [obsolete in .NET Core 3.0 Preview 3 and later](../../../../core/compatibility/2.2-3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span></span>

## <a name="new-behavior"></a><span data-ttu-id="c3064-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="c3064-111">New behavior</span></span>

<span data-ttu-id="c3064-112">`ResourceManagerWithCultureStringLocalizer`類別和方法已 `ResourceManagerStringLocalizer.WithCulture` 在 .Net 5.0 Preview 1 中移除。</span><span class="sxs-lookup"><span data-stu-id="c3064-112">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method have been removed in .NET 5.0 Preview 1.</span></span> <span data-ttu-id="c3064-113">如需進行變更的清查，請參閱 [dotnet/extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files)的提取要求。</span><span class="sxs-lookup"><span data-stu-id="c3064-113">For an inventory of the changes made, see the pull request at [dotnet/extensions#2562](https://github.com/dotnet/extensions/pull/2562/files).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="c3064-114">變更的原因</span><span class="sxs-lookup"><span data-stu-id="c3064-114">Reason for change</span></span>

<span data-ttu-id="c3064-115">[ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)類別和[ResourceManagerStringLocalizer 的 WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)方法通常是當地語系化使用者的混淆來源。</span><span class="sxs-lookup"><span data-stu-id="c3064-115">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were often sources of confusion for users of localization.</span></span> <span data-ttu-id="c3064-116">建立自訂執行時，混淆特別高 <xref:Microsoft.Extensions.Localization.IStringLocalizer> 。</span><span class="sxs-lookup"><span data-stu-id="c3064-116">The confusion was especially high when creating a custom <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementation.</span></span> <span data-ttu-id="c3064-117">這個類別和方法可讓取用者認為 `IStringLocalizer` 實例應該是「每個語言、每個資源」的印象。</span><span class="sxs-lookup"><span data-stu-id="c3064-117">This class and method give consumers the impression that an `IStringLocalizer` instance is expected to be "per-language, per-resource".</span></span> <span data-ttu-id="c3064-118">實際上，實例應該只是「每個資源」。</span><span class="sxs-lookup"><span data-stu-id="c3064-118">In reality, the instance should only be "per-resource".</span></span> <span data-ttu-id="c3064-119">在執行時間， <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 屬性會決定要使用的語言。</span><span class="sxs-lookup"><span data-stu-id="c3064-119">At run time, the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> property determines the language to be used.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c3064-120">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c3064-120">Recommended action</span></span>

<span data-ttu-id="c3064-121">停止使用 `ResourceManagerWithCultureStringLocalizer` 類別和 `ResourceManagerStringLocalizer.WithCulture` 方法。</span><span class="sxs-lookup"><span data-stu-id="c3064-121">Stop using the `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c3064-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c3064-122">Affected APIs</span></span>

- [<span data-ttu-id="c3064-123">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="c3064-123">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [<span data-ttu-id="c3064-124">ResourceManagerStringLocalizer.WithCulture</span><span class="sxs-lookup"><span data-stu-id="c3064-124">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
