---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032322"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="529b4-101">授權： IAuthorizationPolicyProvider 執行需要新的方法</span><span class="sxs-lookup"><span data-stu-id="529b4-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="529b4-102">在 ASP.NET Core 3.0 中，已將新 `GetFallbackPolicyAsync` 方法加入至 `IAuthorizationPolicyProvider` 。</span><span class="sxs-lookup"><span data-stu-id="529b4-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="529b4-103">當未指定任何原則時，授權中介軟體會使用此回退原則。</span><span class="sxs-lookup"><span data-stu-id="529b4-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="529b4-104">如需詳細資訊，請參閱 [dotnet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759)。</span><span class="sxs-lookup"><span data-stu-id="529b4-104">For more information, see [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="529b4-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="529b4-105">Version introduced</span></span>

<span data-ttu-id="529b4-106">3.0</span><span class="sxs-lookup"><span data-stu-id="529b4-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="529b4-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="529b4-107">Old behavior</span></span>

<span data-ttu-id="529b4-108">的實現不 `IAuthorizationPolicyProvider` 需要 `GetFallbackPolicyAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="529b4-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="529b4-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="529b4-109">New behavior</span></span>

<span data-ttu-id="529b4-110">的執行 `IAuthorizationPolicyProvider` 需要 `GetFallbackPolicyAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="529b4-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="529b4-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="529b4-111">Reason for change</span></span>

<span data-ttu-id="529b4-112">如果未指定任何原則，則需要新的方法 `AuthorizationMiddleware` 才能使用新的。</span><span class="sxs-lookup"><span data-stu-id="529b4-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="529b4-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="529b4-113">Recommended action</span></span>

<span data-ttu-id="529b4-114">將 `GetFallbackPolicyAsync` 方法新增至的您的執行 `IAuthorizationPolicyProvider` 。</span><span class="sxs-lookup"><span data-stu-id="529b4-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="529b4-115">類別</span><span class="sxs-lookup"><span data-stu-id="529b4-115">Category</span></span>

<span data-ttu-id="529b4-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="529b4-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="529b4-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="529b4-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
