---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032368"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="69460-101">Identity： SignInAsync 會針對未驗證的身分識別擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="69460-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="69460-102">根據預設，會擲回主體/身分識別的 `SignInAsync` 例外狀況 `IsAuthenticated` `false` 。</span><span class="sxs-lookup"><span data-stu-id="69460-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="69460-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="69460-103">Version introduced</span></span>

<span data-ttu-id="69460-104">3.0</span><span class="sxs-lookup"><span data-stu-id="69460-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="69460-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="69460-105">Old behavior</span></span>

<span data-ttu-id="69460-106">`SignInAsync` 接受任何主體/身分識別，包括中的身分識別 `IsAuthenticated` `false` 。</span><span class="sxs-lookup"><span data-stu-id="69460-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="69460-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="69460-107">New behavior</span></span>

<span data-ttu-id="69460-108">根據預設，會擲回主體/身分識別的 `SignInAsync` 例外狀況 `IsAuthenticated` `false` 。</span><span class="sxs-lookup"><span data-stu-id="69460-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="69460-109">有一個新的旗標可抑制此行為，但預設行為已經變更。</span><span class="sxs-lookup"><span data-stu-id="69460-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="69460-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="69460-110">Reason for change</span></span>

<span data-ttu-id="69460-111">舊的行為有問題，因為依預設會拒絕這些主體 `[Authorize]`  /  `RequireAuthenticatedUser()` 。</span><span class="sxs-lookup"><span data-stu-id="69460-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="69460-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="69460-112">Recommended action</span></span>

<span data-ttu-id="69460-113">在 ASP.NET Core 3.0 Preview 6 中， `RequireAuthenticatedSignIn` 預設會有旗標 `AuthenticationOptions` `true` 。</span><span class="sxs-lookup"><span data-stu-id="69460-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="69460-114">將此旗標設定為， `false` 以還原舊的行為。</span><span class="sxs-lookup"><span data-stu-id="69460-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="69460-115">類別</span><span class="sxs-lookup"><span data-stu-id="69460-115">Category</span></span>

<span data-ttu-id="69460-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="69460-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="69460-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="69460-117">Affected APIs</span></span>

<span data-ttu-id="69460-118">None</span><span class="sxs-lookup"><span data-stu-id="69460-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
