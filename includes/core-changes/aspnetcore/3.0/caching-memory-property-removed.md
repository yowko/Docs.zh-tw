---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032336"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="62f4f-101">快取：已移除 CompactOnMemoryPressure 屬性</span><span class="sxs-lookup"><span data-stu-id="62f4f-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="62f4f-102">ASP.NET Core 3.0 版移除淘汰的 [MemoryCacheOptions api](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18)。</span><span class="sxs-lookup"><span data-stu-id="62f4f-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="62f4f-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="62f4f-103">Change description</span></span>

<span data-ttu-id="62f4f-104">這項變更是 [aspnet/Caching # 221](https://github.com/aspnet/Caching/issues/221)的後續變更。</span><span class="sxs-lookup"><span data-stu-id="62f4f-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="62f4f-105">如需討論，請參閱 [dotnet/extensions # 1062](https://github.com/dotnet/extensions/issues/1062)。</span><span class="sxs-lookup"><span data-stu-id="62f4f-105">For discussion, see [dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="62f4f-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="62f4f-106">Version introduced</span></span>

<span data-ttu-id="62f4f-107">3.0</span><span class="sxs-lookup"><span data-stu-id="62f4f-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="62f4f-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="62f4f-108">Old behavior</span></span>

<span data-ttu-id="62f4f-109">`MemoryCacheOptions.CompactOnMemoryPressure` 屬性可用。</span><span class="sxs-lookup"><span data-stu-id="62f4f-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="62f4f-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="62f4f-110">New behavior</span></span>

<span data-ttu-id="62f4f-111">已 `MemoryCacheOptions.CompactOnMemoryPressure` 移除屬性。</span><span class="sxs-lookup"><span data-stu-id="62f4f-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="62f4f-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="62f4f-112">Reason for change</span></span>

<span data-ttu-id="62f4f-113">自動壓縮快取造成問題。</span><span class="sxs-lookup"><span data-stu-id="62f4f-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="62f4f-114">為了避免非預期的行為，應該只在需要時壓縮快取。</span><span class="sxs-lookup"><span data-stu-id="62f4f-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="62f4f-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="62f4f-115">Recommended action</span></span>

<span data-ttu-id="62f4f-116">若要壓縮快取，請 `MemoryCache` 在需要時向下轉換並呼叫 `Compact` 。</span><span class="sxs-lookup"><span data-stu-id="62f4f-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="62f4f-117">類別</span><span class="sxs-lookup"><span data-stu-id="62f4f-117">Category</span></span>

<span data-ttu-id="62f4f-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="62f4f-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="62f4f-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="62f4f-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
