---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032364"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="a68cf-101">HTTP：回應主體基礎結構變更</span><span class="sxs-lookup"><span data-stu-id="a68cf-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="a68cf-102">支援 HTTP 回應主體的基礎結構已變更。</span><span class="sxs-lookup"><span data-stu-id="a68cf-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="a68cf-103">如果您是 `HttpResponse` 直接使用，就不需要進行任何程式碼變更。</span><span class="sxs-lookup"><span data-stu-id="a68cf-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="a68cf-104">如果您要換行或取代 `HttpResponse.Body` 或存取，請進一步閱讀 `HttpContext.Features` 。</span><span class="sxs-lookup"><span data-stu-id="a68cf-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a68cf-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="a68cf-105">Version introduced</span></span>

<span data-ttu-id="a68cf-106">3.0</span><span class="sxs-lookup"><span data-stu-id="a68cf-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a68cf-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="a68cf-107">Old behavior</span></span>

<span data-ttu-id="a68cf-108">HTTP 回應主體有三個相關聯的 Api：</span><span class="sxs-lookup"><span data-stu-id="a68cf-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="a68cf-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="a68cf-109">New behavior</span></span>

<span data-ttu-id="a68cf-110">如果您取代 `HttpResponse.Body` 了，則會使用指定的資料流程周圍的包裝函式來取代整個， `IHttpResponseBodyFeature` `StreamResponseBodyFeature` 以提供所有預期 api 的預設執行。</span><span class="sxs-lookup"><span data-stu-id="a68cf-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="a68cf-111">設定回原始資料流程會還原此變更。</span><span class="sxs-lookup"><span data-stu-id="a68cf-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a68cf-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="a68cf-112">Reason for change</span></span>

<span data-ttu-id="a68cf-113">動機是將回應內文 Api 合併成單一的新功能介面。</span><span class="sxs-lookup"><span data-stu-id="a68cf-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a68cf-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="a68cf-114">Recommended action</span></span>

<span data-ttu-id="a68cf-115">使用 `IHttpResponseBodyFeature` 您先前使用 `IHttpResponseFeature.Body` 、或的位置 `IHttpSendFileFeature` `IHttpBufferingFeature` 。</span><span class="sxs-lookup"><span data-stu-id="a68cf-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="a68cf-116">類別</span><span class="sxs-lookup"><span data-stu-id="a68cf-116">Category</span></span>

<span data-ttu-id="a68cf-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a68cf-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a68cf-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a68cf-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
