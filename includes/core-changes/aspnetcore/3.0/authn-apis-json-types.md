---
ms.openlocfilehash: 494e792d63a611cdaedf3e40aa607cfbb0420ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901969"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="04e72-101">身份驗證：牛頓軟.Json 類型替換</span><span class="sxs-lookup"><span data-stu-id="04e72-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="04e72-102">在ASP.NET核心 3.0`Newtonsoft.Json`中，身份驗證 API 中使用的類型已`System.Text.Json`替換為類型。</span><span class="sxs-lookup"><span data-stu-id="04e72-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="04e72-103">除以下情況外，身份驗證封裝的基本使用不受影響：</span><span class="sxs-lookup"><span data-stu-id="04e72-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="04e72-104">派生自 OAuth 提供程式的類，例如來自[aspnet-contrib 的](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers)類。</span><span class="sxs-lookup"><span data-stu-id="04e72-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="04e72-105">高級聲明操作實現。</span><span class="sxs-lookup"><span data-stu-id="04e72-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="04e72-106">有關詳細資訊，請參閱[點網/阿斯平核心#7105](https://github.com/dotnet/aspnetcore/pull/7105)。</span><span class="sxs-lookup"><span data-stu-id="04e72-106">For more information, see [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105).</span></span> <span data-ttu-id="04e72-107">有關討論，請參閱[點網/阿斯平核心#7289](https://github.com/dotnet/aspnetcore/issues/7289)。</span><span class="sxs-lookup"><span data-stu-id="04e72-107">For discussion, see [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="04e72-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="04e72-108">Version introduced</span></span>

<span data-ttu-id="04e72-109">3.0</span><span class="sxs-lookup"><span data-stu-id="04e72-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="04e72-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="04e72-110">Recommended action</span></span>

<span data-ttu-id="04e72-111">對於派生的 OAuth 實現，最常見的`JObject.Parse`更改是在`JsonDocument.Parse``CreateTicketAsync`重寫中替換為，[如下所示](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40)。</span><span class="sxs-lookup"><span data-stu-id="04e72-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="04e72-112">`JsonDocument` 會實作 `IDisposable`。</span><span class="sxs-lookup"><span data-stu-id="04e72-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="04e72-113">以下清單概述了已知的更改：</span><span class="sxs-lookup"><span data-stu-id="04e72-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="04e72-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>變為`ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`。</span><span class="sxs-lookup"><span data-stu-id="04e72-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="04e72-115">的所有`ClaimAction`派生實現都同樣受到影響。</span><span class="sxs-lookup"><span data-stu-id="04e72-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="04e72-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> 變成 `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="04e72-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="04e72-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> 變成 `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="04e72-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="04e72-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>已刪除一個舊建構函式，另一個`JObject`替換為`JsonElement`。</span><span class="sxs-lookup"><span data-stu-id="04e72-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="04e72-119">屬性`User`和方法`RunClaimActions`已更新以匹配。</span><span class="sxs-lookup"><span data-stu-id="04e72-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="04e72-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>現在接受類型的`JsonDocument`參數而不是`JObject`。</span><span class="sxs-lookup"><span data-stu-id="04e72-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="04e72-121">屬性`Response`已更新以匹配。</span><span class="sxs-lookup"><span data-stu-id="04e72-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="04e72-122">`OAuthTokenResponse`現在是一次性的，將由 處理`OAuthHandler`。</span><span class="sxs-lookup"><span data-stu-id="04e72-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="04e72-123">重寫`ExchangeCodeAsync`的派生 OAuth 實現不需要釋放`JsonDocument`或`OAuthTokenResponse`。</span><span class="sxs-lookup"><span data-stu-id="04e72-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="04e72-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>從`JObject`更改為`JsonDocument`。</span><span class="sxs-lookup"><span data-stu-id="04e72-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="04e72-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>從`JObject`更改為`JsonElement`。</span><span class="sxs-lookup"><span data-stu-id="04e72-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="04e72-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType>從接受`JObject`更改為`JsonElement`。</span><span class="sxs-lookup"><span data-stu-id="04e72-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="04e72-127">類別</span><span class="sxs-lookup"><span data-stu-id="04e72-127">Category</span></span>

<span data-ttu-id="04e72-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="04e72-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="04e72-129">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="04e72-129">Affected APIs</span></span>

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
