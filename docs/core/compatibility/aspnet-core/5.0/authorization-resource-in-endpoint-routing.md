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
# <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a>授權：端點路由中的資源為 HttpCoNtext

使用 ASP.NET Core 3.1 中的端點路由時，用於授權的資源是端點。 這種方法不足以取得路由資料 () 的存取權 <xref:Microsoft.AspNetCore.Routing.RouteData> 。 先前在 MVC 中 <xref:Microsoft.AspNetCore.Http.HttpContext> 傳入的資源，可讓您存取端點 (<xref:Microsoft.AspNetCore.Http.Endpoint>) 和路由資料。 這項變更可確保傳遞給授權的資源一律為 `HttpContext` 。

## <a name="version-introduced"></a>引進的版本

5.0 Preview 7

## <a name="old-behavior"></a>舊的行為

使用端點路由和授權中介軟體 (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) 或 [[授權]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) 屬性時，傳遞給授權的資源就是相符的端點。

## <a name="new-behavior"></a>新的行為

端點路由會傳遞 `HttpContext` 給授權。

## <a name="reason-for-change"></a>變更的原因

您可以從取得端點 `HttpContext` 。 不過，沒有任何方法可從端點取得路由資料等專案。 非端點路由的功能遺失。

## <a name="recommended-action"></a>建議的動作

如果您的應用程式使用端點資源，請 <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> 在上呼叫， `HttpContext` 以繼續存取端點。

在 ASP.NET Core 5.0 Preview 8 和更新版本中，您可以使用還原成舊版的行為 <xref:System.AppContext.SetSwitch%2A> 。 例如：

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

## <a name="affected-apis"></a>受影響的 API

None

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
