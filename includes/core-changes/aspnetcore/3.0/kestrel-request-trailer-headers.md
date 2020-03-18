---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394375"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="d577b-101">Kestrel：請求將拖車頭移動到新集合</span><span class="sxs-lookup"><span data-stu-id="d577b-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="d577b-102">在以前的版本中，Kestrel 在讀取請求正文到末尾時，將 HTTP/1.1 塊塊的掛頁標頭添加到請求標頭集合中。</span><span class="sxs-lookup"><span data-stu-id="d577b-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="d577b-103">此行為引起了對標頭和尾部之間歧義的擔憂。</span><span class="sxs-lookup"><span data-stu-id="d577b-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="d577b-104">決定把拖車移到一個新的收藏。</span><span class="sxs-lookup"><span data-stu-id="d577b-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="d577b-105">HTTP/2 請求預告片在 ASP.NET 酷 2.2 中不可用，但現在在 ASP.NET Core 3.0 中，此新集合中也提供了該請求預告片。</span><span class="sxs-lookup"><span data-stu-id="d577b-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="d577b-106">添加了新的請求擴充方法來訪問這些拖車。</span><span class="sxs-lookup"><span data-stu-id="d577b-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="d577b-107">HTTP/1.1 預告片在讀取整個請求正文後可用。</span><span class="sxs-lookup"><span data-stu-id="d577b-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="d577b-108">HTTP/2 預告片一旦從用戶端收到，即可用。</span><span class="sxs-lookup"><span data-stu-id="d577b-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="d577b-109">在整個請求正文至少由伺服器緩衝之前，用戶端不會發送預告片。</span><span class="sxs-lookup"><span data-stu-id="d577b-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="d577b-110">您可能需要讀取請求正文以釋放緩衝區空間。</span><span class="sxs-lookup"><span data-stu-id="d577b-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="d577b-111">如果您將請求正文讀到末尾，則始終可用拖車。</span><span class="sxs-lookup"><span data-stu-id="d577b-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="d577b-112">拖車標誌著身體的盡頭。</span><span class="sxs-lookup"><span data-stu-id="d577b-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d577b-113">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="d577b-113">Version introduced</span></span>

<span data-ttu-id="d577b-114">3.0</span><span class="sxs-lookup"><span data-stu-id="d577b-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d577b-115">舊的行為</span><span class="sxs-lookup"><span data-stu-id="d577b-115">Old behavior</span></span>

<span data-ttu-id="d577b-116">請求將拖車標頭添加到集合中`HttpRequest.Headers`。</span><span class="sxs-lookup"><span data-stu-id="d577b-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d577b-117">新的行為</span><span class="sxs-lookup"><span data-stu-id="d577b-117">New behavior</span></span>

<span data-ttu-id="d577b-118">請求拖車標頭**不在**集合中`HttpRequest.Headers`。</span><span class="sxs-lookup"><span data-stu-id="d577b-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="d577b-119">使用以下擴充方法`HttpRequest`訪問它們：</span><span class="sxs-lookup"><span data-stu-id="d577b-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="d577b-120">`GetDeclaredTrailers()`- 獲取請求"Trailer"標頭，列出在正文之後要期待的預告片。</span><span class="sxs-lookup"><span data-stu-id="d577b-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="d577b-121">`SupportsTrailers()`- 指示請求是否支援接收拖車頭。</span><span class="sxs-lookup"><span data-stu-id="d577b-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="d577b-122">`CheckTrailersAvailable()`- 確定請求是否支援預告片，以及它們是否可用於閱讀。</span><span class="sxs-lookup"><span data-stu-id="d577b-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="d577b-123">`GetTrailer(string trailerName)`- 從回應獲取請求的尾隨標頭。</span><span class="sxs-lookup"><span data-stu-id="d577b-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d577b-124">更改原因</span><span class="sxs-lookup"><span data-stu-id="d577b-124">Reason for change</span></span>

<span data-ttu-id="d577b-125">在 gRPC 等方案中，拖車是一個關鍵功能。</span><span class="sxs-lookup"><span data-stu-id="d577b-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="d577b-126">將預告片合併到請求標頭中會令使用者感到困惑。</span><span class="sxs-lookup"><span data-stu-id="d577b-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d577b-127">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d577b-127">Recommended action</span></span>

<span data-ttu-id="d577b-128">使用與拖車相關的擴充方法`HttpRequest`訪問拖車。</span><span class="sxs-lookup"><span data-stu-id="d577b-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="d577b-129">類別</span><span class="sxs-lookup"><span data-stu-id="d577b-129">Category</span></span>

<span data-ttu-id="d577b-130">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d577b-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d577b-131">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d577b-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
