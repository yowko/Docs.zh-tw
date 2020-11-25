---
title: 重大變更：已重新命名或移除 OSPlatform 屬性
description: 瞭解核心 .NET 程式庫中已移除或重新命名已在預覽版本中引進之 OS 平臺屬性的 .NET 5.0 重大變更。
ms.date: 11/01/2020
ms.openlocfilehash: 7e709b84005a7b807e390e12d9f36d8b4f73a9df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760653"
---
# <a name="osplatform-attributes-renamed-or-removed"></a><span data-ttu-id="769fd-103">OSPlatform 屬性已重新命名或移除</span><span class="sxs-lookup"><span data-stu-id="769fd-103">OSPlatform attributes renamed or removed</span></span>

<span data-ttu-id="769fd-104">已移除或重新命名 .NET 5.0 Preview 8 中引進的下列屬性： `MinimumOSPlatformAttribute` 、 `RemovedInOSPlatformAttribute` 和 `ObsoletedInOSPlatformAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="769fd-104">The following attributes that were introduced in .NET 5.0 Preview 8 have been removed or renamed: `MinimumOSPlatformAttribute`, `RemovedInOSPlatformAttribute`, and `ObsoletedInOSPlatformAttribute`.</span></span>

## <a name="change-description"></a><span data-ttu-id="769fd-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="769fd-105">Change description</span></span>

<span data-ttu-id="769fd-106">.NET 5.0 Preview 8 在命名空間中引進了下列屬性 <xref:System.Runtime.Versioning> ：</span><span class="sxs-lookup"><span data-stu-id="769fd-106">.NET 5.0 Preview 8 introduced the following attributes in the <xref:System.Runtime.Versioning> namespace:</span></span>

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

<span data-ttu-id="769fd-107">在 .NET 5.0 Preview 8 中，當專案的目標為 .NET 5 的 OS 特定類別時，會使用 [目標 framework 標記](../../../../standard/frameworks.md) （例如 `net5.0-windows` ），而組建會加入元件層級的 `System.Runtime.Versioning.MinimumOSPlatformAttribute` 屬性。</span><span class="sxs-lookup"><span data-stu-id="769fd-107">In .NET 5.0 Preview 8, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level `System.Runtime.Versioning.MinimumOSPlatformAttribute` attribute.</span></span>

<span data-ttu-id="769fd-108">在 .NET 5.0 RC1 中，已移除，且已重新命名，如下所示 `ObsoletedInOSPlatformAttribute` `MinimumOSPlatformAttribute` `RemovedInOSPlatformAttribute` ：</span><span class="sxs-lookup"><span data-stu-id="769fd-108">In .NET 5.0 RC1, the `ObsoletedInOSPlatformAttribute` has been removed, and `MinimumOSPlatformAttribute` and `RemovedInOSPlatformAttribute` have been renamed as follows:</span></span>

| <span data-ttu-id="769fd-109">Preview 8 名稱</span><span class="sxs-lookup"><span data-stu-id="769fd-109">Preview 8 name</span></span> | <span data-ttu-id="769fd-110">RC1 和更新的名稱</span><span class="sxs-lookup"><span data-stu-id="769fd-110">RC1 and later name</span></span> |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

<span data-ttu-id="769fd-111">在 .NET 5.0 RC1 和更新版本中，當專案以 .NET 5 的 OS 特定類別為目標時，會使用 [目標 framework 的標記](../../../../standard/frameworks.md) （例如 `net5.0-windows` ），而組建會加入元件層級 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="769fd-111">In .NET 5.0 RC1 and later, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> attribute.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="769fd-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="769fd-112">Reason for change</span></span>

<span data-ttu-id="769fd-113">.NET 5.0 Preview 8 引進中的屬性 <xref:System.Runtime.Versioning> ，以指定 api 支援的平臺。</span><span class="sxs-lookup"><span data-stu-id="769fd-113">.NET 5.0 Preview 8 introduced attributes in <xref:System.Runtime.Versioning> to specify supported platforms for APIs.</span></span> <span data-ttu-id="769fd-114">當平臺特定 Api 在不支援這些 Api 的平臺上取用時， [平臺相容性分析器](../../../../core/compatibility/code-analysis.md#ca1416-platform-compatibility) 會使用這些屬性來產生組建警告。</span><span class="sxs-lookup"><span data-stu-id="769fd-114">The attributes are consumed by the [Platform compatibility analyzer](../../../../core/compatibility/code-analysis.md#ca1416-platform-compatibility) to produce build warnings when platform-specific APIs are consumed on platforms that don't supported those APIs.</span></span>

<span data-ttu-id="769fd-115">針對 .NET 5.0 RC1，平臺相容性分析器已新增其他功能來排除平臺。</span><span class="sxs-lookup"><span data-stu-id="769fd-115">For .NET 5.0 RC1, an additional feature was added to the platform compatibility analyzer for platform exclusion.</span></span> <span data-ttu-id="769fd-116">這項功能可讓 Api 在作業系統平臺上標示為完全不受支援。</span><span class="sxs-lookup"><span data-stu-id="769fd-116">The feature allows APIs to be marked as entirely unsupported on OS platforms.</span></span> <span data-ttu-id="769fd-117">這項功能會提示變更屬性，包括使用更適合的名稱。</span><span class="sxs-lookup"><span data-stu-id="769fd-117">That feature prompted changes to the attributes, including using more suitable names.</span></span> <span data-ttu-id="769fd-118">`ObsoletedInOSPlatformAttribute`已移除，因為不再需要它。</span><span class="sxs-lookup"><span data-stu-id="769fd-118">The `ObsoletedInOSPlatformAttribute` was removed because it was no longer needed.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="769fd-119">引進的版本</span><span class="sxs-lookup"><span data-stu-id="769fd-119">Version introduced</span></span>

<span data-ttu-id="769fd-120">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="769fd-120">5.0 RC1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="769fd-121">建議的動作</span><span class="sxs-lookup"><span data-stu-id="769fd-121">Recommended action</span></span>

<span data-ttu-id="769fd-122">當您將專案從 .NET 5.0 Preview 8 重定目標為 .NET 5.0 RC1 時，可能會因為這些變更而遇到組建或執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="769fd-122">When you retarget your project from .NET 5.0 Preview 8 to .NET 5.0 RC1, you might encounter build or run-time errors due to these changes.</span></span> <span data-ttu-id="769fd-123">例如，的重新命名 `MinimumOSPlatformAttribute` 可能會產生錯誤，因為屬性會在組建階段套用至平臺特定的元件，而舊的組建成品仍會參考舊的 API 名稱。</span><span class="sxs-lookup"><span data-stu-id="769fd-123">For example, the renaming of `MinimumOSPlatformAttribute` is likely to produce errors, because the attribute is applied to platform-specific assemblies at build time, and old build artifacts will still reference the old API name.</span></span>

<span data-ttu-id="769fd-124">組建時期錯誤範例：</span><span class="sxs-lookup"><span data-stu-id="769fd-124">Example build-time errors:</span></span>

- <span data-ttu-id="769fd-125">**錯誤 CS0246：找不到類型或命名空間名稱 ' MinimumOSPlatformAttribute ' (您是否遺漏 using 指示詞或元件參考？ )**</span><span class="sxs-lookup"><span data-stu-id="769fd-125">**error CS0246: The type or namespace name 'MinimumOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="769fd-126">**錯誤 CS0246：找不到類型或命名空間名稱 ' RemovedInOSPlatformAttribute ' (您是否遺漏 using 指示詞或元件參考？ )**</span><span class="sxs-lookup"><span data-stu-id="769fd-126">**error CS0246: The type or namespace name 'RemovedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="769fd-127">**錯誤 CS0246：找不到類型或命名空間名稱 ' ObsoletedInOSPlatformAttribute ' (您是否遺漏 using 指示詞或元件參考？ )**</span><span class="sxs-lookup"><span data-stu-id="769fd-127">**error CS0246: The type or namespace name 'ObsoletedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>

<span data-ttu-id="769fd-128">執行階段錯誤範例：</span><span class="sxs-lookup"><span data-stu-id="769fd-128">Example run-time error:</span></span>

<span data-ttu-id="769fd-129">**未處理的例外狀況。TypeLoadException：無法從元件 ' System. Runtime，Version = 5.0.0.0，Culture = 中性，PublicKeyToken = b03f5f7f11d50a3a ' 載入類型 ' MinimumOSPlatformAttribute '。**</span><span class="sxs-lookup"><span data-stu-id="769fd-129">**Unhandled exception. System.TypeLoadException: Could not load type 'System.Runtime.Versioning.MinimumOSPlatformAttribute' from assembly 'System.Runtime, Version=5.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'.**</span></span>

<span data-ttu-id="769fd-130">若要解決這些錯誤：</span><span class="sxs-lookup"><span data-stu-id="769fd-130">To resolve these errors:</span></span>

- <span data-ttu-id="769fd-131">將的任何參考更新 `MinimumOSPlatformAttribute` 為 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="769fd-131">Update any references of `MinimumOSPlatformAttribute` to <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="769fd-132">將的任何參考更新 `RemovedInOSPlatformAttribute` 為 <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="769fd-132">Update any references of `RemovedInOSPlatformAttribute` to <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="769fd-133">移除的任何參考 `ObsoletedInOSPlatformAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="769fd-133">Remove any references to `ObsoletedInOSPlatformAttribute`.</span></span>
- <span data-ttu-id="769fd-134">重建您的專案 (或執行 [清除 + 組建]) ，以刪除舊的組建成品。</span><span class="sxs-lookup"><span data-stu-id="769fd-134">Rebuild your project (or perform clean + build) to delete old build artifacts.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="769fd-135">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="769fd-135">Affected APIs</span></span>

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->
