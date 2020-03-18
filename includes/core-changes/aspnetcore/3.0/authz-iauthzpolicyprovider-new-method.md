---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901605"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="70c1a-101">授權：I授權策略提供程式實現需要新方法</span><span class="sxs-lookup"><span data-stu-id="70c1a-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="70c1a-102">在 ASP.NET Core 3.0`GetFallbackPolicyAsync`中，將`IAuthorizationPolicyProvider`一種新方法添加到 中。</span><span class="sxs-lookup"><span data-stu-id="70c1a-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="70c1a-103">當未指定策略時，授權中介軟體會使用此回退策略。</span><span class="sxs-lookup"><span data-stu-id="70c1a-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="70c1a-104">有關詳細資訊，請參閱[點網/阿斯平核心#9759](https://github.com/dotnet/aspnetcore/pull/9759)。</span><span class="sxs-lookup"><span data-stu-id="70c1a-104">For more information, see [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="70c1a-105">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="70c1a-105">Version introduced</span></span>

<span data-ttu-id="70c1a-106">3.0</span><span class="sxs-lookup"><span data-stu-id="70c1a-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="70c1a-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="70c1a-107">Old behavior</span></span>

<span data-ttu-id="70c1a-108">的`IAuthorizationPolicyProvider`實現不需要方法`GetFallbackPolicyAsync`。</span><span class="sxs-lookup"><span data-stu-id="70c1a-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="70c1a-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="70c1a-109">New behavior</span></span>

<span data-ttu-id="70c1a-110">的`IAuthorizationPolicyProvider`實現需要一種方法`GetFallbackPolicyAsync`。</span><span class="sxs-lookup"><span data-stu-id="70c1a-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="70c1a-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="70c1a-111">Reason for change</span></span>

<span data-ttu-id="70c1a-112">當未指定策略時，新方法`AuthorizationMiddleware`需要一個新的方法才能使用。</span><span class="sxs-lookup"><span data-stu-id="70c1a-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="70c1a-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="70c1a-113">Recommended action</span></span>

<span data-ttu-id="70c1a-114">將`GetFallbackPolicyAsync`方法添加到 的`IAuthorizationPolicyProvider`實現中。</span><span class="sxs-lookup"><span data-stu-id="70c1a-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="70c1a-115">類別</span><span class="sxs-lookup"><span data-stu-id="70c1a-115">Category</span></span>

<span data-ttu-id="70c1a-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="70c1a-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="70c1a-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="70c1a-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
