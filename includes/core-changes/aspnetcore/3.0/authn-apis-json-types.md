---
ms.openlocfilehash: ad451329d7b9ec15bc8b3c49159346d79944d692
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394255"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="e30d2-101">驗證： Newtonsoft 已取代的 Json 類型</span><span class="sxs-lookup"><span data-stu-id="e30d2-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="e30d2-102">在 ASP.NET Core 3.0 中，驗證 Api 中使用的 `Newtonsoft.Json` 類型已取代為 `System.Text.Json` 類型。</span><span class="sxs-lookup"><span data-stu-id="e30d2-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="e30d2-103">除了下列情況以外，驗證套件的基本使用方式不會受到影響：</span><span class="sxs-lookup"><span data-stu-id="e30d2-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="e30d2-104">衍生自 OAuth 提供者的類別，例如來自[aspnet 的 contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers)。</span><span class="sxs-lookup"><span data-stu-id="e30d2-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="e30d2-105">Advanced 宣告操作的實施。</span><span class="sxs-lookup"><span data-stu-id="e30d2-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="e30d2-106">如需詳細資訊，請參閱[aspnet/AspNetCore # 7105 in](https://github.com/aspnet/AspNetCore/pull/7105)。</span><span class="sxs-lookup"><span data-stu-id="e30d2-106">For more information, see [aspnet/AspNetCore#7105](https://github.com/aspnet/AspNetCore/pull/7105).</span></span> <span data-ttu-id="e30d2-107">如需討論，請參閱[aspnet/AspNetCore # 7289](https://github.com/aspnet/AspNetCore/issues/7289)。</span><span class="sxs-lookup"><span data-stu-id="e30d2-107">For discussion, see [aspnet/AspNetCore#7289](https://github.com/aspnet/AspNetCore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e30d2-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e30d2-108">Version introduced</span></span>

<span data-ttu-id="e30d2-109">3.0</span><span class="sxs-lookup"><span data-stu-id="e30d2-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e30d2-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e30d2-110">Recommended action</span></span>

<span data-ttu-id="e30d2-111">針對衍生的 OAuth 執行，最常見的變更是將 `JObject.Parse` 取代為 `CreateTicketAsync` 覆寫中的 `JsonDocument.Parse` [，如下所示。](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40)</span><span class="sxs-lookup"><span data-stu-id="e30d2-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="e30d2-112">`JsonDocument` 會執行 `IDisposable`。</span><span class="sxs-lookup"><span data-stu-id="e30d2-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="e30d2-113">下列清單列出已知的變更：</span><span class="sxs-lookup"><span data-stu-id="e30d2-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="e30d2-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> 會變成 `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`。</span><span class="sxs-lookup"><span data-stu-id="e30d2-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="e30d2-115">`ClaimAction` 的所有衍生的執行都會同樣受到影響。</span><span class="sxs-lookup"><span data-stu-id="e30d2-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="e30d2-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> 變成 `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="e30d2-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="e30d2-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> 變成 `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="e30d2-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="e30d2-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> 已移除一個舊的函式，而且另一個已使用 `JsonElement`取代 `JObject`。</span><span class="sxs-lookup"><span data-stu-id="e30d2-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="e30d2-119">`User` 屬性和 `RunClaimActions` 方法已更新為符合。</span><span class="sxs-lookup"><span data-stu-id="e30d2-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="e30d2-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> 現在接受類型為 `JsonDocument` 的參數，而不是 `JObject`。</span><span class="sxs-lookup"><span data-stu-id="e30d2-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="e30d2-121">`Response` 屬性已更新為符合。</span><span class="sxs-lookup"><span data-stu-id="e30d2-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="e30d2-122">`OAuthTokenResponse` 現在可以處置，並會由 `OAuthHandler`處置。</span><span class="sxs-lookup"><span data-stu-id="e30d2-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="e30d2-123">覆寫 `ExchangeCodeAsync` 的衍生 OAuth 部署不需要處置 `JsonDocument` 或 `OAuthTokenResponse`。</span><span class="sxs-lookup"><span data-stu-id="e30d2-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="e30d2-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> 從 `JObject` 變更為 `JsonDocument`。</span><span class="sxs-lookup"><span data-stu-id="e30d2-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="e30d2-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> 從 `JObject` 變更為 `JsonElement`。</span><span class="sxs-lookup"><span data-stu-id="e30d2-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="e30d2-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> 從接受 `JObject` 變更為 `JsonElement`。</span><span class="sxs-lookup"><span data-stu-id="e30d2-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="e30d2-127">類別</span><span class="sxs-lookup"><span data-stu-id="e30d2-127">Category</span></span>

<span data-ttu-id="e30d2-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e30d2-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e30d2-129">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e30d2-129">Affected APIs</span></span>

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
