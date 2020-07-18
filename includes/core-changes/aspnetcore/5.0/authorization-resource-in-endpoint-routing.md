---
ms.openlocfilehash: 2b88ab7cfdd7a0a0a770b305ecd0200afd9a9b4b
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441542"
---
### <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a><span data-ttu-id="49e1b-101">授權：端點路由中的資源是 HttpCoNtext</span><span class="sxs-lookup"><span data-stu-id="49e1b-101">Authorization: Resource in endpoint routing is HttpContext</span></span>

<span data-ttu-id="49e1b-102">使用 ASP.NET Core 3.1 中的端點路由時，用於授權的資源就是端點。</span><span class="sxs-lookup"><span data-stu-id="49e1b-102">When using endpoint routing in ASP.NET Core 3.1, the resource used for authorization is the endpoint.</span></span> <span data-ttu-id="49e1b-103">這種方法不足以取得路由資料（）的存取權 <xref:Microsoft.AspNetCore.Routing.RouteData> 。</span><span class="sxs-lookup"><span data-stu-id="49e1b-103">This approach was insufficient for gaining access to the route data (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span></span> <span data-ttu-id="49e1b-104">先前在 MVC 中， <xref:Microsoft.AspNetCore.Http.HttpContext> 已傳入資源，可讓您存取端點（ <xref:Microsoft.AspNetCore.Http.Endpoint> ）和路由資料。</span><span class="sxs-lookup"><span data-stu-id="49e1b-104">Previously in MVC, an <xref:Microsoft.AspNetCore.Http.HttpContext> resource was passed in, which allows access to both the endpoint (<xref:Microsoft.AspNetCore.Http.Endpoint>) and the route data.</span></span> <span data-ttu-id="49e1b-105">這種變更可確保傳遞給授權的資源一律為 `HttpContext` 。</span><span class="sxs-lookup"><span data-stu-id="49e1b-105">This change ensures that the resource passed to authorization is always the `HttpContext`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="49e1b-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="49e1b-106">Version introduced</span></span>

<span data-ttu-id="49e1b-107">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="49e1b-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="49e1b-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="49e1b-108">Old behavior</span></span>

<span data-ttu-id="49e1b-109">使用端點路由和授權中介軟體（ <xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware> ）或[[授權]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute)屬性時，傳遞給授權的資源就是相符的端點。</span><span class="sxs-lookup"><span data-stu-id="49e1b-109">When using endpoint routing and the authorization middleware (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) or [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) attributes, the resource passed to authorization is the matching endpoint.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="49e1b-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="49e1b-110">New behavior</span></span>

<span data-ttu-id="49e1b-111">端點路由會將傳遞 `HttpContext` 至授權。</span><span class="sxs-lookup"><span data-stu-id="49e1b-111">Endpoint routing passes the `HttpContext` to authorization.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="49e1b-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="49e1b-112">Reason for change</span></span>

<span data-ttu-id="49e1b-113">您可以從取得端點 `HttpContext` 。</span><span class="sxs-lookup"><span data-stu-id="49e1b-113">You can get to the endpoint from the `HttpContext`.</span></span> <span data-ttu-id="49e1b-114">不過，沒有任何方法可以從端點取得路由資料之類的專案。</span><span class="sxs-lookup"><span data-stu-id="49e1b-114">However, there was no way to get from the endpoint to things like the route data.</span></span> <span data-ttu-id="49e1b-115">非端點路由中的功能遺失。</span><span class="sxs-lookup"><span data-stu-id="49e1b-115">There was a loss in functionality from non-endpoint routing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="49e1b-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="49e1b-116">Recommended action</span></span>

<span data-ttu-id="49e1b-117">如果您的應用程式使用端點資源，請 <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> 在上呼叫 `HttpContext` 以繼續存取端點。</span><span class="sxs-lookup"><span data-stu-id="49e1b-117">If your app uses the endpoint resource, call <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> on the `HttpContext` to continue accessing the endpoint.</span></span>

<span data-ttu-id="49e1b-118">在 ASP.NET Core 5.0 Preview 8 和更新版本中，您可以使用還原成舊的行為 <xref:System.AppContext.SetSwitch%2A> 。</span><span class="sxs-lookup"><span data-stu-id="49e1b-118">In ASP.NET Core 5.0 Preview 8 and later, you can revert to the old behavior with <xref:System.AppContext.SetSwitch%2A>.</span></span> <span data-ttu-id="49e1b-119">例如：</span><span class="sxs-lookup"><span data-stu-id="49e1b-119">For example:</span></span>

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

#### <a name="category"></a><span data-ttu-id="49e1b-120">類別</span><span class="sxs-lookup"><span data-stu-id="49e1b-120">Category</span></span>

<span data-ttu-id="49e1b-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49e1b-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="49e1b-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="49e1b-122">Affected APIs</span></span>

<span data-ttu-id="49e1b-123">無</span><span class="sxs-lookup"><span data-stu-id="49e1b-123">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
