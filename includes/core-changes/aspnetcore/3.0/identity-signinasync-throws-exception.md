---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032368"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Identity： SignInAsync 會針對未驗證的身分識別擲回例外狀況

根據預設，會擲回主體/身分識別的 `SignInAsync` 例外狀況 `IsAuthenticated` `false` 。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`SignInAsync` 接受任何主體/身分識別，包括中的身分識別 `IsAuthenticated` `false` 。

#### <a name="new-behavior"></a>新的行為

根據預設，會擲回主體/身分識別的 `SignInAsync` 例外狀況 `IsAuthenticated` `false` 。 有一個新的旗標可抑制此行為，但預設行為已經變更。

#### <a name="reason-for-change"></a>變更的原因

舊的行為有問題，因為依預設會拒絕這些主體 `[Authorize]`  /  `RequireAuthenticatedUser()` 。

#### <a name="recommended-action"></a>建議的動作

在 ASP.NET Core 3.0 Preview 6 中， `RequireAuthenticatedSignIn` 預設會有旗標 `AuthenticationOptions` `true` 。 將此旗標設定為， `false` 以還原舊的行為。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
