---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901605"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>授權： IAuthorizationPolicyProvider 的部署需要新的方法

在 ASP.NET Core 3.0 中，已將新的 `GetFallbackPolicyAsync` 方法新增至 `IAuthorizationPolicyProvider`。 當未指定任何原則時，授權中介軟體會使用此回溯原則。

如需詳細資訊，請參閱[dotnet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`IAuthorizationPolicyProvider` 的執行不需要 `GetFallbackPolicyAsync` 方法。

#### <a name="new-behavior"></a>新的行為

`IAuthorizationPolicyProvider` 的實現需要 `GetFallbackPolicyAsync` 方法。

#### <a name="reason-for-change"></a>變更的原因

新的 `AuthorizationMiddleware` 需要新的方法，才能在未指定任何原則時使用。

#### <a name="recommended-action"></a>建議的動作

將 `GetFallbackPolicyAsync` 方法加入至 `IAuthorizationPolicyProvider`的執行。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
