---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394070"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>身份驗證：OAuthHandler 交換代碼同步簽名已更改

在 ASP.NET Core 3.0`OAuthHandler.ExchangeCodeAsync`中，的簽名從以下更改為：

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

變更為：

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

和`code``redirectUri`字串作為單獨的參數傳遞。

#### <a name="new-behavior"></a>新的行為

`Code`和`RedirectUri`屬性`OAuthCodeExchangeContext`可以通過`OAuthCodeExchangeContext`建構函式設置。 新`OAuthCodeExchangeContext`類型是傳遞給`OAuthHandler.ExchangeCodeAsync`的唯一參數。

#### <a name="reason-for-change"></a>更改原因

此更改允許以非中斷方式提供其他參數。 無需創建新`ExchangeCodeAsync`的重載。

#### <a name="recommended-action"></a>建議的動作

構造`OAuthCodeExchangeContext`具有適當`code`和`redirectUri`值的 。 必須<xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties>提供實例。 此單個`OAuthCodeExchangeContext`實例可以傳遞給`OAuthHandler.ExchangeCodeAsync`多個參數，而不是多個參數。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
