---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032322"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>授權： IAuthorizationPolicyProvider 執行需要新的方法

在 ASP.NET Core 3.0 中，已將新 `GetFallbackPolicyAsync` 方法加入至 `IAuthorizationPolicyProvider` 。 當未指定任何原則時，授權中介軟體會使用此回退原則。

如需詳細資訊，請參閱 [dotnet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

的實現不 `IAuthorizationPolicyProvider` 需要 `GetFallbackPolicyAsync` 方法。

#### <a name="new-behavior"></a>新的行為

的執行 `IAuthorizationPolicyProvider` 需要 `GetFallbackPolicyAsync` 方法。

#### <a name="reason-for-change"></a>變更的原因

如果未指定任何原則，則需要新的方法 `AuthorizationMiddleware` 才能使用新的。

#### <a name="recommended-action"></a>建議的動作

將 `GetFallbackPolicyAsync` 方法新增至的您的執行 `IAuthorizationPolicyProvider` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
