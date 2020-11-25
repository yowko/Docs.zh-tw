---
title: 重大變更：授權：端點路由中的資源為 HttpCoNtext
description: 瞭解 ASP.NET Core 5.0 的重大變更，其標題為授權：端點路由中的資源為 HttpCoNtext
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 7c5a77cb8999c60a7780b9b4f7ad2a1c79fd8310
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760780"
---
# <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a><span data-ttu-id="39ae3-103">授權：端點路由中的資源為 HttpCoNtext</span><span class="sxs-lookup"><span data-stu-id="39ae3-103">Authorization: Resource in endpoint routing is HttpContext</span></span>

<span data-ttu-id="39ae3-104">使用 ASP.NET Core 3.1 中的端點路由時，用於授權的資源是端點。</span><span class="sxs-lookup"><span data-stu-id="39ae3-104">When using endpoint routing in ASP.NET Core 3.1, the resource used for authorization is the endpoint.</span></span> <span data-ttu-id="39ae3-105">這種方法不足以取得路由資料 () 的存取權 <xref:Microsoft.AspNetCore.Routing.RouteData> 。</span><span class="sxs-lookup"><span data-stu-id="39ae3-105">This approach was insufficient for gaining access to the route data (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span></span> <span data-ttu-id="39ae3-106">先前在 MVC 中 <xref:Microsoft.AspNetCore.Http.HttpContext> 傳入的資源，可讓您存取端點 (<xref:Microsoft.AspNetCore.Http.Endpoint>) 和路由資料。</span><span class="sxs-lookup"><span data-stu-id="39ae3-106">Previously in MVC, an <xref:Microsoft.AspNetCore.Http.HttpContext> resource was passed in, which allows access to both the endpoint (<xref:Microsoft.AspNetCore.Http.Endpoint>) and the route data.</span></span> <span data-ttu-id="39ae3-107">這項變更可確保傳遞給授權的資源一律為 `HttpContext` 。</span><span class="sxs-lookup"><span data-stu-id="39ae3-107">This change ensures that the resource passed to authorization is always the `HttpContext`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="39ae3-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="39ae3-108">Version introduced</span></span>

<span data-ttu-id="39ae3-109">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="39ae3-109">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="39ae3-110">舊的行為</span><span class="sxs-lookup"><span data-stu-id="39ae3-110">Old behavior</span></span>

<span data-ttu-id="39ae3-111">使用端點路由和授權中介軟體 (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) 或 [[授權]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) 屬性時，傳遞給授權的資源就是相符的端點。</span><span class="sxs-lookup"><span data-stu-id="39ae3-111">When using endpoint routing and the authorization middleware (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) or [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) attributes, the resource passed to authorization is the matching endpoint.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="39ae3-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="39ae3-112">New behavior</span></span>

<span data-ttu-id="39ae3-113">端點路由會傳遞 `HttpContext` 給授權。</span><span class="sxs-lookup"><span data-stu-id="39ae3-113">Endpoint routing passes the `HttpContext` to authorization.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="39ae3-114">變更的原因</span><span class="sxs-lookup"><span data-stu-id="39ae3-114">Reason for change</span></span>

<span data-ttu-id="39ae3-115">您可以從取得端點 `HttpContext` 。</span><span class="sxs-lookup"><span data-stu-id="39ae3-115">You can get to the endpoint from the `HttpContext`.</span></span> <span data-ttu-id="39ae3-116">不過，沒有任何方法可從端點取得路由資料等專案。</span><span class="sxs-lookup"><span data-stu-id="39ae3-116">However, there was no way to get from the endpoint to things like the route data.</span></span> <span data-ttu-id="39ae3-117">非端點路由的功能遺失。</span><span class="sxs-lookup"><span data-stu-id="39ae3-117">There was a loss in functionality from non-endpoint routing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="39ae3-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="39ae3-118">Recommended action</span></span>

<span data-ttu-id="39ae3-119">如果您的應用程式使用端點資源，請 <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> 在上呼叫， `HttpContext` 以繼續存取端點。</span><span class="sxs-lookup"><span data-stu-id="39ae3-119">If your app uses the endpoint resource, call <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> on the `HttpContext` to continue accessing the endpoint.</span></span>

<span data-ttu-id="39ae3-120">在 ASP.NET Core 5.0 Preview 8 和更新版本中，您可以使用還原成舊版的行為 <xref:System.AppContext.SetSwitch%2A> 。</span><span class="sxs-lookup"><span data-stu-id="39ae3-120">In ASP.NET Core 5.0 Preview 8 and later, you can revert to the old behavior with <xref:System.AppContext.SetSwitch%2A>.</span></span> <span data-ttu-id="39ae3-121">例如：</span><span class="sxs-lookup"><span data-stu-id="39ae3-121">For example:</span></span>

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

## <a name="affected-apis"></a><span data-ttu-id="39ae3-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="39ae3-122">Affected APIs</span></span>

<span data-ttu-id="39ae3-123">None</span><span class="sxs-lookup"><span data-stu-id="39ae3-123">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
