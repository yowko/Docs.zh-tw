---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394070"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>驗證： OAuthHandler ExchangeCodeAsync 簽章已變更

在 ASP.NET Core 3.0 中，`OAuthHandler.ExchangeCodeAsync` 的簽章已從：

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

收件者:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

@No__t-0 和 @no__t 1 字串已當做個別引數傳遞。

#### <a name="new-behavior"></a>新的行為

`Code` 和 `RedirectUri` 是 `OAuthCodeExchangeContext` 的屬性，可以透過 `OAuthCodeExchangeContext` 的函式來設定。 新的 `OAuthCodeExchangeContext` 型別是傳遞給 `OAuthHandler.ExchangeCodeAsync` 的唯一引數。

#### <a name="reason-for-change"></a>變更的原因

這項變更可讓您以不中斷的方式提供其他參數。 不需要建立新的 `ExchangeCodeAsync` 多載。

#### <a name="recommended-action"></a>建議的動作

使用適當的 `code` 和 @no__t 2 值來建立 `OAuthCodeExchangeContext`。 必須提供 <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> 實例。 這個單一 `OAuthCodeExchangeContext` 實例可以傳遞給 `OAuthHandler.ExchangeCodeAsync`，而不是多個引數。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
