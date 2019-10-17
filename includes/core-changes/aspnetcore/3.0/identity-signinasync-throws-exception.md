---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393976"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>身分識別： SignInAsync 擲回未驗證身分識別的例外狀況

根據預設，`SignInAsync` 會擲回主體/身分識別的例外狀況，其中 `IsAuthenticated` `false`。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`SignInAsync` 會接受任何主體/身分識別，包括 `IsAuthenticated` @no__t 為2的身分識別。

#### <a name="new-behavior"></a>新的行為

根據預設，`SignInAsync` 會擲回主體/身分識別的例外狀況，其中 `IsAuthenticated` `false`。 有一個新的旗標可抑制此行為，但預設行為已變更。

#### <a name="reason-for-change"></a>變更的原因

舊的行為會造成問題，因為根據預設，這些主體會被 `[Authorize]` @ no__t-1 @ no__t-2 拒絕。

#### <a name="recommended-action"></a>建議的動作

在 ASP.NET Core 3.0 Preview 6 中，`AuthenticationOptions` 上有 `RequireAuthenticatedSignIn` 旗標，預設為 `true`。 將此旗標設定為 `false`，以還原舊的行為。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
