---
ms.openlocfilehash: 60ebcd9fc9ca18c33d31b82ba5020426d22a7d5a
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901829"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a><span data-ttu-id="d4daa-101">驗證：已移除 HttpCoNtext 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="d4daa-101">Authentication: HttpContext.Authentication property removed</span></span>

<span data-ttu-id="d4daa-102">已移除 `HttpContext` 上已淘汰的 `Authentication` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d4daa-102">The deprecated `Authentication` property on `HttpContext` has been removed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d4daa-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="d4daa-103">Change description</span></span>

<span data-ttu-id="d4daa-104">做為[dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504)的一部分，已移除 `HttpContext` 上已淘汰的 `Authentication` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d4daa-104">As part of [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504), the deprecated `Authentication` property on `HttpContext` has been removed.</span></span> <span data-ttu-id="d4daa-105">2\.0 之後，`Authentication` 屬性已被取代。</span><span class="sxs-lookup"><span data-stu-id="d4daa-105">The `Authentication` property has been deprecated since 2.0.</span></span> <span data-ttu-id="d4daa-106">已發行[遷移指南](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions)，以將使用此已淘汰屬性的程式碼遷移至新的取代 api。</span><span class="sxs-lookup"><span data-stu-id="d4daa-106">A [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) was published to migrate code using this deprecated property to the new replacement APIs.</span></span> <span data-ttu-id="d4daa-107">與舊的 ASP.NET Core 1.x 驗證堆疊相關的其餘未使用類別/Api，已在認可[dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65)中移除。</span><span class="sxs-lookup"><span data-stu-id="d4daa-107">The remaining unused classes / APIs related to the old ASP.NET Core 1.x authentication stack were removed in commit [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65).</span></span>

<span data-ttu-id="d4daa-108">如需討論，請參閱[dotnet/aspnetcore # 6533 沒有](https://github.com/dotnet/aspnetcore/issues/6533)。</span><span class="sxs-lookup"><span data-stu-id="d4daa-108">For discussion, see [dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d4daa-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d4daa-109">Version introduced</span></span>

<span data-ttu-id="d4daa-110">3.0</span><span class="sxs-lookup"><span data-stu-id="d4daa-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d4daa-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d4daa-111">Reason for change</span></span>

<span data-ttu-id="d4daa-112">ASP.NET Core 1.0 Api 已由 <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>中的擴充方法所取代。</span><span class="sxs-lookup"><span data-stu-id="d4daa-112">ASP.NET Core 1.0 APIs have been replaced by extension methods in <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d4daa-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d4daa-113">Recommended action</span></span>

<span data-ttu-id="d4daa-114">請參閱[遷移指南](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions)。</span><span class="sxs-lookup"><span data-stu-id="d4daa-114">See the [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span></span>

#### <a name="category"></a><span data-ttu-id="d4daa-115">分類</span><span class="sxs-lookup"><span data-stu-id="d4daa-115">Category</span></span>

<span data-ttu-id="d4daa-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d4daa-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d4daa-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d4daa-117">Affected APIs</span></span>

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
