---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198379"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="e5d1a-101">HTTP：回應主體基礎結構變更</span><span class="sxs-lookup"><span data-stu-id="e5d1a-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="e5d1a-102">支援 HTTP 回應主體的基礎結構已變更。</span><span class="sxs-lookup"><span data-stu-id="e5d1a-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="e5d1a-103">如果您直接使用 `HttpResponse`，則不需要進行任何程式碼變更。</span><span class="sxs-lookup"><span data-stu-id="e5d1a-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="e5d1a-104">如果您要包裝或取代 `HttpResponse.Body` 或存取 `HttpContext.Features`，請進一步閱讀。</span><span class="sxs-lookup"><span data-stu-id="e5d1a-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e5d1a-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e5d1a-105">Version introduced</span></span>

<span data-ttu-id="e5d1a-106">3.0</span><span class="sxs-lookup"><span data-stu-id="e5d1a-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e5d1a-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="e5d1a-107">Old behavior</span></span>

<span data-ttu-id="e5d1a-108">有三個與 HTTP 回應主體相關聯的 Api：</span><span class="sxs-lookup"><span data-stu-id="e5d1a-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="e5d1a-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="e5d1a-109">New behavior</span></span>

<span data-ttu-id="e5d1a-110">如果您取代 `HttpResponse.Body`，則會使用 `StreamResponseBodyFeature`，以指定串流的包裝函式取代整個 `IHttpResponseBodyFeature`，以提供所有預期 Api 的預設執行。</span><span class="sxs-lookup"><span data-stu-id="e5d1a-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="e5d1a-111">將原始資料流程設回會還原此變更。</span><span class="sxs-lookup"><span data-stu-id="e5d1a-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e5d1a-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="e5d1a-112">Reason for change</span></span>

<span data-ttu-id="e5d1a-113">動機是將回應主體 Api 結合成單一的新功能介面。</span><span class="sxs-lookup"><span data-stu-id="e5d1a-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e5d1a-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e5d1a-114">Recommended action</span></span>

<span data-ttu-id="e5d1a-115">使用 `IHttpResponseBodyFeature`，您先前使用的是 `IHttpResponseFeature.Body`、`IHttpSendFileFeature` 或 `IHttpBufferingFeature`。</span><span class="sxs-lookup"><span data-stu-id="e5d1a-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="e5d1a-116">Category</span><span class="sxs-lookup"><span data-stu-id="e5d1a-116">Category</span></span>

<span data-ttu-id="e5d1a-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e5d1a-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e5d1a-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e5d1a-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
