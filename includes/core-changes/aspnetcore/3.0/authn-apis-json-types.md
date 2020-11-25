---
ms.openlocfilehash: 9bdfcca2fd03e24a636be3340f5057dc3f39358e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032344"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="e39d9-101">驗證：已取代類型上的 Newtonsoft.Js</span><span class="sxs-lookup"><span data-stu-id="e39d9-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="e39d9-102">在 ASP.NET Core 3.0 中， `Newtonsoft.Json` 驗證 api 中使用的類型已被 `System.Text.Json` 類型取代。</span><span class="sxs-lookup"><span data-stu-id="e39d9-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="e39d9-103">除了下列情況之外，驗證套件的基本用法仍不受影響：</span><span class="sxs-lookup"><span data-stu-id="e39d9-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="e39d9-104">從 OAuth 提供者衍生的類別，例如來自 [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers)的類別。</span><span class="sxs-lookup"><span data-stu-id="e39d9-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="e39d9-105">先進的宣告操作執行。</span><span class="sxs-lookup"><span data-stu-id="e39d9-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="e39d9-106">如需詳細資訊，請參閱 [dotnet/aspnetcore # 7105 in](https://github.com/dotnet/aspnetcore/pull/7105)。</span><span class="sxs-lookup"><span data-stu-id="e39d9-106">For more information, see [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105).</span></span> <span data-ttu-id="e39d9-107">如需討論，請參閱 [dotnet/aspnetcore # 7289](https://github.com/dotnet/aspnetcore/issues/7289)。</span><span class="sxs-lookup"><span data-stu-id="e39d9-107">For discussion, see [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e39d9-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e39d9-108">Version introduced</span></span>

<span data-ttu-id="e39d9-109">3.0</span><span class="sxs-lookup"><span data-stu-id="e39d9-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e39d9-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e39d9-110">Recommended action</span></span>

<span data-ttu-id="e39d9-111">針對衍生的 OAuth 執行，最常見的變更是 `JObject.Parse` 在覆 `JsonDocument.Parse` 寫中取代， `CreateTicketAsync` 如下[here](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40)所示。</span><span class="sxs-lookup"><span data-stu-id="e39d9-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="e39d9-112">`JsonDocument` 會實作 `IDisposable`。</span><span class="sxs-lookup"><span data-stu-id="e39d9-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="e39d9-113">下列清單概述已知的變更：</span><span class="sxs-lookup"><span data-stu-id="e39d9-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="e39d9-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> 成為 `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)` 。</span><span class="sxs-lookup"><span data-stu-id="e39d9-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="e39d9-115">的所有衍生實 `ClaimAction` 也會受到影響。</span><span class="sxs-lookup"><span data-stu-id="e39d9-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="e39d9-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> 變成 `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="e39d9-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="e39d9-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> 變成 `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="e39d9-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="e39d9-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> 已移除一個舊的函式，而另一個已取代為 `JObject` `JsonElement` 。</span><span class="sxs-lookup"><span data-stu-id="e39d9-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="e39d9-119">`User`屬性和 `RunClaimActions` 方法已更新以符合。</span><span class="sxs-lookup"><span data-stu-id="e39d9-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="e39d9-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> 現在接受型別為的參數， `JsonDocument` 而不是 `JObject` 。</span><span class="sxs-lookup"><span data-stu-id="e39d9-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="e39d9-121">`Response`屬性已更新為符合。</span><span class="sxs-lookup"><span data-stu-id="e39d9-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="e39d9-122">`OAuthTokenResponse` 現在是可處置的，且將由處置 `OAuthHandler` 。</span><span class="sxs-lookup"><span data-stu-id="e39d9-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="e39d9-123">衍生的 OAuth 實施覆寫 `ExchangeCodeAsync` 不需要處置 `JsonDocument` 或 `OAuthTokenResponse` 。</span><span class="sxs-lookup"><span data-stu-id="e39d9-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="e39d9-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> 已從變更 `JObject` 為 `JsonDocument` 。</span><span class="sxs-lookup"><span data-stu-id="e39d9-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="e39d9-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> 已從變更 `JObject` 為 `JsonElement` 。</span><span class="sxs-lookup"><span data-stu-id="e39d9-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="e39d9-126">[TwitterHandler. CreateTicketAsync (ClaimsIdentity、AuthenticationProperties、AccessToken、JObject) ](/dotnet/api/microsoft.aspnetcore.authentication.twitter.twitterhandler.createticketasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Authentication_Twitter_TwitterHandler_CreateTicketAsync_System_Security_Claims_ClaimsIdentity_Microsoft_AspNetCore_Authentication_AuthenticationProperties_Microsoft_AspNetCore_Authentication_Twitter_AccessToken_Newtonsoft_Json_Linq_JObject_)的最後一個參數已從變更 `JObject` 為 `JsonElement` 。</span><span class="sxs-lookup"><span data-stu-id="e39d9-126">The last parameter of [TwitterHandler.CreateTicketAsync(ClaimsIdentity,AuthenticationProperties,AccessToken,JObject)](/dotnet/api/microsoft.aspnetcore.authentication.twitter.twitterhandler.createticketasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Authentication_Twitter_TwitterHandler_CreateTicketAsync_System_Security_Claims_ClaimsIdentity_Microsoft_AspNetCore_Authentication_AuthenticationProperties_Microsoft_AspNetCore_Authentication_Twitter_AccessToken_Newtonsoft_Json_Linq_JObject_) changed from `JObject` to `JsonElement`.</span></span> <span data-ttu-id="e39d9-127">取代方法為 <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,System.Text.Json.JsonElement)?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e39d9-127">The replacement method is <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,System.Text.Json.JsonElement)?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="e39d9-128">類別</span><span class="sxs-lookup"><span data-stu-id="e39d9-128">Category</span></span>

<span data-ttu-id="e39d9-129">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e39d9-129">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e39d9-130">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e39d9-130">Affected APIs</span></span>

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
