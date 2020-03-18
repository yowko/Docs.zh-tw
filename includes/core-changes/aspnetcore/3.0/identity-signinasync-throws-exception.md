---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393976"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>標識：SignInAsync 為未身份驗證的標識引發異常

預設情況下，`SignInAsync`為 主體/標識（其中`IsAuthenticated`為`false`）引發異常。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`SignInAsync`接受任何主體/身份，包括`IsAuthenticated`中`false`的身份。

#### <a name="new-behavior"></a>新的行為

預設情況下，`SignInAsync`為 主體/標識（其中`IsAuthenticated`為`false`）引發異常。 有一個新的標誌來禁止此行為，但預設行為已更改。

#### <a name="reason-for-change"></a>更改原因

舊行為存在問題，因為預設情況下，這些主體被`[Authorize]` / `RequireAuthenticatedUser()`拒絕。

#### <a name="recommended-action"></a>建議的動作

在ASP.NET酷睿 3.0 預覽 6`RequireAuthenticatedSignIn`中`AuthenticationOptions`，預設情況下有`true`一個標誌。 將此標誌設置為`false`還原舊行為。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
