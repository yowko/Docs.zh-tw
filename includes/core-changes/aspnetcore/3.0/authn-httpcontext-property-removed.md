---
ms.openlocfilehash: 60ebcd9fc9ca18c33d31b82ba5020426d22a7d5a
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032341"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a><span data-ttu-id="6076c-101">驗證：已移除 HttpCoNtext 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="6076c-101">Authentication: HttpContext.Authentication property removed</span></span>

<span data-ttu-id="6076c-102">已移除已被取代的 `Authentication` 屬性 `HttpContext` 。</span><span class="sxs-lookup"><span data-stu-id="6076c-102">The deprecated `Authentication` property on `HttpContext` has been removed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6076c-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="6076c-103">Change description</span></span>

<span data-ttu-id="6076c-104">在 [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504)中，已移除已 `Authentication` 被取代的屬性 `HttpContext` 。</span><span class="sxs-lookup"><span data-stu-id="6076c-104">As part of [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504), the deprecated `Authentication` property on `HttpContext` has been removed.</span></span> <span data-ttu-id="6076c-105">`Authentication`自2.0 起，屬性已被取代。</span><span class="sxs-lookup"><span data-stu-id="6076c-105">The `Authentication` property has been deprecated since 2.0.</span></span> <span data-ttu-id="6076c-106">已發佈 [遷移指南](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) ，以使用這個已淘汰的屬性將程式碼遷移至新的取代 api。</span><span class="sxs-lookup"><span data-stu-id="6076c-106">A [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) was published to migrate code using this deprecated property to the new replacement APIs.</span></span> <span data-ttu-id="6076c-107">與舊的 ASP.NET Core 1.x 驗證堆疊相關的其餘未使用類別/Api 已在 commit 中移除 [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65) 。</span><span class="sxs-lookup"><span data-stu-id="6076c-107">The remaining unused classes / APIs related to the old ASP.NET Core 1.x authentication stack were removed in commit [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65).</span></span>

<span data-ttu-id="6076c-108">如需討論，請參閱 [dotnet/aspnetcore # 6533](https://github.com/dotnet/aspnetcore/issues/6533)。</span><span class="sxs-lookup"><span data-stu-id="6076c-108">For discussion, see [dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6076c-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6076c-109">Version introduced</span></span>

<span data-ttu-id="6076c-110">3.0</span><span class="sxs-lookup"><span data-stu-id="6076c-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6076c-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="6076c-111">Reason for change</span></span>

<span data-ttu-id="6076c-112">ASP.NET Core 1.0 Api 已由中的擴充方法取代 <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="6076c-112">ASP.NET Core 1.0 APIs have been replaced by extension methods in <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6076c-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="6076c-113">Recommended action</span></span>

<span data-ttu-id="6076c-114">請參閱 [遷移指南](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions)。</span><span class="sxs-lookup"><span data-stu-id="6076c-114">See the [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span></span>

#### <a name="category"></a><span data-ttu-id="6076c-115">類別</span><span class="sxs-lookup"><span data-stu-id="6076c-115">Category</span></span>

<span data-ttu-id="6076c-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6076c-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6076c-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6076c-117">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpContext.Authentication?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler`
- `P:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext`
- `P:Microsoft.AspNetCore.Http.HttpContext.Authentication`

-->
