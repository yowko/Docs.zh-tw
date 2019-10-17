---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393976"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="ee7dc-101">身分識別： SignInAsync 擲回未驗證身分識別的例外狀況</span><span class="sxs-lookup"><span data-stu-id="ee7dc-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="ee7dc-102">根據預設，`SignInAsync` 會擲回主體/身分識別的例外狀況，其中 `IsAuthenticated` `false`。</span><span class="sxs-lookup"><span data-stu-id="ee7dc-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ee7dc-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ee7dc-103">Version introduced</span></span>

<span data-ttu-id="ee7dc-104">3.0</span><span class="sxs-lookup"><span data-stu-id="ee7dc-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ee7dc-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="ee7dc-105">Old behavior</span></span>

<span data-ttu-id="ee7dc-106">`SignInAsync` 會接受任何主體/身分識別，包括 `IsAuthenticated` @no__t 為2的身分識別。</span><span class="sxs-lookup"><span data-stu-id="ee7dc-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ee7dc-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="ee7dc-107">New behavior</span></span>

<span data-ttu-id="ee7dc-108">根據預設，`SignInAsync` 會擲回主體/身分識別的例外狀況，其中 `IsAuthenticated` `false`。</span><span class="sxs-lookup"><span data-stu-id="ee7dc-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="ee7dc-109">有一個新的旗標可抑制此行為，但預設行為已變更。</span><span class="sxs-lookup"><span data-stu-id="ee7dc-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ee7dc-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="ee7dc-110">Reason for change</span></span>

<span data-ttu-id="ee7dc-111">舊的行為會造成問題，因為根據預設，這些主體會被 `[Authorize]` @ no__t-1 @ no__t-2 拒絕。</span><span class="sxs-lookup"><span data-stu-id="ee7dc-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ee7dc-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ee7dc-112">Recommended action</span></span>

<span data-ttu-id="ee7dc-113">在 ASP.NET Core 3.0 Preview 6 中，`AuthenticationOptions` 上有 `RequireAuthenticatedSignIn` 旗標，預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="ee7dc-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="ee7dc-114">將此旗標設定為 `false`，以還原舊的行為。</span><span class="sxs-lookup"><span data-stu-id="ee7dc-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="ee7dc-115">分類</span><span class="sxs-lookup"><span data-stu-id="ee7dc-115">Category</span></span>

<span data-ttu-id="ee7dc-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ee7dc-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ee7dc-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ee7dc-117">Affected APIs</span></span>

<span data-ttu-id="ee7dc-118">無</span><span class="sxs-lookup"><span data-stu-id="ee7dc-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
