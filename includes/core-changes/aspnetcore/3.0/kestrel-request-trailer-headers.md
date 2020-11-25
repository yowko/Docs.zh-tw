---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032384"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="901b9-101">Kestrel：要求尾端標頭移至新集合</span><span class="sxs-lookup"><span data-stu-id="901b9-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="901b9-102">在舊版中，Kestrel 會在要求主體讀取至結尾時，將 HTTP/1.1 區塊尾端標頭新增至要求標頭集合。</span><span class="sxs-lookup"><span data-stu-id="901b9-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="901b9-103">此行為會造成標頭和結尾之間的不明確問題。</span><span class="sxs-lookup"><span data-stu-id="901b9-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="901b9-104">決定將尾端移至新的集合。</span><span class="sxs-lookup"><span data-stu-id="901b9-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="901b9-105">HTTP/2 要求結尾在 ASP.NET Core 2.2 中無法使用，但現在也可在 ASP.NET Core 3.0 的這個新集合中取得。</span><span class="sxs-lookup"><span data-stu-id="901b9-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="901b9-106">已新增新的要求延伸方法，以存取這些結尾。</span><span class="sxs-lookup"><span data-stu-id="901b9-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="901b9-107">讀取整個要求主體後，就可以使用 HTTP/1.1 尾端。</span><span class="sxs-lookup"><span data-stu-id="901b9-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="901b9-108">從用戶端收到 HTTP/2 結尾時，就可以使用它。</span><span class="sxs-lookup"><span data-stu-id="901b9-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="901b9-109">用戶端將不會傳送結尾，直到整個要求主體至少經過伺服器的緩衝處理。</span><span class="sxs-lookup"><span data-stu-id="901b9-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="901b9-110">您可能需要讀取要求主體以釋出緩衝區空間。</span><span class="sxs-lookup"><span data-stu-id="901b9-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="901b9-111">如果您已將要求主體讀取至結尾，一律可使用尾端。</span><span class="sxs-lookup"><span data-stu-id="901b9-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="901b9-112">尾端標記主體結尾。</span><span class="sxs-lookup"><span data-stu-id="901b9-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="901b9-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="901b9-113">Version introduced</span></span>

<span data-ttu-id="901b9-114">3.0</span><span class="sxs-lookup"><span data-stu-id="901b9-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="901b9-115">舊的行為</span><span class="sxs-lookup"><span data-stu-id="901b9-115">Old behavior</span></span>

<span data-ttu-id="901b9-116">要求尾端標頭會新增至 `HttpRequest.Headers` 集合。</span><span class="sxs-lookup"><span data-stu-id="901b9-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="901b9-117">新的行為</span><span class="sxs-lookup"><span data-stu-id="901b9-117">New behavior</span></span>

<span data-ttu-id="901b9-118">集合中 **不存在** 要求尾端標頭 `HttpRequest.Headers` 。</span><span class="sxs-lookup"><span data-stu-id="901b9-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="901b9-119">使用下列擴充方法 `HttpRequest` 來存取它們：</span><span class="sxs-lookup"><span data-stu-id="901b9-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="901b9-120">`GetDeclaredTrailers()` -取得要求 "尾端" 標頭，列出主體之後要預期的尾端。</span><span class="sxs-lookup"><span data-stu-id="901b9-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="901b9-121">`SupportsTrailers()` -表示要求是否支援接收尾端標頭。</span><span class="sxs-lookup"><span data-stu-id="901b9-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="901b9-122">`CheckTrailersAvailable()` -判斷要求是否支援尾端，以及是否可供讀取。</span><span class="sxs-lookup"><span data-stu-id="901b9-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="901b9-123">`GetTrailer(string trailerName)` -從回應取得要求的尾端標頭。</span><span class="sxs-lookup"><span data-stu-id="901b9-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="901b9-124">變更的原因</span><span class="sxs-lookup"><span data-stu-id="901b9-124">Reason for change</span></span>

<span data-ttu-id="901b9-125">尾端是 gRPC 案例中的重要功能。</span><span class="sxs-lookup"><span data-stu-id="901b9-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="901b9-126">將結尾合併到要求標頭會對使用者造成混淆。</span><span class="sxs-lookup"><span data-stu-id="901b9-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="901b9-127">建議的動作</span><span class="sxs-lookup"><span data-stu-id="901b9-127">Recommended action</span></span>

<span data-ttu-id="901b9-128">使用尾端相關的擴充方法 `HttpRequest` 來存取尾端。</span><span class="sxs-lookup"><span data-stu-id="901b9-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="901b9-129">類別</span><span class="sxs-lookup"><span data-stu-id="901b9-129">Category</span></span>

<span data-ttu-id="901b9-130">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="901b9-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="901b9-131">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="901b9-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
