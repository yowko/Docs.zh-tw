---
ms.openlocfilehash: ae5a5fbf97ed4a03de7d35b9d5d5ca8de3aebc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394343"
---
### <a name="caching-responsecaching-pubternal-types-changed-to-internal"></a><span data-ttu-id="38185-101">緩存：回應緩存"公共"類型更改為內部</span><span class="sxs-lookup"><span data-stu-id="38185-101">Caching: ResponseCaching "pubternal" types changed to internal</span></span>

<span data-ttu-id="38185-102">在 ASP.NET Core 3.0 中`ResponseCaching`，"pubenal"類型已更改`internal`為 。</span><span class="sxs-lookup"><span data-stu-id="38185-102">In ASP.NET Core 3.0, "pubternal" types in `ResponseCaching` have been changed to `internal`.</span></span>

<span data-ttu-id="38185-103">此外，作為方法的一部分`IResponseCachingPolicyProvider`，`IResponseCachingKeyProvider`和 的預設實現不再添加到服務中`AddResponseCaching`。</span><span class="sxs-lookup"><span data-stu-id="38185-103">In addition, default implementations of `IResponseCachingPolicyProvider` and `IResponseCachingKeyProvider` are no longer added to services as part of the `AddResponseCaching` method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="38185-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="38185-104">Change description</span></span>

<span data-ttu-id="38185-105">在 ASP.NET 核心中，"pubenal"型別宣告`public`為，但駐留在尾碼與`.Internal`的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="38185-105">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a namespace suffixed with `.Internal`.</span></span> <span data-ttu-id="38185-106">雖然這些類型的是公共的，但它們沒有支援策略，並且可能會進行重大更改。</span><span class="sxs-lookup"><span data-stu-id="38185-106">While these types are public, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="38185-107">遺憾的是，意外使用這些類型很常見，導致這些專案的更改中斷，並限制了維護框架的能力。</span><span class="sxs-lookup"><span data-stu-id="38185-107">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="38185-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="38185-108">Version introduced</span></span>

<span data-ttu-id="38185-109">3.0</span><span class="sxs-lookup"><span data-stu-id="38185-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="38185-110">舊的行為</span><span class="sxs-lookup"><span data-stu-id="38185-110">Old behavior</span></span>

<span data-ttu-id="38185-111">這些類型是公開可見的，但不受支援。</span><span class="sxs-lookup"><span data-stu-id="38185-111">These types were publicly visible, but unsupported.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="38185-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="38185-112">New behavior</span></span>

<span data-ttu-id="38185-113">這些類型現在是`internal`。</span><span class="sxs-lookup"><span data-stu-id="38185-113">These types are now `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="38185-114">更改原因</span><span class="sxs-lookup"><span data-stu-id="38185-114">Reason for change</span></span>

<span data-ttu-id="38185-115">範圍`internal`更好地反映了不支援的策略。</span><span class="sxs-lookup"><span data-stu-id="38185-115">The `internal` scope better reflects the unsupported policy.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="38185-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="38185-116">Recommended action</span></span>

<span data-ttu-id="38185-117">複製應用或庫使用的類型。</span><span class="sxs-lookup"><span data-stu-id="38185-117">Copy types that are used by your app or library.</span></span>

#### <a name="category"></a><span data-ttu-id="38185-118">類別</span><span class="sxs-lookup"><span data-stu-id="38185-118">Category</span></span>

<span data-ttu-id="38185-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="38185-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="38185-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="38185-120">Affected APIs</span></span>

- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- <xref:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.%23ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- `M:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)",
"nameWithType": "ResponseCachingMiddleware.ResponseCachingMiddleware(RequestDelegate, IOptions<ResponseCachingOptions>, ILoggerFactory, IResponseCachingPolicyProvider, IResponseCache, IResponseCachingKeyProvider)`

-->
