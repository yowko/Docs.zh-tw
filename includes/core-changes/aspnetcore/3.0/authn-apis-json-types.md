---
ms.openlocfilehash: 9bdfcca2fd03e24a636be3340f5057dc3f39358e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539572"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>驗證：已取代類型上的 Newtonsoft.Js

在 ASP.NET Core 3.0 中， `Newtonsoft.Json` 驗證 api 中使用的類型已被 `System.Text.Json` 類型取代。 除了下列情況之外，驗證套件的基本用法仍不受影響：

* 從 OAuth 提供者衍生的類別，例如來自 [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers)的類別。
* 先進的宣告操作執行。

如需詳細資訊，請參閱 [dotnet/aspnetcore # 7105 in](https://github.com/dotnet/aspnetcore/pull/7105)。 如需討論，請參閱 [dotnet/aspnetcore # 7289](https://github.com/dotnet/aspnetcore/issues/7289)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

針對衍生的 OAuth 執行，最常見的變更是 `JObject.Parse` 在覆 `JsonDocument.Parse` 寫中取代， `CreateTicketAsync` 如下[here](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40)所示。 `JsonDocument` 會實作 `IDisposable`。

下列清單概述已知的變更：

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> 成為 `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)` 。 的所有衍生實 `ClaimAction` 也會受到影響。
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> 變成 `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> 變成 `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> 已移除一個舊的函式，而另一個已取代為 `JObject` `JsonElement` 。 `User`屬性和 `RunClaimActions` 方法已更新以符合。
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> 現在接受型別為的參數， `JsonDocument` 而不是 `JObject` 。 `Response`屬性已更新為符合。 `OAuthTokenResponse` 現在是可處置的，且將由處置 `OAuthHandler` 。 衍生的 OAuth 實施覆寫 `ExchangeCodeAsync` 不需要處置 `JsonDocument` 或 `OAuthTokenResponse` 。
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> 已從變更 `JObject` 為 `JsonDocument` 。
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> 已從變更 `JObject` 為 `JsonElement` 。
- [TwitterHandler. CreateTicketAsync (ClaimsIdentity、AuthenticationProperties、AccessToken、JObject) ](/dotnet/api/microsoft.aspnetcore.authentication.twitter.twitterhandler.createticketasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Authentication_Twitter_TwitterHandler_CreateTicketAsync_System_Security_Claims_ClaimsIdentity_Microsoft_AspNetCore_Authentication_AuthenticationProperties_Microsoft_AspNetCore_Authentication_Twitter_AccessToken_Newtonsoft_Json_Linq_JObject_)的最後一個參數已從變更 `JObject` 為 `JsonElement` 。 取代方法為 <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,System.Text.Json.JsonElement)?displayProperty=nameWithType> 。

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
