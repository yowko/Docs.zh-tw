---
ms.openlocfilehash: ae5a5fbf97ed4a03de7d35b9d5d5ca8de3aebc39
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394343"
---
### <a name="caching-responsecaching-pubternal-types-changed-to-internal"></a><span data-ttu-id="d03f8-101">Caching： ResponseCaching "pubternal" 類型已變更為 internal</span><span class="sxs-lookup"><span data-stu-id="d03f8-101">Caching: ResponseCaching "pubternal" types changed to internal</span></span>

<span data-ttu-id="d03f8-102">在 ASP.NET Core 3.0 中，`ResponseCaching` 中的 "pubternal" 類型已變更為 `internal`。</span><span class="sxs-lookup"><span data-stu-id="d03f8-102">In ASP.NET Core 3.0, "pubternal" types in `ResponseCaching` have been changed to `internal`.</span></span>

<span data-ttu-id="d03f8-103">此外，`IResponseCachingPolicyProvider` 和 `IResponseCachingKeyProvider` 的預設值不會再加入至服務，做為 @no__t 2 方法的一部分。</span><span class="sxs-lookup"><span data-stu-id="d03f8-103">In addition, default implementations of `IResponseCachingPolicyProvider` and `IResponseCachingKeyProvider` are no longer added to services as part of the `AddResponseCaching` method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d03f8-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="d03f8-104">Change description</span></span>

<span data-ttu-id="d03f8-105">在 ASP.NET Core 中，"pubternal" 類型會宣告為 `public`，但位於尾碼為 `.Internal` 的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="d03f8-105">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a namespace suffixed with `.Internal`.</span></span> <span data-ttu-id="d03f8-106">雖然這些類型是公用的，但它們沒有支援原則，而且可能會受到重大變更。</span><span class="sxs-lookup"><span data-stu-id="d03f8-106">While these types are public, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="d03f8-107">可惜的是，意外使用這些型別是很常見的，因而導致這些專案的重大變更，並限制維護架構的能力。</span><span class="sxs-lookup"><span data-stu-id="d03f8-107">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d03f8-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d03f8-108">Version introduced</span></span>

<span data-ttu-id="d03f8-109">3.0</span><span class="sxs-lookup"><span data-stu-id="d03f8-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d03f8-110">舊的行為</span><span class="sxs-lookup"><span data-stu-id="d03f8-110">Old behavior</span></span>

<span data-ttu-id="d03f8-111">這些類型是公開可見的，但不受支援。</span><span class="sxs-lookup"><span data-stu-id="d03f8-111">These types were publicly visible, but unsupported.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d03f8-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="d03f8-112">New behavior</span></span>

<span data-ttu-id="d03f8-113">這些類型現在 `internal`。</span><span class="sxs-lookup"><span data-stu-id="d03f8-113">These types are now `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d03f8-114">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d03f8-114">Reason for change</span></span>

<span data-ttu-id="d03f8-115">@No__t-0 範圍更能反映不受支援的原則。</span><span class="sxs-lookup"><span data-stu-id="d03f8-115">The `internal` scope better reflects the unsupported policy.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d03f8-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d03f8-116">Recommended action</span></span>

<span data-ttu-id="d03f8-117">複製您的應用程式或程式庫所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="d03f8-117">Copy types that are used by your app or library.</span></span>

#### <a name="category"></a><span data-ttu-id="d03f8-118">分類</span><span class="sxs-lookup"><span data-stu-id="d03f8-118">Category</span></span>

<span data-ttu-id="d03f8-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d03f8-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d03f8-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d03f8-120">Affected APIs</span></span>

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
