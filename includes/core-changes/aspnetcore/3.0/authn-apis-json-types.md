---
ms.openlocfilehash: b4499637cd5fff015335e0cdb3c6cf1c3ea6cff0
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637180"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>身份驗證:牛頓軟.Json 類型替換

在ASP.NET核心 3.0`Newtonsoft.Json`中,身份驗證API中使用的`System.Text.Json`類型已替換為類型。 除以下情況外,身份驗證包的基本使用不受影響:

* 派生自 OAuth 提供程式的類,例如來自[aspnet-contrib 的](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers)類。
* 高級聲明操作實現。

有關詳細資訊,請參閱[點網/阿斯平核心#7105](https://github.com/dotnet/aspnetcore/pull/7105)。 有關討論,請參閱[點網/阿斯平核心#7289](https://github.com/dotnet/aspnetcore/issues/7289)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

對於派生的 OAuth 實現,最`JObject.Parse`常見的`JsonDocument.Parse``CreateTicketAsync`變更是在 重寫中取代為,[如下所示](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40)。 `JsonDocument` 會實作 `IDisposable`。

以下清單概述了已知的更改:

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>變為`ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`。 的所有`ClaimAction`派生實現都同樣受到影響。
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> 變成 `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> 變成 `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>已刪除舊建構函數,另一個`JObject`取代為`JsonElement`。 屬性`User`和方法`RunClaimActions`已更新以匹配。
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>現在接受型態`JsonDocument`的`JObject`參數而不是 。 屬性`Response`已更新以匹配。 `OAuthTokenResponse`現在是一次性的,將由`OAuthHandler`處理 。 重寫`ExchangeCodeAsync`的派生 OAuth`JsonDocument`實現`OAuthTokenResponse`不需要釋放 或 。
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>從`JObject`變更`JsonDocument`為 。
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>從`JObject`變更`JsonElement`為 。
- [TwitterHandler.createTicketAsync(宣告身份、身份驗證屬性、存取權杖、JObject)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.authentication.twitter.twitterhandler.createticketasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Authentication_Twitter_TwitterHandler_CreateTicketAsync_System_Security_Claims_ClaimsIdentity_Microsoft_AspNetCore_Authentication_AuthenticationProperties_Microsoft_AspNetCore_Authentication_Twitter_AccessToken_Newtonsoft_Json_Linq_JObject_)的最後一個`JObject`參數從`JsonElement`變更為 。 取代方法是<xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,System.Text.Json.JsonElement)?displayProperty=nameWithType>。

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
