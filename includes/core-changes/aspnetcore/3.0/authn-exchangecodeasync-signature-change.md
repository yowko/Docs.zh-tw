---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394070"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>驗證： OAuthHandler ExchangeCodeAsync 簽章已變更

在 ASP.NET Core 3.0 中，的簽章 `OAuthHandler.ExchangeCodeAsync` 已變更為：

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

變更為：

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`code`和 `redirectUri` 字串以個別的引數傳遞。

#### <a name="new-behavior"></a>新的行為

`Code` 和 `RedirectUri` 都是上的屬性，可以透過函式來 `OAuthCodeExchangeContext` 設定 `OAuthCodeExchangeContext` 。 新 `OAuthCodeExchangeContext` 類型是唯一傳遞給的引數 `OAuthHandler.ExchangeCodeAsync` 。

#### <a name="reason-for-change"></a>變更的原因

這項變更可讓您以非中斷的方式提供額外的參數。 不需要建立新的多載 `ExchangeCodeAsync` 。

#### <a name="recommended-action"></a>建議的動作

`OAuthCodeExchangeContext`使用適當的 `code` 和值來建立 `redirectUri` 。 <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties>必須提供實例。 此單一 `OAuthCodeExchangeContext` 實例可以傳遞給， `OAuthHandler.ExchangeCodeAsync` 而不是多個引數。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
