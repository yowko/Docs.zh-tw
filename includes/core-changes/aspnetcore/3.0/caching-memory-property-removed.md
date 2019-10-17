---
ms.openlocfilehash: 7d40324e6b0bc4afab9dd39b236f0909f360cc9b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394149"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="4c99c-101">Caching： CompactOnMemoryPressure 屬性已移除</span><span class="sxs-lookup"><span data-stu-id="4c99c-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="4c99c-102">ASP.NET Core 3.0 版本已移除[過時的 MemoryCacheOptions api](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18)。</span><span class="sxs-lookup"><span data-stu-id="4c99c-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="4c99c-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="4c99c-103">Change description</span></span>

<span data-ttu-id="4c99c-104">這是對[aspnet/Caching # 221](https://github.com/aspnet/Caching/issues/221)的後續變更。</span><span class="sxs-lookup"><span data-stu-id="4c99c-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="4c99c-105">如需討論，請參閱[aspnet/Extensions # 1062](https://github.com/aspnet/Extensions/issues/1062)。</span><span class="sxs-lookup"><span data-stu-id="4c99c-105">For discussion, see [aspnet/Extensions#1062](https://github.com/aspnet/Extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4c99c-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="4c99c-106">Version introduced</span></span>

<span data-ttu-id="4c99c-107">3.0</span><span class="sxs-lookup"><span data-stu-id="4c99c-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4c99c-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="4c99c-108">Old behavior</span></span>

<span data-ttu-id="4c99c-109">`MemoryCacheOptions.CompactOnMemoryPressure` 屬性可用。</span><span class="sxs-lookup"><span data-stu-id="4c99c-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4c99c-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="4c99c-110">New behavior</span></span>

<span data-ttu-id="4c99c-111">已移除 `MemoryCacheOptions.CompactOnMemoryPressure` 屬性。</span><span class="sxs-lookup"><span data-stu-id="4c99c-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4c99c-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="4c99c-112">Reason for change</span></span>

<span data-ttu-id="4c99c-113">自動壓縮快取會造成問題。</span><span class="sxs-lookup"><span data-stu-id="4c99c-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="4c99c-114">為避免非預期的行為，只有在需要時才壓縮快取。</span><span class="sxs-lookup"><span data-stu-id="4c99c-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4c99c-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="4c99c-115">Recommended action</span></span>

<span data-ttu-id="4c99c-116">若要壓縮快取，請向 `MemoryCache` 的向下轉換，並在需要時呼叫 `Compact`。</span><span class="sxs-lookup"><span data-stu-id="4c99c-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="4c99c-117">分類</span><span class="sxs-lookup"><span data-stu-id="4c99c-117">Category</span></span>

<span data-ttu-id="4c99c-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4c99c-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4c99c-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4c99c-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
