---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198379"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="5ca45-101">HTTP：回應正文基礎結構更改</span><span class="sxs-lookup"><span data-stu-id="5ca45-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="5ca45-102">支援 HTTP 回應正文的基礎結構已更改。</span><span class="sxs-lookup"><span data-stu-id="5ca45-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="5ca45-103">如果您直接使用`HttpResponse`，則不需要進行任何代碼更改。</span><span class="sxs-lookup"><span data-stu-id="5ca45-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="5ca45-104">如果要包裝、替換`HttpResponse.Body`或訪問`HttpContext.Features`，請進一步閱讀。</span><span class="sxs-lookup"><span data-stu-id="5ca45-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5ca45-105">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="5ca45-105">Version introduced</span></span>

<span data-ttu-id="5ca45-106">3.0</span><span class="sxs-lookup"><span data-stu-id="5ca45-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5ca45-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="5ca45-107">Old behavior</span></span>

<span data-ttu-id="5ca45-108">有三個 API 與 HTTP 回應正文相關聯：</span><span class="sxs-lookup"><span data-stu-id="5ca45-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="5ca45-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="5ca45-109">New behavior</span></span>

<span data-ttu-id="5ca45-110">如果替換`HttpResponse.Body`，它將用給定流周圍的`IHttpResponseBodyFeature`包裝器替換整個物件，用於`StreamResponseBodyFeature`為所有預期的 API 提供預設實現。</span><span class="sxs-lookup"><span data-stu-id="5ca45-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="5ca45-111">設置回原始流將恢復此更改。</span><span class="sxs-lookup"><span data-stu-id="5ca45-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5ca45-112">更改原因</span><span class="sxs-lookup"><span data-stu-id="5ca45-112">Reason for change</span></span>

<span data-ttu-id="5ca45-113">動機是將回應體 API 合併到單個新功能介面中。</span><span class="sxs-lookup"><span data-stu-id="5ca45-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5ca45-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="5ca45-114">Recommended action</span></span>

<span data-ttu-id="5ca45-115">使用`IHttpResponseBodyFeature`以前使用`IHttpResponseFeature.Body`或`IHttpSendFileFeature``IHttpBufferingFeature`的位置。</span><span class="sxs-lookup"><span data-stu-id="5ca45-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="5ca45-116">類別</span><span class="sxs-lookup"><span data-stu-id="5ca45-116">Category</span></span>

<span data-ttu-id="5ca45-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5ca45-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5ca45-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5ca45-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
