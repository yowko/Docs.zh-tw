---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901605"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>授權：I授權策略提供程式實現需要新方法

在 ASP.NET Core 3.0`GetFallbackPolicyAsync`中，將`IAuthorizationPolicyProvider`一種新方法添加到 中。 當未指定策略時，授權中介軟體會使用此回退策略。

有關詳細資訊，請參閱[點網/阿斯平核心#9759](https://github.com/dotnet/aspnetcore/pull/9759)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

的`IAuthorizationPolicyProvider`實現不需要方法`GetFallbackPolicyAsync`。

#### <a name="new-behavior"></a>新的行為

的`IAuthorizationPolicyProvider`實現需要一種方法`GetFallbackPolicyAsync`。

#### <a name="reason-for-change"></a>更改原因

當未指定策略時，新方法`AuthorizationMiddleware`需要一個新的方法才能使用。

#### <a name="recommended-action"></a>建議的動作

將`GetFallbackPolicyAsync`方法添加到 的`IAuthorizationPolicyProvider`實現中。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
