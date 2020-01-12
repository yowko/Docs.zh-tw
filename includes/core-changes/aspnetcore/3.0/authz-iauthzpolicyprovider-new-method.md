---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901605"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="b6f4b-101">授權： IAuthorizationPolicyProvider 的部署需要新的方法</span><span class="sxs-lookup"><span data-stu-id="b6f4b-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="b6f4b-102">在 ASP.NET Core 3.0 中，已將新的 `GetFallbackPolicyAsync` 方法新增至 `IAuthorizationPolicyProvider`。</span><span class="sxs-lookup"><span data-stu-id="b6f4b-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="b6f4b-103">當未指定任何原則時，授權中介軟體會使用此回溯原則。</span><span class="sxs-lookup"><span data-stu-id="b6f4b-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="b6f4b-104">如需詳細資訊，請參閱[dotnet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759)。</span><span class="sxs-lookup"><span data-stu-id="b6f4b-104">For more information, see [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b6f4b-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b6f4b-105">Version introduced</span></span>

<span data-ttu-id="b6f4b-106">3.0</span><span class="sxs-lookup"><span data-stu-id="b6f4b-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b6f4b-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="b6f4b-107">Old behavior</span></span>

<span data-ttu-id="b6f4b-108">`IAuthorizationPolicyProvider` 的執行不需要 `GetFallbackPolicyAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="b6f4b-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b6f4b-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="b6f4b-109">New behavior</span></span>

<span data-ttu-id="b6f4b-110">`IAuthorizationPolicyProvider` 的實現需要 `GetFallbackPolicyAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="b6f4b-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b6f4b-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b6f4b-111">Reason for change</span></span>

<span data-ttu-id="b6f4b-112">新的 `AuthorizationMiddleware` 需要新的方法，才能在未指定任何原則時使用。</span><span class="sxs-lookup"><span data-stu-id="b6f4b-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b6f4b-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b6f4b-113">Recommended action</span></span>

<span data-ttu-id="b6f4b-114">將 `GetFallbackPolicyAsync` 方法加入至 `IAuthorizationPolicyProvider`的執行。</span><span class="sxs-lookup"><span data-stu-id="b6f4b-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="b6f4b-115">分類</span><span class="sxs-lookup"><span data-stu-id="b6f4b-115">Category</span></span>

<span data-ttu-id="b6f4b-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b6f4b-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b6f4b-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b6f4b-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
