---
ms.openlocfilehash: 494e792d63a611cdaedf3e40aa607cfbb0420ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901969"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>身份驗證：牛頓軟.Json 類型替換

在ASP.NET核心 3.0`Newtonsoft.Json`中，身份驗證 API 中使用的類型已`System.Text.Json`替換為類型。 除以下情況外，身份驗證封裝的基本使用不受影響：

* 派生自 OAuth 提供程式的類，例如來自[aspnet-contrib 的](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers)類。
* 高級聲明操作實現。

有關詳細資訊，請參閱[點網/阿斯平核心#7105](https://github.com/dotnet/aspnetcore/pull/7105)。 有關討論，請參閱[點網/阿斯平核心#7289](https://github.com/dotnet/aspnetcore/issues/7289)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

對於派生的 OAuth 實現，最常見的`JObject.Parse`更改是在`JsonDocument.Parse``CreateTicketAsync`重寫中替換為，[如下所示](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40)。 `JsonDocument` 會實作 `IDisposable`。

以下清單概述了已知的更改：

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>變為`ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`。 的所有`ClaimAction`派生實現都同樣受到影響。
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> 變成 `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> 變成 `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>已刪除一個舊建構函式，另一個`JObject`替換為`JsonElement`。 屬性`User`和方法`RunClaimActions`已更新以匹配。
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>現在接受類型的`JsonDocument`參數而不是`JObject`。 屬性`Response`已更新以匹配。 `OAuthTokenResponse`現在是一次性的，將由 處理`OAuthHandler`。 重寫`ExchangeCodeAsync`的派生 OAuth 實現不需要釋放`JsonDocument`或`OAuthTokenResponse`。
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>從`JObject`更改為`JsonDocument`。
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>從`JObject`更改為`JsonElement`。
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType>從接受`JObject`更改為`JsonElement`。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.AspNetCore.Authentication.Facebook?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.MicrosoftAccount?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OAuth?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Twitter?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Facebook`
- `N:Microsoft.AspNetCore.Authentication.Google`
- `N:Microsoft.AspNetCore.Authentication.MicrosoftAccount`
- `N:Microsoft.AspNetCore.Authentication.OAuth`
- `N:Microsoft.AspNetCore.Authentication.OpenIdConnect`
- `N:Microsoft.AspNetCore.Authentication.Twitter`

-->
