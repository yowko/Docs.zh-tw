---
ms.openlocfilehash: 22ef5d0f91a4f61ca75203f677bcc14e91d77dc1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394033"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="a5edb-101">HTTP：回應主體基礎結構變更</span><span class="sxs-lookup"><span data-stu-id="a5edb-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="a5edb-102">支援 HTTP 回應主體的基礎結構已變更。</span><span class="sxs-lookup"><span data-stu-id="a5edb-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="a5edb-103">如果您直接使用 `HttpResponse`，則不需要進行任何程式碼變更。</span><span class="sxs-lookup"><span data-stu-id="a5edb-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="a5edb-104">如果您要包裝或取代 `HttpResponse.Body` 或存取 `HttpContext.Features`，請進一步閱讀。</span><span class="sxs-lookup"><span data-stu-id="a5edb-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a5edb-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="a5edb-105">Version introduced</span></span>

<span data-ttu-id="a5edb-106">3.0</span><span class="sxs-lookup"><span data-stu-id="a5edb-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a5edb-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="a5edb-107">Old behavior</span></span>

<span data-ttu-id="a5edb-108">有三個與 HTTP 回應主體相關聯的 Api：</span><span class="sxs-lookup"><span data-stu-id="a5edb-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="a5edb-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="a5edb-109">New behavior</span></span>

<span data-ttu-id="a5edb-110">如果您取代 `HttpResponse.Body`，則會使用 `StreamResponseBodyFeature`，以指定串流的包裝函式取代整個 `IHttpResponseBodyFeature`，以提供所有預期 Api 的預設執行。</span><span class="sxs-lookup"><span data-stu-id="a5edb-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="a5edb-111">將原始資料流程設回會還原此變更。</span><span class="sxs-lookup"><span data-stu-id="a5edb-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a5edb-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="a5edb-112">Reason for change</span></span>

<span data-ttu-id="a5edb-113">動機是將回應主體 Api 結合成單一的新功能介面。</span><span class="sxs-lookup"><span data-stu-id="a5edb-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a5edb-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="a5edb-114">Recommended action</span></span>

<span data-ttu-id="a5edb-115">使用 `IHttpResponseBodyFeature`，您先前使用的是 `IHttpResponseFeature.Body`、`IHttpSendFileFeature` 或 `IHttpBufferingFeature`。</span><span class="sxs-lookup"><span data-stu-id="a5edb-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="a5edb-116">分類</span><span class="sxs-lookup"><span data-stu-id="a5edb-116">Category</span></span>

<span data-ttu-id="a5edb-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a5edb-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a5edb-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a5edb-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>
 
<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
