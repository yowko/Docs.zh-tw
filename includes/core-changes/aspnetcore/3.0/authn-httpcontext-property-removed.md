---
ms.openlocfilehash: 60ebcd9fc9ca18c33d31b82ba5020426d22a7d5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901829"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a><span data-ttu-id="f74a9-101">身份驗證：HTTPCoNtext.身份驗證屬性已刪除</span><span class="sxs-lookup"><span data-stu-id="f74a9-101">Authentication: HttpContext.Authentication property removed</span></span>

<span data-ttu-id="f74a9-102">已刪除 上的`Authentication``HttpContext`已棄用屬性。</span><span class="sxs-lookup"><span data-stu-id="f74a9-102">The deprecated `Authentication` property on `HttpContext` has been removed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f74a9-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="f74a9-103">Change description</span></span>

<span data-ttu-id="f74a9-104">作為[dotnet/aspnetcore_6504](https://github.com/dotnet/aspnetcore/pull/6504)的一部分，已刪除`Authentication`上的`HttpContext`棄用屬性。</span><span class="sxs-lookup"><span data-stu-id="f74a9-104">As part of [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504), the deprecated `Authentication` property on `HttpContext` has been removed.</span></span> <span data-ttu-id="f74a9-105">自`Authentication`2.0 起，該屬性已被棄用。</span><span class="sxs-lookup"><span data-stu-id="f74a9-105">The `Authentication` property has been deprecated since 2.0.</span></span> <span data-ttu-id="f74a9-106">發佈了[遷移指南](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions)，用於使用此棄用屬性將代碼遷移到新的替換 API。</span><span class="sxs-lookup"><span data-stu-id="f74a9-106">A [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) was published to migrate code using this deprecated property to the new replacement APIs.</span></span> <span data-ttu-id="f74a9-107">其餘未使用的類/API與舊ASP.NET Core 1.x 身份驗證堆疊在提交[dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65)中被刪除。</span><span class="sxs-lookup"><span data-stu-id="f74a9-107">The remaining unused classes / APIs related to the old ASP.NET Core 1.x authentication stack were removed in commit [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65).</span></span>

<span data-ttu-id="f74a9-108">有關討論，請參閱[點網/阿斯平核心#6533](https://github.com/dotnet/aspnetcore/issues/6533)。</span><span class="sxs-lookup"><span data-stu-id="f74a9-108">For discussion, see [dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f74a9-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f74a9-109">Version introduced</span></span>

<span data-ttu-id="f74a9-110">3.0</span><span class="sxs-lookup"><span data-stu-id="f74a9-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f74a9-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="f74a9-111">Reason for change</span></span>

<span data-ttu-id="f74a9-112">ASP.NET 核心 1.0 API 已被 中的<xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>擴充方法替換。</span><span class="sxs-lookup"><span data-stu-id="f74a9-112">ASP.NET Core 1.0 APIs have been replaced by extension methods in <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f74a9-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f74a9-113">Recommended action</span></span>

<span data-ttu-id="f74a9-114">請參閱[遷移指南](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions)。</span><span class="sxs-lookup"><span data-stu-id="f74a9-114">See the [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span></span>

#### <a name="category"></a><span data-ttu-id="f74a9-115">類別</span><span class="sxs-lookup"><span data-stu-id="f74a9-115">Category</span></span>

<span data-ttu-id="f74a9-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f74a9-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f74a9-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f74a9-117">Affected APIs</span></span>

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
